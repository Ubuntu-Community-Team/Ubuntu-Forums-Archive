---
title: "Problems when booting"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by sunde887 on 2010-12-28
I have a new laptop which I would like to dual boot linux and windows 7 on.

I also had a cd from a while ago which I used to do an installation, I manually partitioned the drive, 13gb for the linux install and 4gb for the swap area. When I finished installing it, I loaded it up, with some problems.

When I boot to linux ubuntu it has a black screen which scrolls a bunch of white text, eventually asking for the user name and password I used during the installation. When I type the info in it welcomes me to ubuntu, but remains on this screen. It also gives me an area to type sudo commands, but the actual OS doesn't load. Im really not sure whats going on, any help would get greatly appreciated.

---

### Post by DougieFresh4U on 2010-12-28
Welcome to the forum ):P
A little more info would really help in trying to get to your problem:
what version of Ubuntu did you use
what are your machine specs, grahics card/chipset
processor:Intel/AMD

---

### Post by sunde887 on 2010-12-28
ubuntu 10.10

64 bit
Intel processor
3gb ram
ATI® Mobility Radeon™ HD 5145
I believe its a x86 chipset

The computer can be found here
[http://us.toshiba.com/computers/laptops/satellite/L650/L655-S5075](http://us.toshiba.com/computers/laptops/satellite/L650/L655-S5075)

I will get what the screen says when I try to boot to ubuntu posted momentarily.

---

### Post by DougieFresh4U on 2010-12-28
Does the cd load for a 'live' session?
just wondering.

---

### Post by sunde887 on 2010-12-28
it says

[10/509360] EXT4-fs(sda6): re-mounted. opts: commit=0

Ubuntu 10.10 kenny-Satellity-L655 tty1

kenny-satellite-L655 login: ******
password: ******

Last login: Tue Dec 28 08:35:19 EST 2010 on tty1
Linux kenny-Satellite-L655 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50
UTC 2010 i686 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)

your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, runL
  /usr/bin/check-bios-nx --verbose

0 packages can be updates
0 updates are security updates.

to run command as administration (user "root"), use "sudo <command>".
see "man sudo_root" for details.

kenny@kenny-satellite-L655:~$


Then it allows commands.

After approximately 5 minutes the screen goes black and stays that way until I turn it off.

---

### Post by sunde887 on 2010-12-29
Earlier I thought it worked, I must have been wrong. Im wondering if maybe I have a 32 bit copy cd? I tried downloading the 64 bit and copying it to a dvd, but the computer didn't seem to recognize the dvd on boot up.

---

### Post by wilee-nilee on 2010-12-29
Sounds like your getting the grub menu. Instead of choosing Ubuntu hit e and use the arrow keys to get to the end of the first kernel where it says quiet splash and replace that with nomodeset, then crtl+x to boot to safe graphics mode to get the graphics driver probably.

---

### Post by sunde887 on 2010-12-29
Wilee, I tried what you said and it still loads the same screen when I boot.

---

### Post by wilee-nilee on 2010-12-29
> **sunde887 said:**
> Wilee, I tried what you said and it still loads the same screen when I boot.

At that command line you end up type startx and see if the desktop starts.

Hard to say the exact problem for me, but if you get to the desktop, you can open the update manager and see if this gets resolved with some updates.

---

### Post by sunde887 on 2010-12-29
An update, I downloaded the 64 bit os, and burned it to a cd. I was able to load into a 'live' session with this disc, I deleted the partitions and started with a new install with this disc.

I did 13gb for root directory, 10 for home and 4 for swap. After installation the same thing happened. At the top before scrolling other text it said something similar to:
"fatal error, couldn't find directory" Ill get more details on what it said momentarily, I will also try the startx thing you mentioned. 

What command should I run in the terminal to update? And will I need internet access? I think I am going to need to figure out how to download the driver first if thats the case.



edit: startx did not bring me to the desktop, same problem as before.

---

### Post by sunde887 on 2010-12-29
I managed to get it working, not quite sure, after a few tries with the 64 bit disc the install just went through.

Im having a bit of trouble getting wireless Internet working. I found a post explaining it, I did everything it said, then when I restarted my computer I still cant connect wirelessly.

[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

is the link I used. It said rtl8192ce installed correctly, but when I take out the ethernet cable it just loses connection and doesn't recognize a card. Any help is greatly appreciated.

```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8185
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at 3000 [size=256]
    Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
    Kernel modules: r8192ce_pci

```

is what I got when running lspci -v

---

