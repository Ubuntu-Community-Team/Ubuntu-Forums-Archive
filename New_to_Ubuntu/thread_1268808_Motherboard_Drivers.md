---
title: "Motherboard Drivers"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by George Curnow on 2009-09-17
Hi to you all.

I know this might be silly to ask but I have put a new motherboard and a 40 gb formatted hdd in a old computer with a Pentium 4 processor and installed ubuntu and the computer is working fine. I had not installed the drivers for the motherboard would ubuntu have had the drivers for this motherboard on it disk ????. The motherboard is a Asrock P4i65GV. if not how do I get the drivers on to the motherboard.  Yes I know its a silly question but it is my first computer build and my first time using ubuntu.

Also can you recommend any good books about ubuntu.

Thank you for you help.

Regards George

---

### Post by Marlonsm on 2009-09-17
Usually there is no need to install drivers in Ubuntu, it does all the hard work for you.
Here, when I installed, I just needed to click "activate" for the video card driver and it was done, everything was working.

---

### Post by jerrrys on 2009-09-17
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by George Curnow on 2009-09-17
Thank you both for the reply's. 

So if I upgrade to a  AGP vidio card  ubuntu should have the drivers for it. Is that correct.

Sorry but I am new to this operating system as I have only installed it for the first time to day (about 3 hours ago). but would like to know more about it and how to work with it.

Thanks George

---

### Post by jerrrys on 2009-09-17
video cards can be hit and miss, research the card you want for linux compatability.

this may help

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

[http://www.linuxcompatible.org/compatlistcat23.html](http://www.linuxcompatible.org/compatlistcat23.html)

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

[http://www.ubuntuhcl.org/index](http://www.ubuntuhcl.org/index)

---

### Post by George Curnow on 2009-09-21
Hello to you all and thank you for the help so far.

Today I have been trying to get my head around using Ubuntu 9.04. 

I have no other operating system on this computer as I would like to learn more about using Ubuntu.

Ubuntu loads up ok and I can get on the net via Firefox. and have downloaded and installed all the up dates.

But I cant get any visual effects out of my on board video card. I would love to have some of the great affects that I have seen on You tube.

I have tried the Visual Effects tab and selected Normal but it will not work.

Can any one help me sort this out.

My system is:

[Asrock P4i65GV]("http://asrock%20p4i65gv") motherboard
2.66ghz Pentium 4
1 gb ddr 400mz memory
40 gb ata Hdd
300 w psu

Is there a good Agp Graphics card any one could recommend that Ubuntu  will recognize with its drivers.  

Thank you for your help with this.

Best wishes George

---

### Post by norm7446 on 2009-09-21
Try E-bay there is usually a lot of AGP cards on there just watch that you get a x4 AGP or x8 AGP card as this is  the only ones your motherboard will take. Just watch you dont overload your power supply by getting the biggest card you can find.

---

### Post by LowSky on 2009-09-21
this list is from the american website newegg.com
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609639+1305520548&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010380048+1069609639+1305520548&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=48&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

the list is all the current AGP cards availible (nvidia based as they will work with Ubuntu), hopefully you see something you like that you can get in the UK

---

### Post by George Curnow on 2009-09-21
Thank you both for the reply's. I will have a look.

Best wishes George

---

### Post by George Curnow on 2009-09-22
Hi to you all once more.

Today I got my self a AGP graphics card it is a:

[URL="http://%20Asus%20v9520%20agp%20card"]Asus V9520 Magic , Nvidia Geforce FX 5200 128 mb.AGP 8x/4x/2x.
[/URL]
What I would like to know is, do l just put it in the  AGP slot and then boot up and would Ubuntu recognize it and install the drivers or do I have to do some thing to make it work.

I know this may look like a stupid question but Ubuntu is so new to me that after working with windows since os 95 up to vista it a new learning curve.

Thank you once more Regards George

---

### Post by oldos2er on 2009-09-22
Once you get your new Nvidia card installed, boot Ubuntu, then check menus System, Administration, Hardware Drivers to install the restricted video drivers. Reboot, and you should be able to get visual effects going.

---

### Post by jerrrys on 2009-09-22
congratulations george

if it was me, i just stick it in and see what happens next.  if you need to install drivers

 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by George Curnow on 2009-09-22
thank you both for replays no doubt you will hear more from me on this subject ha ha

Best wishes George

---

### Post by George Curnow on 2009-09-25
Hi once more

Please can some one HELP me.

I can not get any Graphics card to work.  I looked in my motherboard manual and found a list of Graphics cards that are computable with my motherboard. And one thats can be used with Ubuntu info from ubuntu forum. It is a Asus G froce 4 MX400 64mb

I put the card in the computer which then turns off the on board graphics on the motherboard then boot up then nothing bios flashes up the obuntu with a line underneath which starts with a little white line then stops before 1/4 way across and thats it nothing.

Please help as at the moment I am thinking of giveing up on this.

Regards George

---

### Post by oldos2er on 2009-09-25
Can you boot into recovery mode, and run xfix?

---

### Post by norm7446 on 2009-09-25
If you are getting something up on the screen when you first boot IE : the bios test screen, but when Ubuntu starts to boot the screen goes blank. 

Then it sounds like you have not disabled the On-board Graphics on the motherboard. To do this you have to got into the bios and set it to disabled. As normally just putting in either a PCI Graphics card or a AGP one does not actually disable the on-board graphics, this is something you have to do manually in the Bios.

---

### Post by George Curnow on 2009-09-25
Hi 
 
the motherboard info states that when a AGP card is put in the motherboard the on board graphics is disabled.
 
I am new to ubuntu and am still trying to get my head around things in it if any one could point me to a walk throughit would save time so you all would not have to put up with my graphics problems.
 
I would like to carry on with but it may be beating me at the moment.
 
Thank you George
 
ps how do you boot in recovery mode

---

### Post by sukigenseki on 2009-09-25
Hey I am curious if with your new video card installed can you successfully load ubuntu from a livecd? I am not a linux wizard or anything, but perhaps whatever is causing the issue with the existing installation has something to do with your system being configured for the old video card, so booting from a live cd will detect the new one and maybe work since it should load the right stuff. If it does work from a live cd I would just back up your files from there and then do a fresh install.

I hope that at least if you can not find another solution that does not require a re install that this will at least work for you as a fallback.

---

### Post by George Curnow on 2009-09-25
thank you for reply I will try any thing just to get my head around it  George

---

### Post by jerrrys on 2009-09-25
> **oldos2er said:**
> Can you boot into recovery mode, and run xfix?

when your system is booting there will be a "grub screen", when you see it hit your "Esc" key.  you got to be fast, the grub screen only appears for three seconds.  then it will say something like "try to fix X".  do that and then continue your boot process.

---

### Post by George Curnow on 2009-09-27
Hi to you all.

So after a very frustrating week I got the problem sorted out.

It was the mother board all the time, it turn out the Asrock P4i65 GV that I was using uses a different type of AGP slot.

I got in touch with Asrock and I quote

The AGI slot on the P4i65 is not the standard AGP slot, because the intel 865 GV chipset did not support a AGP slot. The AGI slot has limited compatibility so new AGP cards are not supported and Asrock support team says that they are not sure if LINUX can support this special slot and that could be a problem.

So there we go.

Now for the GOOD news.

I got hold of a older motherboard a MSi MS-6524 Intel P4 socket 478.
rebuilt the computer and put in the Nvidia Gforce 4 MX400 reloaded Ubuntu 9.04 loaded the updates and graphics. 

Rebooted and its ALL up and working (at last).

So once more thank you all for the help and the info. It is much appreciated.

Are there any good things that I should down load to make my experience a good one with Ubuntu ?


Best wishes George

---

### Post by jerrrys on 2009-09-27
and a double congrad on figuring that one out.  an agp slot thats not really agp :confused:  sounds like a hair puller to me.

[http://www.google.com/search?q=top+10+ubuntu+downloads&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=top+10+ubuntu+downloads&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

