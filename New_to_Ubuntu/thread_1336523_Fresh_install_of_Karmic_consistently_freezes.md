---
title: "Fresh install of Karmic consistently freezes"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by MockY on 2009-11-24
I just tried to install Karmic on a Dell Inspiron E1505 but the computer completely freezes during install. I have tried multiple times but it freezes on an each attempt, all on different spots (at 12%, 33%, and 64%).
So I installed it using the minimal image, and that worked just fine.

However, now the computer randomly freezes. Sometimes during boot, without even letting me log in to a shell, and sometimes right after I log in to the desktop. I have yet to encounter a time where I can run the computer for more than 30 seconds before it completely stalls (I can't even move the mouse). The times I freezes once the desktop is loaded, the WiFi led blinks consistently, but nothing blinks the times it freezes during boot.

This machine was able to run both 8.10 and 9.04 just fine.

What is going on here? Any ideas?

---

### Post by dca on 2009-11-24
I've seen this when bad memory is to blame.  If mem is fine, you can try (if the Dell lets you) switching off wireless and try starting laptop.  See if it runs fine for a little while then switching on.  If issue then, you may have driver conflict - don't know enough about machines to advise on proper driver installation...

---

### Post by MockY on 2009-11-24
I tested the memory with memtest and nothing suspicious showed up. I disabled the wireless NIC and for a while I thought that this actually fixed the issue. But after 10 minutes of tweaking the desktop, the computer completely frooze yet again, this time while browsing in gconf-editor. 

So now I'm on square once again. :(

---

### Post by fsando on 2009-11-24
> **MockY said:**
> I tested the memory with memtest and nothing suspicious showed up. I disabled the wireless NIC and for a while I thought that this actually fixed the issue. But after 10 minutes of tweaking the desktop, the computer completely frooze yet again, this time while browsing in gconf-editor. 

So now I'm on square once again. :(

I'm seeing the exact same on an asus m2400 (core solo, intel graphics) from ca. 2004. I've tried the daily lucid 10.4 with same result.

I'm trying the live cd. It gets me less than a minute before the desktop freezes. I can still go to another ctrl alt f1, so the machine isn't frozen only the gnome graphic desktop. I can still move the mouse too.

EDIT: Here's a couple of possibly related bugs:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/459340](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/459340)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/445056](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/445056)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/433541](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/433541)

---

### Post by MockY on 2009-11-24
I just installed Jaunty on it using the latest iso, and it works just fine, so it has to do with the later release. Googling around a bit revealed that I'm not alone with this complete system freeze issue. And it seems like it does not matter what distro that is used either. So it has to do with the kernel....but what?

I'll check out the bugs and see if I find any clues.
Thanks for posting them.

---

### Post by fsando on 2009-11-24
> **MockY said:**
> I just installed Jaunty on it using the latest iso, and it works just fine, so it has to do with the later release. Googling around a bit revealed that I'm not alone with this complete system freeze issue. And it seems like it does not matter what distro that is used either. So it has to do with the kernel....but what?

I'll check out the bugs and see if I find any clues.
Thanks for posting them.

Though I tried karmic several times, I never tried the "acpi=off" option before. Just did and now it got past the freeze.

At the install screen press F6 and choose acpi=off

---

### Post by MockY on 2009-11-24
> **fsando said:**
> At the install screen press F6 and choose acpi=off
This solved the GUI installer problem. It did not freeze at all. However, I bypassed that earlier by installing Ubuntu via the minimal image. The end result is the same though; the system freezes on boot or right after the desktop is loaded.

I added acpi=off to the boot options after the install, but the system still freezes.

---

### Post by MockY on 2009-11-25
The most screwed up part is that this machine was purchased from Dell with Ubuntu pre-installed from the factory. That to me should mean that the machine in question can be upgraded to later versions of Ubuntu. Since this laptop is over a year old now, Dell refuses to assist.

This is definitely the last time I suggest Dell to anyone.

---

### Post by kansasnoob on 2009-11-25
I'd describe my "freezes" more as random, but that's why I decided to stay with Jaunty.

I could sometimes go for hours without a hard lockup, then boom!

Other times it would be freeze after freeze after freeze, and I never could narrow it down to a specific cause.

It could happen while running Firefox, typing a document, running updates, etc, etc.

That and so many other small bugs sent me running back to Jaunty.

---

### Post by MockY on 2009-11-25
I just updated the kernel on this machine with Jaunty installed, and I am now experiencing similar freezes. Sometimes it can go 10 minutes, but most often about 5 minutes. So there must be something in the later kernels that causes this.
Very frustrating, especially when the owner does not want to go back to Windows. So now I have no other options. If I install Ubuntu, it will freeze and if I install Windows, the owner wont like it.

*sigh*

---

### Post by crjackson on 2009-11-25
> **MockY said:**
> The most screwed up part is that this machine was purchased from Dell with Ubuntu pre-installed from the factory. That to me should mean that the machine in question can be upgraded to later versions of Ubuntu. Since this laptop is over a year old now, Dell refuses to assist.

This is definitely the last time I suggest Dell to anyone.

MockY, I've got to jump in here.  I don't own a Dell but it's NOT Dell's fault that a newer version of Ubuntu shipped with some nasty bugs in the kernel.

Many PC's don't operate properly after upgrading the OS including Win powered systems.  There were plenty of good running Win95 machines that couldn't run ME or XP.  Does that make the Machine vendor the villain no.

Just stick with the version that shipped until the nasties are worked out and you'll love Dell again.  That's just the way it works.

---

