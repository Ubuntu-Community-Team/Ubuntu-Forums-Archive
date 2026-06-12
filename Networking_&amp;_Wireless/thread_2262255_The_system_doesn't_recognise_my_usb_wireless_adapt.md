---
title: "The system doesn't recognise my usb wireless adapter"
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by vctor2 on 2015-01-23
Hi, 
I have a laptop and in order to get wifi on my virtualbox machine I bought a usb wireless adaptor since I read it's the only way to acces wifi networks from virtualbox,
the problem is, my ubuntu (host) doesn't recognise my usb therefore my guest vbox can't use it.
When I use lsusb it shows this:
```
Bus 002 Device 002: ID 04f2:b45e Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:7601 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
I've tried with the CD driver which comes with my usb adapter: RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911
but when installing comes with the next error:

```
make[2]: ***  [/home/v/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911/os_dep/linux/os_intfs.o]  Error 1
make[1]: ***  [_module_/home/v/Desktop/RTL8188C_8192C_USB_linux_v4.0.2_9000.20130911/driver/rtl8188C_8192C_usb_linux_v4.0.2_9000.20130911]  Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-44-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```
And I don't know what to do in order to work in my vbox without appearing as an usb device in the usb settings of vbox.

---

### Post by TheFu on 2015-01-24
Dude.  The guestOS sees virtual network adapters.  Regardless of which cards are physically installed in the physical system.  If the hostOS is connected to the network with wifi, then the guest can connect thru that, just using whatever virtual NIC is presented. Usually an Intel PRO/1000 is the best choice for Windows guests and virtio is the best for Linux VMs.  The actual adapter used doesn't matter.

---

### Post by vctor2 on 2015-01-24
But actually what I want to do is to search all available WiFi networks through my guestOS and select which one I want to connect, instead of selecting it from my hostOS

---

### Post by TheFu on 2015-01-24
Perhaps if you described the real problem, rather than how you are trying to fix it, we might have other, better, options?
Or maybe we won't. ;)  I can think of a few situations, but those are unlikely for 99.99% of folks.

USB passthru just isn't 100%.  If the hostOS doesn't recognize it, I have doubts that the passthru will work properly either.

The hostOS is Ubuntu version what?
The guestOS is what?

---

### Post by vctor2 on 2015-01-24
the hostOS is ubuntu 14.04 and the guestOS is kali linux

---

### Post by TheFu on 2015-01-24
> **vctor2 said:**
> the hostOS is ubuntu 14.04 and the guestOS is kali linux

Ah ... you are one of "those" people. ;)
I'll ask my defcon group how they do this stuff, but suspect they dual boot.

Ok - asked them.

In the meantime, found a video claiming to have the solution: [http://www.youtube.com/watch?v=K1ETBeRQBs4](http://www.youtube.com/watch?v=K1ETBeRQBs4)
It is a very detailed explanation.

---

### Post by vctor2 on 2015-01-24
Yeah I've considered dual booting too, but since I use windows sometimes for my work I guessed the more viable option was to try with vbox

---

### Post by TheFu on 2015-01-24
So the answer from the author of [NarkNet]("http://narknet.com/") is  ....
> Latency can be an issue when capturing Wi-Fi traffic. I have found it is a little worse when passing a USB Wi-Fi adapter to a VM but it does work,

For normal traffic, he says it works fine, but ... he only uses that on hostile networks where he doesn't want to risk the hostOS being cracked.
At Phreaknic this year, I let my netbook get cracked during KoTH competition.  Not fun before returning home and restoring from a backup.  After international trips, I do the same.  I'm always worried about the maid attacks when in the shower. ;)

And another helpful response:
> ... noticed some intermittent problems with this set up when trying to inject wireless traffic using one of the Alpha cards.  Not sure if it was the card or the virtualization.

Did you see the video link above?

---

### Post by vctor2 on 2015-01-24
Yeah , does that mean that I can't get WiFi with my brand new usb adapter?

---

### Post by TheFu on 2015-01-24
> **vctor2 said:**
> Yeah , does that mean that I can't get WiFi with my brand new usb adapter?

They all use a specific adapter, based on recommendations by others in the industry. For them, it wasn't worth the time/effort to use anything other than the known-to-work $20 adapter.

---

### Post by vctor2 on 2015-01-24
okay thank you :)

---

### Post by TheFu on 2015-01-24
Someone appears to have gotten this wifi version working ... 
[http://forums.linuxmint.com/viewtopic.php?t=94495&f=53](http://forums.linuxmint.com/viewtopic.php?t=94495&f=53) 

Isn't Kali based off debian now? Anyway - should be close enough and not too hard for someone with a little C programming background.

That's outside any virtualization. Just be aware that manually maintaining kernel modules isn't fun. Every new kernel and you get to rebuild it, reinstall it.  I've been doing this since Feb for a touchpad on a chromebook.  Have it down to 1 script, but it is still a hassle.

I nice person from the DC group posted this: [https://averagesecurityguy.files.wordpress.com/2015/01/hack-yourself-first-final.pdf](https://averagesecurityguy.files.wordpress.com/2015/01/hack-yourself-first-final.pdf) which claims to have instructions in the wireless testing section. I haven't looked at the PDF myself.

---

