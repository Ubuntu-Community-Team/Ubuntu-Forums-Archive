---
title: "Wireless card woes"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by Gari22 on 2007-07-23
Hi

I've been trying to install a Wireless card (Belkin BLKWGDv7  Part # F5D7000uk ver. 7000uk). 

I tried installing the driver which came on the disc, but in Hardware Information it showed up as an unknown device.

I tried installing a driver from Belkin's website, which also didn't work.

And I tried a driver which was supposed to be for the chipset in my card.


I'm using Ubuntu Studio and have tried in both the Low Latency and Generic Kernels (2.6.20-16)

Any help would be greatly appreciated.
Thanks,
Sam

---

### Post by fredj on 2007-07-24
Open a terminal and type sudo  lshw -class network
Post the output from that here.

---

### Post by chromedome on 2007-07-24
I've been grappling with the same card for a few weeks, now, off and on (I'm self-employed, and 18-hour days leave little time and few brain cells for computer problems).  While we're waiting for Sam to come back with his output, I'm going to post mine:

> 
*-network: 0 UNCLAIMED
	description:	Ethernet controller
	product:	Belkin
	vendor:	Belkin
	physical id:	a
	bus info:	pci@00.0a.0
	version:	20
	width:	32 bits
	clock:	33MHz
	capabilities:	bus_master cap_list
	resources:	ioport:c800-c8ff iomemory:febff400-febff5ff irq:225
*-network: 1
	description:	Ethernet interface
	product:	VT6102 [Rhine-II]
	vendor:	Via Technologies, Inc.
	physical id:	12
	bus info:	pci@00.12.0
	logicalname:	eth0
	version:	78
	serial:	00:19:66:18:bb:43
	size:	10MB/s
	width:	32 bits
	clock:	33MHz
	capabilities:	bus_master cap_list ethernet phsyical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
	configuration:autonegocation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
	resources:	ioport:d800-d8ff iomemory:febffc00-febffcff irq:209


I have found no obvious way to disable the onboard Ethernet on my ASRock P4VM890 mobo...no documented jumper, nothing in the BIOS.  I don't know if this is a factor or not.

Ndiswrapper reports my Windows driver as properly installed, and the hardware shows as present, though it's not recognized in Device Manager as a wireless card.

I've also downloaded a native Linux driver from RealTek (rtl8185_linux_26.1010.0531.2006.tar.gz) and have extracted it, but (blush) have not yet had time to find out how to install it.

I am an utter Linux noob but I go back to DOS 2.x so the command line is old and familiar to me (I used to write a mean batch file, back in the day).  I'm currently running Edgy Eft.

Thanks in advance for any help that may be available...

-Fred

---

### Post by chromedome on 2007-07-27
(bump)

Son of a gun, this is a busy forum...go figure.

If I had any hair left, I'd be pulling it out...;)

Any further bright ideas from anyone?  I can track an individual thread and try to follow it to a resolution, but trying to bull my way through this huge monster thread in search of usable tidbits would be difficult for me given my work situation (and I don't want to wait until October, when tourist season is over, to get this resolved).

Thanking you all in advance...

---

### Post by kevdog on 2007-07-27
Can you confirm the chipset of this device.  Some other post on google said it was an ra chipset not a realtek.  Im not sure if this info is accurate.

---

### Post by ugm6hr on 2007-07-27
Other info that would be useful:
```
lspci -nn
```
Looking for Network Controller info (corresponding to Belkin wifi).  You need to then make a note of the PCI ID [xxxx: xxxx] near the end of the line, and look it up on google (or ndiswrapper page below).

There tend to be lots of different chipsets in this piece of technology: 
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

Possibilities: Atheros 5005G (likely to work out of box - so probably not what you've got); BCM4306 (common culprit); Ralink RT2500 (has reasonable support - but built-in drivers not fantastic).

Search for the chipset you think you've got here in this forum, or in the ubuntu community wiki.  Or post back here with output from lspci -nn

---

### Post by Junglizer on 2007-07-27
> 
*-network: 0 UNCLAIMED
description: Ethernet controller
product: Belkin
vendor: Belkin
physical id: a
bus info: pci@00.0a.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
resources: ioport:c800-c8ff iomemory:febff400-febff5ff irq:225
*-network: 1
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: Via Technologies, Inc.
physical id: 12
bus info: pci@00.12.0
logicalname: eth0
version: 78
serial: 00:19:66:18:bb:43
size: 10MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet phsyical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration:autonegocation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
resources: ioport:d800-d8ff iomemory:febffc00-febffcff irq:209

I see this crap in all of the "help me get my X wireless card to work" threads, so my question is why does everyone post this? 
The information in that dump are far less useful then a simple dmesg, lspci, or ifconfig dump.

---

### Post by chromedome on 2007-07-27
Thanks for taking an interest, ugm6hr and kevdog.  I can verify that the chipset is indeed the RealTek 8185, because I physically inspected the card before I began looking for solutions online.  I will try your lspci suggestion and report back in the morning (it's well after midnight here, and I've got to be back in a few hours to start all over again).

Junglizer, the reason I posted that info is quite straightforward: I'm an utter n00b, and somebody who was willing to help asked for the info.  I will cheerfully use and post the output of any program that will help me get my wireless running; and one glorious day when tourist season is over (and I'm therefore not working 100+ hours a week), I will set about learning my new OS properly.

Thank you for your input, though, and if you could offer up specific syntax I will certainly use it.

---

### Post by chromedome on 2007-07-28
Okay, the output of the lspci -nn is:

> fred@fred-desktop:~$ sudo lspci -nn
Password:
00:00.0 0600: 1106:0327
00:00.1 0600: 1106:1327
00:00.2 0600: 1106:2327
00:00.3 0600: 1106:3327
00:00.4 0600: 1106:4327
00:00.5 0800: 1106:5327
00:00.6 0600: 1106:6327
00:00.7 0600: 1106:7327
00:01.0 0604: 1106:b198
00:02.0 0604: 1106:a327
00:0a.0 0200: 1799:700f (rev 20)
00:0f.0 0104: 1106:3149 (rev 80)
00:0f.1 0101: 1106:0571 (rev 06)
00:10.0 0c03: 1106:3038 (rev 81)
00:10.1 0c03: 1106:3038 (rev 81)
00:10.2 0c03: 1106:3038 (rev 81)
00:10.3 0c03: 1106:3038 (rev 81)
00:10.4 0c03: 1106:3104 (rev 86)
00:11.0 0601: 1106:3227
00:11.5 0401: 1106:3059 (rev 60)
00:12.0 0200: 1106:3065 (rev 78)
01:00.0 0300: 1106:3343 (rev 02)


A bit of Googling shows that 1799:700f corresponds to my Belkin card (RTL 8185 chipset), the rest are the Via chipset on my mobo.

The Google search I did pulls up these three hits:

[http://www.google.com/search?hl=en&rls=com.microsoft%3Aen-ca%3AIE-SearchBox&rlz=1I7SUNA&q=1799%3A700f+](http://www.google.com/search?hl=en&rls=com.microsoft%3Aen-ca%3AIE-SearchBox&rlz=1I7SUNA&q=1799%3A700f+)

I'm going to try the nswrapper -a avenue, and see how far that gets me.  I've seen several people post that they are successfully running cards wtih this chipset...some with ndiswrapper, some with native Linux drivers...and it irritates me exceedingly that I haven't been able to make either one work for me.

---

### Post by kevdog on 2007-07-28
If you go for ndiswrapper, try using the win 98 drivers over the winxp drivers.  Just another nuance for you.  Ive also read in some cases that a bogus character needs to be added to the essid for it to connect.  (In some cases).  For example if your essid = HOME, then to connect, specify the essid as HOMEx.  Just a few suggestions.  I dont own a rtl card, in fact its my least favorite chipset.

---

### Post by chromedome on 2007-07-28
I'm coming to see why...

Nevertheless, I'm too stubborn and too cheap to go buy another card when others are bullying this same chipset into functionality.

It turned out that my version of ndiswrapper doesn't support the -a parameter.  It also wouldn't report a version number, so I came to the office computer and downloaded the most recent version from Sourceforge.  Now I just need to figure out how to install the program...(starting over with a new OS is *such* fun).

I'm not wedded to ndiswrapper.  I've downloaded the current Linux driver from RealTek's website, I just don't know how to install it.  Searching the documentation has so far unaccountably failed to yield that information.  It occurs to me, though, that I haven't tried that search here on the forums, so I guess that'll be my next step.

---

### Post by ugm6hr on 2007-07-28
> **chromedome said:**
> It turned out that my version of ndiswrapper doesn't support the -a parameter.  It also wouldn't report a version number, so I came to the office computer and downloaded the most recent version from Sourceforge.  Now I just need to figure out how to install the program...(starting over with a new OS is *such* fun).


Someone who got your exact card to work:
[http://ubuntuforums.org/showthread.php?p=2402378#post2402378](http://ubuntuforums.org/showthread.php?p=2402378#post2402378)
This works with the Feisty built-in ndiswrapper (according to final post), but it also tells you how to install latest ndiswrapper if you want to.  Remember kernel updates may not work properly if you compile it manually (if this matters to you).

---

### Post by chromedome on 2007-07-28
Okay...having spent a little bit of time in a Terminal window farting around, I figured out my basic navigational issues and was able to install the native Linux driver provided by RealTek.

When I ran the command wlan0up, though, I got this:

> 
insmod: error inserting 'r8180.ko': -l unknown symbol in module
wlan0: ERROR while getting interface flags: No such device


Next step?

---

### Post by Gari22 on 2007-07-29
Hi, guess I should have checked back sooner.  My card is identical to chromedome's, the Realtek 8185.

I do know that the "driver" supplied by the Realtek website is just something they've nicked from the community.  And as far as I can tell, that is only half what you need.  That supplies the driver for the chipset, but there is a separate radio part to the card, and there are several versions of this part.  

I'm alright using the Terminal, but all this networking stuff is new to me.  Thanks for the replies

If anyone knows anything about this radio stuff, that would help.  

Sam

---

### Post by chromedome on 2007-07-30
I've gotten no further forward with this, largely due to work hours.  I've done nothing further with the native Linux driver, pending input from somebody who knows what to do, and switched my efforts to the ndiswrapper solution.

Trying the solution used in the older thread linked above, I downloaded the newest ndiswrapper and installed it.  Now when I try to load a driver using the graphical interface, it won't show an installed driver BUT says "DRIVER" (not the name of the specific driver I'm using, just the word 'DRIVER") is already installed.  I can't uninstall it graphically, but I can through the command line.  When I try to install the drivers manually from the command line, every driver (from the distribution disc or the Realtek website) errors out at line 217.

Too tired to get into it now, but I'll try to get back tomorrow with specific error messages.

---

### Post by ugm6hr on 2007-07-30
ndis-gtk doesn't work properly.  so you have to use CLI for ndiswrapper.

---

### Post by chromedome on 2007-07-31
Unfortunately, CLI doesn't work for me either with ndiswrapper.  Back later with specific error messages.

---

### Post by Steve1961 on 2007-07-31
OK guys, if your sure that your card has the realtek chipset you don't need to compile the latest ndiswrapper, just ndiswrapper from the repos or your installation CD.  Then download this [driver]("ftp://202.65.194.212/cn/wlan/x86-8185(1094).zip") 

Double click the zip file and extract the contents to a folder in your home directory - I've made one called windriv.

Then open a terminal and type:

sudo ndiswrapper -i /home/yourusername/windriv/net8185.inf

Check that the driver is installed by typing:

ndiswrapper -l

At this point the output should show that the driver is installed but not associated with your hardware.  To resolve this first type:

lspci -n

You should see a line in the output similar to:

02:00.0 0200: 1799:701f (rev 20)

You number may be slightly different, but make a note of whatever the 1799:701f entry is.  Then type:

ndiswrapper -a 1799:701f net8185 (insert your entry in the relevant place)

Check that the driver is now associated with the hardware by typing ndiswrapper -l again.

If all went OK, type:

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo gedit /etc/modules - and add the word ndiswrapper to the end of the file

Then click on network manager and configure your connection (I had to reboot before it would let me do this).

I have a Belkin F5D7010 Verr7000uk, but it has the same chipset so the instructions should be the same.

---

### Post by Gari22 on 2007-08-03
OK, I followed those instructions and it seems to all be correct now, Wireless Connection shows up in Network Settings, but I can't connect and in Device Manager WLAN Interface still shows Device: Unknown

Sam

---

### Post by kevdog on 2007-08-03
As far as ndiswrapper (dont need to be redundant) and rtl -- you need the win 98 drivers for your card.

To see if ndiswrapper is appropriately installed, first check the version
ndiswrapper -v

Can you tell us the version ??

Next see if the driver is installed appropriately:
ndiswrapper -l

Again should not receive duplicate drivers.  If an alternate driver is listed (r8185), you need to make sure this driver is blacklisted in the /etc/modprobe.d/blacklist file.

Next the ndiswrapper module needs to be appropriately inserted in the kernel, you can check a couple of things to determine this:
modprobe -l ndiswrapper
modinfo ndiswrapper

A just a couple of house keeping tasks
Do you have a file name /etc/modprobe.d/ndiswrapper??
Inside this file should be the following:
alias wlan0 ndiswrapper

Also inside the /etc/modules file should be one line (among other lines) that states
ndiswrapper

Check these things and report back.  I fear you will have ndiswrapper 1.38, hopefully not!!

---

### Post by Gari22 on 2007-08-03
Just in case any of this stuff is useful:

sam@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sam@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:79:04:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:EA:79:04:08  
          inet addr:169.254.3.135  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9213 (8.9 KiB)  TX bytes:9213 (8.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3F:2F:05:E2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Memory:fb004000-fb004025 

wlan0:ava Link encap:Ethernet  HWaddr 00:17:3F:2F:05:E2  
          inet addr:169.254.5.161  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Memory:fb004000-fb004025 

sam@ubuntu:~$ sudo ndiswrapper -l
net8185 : driver installed
        device (1799:700F) present


I'm wondering if the hardware is all installed correctly and I just don't know how to configure the network in Ubuntu or if there are still hardware issues.

Thanks,
Sam

---

### Post by noob12 on 2007-08-03
Based on the iwconfig.  It looks like your radio may actually be off.  Check hardware switches.  Right click the NetworkManager icon and make sure Wireless Enabled is checked.

Please run:

```

iwlist scan

```

---

### Post by kevdog on 2007-08-03
Please post some of the things I mentioned in the last post along with 
lshw -C network

Posting ifconfig, iwconfig statements dont do anybody any good until we can confirm the driver is successfully installed

---

### Post by Gari22 on 2007-08-05
Alright then, here goes:



sam@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:17:3F:75:F0:20
                    ESSID:"Garibaldi22"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


sam@ubuntu:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 7
       bus info: pci@02:07.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:2f:05:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Realtek,11/22/2006,5.1094.1122. latency=64 link=no maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11b
       resources: ioport:a000-a0ff iomemory:fb004000-fb0041ff irq:19
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 13
       serial: 00:0f:ea:79:04:08
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 firmware=N/A latency=64 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: iomemory:fb000000-fb003fff ioport:a400-a4ff irq:19



sam@ubuntu:~$ sudo ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586


sam@ubuntu:~$ modprobe -l ndiswrapper
/lib/modules/2.6.20-16-lowlatency/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko


sam@ubuntu:~$ modinfo ndiswrapper
filename:       /lib/modules/2.6.20-16-lowlatency/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.38
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     BAC0B2B6ECA821BB17E1CCA
depends:        usbcore
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)


Do you have a file name /etc/modprobe.d/ndiswrapper??
Inside this file should be the following:
alias wlan0 ndiswrapper

Yes this is here and ndiswrapper is in etc/modules



I hope all this stuff means something to you
Thanks,
Sam

---

### Post by kevdog on 2007-08-06
Here is what I suggest -- lets first upgrade you to version 1.4x of ndiswrapper - you are using an old version.

Here is how to uninstall ndiswrapper -- 

**[SIZE="4"]Ndiswrapper Uninstall Instructions[/SIZE]**
 Dont worry if some of these commands dont do anything or seem not to work -- some may be repetitive.

```

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
gksu gedit /etc/modules
	Remove line that reads ndiswrapper if present
sudo rmmod ndiswrapper
sudo rm -rf /etc/ndiswrapper/*
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

```

**[SIZE="4"]Download, Compiling, Installing and Configuring Ndiswrapper from Source Files[/SIZE]**

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


OK next we want to download the ndiswrapper source files (Reference URL = _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_)

We are grabbing ndiswrapper-1.48-rc1

```
cd ~
mkdir ndiswrapper
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz -O ~/ndiswrapper/ndiswrapper-1.48rc1.tar.gz 
cd ndiswrapper

```

Extract, compile, and install ndiswrapper
```
tar -zxvf ndiswrapper-1.48rc1.tar.gz
cd ndiswrapper-1.48rc1
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```

The output should be something like the following:
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.48rc1
vermagic:       2.6.20-16-generic SMP mod_unload 586

```

Next create and place your Window's wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the Window's driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running

---

### Post by Gari22 on 2007-08-06
It's just a column of error messages, in fact there is so much, I didn't want to text bomb this thread.

I couldn't install ndiswrapper,  I've been having problems with this installation and there's no useful data on the drive, so I'm going to reinstall Ubuntu Studio and try again.

Sam

---

### Post by Gari22 on 2007-08-06
Whoops, forgot to put in the pastebin address.  If this means anything:

[http://ubuntu.pastebin.com/fdb71413](http://ubuntu.pastebin.com/fdb71413)

Thanks,
Sam

---

### Post by kevdog on 2007-08-06
I dont think you installed the linux header files as instructed in the instructions:

sudo aptitude install build-essential linux-headers-`uname -r`

---

### Post by Gari22 on 2007-08-12
I'm not reinstalling Ubuntu Studio, as I no longer have a need for it.  I have bought a Mac for music production and use other versions of Linux for general computer stuff.

Thanks for all the help, I appreciate it but Ubuntu Studio didn't really have what I need anyway and Ubuntu has never seemed like the best distro to me, I'll keep an eye on it though.

Sam

---

### Post by kevdog on 2007-08-12
Wow caught me off guard with that one --- well good luck to you.

---

### Post by chromedome on 2007-09-10
After weeks of being too damned busy and tired to deal with this, I took another stab today.

I saw a wireless-g range extender in a local store, and thought, "Hey...that would connect to my (fully functional) wired ethernet connector, and it would also give better signal on my side of the building...that's worth a try."

So I connected the wee beastie to my computer, and immediately was beset by an amusingly large number of problems.  So, I disconnected it and restarted, and...(drum roll)...the OS now recognizes my wireless card.  I don't know why, and I'll be afraid to turn my machine off, now, but it's there.  Go figure.

So, thanks everybody for all your help, and I guess I'm off to the n00b section to look for instructions on configuring the card now that it's running.

---

### Post by chromedome on 2007-09-10
...and, just like that, I'm up and running.

I left my machine happily downloading the 900-odd updates that were available online, which should take a little while on our poky satellite broadband.  Once that's done, I'll have to make a decision about whether or not to upgrade to Feisty.

Now...in order to make life simpler for myself in future, I desperately want to know how and why I'm running now.  Not that I'm looking a gift horse in the mouth, mind you, but everything I'd tried in the past  - whether ndsiwrapper or the native driver - gave me grief.

What information do I need to find to tell me a) which driver I'm actually using, and b) which settings I need to record for future use, if my next upgrade goes all pear-shaped on me?

---

### Post by ugm6hr on 2007-09-12
> **chromedome said:**
> What information do I need to find to tell me a) which driver I'm actually using, and b) which settings I need to record for future use, if my next upgrade goes all pear-shaped on me?

a. Try this in terminal 
```
lshw -C network
```

b. Result from a - uncertain what else.

---

