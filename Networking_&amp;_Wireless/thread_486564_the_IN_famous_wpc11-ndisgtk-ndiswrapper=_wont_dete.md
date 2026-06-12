---
title: "the IN famous wpc11-ndisgtk-ndiswrapper= wont detect my wireless card"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by chetter72 on 2007-06-28
hello, 

   Im running ubuntu 7.04 i386 and I tried everything to get my wpc11 linksys ver.4 to be detected. ndiswrapper is installed along with ndisgtk. the frustrating part is every time I try to install the driver nothing happens literally its like I didn't do anything. and the driver window in the ndisgtk  is blank. I've tried every type of driver an every version. I am a newby so terminal stuff is tuff but I learn fast. I just want this to work . thanks for your time

---

### Post by kevdog on 2007-06-28
Forget the GUI for know, lets just strictly use the command prompt. 

First lets learn a liitle bit more about your card.  Please post the following output:
lspci
lspci -n 
lshw -C network

That should cover the details of the card.

Second please post your /etc/network/interfaces file.  This file is the "heart" of getting networking up and going. Type:
more /etc/network/interfaces
Cut and paste the output.

Third -- check your installation of ndiswrapper
ndiswrapper -v <----This will give version
ndiswrapper -l <------ This will list any drivers you've tried to wrap with the wrapper


Fourth
Do you have a wired connection on the machine or another computer you could download files with and transfer to Ubuntu via USB stick???

---

### Post by chetter72 on 2007-06-28
thanks for the response,

 **_First=_ **
my card is a pcmcia wirless B linksys wpc11  ver4 -
**lspci=**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:0b.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:0b.1 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:0e.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
01:00.0 VGA compatible controller: Silicon Motion, Inc. SM710 LynxEM (rev a3)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
**lspci -n=**
00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:07.0 0601: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 03)
00:0a.0 0401: 125d:1988 (rev 12)
00:0b.0 0607: 1180:0478 (rev 80)
00:0b.1 0607: 1180:0478 (rev 80)
00:0d.0 0200: 8086:1229 (rev 08)
00:0e.0 0780: 14f1:1456 (rev 08)
01:00.0 0300: 126f:0710 (rev a3)
06:00.0 0200: 10ec:8180 (rev 20)
**lshw -C network=**
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth0
       version: 08
       serial: 00:d0:59:3d:5a:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.102 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:f4010000-f4010fff ioport:1080-10bf iomemory:f4100000-f41fffff irq:9
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@06:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: iomemory:2c000000-2c0001ff irq:9


**_second=_**
here is the out put from more/etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

[B][U]
Third=[/U][/B]

ndiswrapper -v

utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

ndiswrapper -l 
lswl2nds : invalid driver!
lswlnds : invalid driver!
lswlnds5 : invalid driver!

**_Fourth=_**I am connected via either net on the  laptop computer with the problem and it is working splendidly

I already see my drivers are nil, and my ndiswrapper is weird. thank you again! whats next Im learning a lot

---

### Post by kevdog on 2007-06-28
Ok, two things

1. Check out your ndiswrapper -v statement

ndiswrapper -v

utils Error: no version specified!
driver version: 1.38
vermagic: 2.6.20-16-generic SMP mod_unload 586 

I see an error statement

The first thing you want to do is to uninstall ndiswrapper.  I assume you installed via Synaptic, so you need to uninstall via Synaptic

Next you want to issue the following command at the command line since the uninstall procedure will not do this
cd /etc/ndiswrapper
sudo rm -R *

2. Install ndiswrapper properly from source
Since you have an internet connection, please type the following since it will allow you to compile source files
sudo aptitude install build-essential

Lets make a directory for ndiswrapper:
cd ~
mkdir ndiswrapper
Then visit the ndiswrapper website and download the ndiswrapper-1.47. : [http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)
Place this file in the ~/ndiswrapper directory

Lets untar/unzip the source file
cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz

Change into the untarred/unzipped directory
cd ndiswrapper-1.47

Then lets compile and make from source
make distclean
make
sudo make install

Ok your new compiled version of ndiswrapper should be installed.  To check lets do the following
ndiswrapper -v

You should get something like this:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-16-generic SMP mod_unload 586 

Notice no error messages in this output as compared to your old version

Now the next part deals with finding the right driver for your card
In order to do this I need the following from you:
lspci
lspci -n

If you post the following hopefully I can find the correct driver from you on the ndiswrapper website.  If I cant then the fallback is the one that comes on disk, although the results from the drivers on the disk are usually more unpredictable.

---

### Post by chetter72 on 2007-06-28
Thank you so much, so far so good, and Im learning a bunch
First - after ndiswrapper -v this is what I got

module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

**lspci=**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:0a.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
00:0b.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:0b.1 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 80)
00:0d.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 08)
00:0e.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
01:00.0 VGA compatible controller: Silicon Motion, Inc. SM710 LynxEM (rev a3)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

**lspci -n=**
00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:07.0 0601: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 03)
00:0a.0 0401: 125d:1988 (rev 12)
00:0b.0 0607: 1180:0478 (rev 80)
00:0b.1 0607: 1180:0478 (rev 80)
00:0d.0 0200: 8086:1229 (rev 08)
00:0e.0 0780: 14f1:1456 (rev 08)
01:00.0 0300: 126f:0710 (rev a3)
02:00.0 0200: 10ec:8180 (rev 20)

Again thanks I hope thisall worksafter all the timeyou have spent helping me!  thanks again!

---

### Post by kevdog on 2007-06-28
Hey before going down the ndiswrapper path, lets just try something first.

I want you to interpret the results of what you gave me.  You may not know the specific unix commands, but you can interpret the results:

First thing
lspci

Looking at the statement you gave me I was able to fish out your wireless card:
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

Basically this statement tells me that your wireless card's chipset is Realtek version 8180

Next lets look at your lshw -C network statement:
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: 82557/8/9 [Ethernet Pro 100]
vendor: Intel Corporation
physical id: d
bus info: pci@00:0d.0
logical name: eth0
version: 08
serial: 00:d0:59:3d:5a:ed
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.102 latency=66 maxlatency=56 mingnt=8 multicast=yes
resources: iomemory:f4010000-f4010fff ioport:1080-10bf iomemory:f4100000-f41fffff irq:9

*-network UNCLAIMED
description: Ethernet controller
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@06:00.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0 maxlatency=64 mingnt=32
resources: iomemory:2c000000-2c0001ff irq:9

OK you see two network devices listed (I put a space in between the two to make it more legible).
The first is your wired card, it uses the eth0 interface, and the e100 driver

The second is wireless device -- the info it provides is much different.  Notice its not yet associated with an interface name such as eth0, it has no driver listed.  So this line pretty much tells you that no driver is yet associated with your card -- ndiswrapper driver or otherwise.

OK we have choices at this point in what to do.  Its very possible we can continue to pursue to build the correct ndiswrapper driver.  

Another option however (and I know you dont know this), is that this is supposed to be one of the cards that works out of the box in Linux.  Many prior versions of Ubuntu (Breezy, Dapper) there have been problems, Im not sure how it functions in Feisty.  Lets pursue this option first and then if it doesnt work lets go back to ndiswrapper.

First, lets make sure the Realtek 8180 module is loaded in the kernel.  To do this type the following:
sudo modprobe -l | grep 81

Among some of the modules listed on my machine I find:
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl818x/r818x.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko

Hopefully these are in yours.  This basically tells you that the driver module is "built-in" to the Ubuntu Kernel.  It doesnt guarantee it will work, it just tells you it was there.

Because some of the earlier problems with the modules, they were blacklisted, meaning although they were in the kernel, the were not loaded at boot.  To change this, lets "unblacklist" the drivers:
gksu gedit /etc/modprobe.d/blacklist

At the very bottom of the file you will probably find:
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

I want you to put a # sign in front of the blacklist statements. Save the file.

Ok, now reboot, cross your fingers, and lets see what happens.  If there are problems, you can always re-blackist the drivers by removing the # sign in the file.

When you reboot, I want you to repost:
lshw -C network

Specifically I want to see if the r818x driver is associated with your device.  I also want to see the interface name.

Also post the output of:
iwconfig scan

Possibly you will be able to see some wireless networks.

If all else fails, we will reblacklist the drivers and then try to associate your wireless card with the ndiswrapper module rather than the 818x.

---

### Post by chetter72 on 2007-06-29
Well its detected but Im unable to use it as a connection

**lshw -C network=**

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: d
       bus info: pci@00:0d.0
       logical name: eth0
       version: 08
       serial: 00:d0:59:3d:5a:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.100 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:f4010000-f4010fff ioport:1080-10bf iomemory:f4100000-f41fffff irq:9
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 20
       serial: 00:0c:41:c3:49:b1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b
       resources: ioport:2000-20ff iomemory:2c000000-2c0001ff irq:9

**iwconfig scan=**

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.484 GHz  
          Access Point: Not-Associated   Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=30/100  Signal level=-39 dBm  Noise level=-186 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


there you go. I think we are almost there. Again thank you! I can see wireless networks including my own but I can not connect to them

---

### Post by kevdog on 2007-06-29
Well it sees your network and gives you a signal quality.  Again this driver might not work but lets try to manually connect and see what happens:

sudo ifconfig down wlan0
sudo ifconfig up wlan0 
sudo dhclient wlan0

If you get any errors with the above commands can you let me know!

If your router right now is set for WEP/WPA or MAC filtering, please turn all of these options off.  We can add them later

---

### Post by chetter72 on 2007-06-29
her ya go

**sudo ifconfig down wlan0=**

wlan0: Unknown host
ifconfig: `--help' gives usage information.


**sudo ifconfig up wlan0=**

wlan0: Unknown host
ifconfig: `--help' gives usage information

**sudo dhclient wlan0=**

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0c:41:c3:49:b1
Sending on   LPF/wlan0/00:0c:41:c3:49:b1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm not sure what these mean but I see no errors.Its weird It detects the card but doesn't put the option in the network the tool bar icon only gives the wired and manual configuration options. also if I put the wireless in roam mode it detects mine and others around, and even says its connected but I can't get on the internet with it.

---

### Post by chetter72 on 2007-06-30
Kevdog, 

 Man thanks a load. I got it working read some other threads and found the fix. for some reason the driver or something drops the last letter in you ssid, so you just add one and it worked. thanks for your hard work man you rock!!! and I must say I learned so much. 

 Thanks Again chetter72:p

---

### Post by kevdog on 2007-06-30
Glad you got it working -- I knew about that adding an extra letter trick, but until you mentioned it I did remember -- shoot!.  Anyway glad you got it going.  Can you post your /etc/network/interfaces file here so others can take a look at it.  That would be great!

---

### Post by Dangit on 2007-06-30
I've got the same thing as him up until the last part:

sudo dhclient wlan0=
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0=: ERROR while getting interface flags: No such device
wlan0=: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

---

### Post by chetter72 on 2007-07-01
this is what I got for my

 etc/network/interfaces

auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
thanks again Kevdog
:KS

---

### Post by rxp01 on 2007-07-13
Kevdog,

Thanks so much for this post. I did not want to use NDISwrapper (I guess I am stubborn), and this got me working! It was finicky at first, but roaming mode is working, and I am wireless at last. Every other post was using ndiswrapper, and I finally found this.

Thanks again,

=Rob



> **kevdog said:**
> Hey before going down the ndiswrapper path, lets just try something first.

I want you to interpret the results of what you gave me.  You may not know the specific unix commands, but you can interpret the results:

First thing
lspci

Looking at the statement you gave me I was able to fish out your wireless card:
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

Basically this statement tells me that your wireless card's chipset is Realtek version 8180

Next lets look at your lshw -C network statement:
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: 82557/8/9 [Ethernet Pro 100]
vendor: Intel Corporation
physical id: d
bus info: pci@00:0d.0
logical name: eth0
version: 08
serial: 00:d0:59:3d:5a:ed
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.102 latency=66 maxlatency=56 mingnt=8 multicast=yes
resources: iomemory:f4010000-f4010fff ioport:1080-10bf iomemory:f4100000-f41fffff irq:9

*-network UNCLAIMED
description: Ethernet controller
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@06:00.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0 maxlatency=64 mingnt=32
resources: iomemory:2c000000-2c0001ff irq:9

OK you see two network devices listed (I put a space in between the two to make it more legible).
The first is your wired card, it uses the eth0 interface, and the e100 driver

The second is wireless device -- the info it provides is much different.  Notice its not yet associated with an interface name such as eth0, it has no driver listed.  So this line pretty much tells you that no driver is yet associated with your card -- ndiswrapper driver or otherwise.

OK we have choices at this point in what to do.  Its very possible we can continue to pursue to build the correct ndiswrapper driver.  

Another option however (and I know you dont know this), is that this is supposed to be one of the cards that works out of the box in Linux.  Many prior versions of Ubuntu (Breezy, Dapper) there have been problems, Im not sure how it functions in Feisty.  Lets pursue this option first and then if it doesnt work lets go back to ndiswrapper.

First, lets make sure the Realtek 8180 module is loaded in the kernel.  To do this type the following:
sudo modprobe -l | grep 81

Among some of the modules listed on my machine I find:
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl818x/r818x.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko

Hopefully these are in yours.  This basically tells you that the driver module is "built-in" to the Ubuntu Kernel.  It doesnt guarantee it will work, it just tells you it was there.

Because some of the earlier problems with the modules, they were blacklisted, meaning although they were in the kernel, the were not loaded at boot.  To change this, lets "unblacklist" the drivers:
gksu gedit /etc/modprobe.d/blacklist

At the very bottom of the file you will probably find:
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

I want you to put a # sign in front of the blacklist statements. Save the file.

Ok, now reboot, cross your fingers, and lets see what happens.  If there are problems, you can always re-blackist the drivers by removing the # sign in the file.

When you reboot, I want you to repost:
lshw -C network

Specifically I want to see if the r818x driver is associated with your device.  I also want to see the interface name.

Also post the output of:
iwconfig scan

Possibly you will be able to see some wireless networks.

If all else fails, we will reblacklist the drivers and then try to associate your wireless card with the ndiswrapper module rather than the 818x.

---

### Post by achim020 on 2007-07-24
hey chetto can you post the solution you received?  thanks man

---

### Post by chromedome on 2007-07-25
I've been trying to get my wireless card running (Realtek 8185 chipset) and this thread gave me a glimmer of hope for using a native driver.  However, when I try to bring up the blacklist, I get this error:

Authentication rejected, reason: None of the authorization protocols specified are supported, host-based authentication failed.

I'm running Edgy Eft, if that makes a difference.  I do not have any immediately functional means of getting files from the Internet onto my computer until later today, when I get into town and can buy myself a couple of RW discs.

---

### Post by rawirth on 2007-07-26
I am in the same boat as chromedome, same message came up, a ne wwindow opened with
'blacklist (/ect/modprobe.d) -gedit' at the top of the window

I tried several different versions of the command but no luck.

---

### Post by dogshoe21 on 2007-08-12
If you are still having this issue, check out the thread I started, I have a solution there that seems to be working:

[http://ubuntuforums.org/showthread.php?p=3175584#post3175584](http://ubuntuforums.org/showthread.php?p=3175584#post3175584)

Joel

---

### Post by jackherer on 2007-08-30
I have ThinkPad 600E with Linksys WPC11 ver.4 and Xubuntu7.04. Tried to use Xubuntus oen driver butt did not work for me.

Now I installed Ndiswrapper as told before. "ndiswrapper -v" gives:

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename: /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version: 1.47
vermagic: 2.6.20-16-generic SMP mod_unload 586

when I try to install xp driver which o got from Linksys or Realtek webside error message for " sudo ndiswrapper -i NET8180.inf" is

installing net8180 ...
couldn't open NET8180.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.

After I made
#blacklist r818x
#blacklist r8187
to blacklist and rebooted

**lshw -C network**
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0f:66:af:17:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 multicast=yes wireless=802.11b
       resources: ioport:1000-10ff iomemory:14000000-140001ff irq:11
  *-network:1
       description: Ethernet interface
       product: 3cCFE575CT CardBus [Cyclone]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@06:00.0
       logical name: eth0
       version: 10
       serial: 00:01:02:d7:50:58
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=82.181.65.44 latency=64 maxlatency=5 mingnt=10 multicast=yes
       resources: ioport:1800-187f iomemory:1c000000-1c00007f iomemory:1c000080-1c0000ff irq:11

**iwconfig scan**
scan      No such device

**  iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b  Mode:Managed  Frequency:2.447 GHz  
          Access Point: Not-Associated   Bit Rate=11 Mb/s   
          Retry:on   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=96/100  Signal level=-46 dBm  Noise level=-252 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


** sudo ifconfig down wlan0**
wlan0: Unknown host
ifconfig: `--help' gives usage information.

** sudo ifconfig up wlan0 **
wlan0: Unknown host
ifconfig: `--help' gives usage information.

** sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:0f:66:af:17:be
Sending on   LPF/wlan0/00:0f:66:af:17:be
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

So What should I do next to get my wlan running

---

### Post by safet on 2007-09-22
> **kevdog said:**
> Hey before going down the ndiswrapper path, lets just try something first.

I want you to interpret the results of what you gave me.  You may not know the specific unix commands, but you can interpret the results:

First thing
lspci

Looking at the statement you gave me I was able to fish out your wireless card:
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

Basically this statement tells me that your wireless card's chipset is Realtek version 8180

Next lets look at your lshw -C network statement:
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: 82557/8/9 [Ethernet Pro 100]
vendor: Intel Corporation
physical id: d
bus info: pci@00:0d.0
logical name: eth0
version: 08
serial: 00:d0:59:3d:5a:ed
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.1.102 latency=66 maxlatency=56 mingnt=8 multicast=yes
resources: iomemory:f4010000-f4010fff ioport:1080-10bf iomemory:f4100000-f41fffff irq:9

*-network UNCLAIMED
description: Ethernet controller
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@06:00.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0 maxlatency=64 mingnt=32
resources: iomemory:2c000000-2c0001ff irq:9

OK you see two network devices listed (I put a space in between the two to make it more legible).
The first is your wired card, it uses the eth0 interface, and the e100 driver

The second is wireless device -- the info it provides is much different.  Notice its not yet associated with an interface name such as eth0, it has no driver listed.  So this line pretty much tells you that no driver is yet associated with your card -- ndiswrapper driver or otherwise.

OK we have choices at this point in what to do.  Its very possible we can continue to pursue to build the correct ndiswrapper driver.  

Another option however (and I know you dont know this), is that this is supposed to be one of the cards that works out of the box in Linux.  Many prior versions of Ubuntu (Breezy, Dapper) there have been problems, Im not sure how it functions in Feisty.  Lets pursue this option first and then if it doesnt work lets go back to ndiswrapper.

First, lets make sure the Realtek 8180 module is loaded in the kernel.  To do this type the following:
sudo modprobe -l | grep 81

Among some of the modules listed on my machine I find:
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl818x/r818x.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/rtl8187/rtl8187.ko

Hopefully these are in yours.  This basically tells you that the driver module is "built-in" to the Ubuntu Kernel.  It doesnt guarantee it will work, it just tells you it was there.

Because some of the earlier problems with the modules, they were blacklisted, meaning although they were in the kernel, the were not loaded at boot.  To change this, lets "unblacklist" the drivers:
gksu gedit /etc/modprobe.d/blacklist

At the very bottom of the file you will probably find:
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

I want you to put a # sign in front of the blacklist statements. Save the file.

Ok, now reboot, cross your fingers, and lets see what happens.  If there are problems, you can always re-blackist the drivers by removing the # sign in the file.

When you reboot, I want you to repost:
lshw -C network

Specifically I want to see if the r818x driver is associated with your device.  I also want to see the interface name.

Also post the output of:
iwconfig scan

Possibly you will be able to see some wireless networks.

If all else fails, we will reblacklist the drivers and then try to associate your wireless card with the ndiswrapper module rather than the 818x.

i've followed all of these instructions (from the beginning) and thought things were going well until i removed the 2 drivers from the blacklist and rebooted. When my system came up again my ethernet wouldn't connect and my wifi card isn't recognized at all anymore. before the reboot i could see it when i ran lspci and lshw -C network. any suggestions i could try?

---

