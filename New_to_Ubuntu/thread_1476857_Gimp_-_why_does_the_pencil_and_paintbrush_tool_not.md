---
title: "Gimp - why does the pencil and paintbrush tool not work - sometiimes ???"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by cwmoser on 2010-05-08
Starting to use GIMP.

When I start a new image, I can use the pencil and paintbrush tool just fine.  After I do some stuff like adding some layers, I can create lines on the layers but later the pencil and paintbrush tool no longer works.

Is this a bug or have I got Gimp in some mode that is preventing this???

Carl

---

### Post by lukjad on 2010-05-08
Because you are not selecting the right layer to draw on. You need to show the layers pannel (Ctrl+L) and select the layer you want to draw on. If you want to draw on multiple layers, you need to create a new, clear layer and draw on it.

---

### Post by commanderzhao on 2010-05-08
I have used both ubuntu and gimp for a long time
so if you have a bunch of white layers and you have the bottom layer(background layer)selected. it will draw on that.
 and to see it you click the eyes on all of the added layers and you can see it

---

### Post by cwmoser on 2010-05-08
Here is the file that I cannot draw a line on:
[http://www.Cerant.com/RADIOS/SD-2.XCF](http://www.Cerant.com/RADIOS/SD-2.XCF)

When I attempt to draw a line, the starting dot is hollow blank.
I cannot get the line to draw.

Can you note why its keeping from doing this?

Thanks

Carl

---

### Post by cwmoser on 2010-05-09
I hide all layers except for one and tried to draw but still would not.  Tried it for all layers this way and still will not allow me to draw on any layer.

Carl


> **commanderzhao said:**
> I have used both ubuntu and gimp for a long time
so if you have a bunch of white layers and you have the bottom layer(background layer)selected. it will draw on that.
 and to see it you click the eyes on all of the added layers and you can see it

---

### Post by AlphaLexman on 2010-05-09
Just downloaded your file.

There is a small selected area on the 'Lines' layer. It is obscured by the alpha channel and is hard to see. I could draw inside the selection only. 

Go to menu -> Select, None and you will be able to draw lines.

---

### Post by SKhan on 2010-05-09
I also can't use pencil tool after using text tool. because after using text tool the text is selected so pencil tool can't work outside the selection. I don't know how to deselect the text. Ctrl+Shift+A doesn't work here.

---

### Post by cwmoser on 2010-05-09
OMG, thanks.  I pulled my hair out trying to figure this out.
Thanks much.

Carl

> **AlphaLexman said:**
> Just downloaded your file.

There is a small selected area on the 'Lines' layer. It is obscured by the alpha channel and is hard to see. I could draw inside the selection only. 

Go to menu -> Select, None and you will be able to draw lines.

---

### Post by PBKN on 2012-08-31
> **AlphaLexman said:**
> Just downloaded your file.

There is a small selected area on the 'Lines' layer. It is obscured by the alpha channel and is hard to see. I could draw inside the selection only. 

Go to menu -> Select, None and you will be able to draw lines.


Last two days I had this same problem,but now its rectified.  Thanks man.

---

