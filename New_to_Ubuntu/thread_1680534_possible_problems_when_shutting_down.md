---
title: "possible problems when shutting down"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by twowire on 2011-02-02
So, i'm extremely new with ubuntu, and when i shut down my computer, it always gives me this message, what does it mean, and how can i fix it?
thank you!
unmounting local file systems [FAIL]
 
also, i just remembered, sometimes it fails to terminate all processes...

---

### Post by theozzlives on 2011-02-02
Does it shut down?

---

### Post by twowire on 2011-02-02
yes, it does

---

### Post by cipherboy_loc on 2011-02-02
A quick question:
When you shut down, do you close out all applications before shutting down, or do you just click the shutdown button while your mail, Firefox, and your IM Client are still up?



Cipherboy

---

### Post by twowire on 2011-02-02
i close it all, then shut down...

---

### Post by cipherboy_loc on 2011-02-02
What version of Ubuntu are you running?


Cipherboy

---

### Post by twowire on 2011-02-02
ive got 10.10

---

### Post by cipherboy_loc on 2011-02-02
What hardware are you using (**sudo lspci** from the Terminal (Applications -> Accessories -> Terminal)) and how old would you say this install is (weeks, months, just updated from an old release (10.04, etc))? Also, what is the output of **sudo fdisk -l**, also from the terminal.


Cipherboy

---

### Post by twowire on 2011-02-02
Ok, so here's what i got:
```
 [sudo] password for anthony: 
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:11.0 PCI bridge: nVidia Corporation Device 0779 (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:09.0 Network controller: RaLink RT2800 802.11n PCI
01:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)
03:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
03:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
```

and it was installed about a month or two ago from my uncles flash drive...
then the last part:

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f17a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58985   473794560   83  Linux
/dev/sda2           58985       60802    14588929    5  Extended
/dev/sda5           58985       60802    14588928   82  Linux swap / Solaris


haha, if i did anything wrong, just let me know

---

### Post by twowire on 2011-02-02
oh, but this is a custom machine i'm still working all of the kinks out of it, i used to have windows on it, but it just wouldn't connect to the internet, so i went with ubuntu

---

### Post by cipherboy_loc on 2011-02-02
What is your processor type/architecture? Do these problems cause the shutdown to fail entirely (aka it won't shutdown unless you hold the power button), or does it still continue with a shutdown. Also, do these problems cause fsck to run more often than it should be (usually some where around 28-42 boots or 14 days)?


Cipherboy

---

### Post by twowire on 2011-02-02
umm... i'm not entirely sure, but i have an AMD Phenom II 1090T black edition...
it just seems to delay shutting down for a few seconds, but then shuts down. And no, it seems to be running around normally.
this hasn't caused any problems yet, i'm just hoping to avoid any...

---

### Post by cipherboy_loc on 2011-02-02
Have you tried looking at the SMART data of your drive? You will either have to google it for a command line utility or use the GNOME Disk Utility.


Cipherboy

---

### Post by Faan on 2011-02-03
when looking at the original post I am not sure that my problem is entirely the same.
I also have UBUNTU 10.10 installed on a PC where I had and still has Windows on.  When I start the system and shut down immediately everything works fine.  However when the PC has not been working for an hour or two and I want to shut down nothing happens. When looking at my keyboard it is switched / turned off and I think the same applies to the mouse. 

When thinking about it know I wonder whether it is not perhaps a communication problem between mouse and keyboard and the system.  I just do not know where to look to try and fix it.

Thanks

---

### Post by cipherboy_loc on 2011-02-03
@OP: Status update please?

@Faan: Do you get any messages about ACPI on boot? Google how to disable the splash screen if you don't know how. You just have to remove the words **quiet splash** from a file in /etc/grub.d/ (I forgot which file and I am on my iPod), and then run **sudo update-grub2**

Cipherboy

---

### Post by twowire on 2011-02-03
ok, sorry it took so long but i am back!
so, i have looked at the SMART data, but i cant find any issues there.

---

