---
title: "xUbuntu Wubi installation problems"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by VincentFirePony on 2009-08-27
Some members of another forum I belong to suggest I try Ubuntu. After some trouble getting Ubuntu to work I tried xUbuntu and was able to successfully download write the image to a cd and even test xUbuntu out. When I used the Wubi installation option from Windows XP it installed and gave me the dual boot option. When I select xUbuntu it starts up then a screen flashes too quickly to read everything on it. What I did get from it was ERROR FIRMWARE and part of something: b43. Then the desktop loads and a popup windows appears saying NO ROOT FILE SYSTEM. Now I'm an absolute beginner to Ubuntu (obviously) can anyone help me figure out just whats going on?

---

### Post by mike555 on 2009-08-27
sounds like the install got messed up somehow you might try again with another cd (burn it slowly)

---

### Post by LewRockwell on 2009-08-27
oh noes!

not another wubi-buntu-grenade-thrown-into-the-windows-partition-scenario

{{sigh}}

.

---

### Post by VincentFirePony on 2009-08-27
When I burned the Live CD it burned at 4x speed. Should I burn at 2x or 1x?

---

### Post by jmszr on 2009-08-27
VincentFirePony,

Before you reinstall Wubi (if that's what you decide to do), be sure to defragment the Windows drive that you're installing Wubi on. Twice is better.

---

### Post by LewRockwell on 2009-08-27
you're backed-up and/or cloned right mate?

.

---

### Post by VincentFirePony on 2009-08-27
Yes. And I did one defrag already, I can do a second when I go home. But should I Burn another disk? It works fine if I'm just doing to try xUbuntu...

---

### Post by jmszr on 2009-08-27
VincentFirePony,

When you boot the Xubuntu CD one of the options should be something like "Check CD for Errors" or "Check CD Integrity" (or something in that vein), run that and if there are no errors it should be OK. 

If you decide to burn another CD then this is useful: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and this: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) . If you chose to download the .iso again, it is recommended to use a torrent: [http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt) . Yes, go with 1x-2x as a burn speed.

---

### Post by VincentFirePony on 2009-08-28
Ok after several boots i've found out what I'm missing. It says ERROR FIRMWARE FILE B43/UCODE5.FW NOT FOUND. On the same sceen that flies by, it gives a website to go to and get said file. Too fast for me to write it down tho. So once I get this firnware file what do I do? do I need to burn a new live cd?

---

### Post by jmszr on 2009-08-28
VincentFirePony,

The error that you're getting relates to a Broadcom wireless driver: [https://answers.launchpad.net/ubuntu/+question/61277](https://answers.launchpad.net/ubuntu/+question/61277) .
Your real problem seems to be the NO ROOT FILE SYSTEM. 
You have two choices: 1.) Torrent a new .iso and burn the image to CD (check the Md5sum) and install from that, or 2.) use the Wubi installer (might be simpler): [http://wubi-installer.org/](http://wubi-installer.org/) .

These are some good resources: [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi) and: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide).

Remove your present Wubi installation first, of course.

If you have the HD room and the inclination then you might want to consider a full dual-boot installation.

---

### Post by VincentFirePony on 2009-08-28
Where can I Torrent another copy of the ISO.

---

### Post by jmszr on 2009-08-28
VincentFirePony,

You can find the Xubuntu torrent listed here: [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/9.04/release/) .

Edit: That is for the U.S., mirrors for other countries are here: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

