---
title: "Formating Internal Hard Drive"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Themiband on 2011-02-28
Ok so my old pc finally gave up and my friend has given me his newer pc and together I have mashed them into 1 working machine with 2 internal hard drives, here are the specs below

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
01:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

My problem is that I also have another internal hard drive which is 800GB which I want to use instead, it is completely blank thou and will only fit onto the connectors that currently connect the 250GB hard drive that came with the newer PC. I've tried setting up Ubuntu on the other smaller 70GB hard drive but can't get it to boot up. Is there a way without using a cd drive (i have none, luckily my old hard drive is old enough to fit into the cd drive connectors on the newer pc) to make some kinda boot disky thingy on the older smaller hard drive so i can boot up off that and attach my 800GB hard drive

hope that makes sense any problems or clarifications you guys need let me know

---

### Post by Hippytaff on 2011-02-28
You can use a usb stick with something like[ unetbootin]("http://unetbootin.sourceforge.net/") to make a liveusb (bootable usb) thing.

But maybe I've completely missed the point.

---

### Post by Themiband on 2011-02-28
ah no that sounds a very very sensible idea i think i'll try that

i'm very new to this thou, heres problem number 2 i'm trying to install "gnomad" and it says in the install instructions 

"The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code"

I don't know how to "cd to the directory containing the package's source code

---

### Post by Themiband on 2011-02-28
ok so trying to run UNetbootin after i've downloaded it but i can't open bin files it seems, i'm getting quite lost now

---

### Post by alegomaster on 2011-02-28
I say you learn some basic UNIX command line skills before you go too much into Ubuntu.

---

### Post by Themiband on 2011-02-28
any handy links i should check, i'm gonna treat this problem like a mattress and sleep on it. in the morning i'm sure this'll all makes sense

---

### Post by grahammechanical on 2011-02-28
Which is the drive that has the operating system on it? Preferably the Ubuntu operating system.

You say:

> I've tried setting up Ubuntu on the other smaller 70GB hard drive but can't get it to boot up.Is this drive set up to be the first drive that the BIOS looks for to find an operating system? If the machine is set to boot from the 800GB hard disc, then of course an OS on the 70GB hard disc will not boot.

On old PCs with two drives, one drive was set up as Master and the other was set up as Slave. Jumpers on the backs of the drive let you set up the drives this way. The question is this, how new is your friend's newer PC? New enough to set the boot order in the BIOS? Or will you have to change jumper positions on the drives.

If this is not the case, then you will have to give more information about the drive with Ubuntu on that will not boot. What error messages do you see?

Regards.

---

### Post by Zralou on 2011-02-28
From what I can make out from your computer specifications, you have both SATA and IDE drives.  If your motherboard supports SATA, chances are it will support BIOS boot order changing.
If you feel comfortable entering BIOS then go into bios and change the 'boot' order so your HDD with the operating system is 'first' in the boot order.

SATA motherboards should support several HDD's, I can't remember off the top of my head how many, but it should be more than the amount of hard drives you have.  Chances are you will only have one IDE controller which will handle two hard drives/CD drives.

The hard drives with the long narrow connector are IDE, and the hard drives with a smaller almost square connector are SATA.

Sara Lou

---

### Post by Themiband on 2011-03-10
Okay so things have been moving on slowly and I&#472;e gotten a little further along the road to where I want to be

I sucessfully (after alot of failed attempts) made a boot Ubuntu USB stick using these links

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

and have finally managed to switch over to my bigger 800gb hard drive and have the following set up now

0:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
01:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


Zralou your quite right i have both SATA and IDE connectors on my mother board but only enough for either 1 SATA (that is the newer one right) hard drive and 1 IDE hard drive or 1 CD Drive which is why i couldn run the 250gb hard drive with the 800gb hard drive.

but anyway thats all sorted. Now its a matter of using my creative zen so i guess its time to start a new thread thanks alot for your help guys

---

