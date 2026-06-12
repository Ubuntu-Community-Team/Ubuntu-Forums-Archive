---
title: "No wifi on macbook"
date: 2015-10-28
forum: Networking &amp; Wireless
---

### Post by dellboy56 on 2015-10-28
Hi guys just installed clean Ubuntu 14.04 lts on a 2010 MacBook and there's no wifi connections please help!

---

### Post by Lars Noodén on 2015-10-28
Have you followed these steps?

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Which model of wireless card does it show that you have?

---

### Post by dellboy56 on 2015-10-28
I can't and I don't know I'm not connected to Ethernet but there is a propitery driver and when I try to install it's just stuck there not doing anyhting

Says no such pci access method how do I enter the command properly

---

### Post by Lars Noodén on 2015-10-28
Open a terminal and try [lspci](http://manpages.ubuntu.com/manpages/trusty/en/man8/lspci.8.html)

```

lspci -vvnn | grep -A 9 Network 

```

It will probably say something about a Broadcom card.

---

### Post by Bucky Ball on 2015-10-28
*Thread moved to **Networking & Wireless**.*

Please open a terminal and run this:

```
sudo lshw -C network
```

Post the output. Best and easiest is to take your laptop somewhere there is access to a cable or obtain one. You will probably save yourself a great deal of time. 

The proprietary driver can not install as you are not online I suspect.

---

### Post by dellboy56 on 2015-10-28
Ran command from last user the product is a Broadcom bcm4322

---

### Post by Lars Noodén on 2015-10-28
> **dellboy56 said:**
> Ran command from last user the product is a Broadcom bcm4322

For mine, I used the open source driver, but to get it you need an ethernet connnection.  Once connected you can get it in three steps:

```

sudo apt-get update
sudo apt-get install firmware-b43-installer
sudo reboot

```

---

### Post by Bucky Ball on 2015-10-28
Thanks for that, but when asked to post the output, please post the full output between code tags (see last link in my signature). Cheers.

You just need to get near an ethernet cable or do what Lars Nooden has suggested, or, if you can't get online, you need to get to a computer that is online, get yourself a USB dongle to transfer files to/from, and follow the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access").

Good luck. :)

---

### Post by Hadaka on 2015-10-28
Hi, you can load the driver you need ,offline
First let's verify that your Broadcom bcm4322 card has a PCI-ID of BCM4322 [14e4:432b]
please open a terminal...ctrl/alt/t...then COPY and paste this command .
```
lspci -n | awk '/0200|0280/{print$3}'
```
*If one of the numbers is [COLOR=#ff0000]14e4:432b
[/COLOR]then go here follow the instructions on Post #7, dont be concerned that it's 2012
b43 has been around forever -> [URL="http://ubuntuforums.org/showthread.php?t=2098717"]http://ubuntuforums.org/showthread.php?t=2098717
[/URL]please run this command BEFORE loading the b43 diver
```
sudo apt-get remove --purge bcmwl-kernel-source
```
finally, when complete do not load the proprietary driver,,it is incorrect for your card.
good luck

---

### Post by dellboy56 on 2015-11-02
Hi the command I put in is correct the 1434:432b what do I do now I don't have ethernet

But it has come up I got AirPort Extreme in the additional drivers

Don't worry thanks for your support just had to run the AirPort Extreme let it do its thing and ba, it worked you can close thread now thank you:D

Sigh I ran into the problem again I just installed Ubuntu from my disc the only way the wifi worked is because I had all the check marks in the software and updates and it worked only with the disk I now have the disk and I, trying to install the driver but this time it isn't cutting it its just staying orange not moving like it did before from the live session like I said I marked down the code and ran it how do I download the driver and execute it

I have installed the following b43/fwcutter is that correct then should I install b43.zip cause I ran the purge command and it didn't say it uninstalled but it installed Linux-image generic lts vivid

Also the guy with the dell stated you got b43.zip entered the commands etc and still nothing has changed

---

