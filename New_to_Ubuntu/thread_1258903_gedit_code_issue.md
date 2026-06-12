---
title: "gedit code issue?"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Crimm237 on 2009-09-05
Hey I'm running on an Inspiron 1100 and I've been having the same video issues everyone had been I've been looking around the forums a bit more and I found a few possible fixes for it but I end up getting blocked everytime when I run a code like...

gksudo gedit /ect/X11/xorg.conf

or

gksudo gedit /ect/apt/sources.list

I always end up with a warning or error message that says 
"GtK-WARNING **: cannot open display

I've found what I think I need to fix my video issue but I need that display to be opened to change a few settings. Anyone have an idea?

---

### Post by k33bz on 2009-09-05
try```
sudo gedit /ect/X11/xorg.conf
``` in the cli instead

---

### Post by overdrank on 2009-09-05
Hi and if you do not have a GUI then gedit will not work. You will need to use cli like nano or other.

---

### Post by corncob on 2009-09-05
That's what I was going to say.  Try:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Crimm237 on 2009-09-05
Kay well the nano command works but I got lost from there. What I'm trying to do is what it says to do in here but I'm just about as lost confused and frustrated as one can get with this.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

When I go to edit the file I'm lost I'm looking at a screen that basically in Greek to me. So I don't understand on how to reconfigure my xorg file. It tells me that "/ect/gdm/PostLogin/Default" doesn't even exist.

I've been trying to get Ubuntu to work on this computer for well over a week now. *sigh* I'm worried that by tinkering around this system it will do more harm then good. is it possible that someone can give me Simple, easy to follow and complete instructions on how to get this to work? Preferably in dumb Linux noob speak?

My computer is stuck as a vary small resolution with black bars around the sides of the scree.

I read around and I heard that something might me in the next update package to fix this? Is that true? Would ti be better to wait a month? Or... <_<    >_> should I just toss this thing out of the window and hop a car hits it before it gets the chance to hit the ground?

---

### Post by CatKiller on 2009-09-05
> **Crimm237 said:**
> My computer is stuck as a vary small resolution with black bars around the sides of the scree.


Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

> **Crimm237 said:**
> It tells me that "/**ect**/gdm/PostLogin/Default" doesn't even exist.

Pay attention to what you're typing.

---

### Post by corncob on 2009-09-06
> **Crimm237 said:**
> Kay well the nano command works but I got lost from there. 

Navigate the window with the arrow keys.  When the down arrow reaches the bottom it will also scroll the screen.  The mouse doesn't work in the nano screen  -- well if you have a scroll mouse it will scroll the screen but you need the arrow keys to place the cursor.  Control keys are at the bottom.  ^ means the ctrl key.  When you're finished editing and want to save the changes press [ctrl][o].  If you just want to exit the program without saving press [ctrl][x].  For help press [ctrl][g].  You hold down the ctrl key while pressing the other key.
As CatKiller said, its good to make a backup copy of your original xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

---

### Post by Crimm237 on 2009-09-06
Thanks, this has been a lot of help sorry for being so frustrated with Ubuntu guys. lol And I do have to say I got owned on the "etc" file path.

Well now the last thing I'm stuck on is how to find my HorizSync and VertRefresh. Also I know you can do that by finding the chip set but where, is the question. I've been looking in the system info and I can't find it. Have I been looking in the wrong place?

Thanks a bunch. =D

---

### Post by halitech on 2009-09-06
whats the output of ```
lspci
```

normally you shouldn't need to mess around with xorg as it does a pretty good job of autoconfiguring things.

---

### Post by RedRat on 2009-09-06
> **Crimm237 said:**
> Hey I'm running on an Inspiron 1100 and I've been having the same video issues everyone had been I've been looking around the forums a bit more and I found a few possible fixes for it but I end up getting blocked everytime when I run a code like...

gksudo gedit /ect/X11/xorg.conf

or

gksudo gedit /ect/apt/sources.list

I always end up with a warning or error message that says 
"GtK-WARNING **: cannot open display

I've found what I think I need to fix my video issue but I need that display to be opened to change a few settings. Anyone have an idea?

Sorry but something seems to be wrong and it may well be something with 9.04. 

I can run gedit with wither sudo or gksudo, I have done this many times in 8.04. It really should make no difference. I would suggest that you use Nautilus and go to the directory where the various files reside and see if they really exist. 

Try just running sudo gedit and then use the open folder icon and navigate to etc/apt and find sources.list

You should be able to open that file that way. I don't really see the need to run nano, unless you miss the old Vi editor of Unix.:D

---

### Post by halitech on 2009-09-06
for graphical apps you should use gksudo and not just sudo. See here

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

As far as running nano, the OP hasn't really said if they have a gui up or not so they may have to do things with nano as gedit won't run without a gui (same for nautilus)

---

### Post by RedRat on 2009-09-06
> **halitech said:**
> for graphical apps you should use gksudo and not just sudo. See here

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

As far as running nano, the OP hasn't really said if they have a gui up or not so they may have to do things with nano as gedit won't run without a gui (same for nautilus)

On my machine I can run gedit with either sudo or gksudo, both works. I did not see that said he didin't have a GUI. If he doesn't have the GDM or KDM running than he would have to use nano.

---

### Post by halitech on 2009-09-06
gedit seems to be one of the few programs that will work with sudo or gksudo but why try and figure out which will do damage and which won't? just get into the habit of using sudo from the CLI and gksudo when starting a graphical app. they haven't said they don't but haven't said they do either.

---

### Post by overdrank on 2009-09-06
I suggest nano after viewing the op's previous post.
The op also linked the [Intel Graphics in Jaunty]("http://ubuntuforums.org/showthread.php?t=1130582") :)

---

### Post by CatKiller on 2009-09-07
> **Crimm237 said:**
>  Well now the last thing I'm stuck on is how to find my HorizSync and VertRefresh. Also I know you can do that by finding the chip set but where, is the question. I've been looking in the system info and I can't find it. Have I been looking in the wrong place?

The computer doesn't know what those values are; that's kind of the point of specifying them yourself.

[This post]("http://ubuntuforums.org/showthread.php?p=6000430") suggests that ```
        HorizSync 28-80
        VertRefresh 43-60

``` are good numbers to use, but I don't know where they got those numbers from.

---

### Post by Crimm237 on 2009-09-07
What I got off of the "lspci" code for the chip set was: Intel 82845/GL

---

