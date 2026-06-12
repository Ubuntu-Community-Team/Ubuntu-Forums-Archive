---
title: "[SOLVED] Firefox and flash files"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Selphy on 2008-12-23
This is a really silly issue I'm having and it seems like I'm just missing some simple fix. I've been having a problem with firefox and .swf files embedded into websites. It seems to have a knack for not auto loading them and instead displaying a big gray box with a "play" triangle that once clicked loads the flash file. This is really irritating and seems to cause issues specifically on embedded movie players. Anyone know how I can set up a preference to auto load flash content? 

Thanks!

---

### Post by 73ckn797 on 2008-12-23
> **Selphy said:**
> This is a really silly issue I'm having and it seems like I'm just missing some simple fix. I've been having a problem with firefox and .swf files embedded into websites. It seems to have a knack for not auto loading them and instead displaying a big gray box with a "play" triangle that once clicked loads the flash file. This is really irritating and seems to cause issues specifically on embedded movie players. Anyone know how I can set up a preference to auto load flash content? 

Thanks!

What version of flash are you running, in what version of Ubuntu; ie ... 8.04, 8.10, 64 or 32 bit?


I have no problems running the non-free flash.

---

### Post by LastWho on 2008-12-23
hi 73ckn797
i m a newbee, but why don't we suggest to him to install the adobe flash player! it works for everyone all the time, and its prettier!

in a terminal:

```
sudo apt-get autoremove flashplugin-nonfree 
```

Download and install the .deb version of adobe flash player from here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Selphy on 2008-12-23
> **73ckn797 said:**
> What version of flash are you running, in what version of Ubuntu; ie ... 8.04, 8.10, 64 or 32 bit?


I have no problems running the non-free flash.

Ubuntu 8.04 32bit latest version of non-free flash player (not sure on the exact version number but I just installed it a few days ago)

---

### Post by 73ckn797 on 2008-12-23
> **LastWho said:**
> hi 73ckn797
i m a newbee, but why don't we suggest to him to install the adobe flash player! it works for everyone all the time, and its prettier!

in a terminal:

```
sudo apt-get autoremove flashplugin-nonfree 
```Download and install the .deb version of adobe flash player from here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)


That was what I had in mind but forgot the name.

---

### Post by mrbiggbrain on 2008-12-23
> **73ckn797 said:**
> That was what I had in mind but forgot the name.

you have an addon installed on firefox that makes it do that, you need to go to tools, addons, and disable it, i forget the name but it is an addon!

---

### Post by sportscrazed2 on 2008-12-23
its called flashblock

---

### Post by mrbiggbrain on 2008-12-23
> **sportscrazed2 said:**
> its called flashblock


yup thats the one, useful, if you know its installed...its good to keep annoying videos you dont wanna watch froms tealing your bandwith

---

### Post by sportscrazed2 on 2008-12-23
> **mrbiggbrain said:**
> yup thats the one, useful, if you know its installed...its good to keep annoying videos you dont wanna watch froms tealing your bandwith yep i love it you can just make exceptions for the flash sites you use often like youtube and hulu

---

### Post by Selphy on 2008-12-23
> **sportscrazed2 said:**
> its called flashblock

No flashblock installed

---

### Post by 2hot6ft2 on 2008-12-23
> **Selphy said:**
> This is a really silly issue I'm having and it seems like I'm just missing some simple fix. I've been having a problem with firefox and .swf files embedded into websites. It seems to have a knack for not auto loading them and instead displaying a big gray box with a "play" triangle that once clicked loads the flash file. This is really irritating and seems to cause issues specifically on embedded movie players. Anyone know how I can set up a preference to auto load flash content? 

Thanks!
I'm pretty sure you'll find a fix here for that. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Selphy on 2008-12-23
Apparently it was something to do with swfdec-mozilla. I uninstalled it in synaptics and then switched to another firefox flash plug in. Seemed to fix it.

---

