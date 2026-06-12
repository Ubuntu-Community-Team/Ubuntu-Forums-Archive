---
title: "Wireless network won't stay configured/installed!"
date: 2014-07-02
forum: Networking &amp; Wireless
---

### Post by julian10 on 2014-07-02
Hey all, I am a relatively new linux user, and just installed xubuntu.  I was using a this ([https://wikidevi.com/wiki/Netgear_WNA3100](https://wikidevi.com/wiki/Netgear_WNA3100))for my usb wireless, but apparently this particular Broadcom chipset and linux don't get along so well. I tried Ndiswrapper with zero success.  So I switched over to this device due to the driver/module support [https://wikidevi.com/wiki/Netgear_A6100](https://wikidevi.com/wiki/Netgear_A6100)

I followed the super basic install instructions as per [http://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/](http://blog.danielscrivano.com/installing-rtl8812au-on-linux-for-wireless-dual-band-usb-adapters/)
or 
```

sudo bash
#password
make clean
make
make install
modprobe 8812au
```

It works at this point.  But as soon as I restart or shutdown, I have to do it all over again if I want any level of connectivity.  Aside from obviously being inefficient, it seems horribly sloppy as well.

Being that I am new to linux, I've spent the last five or so days trying to fix this, looking up info all over the web, but to no avail.  Time to ask my own question.

How can I make this stick?  I shouldn't have to append some script with all the above code, right?

Much appreciated, thanks in advance etc etc

-julian

---

### Post by yancek on 2014-07-02
> But as soon as I restart or shutdown, I have to do it all over again

Installed Xubuntu where and how?  Did you use a CD/DVD or flash drive with Xubuntu on it to install to your hard drive?  The behavior you are describing is expected behavior running from a Live CD since it is a read-only filesystem and does not save changes on reboot.  If you used something like Universal USB Installer or unetbootin, that is what you have.  How and where did you install Xubuntu?

---

### Post by julian10 on 2014-07-02
That makes sense--I should have thought of that.  I installed via [http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/) and used pendrive ([http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)) to convert the iso to a bootable usb.  I still have the raw iso on another hard drive, so I can remake that step. After booting to the usb I chose clean install (instead of the Live CD bit).  Maybe I mucked it about somewhere in the process.  Is there anything that can be done here, or would my best bet be to do a clean install?

Final thought, can you have installed programs on a Live CD install?  Because I installed Chrome and a couple other things and they stuck, which is probably why I didn't consider this as a problem.

---

### Post by yancek on 2014-07-03
> After booting to the usb I chose clean install 

I'm not sure what that means.  Did you use the bootable flash drive you create with pendrivelinux to install Xubuntu to your hard drive?
If you want to just use the flash drive created with pendrivelinux, you can do that also.  It is a Live CD on a flash drive and is read-only.  However, if you look at the pendrivelinux page, you will see that you can create persistence.  The limit is 4GB.  If you have persistence, you should be able to make changes including your network configuration and save it.  Also install a limited amount of software primarily due to the 4GB limitation.  I'm not sure what your intentions are?

---

### Post by julian10 on 2014-07-03
My intentions were to make a bootable linux usb drive, use it to boot, and then install linux.  I am going to wipe the drive, and give it another go, that way it will be established that this is a fresh install.  If that doesn't fix the problem, you will hear from me shortly!

Appreciate the time!

---

### Post by julian10 on 2014-07-03
Looks like I had a bunk install.  Gave it a clean wipe with a new partition table, and installed the driver.  It worked.  Then did a software update, and it didn't work.  Did a clean install, and it stuck again.  Keeping my fingers crossed that I keeps up with this trend.  Thank you for the help!

Also, how do I make this as solved?  Just edit the original post?

Thanks!

---

### Post by julian10 on 2014-07-07
So I have to revive this.  Everything was working for the last few days, but I took the weekend off and was only booting into Win 8 (to play titanfall, obviously), went back to "work" this morning and booted into linux.  No sauce.  Not internet connection.  So I tried to reinstall--nothing happened.  Restarted, uplugged, plugged in.  Nothing.  Went so far as to drop the security off of my wireless, that didn't work either.

Please help, this is rather frustrating.  Do I just have hardware that linux hates?  Is there such a thing?

Idle, thought, my clock seems to have changed on the desktop, if my CMOS battery is dying would that eff things up?

---

### Post by JeQhdMD on 2014-07-23
Ok, just a couple of thoughts.   So far, you've (with good intentions) made some incorrect assumptions about Linux, Xubuntu and networking.

Number 1 - - are you sure your broadcom wireless is incompatible?  Broadcom doesn't work "initially" . . . until you go to the tool all "buntus' use to intstall proprietary drivers (bcm43xx series).   There are plenty of methods for doing this (via terminal comands, via package managers (like Ubuntu Software Center)).   IF by some unusual circumstance, you do have an unusual broadcom chipset, then, you can still get easy wireless via usb wirelesss adapters BUT not netgear.

Number 2 - - the most compatible usb wireless adapters are:

>   TP Link 822 and/or 722 n . . . each uses the Atheros wireless chipset which has kernel level support (meaning, not wireless drivers to install in the first place).   Another very compatible device is the "Panda Ultra 150 b/g/n" wireless dongle (about $12 on amazon).  The Panda also is plug and play since Ubuntu 12.04 (or maybe 11.10).   Anyway, I highly recommend these as it make wireless automatic and steady (no drops, etc.)

Note:  fastest, most reliable method to run Ubuntu is via a Hard Drive (or sdd) install.   I only use Live Flash-Stick or DVD bootable images as rescue devices (and the best of those imho is Parted Magic - which runs in system RAM and has all the right tools).

---

