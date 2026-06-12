---
title: "Bootup - Wrong resolution"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by Friend-Atish on 2010-06-20
Hi everybody,
When I am running the Ubuntu Live CD, it is running well in 1024x768 resolution. But, when I am installing it into my HDD it is running only in 800x600 resolution. :confused:  
My Display adapter is,
Intel(R) 82845G/GL/GE/PE/GV Graphics Controller.

I have downloaded the Linux driver from the Intel website, and installed it. But there is no change. I have also tried different threads but no result. 

Pls. help me out of this problem.......................................... ](*,)

---

### Post by Perfect Storm on 2010-06-20
You can try this: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

It's a known bug for restricted drivers as ATI and Nvidia - so I don't know if it works for intel cards. 

**Use this guide on your own risk!**

Make sure to edit/change the guide to fit your resolution. 
eg;

GRUB_GFXMODE=1280x1024

to

GRUB_GFXMODE=<your resolution>

etc.

---

### Post by Perfect Storm on 2010-06-20
Thread title changed and added some tags.

---

### Post by Friend-Atish on 2010-06-20
> **Artificial Intelligence said:**
> You can try this: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

It's a known bug for restricted drivers as ATI and Nvidia - so I don't know if it works for intel cards. 

**Use this guide on your own risk!**

Make sure to edit/change the guide to fit your resolution. 
eg;

GRUB_GFXMODE=1280x1024

to

GRUB_GFXMODE=<your resolution>

etc.


After following those steps, ubuntu is giving a black screen.  :mad: :mad:

How may I get back to my previous configuration ?? :confused: :confused:

---

### Post by Friend-Atish on 2010-06-20
How did you changed the title & added tags ?

---

### Post by Stigmata13 on 2010-06-20
This sounds a lot like the problems I've been having on one of my pc's. I think it's got more to do with the Intel Drivers rather than Ubuntu. I'm not exactly sure of what you can do to fix the Grub_GFX_MODE, but try adding "nomodeselect" to the Grub_CMD_LINE in your grub file.

---

### Post by Metrop021 on 2010-06-20
> **Artificial Intelligence said:**
> You can try this: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

It's a known bug for restricted drivers as ATI and Nvidia - so I don't know if it works for intel cards. 

**Use this guide on your own risk!**

Make sure to edit/change the guide to fit your resolution. 
eg;

GRUB_GFXMODE=1280x1024

to

GRUB_GFXMODE=<your resolution>

etc.

i have the same bug and i ran through that guide but it somehow made my ubuntu splash even bigger and uglier (if that was possible). I was trying to make it 1920 by 1080, i'm pretty sure that's possible since i see it when booting from a live cd

---

### Post by Perfect Storm on 2010-06-20
> **Friend-Atish said:**
> How did you changed the title & added tags ?

Title change is a staff feature ;)
Tags you can add end edit in the buttom of the thread. [edit tags]


@ Metrop021

Try with lower resolution eg. 1680x1050

---

### Post by Friend-Atish on 2010-06-20
> **Artificial Intelligence said:**
> Title change is a staff feature ;)
Tags you can add end edit in the buttom of the thread. [edit tags]


@ Metrop021

Try with lower resolution eg. 1680x1050

I had Tried it with 1024x768 ( Windows XP runs in 1024x768 ) .......... 

Is it possible to get back the view again without reinstallation?

---

### Post by Friend-Atish on 2010-06-20
> **Stigmata13 said:**
> This sounds a lot like the problems I've been having on one of my pc's. I think it's got more to do with the Intel Drivers rather than Ubuntu. I'm not exactly sure of what you can do to fix the Grub_GFX_MODE, but try adding "nomodeselect" to the Grub_CMD_LINE in your grub file.

"nomodeselect" is unknown command .........

---

### Post by Perfect Storm on 2010-06-20
> **Friend-Atish said:**
> I had Tried it with 1024x768 ( Windows XP runs in 1024x768 ) .......... 

Is it possible to get back the view again without reinstallation?

Yes if you can recall the default settings.

---

### Post by Friend-Atish on 2010-06-20
> **Artificial Intelligence said:**
> Yes if you can recall the default settings.
How ????

---

### Post by Friend-Atish on 2010-06-20
I have managed to restore my previous view ( 800x600 resolution ).

But I need 1024x768 resolution.......

Pls. help me.................

---

### Post by Metrop021 on 2010-06-20
oops double post

---

### Post by Metrop021 on 2010-06-20
> **Artificial Intelligence said:**
> Title change is a staff feature ;)
Tags you can add end edit in the buttom of the thread. [edit tags]


@ Metrop021

Try with lower resolution eg. 1680x1050

This is strange, I tried to use that resolution, and my monitor flashed "input not supported" then went back to showing the same ugly splash. I have a feeling that what should have happened if the input was really not supported is that the monitor should have just kept saying input not supported and no splash should have shown. Anyways, i went ahead and switched my resolution to 1600 by 900, and now the splash is shown (with strange purple stripes) but it is in a better resolution so i'm a bit happier. 

Even stranger (this is sort of off topic) is that after i booted up with that change, it seems my GNOME crashed. I was unable to maximize windows, type, click on anything other than mouseover, etc. it was really weird and i really really hope it was a fluke because that sounds like a reinstall problem.

Back to the topic, do you know any other resolutions I can try to avoid seeing these stripes? and also just to advance my linux knowledge, gsku is like sudo except that it showed the gui password entry window. Right?

---

### Post by JohnAtilano on 2010-06-20
Just want to report that the [softpedia link]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml") mentioned earlier in the thread worked PERFECTLY!

A few additional pieces of information that may be helpful to others:

You need to determine which resolutions are supported.  To do this reboot and get to your GRUB menu.  Press "c" to enter command line mode.  Then type  

```
vbeinfo
```

You will see all of the available resolutions.  I chose 1440x900x32

Notes for Softpedia steps.

1.  I installed v86d from the ubuntu software center.  Works fine.  apt-get will work too.

2.  Be careful when making these edits!  The example shows the following:

[COLOR=Black][COLOR=#008080]*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"*[/COLOR]
[/COLOR]
I changed mine to:
[COLOR=#008080][I][COLOR=Black]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset  video=uvesafb:mode_option=[COLOR=Red]**1440x900-32**[/COLOR],mtrr=3,scroll=ywrap"[/COLOR]

[COLOR=Black]Notice the DASH ( - ) in 1440x900[B][COLOR=Red]-32

[/COLOR][/B][COLOR=Red][COLOR=Black]I changed [/COLOR][/COLOR][/COLOR][/I][/COLOR][COLOR=Black][COLOR=#008080]*GRUB_GFXMODE=1280x1024 to *[/COLOR][COLOR=#008080][I]

GRUB_GFXMODE=1440x900[COLOR=Red]x32[/COLOR][/I][/COLOR][/COLOR]

Note that this entry is x32 NOT -32

3 - 7.  Follow as described.  To be honest, I have no idea what [COLOR=#008080][I][COLOR=Black]steps 3 & 4 were doing.
[/COLOR][/I][/COLOR]

---

