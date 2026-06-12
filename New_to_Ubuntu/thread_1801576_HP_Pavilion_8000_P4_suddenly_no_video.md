---
title: "HP Pavilion 8000 P4 suddenly no video"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-07-10
Last week I installed Ubuntu 11.04 on an old HP laptop.
The install went well and for a few days I was able to use Ubuntu on the machine.

The other day I started it up and all of a sudden after the initial HP boot screen the monitor went blank.

I tried rebooting and booting from a USB drive and a CD with no luck.

I also tried installing a less resource intensive distribution - Crunchbang.

The strange thing is I can do the graphical install for Crunchbang but as soon as it's time to boot into the freshly installed OS I get the blank screen again.

I can boot from the Crunchbang CD but if I try to run the live CD I get the blank screen again.

Does anyone know why I get the initial HP boot screen, can run the installer and see the menu for boot options from the CD but am absolutly unable to actually run the OS (at least graphically, I haven't tried running just a command line session.)  I did hit c when I was able to get grub to load once, but that seems to be a command line session for grub, I wasn't able to boot into the OS.

---

### Post by wildmanne39 on 2011-07-10
> **GrouchyGaijin said:**
> Last week I installed Ubuntu 11.04 on an old HP laptop.
The install went well and for a few days I was able to use Ubuntu on the machine.

The other day I started it up and all of a sudden after the initial HP boot screen the monitor went blank.

I tried rebooting and booting from a USB drive and a CD with no luck.

I also tried installing a less resource intensive distribution - Crunchbang.

The strange thing is I can do the graphical install for Crunchbang but as soon as it's time to boot into the freshly installed OS I get the blank screen again.

I can boot from the Crunchbang CD but if I try to run the live CD I get the blank screen again.

Does anyone know why I get the initial HP boot screen, can run the installer and see the menu for boot options from the CD but am absolutly unable to actually run the OS (at least graphically, I haven't tried running just a command line session.)  I did hit c when I was able to get grub to load once, but that seems to be a command line session for grub, I wasn't able to boot into the OS.
Hi, do yo know if grub is loading? and then the screen is going blank. If so try this link, then post back the results. It sounds like you may have updated your video card driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by GrouchyGaijin on 2011-07-11
> **wildmanne39 said:**
> Hi, do yo know if grub is loading? and then the screen is going blank. If so try this link, then post back the results. It sounds like you may have updated your video card driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thank you!

Actually grub usually doesn't come up, but I was able to get it to appear if I pressed I think F6 during boot.  I looked over the thread you mentioned and will read it / try the suggestions in the morning.

I thought that I had probably updated a driver, but figured that if I did a clean install any offending drivers would be removed.

---

### Post by wildmanne39 on 2011-07-11
Hi, yes if you reinstall you should get rid of any updated driver but that is not the best way to do it, but if it works for you it is ok.

---

### Post by GrouchyGaijin on 2011-07-11
> **wildmanne39 said:**
> Hi, yes if you reinstall you should get rid of any updated driver but that is not the best way to do it, but if it works for you it is ok.
Yeah that is the problem - it didn't work.
I can go through the install but when I reboot the machine into the OS I still get the blank screen.

---

### Post by wildmanne39 on 2011-07-11
> **GrouchyGaijin said:**
> Yeah that is the problem - it didn't work.
I can go through the install but when I reboot the machine into the OS I still get the blank screen.Hi, ok check out that link after you get some rest.

---

### Post by GrouchyGaijin on 2011-07-12
> **wildmanne39 said:**
> Hi, ok check out that link after you get some rest.

Hi again,

I read through all the pages on that thread and tried several different options including the nomodeset option.  Nothing helped.
As soon as the machine tries to boot into the OS I get the blank screen.

---

### Post by wildmanne39 on 2011-07-12
> **GrouchyGaijin said:**
> Hi again,

I read through all the pages on that thread and tried several different options including the nomodeset option.  Nothing helped.
As soon as the machine tries to boot into the OS I get the blank screen.Hi, ok  post the information from this script so we can see where everything is located:
You will need to boot with the livecd.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by GrouchyGaijin on 2011-07-12
> **wildmanne39 said:**
> Hi, ok  post the information from this script so we can see where everything is located:
You will need to boot with the livecd.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

I appreciate the help, but I'm a bit stuck.

As I said when I first installed 11.04 everything worked, then all of a sudden I started getting the black screen.

I am now unable to boot from an 11.04 live CD.

I thought that maybe a less resource intensive distribution would work (I thought it would remove any offending drivers if I did a clean install).  So I installed Crunchbang.

Now I am able to boot from the Crunchbang CD as well as run the graphical installer for Crunchbang.  BUT if I try to boot into Crunchbang after the grub menu I get the black screen.  Also if I try to run the Crunchbang live CD I get the same black screen.

So basically, I can't seem to run a live CD session or do anything at all with the Ubuntu CD.

I'm pretty confused but happy that this is on an old laptop I was just going to use to play around with.  My regular laptop is running 11.04 well.

---

### Post by wildmanne39 on 2011-07-13
Hi, I undrstand I was working one my very old laptop 2 weeks ago and had same problems. 

You can reset your cmos so it will clear your bios then configure your bios again that might make you able to boot a livecd, but if it is that old I would go with a light version of linux not ubuntu 11.04.

---

