---
title: "Nvidia driver question , but a somewhat unusual one"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by beew on 2010-08-23
Hello, 

There are many threads about installing Nvidia drivers  and my question is also about Nvidia drivers, but a somewhat unusual one.

To explain my problem I have to back track a little bit. I have created a "portable" Ubuntu system (10.04) by installing the OS in a 8 G flash drive.

 I emphasize: it is not a live usb  with persistence but a real installation. It is formatted in ext3 and I can do all kinds of updates including kernel and system updates that would break a mere live usb with persistence. Because of the limitation in size and speed I basically use it for testing rather than real work (but I have another portable installation in a 40G external drive, it is fully workable as a "real" system)

I can plug this in a computer and start running and it is not limited by things such as ram. My own laptop (Dell) has only 1 g of ram but if I plug the usb (or the 40 G external drive) into the computer at work suddenly I have 3 g of ram instead. :)

I have tried this with different computers and things work out of the box beautifully. But they are all Dells.

Now I have a SamSung laptop which uses a Nvidia card and when I plugged in the usb installation in the graphics didn't quite work. So I figured I would just install the Nvidia drivers. There are many tutorials for that.  I downloaded the Nvidia driver for Linux (my card is supported)  and tried to install it using the usual procedure described in a dozen of tutorials. But for some reasons I couldn't kill the Noveau driver. I blacklisted it but it always regenerates itself somehow. Finally I removed it completely from synpatic but I was still getting some kind of graphics instead of getting a no graphic error as described in these tutorials so I can use the terminal to install the Nvidia driver.

After some more searching I instead installed the Nvidia driver from this PPA and it works! [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Here is the problem. When  I unplug the usb from the SamSung and plug it back into a Dell I am not getting graphic effects. While starting up there is an error message saying that it is not detecting a Nvidia card and it can only display in low grade graphic mode etc. 

I am thinking that if there is no Nvidia card Ubuntu should load whatever graphic driver which was using before instead. This is the case with wifi drivers. I plug the usb in computers using different wireless cards and Ubuntu just loads the right one automatically. Am I missing something? 

So the only way I can get full graphic effects now is to remove Nvidia  drivers when I plug the usb in the Dell and reinstall them  with Synaptic when I  plug it into the Samsung. Is there a better way?

Thanks for any advice in advance. :)

---

### Post by LowSky on 2010-08-23
The simple answer is dont use proprietary drivers.

---

### Post by beew on 2010-08-23
That is not an answer as the non proprietary ones don't  work fully. Sorry, I am trying to get the best functionality out of Linux, I am not on a religious crusade. If I were I wouldn't be using Ubuntu, there are more "pure" Linux distros for the free software purists like those endorsed by Richard Stallman.

---

### Post by mhgsys on 2010-08-23
What LowSky probably ment with "The simple answer is dont use proprietary drivers" is the fact those drivers will not just work with any videocard.

---

### Post by beew on 2010-08-23
No, I don't expect the Nvidia drivers to work with non Nvidia cards, but there are other drivers that do work with the other cards and they are  already installed. My question is whether there a way to configure Ubuntu in such a way that it will detect which one to use depending on which card you have just like it does with wireless drivers (I have plugged the usb in different computers from one that uses a external usb wireless card to one that uses a broadcom card to one that uses an athero card, everytime a different driver is used and Ubuntu chooses the right one automatically)

---

### Post by mhgsys on 2010-08-23
Yes; The simple answer is dont use proprietary drivers.

or uninstall the drivers you were using before plugging it in to another computer.

But that doesn't really answer your question I guess..

I'm thinking bash scripts auto editing xorg.conf here; 
Can't help you with that though; to less spare time to code;

ps:
(you can auto-generate..xorg.conf before we have the "missing" xorg.conf discussion)
[http://ubuntuforums.org/showthread.php?p=9755881#post9755881](http://ubuntuforums.org/showthread.php?p=9755881#post9755881)

---

### Post by beew on 2010-08-23
Thanks for the link. I will take a look.

---

