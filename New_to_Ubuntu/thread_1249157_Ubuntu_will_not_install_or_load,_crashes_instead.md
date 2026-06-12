---
title: "Ubuntu will not install or load, crashes instead"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by dreamscaper555 on 2009-08-25
[SIZE=3]I am trying to install ubuntu 9.04 Desktop on my desktop computer. Every time the splash screen gets about 1/8 of the way done, it freezes and gives this error: init: rc-default main process (2882) terminated with status 127. I have tried using the safe graphics mode and a few of the other options as well with no luck. I also burned the iso on the slowest setting and checked the MD5's on everything and it is all as it should be.

Here is what I am trying to run this on:

Via Belarc:
[/SIZE]
[SIZE=2]System:Compaq Presario 061 DW255A-ABA Original mobo, but diff HDD's, optical, and a wireless card added
[/SIZE]**[SIZE=2]Processor: [/SIZE]**[SIZE=2]2.80 gigahertz Intel Celeron
8 kilobyte primary memory  cache
128 kilobyte secondary memory cache
Not hyper-threaded

[/SIZE][B][SIZE=2]Main Circuit Board :
[/SIZE][/B][SIZE=2]Board: MICRO-STAR INTERNATIONAL CO., LTD Gamila/Giovani/Neon series  030
Serial Number: 4113185351
Bus Clock: 100 megahertz
BIOS: Phoenix  Technologies, LTD 3.06 12/31/2003

Drives: [/SIZE][SIZE=2]620.12 Gigabytes Usable Hard Drive Capacity
547.43 Gigabytes  Hard Drive Free Space

CD-ROM Drive
LITE-ON LTR-48247S [CD-ROM  drive]

MAXTOR STM3500630A [Hard drive] (500.11 GB) -- drive 0, s/n  9QG54T1W, rev 3.AAE, [SMART]("http://www.belarc.com/smart.html")  Status: Healthy
WDC WD1200BB-00DWA0 [Hard drive] (120.03 GB) -- drive 1, s/n  WD-WMAEK2405620, rev 15.05R15, [SMART]("http://www.belarc.com/smart.html") Status: Healthy

memory:[/SIZE][SIZE=2]2040 Megabytes Usable Installed Memory

Slot 'A0' has 1024  MB
Slot 'A1' has 1024 MB

Display: [/SIZE][SIZE=2]Intel(R) 82845G/GL/GE/PE/GV Graphics Controller [Display  adapter]
VisionTek Radeon X1300 Series [Display adapter]
VisionTek Radeon  X1300 Series Secondary [Display adapter]
Default Monitor (2x)

Audio: [/SIZE][SIZE=2]Realtek AC'97

Wireless Card: [/SIZE][SIZE=2]    


 [SIZE=2]D-Link WDA-2320 Desktop Adapter[/SIZE][/SIZE]
[SIZE=2]What should I do to get this thing installed and running with my hardware?
[/SIZE]

---

### Post by TuckLive on 2009-08-25
Reboot your computer with the Ubuntu cd in.  When it comes up to the menu choose check cd for errors.  If you downloaded the iso as a torrent it may be that the image is bad and you'll need to download and burn another cd.

---

### Post by dreamscaper555 on 2009-08-25
> **TuckLive said:**
> Reboot your computer with the Ubuntu cd in.  When it comes up to the menu choose check cd for errors.  If you downloaded the iso as a torrent it may be that the image is bad and you'll need to download and burn another cd.

But I burned at 4x, and checked the MD5sums and they were good both before and after burning the cd. I also am having the exact same problem when I try to run Linux Mint 7 and Linux Mint 5, both of which I checked the MD5sums on as well. I did run the cd checker on Linux Mint 7 and it said it was fine. I can run it for this Ubuntu disk if need be, but I am pretty sure that is not it. Also, it seems to freeze up at the squashfs part and give a bunch of squashfs errors in Mint. Couldn't get it to do that on Ubuntu 9, but it has all of the same symptoms otherwise.

---

### Post by nhasian on 2009-08-25
please try the alternate installer instead:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by zkriesse on 2009-08-25
Alright....but check the disk anyway. Doesn't hurt.

---

### Post by dreamscaper555 on 2009-08-25
> **nhasian said:**
> please try the alternate installer instead:

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Okay, I will get that and try it and report back.

---

### Post by TuckLive on 2009-08-25
I would try the cd checker since it doesn't take to long.  It would eliminate the cd as the problem.  If the cd is good or you might could try using the livecd and try the option "Try before installing" then look through the logs to see if you can maybe find what hardware is holding you up.  I know this is taking a stab in the dark, but maybe it'll help.

---

### Post by dreamscaper555 on 2009-08-25
[SIZE=3]Okay, so I managed to install ubuntu 9.04 x86 alternate version onto my hard drive (the 120 gig one, I rewrote the entire drive). However, after all that was said and done I removed the disk and it reloaded via the 120 gig HDD and crashed in the same spot as with the live CD (1/8 of the way through the splash bar). It spat out some error messages as well.

And Before anyone asks, I did the MD5sum check on the iso, and a few files on the CD, AND ran the disc checker, AND wrote at the slowest speed possible. Everything came up clean. I also used cdburnerXP which has been the most reliable software I have ever used for burning iso images (K3B is good too though). So it's not the disk.[/SIZE] 

[SIZE=3]As a matter of fact, after I read these last error messages it became obvious that it is a driver problem, my best guess is with the motherboard.There is no video card except the onboard one, however I do have a vid card that I could PROBABLY (assuming the ports match) put in it's place if the on board video turns out to be the culprit. The other card I have is a used Radeon 9600 XT.

Anyway, this is what happened after the stall in the splash screen:

It switched to text mode and started loading the system and went down the line ok until it said loading drivers and then there was the crash.

First it gave a string of different error messages ending with "abnormal exit". Then I went to go get a pen and paper and when I came back it moved onto a different string of error messages that read "unable to execute /sbin/getty for tty3 no such file or directory" and "init: tty4 main process [1493] terminated with status 255"

Then control alt deleting did nothing and I had to hold the power button to shut down the cpu. Also it should be noted I tried recovery mode already with the same errors.

So like I said it is probably the motherboard. As such, I will list below everything that you ever wanted to know about my mobo:

[/SIZE]**Motherboard specification table**
                                                                                                         Part/Feature                                                               Specifications/Supports                                                                                                                              **Motherboard Description**                                          MIS name: MS-6577 M-ATX Rev. 3.1 (Giovani), Rev. 4.0 (Giovani2)

Compaq name: Giovani-GL6, Giovani2-GL6                                                                                    **CPU **                                                               
[LIST]
[*]    Socket 478 for Intel P4 Williamette and Northwood processors
[/LIST]



[LIST]
[*]    Supports Intel Pentium 4 processor up to 2.8 GHz
[*]    Supports Intel Celeron processor up to 3.06 GHz (Prescott based Celeron with 533MHz FSB)
[/LIST]


                                                                                   ** Intel 845GV Chipset**                                                               
[LIST]
[*]FSB 400/533
[*]Multiplexed AGP interface
[*]Integrated 3D/2D graphic core
[*]Supports DDR 333/266/200 memory
[/LIST]
                                                                                                         **Intel ICH4 Chipset**                                                               
[LIST]
[*]High speed USB 2.0 controller, 480Mb/sec
[*]PCI Master 2.2
[*]I/O APIC
[*]AC'97 2.2 interface
[*]Three  UHCI host controllers
[*]One EHCI host controller
[/LIST]
                                                                                                         **Main Memory**                                                               
[LIST]
[*]Two 184-pin DDR DIMM
[*]Maximum memory size is up to 2GB, 1GB per slot.
[*]HP recommends a maximum memory of 1GB, 512MB per slot.
[*]Supports PC2100 0r PC2700 unbuffered non-ECC
[/LIST]
                                                                                                         **Slots**                                          Three 32-bit Master PCI (peripheral component interconnect) Bus slots                                                                                    **Onboard IDE**                                                               
[LIST]
[*]IDE HDD/CD-ROM operation modes:
[LIST]
[*]PIO
[*]Bus Master
[*]Ultra DMA 100/66
[/LIST]
 
[*]Connect up to four IDE devices
[/LIST]
                                                                                                         **Onboard Peripherals**                                                               
[LIST]
[*]Two PS/2 ports
[*]Six USB ports (four front, two rear)
[*]One Parallel port
[*]One Serial port
[*]One VGA
[*]One RJ-45 LAN port
[*]Vertical audio ports (line-in, line-out, microphone-in)
[/LIST]
                                                                                                         **Connectors**                                                               
[LIST]
[*]Two IDE  (ATA 100)
[*]One ATX power
[*]One Floppy
[*]One AUX-in
[*]One Mic-in
[/LIST]
                                                                                                         **Pinheaders**                                                               
[LIST]
[*]One Front panel
[*]One Clear password
[*]One Clear CMOS
[/LIST]
                                                                                                         **Audio**                                                               
[LIST]
[*]AC'97 link controller integrated in ICH4
[*]Six-channel software codec RealTek AL658 (optional)
[/LIST]
                                                                                                         **LAN**                                                               
[LIST]
[*]RealTek RTL8101L chip
[*]Integrated Fast Ethernet MAC AND PHY (one chip)
[*]Supports 10 Mb/s and 100Mb/s
[*]Compliance with PCI V2.2
[*]Supports ACPI Power Management
[/LIST]
                                                                                                         **BIOS**                                                               
[LIST]
[*]PnP (plug & play) to detect peripheral devices and expansion cards automatically.
[*]DMI (desktop management interface) function to record motherboard specifications.
[/LIST]
                                                                                                         **Dimension**                                          Micro-ATX form factor

**[SIZE=5]SO what is the next step?[/SIZE]**

---

### Post by R3fr4cti0n on 2009-08-25
i had this problem on my laptop, this may sound stupid but i had to keep the screensaver or anything else from disturbing the screen. try moving the mouse every few minuets during  install..

---

### Post by dreamscaper555 on 2009-08-25
> **R3fr4cti0n said:**
> i had this problem on my laptop, this may sound stupid but i had to keep the screensaver or anything else from disturbing the screen. try moving the mouse every few minuets during  install..

Actually, I already have it installed now thanks to the alternate install cd, but it still crashes just like it did when attempting to run the live cd or install with the regular cd. Right at the part when it has decided what drivers to load and attempts to load them for Ubuntu, or the squashfs part with mint (I have tried both).

Also, this is a slightly dated compaq presario desktop I am using. However, I will restart and try loading Ubuntu from the drive and move the mouse around so I can rule this possibility out... BRB

---

### Post by dreamscaper555 on 2009-08-25
> **dreamscaper555 said:**
> Actually, I already have it installed now thanks to the alternate install cd, but it still crashes just like it did when attempting to run the live cd or install with the regular cd. Right at the part when it has decided what drivers to load and attempts to load them for Ubuntu, or the squashfs part with mint (I have tried both).

Also, this is a slightly dated compaq presario desktop I am using. However, I will restart and try loading Ubuntu from the drive and move the mouse around so I can rule this possibility out... BRB

Nope, didn't work. It stalled at exactly the same spot. Also noted. no mouse cursor was ever present. But I also hit keys on the keyboard.

---

### Post by dreamscaper555 on 2009-08-25
I am still working on this problem if anyone would care to help or direct me to the correct place to get help with my issue. Please.

---

### Post by nhasian on 2009-08-26
hello,

i'm sorry you are having such difficulty installing ubuntu.  it is quite unusual but i have another suggestion that may help you.  I noticed from your detailed specs that your motherboard has builtin video and uses the intel graphics chip.  I know there were lots of problems with intel graphics cards and 9.04.  the new Karmic Koala fixed a lot of video problems for intel GPUs.  

here is the latest karmic iso for 32bit processors:

[http://cdimage.ubuntu.com/daily/current/karmic-alternate-i386.iso](http://cdimage.ubuntu.com/daily/current/karmic-alternate-i386.iso)

---

### Post by venividivici24 on 2012-05-01
> **dreamscaper555 said:**
> I am still working on this problem if anyone would care to help or direct me to the correct place to get help with my issue. Please.
I don't know if you're still having the problem, but I thought I would try and help. Make sure that you have the other graphics card in first. I had exactly the same problem with my computer, same specs and everything. Somehow a friend of mine found the answer. When you boot into the live cd, not the alternate install,  (make sure that the Try Ubuntu before install is selected) press F6 to bring up the advanced options, then press ESC. There should be a line of text at the bottom of the screen now. Type in   agpart.blacklist=true intel_agp.blacklist=true. I hope that this helps. Ubuntu 12.04 works like a charm for me, so maybe you could try that if this doesn't work.

---

