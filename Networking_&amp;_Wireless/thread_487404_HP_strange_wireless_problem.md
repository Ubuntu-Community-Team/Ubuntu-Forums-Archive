---
title: "HP strange wireless problem"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by Morhas on 2007-06-29
OK, I decided to install ubuntu on my laptop. When I first just booted ubuntu off the live cd, everything worked fine, and I had wireless capability (led turned blue and I connected to my friends network). Since everything went well just booting off the live cd, I decided to install it. Right now I have it setup to dual boot with vista. When I launch ubuntu, I have no wireless. I tried booting off the live cd to see if it is just working with the live cd, but it stopped working there too.

I am new to linux, but any help you guys could give me would be greatly appreciated. I have an HP dv2310ca, running 7.04. 

Any thoughts?

---

### Post by Atomic Dog on 2007-06-29
Well first things first.  How about you go into the terminal and type:

```
lspci
```

then

```
lsusb
```

This will let us know what you have for hardware.  give us the output of both commands.

---

### Post by Morhas on 2007-06-29
morgan@morgan-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

morgan@morgan-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
morgan@morgan-laptop:~$

01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) im not seeing this in NDISwrapper at first glance...

(thanks for the quick response)

---

### Post by kevdog on 2007-06-29
This is your wireless card:
01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

This works via ndiswrapper

Does your ubuntu computer have a wired connection because we are going to have to download some files?? If not do you have access to an internet connected computer with USB stick for file transfer?

---

### Post by Morhas on 2007-06-29
I can just download them onto my desktop (xp) and transfer them via SD card lol. What will I need to download?

---

### Post by kevdog on 2007-06-29
Ok, first task is to install ndiswrapper from source (Wow!)

Place installation ubuntu cd in disk drive and wait for it to become ready.  At command line type
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

This installs c compilers so we can compile source programs.

Next:
cd ~
mkdir ndiswrapper
Go to ndiswrapper website and download ndiswrapper-1.47.tar.gz: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

When copying this file from SD card put it in ~/ndiswrapper directory.

Extract files from archive
cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47

Build from source
make distclean
make

Install package
sudo make install

Check if process was successful
ndiswrapper -v

You should get something like:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

If you got this far successfully let me know -- Onto the next step!

---

### Post by Morhas on 2007-06-29
I almost got it....

utils version: '1.9', utils version needed by module: '0'
module details:
filename:  /lib/modules/2.6.20-15-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:   1.38 (?)
vermagic: 2.6.20-15-generic SMP mod_unload 586

---

### Post by kevdog on 2007-06-29
Where did you get the 1.38 version??  This might work, however what was wrong with the 1.47 version??

If you need to uninstall the 1.38 version (assuming you compiled it from source), go back into the directory where you compiled the sources:
cd (Whatever path/directory)
sudo make uninstall

We can proceed to see if 1.38 works, but if something doesnt work the first thing I would probably recommend is to upgrade to 1.47

---

### Post by Morhas on 2007-06-29
I downloaded the 1.47 though....( ndiswrapper-1.47.tar.gz)  I really can't see how I got the older version. Should I just try it as it is?

---

### Post by kevdog on 2007-06-29
This is what I would do

Just start over.

Uninstall ndiswrapper as per previous post. (Dont skip this)
Check to see with:
ndiswrapper -v

You should get something like module not found, or command not found.  If you get something else, stop and just repost giving me the output.  You didnt happen to use Synaptic or apt-get to install the repository version of ndiswrapper??

Then 
cd ~/ndiswrapper
rm -R *
Copy the ndiswrapper-1.47.tar.gz file to ~/ndiswrapper and repeat previous instructions.

---

### Post by Morhas on 2007-06-29
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename: /lib/modules/2.6.20-1**5**-generic/misc/ndiswrapper.ko
version: 1.47
vermagic: 2.6.20-1**5**-generic SMP mod_unload 586

Almost 100%. I got the right version, so I assume we shoudl be good. What would the next step be?

---

### Post by kevdog on 2007-06-29
Ok the next step is to actually find the drivers for the card.  Please let me know if you dont have the drivers for the card.  Im specifically looking for some type of XP driver

Ok lets place the drivers somewhere where we know we can find them:
cd ~
mkdir wireless_drivers
cd wireless_drivers

Place you wireless *.sys and *.inf files in this directory

Wrap the drivers within the ndiswrapper module:
sudo ndiswrapper -i **.inf  <---Put name of file here -- 

Check to see if successful
ndiswrapper -l   <--- If you could post this it would be helpful

Load module into kernel
sudo depmod -a  <----- Make sure you get no errors
sudo modprobe -i ndiswrapper

Check to see if there were any errors:
dmesg | grep ndiswrapper <----Please post output

Im going to take a break at this point and allow you to catch up.

---

### Post by Morhas on 2007-06-29
I found the .sys driver, but I couldn't fin the .inf file.  I tried to downloadthe drivers off the internet, but after about an hour of searching, I have nothing. Any thoughts?

---

### Post by kevdog on 2007-06-29
Try one of these:

#
Card: Dell Wireless 1390 WLAN MiniCard (Dell Inspiron E1405, Dell Inspiron E1505, Dell Latitude D620, Dell Inspiron 640m, Compaq Presario V3010AU, V3011AU)

    *
      Chipset: Broadcom BCM4311
    *
      pciid: 14e4:4311 (rev 01, subsys 1028:0007)
    *
      Driver: generally called bcmwl5 [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE), though reporting that R115321.EXE driver does not work for Kubuntu 6.06 LTS 64-bit (Kernel 2.6.15-27),[http://ftp.us.dell.com/network/R140747.EXE](http://ftp.us.dell.com/network/R140747.EXE) UPDATE: The above driver has a mayor security bug, the newest driver is R140747.EXE.
    *
      Alternate 64 bit driver: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228](http://h10025.www1.hp.com/ewfrf/wc/softwareList?lc=en&cc=us&dlc=en&tool=softwareCategory&product=3210693&os=228)

---

### Post by Morhas on 2007-06-29
Ok. so which exe am I downloading? Im trying the R140747 now. Thank you for the post

[EDIT] Download is at about 15% (i hate my internet). I'll be back in a bit.

---

### Post by kevdog on 2007-06-29
I really dont know

You dont want the 64bit driver.  If one driver doesnt work then we will try the other.  The link said something about a version (listed after the update) but didnt provide a link.  Could you find this driver?

---

### Post by Morhas on 2007-06-29
The driver that vista is currently using is BCMWL6.SYS .

[EDIT]
 76% done

---

### Post by Ayuthia on 2007-06-29
ndiswrapper does not have a version that works with the Vista drivers yet.

---

### Post by Morhas on 2007-06-29
I know I just downloaded the xp drivers for it (i think...). I'm going to try installing it again.

---

### Post by Morhas on 2007-06-29
Ok I went through the process and got:

bcmwl5: invalid driver!
bcmwl6: invalaid driver!
bcmwl.sys: invalaid driver!

ugh

The last 2 were my first attemts which were a long shot. BCMWL5 was the driver supllied in the download.

I think I might just pull ubuntu out and start over again.
 Any ideas?

---

### Post by kevdog on 2007-06-29
You cant keep instaling driver after driver.  If you install a driver, its states invalid driver, then you need to remove the driver.  The quickest way to remove all the drivers is:

cd /etc/ndiswrapper
sudo rm -R *

Try the driver from the first link on the page.  If not the second.  Say those two dont work, then you are going to have to go to your manufacturer's website (HP for example), and then do a search of wireless drivers they offer for your model.

---

### Post by Morhas on 2007-06-29
Ok the next step is to actually find the drivers for the card. Please let me know if you dont have the drivers for the card. Im specifically looking for some type of XP driver

Ok lets place the drivers somewhere where we know we can find them:
cd ~
mkdir wireless_drivers
cd wireless_drivers

Place you wireless *.sys and *.inf files in this directory

Wrap the drivers within the ndiswrapper module:
sudo ndiswrapper -i **.inf <---Put name of file here --

Check to see if successful
ndiswrapper -l <--- If you could post this it would be helpful
[COLOR="Red"]bcmwl5 : driver installed
device (14E4:4311) present (alternate driver: bcm43xx[/COLOR]

Load module into kernel
sudo depmod -a <----- Make sure you get no errors
sudo modprobe -i ndiswrapper

Check to see if there were any errors:
dmesg | grep ndiswrapper <----Please post output
[COLOR="Red"][2256.020000] ndiswrapper version 1.47 loaded (smp=yes)
[2256.064000] usbcore: registered new interface driver ndiswrapper[/COLOR]

Im going to take a break at this point and allow you to catch up.

[COLOR="Red"]It looks like everything is good so far. Took me long enough though, thanks for being patient.

[EDIT] I'm going to call it a night. If you could get the next step up, that would be greatly appreciated. Thanks again for all the time and effort you've put into this. [/COLOR]

---

### Post by kevdog on 2007-06-30
I called it a night a long time ago

Here is the part of the installation that is variable for everyone

#1 Make sure for now at least that all WEP/WPA encryption and/or MAC filtering is turned off on the router.  We can add this is later

#2.Reboot and just see what happens -- no more modifications may be needed

#3. If nothing happens, please make sure your wireless card is turned on -- I think its either alt-f2 or cntl-f2 or some other key combination on the laptop that makes your wireless card turn off and on.  Just make sure it is on (this step has caused many a problem in the past).  The exact key combination may be different for your laptop

#4. Still if nothing works then provide me with the following (cut and paste contents of these two files):
/etc/network/interfaces
/etc/iftab

---

### Post by Morhas on 2007-06-30
The led is still orange, meaning no wireless.

/etc/network/interfaces

auto lo
iface lo inet loopback

auto ethl
iface eth0 inet dchp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by kevdog on 2007-06-30
OK, your interfaces file looked OK

Please post:
/etc/iftab
lshw -C network
iwlist scanning
ifconfig

One of these should help us diagnose the problem

---

### Post by kevdog on 2007-06-30
I forgot to tell you to do something

sudo ndiswrapper -m <----This loads the module at boot

Reboot, and if still no success post the following information I listed in the previous post!

---

### Post by Xs1t0ry on 2007-06-30
I'm trying to follow this because I'm having the same problem myself and is it ever complicated!

If you wouldn't mind helping me, I'm using Xubuntu and have a USB WLAN connection (DWL-G122/C1) and no network card. Would the steps you outlined work the same for me even though I'm on Xubuntu? Do some USB receivers and/or routers just not work with Linux?

---

### Post by kevdog on 2007-06-30
ndiswrapper can work with Ubuntu,Xbuntu,Kubuntu,Ebuntu -- the only restriction is that you have a driver for your card.  Every driver hasnt been tested with ndiswrapper (many, many have), so even then its not guaranteed to work.  You might want to check out the ndiswrapper website for more info:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)

---

### Post by Morhas on 2007-06-30
Please post:
/etc/iftab
[COLOR="Red"]eth0 mac 00:16:d3:94:6e:ef arp 1
eth1 mac 00:1a:73:31:08:71 arp 1[/COLOR]

lshw -C network
[COLOR="Red"]morgan@Morganlaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:31:08:71
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c3000000-c3003fff irq:21
morgan@Morganlaptop:~$ 

[/COLOR]
iwlist scanning
[COLOR="RED"]
morgan@Morganlaptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
morgan@Morganlaptop:~$ 
[/color]

ifconfig
[COLOR="RED"]

morgan@Morganlaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:94:6E:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:D3:94:6E:EF  
          inet addr:169.254.9.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:770 errors:0 dropped:0 overruns:0 frame:0
          TX packets:770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61604 (60.1 KiB)  TX bytes:61604 (60.1 KiB)

morgan@Morganlaptop:~$ 
[/color]

I see a network diabled in there, if I had to guess that would be bad.....

I tried sudo ndiswrapper -m  but nothing.

---

### Post by kevdog on 2007-06-30
Ok, really strange but you did provide something useful

Under the lshw -C network, look under your wireless device and see where it says driver:

> 
driver=bcm43xx


This tells me the system is associating your card with the bcm43xx driver rather than ndiswrapper.

Try editing your blacklist file:
gksu gedit /etc/modprobe.d/blacklist

#Blacklist bcm43xx driver
blacklist bcm43xx


Save the file and reboot and then repost:
lshw -C network

---

### Post by Morhas on 2007-06-30
It is officially working!! I never thought a little blue led could look so damn sexy lol. Thank you so much for your continued support throughout this process, you were extremely helpful. It helped that you were telling me what each command was doing, I learned a lot. Thanks again.

---

### Post by kevdog on 2007-06-30
Great!!!  I thought we might have one or two more things to configure but it seems all is well.   I think you could probably figure out how to use WEP if you needed it on your router.  If you need help with WPA let me know!

---

### Post by Morhas on 2007-06-30
Will do, my next project is beryl. Im sure i'm going to need help here lol.

---

### Post by kevdog on 2007-06-30
My damn videocard on my laptop is so old I cant even install beryl/compiz.  So sorry I cant help you!

---

### Post by Morhas on 2007-06-30
Thats rough lol. I just bought this laptop new, so it's pretty exciting.

---

### Post by ddevore on 2007-08-09
I must say THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU 

I have been working on my wireless for hours and finally got it working with this post. I think it was the correct drivers.. Actually I had the wireless working and this morning I killed them because my laptop will freeze occasionally when on wireless and I thought I would get it fixed.. It turned into a painful event. I hope these don't freeze the system on me.. 

I have 2 quick questions if you get this thread. 

1. How do I stop it from giving me the following message..? 

kernel: [   xxx.xxxxxx] Disabling IRQ #7 (sometimes #9)
I did have to a command line switch when installing but I can't remember what it was. 

2. I get a bios bug report upon booting.. bios bug found #81 or something like that..

Do you have any idea how to stop the madness? They are basically annoying and thats it. 

once again THANK YOU THANK YOU THANK YOU

---

### Post by ddevore on 2007-08-09
OK my hopes were dashed....It is still freezing up when on wireless.

Anyone have any suggestions. I am currently using the latest drivers listed in this post. 

AAHHAHHHH

---

### Post by kokyaw on 2007-08-22
> **kevdog said:**
> Ok, really strange but you did provide something useful

Under the lshw -C network, look under your wireless device and see where it says driver:



This tells me the system is associating your card with the bcm43xx driver rather than ndiswrapper.

Try editing your blacklist file:
gksu gedit /etc/modprobe.d/blacklist

#Blacklist bcm43xx driver
blacklist bcm43xx


Save the file and reboot and then repost:
lshw -C network

Hi, I've been successfully following your instructions and I got upto this point. I edited the blacklist file: I added these two lines in the file: 
#Blacklist bcm43xx driver
blacklist bcm43xx

Then I restarted my pc and here is my output for:

lshw -C network

[COLOR="Red"]WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:e8204000-e8205fff irq:5
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:69:be:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:a000-a0ff iomemory:e8208800-e82088ff irq:18[/COLOR]

My wireless card is still not working and it doesn't lit up. I can't connect to the wireless network. Please help me as I've been spending more than a day trying to get this thing working. I really appreciate your instructions!

---

