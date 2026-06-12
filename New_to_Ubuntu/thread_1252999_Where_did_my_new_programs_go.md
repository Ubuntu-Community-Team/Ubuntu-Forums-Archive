---
title: "Where did my new programs go?"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-29
I downloaded some new programs through both:  a) synaptic and b) the add / remove menu under "Applications".

Some appear in my menu after download / install but some do not.  I have checked the "System - Preferences - Main Menu" to add them, but they even are not there.

Surely I can't be the first person to whom this has happened.  Are there any resources on this?  It is probably something very simple.

Thanks.

---

### Post by Bachstelze on 2009-08-29
Can you give precise examples? Which programs did you install?

---

### Post by cat2005 on 2009-08-29
> **HymnToLife said:**
> Can you give precise examples? Which programs did you install?

There are several whose names I can not remember, but one I do remember:  imagemagick

from synaptic

---

### Post by Bachstelze on 2009-08-29
> **cat2005 said:**
> There are several whose names I can not remember, but one I do remember:  imagemagick

from synaptic

ImageMagick is a command-line utility, so you have to run it from there. The same probably goes for the other programs you installed.

---

### Post by donkyhotay on 2009-08-29
Only GUI based programs will ever show up in the applications menu. 99% of the time you install a program with synaptic and it doesn't show up it's a CLI only program.

---

### Post by nothingspecial on 2009-08-29
You launch ImageMagic by opening a terminal and typing
```

covert
``` followed by what you want to convert, then what you want to convert it to. Or one of another options.

Open a terminal and type ```
man ImageMagick
``` for instructions.

---

### Post by cat2005 on 2009-08-29
This is from the synaptic description (emphasis added):

ImageMagick is a software suite to create, edit, and compose bitmap images.
It can read, convert and write images in a variety of formats (over 100)
including DPX, EXR, GIF, JPEG, JPEG-2000, PDF, PhotoCD, PNG, Postscript,
SVG, and TIFF. Use ImageMagick to translate, flip, mirror, rotate, scale,
shear and transform images, adjust image colors, apply various special
effects, or draw text, lines, polygons, ellipses and Bézier curves.
[I]All manipulations can be achieved through shell commands as well as through
an X11 graphical interface (display).[/I]

That makes me think there is a gui somewhere.  Am I correct?

---

### Post by cat2005 on 2009-08-29
> **nothingspecial said:**
> You launch ImageMagic by opening a terminal and typing
```

covert
``` followed by what you want to convert, then what you want to convert it to. Or one of another options.

Open a terminal and type ```
man ImageMagick
``` for instructions.


What does "convert" mean?  Does that make it have a gui?

---

### Post by wojox on 2009-08-29
Try opening Synaptic and search 

```
ImageMagick
```

Look for anything that says GUI or Interface.

---

### Post by Bachstelze on 2009-08-29
> **cat2005 said:**
> 
That makes me think there is a gui somewhere.  Am I correct?

What part of "ImageMagick is a command-line program" do you not understand? You're probably looking for GIMP.

---

### Post by SunnyRabbiera on 2009-08-29
Some apps like imageshack wont have menu entries as its commandline, some might have GUI's but sometimes mess up in the menu entries.
Again I will ask what did you try to install, imageshack is one what are the others?

---

### Post by cat2005 on 2009-08-29
> **SunnyRabbiera said:**
> Some apps like imageshack wont have menu entries as its commandline, some might have GUI's but sometimes mess up in the menu entries.
Again I will ask what did you try to install, imageshack is one what are the others?


Thank you SunnyRabbiera.

Unfortunately, that is the only program whose name I remember.  I am looking for an alternative to "gimp" to do basic - intermediate level photo editing.  GIMP is nice but cumbersome.

Do you have any suggestions?

Thanks.

---

### Post by SunnyRabbiera on 2009-08-29
> **cat2005 said:**
> Thank you SunnyRabbiera.

Unfortunately, that is the only program whose name I remember.  I am looking for an alternative to "gimp" to do basic - intermediate level photo editing.  GIMP is nice but cumbersome.

Do you have any suggestions?

Thanks.

Gimp is pretty much it for fairly decent image editing, but if you are looking for a MSpaint clone well...
More then likely you installed some CLI apps, some apps on linux use commandline, some dont and use a GUI.
Linux can be a little more commandline oriented then Windows or OSX, most people will give you instructions on how to do something using commandline.
There are a few main reasons for this:
1: its just easier for some people to give CLI instructions on how to do something, I try to give out GUI instructions when possible.
2: there is a lot of GUI tools out there and different interfaces, so commandline instuctions and apps are sometimes preferred.
3: GUI in linux is still relatively new compared to Windows, but its getting better each day.

---

### Post by nothingspecial on 2009-08-29
> **cat2005 said:**
> What does "convert" mean?  Does that make it have a gui?
```


ImageMagick includes a number of command-line utilities for  manipulat&#8208;
       ing  images. Most of you are probably accustom to editing images one at
       a time with a graphical user interface (GUI) with such programs as gimp
       or Photoshop. However, a GUI is not always convenient. Suppose you want
       to process an image dynamically from a web script or you want to  apply
       the  same  operations  to many images or repeat a specific operation at
       different times to the same or different  image.  For  these  types  of
       operations, the command-line image processing utility is appropriate.

```

---

### Post by Norm24 on 2009-08-29
> **cat2005 said:**
> [I]All manipulations can be achieved through shell commands as well as through
an X11 graphical interface (display).[/I]

That makes me think there is a gui somewhere.  Am I correct?

My thought exactly but HymnToLife from his response thinks you're a moron for assuming there's a GUI?

HTL,as forums staff don't ya think you could've been a little more tactful?

Quoting you:
"What part of "ImageMagick is a command-line program" do you not understand?"

Did you not see the X11 grahical interface reference in the description?The average person would take that as meaning a GUI.Shame on you for lambasting the guy!A nice courteous answer would've been more appropriate.

---

### Post by Bachstelze on 2009-08-29
> **Norm24 said:**
> My thought exactly but HymnToLife from his response thinks you're a moron for assuming there's a GUI?


No. I said ImageMagick was a command-line utility (rather, it is a collection of comand-line utilities, but that is irrelevant to the point). cat2005 seemed to not understand that, so I asked what exactly he did not understand. I don't see where I called anyone a "moron". New users sometimes don't understand things that more advanced users take for granted, that's just normal.

---

### Post by Bachstelze on 2009-08-29
> **SunnyRabbiera said:**
> Gimp is pretty much it for fairly decent image editing, but if you are looking for a MSpaint clone well...

There's Xpaint, KolourPaint, TuxPaint, and probably a few others.

---

### Post by SunnyRabbiera on 2009-08-29
> **HymnToLife said:**
> There's Xpaint, KolourPaint, TuxPaint, and probably a few others.

Yeh I was guing to suggest them soon, though I rather use gimp as MSpaint is so primitive...

---

### Post by nothingspecial on 2009-08-29
I think, from reading back, I might have sounded a bit short too.

I appologise and would recommend gimp too.

It can seem a little heavy but it will accomplish pretty much everything you want to do..........

........or atleast anything I`ve ever wanted to do - I`m not clever enough to use it fully.

---

