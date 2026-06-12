---
title: "Stuck at Wubi install screen"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by MillCzarr on 2011-06-28
Okay, well before I was in the version 10.10, but since I was fine with Windows, I un-installed it.

But now, I've decided to install Ubuntu "11.04" back on my computer. But I'm stuck. When I click wubi.exe, then fill in the boxes, and then click "Install", it just gets stuck.

It really stops when it says: "Downloading ubuntu 11.04-desktop-amd64.iso.torrent"

I've been waiting 3 hours on this screen. The green bar hasn't even moved 1 bit. I've cancelled, and tried to install again 3 times. Still no progress.

Let me post my specifications:
OS: Windows 7 64-bit
Processor: AMD Sempron Processor LE-1300, ~2.3GHz
Memory: 2048MB
Graphics: NVIDIA GeForce 6150SE nForce 430

I've been searching for awhile now, and still haven't found a solution. Please help me...

---

### Post by climhazzard36 on 2011-06-28
Your best off not using wubi as it slows drive performance.

If you install ubuntu from a live cd there is an option to install it side-by-side with Windows. This has worked perfectly every time for me and you can select how much space to allocate to the new install.

Hope this helps :)

---

### Post by dFlyer on 2011-06-28
Download the live desktop cd and testdrive it first to be sure all your hardware is supported. I would recommend a dual boot system with windows on a partition and ubuntu on it's own partitions instead of running wubi which is running linux through windows itself.

---

### Post by bcbc on 2011-06-28
> **dFlyer said:**
> Download the live desktop cd and testdrive it first to be sure all your hardware is supported. I would recommend a dual boot system with windows on a partition and ubuntu on it's own partitions instead of running wubi which is running linux through windows itself.
Not true. Wubi runs in Windows. Ubuntu installed with Wubi does not.

> **MillCzarr said:**
> Okay, well before I was in the version 10.10, but since I was fine with Windows, I un-installed it.

But now, I've decided to install Ubuntu "11.04" back on my computer. But I'm stuck. When I click wubi.exe, then fill in the boxes, and then click "Install", it just gets stuck.

It really stops when it says: "Downloading ubuntu 11.04-desktop-amd64.iso.torrent"

I've been waiting 3 hours on this screen. The green bar hasn't even moved 1 bit. I've cancelled, and tried to install again 3 times. Still no progress.

Let me post my specifications:
OS: Windows 7 64-bit
Processor: AMD Sempron Processor LE-1300, ~2.3GHz
Memory: 2048MB
Graphics: NVIDIA GeForce 6150SE nForce 430

I've been searching for awhile now, and still haven't found a solution. Please help me...

You can download the ISO yourself and place it in the same folder as wubi.exe. When you run wubi it will find it and use it.
See [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation) for more information on your options.

---

### Post by beew on 2011-06-28
Don't bother with WUBI, it is buggy, unstable and it adds unnecessary complications because it has to work through windows and is limited by it. If you are nervous about partitioning your hard drive install Ubuntu in an external hard drive. Basically the same step as you would do an internal install, but make sure you install into the correct drive (sda is the internal drive so the external one would be sdb or sdc, and install the bootloader in the partition where Ubuntu is install instead of the drive,--so install bootloader in sdc1 instead of sdc, if sdc is your external drive)

[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

This is for 10.04 but the idea is the same for 11.04, choose "something different" when the screen asks you to choose the way to install.  The guide talks about intsalling in an usb flash drive, it is exactly the same for external hard drive but external hard drive is a lot faster and gives the same performance as installing internally (except may be for boot up time depending on your BIOS)

---

### Post by Frogs Hair on 2011-06-28
In some cases the firewall needs to be disabled for torrent to download  . On Win 7 a message should  appear offering that option .

---

### Post by MillCzarr on 2011-06-28
Alright, I ended up downloading the .iso and putting it in the folder with the wubi. So now its installed.

So I thank you all for your help! :)

---

### Post by Rubi1200 on 2011-06-28
Glad you got this sorted out :-)

If you need information or help with Wubi issues, you can refer to these links:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Enjoy!

---

