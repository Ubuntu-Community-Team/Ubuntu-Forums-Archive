---
title: "[Intel Dual Band AC 7265] Bluetooth not working BUT wifi does. Whats wrong?"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by GhettoGirl on 2015-10-10
[COLOR=#ff0000][SIZE=6]**Problem finally solved, take a look to the last thread if you have the same issue :)**[/SIZE][/COLOR]

Hello dear forum members. This is my first post in here.
I recently purchased a new laptop since my old one is over 8 years old. Got quite anything working except the built-in bluetooth. After wasting days of my life (online research so far) I desided to ask the community to help me...
Just to clarify some things out. I'm linux user since my whole life, but I can't fix this problem for some reason.

The Laptop [[TUXEDO Book XC1705]("http://www.tuxedocomputers.com/Linux-Hardware/Linux-Notebooks/17-3-Zoll/TUXEDO-Book-XC1705-17-3-matt-Full-HD-bis-NVIDIA-Geforce-GTX-980M-Grafik-bis-vier-SSD-HDD-Intel-Core-i7-Quad-Core-bis-32GB-RAM.geek")] comes with the **Intel® Dual Band AC 7265 + Bluetooth** pci card. Wifi works 100% without any drops or anything else :D But Bluetooth doesn't...

```

Distro: Ubuntu 15.04 "Vivid Vervet" x86_64
uname -a
Linux 4.1.0-040100rc8-generic #201506150335 SMP Mon Jun 15 02:37:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
lspci
04:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)
```
This is also quite strage for me. Why is shows 8260 and not 7265? Does the manufactor lie to me :x 

```
hciconfig
hci0:   Type: BR/EDR  Bus: USB
        BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
        DOWN 
        RX bytes:13885 acl:0 sco:0 events:2309 errors:0
        TX bytes:579390 acl:0 sco:0 commands:2309 errors:0
```
There is no BD address. Is that because it cannot activate the device?

```

hciconfig -a hci0 up
Can't init device hci0: No such device (19)
```

```
dmesg
[20649.693922] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[20649.698927] Bluetooth: hci0: Device revision is 5
[20649.698930] Bluetooth: hci0: Secure boot is enabled
[20649.698932] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[20649.699055] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[20651.036105] Bluetooth: hci0: Failed to send firmware data (-38)
```

Let me know if you guys need some more info.
I hope someone can help me get that damn built-in bluetooth to work. I won't waste a usb port for external bluetooth dongle anymore, especially when I have a built-in one.

EDIT: some side note
bluetooth services works normal, with my external bluetooth usb dongle I can use everything like speakers, keyboards, mice and stuff

EDIT2: solved

---

### Post by GhettoGirl on 2015-10-13
bump

---

### Post by jeremy31 on 2015-10-13
I would file a bug report, start at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

I am not familiar with that bluetooth chipset

It almost looks like the dmesg info was from after a suspend/sleep mode...does the dmesg info look the same after a shutdown and boot?

---

### Post by GhettoGirl on 2015-10-13
I never put laptops in sleep/standby mode, ONLY hibernation. But the dmesg output never changes across reboots or resumes from hibernations.
I even tried symlinking different firmware files, but it displays all kind of errors in dmesg and bluetooth just won't work.

```
rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

Also, the device is NOT softlocked nor hardlocked. This error is indeed very strange. Perhaps I should contact the manufactor, maybe they can help a little bit more.

---

### Post by GhettoGirl on 2015-10-23
bump...
just can't get that damn bluetooth to work. no one that can help? :icon_frown:

---

### Post by howefield on 2015-10-23
Might be worth using a 15.10 live CD/USB media if you can, and testing out the updated [bluetooth]("https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes") support.

---

### Post by GhettoGirl on 2015-10-23
So, I booted up into a 15.10 live session to check some things. Bluetooth and Wifi is working out of the box. (:
Now the strange part: I just played around a little bit - never installed or touched the system in any form -, than I rebooted back to the main OS and out of the sudden bluetooth works. What is even happening :lolflag: whyyyy-what?

Can it be that the live session did something with the hardware? That CAN'T BE...

I'm not sure if I should mark the thread as [SOLVED] :???:

EDIT: if things don't break "out of the sudden" the next 2~3 reboots, than i will mark the thread as solved

---

### Post by howefield on 2015-10-23
Well, that's good news :)

If your existing install doesn't survive a cold reboot with a working bluetooth connection, at least it looks like an install of 15.10 will sort you out.

---

### Post by GhettoGirl on 2015-10-23
Good news and finally solved this pesky issue :D (without updating ubuntu itself)
NOTE: after a reboot I had the same issue with firmware not sending

Here are the steps what I did to help others.

**1.** Download the current kernel source from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) (for me 4.1.0-rc8)
**2.** Apply the patches according to the *SOURCES* file
**3.** Apply this patch here -> [https://lkml.org/lkml/2015/7/31/1248](https://lkml.org/lkml/2015/7/31/1248) | 4.1-stable review patch, [PATCH 4.1 017/267] Bluetooth: btusb: Fix secure send command length alignment on Intel 8260
**4.** Compile the kernel... (took a very very long time......)
**5.** Extract the *bluetooth* folder from *(deb)/kernel/driver/bluetooth* and place it into my real modules folder (override files, make sure that you create a backup first)
**6.** Run _modprobe -r btusb_ and _modprobe btusb_
**7.** Bamm!! Bluetooth works! :mrgreen: (without updating kernel/ubuntu system)

I finally can use my internal bluetooth which also survives cold reboots (: and the best of all: wifi didn't broke, now both works like a charm

but thank you anyway for the 15.10 livecd tip. maybe someday I will upgrade - when the time has come

---

