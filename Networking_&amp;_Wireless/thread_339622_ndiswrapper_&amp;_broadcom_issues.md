---
title: "ndiswrapper &amp; broadcom issues"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by DJCreation on 2007-01-16
Hi folks, noob here.

I'm running a Dell E1705 dual-boot and having issues with the Broadcom 4328 chipset wireless Dell provides.

Fresh install of 6.06, downloaded the tar of ndiswrapper (1.34) using the windows-side partition, make && make install 'n' all that jazz, seem to get the driver working... well, somewhat alright.

However the Sys-->Networking applet started to throw issues at me. Entered the WEP key, wouldn't connect to the network. So I went into a terminal, rocked the

> sudo iwconfig wlan0 key XXXXXXXXXXXX

Lo and behold the meter-thingy (forgive me, can't remember the name of the damned thing) lit up, but following that, couldn't pull up Google.

So I looked at the dmesg and found the following (what seems to me to be important, inexperienced as I am at this, is in **bold**:

> [17179596.592000] ndiswrapper version 1.34 loaded (preempt=yes,smp=no)
[17179596.660000] ndiswrapper: driver bcmwl5 (Broadcom,06/21/2006, 4.80.28.5) loaded
[17179596.660000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179596.660000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[17179596.672000] ndiswrapper: using IRQ 177
[17179597.308000] wlan0: ethernet device 00:19:7d:30:fc:87 using NDIS driver: bcmwl5, version: 0x4501c05, NDIS version: 0x501, vendor: '', 14E4:4328.5.conf
[17179597.308000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179597.308000] usbcore: registered new driver ndiswrapper
**[17179597.308000] ndiswrapper (add_wep_key:820): adding encryption key 1 failed (C0010015)**
[17179664.156000] ACPI: AC Adapter [AC] (on-line)
[17179664.176000] ACPI: Battery Slot [BAT0] (battery present)
[17179664.236000] ACPI: Lid Switch [LID]
[17179664.236000] ACPI: Power Button (CM) [PBTN]
[17179664.236000] ACPI: Sleep Button (CM) [SBTN]
[17179664.296000] ibm_acpi: ec object not found
[17179664.324000] pcc_acpi: loading...
[17179664.400000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179664.404000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179664.404000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179669.336000] ppdev: user-space parallel port driver
[17179669.636000] apm: BIOS not found.
[17179682.848000] Bluetooth: Core ver 2.8
[17179682.848000] NET: Registered protocol family 31
[17179682.848000] Bluetooth: HCI device and connection manager initialized
[17179682.848000] Bluetooth: HCI socket layer initialized
[17179682.868000] Bluetooth: L2CAP ver 2.8
[17179682.868000] Bluetooth: L2CAP socket layer initialized
[17179682.872000] Bluetooth: RFCOMM socket layer initialized
[17179682.872000] Bluetooth: RFCOMM TTY layer initialized
[17179682.872000] Bluetooth: RFCOMM ver 1.7
[17179685.844000] NET: Registered protocol family 10
[17179685.844000] lo: Disabled Privacy Extensions
[17179685.844000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179685.844000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179685.844000] IPv6 over IPv4 tunneling driver
[17179688.404000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179688.480000] ISO 9660 Extensions: RRIP_1991A
[17179718.628000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17179729.136000] wlan0: no IPv6 routers present

Not sure if the bolded above really is the problem or not, and if so, what to do about it from this point. Any help would be greatly appreciated.

PS-

A previous install, same OS and ndiswrapper, worked fine (I had to reinstall because I got too big for my britches and started playing with the kernel despite not having a clue what I was doing. Thankfully it's a new box, so there wasn't anything important lost as a result except my oversized ego) - a bit of tinkering and I got online.

Why I'm running into this issue now is beyond me, but hey - that's why I'm a noob ;)

---

### Post by flyingsolo on 2007-01-16
Sorry but I can't help your issue but I'm trying to get the same Dell with bcm4328 to work.  You seem to be ahead of me!  Could you give details of how you got a valid driver to work with ndiswrapper 1.34?  I've got to point of installing 1.34 and bcmwl5 but when I do:
ndiswrapper -l  I get:
bcmwl5 : invalid driver!
I'm stumped and need help--thanks.

---

### Post by Floppyjoe on 2007-01-16
> Sorry but I can't help your issue but I'm trying to get the same Dell with bcm4328 to work. You seem to be ahead of me! Could you give details of how you got a valid driver to work with ndiswrapper 1.34? I've got to point of installing 1.34 and bcmwl5 but when I do:
ndiswrapper -l I get:
bcmwl5 : invalid driver!
I'm stumped and need help--thanks.
Reply With Quote

Were you in the right directory in the terminal when you installed the driver?Did you have the necessary files in that directory?

---

