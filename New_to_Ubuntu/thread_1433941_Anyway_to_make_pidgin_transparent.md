---
title: "Anyway to make pidgin transparent?"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by razorseal on 2010-03-19
I remember when I had my mac, in adium you can make adium transparent and almost like part of the background.... it looked so awesome.... is there a way to do this with pidgin?

---

### Post by tom.swartz07 on 2010-03-19
> **razorseal said:**
> I remember when I had my mac, in adium you can make adium transparent and almost like part of the background.... it looked so awesome.... is there a way to do this with pidgin?

If you install Compiz Config Settings Manager from the software center, you could configure that specific window to be transparent. 


If you need detailed help how to set that window transparent, let me know.

---

### Post by razorseal on 2010-03-19
> **tom.swartz07 said:**
> If you install Compiz Config Settings Manager from the software center, you could configure that specific window to be transparent. 


If you need detailed help how to set that window transparent, let me know.

problem is, if you do that, not only will the window be transparent, but everything else will too... I just want the background transparent but the usernames opaque so it looks like the usernames are floating on the desktop background

---

### Post by ankspo71 on 2010-03-19
I think there are some conky configurations and conky scripts that will allow you to do that.

[http://www.ipodtouchfans.com/forums/imgcache2/35659.png](http://www.ipodtouchfans.com/forums/imgcache2/35659.png)
[http://media.photobucket.com/image/conky%20pidgin/blogwork/screenshot-1.jpg]("http://media.photobucket.com/image/conky%20pidgin/blogwork/screenshot-1.jpg")

I saw those by searching google for [ conky pidgin ]. Many of the results linked back to here.

---

### Post by razorseal on 2010-03-19
Those look awesome, how do I get it?

---

### Post by razorseal on 2010-03-19
OK, I just DL'd conky... where do I access it? I don't see it in preferences or anything

---

### Post by ankspo71 on 2010-03-19
Hi,
To start conky, press Alt+F2 then type conky .
To have it start automatically, you will need to create a start up entry for it in
System > Preferences > Startup Applications.
Name: Conky
Command: conky

The next part is customization: 
You will probably need to borrow ideas from other posters from this link. [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
There are also alot of people on the internet that show their conky configurations.

Unfortunately, Conky doesn't display right on my computer, and I don't have much experience with it... so I won't be of much more help. In fact, I need to head back to my conky bug report tonight and let them know the problem (only on my computer) still exists.

For documentation see the links named:

[LIST]
[*][Official  Conky Wiki.]("http://wiki.conky.be/index.php/Main_Page")
[*]View the Conky [man page (1.7.2)]("http://conky.sourceforge.net/docs.html").
[*]View the Conky [FAQ]("http://conky.sourceforge.net/faq.html").
[*]Pretty table of Conky [variables (1.7.2)]("http://conky.sourceforge.net/variables.html").
[*]Pretty table of Conky [config file settings (1.7.2)]("http://conky.sourceforge.net/config_settings.html").
[*]Pretty table of the Conky [Lua API (1.7.2)]("http://conky.sourceforge.net/lua.html").
[*]View the [changelog (1.7.2)]("http://conky.sourceforge.net/changelog.html").
[/LIST]
at [http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

Hope this gets you started. ;)

---

### Post by razorseal on 2010-03-20
Thanks! but how do I customize it? where are the settings?

and how do I quit it? lol

---

### Post by tom.swartz07 on 2010-03-20
> **razorseal said:**
> Thanks! but how do I customize it? where are the settings?

and how do I quit it? lol

The settings are all programming (code) based in a config file. If you look in your home folder there should be a hidden file called .conkyrc

This file has all of the settings in it, you could hit the link at the bottom of my signature to see a guide on how my conky is set up.


You can close conky by running 

```
killall conky
``` from the terminal

---

### Post by razorseal on 2010-03-21
I just looked in my home folder, with view hidden files, there is no .conky there =/

---

