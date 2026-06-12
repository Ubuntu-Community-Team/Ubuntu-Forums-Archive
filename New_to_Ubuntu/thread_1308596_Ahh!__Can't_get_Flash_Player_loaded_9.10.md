---
title: "Ahh!  Can't get Flash Player loaded 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by LoneWolf08 on 2009-10-31
Ok tried the little automatic "install missing plugings" thingy when prompted in Firefox but it tells me it can't find ANY of the packages.  What?

So then I went to Adobe Flash Player download site and pulled down ALL available options.  Followed their instructions for all.  Jack sh*t for me.

I'm fairly new to linux so I really dont know what I'm doing wrong.  Please help me abandon Apple (wanna be linux) and Windows!

---

### Post by Schendje on 2009-10-31
Easiest way to install Flash is to install the Ubuntu Restricted Extras. They're in the Software Center, or otherwise do:

```
sudo apt-get install ubuntu-restricted-extras
```

In a terminal.

It'll also install some other codecs, mp3 support, Java stuff, etc.

Welcome to Linux, btw! :D

---

### Post by X1R1 on 2009-10-31
have you installed ubuntu restricted extras package? If not go to the software center, search for it, and install. the try if your flash works :D

Schendje: Damn you typed faster than me!! lol

---

### Post by aysiu on 2009-10-31
This should help you (includes screenshots):
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by jorgevazq on 2009-10-31
> **LoneWolf08 said:**
> Ok tried the little automatic "install missing plugings" thingy when prompted in Firefox but it tells me it can't find ANY of the packages.  What?

So then I went to Adobe Flash Player download site and pulled down ALL available options.  Followed their instructions for all.  Jack sh*t for me.

I'm fairly new to linux so I really dont know what I'm doing wrong.  Please help me abandon Apple (wanna be linux) and Windows!

You should try this:

First type in your Firefox bar
" About:plugins " (whithout the quotations, the :p is actually ":"p, but the forum recognizes it as a smiley :S )

Then, locate the section Shockwave Flash (if you don't have it, better).

Here comes an IF:
    IF you have more than one flash plugins, OR you don't have the official provided by Adobe, THEN you should erase those (Synaptic may do the job).
    ELSE, you can skip to the next step.

Finally, you can go to Ubuntu Software Center (located in the Applications menu), and **find ubuntu-restricted-extras**. This package has not only flash but plenty of codecs for restrictive formats such as mp3, aac, mp4... and many more.

Hopes this helps you. :D

---

### Post by LoneWolf08 on 2009-10-31
OMG!  How easy was that!  Followed the advice to go Applications > Ubuntu Software Center > searched for "flash" and found the official Adobe Flash and basically installed it right there!  Restarted FF and it's working like a charm!

Man, I didn't think anyone would reply to me until later tonight and I look back here a half hour later and tons of replies! 

I LOVE IT!!  Thanks everyone.  I need to fire up the Terminal and learn how to use that more though huh?

---

### Post by aysiu on 2009-10-31
You don't need to learn to use the terminal, but you may want to just for fun.

---

### Post by X1R1 on 2009-10-31
terminal is pretty good if you want to do things fast, and yes you should familiarize yourself with some common commands used in Ubuntu. But ubuntu is also designed in a way that you could live and do everyday things without the terminal :D

---

### Post by LoneWolf08 on 2009-10-31
Good call **Aysiu** & **X1R1**, I think I'm gonna try to at least run the command that **Schendje** suggested.  Sounds like some important extras to have installed no?

---

### Post by aysiu on 2009-10-31
> **LoneWolf08 said:**
> Good call **Aysiu** & **X1R1**, I think I'm gonna try to at least run the command that **Schendje** suggested.  Sounds like some important extras to have installed no?
Those also can be installed through the Ubuntu Software Center. Just search for *restricted* and click to install *ubuntu-restricted-extras*.

---

### Post by LoneWolf08 on 2009-10-31
Anything else I should install that you guys can think of?  I just bumped the Visual Effects (System > Preferences > Appearance) up to **Normal** and now everything looks nice and clean!  Drop shadows too!

---

