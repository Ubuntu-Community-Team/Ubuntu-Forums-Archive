---
title: "Gif animator?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2011-03-28
Hi guys.
I'm currently in need of a gif animator.
I always try to find an open source solution that works in both windows and ubuntu.
Can anyone recommend me a gif animator that works in both.
I've found a few free closed source programs that get the job donebut I'd prefer a cross platform open solution. 
Any thoughts?

---

### Post by kellemes on 2011-03-28
[The Gimp]("http://www.gimp.org/") is cross-platform and able to create animated gifs, I know for Windows there are 'easier' solutions but The Gimp is very powerfull.

One of many howto's..
[http://graphicssoft.about.com/od/gimptutorials/tp/animated-gif.htm]("http://graphicssoft.about.com/od/gimptutorials/tp/animated-gif.htm")

---

### Post by bigmonmulgrew on 2011-03-28
> **kellemes said:**
> [The Gimp]("http://www.gimp.org/") is cross-platform and able to create animated gifs, I know for Windows there are 'easier' solutions but The Gimp is very powerfull.

One of many howto's..
[http://graphicssoft.about.com/od/gimptutorials/tp/animated-gif.htm]("http://graphicssoft.about.com/od/gimptutorials/tp/animated-gif.htm")

Thanks for the quick reply. I'll take a look at that. I've used GIMP briefly before but I didnt know it could do animated gifs.

---

### Post by Perfect Storm on 2011-03-28
To make a .gif with gimp, you'll work in layers. So you'll add a new layer for the next drawing of the .gif

Layer ---> New Layer

You can edit each layer to tell it the speed of each layer. Right click on selected layer (in the Layers, Channels Window) and click 'Edit Layer Attributes'.

Give each layer a name (optional) and add afterwards (XXXXms) for speed.

---

### Post by bigmonmulgrew on 2011-03-28
Thanks for the info guys. GIMP will do nicely.
Marked as Solved
I've also emailed the link to the missus, shes the one whos really going to be using it for her cake making website we've just made. I just needed to crop a gif that had an overly large background.

---

### Post by SeijiSensei on 2011-03-28
Couple of other hints for using GIMP to make animations.

Considering installing GAP, the GIMP extensions for animation.  Just install the "gimp-gap" package from the repositories.

Also I've found that using Filters > Animation > Optimize for GIF can sometimes create a smaller, more optimized file than simply using Save AS and choosing the GIF extension.  The Filter seems to do a better job of differencing the frames.

Try to keep the background fairly static so that a large proportion of the pixels remain constant from frame to frame.  A shot from above of your wife stirring a mixing bowl will compress nicely.  A shot of a busy street corner will not.

---

