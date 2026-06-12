---
title: "[HELP] Booting ubuntu installer from USB stick."
date: 2009-09-05
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-09-05
Hi,

Some people on this forum may have recently read my thread on problems when trying to use the installer and partition my hard drive, well I've diagnosed the problems with that, and it turns out I just need to launch the installer from a CD or USB stick, which is now what I'm trying to do. 

I'm having trouble running the ubuntu install from a USB using unetbootin, I get the ubuntu load up screen (with the loading bar) but after that I get a black screen with this white text: [http://pastebin.com/d4fc70064](http://pastebin.com/d4fc70064).

It would seem that I have a file missing, but how is this possible when all I've done is download the .iso and run it, this makes me think that re-downloading the file wouldn't actually make any difference :/

Any replies much appreciated.
~Aaron.

---

### Post by coldReactive on 2009-09-05
I suggest not using UNetboot or whatever at all if you plan to use Ubuntu on USB. Just use the USB Live Creator from an already installed Ubuntu machine, unless your other computer is windows?

And if you're installing Netbook Remix, install and use imagewriter (and download the .img file), not unetboot

---

### Post by snowpine on 2009-09-05
Hi Aaron, it's tough to troubleshoot Unetbootin here because it is not part of the Ubuntu project... they have their own site and forum at: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Have you tried using an Ubuntu Live CD or a USB stick prepared using Ubuntu's official usb-creator application?

---

### Post by Letterbomb05 on 2009-09-05
Hi,

thanks both of you for your replies. I don't believe the problem is with UNetBootin, and I'm installing it on an MS Windows XP computer.

Also, I don't have a spare CD to write the file to, so using an actual CD is out of the question :/

~Aaron.

---

### Post by snowpine on 2009-09-05
> **Letterbomb05 said:**
> Also, I don't have a spare CD to write the file to, so using an actual CD is out of the question :/

Blank CDs are cheap; how much is your time worth to you? ;)

---

### Post by bodhi.zazen on 2009-09-05
Unetbootin generally works just fine.

You need to download and use the "desktop" (Live) iso and not the alternate or server .iso

Generally that error is due to a corrupt iso, I suggest you check the md5sum of your iso.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If your iso is "OK", reformat the usb to FAT and re-run unetbootin. When booting from the usb select the option labeled "Default" on the (graphical) boot menu.

You need to at a minimum delete all the files from your USB before you re-run unetbootin (unetbootin does a poor job cleaning up after itself and you can not simply re-install). Formatting is ofter easier and ensures the usb is clean.

---

### Post by coldReactive on 2009-09-05
> **bodhi.zazen said:**
> You need to at a minimum delete all the files from your USB before you re-run unetbootin (unetbootin does a poor job cleaning up after itself and you can not simply re-install). Formatting is ofter easier and ensures the usb is clean.

Formatting may not remove U3 from the drive though if you have a U3 drive (Such as a Sandisk Cruzer.)

---

### Post by Letterbomb05 on 2009-09-05
Hi all,

thanks all for your replies, I got the fix from someone on IRC. All it took was for me to remove the USB for a few seconds when I got the "Ubuntu" loading screen, before putting the USB back in. Somehow this worked and I was able to partition my HD and install ubuntu as I wanted.

~Aaron.

---

