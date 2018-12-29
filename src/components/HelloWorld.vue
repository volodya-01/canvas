<template>
  <div class="hello" ref="box">
   <canvas ref="canvas" width="1000" height="1000"></canvas>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted(){
    console.log(this.$refs.box)
    console.log(this.$refs.canvas)
    this. canvasapi()
  },
  methods:{
    canvasapi(){
      var canvas = this.$refs.canvas;
var context = canvas.getContext('2d');
// 偏移大小
var offset = 0;
var coodinates = [];
var lines = 5000;
 var createCoordinates = function () {
for(var i=0;i<lines;i++) { 
    var temp ={} ;
    var x;
    var y;
temp.x = Math.random()*1000;
temp.y = Math.random()*1000;
coodinates.push(temp);
 }
 }
createCoordinates();
console.log(coodinates);
var clear = function () {
// 清除画布
context.clearRect(0, 0, 1000, 1000);
context.fillText('清除', 200, 300);
setTimeout(draw, 2000);
};
// 绘制
var draw = function () {

context.clearRect(0,0, 1000, 1000);
context.fillText('绘制', 200, 300);
context.setLineDash([8, 4]);
context.lineWidth = 3;
context.strokeStyle = '#ff0000';
context.lineDashOffset = offset;
/* context.strokeRect(2, 2, 236, 116); */
context.beginPath();
for(var i=0;i<lines;i+=2){
context.moveTo(coodinates[i].x,coodinates[i].y);
context.lineTo(coodinates[i+1].x,coodinates[i+1].y);
}
context.closePath();
/* context.stroke();
context.moveTo(500,200)
context.lineTo(600,600+100*temp) */
/* context.lineTo(Math.random()*1000,Math.random()*1000) */
context.stroke()

//setTimeout(clear, 2000);
/* for(var i=0;i<20;i++){

setTimeout(draw1(), 1000);
}
 */

/* context.stroke() */
}

var run = function () {
offset += 1;
if (offset > 24) {
offset = 0;
}
draw();

// 继续绘制
requestAnimationFrame(run);
}
run();

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
