---
title: "Machine translation of HTML document"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by yc2 on 2011-03-05
Hi,

I don't know in which category to put this, I hope it is OK here.

I have been writing on an introduction to Ubuntu for pre-beinners (those thinking of "trying out Linux"). ([http://e-dog.info/t/63/doc/Ubuntu_installation.php](http://e-dog.info/t/63/doc/Ubuntu_installation.php))

I have written in Swedish and I now want to try to machine translate it into English.

I tried entering the url into Google translate which gave a better translation than I had expected. However, it was very irregular. Sometimes it didn't work at all. Most often it stopped translating in the middle of the document. Often the control-window duplicated itself repeatedly etc etc Javascript always broke down.

I will obviously have to do this machine translation semi-manually and put the result on my own server.

I will continue to rewrite the text in Swedish and sometimes translate it into English. I therefore want as little manual translation work as possible, but JavaScript must be intact, that is my wish.

Maybe I can avoid the problems of the PHP-code by taking the source from the browser and not by FTP. (JavaScript document.write-statements are maybe a smaller problem.)

So, summarizing:
I have a PHP-JavaScript HTML document in Swedish that I want to translate into English.

How should I do it in order to keep JavaScript intact and avoid the technical (but not so much laguagerelated) shortcomings of Google translate?

Right now I do not have regular access to my Ubuntu system. Instead I usually format documents using PHP on a web-server I have access to.

Thanks

---

### Post by grahammechanical on 2011-03-05
I think that you are doing a good work. I wish you success. I do not understand what the problems is, so forgive me if I get it wrong.

I am guessing that the machine/program based translation is failing because of the code that you have in the HTML document. Is this correct? Surely, HTML code and PHP code says the same whatever language the programmer is using?

You need to separate the text of the document from the coded document. Machine translate the text of the your "Ubuntu for Pre-beginners" document and then insert it into the HTML and Java coded document.

I am working on a English - Greek dictionary of the Christian Greek Scriptures. And I am coding it with HTML. I do have a master document but I also have each section/chapter as a separate file. I create the text of my dictionary in a word processor and then paste it in a HTML document putting in the codes as I go along. 

If I was tempted to machine translate as you are doing I would translate the text in the word processor and not the HTML document. I would then paste the new language text over the old language text.

It is the long way of doing it but is there an alternative? Someone may suggest an alternative.

Regards.

---

### Post by yc2 on 2011-03-05
To think first and type later is what you did and that is the best.

I have come to a situation where I have this mixed PHP-JS-HTML document where automatic translation messes up the JS.

I think the PHP is less of a problem since it only generates JS and HTML. It is better to start the translation when the PHP has already executed.

Google translate seems to be able to NOT to touch the HTML tags. However, JS gets really messed up.

I think I can maybe solve the problem in either of two ways, both taking some work.

1. Put all JS in external files and only include the reference in the document:
<script type="text/javascript" src="http://example.com/routine_003.js"></script>
I think these tags are left alone by the translator.

I just fear this method may change the order in which the code is read. If one routine reads a cookie value and the next uses it they must be read in the correct order. If I shift the routines to external files I am not sure they are read in the order they appear?? (I read some cookies before the load-event of the page and they determine formatting.)

2. Make a program that strips the document of JS and leaves a code(number) in the place where the JScode was removed. Then translate the document and finally put back the JS in the places where the code(numbers)s are found. This would make the code be read in the same order as in the original document. I started a thread about that:
[http://ubuntuforums.org/showthread.php?t=1700569](http://ubuntuforums.org/showthread.php?t=1700569)

---

### Post by wep940 on 2011-03-06
Okay, first I'm not the expert you guys are on this stuff. I can, however, tell you what I did that I think *might* apply for you:
 
I created a Perl program which read different parts of the html, etc., from different files and built the webpage it then sent to the user. If you did something similar, you could build your page using any translation you want if you keep the text itself in separate files - example: txt1_swedish.dat, txt1_english.dat, txt2_swedish.dat, txt2_english.dat, etc.. Use other little files for each piece of html that would be before and after each text portion. Then, build a small "template" file that lists the files in the order they should be processed, in example:
 
html1.html
html2.html
java1.java
txt1.dat
java2.java
txt2.dat
java2.java
html3.html
html4.html
 
 
etc..
 
Then using the Perl program, read the the template file, opening each file as stated and based on the language (I think you said you are getting this prior to load - just let the loaded form execute the Perl program on the server):
 
.html files in a html folder
.java files in a jave folder
.dat files in multiple folders: dat/swedish, dat/english, etc. dependant on the language you need to use
 
As you are reading these files you simply write them straight out to the connection.
 
EDIT:  Just in case I didn't make it clear, the html and java,etc., files don't have to be complete statements - it's just data you are reading to send out.  You can have a statement broken into multiple files, with the swedish/english bits in between where needed.

---

### Post by yc2 on 2011-03-06
I agree with you wep940. It is always better to put parts together than to try to take complex files apart. (I just didn't think so far when I put down a few lines four years ago. But adding small bits all the time, the text grows in amount and complexity.)

I am more used to PHP than to Perl. Therefore I would have done what you describe but in PHP. (Maybe better for once to keep the text in a file than in the MySQL database that usually "comes free" with the PHP.)

Also good input from you to put the _text_ separate. In the thread I linked to I suggested letting a program pick out javaScript. But maybe best to go through the manuscript manually once and set markers for where the pieces of _text_ starts and stops. Then try to make a program (PHP, Perl ...) that puts the marked text fragments in separate files and replace the text with a code

"===include file 0000001==="
"===include file 0000002==="

But so far I don't feel completely lost. I have just spent four hours putting 90% of JS (All that was not generated by PHP) in separate files. Since Google translate seems to leave HTML-tags alone, at least I feel the situation is not hopeless. I will not be able to generate different translations on the fly, but maybe in a coule of hours manual work, hopefully ...
(Neither can I have a file where I keep corrections that override errors in the automatic translation... many things to think of here ;) )

---

### Post by wep940 on 2011-03-07
I don't know anything about java or the other stuff you are using, but I thought I'd add a little to my reply just in case.
 
I was assuming that you would actually store the translated text in files on the server instead of translating on the fly.  In that way, your opening page can do no more than just determine the language then load the perl/whatever running page, which would build all of the page dynamically and send it out.  That way you would be able to support more than Swedish and English, with the catch being that if you make a change to the original (I assume Swedish) text, then you have to regenerate the translated pages.
 
I suppose that was already pretty clear, it's just that I sometimes don't explain things very well, and I don't have the experience you do so it could very well be that what you are doing is way over my head!
 
Best of luck!  ;)

---

### Post by yc2 on 2011-03-12
I now use an approach similar to what you suggested.
I cannot generate translations on the fly. I only cut and paste into Google translate.
My problem is separating what should be translated (text) and what should not (HTML, JavaScript). (Some links and most JavaScript becomes corrupt in the translation.) I already have an HTML document which mixes what should be translated and what cannot be translated (like JS) .
I finally decided to try the following:
I have inserted my own "XML"-tags into the PHP-document, indicating what should be translated.
```
This will not be translated.
<tX s=0>This will go to translation</tX>
This will not be translated.

```
All in all I inserted about 1200 tags into the document.
I then made a PHP program that numbers the "tX"-tags and puts the content of the tX-tags in a separate file only containing the text of the tX-tags.
I then translate this separate document through Google translate.
Later another program puts the translated tags back into the document in the appropriate places.
It finally seems to work. (I do not do so much parsing myself but use preg_match and preg_replace of PHP (like SED).)
The document got translated and JS and HTML is untouched.

However, the translation gets hacked up if a tag is in the sentence. It is not so easy to avoid. If I have a sentence in Swedish corresponding to
It is fine <a href=#w>weather</a> today.
and it gets translated to
It is a fine day.

Where should you put the link-tag in the final sentence :) The linked word (weather) is gone in the translation. You have to translate parts and it gets quirky.

The program seems to work rudimentaryly now. I just want to add the possibility of having unique IDs in the translation tags. if the translation is really quirky I want to be able to introduce manual translations into tags with a special ID. Will do that when I have time.

It is still a far way to go. The current reslut looks like this:
[http://e-dog.info/t/63/doc/Ubuntu_installation_eng.php](http://e-dog.info/t/63/doc/Ubuntu_installation_eng.php)

Extract from the source:
```
<p>
<tX s=0>
Har du synpunkter på sidans innehåll så finns
<a href="#Kontakt">kontaktinformation</a> längst ner. Välkommen
</tX>
<img src="http://yorabbit.info/e-dog.info/t/63/doc/pic/smiley.gif" alt=""></p>

<A name="snabbguide"></A>
<!-- a href="#example_xx" id="snabb" class="Fsp.Reveal"  style="margin: -6px 4px -16px 12px;  position: relative; top: -8px;  " onmouseup="quick_mouse_up()"><u>
<tX s=0>
snabbguide
</tX></u></a -->
<a href="javascript:quick_mouse_up()" id="snabb"  style="margin: -6px 4px -16px 12px;  position: relative; top: -8px; "><u>snabbguide</u></a>

<script type="text/javascript" src="http://yorabbit.info/e-dog.info/t/63/doc/ja_scr/fragments/read_quick_cookie.js"></script>

<!--  make border softer in MSIE since it does not fit absolutely perfectly -->
<div id="snabbguide_inner" class="p-shadow yl_red" style="width: 650px; border-width: 1px 0px 0px 1px; border-style: solid; border-top-color: #f4f4f4; _border-top-color: #f8f8f8; border-left-color: #f6f6f6; _border-left-color: #f8f8f8">
<div  class=yl_red>


<script type="text/javascript" src="http://yorabbit.info/e-dog.info/t/63/doc/ja_scr/fragments/operaChromeDiv_ON.js"></script>

<!-- width verkar funka pa msie och padding pa ff ??  -->

<!-- the [x] -->
<!-- span class="yl_small"  style="float: right"><a href="#example_xx" class="Fsp.Hide" onmouseup="quick_close_mouse_up()">[x]</a -->
<span class="yl_small"  style="float: right"><a href="javascript:quick_mouse_up()">[x]</a>

<script type="text/javascript" src="http://yorabbit.info/e-dog.info/t/63/doc/ja_scr/fragments/addBlankChars.js"></script>

</span>
<!-- the [x] -->

<span class="yl_small"><tX s=0>Har du inte tid att läsa den här web-sidan nu? - Kom igång direkt istället</tX>:</span><br>
1. <tX s=0>Laddda ner</tX>
<a href="http://www.ubuntu.com/getubuntu/download" target="_parent">Ubuntu desktop Live-CD</a>.
<div>2. <tX s=0>Bränn den nedladdade filen till en CD.</tX></div><div class=yl_small>
<span id="sp01" style="position: relative; left: 16px; width: 600px;  _width: 650px; padding: 0px 40px 0px 0px">
<tX s=0>Här står hur man
bränner</tX> <a href="#iso_fil"><tX s=0>iso-filer</tX></a>.</span></div>
<div>3. <tX s=0>Lägg CDn i CD-spelaren.</tX></div>
<div id="sp02" style="position: relative; left: 16px; width: 600px; padding: 0px 0px 0px 0px">
<span class="yl_small"><tX s=0>CD-spelaren kanske är inställd
att starta automatiskt och börjar spela en introduktion om Ubuntu.
Stäng i så fall av den.</tX></span></div>
4. <tX s=0>Starta om datorn.</tX>
<div class=yl_small>
<span  id="sp03" style="position: relative; left: 16px; width: 600px; _width: 650px; padding: 0px 40px 0px 0px">
<tX s=0>Om Ubuntu inte startar, ändra i</tX>
<a href="#Liten_ordlista">BIOS</a> <tX s=0>så att CD-spelaren står först i
start-ordningen</tX> ("boot-order").</span></div>
<div>5.<tX s=0> Välj alternativet "Prova Ubuntu utan att göra förändringar i din dator."</tX></div>
<div id="sp04" style="position: relative; left: 16px; width: 600px; padding: 0px 0px 0px 0px">
<span class="yl_small"><tX s=0>Ubuntu körs nu från CD-spelaren utan att påverka datorns hårddisk.
Systemet arbetar betydligt långsammare än vid en installation till hårddisken men gör att man kan se hur Ubuntu fungerar i ens egen dator.</tX>
</span></div>
6. <tX s=0>Installera eventuellt Ubuntu på hårddisken.</tX><br>

```

---

