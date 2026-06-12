---
title: "Ralink usb no longer detected after kernel upgrade"
date: 2016-03-19
forum: Networking &amp; Wireless
---

### Post by Evil Wayz on 2016-03-19
System did its normal upgrade of headers and image, and now my wireless doesn't show up.

Lsusb output:
```
 lsusb
Bus 001 Device 008: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 006: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 005: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 007: ID 1997:2433  
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 045e:0752 Microsoft Corp. Wired Keyboard 400
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I installed the driver for my adapter and got it to work for my Ralink wt7601 usb adapter using the following commands:
```
sudo apt-add-repository ppa:thopiekar/mt7601
sudo apt-get update
sudo apt-get install mt7601-sta-dkms
```

And it immediately detected it and worked.  And the first time the kernel upgraded, it worked fine.

As you can see, it is no longer detected as a usb device.  I checked to see if the driver was still installed and got this output:
```
sudo apt-get install mt7601-sta-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mt7601-sta-dkms is already the newest version.
```

sudo modprobe mt7601-sta outputs this though:
```
[sudo] password for wolf: 
modprobe: FATAL: Module mt7601-sta not found.
```

It was my understanding that by using the PPA i wouldn't have to compile the driver every time the kernel upgraded, which incidentally it has done three times in the last eight hours.

I am using the 3.16 kernel, and Cinnamon 2.8 on Ubuntu 14.04.4

---

### Post by jeremy31 on 2016-03-19
Unplug some unneeded USB devices and see if it gets found then

---

### Post by Evil Wayz on 2016-03-19
Ok, now when I type lsusb, it just sits there.  there is no output.

---

### Post by jeremy31 on 2016-03-19
Might a serious issue with the kernel, see if things work with the old kernel

---

### Post by Evil Wayz on 2016-03-19
Since this is the wireless forum I will add this.  MY bluetooth keyboard is now having issues.  THe computer insists that the battery power is at sero, but when I plug the keyboard in the green full power light comes on.  Restarting the computer works for a little bit.  Also I tried the teo earlier kernels in grub and they both hang at the Nivida test screen.  HELP.

---

### Post by Evil Wayz on 2016-03-19
Matter of fact, bluetooth is off and will not turn on.

---

### Post by Evil Wayz on 2016-03-19
OK, official list of things that are haywire:

Bluetooth insists that my keyboards battery is at 58%
nothing wireless will work.  I checked the hub, and anything else will work.  But my wireless n adapter and my 2.4 ghz adapter for my other keyboard aren't recognized.  I am definitely thinking this is a kernel issue as the computer worked fine before i removed the old headers and restarted my computer.   I would file a bug report but I don't know what to report.
Lsusb does not detect either wireless adapter.
driver for adapters are installed, but modprobe returns a fatal error.

---

### Post by jeremy31 on 2016-03-20
I wonder if the 4.2 kernel can fix this.  The source code for the PPA comes from [https://github.com/porjo/mt7601](https://github.com/porjo/mt7601) and it says

[h=1]DON'T USE!! This driver is old + buggy - use the official Linux driver instead[/h]

---

### Post by Evil Wayz on 2016-03-20
I don't believe my machine is capable of using the 4.2 kernel.  It installed with the 3.13 kernel, and 3.16 was as high as I could cheat up and still have it work.  How would I find out?

---

### Post by Evil Wayz on 2016-03-21
OK, I am now running the 4.3 kernel, and the ralink still doesn't work.

---

