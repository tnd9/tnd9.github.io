<!DOCTYPE html>
<html lang="es">
    <head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Taylor Dillon HM2/1.html</title>
        <style>
    body {	
    	margin: 0;
    	font-size:18px;
        font-family: Verdana, Geneva, sans-serif;
        color:#333;}
            
	ul.topnav {
    	list-style-type: none;
    	margin: 0;
    	padding: 0;
    	overflow: hidden;
    	background-color: #333;
    	position: fixed;
    	top: 0;
    	width: 100%;
}

	ul.topnav li {float: left;}

	ul.topnav li a {
		display: block;
   		color: white;
    	text-align: center;
    	padding: 14px 16px;
    	text-decoration: none;
    	font-family: Verdana, Geneva, sans-serif;
}

	ul.topnav li a:hover:not(.active) {background-color: #111;}

	ul.topnav li a.active {background-color: #00aaff;}

	ul.topnav li.right {float: right;}

@media screen and (max-width: 600px){
    ul.topnav li.right, 
    ul.topnav li {float: none;}
}
		#header{
        border:3px solid #333;
     	color:black;
        text-align: center;
        background-color: #e6f7ff;
        margin-top: 50px;
            }
   		#inicio{
        background-color:#f2f2f2;
        padding: 10px 10px 100px;
        margin: 10px 5px;
        }
        
        #cv{
        padding: 10px 10px 200px;
        margin: 10px 5px;
        background-color: #f2f2f2;
        }
        
        #ejercicios{
        padding: 10px 10px 200px;
        margin: 10px 5px;
        background-color: #f2f2f2;
        }
        footer{
        text-align: center;}
        </style>
        
<!--sparkles below-->
	<script type="text/javascript">
// <![CDATA[
var colour="#00baff";
var sparkles=120;

var x=ox=400;
var y=oy=300;
var swide=800;
var shigh=600;
var sleft=sdown=0;
var tiny=new Array();
var star=new Array();
var starv=new Array();
var starx=new Array();
var stary=new Array();
var tinyx=new Array();
var tinyy=new Array();
var tinyv=new Array();

window.onload=function() { if (document.getElementById) {
  var i, rats, rlef, rdow;
  for (var i=0; i<sparkles; i++) {
    var rats=createDiv(3, 3);
    rats.style.visibility="hidden";
    document.body.appendChild(tiny[i]=rats);
    starv[i]=0;
    tinyv[i]=0;
    var rats=createDiv(5, 5);
    rats.style.backgroundColor="transparent";
    rats.style.visibility="hidden";
    var rlef=createDiv(1, 5);
    var rdow=createDiv(5, 1);
    rats.appendChild(rlef);
    rats.appendChild(rdow);
    rlef.style.top="2px";
    rlef.style.left="0px";
    rdow.style.top="0px";
    rdow.style.left="2px";
    document.body.appendChild(star[i]=rats);
  }
  set_width();
  sparkle();
}}

function sparkle() {
  var c;
  if (x!=ox || y!=oy) {
    ox=x;
    oy=y;
    for (c=0; c<sparkles; c++) if (!starv[c]) {
      star[c].style.left=(starx[c]=x)+"px";
      star[c].style.top=(stary[c]=y)+"px";
      star[c].style.clip="rect(0px, 5px, 5px, 0px)";
      star[c].style.visibility="visible";
      starv[c]=50;
      break;
    }
  }
  for (c=0; c<sparkles; c++) {
    if (starv[c]) update_star(c);
    if (tinyv[c]) update_tiny(c);
  }
  setTimeout("sparkle()", 40);
}

function update_star(i) {
  if (--starv[i]==25) star[i].style.clip="rect(1px, 4px, 4px, 1px)";
  if (starv[i]) {
    stary[i]+=1+Math.random()*3;
    if (stary[i]<shigh+sdown) {
      star[i].style.top=stary[i]+"px";
      starx[i]+=(i%5-2)/5;
      star[i].style.left=starx[i]+"px";
    }
    else {
      star[i].style.visibility="hidden";
      starv[i]=0;
      return;
    }
  }
  else {
    tinyv[i]=50;
    tiny[i].style.top=(tinyy[i]=stary[i])+"px";
    tiny[i].style.left=(tinyx[i]=starx[i])+"px";
    tiny[i].style.width="2px";
    tiny[i].style.height="2px";
    star[i].style.visibility="hidden";
    tiny[i].style.visibility="visible"
  }
}

function update_tiny(i) {
  if (--tinyv[i]==25) {
    tiny[i].style.width="1px";
    tiny[i].style.height="1px";
  }
  if (tinyv[i]) {
    tinyy[i]+=1+Math.random()*3;
    if (tinyy[i]<shigh+sdown) {
      tiny[i].style.top=tinyy[i]+"px";
      tinyx[i]+=(i%5-2)/5;
      tiny[i].style.left=tinyx[i]+"px";
    }
    else {
      tiny[i].style.visibility="hidden";
      tinyv[i]=0;
      return;
    }
  }
  else tiny[i].style.visibility="hidden";
}

document.onmousemove=mouse;
function mouse(e) {
  set_scroll();
  y=(e)?e.pageY:event.y+sdown;
  x=(e)?e.pageX:event.x+sleft;
}

function set_scroll() {
  if (typeof(self.pageYOffset)=="number") {
    sdown=self.pageYOffset;
    sleft=self.pageXOffset;
  }
  else if (document.body.scrollTop || document.body.scrollLeft) {
    sdown=document.body.scrollTop;
    sleft=document.body.scrollLeft;
  }
  else if (document.documentElement && (document.documentElement.scrollTop || document.documentElement.scrollLeft)) {
    sleft=document.documentElement.scrollLeft;
	sdown=document.documentElement.scrollTop;
  }
  else {
    sdown=0;
    sleft=0;
  }
}

window.onresize=set_width;
function set_width() {
  if (typeof(self.innerWidth)=="number") {
    swide=self.innerWidth;
    shigh=self.innerHeight;
  }
  else if (document.documentElement && document.documentElement.clientWidth) {
    swide=document.documentElement.clientWidth;
    shigh=document.documentElement.clientHeight;
  }
  else if (document.body.clientWidth) {
    swide=document.body.clientWidth;
    shigh=document.body.clientHeight;
  }
}

function createDiv(height, width) {
  var div=document.createElement("div");
  div.style.position="absolute";
  div.style.height=height+"px";
  div.style.width=width+"px";
  div.style.overflow="hidden";
  div.style.backgroundColor=colour;
  return (div);
}
// ]]>
</script>
<!--sparkles above-->
<!--Bubbles below
	<script>if(typeof jQuery=='undefined'){document.write('<'+'script');document.write(' language="javascript"');document.write(' type="text/javascript"');document.write(' src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js">');document.write('</'+'script'+'>')}</script><script>if(!image_urls){var image_urls=Array()}if(!flash_urls){var flash_urls=Array()}image_urls['rain1']="http://i40.tinypic.com/2m34m6u.png";image_urls['rain2']="http://i40.tinypic.com/2m34m6u.png";image_urls['rain3']="http://i40.tinypic.com/2m34m6u.png";image_urls['rain4']="http://i40.tinypic.com/2m34m6u.png";$(document).ready(function(){var c=$(window).width();var d=$(window).height();var e=function(a,b){return Math.round(a+(Math.random()*(b-a)))};var f=function(a){setTimeout(function(){a.css({left:e(0,c)+'px',top:'-30px',display:'block',opacity:'0.'+e(10,100)}).animate({top:(d-10)+'px'},e(7500,8000),function(){$(this).fadeOut('slow',function(){f(a)})})},e(1,8000))};$('<div></div>').attr('id','rainDiv')
.css({position:'fixed',width:(c-20)+'px',height:'1px',left:'0px',top:'-5px',display:'block'}).appendTo('body');for(var i=1;i<=20;i++){var g=$('<img/>').attr('src',image_urls['rain'+e(1,4)])
.css({position:'absolute',left:e(0,c)+'px',top:'-30px',display:'block',opacity:'0.'+e(10,100),'margin-left':0}).addClass('rainDrop').appendTo('#rainDiv');f(g);g=null};var h=0;var j=0;$(window).resize(function(){c=$(window).width();d=$(window).height()})});</script>
	<script>if(typeof jQuery=='undefined'){document.write('<'+'script');document.write(' language="javascript"');document.write(' type="text/javascript"');document.write(' src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js">');document.write('</'+'script'+'>')}</script>
-->
    </head>
    <body>
	<ul class="topnav">
 		<li><a class="active" href="#inicio">INICIO</a></li>
  		<li><a href="#cv">CV</a></li>
  		<li><a href="#ejercicios">EJERCICIOS</a></li>

	</ul>
	<div id="header">
            <h1>Taylor Dillon H2/1</h1>
    </div>
    <div id="inicio">
                <p> ¡Bienvenidos a mi mini-pagina web! Soy Taylor. Esto es un borrador de mi proyecto sin el contenido </p>
                <p> No me gusta escribir sobre mí mismo. En la siguiente tarea, hará una pequeña biografía aqui </P>
    </div>
    <div id="cv">
                <h2 style="text-align: center; color: black;">Curriculum Vitae</h2>
                <h3>Educación</h3>
                <ul>
                    <li>Universidad de Miami, Colegio Rosenstiel de Ciencia Marina y Atmosférica (Coral Gables, Florida): Clase de 2019</li>
                    <li>Chadwick (California): Clase de 2015</li>
                </ul>
                <h3>Experiencia de Investigación</h3>
                <ul>
                    <li>Universidad de California Sur, Instituto Wrigley de Estudias Ambientales (Isla Santa Catalina, California): Junio 2017- Agosto 2017 </li>
                </ul>
                <h3>más</h3>
    </div>
    <div id="ejercicios">
                <h2 style="text-align: center; color: black;">Ejercicios</h2>
                <p>aqui puede ver los ejercicios que hagamos en clase</p>
    </div>
       
        
    <footer>
            <a>tnd9@miami.edu</a>
    </footer>
    </body>
</html>
