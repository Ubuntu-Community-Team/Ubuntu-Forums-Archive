---
title: "BCM4318 Wireless"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Newuser1111 on 2007-08-17
Acer Laptop.
Wireless isn't working! Why?

---

### Post by notoriousdbp on 2007-08-17
OK, can you give us a bit more info, such as have you just installed Ubuntu, was it working before etc.  There are loads of people who use this card and plenty of How To's on this forum for getting this card up and running.  I'm actually using the same card now.
Go to  [http://ubuntuforums.org/showthread.php?t=524797&highlight=43xx](http://ubuntuforums.org/showthread.php?t=524797&highlight=43xx) and my post (number 4) has the drivers in a zipped folder that you can use with  the program called ndiswrapper to get it up and running

---

### Post by Newuser1111 on 2007-08-17
I installed ubuntu yesterday & it dual boots with windows.
The wireless works on windows xp.

---

### Post by notoriousdbp on 2007-08-17
OK you obviously have internet - is this in ubuntu?

---

### Post by Newuser1111 on 2007-08-17
No, I'm here using the wireless internet on my PSP.
What do I do with the .SYS and the .INF?

---

### Post by ios_base on 2007-08-17
You know... I tried 3 different standard ways to install that exact same card on my friends acer laptop.  I'm a little stuck...  You see there used to be an "eth1" port that was the wireless card.  Now when I try "iwconfig" it just gives me "eth0    no wireless extensions."  For some reason the "eth1" just disappeared and I don't know how to tell it that I want it back.  When I use "lshw" and "lspci" it tells me I have it...   :(   Can anyone tell me what's going wrong?

---

### Post by Newuser1111 on 2007-08-17
What do I do with BCMWL5.INF and BCMWL5.SYS that was in wireless.zip.

---

### Post by ios_base on 2007-08-17
okay, this could help:
> 
Bus info        Device      Class       Description
===================================================
pci@06:01.0     eth0        network     BCM4401-B0 100Base-TX
pci@06:02.0                 network     BCM4318 [AirForce One 54g] 802.11g Wireless LAN Cont

that was output from: 
```
sudo lshw -C network -businfo
```

See under device where there's no "eth1" ?  How do I change it...

---

### Post by ios_base on 2007-08-17
> **Newuser1111 said:**
> What do I do with BCMWL5.INF and BCMWL5.SYS that was in wireless.zip.

You use ndiswrapper to install the .INF file:
```
sudo ndiswrapper -i <location of .inf file> 
```

---

### Post by Newuser1111 on 2007-08-17
Where do I get Ndiswrapper and How do I use it and How do I install it?

---

### Post by kchaja on 2007-08-17
I found this guide in czech Ubuntu:

at first install ndiswrapper:
```
sudo apt-get install ndiswrapper-common
sudo apt-get install ndiswrapper-utils-1.9

```

Shutdown modul for linux drivers:
```

sudo rmmod bcm43xx
```

Check other drivers in Mdiswrapper:
```
ndiswrapper -l
```

If there is, then uninstall:

```
sudo ndiswrapper -e driver_name_in_left_side
```

And install windows drivers (extract Zip archiv from notoriousdbp)
```
sudo ndiswrapper -i bcmwl5.inf
```

Now check with this:
```
ndiswrapper -l
```
If there is, its OK

Now lets use the modul:
```
sudo modprobe ndiswrapper
```

And u can check with this command:
iwconfig



Originally from: [http://wiki.ubuntu.cz/Wi-Fi/BCM4318](http://wiki.ubuntu.cz/Wi-Fi/BCM4318)
And now, I will try it :)

---

### Post by Newuser1111 on 2007-08-17
it says Couldn't find ndiswrapper-common

---

### Post by Newuser1111 on 2007-08-17
How Do Install Ndiswrapper Without Already Having An Internet Connection.

---

### Post by Newuser1111 on 2007-08-17
Or does it reqiure an internet conection?

---

### Post by Sand Lee on 2007-08-17
It does, have you tried using ethernet?

---

### Post by kevdog on 2007-08-17
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

***The following section will work if you have an internet connection
*** If you do not have an internet connection, on a different computer you will need to download the ndiswrapper source file from: 
[http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.48rc1.tar.gz)
Please place this file on a flash drive (USB Flash drive), transfer it to the Ubuntu machine, and then place it in the ~/ndiswrapper directory.  Continue with the next following set of instructions
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

### Post by Newuser1111 on 2007-08-17
Now I have Ndiswrapper and the wireless still isn't working! How do I use wireless?

---

### Post by Newuser1111 on 2007-08-18
help?

---

### Post by kevdog on 2007-08-18
Ok 

post the following:

ndiswrapper -v
ndiswrapper -l
lshw -C network

If ndiswrapper is installed correctly -- you are close!!

---

### Post by Newuser1111 on 2007-08-18
for ndiswrapper -v it's output was

modinfo: could not open ndiswrapper: No such device
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: No such device

for ndiswrapper -l it's output was

bcmw15 : driver installed
device (14E4:4318 ) present (alternate driver: bcm43xx)

I put a space to remove the smiIlie.

---

### Post by Newuser1111 on 2007-08-18
help?

---

### Post by Newuser1111 on 2007-08-18
Help me!

---

### Post by kevdog on 2007-08-18
Quit bumping the thread -- people have to sleep!!

Im not sure if your ndiswrapper is setup correctly.  It could be

Please provide the following:

modinfo ndiswrapper
sudo modprobe -l ndiswrapper

---

### Post by notoriousdbp on 2007-08-18
It's possible you haven't
a) blacklisted bcm43xx
b) told ubuntu to load ndiswrapper at startup

For a), open a terminal and type in
```
sudo gedit /etc/modprobe.d/blacklist
``` - a text editor will open.  Page down to the end of the document and add this line
```
blacklist bcm43xx
```

Save and close the doc

The terminal should still be open. To do b) type in
```
sudo gedit /etc/modules
```

and add this line at the end of the doc
```
ndiswrapper
```

Reboot and let us know how you get on

---

### Post by Newuser1111 on 2007-08-18
For modinfo ndiswrapper

modinfo: could not open ndiswrapper: No such device

For sudo modprobe -l ndiswrapper

Password:
/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko

---

### Post by Newuser1111 on 2007-08-18
It works now!
Is It slower than windows?
And why do the fonts look wrong?

---

### Post by notoriousdbp on 2007-08-18
nice one :) glad you got there in the end.  as for the fonts looking 'wrong' it might be because you are used to clear type.  also windows core fonts like arial don't come with linux. as this is your first bash at ubuntu then i would hunt around for a program called automatix (there's plenty of referneces to it on this forum) which installs loads of useful apps which should help you to feel at home.

---

### Post by likemindead on 2007-08-19
Well, I followed every step meticulously but to no avail. My Acer Aspire 3003LCi with a BCM4318 still doesn't want to go wireless. Any help will be *greatly* appreciated. Thanks in advance....

---

### Post by likemindead on 2007-08-19
Well folks, I followed the steps on this thread:

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

and then installed Wicd Manager from here:

[http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

and I'm rockin' and rollin'!!!:guitar:

---

### Post by boomcat on 2007-08-22
After nearly a week of struggling with my Broadcom wireless card I finally found the solution, and here it is:

[http://ubuntuforums.org/showthread.php?p=3208474#post3208474](http://ubuntuforums.org/showthread.php?p=3208474#post3208474)

Specs: 
Thinkpad T20, Pentium 3
Feisty Fawn 7.04
Card: Linksys WPC54G (label says “ver 03” but iwconfig says “ver 02”) with Broadcom 4318.

The procedure took about 20 minutes, with only one problem. After: “sudo ndiswrapper -i bcmwl5.inf” I got the error message “bcmwl5 already exists”. I searched for this filename but I found only an empty folder in the /etc directory, so I went to Terminal and “sudo rmdir bcmwl5” and removed it. Then I picked up the installation where I had left off and it worked all the way through. Apparently my problem was some left-over files from previous busted installation attempts. There may have been other problems, too, but these installation instructions are so comprehensive that they include comments and examples of returned text and you just roll over the problems. Other than stated, I followed the instructions to the letter.

So thanks, Kevdog!

---

### Post by boomcat on 2007-08-22
And the OTHER computer that I'm converting to Ubuntu was so scared that its wireless card (a Linksys PCI card with the BCM4306 chip) decided to start working spontaneously!

Life is good.

---

### Post by McDorian on 2007-09-04
Just to say that I have exactly the same problem as Ios_Base and have no idea how to solve it.

The problem arose after following the Howto here

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Previously I had a broken (worked on dapper, and also after Feisty ugrade, but mysteriously stopped working about a month ago) wireless connection on a Compaq Presario R3000. I thought some leftover files, like the bcmlw5 that came from my Windows partition, may have caused problems, but why should that make eth1 disappear completely?

Any suggestions most welcome.

---

### Post by kevdog on 2007-09-04
If you can post 

lshw -C network
/etc/iftab
/etc/network/interfaces

It would help, and we can get you rolling.

---

### Post by McDorian on 2007-09-04
Thanks for the quick reply. What I have is as follows

lshw -C network

 *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:41:39:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:17
  *-network:1 UNCLAIMED
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
       resources: iomemory:e0104000-e0105fff irq:11

/etc/iftab

# This file assigns persistent names to network interfaces.

# See iftab(5) for syntax.



eth0 mac 00:0f:b0:41:39:ad arp 1

eth1 mac 00:90:4b:99:4f:9f arp 1

/etc/network/interfaces

auto lo

iface lo inet loopback

address 127.0.0.1

netmask 255.0.0.0





iface eth0 inet static

address 192.168.1.3

netmask 255.255.255.0

gateway 192.168.1.1





auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp

---

### Post by kevdog on 2007-09-04
You dont have any driver associated with your wireless device.  What method have you tried?  The only two methods I know available to you are either bcm43xx or ndiswrapper/winxp drivers.

---

### Post by McDorian on 2007-09-04
OK, I'll have to stop now. It's midnight here in France and I have a baby to feed.

Am I right in thinking that /etc/network/interfaces is causing the problem?  There seems to be nothing in there defining eth1.

I'll check up again tomorrow, but I won't be able to send any more info till then.

---

### Post by McDorian on 2007-09-04
I tried the python script from Darknoob 
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
that was supposed to set up Ndiswrapper. However, after a reboot eth1 disappeared.

Really got to go now ..;..

---

### Post by kevdog on 2007-09-04
Whatever script you followed didnt successfully setup the driver - and as far as Im aware darknoobs script sets up bcm43xx.  When you get back tommorrow, I give you some instructions.

---

### Post by noob12 on 2007-09-04
The script on that thread looks at your device and will either set up bcm43xx or ndiswrapper.

---

### Post by McDorian on 2007-09-05
kevdog,

I just tried a manual install of ndiswrapper and things seem to be working. 

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
and I can ping the wireless router through wlan0, so I guess the connection is working, but my internet connection still seems not to function. I'll try messing about a bit more to see if I can get it going. 

Thanks for your help, you got me back on the right track when I had no idea what to do.

---

### Post by McDorian on 2007-09-05
Doh .... I just had to disable my Eth0 cable that I was using to sort all this stuff out. Now it works fine, and fast, too.

---

