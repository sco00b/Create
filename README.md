<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<style>
canvas {
    border: 1px solid #d3d3d3;
    background-color: #bd6a6a;
}
</style>
</head>
<body onload="startGame()">
<script>

var myGameCharacter;
var GameObstacle;


function startGame() {
    myGameCharacter = new component(30, 30, "blue", 10, 120);
    GameObstacle = new component(20,250, "red", 310,120);
    myGameArea.start();
    
}



var myGameArea = {
    canvas : document.createElement("canvas"),
    start : function() {
        this.canvas.width = 480;
        this.canvas.height = 270;
        this.context = this.canvas.getContext("2d");
        document.body.insertBefore(this.canvas, document.body.childNodes[0]);
		this.interval = setInterval(updateGameArea, 20);
    },
	clear: function() {
	this.context.clearRect(0,0, this.canvas.width, this.canvas.height);
    },
    
}

function component(width, height, color, x, y) {
    this.width = width;
    this.height = height;
    this.speedX = 0;
    this.speedY = 0;
	this.x=x;
	this.y = y;    
this.update = function() {
    ctx = myGameArea.context;
    ctx.fillStyle = color;
    ctx.fillRect(this.x, this.y, this.width, this.height);
}
 this.newPos = function() {
        this.x += this.speedX;
        this.y += this.speedY;        
    }    



    
}

function updateGameArea() {
    
    myGameArea.clear();
    GameObstacle.update();
    myGameCharacter.newPos();    
    myGameCharacter.update();
}

function moveup() {
    myGameCharacter.speedY -= 1; 
}

function movedown() {
    myGameCharacter.speedY += 1; 
}

function moveleft() {
    myGameCharacter.speedX -= 1; 
}
function moveright() {
    myGameCharacter.speedX += 1; 

}


</script>
<div style="text-align:center;width:480px;">
    <button onclick="moveup()">UP</button><br><br>
    <button onclick="moveleft()">LEFT</button>
    <button onclick="moveright()">RIGHT</button><br><br>
    <button onclick="movedown()">DOWN</button>
</div>
</body>
</html>
