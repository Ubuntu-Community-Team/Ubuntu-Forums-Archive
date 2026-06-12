---
title: "wireless-install"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by JoeRotonda on 2007-09-06
How do I install wireless on unbuntu 7.04?  I need step by step instructions . I am a newbe to ubuntu.  how to identify my card..get into admin mode etc...

---

### Post by kevdog on 2007-09-06
Please post the following and then I can provide appropriate instructions given what chipset you have for your wireless card:

lspci -nn
lshw -C network

---

### Post by JoeRotonda on 2007-09-06
lol...i am a newbie...before I can post the info you want..what is ISPCI-NN and ISHW-C network and how do I find the information?

---

### Post by unisol on 2007-09-06
go to applications-accessories, and click on terminal. when it opens, type in the terminal;
lspci -nn
lshw -C network
and post the output on the forum.

---

### Post by kevdog on 2007-09-06
If you type them you will find out what the do:

lspci (list = li, pci bus = pci)
lshw -C network (list =li, hardware=hw, -C (class) network)

Unfortunately when you first start out with linux you want to understand every command, what it does, modifcations, etc.  Unvortunately much of the learning process early on is memorizing, and later comes the understanding.  You need to develop a foundation before you can start analyzing, contrasting.  The man pages are useful, but overwhelming at first.  Google is also your friend.  Writing down the commands into an editor and either summarizing them or writing the output is also useful.  You will be surprised however in a few months when you took a look at your log, and laugh at a lot of the things you wrote down at first.

---

### Post by JoeRotonda on 2007-09-06
I get command not found both times...

---

### Post by kevdog on 2007-09-06
What exactly are you typing, Im sure its a syntax error

---

### Post by unisol on 2007-09-06
make sure you type sudo in front of the command.

---

### Post by cyris69 on 2007-09-06
Could you help me out too please, I wanted something other than vista on my PC and Ubuntu seemed lighter than fadora size and speed.

I just need to get my wireless card recognized all I have is modem under Networking

here is all the info you required for another user

```
cyris69@cyris69-desktop:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82955X Memory Controller Hub [8086:2774]
00:01.0 PCI bridge [0604]: Intel Corporation 82955X PCI Express Root Port [8086:2775]
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT] [10de:00f9] (rev a2)
05:00.0 Unknown class [ff00]: Unknown device [1971:1011]
05:01.0 Multimedia audio controller [0401]: Creative Labs SB Audigy [1102:0004] (rev 04)
05:01.1 Input device controller [0980]: Creative Labs SB Audigy Game Port [1102:7003] (rev 04)
05:01.2 FireWire (IEEE 1394) [0c00]: Creative Labs SB Audigy FireWire Port [1102:4001] (rev 04)
**05:02.0 Ethernet controller [0200]: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card [17fe:2120]**
05:04.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller [104c:8025] (rev 01)

```

```
cyris69@cyris69-desktop:~$ sudo lshw -C Network
SCSI                      

*-network UNCLAIMED
       description: Ethernet controller
       product: WMP11v4 802.11b PCI card
       vendor: Linksys, A Division of Cisco Systems
       physical id: 2
       bus info: pci@05:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=32 mingnt=32
       resources: iomemory:93008800-93008fff irq:11
```

I cannot use NDISWrapper, I can not get online to download and install but I downloaded the tar.gz and had no clue how to use it. The commands for it didn't work b/c I always had cyris69@cyris69-desktop:~$ 
so i would receive a E: Error message

Please if you could help me I would greatly appreciate it.

---

### Post by cyris69 on 2007-09-06
I have posted my info from your post, can you help?

---

### Post by kevdog on 2007-09-07
Do you have, or have access to Windows XP drivers for your networking card???  And have the ubuntu installation CD?

---

### Post by JoeRotonda on 2007-09-07
first instructions did not include typing sudo.. tried that still command not found.
Here is what I tried I entered...tried both upper and lower case.

sudo ispci -nn
sudo ishw -C network

---

### Post by JoeRotonda on 2007-09-07
I have notebook dual booted with windows xp and ubuntu 7.04...have all disks drivers etc for windows..

---

### Post by JoeRotonda on 2007-09-07
opps sorry was typing an i not an l...

---

### Post by JoeRotonda on 2007-09-07
joseph@joeslaptop:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:7f:0e:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.104 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:3000-30ff iomemory:d2004800-d20048ff irq:10
  *-network
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:10
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 03
       serial: 00:0c:41:c4:6c:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:3c000000-3c001fff irq:10
joseph@joeslaptop:~$ 

joseph@joeslaptop:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge [8086:2561] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go] [10de:0175] (rev a3)
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
02:04.1 CardBus bridge [0607]: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller [1217:6933] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

Hope this helps?? Joe Rotonda

---

### Post by kevdog on 2007-09-07
You should have no problem installing drivers for this card -- its the same chipset as mine.

You have a broadcom rev03 chipset.  You will need ndiswrapper along with the WinXP drivers either from disk or for the internet for your card.  These are the only two files you need to find (or download) from the internet.  

Do you have a working internet connection on the computer or do you have to transfer files via USB stick?

---

### Post by JoeRotonda on 2007-09-07
I have internet access from both UBUNTU and Windows XP professional..I downloaded ndiswrapper to my ubuntu desktop..it is a tar.gz file...now what do I do with it.? I do not have ubuntu disks downloaded v704 as an iso file burned it to cd and installed from there.

What is the second file I need ..a google search on winxp of course gets all kinds of hits.????
Found ndiswrapper ok...

---

### Post by unisol on 2007-09-07
try this:
sudo aptitude install build-essential
If you downloaded the ndiswrapper tar.gz file, I'm going to assume it is on your desktop
cd ~
mkdir ndiswrapper
cd ~/Desktop
cp *****.tar.gz ~/ndiswrapper <---Put in the file name here
cd ~/ndiswrapper
tar -zxvf ******.tar.gz <---Put in file name here
cd ndiswrapper-1.47 (Or whatever appropriate directory)
make distclean
make
sudo make install

Check if the ndiswrapper package has been installed correctly
ndiswrapper -v 
Should get no errors here

I assume you have the wireless driver for your card??? If you do
cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf <-----Put in file name here
cd /mnt/cdrom/Installer/WINXP


Check if everything is Ok
ndiswrapper -l
Should say driver is installed --- no errors

Now insert ndiswrapper module into kernel
sudo depmod -a <----- Make sure you get no errors after this command
sudo modprobe -i ndiswrapper

Make sure module runs at boot
sudo ndiswrapper -m

Ok we may have to do just a few more steps at this point. What I need from you is the following:
/etc/network/interfaces
/etc/iftab
lshw -C network
__________________
And use this command to remove the driver (as root):if you make a mistake

Code:
ndiswrapper -e driver_name
modprobe -r <drivername>E.G.:
Code:
modprobe -r  name of wireless cardAnd load Ndiswrapper again (As root):

Code:
modprobe ndiswrapper

note i did this in debian etch but it should work for you, just substitute your wireless card.

---

### Post by cyris69 on 2007-09-07
Yes, I have all the drives for my Linksys(.sys/.inf)card on my flash drive and in my windows Vista Partition

Please the only reason I will be deleting Ubuntu is if I can't get online :(

---

### Post by unisol on 2007-09-07
does your flash drive work in ubuntu?

---

### Post by zekica on 2007-09-07
@cyris69

Have you installed ndiswrapper (using the instructions from unisol)? If you had problems, perhaps you can download it for Ubuntu from Windows: you have to download [ndiswraper-common]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-common_1.38-1ubuntu1_all.deb&md5sum=95b621b374025d41b0a4ad6ca649ce47&arch=all&type=main") and [ndiswrapper-utils-1.9]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fn%2Fndiswrapper%2Fndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb&md5sum=e8876c665294254b55b32c02f629ac78&arch=i386&type=main")
save them to Flash drive, and install them by double-clicking on package file (first ndiswrapper-common).

After this, you should have working ndiswrapper installed. To check this you can type in terminal: **ndiswrapper -v**. If that works, you can continue.

You have to copy those **.inf** and **.sys** files for example to your Desktop. Then you'll need to type in terminal:
[B]cd ~/Desktop
sudo ndiswrapper -i *****.inf
sudo rmmod ndiswrapper[/B] <- if you get an error here don't worry
**sudo modprobe ndiswrapper**

Then, type:
**ndiswrapper -l**
And if it shows something like:
[COLOR="DarkRed"]xxxxx: driver installed
  device (xxxx:xxxx) present ...[/COLOR]
You have installed drivers for your wireless card.

Now you have to edit one file:
**sudo gedit /etc/modules**
and append:
[COLOR="DarkRed"]ndiswrapper[/COLOR]
at the end of file.

If you have active AP or Ad-Hoc network you can try to scan and see if it detects it:
**sudo iwlist wlan0 list** (instead of wlan0, you can try wlan1, wlan2 etc. or eth1, eth2 etc)

If it works you can restart your computer and try to connect using "Network Manager" application - that network icon in system tray.

---

### Post by cyris69 on 2007-09-07
I could not edit /ect/modules 
it was read only and i didnt get to append
ndiswrapper to it
i do have 
lsipnds : driver installed
             Device (17FE:2120)

I restarted my pc and the went into network settings and it still only displays
Modem connection that's it not wireless.

Well i think I'm done messing with this I think I'm going to just install fadora
unless this is running in a few

---

### Post by zekica on 2007-09-07
Have you typed in terminal:
**sudo gedit /[COLOR="Red"]etc[/COLOR]/modules**
You wrote that you could not save /ect/modules

Can you open terminal and type:
**sudo modprobe ndiswrapper**

And then open Network preferences?

---

### Post by zekica on 2007-09-07
Or you could just type in terminal:
**echo ndiswrapper | sudo tee -a /etc/modules**

---

### Post by cyris69 on 2007-09-07
ok, I ran
sudo modprobe ndiswrapper
got the wireless setting cannot see my wireless router the is no security like wep
how can i connect?

Edit:
got it
I'd still like to have it run ndiswrapper at boot though  but I can't edit modules

---

### Post by kevdog on 2007-09-08
Do the following

echo ndiswrapper | sudo tee -a /etc/modules

That will edit the file and make sure that the ndiswrapper module is loaded at boot.

---

### Post by cyris69 on 2007-09-08
Awesome, went through without error.

I'm sure it will work, I'm not very familiar with Linux and its ways.
I'm just glad I have other means of surviving on a PC without being crippled using Vista. 
Now, I can play games on vista and everything else on Linux!

Thank you all for your support and guidance!

---

### Post by cyris69 on 2007-09-08
I accidentally ran the code twice now there are two ndiswrapper lines will that be an issue?

---

### Post by unisol on 2007-09-08
comment one out with the # sign

---

### Post by cyris69 on 2007-09-08
I can't physically edit the modules file. Unless there is a way to echo it out then I'm SOL

---

### Post by zekica on 2007-09-08
It shouldn't be a problem if you have the same module listed in /etc/modules twice.
But if you have any problems, you can remove ndiswrapper from /etc/modules by using:
**sudo cp /etc/modules /etc/modules-old**
**grep -v ndiswrapper /etc/modules | sudo tee /etc/modules**

And then you will be able to insert it again.

---

### Post by cyris69 on 2007-09-08
Awesome thx.
Off Topic
Now, if I could only get my sound card working, it will play the start up sound and gaim sounds but nothing else(this happens some boots and not others)
Guess I leave that for another topic
I'm running Creative Audigy ZS 2

Thanks for the code.

---

### Post by cyris69 on 2007-09-08
Off to bed for now, need sleep to goto lunch and then see Halloween!

---

### Post by |Eric| on 2007-10-06
> **JoeRotonda said:**
> first instructions did not include typing sudo.. tried that still command not found.
Here is what I tried I entered...tried both upper and lower case.

sudo ispci -nn
sudo ishw -C network

its LSPCI (lowercase ) 

basicaly ls means list 
ls by itself shows a list of files & folders (directories) 
lspci list the detected hardware (it dosent mean its backed by a driver)

---

