---
title: "problems playing videos in ubuntu 11.04"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by sugavaneshb on 2011-08-13
I have been using dual boot of ubuntu 11.04 and windows 7... In windows7 as of now no problem...In ubuntu 11.04 when i play any movie or video, it is not really playing it well... the video rendering is not good.. its kind of odd just showing a fast display of some pictures or something.. i didnt have this problem with 10.04.. i have installed ati graphic drivers still i really cant find out what is causing this problem.. someone out there pls help me out... Its Dell studio model.. 1 gb ATI radeon graphics card.. windows 7 and ubuntu 11.04 dual boot... I mostly use vlc to play videos.. but i find this bug even with the movie player... so i don't think the problem is actually with the player....

---

### Post by snip3r8 on 2011-08-13
What format of video are you attempting to play?

---

### Post by sugavaneshb on 2011-08-13
> **snip3r8 said:**
> What format of video are you attempting to play?
 

this problem happens with most of the formats.. lets make it 'all'... .avi, .mkv, .mp4...

---

### Post by amjjawad on 2011-08-13
> **sugavaneshb said:**
> I have been using dual boot of ubuntu 11.04 and windows 7... **In windows 7 **when i play any movie or video, it is not really playing it well ... the video rendering is not good.. its kind of odd just showing a fast display of some pictures or something.. i didnt have this problem with 10.04.. i have installed ati graphic drivers still i really cant find out what is causing this problem.. someone out there pls help me out... Its Dell studio model.. 1 gb ATI radeon graphics card.. windows 7 and ubuntu 11.04 dual boot... I mostly use vlc to play videos.. but i find this bug even with the movie player... so i don't think the problem is actually with the player....

Ok, are we talking about Ubuntu or Windows 7 here OR both?

Can you play it normally on Win7 but not on 11.04? or it's not playing well on both Windows and Ubuntu?

---

### Post by sugavaneshb on 2011-08-13
> **amjjawad said:**
> Ok, are we talking about Ubuntu or Windows 7 here OR both?

Can you play it normally on Win7 but not on 11.04? or it's not playing well on both Windows and Ubuntu?

sorry for the error.. now i have edited the post.. the problem is with ubuntu 11.04 only thats why i posted here in ubuntu forums in the first place.... In windows 7 its normal and not on 11.04....!!!

---

### Post by amjjawad on 2011-08-13
> **sugavaneshb said:**
> sorry for the error.. now i have edited the post.. the problem is with ubuntu 11.04 only thats why i posted here in ubuntu forums in the first place.... In windows 7 its normal and not on 11.04....!!!

It's ok, I know that but some other might be confused so better to be clear and simple :)

So, back to topic.
Is it possible to post a screenshot when you play something?

Are you using VLC only? did you try another Media Player?

When you installed VLC, did you run:

```
sudo apt-get update
```  ?

Have you tried to remove VLC and re-install it again?

```
sudo apt-get purge vlc -y
```

then

```
sudo apt-get update && sudo apt-get install vlc -y
```

---

### Post by 3rdalbum on 2011-08-13
Two things to try:

1. Log out, select your username, and then in the Session menu at the bottom of the screen choose Ubuntu Classic (No Effects) or Unity 2D. This effectively turns off Compiz. ATI video cards don't play well with Compiz, unfortunately.

2. The other thing to try is changing the video output module. You can do this in VLC's settings. If it's currently at XVideo, try changing it to X11. You'll need to restart VLC after doing this. You might have some luck with this method.

*I honestly wouldn't bother trying to remove and reinstall VLC again. The problem is not a corrupted VLC binary, which reinstalling VLC would have fixed. It's very rare that "remove and reinstall the program" actually fixes problems on Linux, because the programs almost never get corrupted.

---

### Post by coffeecat on 2011-08-13
Let's also look at your video card/driver combination because this could be a video driver issue. You don't say which ATI card you have and it sounds as though you've installed the proprietary fglrx driver which can actually be worse than the open source driver for some chips. I'm posting from a machine with an ATI Radeon HD5450 using the open source driver and video playback, including high-definition, is just fine. Open a terminal and post the output of:

```
sudo lshw -C video
```

This will tell us, among other things, which ATI GPU you have.

---

### Post by coffeecat on 2011-08-13
> **3rdalbum said:**
> ATI video cards don't play well with Compiz, unfortunately.

That is a sweeping generalisation which is simply untrue. On my various machines I have three different ATI GPUs - Mobility Radeon HD4200, Radeon HD4350 and Radeon HD5450 - and they all play extremely well with compiz with the open source driver.

---

### Post by sugavaneshb on 2011-08-13
> **coffeecat said:**
>  Open a terminal and post the output of:

```
sudo lshw -C video
```


alright x11, ubuntu classic(no effects) didn't work....
and Here is the output of the command... 
*-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:d0000000-dfffffff memory:cfee0000-cfefffff ioport:2000(size=256) memory:cfe00000-cfe1ffff

---

### Post by amjjawad on 2011-08-13
> **sugavaneshb said:**
> alright x11, ubuntu classic(no effects) didn't work....


and Here is the output of the command... 

```
*-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: **driver**=**[COLOR=Red]fglrx[/COLOR]**_pci latency=0
       resources: irq:46 memory:d0000000-dfffffff memory:cfee0000-cfefffff ioport:2000(size=256) memory:cfe00000-cfe1ffff
```



I think it's the same that coffeecat referred to.

---

### Post by Sef on 2011-08-13
Have you installed the codecs to play the movies?

---

### Post by sugavaneshb on 2011-08-13
> **Sef said:**
> Have you installed the codecs to play the movies?

Yes i have...

> **amjjawad said:**
> I think it's the same that coffeecat referred to.

in that case where to get the open source drivers... I actually installed proprietary drivers which pops up after a fresh install.. I dont know whether it is right or not! with 10.04 on the same system, i never had any problem with ati, compiz along side with proprietary drivers only... I upgraded to 11.04 then all these problems are occurring..

---

### Post by coffeecat on 2011-08-13
> **amjjawad said:**
> I think it's the same that coffeecat referred to.

Well - possibly. :) The OP's lshw output gives this:

> **sugavaneshb said:**
> 
       product: Manhattan [Mobility Radeon HD 5000 Series]

But doesn't say which actual GPU it is, Unless Manhatten means something, but I can't see it in this link:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_5xxx_Series](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#Mobility_Radeon_HD_5xxx_Series)

@sugavaneshb, I'm tempted to suggest you uninstall the fglrx driver and see how you get on with the open source one but before you do, please post the output of:

```
lspci | grep VGA
```

I'm hoping that lspci will be somewhat less obtuse than lshw, but I fear it may give the same result.

---

### Post by sugavaneshb on 2011-08-13
> **amjjawad said:**
> before you do, please post the output of:

```
lspci | grep VGA
```

I'm hoping that lspci will be somewhat less obtuse than lshw, but I fear it may give the same result.
Here goes the output...

02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

---

### Post by coffeecat on 2011-08-13
> **sugavaneshb said:**
> 02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]

OK, I thought that would be the case - lspci doesn't tell us any more. My guess is that Manhatten is the GPU code name (it's "Cedar" for my HD5450). Did you use "Additional Drivers" to install the proprietary fglrx driver? If so, all I can suggest is to use Additional Drivers to uninstall the fglrx driver, reboot and see if the open source driver can do any better. With some ATI cards you are better off with the open source driver. The OS driver is just fine with my cards, but that doesn't necessarily mean that it will be with yours. You just have to try it and see.

---

### Post by sugavaneshb on 2011-08-13
> **coffeecat said:**
>  If so, all I can suggest is to use Additional Drivers to uninstall the fglrx driver, reboot and see if the open source driver can do any better. 

I ll do that and see whether it works.. I hope it will.. Can u just specify the steps about how to install this open source drivers and where from.. Uninstalling of fglrx drivers i can take care of that.. only installing this os drivers i dont know how to do that and where to find it...

---

### Post by coffeecat on 2011-08-13
> **sugavaneshb said:**
> I ll do that and see whether it works.. I hope it will.. Can u just specify the steps about how to install this open source drivers and where from.. Uninstalling of fglrx drivers i can take care of that.. only installing this os drivers i dont know how to do that and where to find it...

The open source driver is already installed and will simply be activated when you next boot up after uninstalling the fglrx driver. However, in earlier versions of Ubuntu, Additional Drivers didn't do a thorough job and some extra terminal commands were needed. I believe this has been fixed in 11.04 - I tried it myself - so disabling the proprietary driver in Additional Drivers and rebooting should be enough. If you get any problems, such as the GUI crashing when you reboot, post back and I can give you some terminal commands.

---

### Post by sugavaneshb on 2011-08-13
> **coffeecat said:**
> The open source driver is already installed and will simply be activated when you next boot up after uninstalling the fglrx driver. However, in earlier versions of Ubuntu, Additional Drivers didn't do a thorough job and some extra terminal commands were needed. I believe this has been fixed in 11.04 - I tried it myself - so disabling the proprietary driver in Additional Drivers and rebooting should be enough. If you get any problems, such as the GUI crashing when you reboot, post back and I can give you some terminal commands.



Thanks a lot coffeecat..:D:D:) It works like a charm now.. so no need of those proprietary drivers right.. I have uninstalled and rebooted.. Now it plays how it is supposed to....:D:D

---

### Post by coffeecat on 2011-08-13
> **sugavaneshb said:**
> Thanks a lot coffeecat..:D:D:) It works like a charm now.. so no need of those proprietary drivers right.. I have uninstalled and rebooted.. Now it plays how it is supposed to....:D:D

That's good news and thanks for the feedback. It bears out my experience. The couple of times I was tempted to install the fglrx driver, I wished I hadn't done so. :)

The open source ATI driver has come an awful long way in the last year or so and I believe some of those making adverse comments about ATI GPUs just simply aren't aware of how well they can perform out of the box in Ubuntu.

Good luck!

---

