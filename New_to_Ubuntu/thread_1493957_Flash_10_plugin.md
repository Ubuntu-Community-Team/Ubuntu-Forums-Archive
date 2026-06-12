---
title: "Flash 10 plugin"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by maryalesia on 2010-05-26
Hey guys!

I just installed Kubuntu 10.04 onto my gateway FX series laptop because I was too lazy to figure out how to delete harddrive partitions and get windows off my system. I now have an all-linux laptop! 

I've never used kubuntu before, so I'm still in the confusing phase where I figure out the UI. Please bear with me. 

It took me forever to get the flash plugin to work in Google Chrome when I was using Ubuntu. I'm not sure what I did; it just started working one day. Very random. Anyway, now that I'm in kubuntu, it appears that I will have to do the whole thing over again. When I tried to download the plugin off of the website, I received this error message:

Unknown channel '$distro-partner'

I have no idea what this means. Also, I can't tell if it works in firefox, because all I have in applications "mozilla firefox install browser", and when I run that I get a message saying that the packages are already installed. :confused:

Any ideas? 

Also, how do I get to the ubuntu software center in kubuntu? 

help would be much appreciated!!

---

### Post by mikewhatever on 2010-05-26
Why don't you just search for 'flash' in Kubuntu's package manager and install from the repositories. CLI should also work:

sudo apt-get install flashplugin-installer

---

### Post by uRock on 2010-05-26
The flash link in my signature should get you up and running properly.

---

### Post by maryalesia on 2010-05-26
> **uRock said:**
> The flash link in my signature should get you up and running properly.

When I right click the package, "properties" is not one of the available options. :confused:

---

### Post by Viau on 2010-05-26
have you tried the flash addon for firefox? I have installed it for my chrome and its working really fine.

---

### Post by maryalesia on 2010-05-26
> **Viau said:**
> have you tried the flash addon for firefox? I have installed it for my chrome and its working really fine.

O.o No, I haven't. Could you explain how?:)

---

### Post by uRock on 2010-05-26
WHen I ran it, I placed it in my Home folder then ran ```
chmod +x adobe_tools-kubuntu*
``` then ```
./adobe_tools-kubuntu*
```Running those will start the app, then just follow the directions in the link to get the right Flash installed.

---

### Post by Viau on 2010-05-26
> **maryalesia said:**
> O.o No, I haven't. Could you explain how?:)

Have you tried this?

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by lovinglinux on 2010-05-26
> **maryalesia said:**
> O.o No, I haven't. Could you explain how?:)

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by andrewthomas on 2010-09-25
[http://ubuntuforums.org/showpost.php?p=9889479&postcount=3](http://ubuntuforums.org/showpost.php?p=9889479&postcount=3)

---

