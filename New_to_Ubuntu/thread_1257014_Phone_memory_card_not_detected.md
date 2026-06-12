---
title: "Phone memory card not detected"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by | Gnome | on 2009-09-03
I have a nokia phõne and i wanted to connect it to my computer (ubuntu-jaunty) for data transfer. When i connect it to the computer in data storage mode, ubuntu doesnt detect it, however its ok with pendrives. What might be the reason?

---

### Post by LowSky on 2009-09-03
might be the phone...what model is it

 when connected run the command ```
lsusb
``` it will tell you if the phone is being detected, if it is your next move is try to mount the phone's media card manually

---

### Post by Weidbrewer on 2009-09-03
Ugh...phones and memory cards.  At least Ubuntu is a lot easier that Windows, but man, the companies love to lock their hardware down.  I've actually had it vary between phones *of the same model*!  Blackberry Storm 1 and 3 mounted automatically for me with no problems...Storm #2, I never got it to connect.

Like **LowSky** says above, run that lsub command.  It might not show you something as obvious as "Nokia phone with memory card."  For example, my Storm lists as something like, "Research in Motion USB Device."  (This is the manufacturer.)  Look for something along those lines of you don't see your phone right away.

Also, go to your menu dropdowns and check in "removable media."  I've had a few phones that have hidden there rather than auto-connecting.

---

### Post by LewRockwell on 2009-09-03
> **weidbrewer said:**
> ugh...phones and memory cards.

+ 1

.

---

### Post by | Gnome | on 2009-09-03
Ok, I connected my phone and ran the command "lsusb". Following is the message displayed after that. Now what should I do? Please be as elaborate as possible. I am totally a newbie to Ubuntu.
Thanks in advance!!

[B]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0421:0019 Nokia Mobile Phones 6288 GSM Smartphone (imaging mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[/B]

---

### Post by philinux on 2009-09-03
It says it's in imaging mode, not sure what that is, my phones not smart lol. At least it's detected. Needs to be in a file transfer mode.

---

### Post by | Gnome | on 2009-09-04
> **philinux said:**
> It says it's in imaging mode, not sure what that is, my phones not smart lol. At least it's detected. Needs to be in a file transfer mode.

NO, it's in data transfer mode. I don't know why is it showing "imaging mode".
BTW it works fine on Windows.

---

### Post by Weidbrewer on 2009-09-04
> **| Gnome | said:**
> NO, it's in data transfer mode. I don't know why is it showing "imaging mode".
BTW it works fine on Windows.

Crap.  That's exactly what happened with BlackBerry Storm #2 with me...I had transfer mode selected, and it kept saying it wasn't.  Honestly, this is probably more phone-side than it is PC side.  This phone isn't, by any chance, a refurb is it?  Storm #2 was for me, and someone had installed a beta of an OS upgrade on it that the techs didn't catch when they sent it back out.  Part of what made me go back for Storm #3.

---

### Post by LowSky on 2009-09-04
> **| Gnome | said:**
> 
BTW it works fine on Windows.

LOL, make sure when you disconnect the phone in Windows, that you remove it properly and not by just pulling the cord.

The same thing happens to Flash drives when people forget to remove the disk the correct way.

---

### Post by | Gnome | on 2009-09-05
> **LowSky said:**
> LOL, make sure when you disconnect the phone in Windows, that you remove it properly and not by just pulling the cord.

The same thing happens to Flash drives when people forget to remove the disk the correct way.


So....  what's the solution now. Isn't there any??

---

### Post by Weidbrewer on 2009-09-05
Load it back on a Windows machine, get it recognized, then remove it safely...might reset things.

---

### Post by | Gnome | on 2009-09-07
> **Weidbrewer said:**
> Load it back on a Windows machine, get it recognized, then remove it safely...might reset things.


I tried that but the problem persists. Any other solutions please??

---

