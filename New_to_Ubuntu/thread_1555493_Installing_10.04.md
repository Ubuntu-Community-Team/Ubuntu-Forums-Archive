---
title: "Installing 10.04"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by DJSteve on 2010-08-18
hello all,
just been trying for the last couple of hours to install ubuntu 10.04 on my pc. ive already created a partition for it on one of my hds but the ubuntu installer refuses to even recognise that drive exists (it shows all my other drives). gparted shows the offending drive fine and i can mount the windows partition thats one the same drive in ubuntu without isue so it seems to be just the installer that has problems with that drive. 

any ideas how to persuade it to see the disk

if its any use the drive is an ide one and the others are sata

---

### Post by jmfal on 2010-08-18
Welcome to ubuntu,

Had the same problem a while back, finally I just unplugged the other hdd`s and installed ubuntu.

If you still have trouble doing it this way you may have to try the alternate version.

good luck

---

### Post by DJSteve on 2010-08-18
hmm ok ill have a look at doing that, fact im booting ubuntu off a usb drive shouldn cause it should it ?

---

### Post by DJSteve on 2010-08-18
ok just tried disconnecting all drives except my 80gb one and installer finds precisely 0 disks. 

any other ideas or am i forever stuck with using a usb drive for ubuntu

---

### Post by jmfal on 2010-08-18
Sorry for taking so long to reply (have to work)

really  surprised that anybody else has tried to help.

never messed with usb boot

Do know that pc/laptop must be capable of booting from usb, best  way is pc manual

no manual: restart into bios/setup >boot priority>see if option to boot from usb make this first then install. I may be wrong on this but, maybe someone else will give some advice

---

### Post by DJSteve on 2010-08-18
No i meaNt i am booting ubuntus live os from a usb pendrive but want to install it to one of my internal hds which every app except the installer happily recognises. Installer will not see it at all

---

### Post by AliG112 on 2010-08-18
Can I ask what kind of computer you have?

---

### Post by DJSteve on 2010-08-18
a self built tower. Have a rather large amount of hdds in. . . 2x250gb ide drives on a pci ide raid card in hw raid 0
2x500gb sata2 hdds 
80gb ide boot drive . I already have a ext partition created on here for ubuntu but although the os itself can see this drive installer will not

Amd athlon x2 cpu using 64bit ubuntu from usb pen

---

### Post by AliG112 on 2010-08-18
Ok. I had a similar problem to yours and it ended up being solved by disabling udma in my bios. However, I have a Dell and only two internal drives. So I am not confident it will be the same for you. Sorry I can't help much further, I am too new to ubuntu. 

Give it a try but someone else should be able to help you soon.

Good Luck. :D

---

### Post by DJSteve on 2010-08-18
will keep that in mind. Would rather not disable udma as itll reduce speed stupidly

---

### Post by john newbuntu on 2010-08-19
I am not sure if it is because of the fakeraid.  See this for details:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/573618](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/573618)
I guess try uninstalling dmraid after booting from liveCD prior to the install and see if it helps.

---

### Post by DJSteve on 2010-08-19
ok looks like removing dmraid works :) it didnt work on boot but after cancelling installer and booting into the full os then running sudo apt-get remove dmraid the installer detected everything

---

