---
title: "Wireless card not working after kernel upgrade"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by konsu77 on 2006-08-09
Hi gurus,

I downloaded and compiled the latest 2.6.17.8 kernel and compiled it keeping the old configuration. I have Dapper Drake and with the previous kernel everything was ok. 

My laptop is a DELL Latitude X300 with a Wireless LAN 2100 3B Mini PCI Adapter. Pls find below the lspci output.

The problem is I have is already seen by someone else SIOCGIFFLAGS error - no such device

Thanks for your help
Konrad

0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
0000:02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
0000:02:04.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
0000:02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)


iwconfig

lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.



ifconfig


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:458311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:458311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:37352285 (35.6 MiB)  TX bytes:37352285 (35.6 MiB)

---

### Post by hardyn on 2006-08-10
ditto...

exactly the same symtoms with intel 2915 card, after upgrade.

thanks.

---

### Post by hardyn on 2006-08-11
Ok... i tried rebuilding the kernel again using the current ubuntu specific kernel, and again killed the wireless... this really makes ask the question, what does ubuntu do to make there kernels work, and why wont mine?

i am rebuilding the kerel to try to beat the P-M / 686 kernel problem (other threads) and i can build the kernel just fine which takes care of the 686 problems, but defeats the wlan in the process.

I found a thread on a gentoo site that explained using the intel proprietary drivers and ieee modules (i have a intel wlan card) but it doesn't seem like it should be necessary, as i the wlan worked out of the box.  

i have tried the kernel rebuild with both the new ones 2.6.16 and the old one "kernel-source" and both have completed with the same loss of the wlan.

can somebody smarter than me please explain this?  mabe provide a solution?  do i really have to go through the intel mumbo-jumbo?

thanks.

---

