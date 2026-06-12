---
title: "what theme is this??"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by finer recliner on 2009-03-08
does any one know what window border theme this is:

[IMG]http://www.gnome-look.org/CONTENT/content-pre3/42755-3.jpg


thanks!

---

### Post by namegame on 2009-03-08
I'm not exactly sure, but I believe that's an Emerald theme with a name like "Capuccino." I might be wrong, I haven't used Emerald/compiz in months.

---

### Post by finer recliner on 2009-03-08
> **namegame said:**
> I'm not exactly sure, but I believe that's an Emerald theme with a name like "Capuccino." I might be wrong, I haven't used Emerald/compiz in months.

was this what you were thinking of:

[http://www.gnome-look.org/content/show.php/Art+Of+Cappuccino+Emerald+Theme?content=64309](http://www.gnome-look.org/content/show.php/Art+Of+Cappuccino+Emerald+Theme?content=64309)

it doesnt appear to be what i was looking for, but thanks for trying

---

### Post by Helios1276 on 2009-03-08
The answer just may be in the picture...[http://www.cimitan.com/murrine/](http://www.cimitan.com/murrine/)

---

### Post by finer recliner on 2009-03-08
> **Helios1276 said:**
> The answer just may be in the picture...[http://www.cimitan.com/murrine/](http://www.cimitan.com/murrine/)

well...murrine is a gtk engine, not a theme. plus i'm looking for the theme for the *window border* (i.e. the close, minimize, maximize button stuff), as i stated in the original post. thanks though.

---

### Post by blueridgedog on 2009-03-08
Since the image is hosted at gnome-look, I suggest you just start combing through the themes:

[http://www.gnome-look.org/CONTENT/content-pre3/42755-3.jpg](http://www.gnome-look.org/CONTENT/content-pre3/42755-3.jpg)

---

### Post by Sarai the Geek on 2009-03-08
Here it is:
[http://www.gnome-look.org/content/show.php/Murrine+GTK2+Cairo+Engine?content=42755](http://www.gnome-look.org/content/show.php/Murrine+GTK2+Cairo+Engine?content=42755)

Took me a few seconds to find. Google really is your friend. There is an included metacity theme that is presumably the window manager theme used in the screenshot. :D

---

### Post by damis648 on 2009-03-08
Whoa, how is GTK transparent in that screenshot? (I know it is not compiz, because other elements are solid)

---

### Post by Gp. on 2009-03-08
It uses Murrine (A GTK engine)
[http://www.cimitan.com/murrine/project/murrine](http://www.cimitan.com/murrine/project/murrine)

---

### Post by stchman on 2009-03-08
I believe that is a Linux Mint theme called Cassandra with different borders.

---

### Post by damis648 on 2009-03-08
> **Gp. said:**
> It uses Murrine (A GTK engine)
[http://www.cimitan.com/murrine/project/murrine](http://www.cimitan.com/murrine/project/murrine)

I got that, but I can't get it to work... they stay solid.

EDIT: I should say I have installed Murrina configurator, but the configurator shows no themes. (I know i have several murinna themes installed)... any ideas?

---

### Post by LowSky on 2009-03-08
It compiz with emerald

```
sudo apt-get install emerald
```

[IMG]http://www.gnome-look.org/CONTENT/content-pre1/44063-1.png[/IMG]

---

### Post by Gp. on 2009-03-09
> **damis648 said:**
> I got that, but I can't get it to work... they stay solid.

EDIT: I should say I have installed Murrina configurator, but the configurator shows no themes. (I know i have several murinna themes installed)... any ideas?

I don't think Murrine modifies the window borders.

That's all done with emerald and compiz.

Murrine is more of a control themer, I think? I'm confused on it as well lol


By the way, the themes go into the .themes folder. I had to install them manually.

**BTW LOW SKY, DO YOU KNOW WHAT EMERALD THEME IT IS HE'S ASKING FOR IN THE PICTURE?**

---

### Post by damis648 on 2009-03-09
> **LowSky said:**
> It compiz with emerald

```
sudo apt-get install emerald
```

[IMG]http://www.gnome-look.org/CONTENT/content-pre1/44063-1.png[/IMG]

Um... not what I meant.
Yes, I know about and use emerald daily. Great decorator. What I am referring to is how GTK elements are also transparent in that screenshot, like Vista.

---

### Post by sasquatch74 on 2009-03-09
^Yeah, the transparent controls caught my eye too.
A quote from Cimi's Murrine page on gnome-look:
The Future:
A transparent version (like Vista but faster and nicer ;) ) is under development!

So looks like we have to wait to get it.

---

### Post by namegame on 2009-03-10
> **finer recliner said:**
> was this what you were thinking of:


No. More like this:

Here:
[http://gnome-look.org/content/show.php/Capuccino+for+cgwd+(quinn+compiz)?content=43780](http://gnome-look.org/content/show.php/Capuccino+for+cgwd+(quinn+compiz)?content=43780)

---

### Post by Giant Speck on 2009-03-10
The screenshot is originally from here:

[http://www.gnome-look.org/content/show.php?content=42755](http://www.gnome-look.org/content/show.php?content=42755)

However, I cannot figure out what specific theme it is.  And as for the transparent effects, I guess it's something Cimi is working on.  I didn't even know he was working on something like that.  Now I can't wait!

---

### Post by damis648 on 2009-03-10
> **giant speck said:**
> and as for the transparent effects, i guess it's something cimi is working on.  I didn't even know he was working on something like that.  Now i can't wait!

+1

---

### Post by finer recliner on 2009-03-13
alright. there were a couple misunderstands and some tangents in this thread, but i finally got what i wanted (the window buttons to look like the ones in my OP, i.e. the minimize, maximize and exit buttons)

steps:

1) enable compiz fusion effects (system > preferences > appearance > visual effects tab > normal)
2) install emarald theme manager (apt-get install emerald)
3) install the compiz fusion icon (apt-get install fusion-icon)
4) run the fusion icon which lets your quickly change compiz and window manager settings. right click the icon and set emerald as your window decorator.

done-- enjoy!

---

