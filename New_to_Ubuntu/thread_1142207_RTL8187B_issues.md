---
title: "RTL8187B issues"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Cerberus2k7 on 2009-04-29
Alright folks.  First post here so I hope I don't come off as too much of a noob. :D  Been running Ubuntu 9.04 for the past week or so and it's been okay.  I'm a Windows guy so compiling these packages is pretty alien to me.  Been actually having a lot of issues.  One with wallpaper-tray.  Aparrently glib-2.0 is located in the wrong spot!  But that's besides the issue.  The issue I'm having is this.  I am online via ethernet cable just fine.  Works perfectly.  But wireless(yes...) is another story altogether.  Laptop is a Toshiba L45-S7423, and according to lsusb I am running a "Realtek Semiconductor Corp. RTL8187B Wireless Adapter".  Ok, so it sees that in there.  But for the life of me I cannot get the damn thing to work.  I have tried 4 different drivers and none of them seem to work.  Used ndiswrapper, it tells me there is no hardware present.  I have tried 3 different modded drivers and I get the same error every time.

```
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/cerberus/Documents/Programs/rtl8187b-modified/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/cerberus/Documents/Programs/rtl8187b-modified/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [modules] Error 2

```

It's honestly quite annoying.  I've used the Backtrack 4 live CD and wireless worked just fine.  so it's A. Me being an idiot(most likely cause), or B. Things aren't getting installed where they need to be.  Any and all help is appreciated. :D

---

### Post by llamabr on 2009-04-29
Is it this one?

[http://ubuntuforums.org/showthread.php?p=3539861](http://ubuntuforums.org/showthread.php?p=3539861)

---

### Post by Cerberus2k7 on 2009-04-29
> **llamabr said:**
> Is it this one?

[http://ubuntuforums.org/showthread.php?p=3539861](http://ubuntuforums.org/showthread.php?p=3539861)

Mine errors when I run ./makedrv.  I have used ndiswrapper with the win98/xp/2000/vista drivers and they all tell me that the hardware is not present.

In terms of what I've tried:

[http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html](http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html)

[http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/](http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/)

[http://www.softlinkwireless.com/internet-connection-wireless/ubuntu-windows-wireless-drivers](http://www.softlinkwireless.com/internet-connection-wireless/ubuntu-windows-wireless-drivers)

---

### Post by Cerberus2k7 on 2009-04-29
Ok, I'm posting from someone elses network right now.  I got wireless to work!

I followed this: [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

But now my ethernet connection wont work.  I pretty much had to remove ndiswrapper and reinstall manually, reboot, then I had no connection at all.

But now when I look under my networking area, it says my wired device is not managed.  Does Ubuntu have issues with running both at the same time or something?  I'm going to tinker around some more but man this is exhausting!  And exciting.  But the best way to learn is to fix the broken stuff I guess.

EDIT: Got my ethernet back, but it still says it's not managed in the panel.  Just going to see how long it stays connected now.  I *think* I'm close to figuring this out.  Hope so anyways. heh

---

### Post by Cerberus2k7 on 2009-04-29
I was able to figure out a tiny bit more.  What I found out is that with an ethernet connection and wireless ON, I can still use it just fine, but as soon as I connect to a wireless network, or even attempt to connect to one; my eth0 connection dies.  And if I disable wlan0 I am left with no connection at all.  The only way to restore eth0 without rebooting that I have found is by using xnetcardconfig and reconfiguring the eth0 connection.

If I try to configure my eth0 connection via System>Administration>Network Tools, it tells me that the interface does not exist.(Same for wlan0)  So now I'm completely lost.  Some areas are telling me the ethernet works and it does, but others can't even see that it exists.  Anyone have some insight as to why this is happening?

---

### Post by llamabr on 2009-04-29
as per my post above, I solved this headache with an external usb wireless stick.  You can find the same one on ebay these days for five bucks.  And just wait for the open source drivers to catch up with your hardware.

---

### Post by Cerberus2k7 on 2009-04-30
> **llamabr said:**
> as per my post above, I solved this headache with an external usb wireless stick.  You can find the same one on ebay these days for five bucks.  And just wait for the open source drivers to catch up with your hardware.

I'm probably going to do that.  But damn Express cards are still more expensive.  Now it's just my ethernet connection that's cutting out that I need to work on.

---

