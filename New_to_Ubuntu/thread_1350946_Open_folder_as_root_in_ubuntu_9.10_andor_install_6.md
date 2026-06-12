---
title: "Open folder as root in ubuntu 9.10 and/or install 64-bit flash."
date: 2009-12-09
forum: New to Ubuntu
---

### Post by bix15 on 2009-12-09
I'm pretty darn new to ubuntu, and just linux in general.
I'm trying to install flash on my 64-bit ubuntu as a firefox plugin.
sooooo..... I need to open the following folder, /filesystem/usr/lib/mozilla 
as root so that I can drag and drop my libflashplayer.so file into the mozilla plugins folder. I've tried this normally and I now know that I need to open it as root. 
How do I do this??

P.S. If you guys have any other way for me to install flash on my system I will gladly take answers! I just want to watch my youtube videos and chat on facebook and I've noticed that I can watch youtube videos and click play/pause. BUT when I want to chat on facebook through the IM client, when I try to click in the textbox to type somthing, I can't.

Thank you for your help!!

---

### Post by tom.swartz07 on 2009-12-09
> **bix15 said:**
> I'm pretty darn new to ubuntu, and just linux in general.
I'm trying to install flash on my 64-bit ubuntu as a firefox plugin.
sooooo..... I need to open the following folder, /filesystem/usr/lib/mozilla 
as root so that I can drag and drop my libflashplayer.so file into the mozilla plugins folder. I've tried this normally and I now know that I need to open it as root. 
How do I do this??

P.S. If you guys have any other way for me to install flash on my system I will gladly take answers! I just want to watch my youtube videos and chat on facebook and I've noticed that I can watch youtube videos and click play/pause. BUT when I want to chat on facebook through the IM client, when I try to click in the textbox to type somthing, I can't.

Thank you for your help!!

Hey-o.

hit ALT+F2 and type gksu nautilus /usr/lib/mozilla/plugins/

Be careful, unless you know the path exactly, you might be better off using gksu nautilus / 
and then navigating to the folder from there.

The problems youre talking about with not being able to click, I have them too- I found out that if you middle click, hold it, and then left click on what you need it works. It might be a bug for flash, we shall see....

---

### Post by audiomick on 2009-12-09
if you do
```
sudo nautilus
```
you will get a file manager with root privliges, and should be able to alter the file you are talking about,
**_but_**
you shouldn't have to do it that way.

The following (is a lot but) should privide some useful reading:
[http://ubuntuforums.org/showthread.php?t=1310795](http://ubuntuforums.org/showthread.php?t=1310795)
[http://ubuntuforums.org/showthread.php?t=1325659](http://ubuntuforums.org/showthread.php?t=1325659)
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by sandyd on 2009-12-09
> **bix15 said:**
> I'm pretty darn new to ubuntu, and just linux in general.
I'm trying to install flash on my 64-bit ubuntu as a firefox plugin.
sooooo..... I need to open the following folder, /filesystem/usr/lib/mozilla 
as root so that I can drag and drop my libflashplayer.so file into the mozilla plugins folder. I've tried this normally and I now know that I need to open it as root. 
How do I do this??

P.S. If you guys have any other way for me to install flash on my system I will gladly take answers! I just want to watch my youtube videos and chat on facebook and I've noticed that I can watch youtube videos and click play/pause. BUT when I want to chat on facebook through the IM client, when I try to click in the textbox to type somthing, I can't.

Thank you for your help!!
see link in my signature 
then, look at the x64bit without nspluginwrapper section

or, if it really doesn't work, run
```
sudo rm /usr/lib/firefox/plugins/libflashplayer.so
```

and follow the 32 bit instructions which is.....```
sudo apt-get install flashplugin-installer
```
or simply download the deb from the adobe site (make sure your downloading the 9.04+ version, or your gunna have trouble.....

---

### Post by bix15 on 2009-12-09
> **tom.swartz07 said:**
> Hey-o.

hit ALT+F2 and type gksu nautilus /usr/lib/mozilla/plugins/

Be careful, unless you know the path exactly, you might be better off using gksu nautilus / 
and then navigating to the folder from there.

The problems youre talking about with not being able to click, I have them too- I found out that if you middle click, hold it, and then left click on what you need it works. It might be a bug for flash, we shall see....
ok sweet thanks a lot!
I got flash working in just about 30  seconds. easy peasy!

now with the middle click solution that you gave me, i've got a laptop.....I don't think I can middle click. Can I? O_o

---

### Post by tom.swartz07 on 2009-12-10
> **bix15 said:**
> ok sweet thanks a lot!
I got flash working in just about 30  seconds. easy peasy!

now with the middle click solution that you gave me, i've got a laptop.....I don't think I can middle click. Can I? O_o

HAHA, actually, you can- believe it or not.
if you hold the two buttons down, thats considered a 'middle click' then you could tap the touchpad to click.


Just as an interesting side note, I updated the x64 flash player, step by step according to this guide:[http://www.omgubuntu.co.uk/2009/12/adobe-flash-64bit-refresh-available-for.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Reader]("http://www.omgubuntu.co.uk/2009/12/adobe-flash-64bit-refresh-available-for.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Reader")
and it restored my ability to click regularly in the flash applications.


Its worth a shot if you find it difficult to middle click and tap at once.

---

