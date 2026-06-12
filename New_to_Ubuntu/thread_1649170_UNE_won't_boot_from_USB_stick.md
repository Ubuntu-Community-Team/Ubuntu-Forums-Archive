---
title: "UNE won't boot from USB stick"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by TinGodz on 2010-12-19
I have an HP Mini 210-2000. Downloaded UNE 10.10 and installed it onto my Hama 16gb USB stick via Universal USB Installer. The USB stick shows up as "USB Floppy" under my boot options. Thus I have placed USB Floppy as the first boot option.

Whenever it attempts to boot, it briefly shows a string of text (SYSLINUX . . .; can't recall the exact string, but it was a bunch of numbers as if it was listing a version of something), flashes to a brown/tan display (as if it's trying to boot the initial Ubuntu screen, I presume) and quickly goes to a black screen and halts the process altogether. The SYSLINUX screen to brown screen to black screen occurs within a second. However, one time it actually did pause on the SYSLINUX screen but it has not done it since.

I have tried looking around the forums for a solution but have not found anything so far. I'll continue to look because I'm hoping to solve this problem ASAP to finally give Linux a test run. Any help would be greatly appreciated.

FYI: I have not tried this USB stick on another computer, but I plan on doing that right now.

EDIT: As mentioned in my post below Shintek's, I have now tried the USB stick on my other laptop and it boots Ubuntu just fine. I am actually typing this message in Ubuntu. Any help on why the boot process does not work with my netbook would be awesome!

---

### Post by Shintek on 2010-12-19
Did you format the USB stick?

---

### Post by TinGodz on 2010-12-19
lol, of course.

I am currently running UNE off of the USB stick on my Compaq laptop. Therefore, as I had presumed, it's not the USB stick. Does anyone have any information as to why the HP netbook won't boot it? From my inconclusive searches through Google, it seems like they actually shipped some of the HP minis with Ubuntu preinstalled. So I don't see how it could be a hardware limitation unless they were just built drastically different.

Again, any help would be greatly appreciated.

---

### Post by Eiji Takanaka on 2010-12-19
You got a 32-bit or 64-bit install bud?

I just briefly checked the specs on your laptop and its 32-bit architecture right?

One logical path to eliminate anyways ;)

- dan

---

### Post by TinGodz on 2010-12-20
> **Eiji Takanaka said:**
> You got a 32-bit or 64-bit install bud?

I just briefly checked the specs on your laptop and its 32-bit architecture right?

One logical path to eliminate anyways ;)

- dan

Yes, the netbook is 32-bit and I am using the 32-bit install.

---

### Post by TinGodz on 2010-12-20
Has anyone here successfully booted Ubuntu on their HP mini netbook?

---

### Post by TinGodz on 2010-12-20
I found the aforementioned blinking message after going to the boot options page to manually boot from the USB. It goes to a black screen that says "SYSLINUX 4.02 2010-07-21 EDD." Then approx. 4 minutes later a copyright for H. Peter [something] appeared for about 20 seconds until the screen went blank again.

So as I was typing this, I was googling the above text and have found a couple more links to check out for possible solutions. I will come back and edit if my problem is resolved. Until then, just wanting to get this out there in case someone already has a solution at hand.

Thanks.

---

### Post by wilee-nilee on 2010-12-20
How did you load the thumb?

Did you MD5SUM the ISO?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cariboo on 2010-12-20
This is a well known problem, you have to create the device using the Startup Disk Creator in Maverick, older versions won't work, or the latest version of unetbootin for Windows. You can get unetbootin [here]("http://unetbootin.sourceforge.net/").

It's a bug due to the new  Maverick installer.

---

### Post by wilee-nilee on 2010-12-20
> **cariboo907 said:**
> This is a well known problem, you have to create the device using the Startup Disk Creator in Maverick, older versions won't work, or the latest version of unetbootin for Windows. You can get unetbootin [here]("http://unetbootin.sourceforge.net/").

It's a bug due to the new  Maverick installer.

That's what I was thinking to.;)

---

### Post by TinGodz on 2010-12-20
> **wilee-nilee said:**
> How did you load the thumb?

Did you MD5SUM the ISO?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Yes, I verified the ISO as good.

> **cariboo907 said:**
> This is a well known problem, you have to create the device using the Startup Disk Creator in Maverick, older versions won't work, or the latest version of unetbootin for Windows. You can get unetbootin [here]("http://unetbootin.sourceforge.net/").

It's a bug due to the new  Maverick installer.

Roger that. Will have to look up Startup Disk Creator because I don't know what that is, but in the mean time, I do have UNetbootin. Currently installing on the USB now. First time it didn't install properly for some reason, so hopefully it works this time.

EDIT: Sweet. I am good to go at this time. Reformatted USB stick again, installed the ISO via Unetbootin again, and it booted just fine this time. Thanks for everyone that took the time to respond to this thread. Greatly appreciated.

---

