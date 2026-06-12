---
title: "installer fails"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by stonecoldjha on 2011-07-20
I tried installing ubuntu 11.04 with a freshly burnt iso.....but the installer freezes up when it asks for the geographical location of the user....and i have to power down my computer..the same thing happens when i try using a ubuntu 11.04 bootable usb stick...it also happens when i try installing lubuntu 11.04....
why can i not install ubuntu??
and how do i do it???

---

### Post by Bucky Ball on 2011-07-20
Give 10.04 LTS a go and see if you have the same issues.

---

### Post by Jacobonbuntu on 2011-07-20
> **stonecoldjha said:**
> I tried installing ubuntu 11.04 with a freshly burnt iso.....but the installer freezes up when it asks for the geographical location of the user....and i have to power down my computer..the same thing happens when i try using a ubuntu 11.04 bootable usb stick...it also happens when i try installing lubuntu 11.04....
why can i not install ubuntu??
and how do i do it???
you can install with a "alternate installation"
look at the ubuntu download site for "alternate" -iso
it installs on about everything. it is text-base but pretty easy. if you start up
, you might get a prompt. if so, type "install", the rest is logical.

---

### Post by amjjawad on 2011-07-20
> **stonecoldjha said:**
> I tried installing ubuntu 11.04 with a freshly burnt iso.....but the installer freezes up when it asks for the geographical location of the user....and i have to power down my computer..the same thing happens when i try using a ubuntu 11.04 bootable usb stick...it also happens when i try installing lubuntu 11.04....
why can i not install ubuntu??
and how do i do it???

Please check the first link in my signature!
Or, to be more specific, please check this: 
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Make sure you burn your LiveCD at Lower Burn Speed and make sure you're following the correct procedure to create a LiveUSB.

---

### Post by stonecoldjha on 2011-07-21
i have wasted a good number of CDs....and yes...i use slowest burning speeds when making its iso....
i tried installing ubuntu 10.04 using a bootable usb drive(i used unetbootin to create usb live image)...the installation was smooth with no errors...but when it boots up...it doesnt go to grub menu where i am supposed to see ubuntu 10.04 and windows 7...instead it shows grub error no such partition....
what do i do now?

---

### Post by Bucky Ball on 2011-07-21
I would plug in a cable, boot off the install CD, 'Try Ubuntu', make sure you are online, open a terminal and put in these commands to install Boot-Repair (yes, it will work on a Live install):

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```From here:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

You will then find Boot-Repair in System (probably administration - I am on xfce right now so slightly different).

Run it, choose the option to install grub to the MBR. Reboot, should be fixed. ;)

Incidentally, foolproof way of downloading the ISO is with a torrent:

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

mdsum checked in the process of torrentlng so you know it won't be defective (but that doesn't guarantee the actual physical media is not). Also make sure the media is nice and clean, no fingerprints or greasy smudges of any kind. I say this because it has happened to me. I was about to trash a 'defective' CD and burn a new one when I discovered the tiniest of finger marks; cleaned with isopropyl and installed straight away.

---

### Post by amjjawad on 2011-07-21
> **stonecoldjha said:**
> i have wasted a good number of CDs....and yes...i use slowest burning speeds when making its iso....
i tried installing ubuntu 10.04 using a bootable usb drive(i used unetbootin to create usb live image)...the installation was smooth with no errors...but when it boots up...**it doesnt go to grub menu where i am supposed to see ubuntu 10.04 and windows 7...instead it shows grub error no such partition....**
what do i do now?

As per your [first post]("http://ubuntuforums.org/showpost.php?p=11068154&postcount=1"), you were unable to install Ubuntu so from where did the GRUB menu come?

GRUB Menu will show up "after" installation not before!

Could you please explain clearly?

Thank you!

---

