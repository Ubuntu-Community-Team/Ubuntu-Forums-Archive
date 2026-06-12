---
title: "[SOLVED] I've installed ndiswrapper, now how do I install the drivers"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by crjackson on 2007-06-24
I have installed ndiswrapper, and I have the drivers for my Linksys 54G PCI card.  Now how do I use the wrapper to install the drivers.

I don't know much about command line usage so I'll need some hand holding.

---

### Post by kevdog on 2007-06-24
Lets just check if you have ndiswrapper installed properly before we proceed.

What is the output of 
ndiswrapper -v

---

### Post by crjackson on 2007-06-25
> **kevdog said:**
> Lets just check if you have ndiswrapper installed properly before we proceed.

What is the output of 
ndiswrapper -v

Thanks for your reply.  I'm at work right now and I'll have to check this when I get home.  I had to reboot into windows on that system so that it would have an iternet connection.  I had it wired when updating it but I was using the cable from my network printer.  All that had to be put back into a usable state before going to work.

I'll post back today or tomorrow after I've had a chance to copy the output of ndiswrapper -v

Thanks.

---

### Post by crjackson on 2007-06-26
> **kevdog said:**
> Lets just check if you have ndiswrapper installed properly before we proceed.

What is the output of 
ndiswrapper -v

go@go-desktop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by kevdog on 2007-06-26
One of the problems is that ndiswrapper is not installed properly.  This isnt your fault, it happens when you install from repository.  First you need to uninstall ndiswrapper using whatever method you installed it (ie Synaptic).  You then need to grab the sources from the ndiswrapper website and compile and install them. [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

This can be somewhat tricky, but should work for you.

---

### Post by crjackson on 2007-06-26
> **kevdog said:**
> One of the problems is that ndiswrapper is not installed properly.  This isnt your fault, it happens when you install from repository.  First you need to uninstall ndiswrapper using whatever method you installed it (ie Synaptic).  You then need to grab the sources from the ndiswrapper website and compile and install them. [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

This can be somewhat tricky, but should work for you.

Okay, so I've downloaded the file.  Now I'm in over my head...

---

### Post by kevdog on 2007-06-26
Ok, we are using command line only here.

If you have internet connection skip to #4.  If you do not have an internet connection (such as a wired connection do the following)
#1. Stick in ubuntu installation cd and wait for it to become ready
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

If you downloaded the ndiswrapper tar.gz file, I'm going to assume it is on your desktop
cd ~
mkdir ndiswrapper
cd ~/Desktop
cp *****.tar.gz ~/ndiswrapper <---Put in the file name here
cd ~/ndiswrapper
tar -zxvf ******.tar.gz <---Put in file name here
cd ndiswrapper-1.47  (Or whatever appropriate directory)
make distclean
make
sudo make install

Check if the ndiswrapper package has been installed correctly
ndiswrapper -v  
Should get no errors here

I assume you have the wireless driver for your card???  If you do
cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf  <-----Put in file name here

Check if everything is Ok
ndiswrapper -l
Should say driver is installed --- no errors

Now insert ndiswrapper module into kernel
sudo depmod -a  <----- Make sure you get no errors after this command
sudo modprobe -i ndiswrapper

Make sure module runs at boot
sudo ndiswrapper -m

Ok we may have to do just a few more steps at this point.  What I need from you is the following:
/etc/network/interfaces
/etc/iftab
lshw -C network

---

### Post by crjackson on 2007-06-26
> **kevdog said:**
> Ok, we are using command line only here.

If you have internet connection skip to #4.  If you do not have an internet connection (such as a wired connection do the following)
#1. Stick in ubuntu installation cd and wait for it to become ready
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

If you downloaded the ndiswrapper tar.gz file, I'm going to assume it is on your desktop
cd ~
mkdir ndiswrapper
cd ~/Desktop
cp *****.tar.gz ~/ndiswrapper <---Put in the file name here
cd ~/ndiswrapper
tar -zxvf ******.tar.gz <---Put in file name here
cd ndiswrapper-1.47  (Or whatever appropriate directory)
make distclean
make
sudo make install

Check if the ndiswrapper package has been installed correctly
ndiswrapper -v  
Should get no errors here

I assume you have the wireless driver for your card???  If you do
cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf  <-----Put in file name here

Check if everything is Ok
ndiswrapper -l
Should say driver is installed --- no errors

Now insert ndiswrapper module into kernel
sudo depmod -a  <----- Make sure you get no errors after this command
sudo modprobe -i ndiswrapper

Make sure module runs at boot
sudo ndiswrapper -m

Ok we may have to do just a few more steps at this point.  What I need from you is the following:
/etc/network/interfaces
/etc/iftab
lshw -C network

Okay great, I do have a wired connection at this point and had already installed the build-essential.

I'm at work right now so I'll do these steps in the morning when I get home.  Regarding "What I need from you is the following:"

Are those terminal commands?  If yes then no problem.  If no, then please explain.

Thanks for your help btw...:)

---

### Post by kevdog on 2007-06-26
Just put the statement "more" in front of the first two commands and then cut and paste the output.  The last is a terminal command.

---

### Post by crjackson on 2007-06-26
> **kevdog said:**
> Just put the statement "more" in front of the first two commands and then cut and paste the output.  The last is a terminal command.

Got it, will do...

---

### Post by streptococcus on 2007-06-26
**This post could be related to an Ubuntu bug filed at**: # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:1b:24:28:e1:22 arp 1
eth1 mac 00:1a:73:50:5e:9f arp 1 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **kevdog said:**
> Ok, we are using command line only here.

If you have internet connection skip to #4.  If you do not have an internet connection (such as a wired connection do the following)
#1. Stick in ubuntu installation cd and wait for it to become ready
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

If you downloaded the ndiswrapper tar.gz file, I'm going to assume it is on your desktop
cd ~
mkdir ndiswrapper
cd ~/Desktop
cp *****.tar.gz ~/ndiswrapper <---Put in the file name here
cd ~/ndiswrapper
tar -zxvf ******.tar.gz <---Put in file name here
cd ndiswrapper-1.47  (Or whatever appropriate directory)
make distclean
make
sudo make install

Check if the ndiswrapper package has been installed correctly
ndiswrapper -v  
Should get no errors here

I assume you have the wireless driver for your card???  If you do
cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf  <-----Put in file name here

Check if everything is Ok
ndiswrapper -l
Should say driver is installed --- no errors

Now insert ndiswrapper module into kernel
sudo depmod -a  <----- Make sure you get no errors after this command
sudo modprobe -i ndiswrapper

Make sure module runs at boot
sudo ndiswrapper -m

Ok we may have to do just a few more steps at this point.  What I need from you is the following:
/etc/network/interfaces
/etc/iftab
lshw -C network




hi kevdog, 

i hate to steal crjackson's thunder, but I too have been following your guide and am now where he is. I was hoping you could help me too. (I am a recent Linux convert, who also convinced my gf to switch to Linux with her new laptop she just bought yesterday)
[B]
Here is a 'more' cut and paste of my /etc/network/interfaces:[/B]

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid Net Work

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
[B]
and here is a 'more' of my /etc/iftab:[/B]

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:1b:24:28:e1:22 arp 1
eth1 mac 00:1a:73:50:5e:9f arp 1
[B]
and finally, here is a copy of the statement after running "lshw -C network" :[/B]

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:50:5e:9f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=0 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:b8000000-b8003fff irq:10


Hopefully crjackson's is the same/similar so you don't have to do both. Thanks a bunch

- Andrew

---

### Post by streptococcus on 2007-06-26
Actually, wireless now seems to work, but compared to my thinkpad running XP currently (both on the same wireless network) it is running at about 10% speed.. 

I tried grabbing ubuntu from the site, thinkpad was getting it at 250kb/s, whereas the compaq was chugging at 15-20 kb/s...


i am not sure if this has something to do with the settings you mentioned above, but if you could help that'd be appreciated!


thanks a bunch,

Andrew

---

### Post by kevdog on 2007-06-27
First modify your /etc/network/interfaces file:

This is only a general recommendation, you may need to modify yours as appropriate, strep this is what it should be:
gksu gedit /etc/network/interfaces  

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
#wireless-essid Net Work

Next modify the /etc/network/interfaces file to reflect that the MAC address of the wireless card is associated with with wlan0  (if your interfaces file is empty of the MAC address of your wireless card (as seen in the output of lshw -C network) is not listed, then skip this step)

gksu gedit /etc/iftab
eth0 mac 00:1b:24:28:e1:22 arp 1
wlan0 mac 00:1a:73:50:5e:9f arp 1

Just to make sure everything is OK at this point, change router settings so no WEP or WPA encryption is activated, and no MAC filtering is being used.  For testing purposes, you just want the generic settings.

Reboot computer.

Hopefully on reboot, you will be able to connect.
If nothing is happening or it seems you can not connect try and post the following command:
iwlist wlan0 scanning

Also note the following:
YOU CANNOT HAVE WIRELESS AND WIRED INTERFACE WORKING AT SAME TIME!  So before rebooting unplug any network cable.

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Ok, we are using command line only here.

If you have internet connection skip to #4.  If you do not have an internet connection (such as a wired connection do the following)
#1. Stick in ubuntu installation cd and wait for it to become ready
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

If you downloaded the ndiswrapper tar.gz file, I'm going to assume it is on your desktop
cd ~
mkdir ndiswrapper
cd ~/Desktop
cp *****.tar.gz ~/ndiswrapper <---Put in the file name here
cd ~/ndiswrapper
tar -zxvf ******.tar.gz <---Put in file name here
cd ndiswrapper-1.47  (Or whatever appropriate directory)
make distclean
make
sudo make install

Check if the ndiswrapper package has been installed correctly
ndiswrapper -v  
Should get no errors here

I assume you have the wireless driver for your card???  If you do
cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf  <-----Put in file name here

Check if everything is Ok
ndiswrapper -l
Should say driver is installed --- no errors

Now insert ndiswrapper module into kernel
sudo depmod -a  <----- Make sure you get no errors after this command
sudo modprobe -i ndiswrapper

Make sure module runs at boot
sudo ndiswrapper -m

Ok we may have to do just a few more steps at this point.  What I need from you is the following:
/etc/network/interfaces
/etc/iftab
lshw -C network

go@go-desktop://media/cdrom0/Drivers$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

go@go-desktop://media/cdrom0/Drivers$ more /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:13:d3:0e:15:f4 arp 1
ra0 mac 00:12:17:64:a2:74 arp 1
go@go-desktop://media/cdrom0/Drivers$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@02:00.0
       logical name: ra0
       version: 01
       serial: 00:12:17:64:a2:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:fdcfc000-fdcfdfff irq:20
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:0e:15:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.8 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:de00-deff iomemory:fdcff000-fdcff0ff irq:16
go@go-desktop://media/cdrom0/Drivers$

---

### Post by crjackson on 2007-06-27
I went ahead and rebooted with the wired connections disconnected.

I get same result, it shows wireless HOSTS in the area and indicates who is secured and who isn't.  There are no signal strength bars on any of them, and of course it will connect to noting.

What now?

---

### Post by kevdog on 2007-06-27
Just a learning point for you:
Look at the output of lshw -- specifically your wireless connection:

> 
*-network:0
description: Wireless interface
product: RT2500 802.11g Cardbus/mini-PCI
vendor: RaLink
physical id: 0
bus info: pci@02:00.0
logical name: ra0
version: 01
serial: 00:12:17:64:a2:74
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
resources: iomemory:fdcfc000-fdcfdfff irq:20


It wants to work on the ra0 interface name (logical name as seen above)
Before you go on -- did you use ndiswrapper to install the driver?? The only reason I am asking is that I see from the above statement your driver is RT2500STA.  
I use ndiswrapper and my driver line = ndiswrapper+lsbcmnds 
lsbcmnds is the driver I installed with ndiswrapper.

Lets just try this for the meantime, until I hear back from you.
Just add the following to your /etc/network/interfaces file -- again gksu gedit /etc/network/interfaces:
auto ra0
iface ra0 inet dhcp

Reboot and tell me what happens

---

### Post by kevdog on 2007-06-27
Can you tell me more about your card??  Im predicting a driver problem in the future.  This is a Linksys 54G PCMCIA card or PCI card?? No usb right?? or is it?
If its PCI/PCMCIA please copy and paste the output of:
lspci
lspci -n

If its USB then copy and paste:
lsusb

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Can you tell me more about your card??  Im predicting a driver problem in the future.  This is a Linksys 54G PCMCIA card or PCI card?? No usb right?? or is it?
If its PCI/PCMCIA please copy and paste the output of:
lspci
lspci -n

If its USB then copy and paste:
lsusb

I'm getting ready for work right now, so I'll have to post that output tonight when I get home.

It's a Linksys Woreless-G PCI Adapter w/SpeedBooster
Model No. WMP54GS

Desktop PC PCI card...  No usb, no PCMCIA.

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Just a learning point for you:
Look at the output of lshw -- specifically your wireless connection:



It wants to work on the ra0 interface name (logical name as seen above)
Before you go on -- did you use ndiswrapper to install the driver?? The only reason I am asking is that I see from the above statement your driver is RT2500STA.  
I use ndiswrapper and my driver line = ndiswrapper+lsbcmnds 
lsbcmnds is the driver I installed with ndiswrapper.

Lets just try this for the meantime, until I hear back from you.
Just add the following to your /etc/network/interfaces file -- again gksu gedit /etc/network/interfaces:
auto ra0
iface ra0 inet dhcp

Reboot and tell me what happens

I used ndiswrapper to install the driver.

it was something like:
ndiswrapper -i WMP54GS.INF

Then it just said "installed"

---

### Post by kevdog on 2007-06-27
Lets try something.  I dont think after all of this that you need ndiswrapper.  I think the drivers should work out of the box for you -- except for a little tweaking.  I didnt know until the last post that your card uses the rt2500 drivers, which by default are installed in ubuntu.  Because you are using these drivers (not ndiswrapper) that is the reason why you are seeing the exact same behavior between your first post to the forum and your last post. 

Lets first uninstall ndiswrapper.
sudo modprobe -r ndiswrapper

That at least takes it out of the kernel.

Second can you send the output of the following:
iwlist scan

This should list the access points that your card is "seeing".

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Lets try something.  I dont think after all of this that you need ndiswrapper.  I think the drivers should work out of the box for you -- except for a little tweaking.  I didnt know until the last post that your card uses the rt2500 drivers, which by default are installed in ubuntu.  Because you are using these drivers (not ndiswrapper) that is the reason why you are seeing the exact same behavior between your first post to the forum and your last post. 

Lets first uninstall ndiswrapper.
sudo modprobe -r ndiswrapper

That at least takes it out of the kernel.

Second can you send the output of the following:
iwlist scan

This should list the access points that your card is "seeing".

Okay, I removed the wrapper as shown.

go@go-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:16:01:AD:12:03
                    Mode:Managed
                    ESSID:"Buffalo"
                    Encryption key: on
                    Channel:11
                    Quality:0/100  Signal level:-44 dBm  Noise level:-195 dBm
          Cell 02 - Address: 00:0F:66:E2:BC:5F
                    Mode:Managed
                    ESSID:"Pineapple"
                    Encryption key: off
                    Channel:6
                    Quality:0/100  Signal level:-85 dBm  Noise level:-204 dBm

go@go-desktop:~$

---

### Post by kevdog on 2007-06-27
I can see it lists the quality of both AP's as 0/100. 

Which access point is yours?? -- Buffalo or Pineapple?

Also can you post the output of the following:
sudo modprobe -l | grep rt25

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> I can see it lists the quality of both AP's as 0/100. 

Which access point is yours?? -- Buffalo or Pineapple?

Also can you post the output of the following:
sudo modprobe -l | grep rt25

Buffalo

---

### Post by crjackson on 2007-06-27
go@go-desktop:~$ sudo modprobe -l | grep rt25
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
go@go-desktop:~$

---

### Post by crjackson on 2007-06-27
Got to run out the door for work.  I'll pick this up in an hour or two after I get logged in at work

---

### Post by kevdog on 2007-06-27
Hmm, Ok as you can see from the last statement you sent me, the rt2500 drivers are installed by default on your system.

First turn off any encryption on your router.  It seems by the output you have given me that buffalo's encryption key is on.  (I'll bet it is WEP encryption :))  Anyway turn off WEP and do not MAC filter on the router.  We can eventually add all of this stuff back in later.

Ok we are going to test with a manual configuration.  If this works then we can automate it, but for now - since we are kind of struggling I want you to do the following.  At the command line I want you to type the following:

sudo ifconfig ra0 down
sudo ifconfig ra0 up
sudo iwconfig ra0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig ra0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient ra0

After you get done (hopefully you will be connected, type
ifconfig (to see if you have been issued a IP address)

then ping various sites to see if you get a response:
ping yahoo.com
ping localhost
ping ROUTER_IP_ADDRESS (whatever your router local lan address is -- ie 192.168.1.1)

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Hmm, Ok as you can see from the last statement you sent me, the rt2500 drivers are installed by default on your system.

First turn off any encryption on your router.  It seems by the output you have given me that buffalo's encryption key is on.  (I'll bet it is WEP encryption :))  Anyway turn off WEP and do not MAC filter on the router.  We can eventually add all of this stuff back in later.

Ok we are going to test with a manual configuration.  If this works then we can automate it, but for now - since we are kind of struggling I want you to do the following.  At the command line I want you to type the following:

sudo ifconfig ra0 down
sudo ifconfig ra0 up
sudo iwconfig ra0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig ra0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient ra0

After you get done (hopefully you will be connected, type
ifconfig (to see if you have been issued a IP address)

then ping various sites to see if you get a response:
ping yahoo.com
ping localhost
ping ROUTER_IP_ADDRESS (whatever your router local lan address is -- ie 192.168.1.1)

Okay - the other listed Pineapple connection is not encrypted and I can connect to it all the time while running windows.  ubuntu however won't connect to that either.

Also I get no signal stregnty bars on any of the connections uning ubuntu.  A different member told me that was an indication that the driver wasn't working at all.

Just throwing that out so you'll know the same information I have.

---

### Post by kevdog on 2007-06-27
Its very possible its a driver problem, but did you manually try to connect using those commands??  If that doesnt work then we will have to find another driver!

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Its very possible its a driver problem, but did you manually try to connect using those commands??  If that doesnt work then we will have to find another driver!

No, I'm at work right now.  I'll try it when I get home and post back with the results.

Wireless seems to be a problematic issue with ubuntu.  I booted the live 32bit CD on my wife's laptop which it seems that EVERYTHING is supported.  It showed power bars for 6 neighborhood wireless connections (several were not encrypted).  Even her laptop couldn't connect.  I was very surprised.

---

### Post by kevdog on 2007-06-27
Just my personal opinion, but wireless is the Achilles Heel of Ubunutu.  Im not sure if its Ubuntu specific, but rather common among all Unix distros.  Yes I know some may function better with some cards, however the major problem is that card manufacturers dont release the source code for their drivers and also usually do not release linux drivers.  Because of this you have a lot of third party people trying to make drivers or methods to convert the windows drivers to linux drivers (ndiswrapper).  Some chipsets of cards are better supported than others also.

If you were to go try to get a card and asked what card works "out of the box" with ubuntu, your specific card would be listed as one of those cards.  You can see however that "out of the box" doesnt work for many cards that it is supposed to.

Hang in there.  We will get it working.  Just look at it this way.  You are learning a lot about working with linux -- probably more than you wanted to know, but none the less the skills you are acquiring with this task will come in very handy down the road!

---

### Post by crjackson on 2007-06-27
> **kevdog said:**
> Just my personal opinion, but wireless is the Achilles Heel of Ubunutu.  Im not sure if its Ubuntu specific, but rather common among all Unix distros.  Yes I know some may function better with some cards, however the major problem is that card manufacturers dont release the source code for their drivers and also usually do not release linux drivers.  Because of this you have a lot of third party people trying to make drivers or methods to convert the windows drivers to linux drivers (ndiswrapper).  Some chipsets of cards are better supported than others also.

If you were to go try to get a card and asked what card works "out of the box" with ubuntu, your specific card would be listed as one of those cards.  You can see however that "out of the box" doesnt work for many cards that it is supposed to.

Hang in there.  We will get it working.  Just look at it this way.  You are learning a lot about working with linux -- probably more than you wanted to know, but none the less the skills you are acquiring with this task will come in very handy down the road!

I understand all that and I apreciate all the help, but it makes for a hard sell when we are in the wireless age.  My wife (who hates learning anything new on her computer) is all but ready to let me install ubuntu on her laptop.  The only problem is that the wireless which seems supported won't even work there either, so I don't dare even start until I can make it all seem like plug and play in her eyes.

She has problems on windows ALL the time.  I've done many installs for her and to be honest, ubuntu seems to support the laptop better that XP and all it's drivers (save for the wireless not working).  I'm so tired of working on her laptop for this and that.  She doesn't do anything on it except web surfing, email, digital photo manipulation, and music related things with her iPod.

I have no issues with XP on any of my other systems.  It runs well on all of them, but I have no intentions of ever putting that Vista Virus on any of my systems so I'd rather start moving away from the whole windows thing now if possible.

---

### Post by kevdog on 2007-06-27
I hope by the tone of your last email you are not giving up!!  In the worst case scenario I would just go out and purchase a different wireless card.  

If you want to proceed, please repost.
Two possible resolutions for you (if the last set of instructions I gave you dont work)
1. Uninstall the default, preinstalled drivers and attempt to use ndiswrapper
2.  The preinstalled drivers for your card that are included in Ubuntu by default are quite old.  Download and compile the new version of these drivers.

---

### Post by streptococcus on 2007-06-28
thanks for all your help kevdog,

wireless works now, but speed is still an issue (i am running with normal router settings, WPA, etc... but i don't see how that should affect speed)

i guess it is good for now, though if you know of any reason why it is going so slow (and unpredictable, downloads apparently go from 300 B/s to 43kB/s) any help would be appreciated.

for now, however, i will call this a victory.



thanks again!

- andrew

---

### Post by kevdog on 2007-06-28
Andrew

I have no idea -- likely its a driver issue, but that is only a guess.  I have a Linksys WRT54Gs card, and at least to me the performance is as good as in windows.  Wireless in Ubuntu is very unpredictable.  Its very driver specific.  Hopefully in the months ahead I can get a better sense of what types of cards work better in terms of performance.  Cards that supposedly "work out of the box" are not always the best option due to driver-related problems.  Maybe some of the problems will be addressed in Gusty!

---

### Post by crjackson on 2007-06-28
> **kevdog said:**
> I hope by the tone of your last email you are not giving up!!  In the worst case scenario I would just go out and purchase a different wireless card.  

If you want to proceed, please repost.
Two possible resolutions for you (if the last set of instructions I gave you dont work)
1. Uninstall the default, preinstalled drivers and attempt to use ndiswrapper
2.  The preinstalled drivers for your card that are included in Ubuntu by default are quite old.  Download and compile the new version of these drivers.

No, I'm not giving up on it.  I'll keep plugging away until I see some kind of results.

---

### Post by kevdog on 2007-06-28
If the above commands didnt work, we are going to try ndiswrapper.  We are over half way there with ndiswrapper so this trial, shouldnt take too long to see if its going to work or fail!

---

### Post by crjackson on 2007-06-28
> **kevdog said:**
> If the above commands didnt work, we are going to try ndiswrapper.  We are over half way there with ndiswrapper so this trial, shouldnt take too long to see if its going to work or fail!

Okay - the manual connection didn't work.  I've been messing with it for 2 hours now...

---

### Post by kevdog on 2007-06-28
Ill get back to you in about an hour

General procedure
lsmod -l | grep /rt[[:digit:]]

All the rt modules that comeup, you need to remove them from kernel
sudo modprobe -r ******.ko

Then blacklist the modules in /etc/modprobe.d/blacklist

Then reload your ndiswrapper
sudo modprobe -i ndiswrapper
sudo depmod -a
sudo ndiswrapper -m

Change /etc/iftab and /etc/network/interfaces --- substitute wlan0 for ra0
Reboot!

Sorry I dont have time to give specifics, I gotta run!

---

### Post by crjackson on 2007-06-28
> **kevdog said:**
> Ill get back to you in about an hour

General procedure
lsmod -l | grep /rt[[:digit:]]

All the rt modules that comeup, you need to remove them from kernel
sudo modprobe -r ******.ko

Then blacklist the modules in /etc/modprobe.d/blacklist

Then reload your ndiswrapper
sudo modprobe -i ndiswrapper
sudo depmod -a
sudo ndiswrapper -m

Change /etc/iftab and /etc/network/interfaces --- substitute wlan0 for ra0
Reboot!

Sorry I dont have time to give specifics, I gotta run!

No problem, I'm running out the door for work right now.  I'll have to do it later.  Hopefully I'll get all this worked out by Monday.  I'll have some time to work on it at length this weekend.

---

### Post by kevdog on 2007-06-28
Ok, one last thing was incorrect on my instructions from last post (im going to post an example for you.

The correct command is
modprobe -l | grep /rt[[:digit:]]

This command produces for me the following output:
```

/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2400/rt2400.ko

```

So want you to do is remove the following:
sudo modprobe -r ****.ko
Where ***.ko is equal to
rt61.ko
rt2x00lib.ko
rt2500pci.ko
rt2400pci.ko
rt2500.ko
rt2400.ko
rt2570.ko

Then add these to the blacklist (/etc/modprobe.d/blacklist).  You will see examples in the file.  Just append the module names to the end of the list.

Then proceed to load ndiswrapper module into the kernel as described above.
You then need to change the interface name from ra0 to wlan0 since ndiswrapper expects an interface name of wlan0.

Reboot.
If nothing happens when you reboot, first check to see your card is loaded with the ndiswrapper driver:
lshw -C network

You should see under driver name ndiswrapper (with possibly something else) listed.

Just to let you know.  This process is totally reversible if you know what modules your removed from the kernel and blacklisted.  

Let me know what happens.

---

### Post by crjackson on 2007-06-28
Okay, I'm going to have to do this slow.  I don't want to take out anything extra that will mess me up.  I'll post the output of that command and you can direct me to the EXACT entries I need to remove.

Next, I need to know what the command is to edit the black list file.

Once that's done, I'll redownload the ndiswrapper package and run through the comple procedure noted earlier.

I won't be able to start on this until tomorrow morning when I get home from work.

BTW - I have (2) sets of drivers for this card.  One came on CD with the card, and one I downloaded from a link provided by the  ndiswrapper page.  Which driver do you suggest I go with?

---

### Post by kevdog on 2007-06-28
Again not to scare you, however nothing that we are about to embark upon is unreversible.

To edit your blacklist file type the following at the command line:
gksu gedit /etc/modprobe.d/blacklist

This will pop open a GUI so you can edit the file and then save it as normal

Ndiswraper
I think everything should be fine with this (I think).  One way to check is to do the following:
ndiswrapper -v
ndiswrapper -l

If you cut and paste the output of these two commands, I think everything should be fine.  We then need to insert this module into the kernel:
sudo modprobe -i ndiswrapper

As far as the drivers -- you are touching on a sticky issue.  This essentially is the crux of the problem.  In the first case, the built-in drivers didnt work.  Now we are going to try drivers with ndiswrapper.  If this doesnt work, then we are going to compile and then install newer versions of the built-in-drivers -- known as serialmonkey drivers.  If that doesnt work I give up!!!  With ndiswrapper try the drivers first that you may have downloaded from the ndiswrapper website.  These supposedly have been tested and the reason they are present is that they at least worked for someone!

Let me know how you are coming along!

---

### Post by streptococcus on 2007-06-28
kevdog, just to let you know, i disabled IPV6 and now my wireless is blazing.

crjackson, you may want to do this eventually once you actually get it up and running. it's not that difficult, and if you find your wireless unreliable and slow (<25kB/s when it should be >100kB/s) you can try this:

in terminal,

sudo gedit /etc/modprobe.d/bad_list

which should open a blank window, in which you type:

alias net-pf-10 off

and save.

then, to disable it in Firefox (which may not be needed, but I did it anyway), just follow the instructions on this website:

[http://en.opensuse.org/Disable_IPv6_for_Firefox]("http://en.opensuse.org/Disable_IPv6_for_Firefox")


thanks again for your help!


- andrew

---

### Post by crjackson on 2007-06-30
okay, so I tried to re-install the ndiswrapper and this is that I got:

[B]go@go-desktop:~/Desktop/ndiswrapper$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)
go@go-desktop:~/Desktop/ndiswrapper$ [/B]

What do I now need to do?  Is there an update that I need?

---

### Post by crjackson on 2007-07-01
Okay I'm trying to remove the modules but I'm doing something wrong.

[B]go@go-desktop:~$ sudo depmod -a
Password:
go@go-desktop:~$ sudo -m
sudo: illegal option `-m'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
go@go-desktop:~$ sudo ndiswrapper -m
module configuration already contains alias directive

go@go-desktop:~$ modprobe -l|grep /rt[[:digit:]]
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2400/rt2400.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2400pci.ko
go@go-desktop:~$ sudo modprobe -r rt2400.ko
FATAL: Module rt2400.ko not found.
go@go-desktop:~$ sudo modprobe -r /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2400/rt2400.ko
FATAL: Module /lib/modules/2.6.20_16_generic/kernel/ubuntu/wireless/rt2x00_legacy/rt2400/rt2400.ko not found.
go@go-desktop:~$ sudo -r rt61.ko
sudo: illegal option `-r'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
go@go-desktop:~$ sudo modprobe -r rt61.ko
FATAL: Module rt61.ko not found.
go@go-desktop:~$ [/B]

---

### Post by crjackson on 2007-07-02
Standing by...

---

### Post by kevdog on 2007-07-02
Ok

Lets just check a few things right now:
Please list:

lshw -C network

I want to make sure the driver has been removed (the built in driver).

As far as your ndiswrapper problem, I seen this happen before, and I dont know why it does this.  Lets uninstall ndiswrapper then reinstall it.

sudo modprobe -r ndiswrapper
Check the module was unloaded with
modprobe -l | grep ndis <----Make sure ndiswrapper.ko is not shown

sudo rm -R /etc/ndiswraper/*
cd ~/ndiswrapper/ndiswrapper-1.47 <---If this is not the directory were the sources are located then substitute your directory where the sources are located
sudo make uninstall
make distclean
make
sudo make install

Check to see if ndiswrapper was installed properly
ndiswrapper -v

Let me know what you get!!

---

### Post by crjackson on 2007-07-02
kevdog,

Before we embark on removing and reinstalling the ndiswrapper, have a look at the post above.  I haven't been able to remove those *.ko packages  My syntax is wrong and I need some help.

Tell me what I'm typing in wrong and I'll remove those *.ko packages when I get home from work.

---

### Post by kevdog on 2007-07-02
Lets just try blacklisting them before we remove them.  I gave you the wrong syntax for removing so sorry.  But lets just try to blacklist first

To blacklist
gksu gedit /etc/modbrobe.d/blacklist

There are many examples in the file, but to blacklist something its basically
blacklist *module_name*

So taking an example:
blacklist rt61
blacklist rtx200lib


You dont need to add the .ko suffix
After blacklist what you want then just reboot!

Just for your knowledge, run the command lshw -C network
I know there are a bunch of lines, but if your wireless card is plugged in, it will list on one of the lines driver *driver_name*

You really only need to blacklist the name of the driver you see.  Once you blacklist and reboot, you should run the command lshw -C network and then look at the driver statement.  It shouldnt be listed as before.

---

### Post by crjackson on 2007-07-02
> **kevdog said:**
> Lets just try blacklisting them before we remove them.  I gave you the wrong syntax for removing so sorry.  But lets just try to blacklist first

To blacklist
gksu gedit /etc/modbrobe.d/blacklist

There are many examples in the file, but to blacklist something its basically
blacklist *module_name*

So taking an example:
blacklist rt61
blacklist rtx200lib


You dont need to add the .ko suffix
After blacklist what you want then just reboot!

Just for your knowledge, run the command lshw -C network
I know there are a bunch of lines, but if your wireless card is plugged in, it will list on one of the lines driver *driver_name*

You really only need to blacklist the name of the driver you see.  Once you blacklist and reboot, you should run the command lshw -C network and then look at the driver statement.  It shouldnt be listed as before.

Great - Thanks.  I'll work on that right away.  So am I only looking to blacklist ONE specific driver?

---

### Post by kevdog on 2007-07-02
I think so, depending on what the driver is.  Again if you look at lshw -C network, it will tell you what the driver currently is.  You basically want to blacklist things until the driver portion no longer shows up, is blank, or nothing is listed.

---

### Post by crjackson on 2007-07-03
go@go-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@02:00.0
       logical name: ra0
       version: 01
       serial: 00:12:17:64:a2:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:fdcfc000-fdcfdfff irq:20
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:0e:15:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.8 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:de00-deff iomemory:fdcff000-fdcff0ff irq:16

---

### Post by kevdog on 2007-07-03
Ok try this

gksu gedit /etc/modprobe.d/blacklist
blacklist rt2500
blacklist rt2x00lib
blacklist rt2500pci
blacklist rt2500usb

---

### Post by crjackson on 2007-07-03
> **kevdog said:**
> Ok try this

gksu gedit /etc/modprobe.d/blacklist
blacklist rt2500
blacklist rt2x00lib
blacklist rt2500pci
blacklist rt2500usb

Okay - I'll do this when I get home.  I did this today - completely remove the ndiswrappr - download/install version 1.47 (it still reports that it is 1.38 however) - loaded the driver.

ndiswrapper -l  reports driver installed - device present.
ndiswrapper -v reports version 1.38 - "Module To Old" - something about tools.

I removed it twice and reinstalled it twice.  It gives me the same result no matter what I do.

I think I'm on the right track since it tells me the driver is installed and the device is present.

I'll do the blacklist thing when I get home tonight or in the morning and post back...

---

### Post by kevdog on 2007-07-03
Try this to remove any old ndiswrapper installations:

sudo updatedb <---This will take a minute or two to run:
When it is done, run 

sudo locate ndiswrapper 

and remove all the files listed. Then run 

sudo locate loadndisdriver 

and remove all the files listed

Also do the following

sudo modprobe -r ndiswrapper

Also remove any installed drivers:

sudo rm -rf /etc/ndiswrapper

This will totally wipe out any installed ndiswrapper on your system.

---

### Post by crjackson on 2007-07-03
> sudo locate ndiswrapper

and remove all the files listed. Then run

sudo locate loadndisdriver

and remove all the files listed

By this, do you mean to delete the files from the drive, or is there some procedure to un-install them?

---

### Post by kevdog on 2007-07-03
Here are the full blown instructions, I would follow the whole guide since Ive done it many times on my machine and I know it works.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

---

### Post by crjackson on 2007-07-03
> **kevdog said:**
> Here are the full blown instructions, I would follow the whole guide since Ive done it many times on my machine and I know it works.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

Okay - I'll work on this tomorrow.  If this doesn't workout, I'm think I'll just blow ubuntu off the HD and reinstall from scratch, start at the top and try again.

---

### Post by crjackson on 2007-07-04
Okay - so I did a fresh install of ubuntu 64, then I downloaded ndiswrapper and attempted an install.  It looks good except for this.  Tell me what do do now...

charles@eMachines-Kitchen:~$ ndiswrapper -v
**utils Error: no version specified!**
driver version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 
charles@eMachines-Kitchen:~$

---

### Post by crjackson on 2007-07-04
[B]charles@eMachines-Kitchen:~$ ndiswrapper -l
rt2500 : driver installed
        device (1814:0201) present (alternate driver: rt2500)
charles@eMachines-Kitchen:~$ 
[/B]

I forged ahead but perhaps to no avail.  I loaded the driver and ignored the error.  I did the thing where it puts it into the kernal, and the other thing to make it load at boot.

Still it doesn't work at all...

---

### Post by kevdog on 2007-07-04
Did you install ndiswrapper with synaptic??  That is the reason for this error most likely!

As far as the other error, remember we tried using the built in driver but it didnt work.  Im skeptical that ndiswrapper will work, but we can always try.

You need to blacklist the built-in drivers
gksu gedit /etc/modprobe.d/blacklist

blacklist rt2500
blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib

Then insert ndiswrapper module
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Please reboot and post the following:
lshw -C network

---

### Post by crjackson on 2007-07-04
> **kevdog said:**
> Did you install ndiswrapper with synaptic??  That is the reason for this error most likely!

As far as the other error, remember we tried using the built in driver but it didnt work.  Im skeptical that ndiswrapper will work, but we can always try.

You need to blacklist the built-in drivers
gksu gedit /etc/modprobe.d/blacklist

blacklist rt2500
blacklist rt73usb
blacklist rt2570
blacklist rt2500usb
blacklist rt2x00lib

Then insert ndiswrapper module
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Please reboot and post the following:
lshw -C network

I downloaded and installed.  It wouldn't completely install.  It gave me chingos of errors when I typed sudo make install.  Must have made about 30 errors or so.  So I turned to automaticx and installed.  It seemed to work without errors and then reported version 1.47 which a manual install never would do.

I was pleased to see that it reported installed and device present, but sad to see the utilities problem.  I didn't black list anything yet but I did load the driver and it seemed to load properly (aside from the fact that it still doesn't let me connect).

Is there anyway to fix the utils error?  Just downloading the wrapper and compiling from the instructions just plain doesn't work for me.  I'm sure I'm doing it improperly or something, but I can't make it happen.  I've tired about 60 times today.  I've even wiped my HD and re-installed Linux.  It's really BS that this is so damned hard.  I'm just about ready to throw all my computers into the swimming pool and get a new hobby.

---

### Post by kevdog on 2007-07-04
Even with the utils error, the userspace utility ndiswrapper is still present.  I wouldnt get hung up on this for now.  

We really however have to the driver of your card from the rt2500 driver to the ndiswrapper/windows driver set.  The only way I know to see what driver is currently assigned to your card is by using the command
lshw -C network and seeing from the output what driver is currently assigned.

Unless we blacklist the rt modules they will always take precedence over ndiswrapper.

---

### Post by crjackson on 2007-07-04
charles@eMachines-Kitchen:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@02:00.0
       logical name: ra0
       version: 01
       serial: 00:12:17:64:a2:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:fdcfc000-fdcfdfff irq:20
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:0e:15:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.8 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:de00-deff iomemory:fdcff000-fdcff0ff irq:23

---

### Post by kevdog on 2007-07-04
Im not sure if you blacklisted and then rebooted, because your device is still using the rt2500 driver.

> configuration: broadcast=yes[COLOR="Red"] driver=RT2500STA[/COLOR] driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless

If you did blacklist, then try adding this to the blacklist file
blacklist rt2500sta

What you might want to do is do the following
sudo modprobe -l grep rt2500

And see the output.  I thought that there was only a rt2500.ko module, however possibly there is also a rt2500sta.ko module.  If the rt2500sta.ko module does exist, you will definitely need to blacklist it with the above provided blacklist statement

Understand what we are doing??

---

### Post by crjackson on 2007-07-05
> **kevdog said:**
> Im not sure if you blacklisted and then rebooted, because your device is still using the rt2500 driver.



If you did blacklist, then try adding this to the blacklist file
blacklist rt2500sta

What you might want to do is do the following
sudo modprobe -l grep rt2500

And see the output.  I thought that there was only a rt2500.ko module, however possibly there is also a rt2500sta.ko module.  If the rt2500sta.ko module does exist, you will definitely need to blacklist it with the above provided blacklist statement

Understand what we are doing??

charles@eMachines-Kitchen:~$ sudo modprobe -|grep rt2500
Password:
FATAL: Module _ not found.
charles@eMachines-Kitchen:~$

---

### Post by crjackson on 2007-07-05
charles@eMachines-Kitchen:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64
       resources: iomemory:fdcfc000-fdcfdfff irq:5
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:0e:15:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.8 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:de00-deff iomemory:fdcff000-fdcff0ff irq:23
charles@eMachines-Kitchen:~$

---

### Post by crjackson on 2007-07-05
charles@eMachines-Kitchen:~$ ndiswrapper -l
rt2500 : driver installed
        device (1814:0201) present (alternate driver: rt2500)
charles@eMachines-Kitchen:~$

---

### Post by kevdog on 2007-07-05
You are persistent -- I will give you that!

Ok, I think we are on the right track. Hopefully.

Your card is no longer associated with the rt2500sta driver.  I didnt think there was a 2500sta module, but I wasnt sure on your machine.  To my knowledge there is only a rt2500 module which after you blacklisted it, no longer shows up.

Your windows driver is effectively wrapped inside the ndiswrapper package.  Now we need to insert the ndiswrapper module into the kernel and hopefully everything will work! 

sudo dmesg -a <---Make sure no errors
sudo modprobe -i ndiswrapper
sudo ndiswrapper -m
Check to see if successfully inserted into kernel:
dmesg | grep ndiswrapper  <--- If there doenst appear to be an error then most likely everything is OK

ndiswrapper by default sets the device up with an interface name of wlan0.  
What I would do at this point, is to reboot.
Everything might work, but if not, only a few more modifications will be needed.

If everything isnt working post this info with the next post:
/etc/iftab
/etc/network/interfaces
lshw -C network

Thanks

---

### Post by crjackson on 2007-07-05
10-4

I'll be posting the results after work as usual.

---

### Post by crjackson on 2007-07-06
charles@eMachines-Kitchen:~$ sudo dmesg -a
dmesg: invalid option -- a
Usage: dmesg [-c] [-n level] [-s bufsize]
charles@eMachines-Kitchen:~$

---

### Post by crjackson on 2007-07-06
charles@eMachines-Kitchen:~$ sudo ndiswrapper -m
module configuration already contains alias directive

---

### Post by crjackson on 2007-07-06
charles@eMachines-Kitchen:~$ dmesg | grep ndiswrapper
[   44.286800] ndiswrapper version 1.47 loaded (smp=yes)
[   44.360554] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   44.360560] ndiswrapper (load_sys_files:216): couldn't prepare driver 'rt2500'
[   44.360956] ndiswrapper (load_wrap_driver:118): couldn't load driver rt2500; check system log for messages from 'loadndisdriver'
[   44.362415] usbcore: registered new interface driver ndiswrapper
charles@eMachines-Kitchen:~$

---

### Post by fredj on 2007-07-06
It looks like there are several things wrong here. You seem to have installed the 64 bit version of ubuntu
but you are trying to use ndiswrapper to install 32 bit Windows XP drivers. This probably won't work.

Also you still seem to have a defective version of ndiswrapper. Even if you got ndiswrapper sorted out I
don't think you will get your 32 bit windows driver to work.

---

### Post by kevdog on 2007-07-06
Do you have a 64 bit Windows driver??  You may need to look on the manufacture's website.

If not its onto plan C -- compilation of serialmonkey drivers.

---

### Post by crjackson on 2007-07-06
> **fredj said:**
> It looks like there are several things wrong here. You seem to have installed the 64 bit version of ubuntu
but you are trying to use ndiswrapper to install 32 bit Windows XP drivers. This probably won't work.

Also you still seem to have a defective version of ndiswrapper. Even if you got ndiswrapper sorted out I
don't think you will get your 32 bit windows driver to work.

I am using 64bit ubuntu - the first time around I was using the 32bit without luck.  When I did a new OS install, this time I installed the 64bit hoping for better results.

How do you know the ndiswrapper is defective?  I downloaded from the website and followed the instructions.

---

### Post by crjackson on 2007-07-06
> **kevdog said:**
> Do you have a 64 bit Windows driver??  You may need to look on the manufacture's website.

If not its onto plan C -- compilation of serialmonkey drivers.

Okay - I just checked and Linksys has no 64bit drivers at all.  Let's push on to plan C.

---

### Post by kevdog on 2007-07-06
Craig you are probably home and awake, Im going to bed.  Lets pick this up tomorrow.  Just for a preview here is the serialmonkey site:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

There is also a good post by depruis -- something like serialmonkey howto for rt73.  We will be using the same process but only using the cvs rt2500 driver rather than the cvs rt73 driver.

---

### Post by kevdog on 2007-07-06
Alright

First thing is to install the build-essential package.  This allows up to compile source-files.  It contains among other things the c compiler.  Again you can either install this from repository or from you ubuntu cd.  Ive included the instructions earlier in this post. (page #1)

Next is to grab a copy of the rt2500cvs source files.
mkdir ~/rt2500
cd ~/rt2500
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz) -O ~/rt2500-cvs-daily.tar.gz

Extract the module
tar -zxvf rt2500-cvs.daily.tar.gz

Now compile the module
cd ~/rt2500/rt2500-cvs-yyyymmddhh/Module  <--Must substitute appropriate directory year
sudo make

Hopefully you dont receive any errors with the make step.  If you do, stop and then post them

Now lets install our new module
sudo make install

Now make sure of the following:
gksu gedit /etc/modprobe.d/blacklist

Make sure the rt2500 module is not blacklisted.  If it is either delete the line, or put a # sign in the front of the line.  We want to make sure your wireless card is associated with the rt2500 driver.  Also add the following:

blacklist ndiswrapper

This will make sure the card is not associated in any way with ndiswrapper.

Reboot!

Load the new module:
sudo modprobe -v rt2500

Now comes the trick part
I need you to post the following:
sudo modprobe -l | grep /rt2

This will give me a list of all the "built-in" rt modules.  Some of these we will also need to blacklist.

Please repost the following now:
lshw -C network

I wait here and let you catch up.  At this point I am only looking for the card to be associated with the new rt2500 driver.  We will need to make adjustments to the /etc/network/interfaces file.

---

### Post by crjackson on 2007-07-06
> **kevdog said:**
> Alright

First thing is to install the build-essential package.  This allows up to compile source-files.  It contains among other things the c compiler.  Again you can either install this from repository or from you ubuntu cd.  Ive included the instructions earlier in this post. (page #1)

Next is to grab a copy of the rt2500cvs source files.
mkdir ~/rt2500
cd ~/rt2500
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz) -O ~/rt2500-cvs-daily.tar.gz

Extract the module
tar -zxvf rt2500-cvs.daily.tar.gz

Now compile the module
cd ~/rt2500/rt2500-cvs-yyyymmddhh/Module  <--Must substitute appropriate directory year
sudo make

Hopefully you dont receive any errors with the make step.  If you do, stop and then post them

Now lets install our new module
sudo make install

Now make sure of the following:
gksu gedit /etc/modprobe.d/blacklist

Make sure the rt2500 module is not blacklisted.  If it is either delete the line, or put a # sign in the front of the line.  We want to make sure your wireless card is associated with the rt2500 driver.  Also add the following:

blacklist ndiswrapper

This will make sure the card is not associated in any way with ndiswrapper.

Reboot!

Load the new module:
sudo modprobe -v rt2500

Now comes the trick part
I need you to post the following:
sudo modprobe -l | grep /rt2

This will give me a list of all the "built-in" rt modules.  Some of these we will also need to blacklist.

Please repost the following now:
lshw -C network

I wait here and let you catch up.  At this point I am only looking for the card to be associated with the new rt2500 driver.  We will need to make adjustments to the /etc/network/interfaces file.

> **blacklist ndiswrapper**

Would it be better to just remove the ndiswrapper since it's a broke install?  If so tell me how to do that 1st.  I'm getting ready for work and I'll have to do this when I get home.

---

### Post by kevdog on 2007-07-06
ndiswrapper didnt break the install, its just that its a bad windows driver.

By default ndiswrapper places all its installed drivers in /etc/ndiswrapper
So to remove everything (the brute force way):
sudo rm -R /etc/ndiswrapper *
If you added ndiswrapper to the kernel (sudo modprobe ndiswrapper), then uninstall the kernel module:
sudo modprobe -r ndiswrapper

If you want to physically remove the ndiswrapper user space utilities program, then undo the installation process -- for you since you used automatix to install it, use automatix to uninstall it.  This isnt really necessary but if you want to do it, you can!;)

---

### Post by catnappist on 2007-07-06
This is random, and I apologize in advance for jumping into somebody else's conversation.  I don't know how to post except to reply to someone else's that seems to have nothing to do with me.  Help?

---

### Post by crjackson on 2007-07-06
**@capnapppist**

Just go to the main catagory you're looking for, and assuming you are logged in, at the top left of the page click Make new post.

There you can start you own thread with your particular problem

---

### Post by crjackson on 2007-07-06
> **kevdog said:**
> ndiswrapper didnt break the install, its just that its a bad windows driver.

By default ndiswrapper places all its installed drivers in /etc/ndiswrapper
So to remove everything (the brute force way):
sudo rm -R /etc/ndiswrapper *
If you added ndiswrapper to the kernel (sudo modprobe ndiswrapper), then uninstall the kernel module:
sudo modprobe -r ndiswrapper

If you want to physically remove the ndiswrapper user space utilities program, then undo the installation process -- for you since you used automatix to install it, use automatix to uninstall it.  This isnt really necessary but if you want to do it, you can!;)

You indicated that the ndiswrapper appears to be a broken install, so I'd just as soon remove it.  I'll work on that tonight.  Thanks.

---

### Post by crjackson on 2007-07-07
> **kevdog said:**
> Alright

First thing is to install the build-essential package.  This allows up to compile source-files.  It contains among other things the c compiler.  Again you can either install this from repository or from you ubuntu cd.  Ive included the instructions earlier in this post. (page #1)

Next is to grab a copy of the rt2500cvs source files.
mkdir ~/rt2500
cd ~/rt2500
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz) -O ~/rt2500-cvs-daily.tar.gz

Extract the module
tar -zxvf rt2500-cvs.daily.tar.gz

Now compile the module
cd ~/rt2500/rt2500-cvs-yyyymmddhh/Module  <--Must substitute appropriate directory year
sudo make

Hopefully you dont receive any errors with the make step.  If you do, stop and then post them

Now lets install our new module
sudo make install

Now make sure of the following:
gksu gedit /etc/modprobe.d/blacklist

Make sure the rt2500 module is not blacklisted.  If it is either delete the line, or put a # sign in the front of the line.  We want to make sure your wireless card is associated with the rt2500 driver.  Also add the following:

blacklist ndiswrapper

This will make sure the card is not associated in any way with ndiswrapper.

Reboot!

Load the new module:
sudo modprobe -v rt2500

Now comes the trick part
I need you to post the following:
sudo modprobe -l | grep /rt2

This will give me a list of all the "built-in" rt modules.  Some of these we will also need to blacklist.

Please repost the following now:
lshw -C network

I wait here and let you catch up.  At this point I am only looking for the card to be associated with the new rt2500 driver.  We will need to make adjustments to the /etc/network/interfaces file.

[B]charles@eMachines-Kitchen:~$ sudo modprobe -v rt2500
Password:
charles@eMachines-Kitchen:~$ sudo modprobe -l | grep /rt2
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2400/rt2400.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2570/rt2570.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt61/rt61.ko
charles@eMachines-Kitchen:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@02:00.0
       logical name: ra0
       version: 01
       serial: 00:12:17:64:a2:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 BETA4 latency=64 multicast=yes wireless=RT2500 Wireless
       resources: iomemory:fdcfc000-fdcfdfff irq:20
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:0e:15:f4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.11.8 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:de00-deff iomemory:fdcff000-fdcff0ff irq:23
charles@eMachines-Kitchen:~$ 

[/B]

---

### Post by kevdog on 2007-07-07
I just want to check the version you installed before proceeding --- a little paranoia on my part.

Can you post the following

modinfo rt2500

---

### Post by crjackson on 2007-07-07
[B]charles@eMachines-Kitchen:~$ modinfo rt2500
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rt2x00-legacy/rt2500/rt2500.ko
license:        GPL
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 BETA4 2006/06/18
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     FE0FF717CAE37FC640C6914
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)
parm:           ifname:Network device name (default ra%d) (charp)
charles@eMachines-Kitchen:~$ [/B]

---

### Post by kevdog on 2007-07-07
Awesome -- Ok here is what I want you to type at command line, if everything works then we will make the changes permanent in the /etc/network/interfaces file so you it will be automated.  Make sure you have any WEP/WPA or MAC filtering at your router turned off.  We can add this later if you require it.

Your interface name is ra0.

sudo ifconfig ra0 down
sudo ifconfig ra0 up
sudo iwconfig ra0 essid YOUR_NETWORK_NAME_HERE
sudo dhclient ra0

The last command will lock the terminal (I think) -- which is expected.  You can kill the process with cntrl-C.  However before killing the process, open a second terminal prompt.  Type ifconfig -- to see if you have a local LAN address.  If you do, try issuing the command ping yahoo.com or any other site.  If you can ping, congrats you have internet access.  

Write back with any report so we can automate the process and add any WEP or WPA if required.

---

### Post by crjackson on 2007-07-07
AWESOME!  IT WORKED!:D

I do need to automate it so it loads at boot.  I do need a WEP key turned back on.

The network connection icon on the task bar indicates no connection but a good signal strength. Tell me what (if anything) I should do with that.  Ideally I would like that thing to work, but I'm just so damned happy to have a wireless connection, it doesn't really matter that much to me.

Thanks....:D

---

### Post by kevdog on 2007-07-07
Ill post back later what to do.  Finally after about 2 weeks of work, it worked.  Cant say most people would have stuck it out that long.

The bars you talk about in the task bar that indicate no connection -- thats the network manager program.  ra drivers do not work very well with network manager.  As a replacement, there is a program that is known as rutilt (sorry spelling might be off).  We will compile that later.  I think it will give you what you want.

Ill give you full details later since you need WEP

The rest is just icing on the cake -- the hard work is done:p

---

### Post by kevdog on 2007-07-07
First thing -- how to automate.  I wrote these instructions for someone else off another post.  I just copied and pasted.

They should work however:

Ok its  easy to automate however just a few points.

#1. You need to know what interface your wireless card is assigned to.  This could be wlan0, eth0, eth1, ra0, ra1, etc.  This best way to determine this if the following:

```
lshw -C network
```

Look for the line that states [COLOR="Red"]logical name[/COLOR].  That is your interface name

#2. Network manager does not work with ra cards.  So dont even try to use it or it will screw everthing up.

If the above manual commands worked for you (see previous post above), here is how to automate the process

1.  ```
gksu gedit /etc/network/interfaces
```

2. Look for the section containing your interface name (wlan0, eth0, eth1, etc)
```

auto *interface_name*
iface *interface_name* inet dhcp

```

3. Beneath these lines add the following:
```
	
pre-up ifconfig *interface_name* up
pre-up iwconfig *interface_name* essid YOUR_ESSID
pre-up iwconfig *interface_name* key WEP_KEY_OR_DO_NOT_INCLUDE_THIS_LINE_IF_YOU_DO_NOT_NEED_WEP

```

4. If using WPA make your section appear like this:
```

auto *interface_name*
iface *interface_name* inet dhcp
pre-up ifconfig *interface_name* up
pre-up iwconfig *interface_name* essid "YOUR_ESSID"
pre-up iwconfig *interface_name* mode managed
pre-up iwpriv *interface_name* set AuthMode=WPAPSK
pre-up iwpriv *interface_name* set EncrypType=TKIP
pre-up iwpriv *interface_name* set WPAPSK="YOUR_WPA_PSK_KEY"
pre-up iwpriv *interface_name* set SSID="YOUR_SSID"

```

If you requires a static IP address, then make the following modifications:

```

auto *interface_name*
iface *interface_name* inet static
address *192.168.168.40*
gateway *192.168.168.230*
dns-nameservers *192.168.168.230*
netmask *255.255.255.0*

```


I dont know if the dns-nameservers is absolutely necessary so you might want to try with and without it.
Also substitute the appropriate values of the entries in italics for whatever works with your setup

To restart everthing and enable the changes:
```
sudo /etc/init.d/networking restart
```

If that doesnt work
```
sudo /etc/init.d/dbus restart
```

If that doesnt work, Reboot!

---

### Post by crjackson on 2007-07-07
Cool.  My daughter is playing runescape on it right now, so I'll do the automation after she finishes...

Man what a relief...

---

### Post by kevdog on 2007-07-07
Ill modify the instructions (actually add to them later, to get the GUI up and running).  You will have to compile and install the program, but after doing everything up to this point, you should be a pro!

---

### Post by kevdog on 2007-07-08
Ok try this out for a graphic utility -- Its known as RutilT

Lets get the sources

```
mkdir ~/RutilT
cd ~/RutilT
wget http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz -O ~/RutilT/RutilTv0.15.tar.gz
```

Extract the files

```
tar -zxvf RutilTv0.15.tar.gz
cd RutilTv0.15
```

Before compiling the source it requires a package known as libgtk2.0-dev.
So lets install that package

```
sudo aptitude install libgtk2.0-dev
```

I also going to install the wpa package in case you ever need WPA encryption for a network

```
sudo aptitude install wpasupplicant
```

Ok now lets compile the RutilT files:

```
./configure.sh --launcher=external
make
sudo make install
```

Now to run the program type at the command prompt:

```
rutilt
```

This should produce a system tray icon along with showing the networks in your area.  If you can start this manually then we can later add it to a startup script that will allow it to start at boot if you want!

---

### Post by crjackson on 2007-07-08
Automation worked out good - I removed the network manager icon from the taskbar.

I can't download the other utility though.

charles@eMachines-Kitchen:~$ wget [http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz](http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz) -O ~/RutilT
/home/charles/RutilT: Is a directory
charles@eMachines-Kitchen:~$

---

### Post by kevdog on 2007-07-08
I modified the wget statement.  Sorry about that:(

---

### Post by crjackson on 2007-07-09
> **kevdog said:**
> I modified the wget statement.  Sorry about that:(

[B]charles@eMachines-Kitchen:~/RutilT$ tar -zxvf RutilTv0.15.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
charles@eMachines-Kitchen:~/RutilT$
[/B]

---

### Post by kevdog on 2007-07-09
I have no idea why that didnt work.

Here just do this, download the following file:
[http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz](http://cbbk.free.fr/bonrom/?download=RutilTv0.15.tar.gz)

and then place it in the ~/RutilT directory.  Then try the tar -zxvf statement again.

---

### Post by crjackson on 2007-07-09
I got to this command and then errors...

[B]charles@eMachines-Kitchen:~$ cd /home/charles/Desktop/RutilTv0.15
charles@eMachines-Kitchen:~/Desktop/RutilTv0.15$ ./configure.sh --launcher=external
Using helper_launcher.sh as launcher proxy, you may need or want to tune this script.
Generating Makefile constants... done
Generating program constants... done
Generating desktop launcher... done
Generating helper_launcher.sh... done
charles@eMachines-Kitchen:~/Desktop/RutilTv0.15$ make
    Compiling lib/WE17Driver.o
/bin/sh: g++: not found
make: *** [lib/WE17Driver.o] Error 127
charles@eMachines-Kitchen:~/Desktop/RutilTv0.15$ make
    Compiling lib/WE17Driver.o
/bin/sh: g++: not found
make: *** [lib/WE17Driver.o] Error 127
charles@eMachines-Kitchen:~/Desktop/RutilTv0.15$ sudo make
    Compiling lib/WE17Driver.o
/bin/sh: g++: not found
make: *** [lib/WE17Driver.o] Error 127
charles@eMachines-Kitchen:~/Desktop/RutilTv0.15$[/B]

---

### Post by kevdog on 2007-07-09
I want to let you know that I tried everystep I gave you on my machine first, and I didnt have a problem -- so Im not pulling these instructions out of my a$$. -- in case you were wondering

Anyway because you have an internet connection its much easier.  First Im going to assume you have the build-essential package installed.  If not, sudo aptitude install build-essential.  

Second can you post the results of 
g++ --version

I thought the g++ compiler however was installed by default with build-essential

---

### Post by crjackson on 2007-07-09
> **kevdog said:**
> I want to let you know that I tried everystep I gave you on my machine first, and I didnt have a problem -- so Im not pulling these instructions out of my a$$. -- in case you were wondering

Anyway because you have an internet connection its much easier.  First Im going to assume you have the build-essential package installed.  If not, sudo aptitude install build-essential.  

Second can you post the results of 
g++ --version

I thought the g++ compiler however was installed by default with build-essential

kevdog,

I wasn't wondering at all.  There is no way you could have amassed this much information and detailed instructions w/o having done it before.

build-essential is installed.

I'll get you the g++ --version when I get home from work.

Thanks for all your help...

---

### Post by crjackson on 2007-07-10
Okay - I installed g++ and rutil installed and runs.  I have a small problem that you may or may not know how to help with.

Any program that is supposed to minimize to the system tray doesn't.  I caused this by accident.

I only wanted to have one taskbar at the bottom of the screen so I placed my wanted items onto one task bar and removed the other one.  The system tray with the clock and standard things are still there but when I minimize thing that is supposed to go to the tray it just disappears.  Firestarter does the same thing.

Do you know how I can fix this?

---

### Post by kevdog on 2007-07-10
Im no expert on dealing with panels,  could you provide a screen shot of your desktop to show me what it looks like??  Can you just right click on the panel you have and choose and new panel?? Does this work.  You can drag the panel to left,top,bottom,right to place it if you want.

---

### Post by crjackson on 2007-07-10
> **kevdog said:**
> Im no expert on dealing with panels,  could you provide a screen shot of your desktop to show me what it looks like??  Can you just right click on the panel you have and choose and new panel?? Does this work.  You can drag the panel to left,top,bottom,right to place it if you want.

I figured out that when I removed the network manager icon it removed the notification area.  I put the notification area back and it works.  Now how do I make the RutilT app start at boot up?

Also, do you know what "Injection in monitor mode", "Tx Burst", Turbo Rate", and "OFDM in ad-hoc mode" are?

---

### Post by kevdog on 2007-07-10
Ok, this part I have not done before -- so you are going to kind of a guiney pig for this one

gksu gedit /etc/rc.local

add before exit 0
rutilt

Save the file and reboot.
You are going to have to tell me if it works!

---

### Post by crjackson on 2007-07-10
> **kevdog said:**
> Ok, this part I have not done before -- so you are going to kind of a guiney pig for this one

gksu gedit /etc/rc.local

add before exit 0
rutilt

Save the file and reboot.
You are going to have to tell me if it works!

I'll try this tonight when I get home from work.  Thanks for all the help...

---

### Post by kevdog on 2007-07-10
Let me know what happens, Im curious about this one!

---

### Post by crjackson on 2007-07-18
> **kevdog said:**
> Let me know what happens, Im curious about this one!

kevdog,

I decided I didn't need it loaded on boot so I never tried it.  I just thought I'd let you know that.  This week I plan to attempt WEP128 to get this thing secured.  I'm tired of the freebie I've been giving to the neighbors.  I'll let you know how that goes.  Anything special I should be on the lookout for?

---

### Post by kevdog on 2007-07-18
Id recommend WPA over WEP if you can do it.  But WEP is far better than nothing.  From where we last left off, configuring the interfaces file, I think you need to put one more iwconfig line in it for WEP.  Something like:
pre-up iwconfig wlan0 key WEP_KEY

Here again is a good reference:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

---

### Post by crjackson on 2007-07-21
Just an update.  I enabled WPAPSK without any issues.  Wireless is now protected and working fine.

In the rutilT program, I'm sowning the only the old profile in the profile tab and the new connection under site survey tab.

should I delete the old porfile?  Will it mess anything up if I do?

Thanks.

---

### Post by crjackson on 2007-10-24
@kevdog

I've upgraded several of my WIRED systems to Gutsy.  Dare I try this system?  Do you know if support for this card has improved or will have have a big hastle again.  If so, I'll just keep the Feisty install.

---

### Post by Koikirai on 2008-01-08
Hi guys this is my first post, just to THANK YOU SO MUCH!

This is my first day of using linux, i only got it for beryl which is now updated and merged with someone else but yeah, thanks to you guys i got my WMP54G PCI card working by following this tutorial took me about 10 hours to figure everything out as i know NOTHING about linux but i'm finally wireless. Thank you so much =]

---

