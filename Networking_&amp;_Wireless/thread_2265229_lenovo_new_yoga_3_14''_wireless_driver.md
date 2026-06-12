---
title: "lenovo new yoga 3 14'' wireless driver"
date: 2015-02-13
forum: Networking &amp; Wireless
---

### Post by Shuran_Li on 2015-02-13
So I just installed ubuntu on my lenovo yoga laptop. And not surprisingly, the built in wireless adapter, a qualcomm Atheros QCA61x4, was not recognized.
It showed "No network devices available" when I clicked on the wireless icon in the taskbar.

```

rfkill list all
```

showed

```

0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: yes
2: hci0: bluetooth
        Soft blocked: yes
        Hard blocked: no
```

But I can't find a wireless switch on the laptop, the closest thing is the F7/fight mode key, which only turned all of the soft blocked status to yes when pressed.

I tried to use an usb wireless adapter, a TP-LINK TL-WN725N V1, or Realtek RTL8188CUS.
But the wireless icon showed "Wi-Fi is disabled by hardware switch" when I plugged the adapter in. And the device doesn't show up in rfkill.
However it does show up in lsusb as 
```
0bda:8179 Realtek Semconductor Corp.
```

I have tried installing drivers for both the build in adapter and the usb one. But nothing worked so far.
What could the problem be? There are too many links in the chain that could go wrong and I feel I'm not able to narrow it down.
Has anyone had better luck with this model, or better understanding of the matter? Any tip or experience is welcome.

---

### Post by howefield on 2015-02-13
Thread moved to the "*Networking & Wireless*" forum. Better chance of help in here.

---

### Post by chili555 on 2015-02-13
I doubt you need a driver. You need to fix this: > Hard blocked: yes
.....
But I can't find a wireless switch on the laptop, the closest thing is the F7/fight mode key, which only turned all of the soft blocked status to yes when pressed.This is a rather well-known issue with Yoga laptops. The little helper module *ideapad-laptop* is supposed to translate key presses, F7 in your case, to action; ideally "turn on the wireless, please."

A search of this forum for ideapad-laptop will show many threads with long, tortuous attempts to get it solved. In one of them, a whole different ideapad-laptop driver was compiled from source code and loaded. 

Let's start  with the easy way and go from there. First, let's remove the module temporarily and see if the wireless springs to life:```
sudo modprobe -r ideapad-laptop
```If it helps, we'll blacklist it, you'll give me a Solved and we're done. 

If not, then I understand that it is fixed in Ubntu 14.10. I suggest you download and try the live DVD or USB and see. If so, I'd install it.

We await your findings.

---

### Post by Shuran_Li on 2015-02-13
> **chili555 said:**
> 
Let's start  with the easy way and go from there. First, let's remove the module temporarily and see if the wireless springs to life:```
sudo modprobe -r ideapad-laptop
```If it helps, we'll blacklist it, you'll give me a Solved and we're done. 



The built-in adapter disappears from the rfkill list, but the usb adapter works now.

---

### Post by jeremy31 on 2015-02-13
I am interested to see what Ubuntu says the internal wifi is ```
lspci -nnk | grep -iA2 net
``` If you please

---

### Post by Shuran_Li on 2015-02-13
Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20) Subsystem: Lenovo Device [17aa:3545]

---

### Post by chili555 on 2015-02-13
A new device, it seems! What do ya reckon, Jeremy?

---

### Post by jeremy31 on 2015-02-14
[https://wireless.wiki.kernel.org/en/users/drivers/ath10k](https://wireless.wiki.kernel.org/en/users/drivers/ath10k)  Should be supported in kernel 3.20

EDIT: after searching it looks like 168c:003e is the one that is added, happens to be the Qualcomm Killer N1525

---

### Post by Pilot6 on 2015-02-14
The Lenovo block has been fixed upstream.
Ath10k is in 3.19 already. So that kernel must solve the problem.

---

### Post by chili555 on 2015-02-14
@jeremy31--

You might guide the OP through this and see if it springs to life: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/)

---

### Post by Pilot6 on 2015-02-14
Why 3.19rc1, if 3.19 is released? Why not just install it from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-vivid/)

---

### Post by chili555 on 2015-02-14
3.19-rc1 is the latest backports package available. Your link is to the entire kernel. With backports, you are able to select only the driver you want and install, and remove if it's ineffective, a relatively slender package on your existing linux-image.

EDIT: I compiled backports as above and find this:```
$ modinfo drivers/net/wireless/ath/ath10k/ath10k_pci.ko
filename:       /home/chili/Desktop/Forum/backports-3.19-rc1-1/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
srcversion:     FD00C94F84CCF97E4201BD2
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]003C[/COLOR]sv*sd*bc*sc*i*
depends:        ath10k_core,compat
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

```Therefore, your device  Qualcomm Atheros Device [[COLOR="#FF0000"]168c:0041[/COLOR]] (rev 20)  is not covered.

Pilot6, if you have tested the 3.19 kernel, then I suggest you guide him on the installation.

---

### Post by DOS286 on 2015-03-18
I am also trying to install Ubuntu on a Yoga 3 14" with the same wireless device. Did anyone find a solution to this?

---

### Post by jsalisbury2 on 2015-03-26
There is some discussion about this device upstream.  It looks like there are some firmware issues, but a fix is in the works: 

 [http://permalink.gmane.org/gmane.linux.drivers.ath10k.devel/2057](http://permalink.gmane.org/gmane.linux.drivers.ath10k.devel/2057)

---

### Post by jsalisbury2 on 2015-03-26
Also, there is now a bug opened in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)

---

### Post by Shuran_Li on 2015-04-04
> **jsalisbury2 said:**
> Also, there is now a bug opened in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)


Thanks for the attention to this matter.

---

### Post by btsulliv on 2015-05-03
I am also having this problem on a newly purchased Lenovo Yoga 3 14". Would you suggest that upgrading the kernel is the best option? Or should we try the old [driver fix solution]("http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/") from the Yoga 2 13"?

---

### Post by chili555 on 2015-05-03
> **btsulliv said:**
> I am also having this problem on a newly purchased Lenovo Yoga 3 14". Would you suggest that upgrading the kernel is the best option? Or should we try the old [driver fix solution]("http://billauer.co.il/blog/2014/08/linux-ubuntu-yoga-hardware-blocked-wireless-lan/") from the Yoga 2 13"?There are two issues discussed here; hard-blocked and a specific Atheros wireless device. Which is yours?```
lspci -nn| grep 0280
rfkill list all
uname -r
```

---

### Post by btsulliv on 2015-05-05
I am running 15.04 Vivid

ubuntu@ubuntu:~$ lspci -nn| grep 0280
02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
ubuntu@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ uname -r
3.19.0-15-generic

---

### Post by chili555 on 2015-05-06
> 0: ideapad_wlan: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]May I safely assume that pressing the wireless button or key combination does nothing? You might get the key to respond by removing the module that is supposed to but doesn't control it correctly:```
sudo modprobe -r ideapad-laptop
rfkill list all
```Even when you get the button working, you still have this:>  Qualcomm Atheros Device [[COLOR="#FF0000"]168c:0041[/COLOR]] (rev 20)It is a very new device for which there is no working driver and not even a hint at what might experimentally work if we hack the driver like the ham-handed amateurs we really are.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)  I suggest you register and add to the bug report.

In the meantime, I suggest you temporarily get a USB wireless. There are threads here and on askubuntu.com regularly about known working devices.

---

### Post by btsulliv on 2015-05-06
Pressing the "Airplane Mode" button affects the soft block, but does nothing about the hard block. I am going to get a wired connection and try to update the Broadcom drivers to see if that helps. I had already tried the modprobe command previously to no avail.

---

### Post by chili555 on 2015-05-06
> **btsulliv said:**
> Pressing the "Airplane Mode" button affects the soft block, but does nothing about the hard block. I am going to get a wired connection and try to update the Broadcom drivers to see if that helps. I had already tried the modprobe command previously to no avail.Why? You have no Broadcom. As you told us, you have:```
Qualcomm Atheros Device [168c:0041] (rev 20)
```A complete update is always desirable but Additional Drivers will not magically find a driver for your Atheros; none exists.

---

### Post by btsulliv on 2015-05-06
> **chili555 said:**
> Why? You have no Broadcom. As you told us, you have:```
Qualcomm Atheros Device [168c:0041] (rev 20)
```A complete update is always desirable but Additional Drivers will not magically find a driver for your Atheros; none exists.

Yes, you are correct. If I get a USB wireless adapter (e.g. this [TP-LINK N150 Wireless Nano USB Adapter]("http://www.tp-link.com/lk/products/details/?model=TL-WN725N")), how do I know that I won't run into the same problem? How likely do you think I am to be able to use a wireless USB right out of the box? Thank you again for your input, reading your previous posts it's obvious you know your stuff.

---

### Post by chili555 on 2015-05-07
>  how do I know that I won't run into the same problem? How likely do you think I am to be able to use a wireless USB right out of the box? Because, as I said:> There are threads here and on askubuntu.com regularly about known working devices. Search for them here or on Google. [https://www.google.com/search?client=ubuntu&channel=fs&q=working+USB+wireless+Ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=working+USB+wireless+Ubuntu&ie=utf-8&oe=utf-8) I understand that some of them are available for as little as US$10.

Your issue with the wireless button may get fixed with an update but, if not, we can probably fix it pretty easily. The button often also affects USB wireless.

---

### Post by geoff-2 on 2015-05-07
> **btsulliv said:**
> Yes, you are correct. If I get a USB wireless adapter (e.g. this [TP-LINK N150 Wireless Nano USB Adapter]("http://www.tp-link.com/lk/products/details/?model=TL-WN725N")), how do I know that I won't run into the same problem? How likely do you think I am to be able to use a wireless USB right out of the box? Thank you again for your input, reading your previous posts it's obvious you know your stuff.


FWIW, I have the same issue with my Yoga 3 and I ended up getting a cheap USB Wifi adapter from monoprice which worked right away.  It's probably not the fastest or most robust option out there, but for the price, it does the job well.  Until drivers are available for the internal wifi card.

---

### Post by btsulliv on 2015-05-16
Anyone have an update on this issue?

---

### Post by chili555 on 2015-05-17
> **btsulliv said:**
> Anyone have an update on this issue?Not yet, it seems.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)

---

