---
title: "Is Ubuntu's default resolution 1024x768?"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by psam3 on 2009-03-16
I cannot get a video signal at all when trying to install Ubuntu. I get the input not supported message but if the default is 1024x768 I do no understand because my TV supports that resolution. Even if I'm trying to use a 32" LCD TV shouldn't it work just the same as a normal monitor since it's going through a VGA connection? Did I just spend $500 on a computer for nothing because of my lousy TV?

---

### Post by linuxuser21 on 2009-03-16
It depends on your hardware I think.

---

### Post by psam3 on 2009-03-16
AMD Athlon 64 X2 5600 2.9 GHZ Dual-Core
4 gb DDR2 800 PC2 6400 RAM
160 gb Western Digital Caviar
500 Watt power supply, Radeon 3200 integrated

---

### Post by psam3 on 2009-03-16
I think I might have wasted my money, or else spend another $200 on a monitor just because my TV sucks. I have searched and found nothing. I doubt their is anyway to change anything considering I can't even see the bios screen. Oh well, just one more thing to add to my bad day. I think I'll go end my useless miserable life.

---

### Post by ModelM on 2009-03-17
Your problem may be that Ubuntu simply doesn't know what resolution your television supports.

Most modern computer monitors have a function called EDID which allows the operating system to "ask" the monitor what resolution/refresh rate(s) are supported. That's why I was able to, only a few days ago, unplug a monitor running at 1280x1024 & plug in a monitor running at 1440x900 and have the system come up running perfectly at the new resolution without any tweaking at all.

Your television, however, probably does not have EDID and so you may have to manually set up the resolution in the /etc/X11/xorg.conf file.

---

### Post by psam3 on 2009-03-17
> **ModelM said:**
> 

Your television, however, probably does not have EDID and so you may have to manually set up the resolution in the /etc/X11/xorg.conf file.

I understand and that makes perfect sense but how will I change it?  I can't get into any screen and I don't have anymore available monitors.

---

### Post by t0p on 2009-03-17
> **psam3 said:**
> I think I might have wasted my money, or else spend another $200 on a monitor just because my TV sucks. I have searched and found nothing. I doubt their is anyway to change anything considering I can't even see the bios screen. Oh well, just one more thing to add to my bad day. I think I'll go end my useless miserable life.

Don't kill yourself yet. Buy a monitor first. Then kill yourself if you think you should. (This is a joke).

---

### Post by Bölvaður on 2009-03-17
monitors tent to support low resolutions. I have a pretty big tv next to me that uses 800x600 which is quite good as it is an old tube screen. My father's lcd screen supports upto 1024x768... computer monitors have much smaller pixels.

---

### Post by SunnyRabbiera on 2009-03-17
> **linuxuser21 said:**
> It depends on your hardware I think.

Indeed it does, my default resolution by the initial setup by xorg sets it at that.
I have to use extra tools such as displayconfig to trick it into getting me a higher resoltion.
This is why ibex sucks for me, and why Jaunty will suck too as there has yet to be a replacement for it.

---

### Post by aeiah on 2009-03-17
my 32" tv runs fine. i use a dvi to hdmi cable, although the POST screen is only visible through vga because of resolution issues so i have that set up too. id suggest borrowing a monitor off someone first. if that works, you could try adding the tv as the 2nd video input as a dual screen type set up. set it to clone so they're both the same and fiddle with the settings, then you can give the monitor back once you've got it working. if you cant see anything then there's not much you can do until you can. you dont know if its a vga issue that'd be fixed with an hdmi cable, a graphics card issue, a configuration issue, a faulty tv or an awkward tv. you need to narrow it down without spending money.

---

