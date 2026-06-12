---
title: "How do I install an Nvidia driver?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by Stevy on 2008-12-07
Hello,  I need to get switch to "Root" from my normal login to install NVIDIA drivers for a new card.  I cant switch easily.  What is the method please?

---

### Post by __Ryan__ on 2008-12-07
Use the sudo command:

```
$ sudo *command*
```

---

### Post by SuperSonic4 on 2008-12-07
If you want to install nvidia drivers you'll need to press ctrl+alt+f1, log in as user in the text window and use sudo command

---

### Post by Michael.Godawski on 2008-12-07
Yep, sudo ( **do** as **s**uper**u**ser ) gives you the needed root privileges. 
If you need more information about a specific topic you can also check the community documentation:


[LIST]
[*][https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[/LIST]
Sudo and Root info:


[LIST]
[*][http://godawski.oxyhost.com/rootsudo.html](http://godawski.oxyhost.com/rootsudo.html)
[*][https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[/LIST]

---

### Post by CatKiller on 2008-12-07
> **Stevy said:**
> Hello,  I need to get switch to "Root" from my normal login to install NVIDIA drivers for a new card.  I cant switch easily.  What is the method please?

The sensible method to install the NVidia drivers isn't to follow the Windows Way and download a file from some website, but to use the package manager.

If you go to System -> Administration -> Hardware Drivers you should get the automatically configured driver listed for download and installation.

Failing that, you can use the package manager directly by opening up System -> Administration -> Synaptic Package Manager and installing the appropriate **nvidia-glx** package for the graphics card you have.

There is also a script, called Envy (which is widely described on this forum), that will automatically download and install the appropriate driver for your system.

---

### Post by mgmiller on 2008-12-07
> The sensible method to install the NVidia drivers isn't to follow the Windows Way and download a file from some website, but to use the package manager.

This is a very important concept for new users of Ubuntu.  Until you become much more proficient, and really know what you're doing, this is how you should be installing virtually anything else you want.

Do not download stuff off the net and try to install it.  

If what you are looking for is not in your package manager, you may need to add some extra repositories (think trusted libraries) and then use the package manager to install.

This is especially important for most restricted codecs and similar items like flash, java, mp3, etc. 

These are all in the package ubuntu-resticted-extras (or kubuntu-restricted-extras if you use kubuntu).

For dvd playback and mstcorefonts and google earth, go to:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Follow the instructions for adding the appropriate repository and updating your system.  It's a matter of 5 seconds of copy and paste in terminal.

Once you do that, you can easily add google earth, dvd, and extra codecs.
They will be in synaptic package manager called:
w32codecs  (w64codecs if you installed 64 bit ubuntu)
libdvdcss2
[FONT=monospace]googleearth[/FONT]

It's easy, it's different, it's not Windows.

---

