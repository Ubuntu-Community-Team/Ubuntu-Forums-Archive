---
title: "How the words can be reversed"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-21
[CENTER][LEFT][COLOR=black]I have seen this signature in this forum but the first two lines are upside down,how can we do this..?[/COLOR]Looks something different ;)
[COLOR=DarkOrange]
[/COLOR][/LEFT]
[COLOR=DarkOrange]&#633;&#477;pun u&#653;op pu&#592;l &#592; &#623;o&#633;&#607; &#477;&#623;o&#596;  &#305;[/COLOR]
[COLOR=DarkOrange]&#633;&#477;pun&#613;&#596; u&#477;&#623;  pu&#592; &#653;ol&#607; s&#477;op &#633;&#477;&#477;q &#477;&#633;&#477;&#613;&#653;[/COLOR]
[COLOR=Sienna]"May the source be with you"[/COLOR][/CENTER]

---

### Post by stinkeye on 2010-06-21
oll&#601;&#613;
[http://www.sunnyneo.com/upsidedowntext.php]("http://www.sunnyneo.com/upsidedowntext.php")

---

### Post by karthick87 on 2010-06-21
Can someone post [COLOR=Red]php[/COLOR] script for that..?

---

### Post by Matt__ on 2010-06-21
the letters are just remapped in unicode (mostly extended latin & phonetic alphabet).
something like this in Javascript...
```
<html><head> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"> 
<meta name="description" content="Turn text upside down. Rotate letters 180 degrees with Unicode."> 
<title>Upside down text conversion</title> 
<style type="text/css"> 
textarea { font-family: "Arial Unicode MS" }
h1 { margin-bottom: 2px;}
</style> 
<script> 
function flip() 
{
 var result = flipString(document.f.original.value.toLowerCase());
 document.f.flipped.value = result;
}
 
function flipString(aString)
 {
 var last = aString.length - 1;
 var result = new Array(aString.length)
 for (var i = last; i >= 0; --i) {
  var c = aString.charAt(i)
  var r = flipTable[c]
  result[last - i] = r ? r : c
 }
 return result.join('')
}
 
var flipTable = {
a : '\u0250',
b : 'q',
c : '\u0254', 
d : 'p',
e : '\u01DD',
f : '\u025F', 
g : '\u0183',
h : '\u0265',
i : '\u0131', 
j : '\u027E',
k : '\u029E',
//l : '\u0283',
m : '\u026F',
n : 'u',
r : '\u0279',
t : '\u0287',
v : '\u028C',
w : '\u028D',
y : '\u028E',
'.' : '\u02D9',
'[' : ']',
'(' : ')',
'{' : '}',
'?' : '\u00BF', 
'!' : '\u00A1',
"\'" : ',',
'<' : '>',
'_' : '\u203E',
'\u203F' : '\u2040',
'\u2045' : '\u2046',
'\u2234' : '\u2235',
'\r' : '\n' 
}
 
for (i in flipTable) {
  flipTable[flipTable[i]] = i
}
</script></head><body> 
<h1>Upside Down</h1> 
<form name="f">Original:
<br> 
<textarea rows="5" cols="50" name="original" onkeyup="flip()"></textarea>  
<br> 
Flipped:
<br> 
<textarea rows="5" cols="50" name="flipped"></textarea> 
</form> 
</body></html>
```dosnt really support capitalisation (im sure there is a way to do somewhere) and some of the letters are out of line too.

you could also just reverse the order of the letters
```
 <html>
<head>
<script type="text/javascript">
function reverseText( f, fromField, toField )
{
f.elements[toField].value = f.elements[fromField].value.split('').reverse().join('');
}
</script>
</head>
<body>
<form>
<input type="text" name="from" />
<input type="text" name="to" readonly="readonly"/>
<br/>
<input type="button" value="reverse" onclick="reverseText( this.form, 'from', 'to' );"/>
</form>
</body>
</html>
```
[COLOR=White].[/COLOR]

---

### Post by karthick87 on 2010-06-21
> **Matt__ said:**
> the letters are just remapped to unicode (mostly extended latin & phonetic alphabet).
something like this in Javascript...
```
<html><head> 
<meta http-equiv="Content-Type" content="text/html; charset=utf-8"> 
<meta name="description" content="Turn text upside down. Rotate letters 180 degrees with Unicode."> 
<title>Upside down text conversion</title> 
<style type="text/css"> 
textarea { font-family: "Arial Unicode MS" }
h1 { margin-bottom: 2px;}
</style> 
<script> 
function flip() 
{
 var result = flipString(document.f.original.value.toLowerCase());
 document.f.flipped.value = result;
}
 
function flipString(aString)
 {
 var last = aString.length - 1;
 //Thanks to Brook Monroe for the suggestion to use Array.join
 var result = new Array(aString.length)
 for (var i = last; i >= 0; --i) {
  var c = aString.charAt(i)
  var r = flipTable[c]
  result[last - i] = r ? r : c
 }
 return result.join('')
}
 
var flipTable = {
a : '\u0250',
b : 'q',
c : '\u0254', 
d : 'p',
e : '\u01DD',
f : '\u025F', 
g : '\u0183',
h : '\u0265',
i : '\u0131', 
j : '\u027E',
k : '\u029E',
//l : '\u0283',
m : '\u026F',
n : 'u',
r : '\u0279',
t : '\u0287',
v : '\u028C',
w : '\u028D',
y : '\u028E',
'.' : '\u02D9',
'[' : ']',
'(' : ')',
'{' : '}',
'?' : '\u00BF', 
'!' : '\u00A1',
"\'" : ',',
'<' : '>',
'_' : '\u203E',
'\u203F' : '\u2040',
'\u2045' : '\u2046',
'\u2234' : '\u2235',
'\r' : '\n' 
}
 
for (i in flipTable) {
  flipTable[flipTable[i]] = i
}
</script></head><body> 
<h1>Upside Down</h1> 
<form name="f">Original:
<br> 
<textarea rows="5" cols="50" name="original" onkeyup="flip()"></textarea>  
<br> 
Flipped:
<br> 
<textarea rows="5" cols="50" name="flipped"></textarea> 
</form> 
</body></html>
```dosnt really support capitalisation (im sure there is a way to do somewhere) and some of the letters are out of line too.



[COLOR=White].[/COLOR]


Gr8 thank you :)

---

### Post by Goodseeker on 2010-06-21
Of course, in situations where one can control the font, a similar effect could be obtained by using one of those fonts that have upside-down letters by design.

---

### Post by karthick87 on 2010-06-22
I know more people in this forum has very good programming skills...Can someone add capitalisation to the above script...?

---

### Post by Zill on 2010-06-22
Is it just *me* that can't see the point to this thread? :confused:

---

### Post by karthick87 on 2010-06-22
you could also just reverse the order of the letters
```
 <html>
<head>
<script type="text/javascript">
function reverseText( f, fromField, toField )
{
f.elements[toField].value = f.elements[fromField].value.split('').reverse().join('');
}
</script>
</head>
<body>
<form>
<input type="text" name="from" />
<input type="text" name="to" readonly="readonly"/>
<br/>
<input type="button" value="reverse" onclick="reverseText( this.form, 'from', 'to' );"/>
</form>
</body>
</html>
```How to increase the work area...?It means how to increase the text area...?

---

