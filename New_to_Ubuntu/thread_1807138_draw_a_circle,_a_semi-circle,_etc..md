---
title: "draw a circle, a semi-circle, etc."
date: 2011-07-18
forum: New to Ubuntu
---

### Post by mkornig on 2011-07-18
Hi there!

I'd like to draw simple geometrical objects (such as a circle, semi-circle and eventually a simple pie chart) in a jpg or png file.

I've tried gimp. But so far I haven't been able to draw a single circle.:(

Is there something simpler around (simpler to use I mean)? What application should I use?

---

### Post by Brushstroke on 2011-07-18
Try GNU Paint. 

```
sudo apt-get install gpaint
```

---

### Post by haqking on 2011-07-18
> **mkornig said:**
> Hi there!

I'd like to draw simple geometrical objects (such as a circle, semi-circle and eventually a simple pie chart) in a jpg or png file.

I've tried gimp. But so far I haven't been able to draw a single circle.:(

Is there something simpler around (simpler to use I mean)? What application should I use?


If you couldnt draw a circle in Gimp ? then i am not sure i can help you.

however you could try GNU Paint or GNOME Paint

---

### Post by robertc36 on 2011-07-18
It's the same as photoshop.
Use the ellipse tool and then stroke.
:)

---

### Post by mkornig on 2011-07-18
> **haqking said:**
> If you couldnt draw a circle in Gimp ? then i am not sure i can help you.

however you could try GNU Paint or GNOME Paint

Yes, I can't draw a circle in Gimp. And I've tried hard.

Before getting back to gimp, I'll try gpaint.

---

### Post by AlphaLexman on 2011-07-18
In my experience gimp does not have a circle drawing tool, only a circle select tool. **EDIT:** which can be converted to a path...

However, **inkscape** can draw perfect circles. You can even set the width of the outline and it's color, and the interior color or gradient.

---

### Post by SoFl W on 2011-07-18
Are you talking about a filled in circle or a hollowed out circle?  (In GIMP)

Holding down the shift key should keep the ellipse tool's aspect ratio the same. 

If you are trying to draw a hollowed out or empty circle then:
1) Create a new layer.
2) Draw your circle (holding down the shift key for the aspect ratio)
3) Fill your circle in with the color you want.
4) goto the Select menu, and select "Shrink"
5) shrink the selection by the number of pixels you wish.
6) Click "Ok"
7) press the delete key.

---

### Post by jtarin on 2011-07-18
[http://www.youtube.com/watch?v=DtniDrYoV0I&feature=related](http://www.youtube.com/watch?v=DtniDrYoV0I&feature=related)

---

### Post by alphacrucis2 on 2011-07-18
You could try an actual drawing program like inkscape.

---

### Post by decoherence on 2011-07-18
Yes, inkscape is probably what you want.

OpenOffice (or LibreOffice or whateve it is this week) also has a program called Draw which should already be there if you have Open/LibreOffice.

---

### Post by mkornig on 2011-07-19
Dear all,

Thanks for your suggestions and your help. Again, I'm impressed by the speed and the quality of the help this forum provides.

I've installed and played around with three different applications. Here are my first impressions:

[LIST]
[*]**GNU paint** (gpaint). Drawing a closed, circular line (a circle) or an ellipse of a given line width is a piece of cake. I did it within 10 seonds without reading the manual (I'm not even sure it has one). Drawing a disc (filled circle) is easy, too. It doesn't seem to have a zoom, neither an "undo last operation" facility. If you ask for a black line some of the pixels are in deed turned to black, others to various gray shades (to make a curved line look smooth?).
[*]**Inkshape** seems to be quite powerfull. Drawing circles, semi-circles, sectors and pie charts (filled or not not or with a given border color) is relatively easy. It does lots of other fancy objects, too. I did it within a few minutes (without reading the manual, an English manual is available). I haven't yet been able to produce a jpg or png file, though  (maybe for this I will have to study the manual?).
[*]I also tried **gimp**. It was acually my first choice. But I haven't found a "draw a circle" or an "ellipse" button or a similar "tool" (as some of you seem to have suggested). So I haven't been able to produce a circle, not even a simple one. Not a disk either. And I played around with gimp for some time (at least 30 minutes I think). Maybe I'm missing something... I used gimp in connection with gpaint to enlarge the drawing, to choose colors, fill a closed area with another color, etc. That worked alright. I have found a manual for gimp, but I didn't find what I was looking for in the first 5 minutes (and I still wonder whether or not gimp can actually do what I want). Perhaps experienced gimp users will laugh at me (and produce a nice circle within 5 secons). But this is MY first impression.
[/LIST]
Cheers, Martin

---

### Post by haqking on 2011-07-19
Yeah it can be done in GIMP in no problems but for simple vector graphics there are easier programs such as the ones been suggested.

Gnu Pint
Gnome Paint
Inkscape 

are all easier for your needs.

have fun

---

### Post by mkornig on 2011-07-19
> **haqking said:**
> Yeah it can be done in GIMP in no problems but for simple vector graphics there are easier programs such as the ones been suggested.

Gnu Pint
Gnome Paint
Inkscape 

are all easier for your needs.

have fun

Where could I find Gnome Paint? Is it different from GNU Paint?

---

### Post by mkornig on 2011-07-19
> **jtarin said:**
> [http://www.youtube.com/watch?v=DtniDrYoV0I&feature=related](http://www.youtube.com/watch?v=DtniDrYoV0I&feature=related)

Hi jtarin,

I checked out this youtube link. Acually I watched the video twice. But I still can't draw a circle in gimp. Mouse clicks and movements are too fast for me and the video doesn't have sound :(

Thanks for your help anyway.

---

### Post by alphacrucis2 on 2011-07-19
> **mkornig said:**
> Dear all,

Thanks for your suggestions and your help. Again, I'm impressed by the speed and the quality of the help this forum provides.

I've installed and played around with three different applications. Here are my first impressions:

[LIST]
[*]**GNU paint** (gpaint). Drawing a closed, circular line (a circle) or an ellipse of a given line width is a piece of cake. I did it within 10 seonds without reading the manual (I'm not even sure it has one). Drawing a disc (filled circle) is easy, too. It doesn't seem to have a zoom, neither an "undo last operation" facility. If you ask for a black line some of the pixels are in deed turned to black, others to various gray shades (to make a curved line look smooth?).
[*]**Inkshape** seems to be quite powerfull. Drawing circles, semi-circles, sectors and pie charts (filled or not not or with a given border color) is relatively easy. It does lots of other fancy objects, too. I did it within a few minutes (without reading the manual, an English manual is available). I haven't yet been able to produce a jpg or png file, though  (maybe for this I will have to study the manual?).
[*]I also tried **gimp**. It was acually my first choice. But I haven't found a "draw a circle" or an "ellipse" button or a similar "tool" (as some of you seem to have suggested). So I haven't been able to produce a circle, not even a simple one. Not a disk either. And I played around with gimp for some time (at least 30 minutes I think). Maybe I'm missing something... I used gimp in connection with gpaint to enlarge the drawing, to choose colors, fill a closed area with another color, etc. That worked alright. I have found a manual for gimp, but I didn't find what I was looking for in the first 5 minutes (and I still wonder whether or not gimp can actually do what I want). Perhaps experienced gimp users will laugh at me (and produce a nice circle within 5 secons). But this is MY first impression.
[/LIST]
Cheers, Martin

Inkscape allows save as png.

---

### Post by haqking on 2011-07-19
> **mkornig said:**
> Where could I find Gnome Paint? Is it different from GNU Paint?


yeah they are both and with lots of others in the software centre.

just type paint, there are a few.

GNU Paint and Gnome Paint Drawing Editor etc etc

---

### Post by jtarin on 2011-07-19
> **mkornig said:**
> Hi jtarin,

I checked out this youtube link. Acually I watched the video twice. But I still can't draw a circle in gimp. Mouse clicks and movements are too fast for me and the video doesn't have sound :(

Thanks for your help anyway.If you hover over the different tools in the Gimp it will tell you what they are....you want the [Ellipse Tool]("http://docs.gimp.org/2.6/en/gimp-tool-ellipse-select.html"). Top row,second from the left.
[http://docs.gimp.org/2.6/en/](http://docs.gimp.org/2.6/en/)

---

### Post by 23dornot23d on 2011-07-19
This link may help too it has step by step instructions and written explanations as to what tools do ..... [http://en.linuxreviews.org/GIMP](http://en.linuxreviews.org/GIMP)

But as already pointed out ..... GIMP is maybe not the best tool of choice for this
as Gimp is a Image manipulation tool mainly for photos etc ..... 

Inkscape or Xaralx are for designs and creating things which then can be transferred into GIMP if you want.

Inkscape Xaralx even a cad program like Qcad/Librecad (or Draftsight) for circles depending on what you are trying to create and what you want to use it in ......

Most circles created in any of the above programs  [[COLOR=Red]_***can be transferred from one program to another too either as a svg or bmp or jpg***_[/COLOR]]("http://img813.imageshack.us/img813/349/screenshot5qf.jpg") ...... or many others .....

The best way is svg as it is scalable and keeps the nice accurate edge display to it .....

There are many videos too ..... 

I just did a quick scan in [[COLOR=Red]_***google on Gimp and create a circle***_[/COLOR]]("http://www.google.com/search?client=ubuntu&channel=fs&q=gimp+circle+video&ie=utf-8&oe=utf-8") and there are ones with sound too .....

---

### Post by fractalman on 2011-07-19
You can draw circles in gimp using the shape paths plug in

[http://registry.gimp.org/node/59](http://registry.gimp.org/node/59)

just download the .scm file and put it in gimp>scripts folder.

you can find it under script fu >shape paths

you can also get a two tone shape grids plug in that will render a grid of shapes, just set it to 1 shape x 1 shape and you can get a circle

---

### Post by SoFl W on 2011-07-19
mkornig

Did you try my instructions at post #7?
That is how I draw circles, using the elipse tool, as I am drawing I press the shift key to keep the aspect ratio the same.

---

### Post by mkornig on 2011-07-20
Thanks everybody for your help and suggestions.

I can now draw a circle with various applications. Even in gimp..

I'am going to declare this subject as closed now.

Cheers, mkornig

---

### Post by jtarin on 2011-07-20
> **mkornig said:**
> Thanks everybody for your help and suggestions.

I can now draw a circle with various applications. Even in gimp..

I'am going to declare this subject as closed now.

Cheers, mkornigMark this one as solved by using thread tools at the top of the page.
Now open one up for drawing a square.:P

---

