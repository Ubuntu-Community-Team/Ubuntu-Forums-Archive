---
title: "various questions.."
date: 2009-05-25
forum: New to Ubuntu
---

### Post by rvgsd on 2009-05-25
Hi.. I recently Installed Xubuntu 8.04.1 LTS, and I use Kernel 2.6.24-19 (new kernels above this one stop my wireless..!)
I had a few questions and I would be glad if someone could answer,

1. What should I add to my fstab file, so that I can read/write in my Windows partition?
(Currently, I use '**sudo mount -t ntfs-3g  /dev/sda1 /media/Win**'. This works perfect, but I have to do this every time I restart the system.)

2. The exact same problem with my Western Digital External Harddrive. I can read/write to it using 
**'sudo mount -t vfat /dev/sdb1 /mnt/External -o iocharset=utf8,umask=000'**.
Can this be somehow entered into the fstab file? or somewhere else?

3. The current release of VLC player is 0.9.9, but my synaptic shows 0.8.6. Why does this happen? how do I fix it?

Appreciate all the help.
Thanks

---

### Post by superprash2003 on 2009-05-26
the newer versions of ubuntu handles this automatically.. try 8.10 or 9.04

---

### Post by Jimmynemo2 on 2009-05-26
Since you did say you cant use newer kernels, how about this:

In the repo's is a program called ntfs config - use that- you show it your ntfs drives, and it configures them in your fstab. I use it for all my non primary ntfs drives, and it works like a charm. Use it once, and never need it again.

Hope this helps.

---

### Post by rvgsd on 2009-05-26
Thanks, ntfs-config looks good. I will try.!

---

### Post by kpkeerthi on 2009-05-26
> **rvgsd said:**
> 
1. What should I add to my fstab file, so that I can read/write in my Windows partition?
(Currently, I use '**sudo mount -t ntfs-3g  /dev/sda1 /media/Win**'. This works perfect, but I have to do this every time I restart the system.)

> **rvgsd said:**
> 
2. The exact same problem with my Western Digital External Harddrive. I can read/write to it using 
**'sudo mount -t vfat /dev/sdb1 /mnt/External -o iocharset=utf8,umask=000'**. Can this be somehow entered into the fstab file? or somewhere else?


See [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

> **rvgsd said:**
> 
3. The current release of VLC player is 0.9.9, but my synaptic shows 0.8.6. Why does this happen? how do I fix it?

Ubuntu does not (always) keep up with upstream releases. See [https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

[https://edge.launchpad.net/~c-korn/+archive/vlc]("https://edge.launchpad.net/~c-korn/+archive/vlc")

---

### Post by Jimmynemo2 on 2009-05-26
Glad to hear it, and if you have any issues or that doesnt do the trick, feel free to reply again and we'll see what better we can do.

---

### Post by rvgsd on 2009-05-26
Thank you for all the help! I should be good with this info :)

---

### Post by anewguy on 2009-05-26
For the heck of it, what wireless adapter do you have?  You could post back the output of lspci (and lsusb if it's a laptop or the adapter is usb).

If your wireless works in earlier kernels, I would think we should be able to make it work with restricted drivers, ndiswrapper or some other method (madwifi perhaps if the chipset is correct).

If all that was holding you back was wireless, how about if we try to track down a solution for you, then you can update and be prepared to get your wireless going when you do.

Dave :)

---

### Post by blueridgedog on 2009-05-26
You might also try the current livecd to see if the wireless issue is resolved, or take the offer to work through the problems once you upgrade.

---

### Post by rvgsd on 2009-05-26
Hi, Thanks for replying!!
If my wireless starts working on the new Kernels or the 9.04 versions of the distro, it would be AWESOME.!

I use **Broadcom 4306** wireless adapter, and use **b43-fwcutter** to install the drivers for it. 
I have tried to get it working on Ubuntu 9.04, after a week of (tiring and unsuccesfull) attempts and various suggestions on the internet, I gave up and downgraded to xubuntu 8.04 with 2.6.24-19.

Here is the output of lspci:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller

```

Any suggestion are welcome!!

---

### Post by anewguy on 2009-05-27
I think that card should work with the included restricted driver.  I myself prefer using ndiswrapper just from habit.  There are a lot of posts here for using the restricted driver, and if you want to try ndiswrapper just let me know.

It may be a simple matter of something not getting blacklisted (or perhaps is already blacklisted).

Dave :)

---

