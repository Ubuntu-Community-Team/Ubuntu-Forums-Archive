---
title: "Want to run Meerkat as sole OS."
date: 2010-10-10
forum: New to Ubuntu
---

### Post by 5hadow5un on 2010-10-10
I have WinXP on first partition, Ubuntu on second.  I want to make Ubuntu sole OS and at front of HD.  How do I do that?

---

### Post by coffeecat on 2010-10-10
Are you hoping to remove the Windows partition and enlarge/move the Ubuntu root partition? Or would you be willing to re-install. The latter would be quicker and easier, but if you want to move the Ubuntu partition, post the terminal output of:

```
sudo fdisk -lu
```And we can see whether that's possible.

---

### Post by amjjawad on 2010-10-10
> **coffeecat said:**
> Are you hoping to remove the Windows partition and enlarge/move the Ubuntu root partition? Or would you be willing to re-install. The latter would be quicker and easier, but if you want to move the Ubuntu partition, post the terminal output of:

```
sudo fdisk -lu
```And we can see whether that's possible.

And I suggest to keep Windows XP just in case especially if you're new to Ubuntu. When you be more familiar with Ubuntu, then you could get rid of XP ;)

---

### Post by oldos2er on 2010-10-10
Why does Ubuntu need to be at the "front"?

---

### Post by ParadoxTwelve on 2010-10-10
I would use gparted live.  It is a great program that you can use to resize and remove partitions outside of either os.  It needs to be installed on a usb drive and booted from start up.  And as far as being new to Ubuntu and going all the way, I highly recommend it and give you props for your bravery. This is my first reply on the forums. But I started using Kubuntu at 7.10 Gutsy Then after the release of 8.04 hardy I began using gnome for my desktop and completely ditched windows.  But I won't lie, windows 7 through me for a little interest, but to say the least after a couple months I'm back.  I now have no use for windows and for the short time I left my gnome desktop I felt like I lost one of my children.  So yeah, ditch your windows and in time I know that Ubuntu will become more native to you than windows ever was.  And now that I am back and here just in time for 10.10 I think I may just started giving a little input from time to time.

---

### Post by migs73 on 2010-10-10
> **ParadoxTwelve said:**
> I would use gparted live.  It is a great program that you can use to resize and remove partitions outside of either os.  It needs to be installed on a usb drive and booted from start up. 
Gparted is part of the Ubuntu Live CD/USB so if you already have one of these you can access Gparted by booting from the Ubuntu CD and you'll find it in the Applications menu.
Because you are booting from the CD you can use it to alter your HDD.

---

### Post by amjjawad on 2010-10-10
> **migs73 said:**
> Gparted is part of the Ubuntu Live CD/USB so if you already have one of these you can access Gparted by booting from the Ubuntu CD and you'll find it in the Applications menu.
Because you are booting from the CD you can use it to alter your HDD.

Ditto.
In fact, as long as you have a LiveCD/USB, you don't need to create extra CD for GParted alone but that won't harm if you have one already :)

---

### Post by ParadoxTwelve on 2010-10-10
Gparted seems to run so much smoother when its on its own drive, and it runs in a smaller linux environment so it is easier to use with out any lag. I would consider the Ubuntu live cd as a third resort to gparted as the live cd takes some time to boot due to its media type, if your Ubuntu is on a usb drive it may be a little more recommended, I have also observed less errors in the native gparted environment due to the fact that it is running on such a small OS with less lag time.  Don't get me wrong, I think everything Ubuntu can do is amazing, but if you are going to get rid of an OS and use Ubuntu as your native, then you can not afford the chance of errors.  Cds tend to freeze, usb drives are more stable.

---

