---
title: "Belkin USB Wireless Stick F5D7051"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by Tim Hughes on 2008-10-28
Hi all,

Firstly, I am completely new to Linux so please go easy on me!

I managed to get Ubuntu installed on my machine and was really chuffed with myself :)

Unfortunately I have no idea how to install new software etc, I know it is something to do with the terminal thing but I have no idea about commands etc.

The main thing I would like to do is to get my wireless USB stick (above) working so I can access the internet. Ubuntu does not automatically recognise it and it seems to have no power, no lights etc.

Does anyone have a dummies guide in how to install software and then install my USB Stick so I can connect to the internet? 

My USB Stick is a BELKIN F5D7051.

I really hope someone can help because I want to really get stuck in to this new OS and to learn Linux!

Cheers

---

### Post by pytheas22 on 2008-10-28
Please open a terminal (Applications>Accessories>Terminal), run the following commands and post the output here:
```

lsusb
lshw -C Network
```

(to copy terminal text, highlight it, right-click and select 'copy')

That will help to figure out how to get your card working.  Installing hardware drivers in Ubuntu is actually sort of a specialized process (and one that you usually don't need to worry about, as the Linux kernel comes with drivers built in for most hardware, although your wireless card is an exception).  But for normal software, you usually install using Synaptic or Add/Remove Programs; take a look [here]("http://psychocats.net/ubuntu/installingsoftware") for more information.  But again, you won't be able to install wireless drivers that way.

---

### Post by Tim Hughes on 2008-10-29
Thanks for the speedy reply :)

I am currently at work, so as soon as I am home I will complete the above and post the results here.

Can't wait to get ubuntu working properly... woo hoo!

Once again, thanks very much.

---

### Post by Tim Hughes on 2008-10-30
Hey,

Here is the result of the command from the terminal.

I am guessing this lists all devices that are attched to my PC? When I try to run this command with the wireless stick in, nothing happens, take it out and the command works fine!

lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 116f:c108 Silicon 10 Technology Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 043d:007b Lexmark International, Inc. 
Bus 001 Device 005: ID 043d:007c Lexmark International, Inc. 
Bus 001 Device 004: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 003: ID 043d:007a Lexmark International, Inc. 
Bus 001 Device 001: ID 0000:0000  
tim@Home:~$ lshw -cnetwork
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

Hope this is what you were looking for.

Many Thanks :)

---

### Post by james_vanb on 2008-10-30
Not sure what you've tried, but I have Belkin Wireless G USB F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin F5D7050, v. 3000 with rt73 driver. Install has been the same using ndiswrapper and the Belkin install cd as follows:  (This process should also work for your USB)

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

Give it a shot.

---

### Post by pytheas22 on 2008-10-30
Tim Hughes: the instructions in the post above should work if your card has a Ralink rt73 chipset.  It's impossible to know for sure which chipset you have, however, without seeing the output of 'lsusb' when your card is plugged in.  You say that when you ran that command with the card plugged in, nothing happened?  That's really strange.  Did it just return you to the command prompt without printing anything out?

Maybe things would work better if you reboot your computer, then plug the wireless card into a USB port that you know works.  Then run these commands and post the output:
```

lsusb
lshw -C Network
lsmod
```

Note that the C in 'lshw -C Network' is capitalized (case matters in the Unix world!), and that there's a space between '-C' and 'Network'.  When you typed the command before, it didn't print out the information I was looking for because of these problems.

You say that your card is called F5D7051, while james' is F5D7050, so I'd be hesitant to assume that they necessarily both contain the same chipsets.

---

### Post by Tim Hughes on 2008-10-31
Right!

I am CONNECTED!!!

I upgraded to 8.10 and this fixed everything. They must have added the driver to the default drivers list.

I can't thank you both enough for all your help.

Here's to a problem fre life with Ubuntu!

---

### Post by Resarcio on 2008-11-04
Hi guys, I was wondering if you could help me out a bit? I have the exact same problem as Tim had, only I have Ubuntu 8.10 installed and I still cant get it to work... whenever i try to type ```
lsusb
``` nothing happens, unless I unplug the usb device, then it instanty gives the information about my usb ports... Any clue on how I might get it to recognize my device ?

---

### Post by pytheas22 on 2008-11-04
Resarcio: so when the device is plugged in and you type 'lsusb' it doesn't mention it anywhere?  Have you tried all of your different USB ports?  If so, it could be a hardware problem.

If you plug the device in (and keep it in), then immediately run the commands:
```

dmesg | tail
lsusb
```

what is the output?

---

### Post by Resarcio on 2008-11-04
Geez this forum is just hellbend on not wanting to let me log in ... 

Anyways, first attempt :
```
draug@draug:~$ dmesg | tail
[   46.596275] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.596305] Bluetooth: BNEP filters: protocol multicast
[   46.690942] Bridge firewalling registered
[   46.693930] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   46.736836] Bluetooth: SCO (Voice Link) ver 0.6
[   46.736856] Bluetooth: SCO socket layer initialized
[   50.933038] eth0: link down
[  123.729264] hub 1-0:1.0: unable to enumerate USB device on port 1
[  124.036122] usb 1-1: new full speed USB device using ohci_hcd and address 3
[  124.289884] usb 1-1: configuration #1 chosen from 1 choice
draug@draug:~$ lsusb
```

Second attempt where I removed usb wireless after approx 5 sec of inactivity
```
draug@draug:~$ dmesg | tail
[  410.042855] usbcore: registered new interface driver cdc_ether
[  410.292322] usbcore: registered new interface driver rndis_host
[  410.382679] usbcore: registered new interface driver rndis_wlan
[  410.603079] ppdev0: registered pardevice
[  411.092779] ppdev0: unregistered pardevice
[  412.992398] ppdev0: registered pardevice
[  413.128896] ppdev0: unregistered pardevice
[  425.772124] hub 1-0:1.0: unable to enumerate USB device on port 1
[  426.077231] usb 1-1: new full speed USB device using ohci_hcd and address 5
[  426.351343] usb 1-1: configuration #1 chosen from 1 choice
draug@draug:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
draug@draug:~$  
```

So the lsusb only replies when I remove usb device... and yes all my ports work properly, I tested them with a usb key and it found it immediately.. Hope this helps... and thx for the fast reply btw :)

---

### Post by pytheas22 on 2008-11-04
So when you type 'lsusb' with the device inserted, you get no output at all?  That's very strange.

The bit in dmesg about being "unable to enumerate USB device" is interesting.  I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256767") which seems to be related to the issue.  It seems to have been introduced in Intrepid.  Unfortunately there's no clear answer there, but at least they're aware of it.

It may help to run this command before plugging the device in:
```

sudo modprobe -r ehci_hcd
```

then plug the stick in; does it help?

I think that your problem ultimately has to do with your USB drivers, not your wireless card.  Have you had any other trouble with USB devices since upgrading to Intrepid?

---

### Post by Resarcio on 2008-11-04
First of all, I'm brand new to Ubuntu so havent really toyed around that much... I also plugged in my Ethernet cable between the 2 runs of previous commands, thats why they might look a bit wierd... 

sry, it didnt help either... just wondering why I would have troubles with the drivers when OP's device started working after he installed 8.10 ? 

Got any pointers on how to upgrade / install the correct drivers in that case ?

---

### Post by pytheas22 on 2008-11-05
> just wondering why I would have troubles with the drivers when OP's device started working after he installed 8.10 ?

Got any pointers on how to upgrade / install the correct drivers in that case ? 

I really think the problem has to do with your USB hub, not the wireless card itself--hence why the original poster's card works fine but not yours (he or she probably has a different motherboard with different USB hubs).  Do you know the make and model of your motherboard?  And what is the total output of:
```

lspci
lshw
```

---

### Post by Resarcio on 2008-11-05
Its a old laptop I'm installing it on so I have no clue of what make or model the motherboard is :) 

But since the system keeps locking down at odd times, I have decided to postpone my unix experience untill my desktop grows old enough to be replaced and fire it up on that one :)

I thank you for your fast reply's and the effort you put into it..

See you out there...

---

### Post by pytheas22 on 2008-11-05
With the output of 'lshw' and 'lspci -nn' it might be possible to figure out the problem even without knowing the motherboard, although it may not be easy, so I understand if you want to give up on it for now.  I do hope you'll come back when you're ready to try Ubuntu on your desktop (or consider dual-booting now...you can install Ubuntu very easily using [wubi]("http://wubi-installer.org/") without even having to partition).

---

### Post by Resarcio on 2008-11-05
Sweet! :D will install it on my desktop straight away, and return with a whole new world of problems :p

Thanks alot mate.

---

### Post by oli1997 on 2008-12-28
hi my names oli, am im a noob.    now with my belkin 54g usb "stick drivers rt2500usb" i was wondering how to get it to have a better connection and to get it to flash like it does on windows xp my dad already did this for his but his is a pci card not usb so i need help       



p.s im running ubuntu 8.10

---

### Post by pytheas22 on 2008-12-28
oli1997: does your card work at all?  Can you connect to networks but have problems thereafter?  If so, please describe more specifically what happens.

The lights on the adapter should also be on if it's working, I would think, although they may not behave the same as they do in Windows.  Are there any lights working at all under Ubuntu?

Also, please plug the card in, open up a terminal, run the following command and post the output:
```

lsusb
```

---

### Post by oli1997 on 2008-12-29
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0930:6545 Toshiba Corp. 
Bus 001 Device 005: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



kk here are the things you asked for.   but on windows the stick flashes when i download or brows but in ubuntu it doesn't i think its rather odd

---

### Post by pytheas22 on 2008-12-29
oli1997: I researched your problem a bit.  There are probably some things that we could do to get the light to turn on, but it would involve a substantial amount of work.  Unless seeing the light is really important to you, I'd recommend that you just leave well-enough alone, since from what you say it sounds like the device gets you connected to the Internet without a problem, you just don't see any lights.

If you want to see notifications when there's network activity, you could always add the 'Network Monitor' applet to the Gnome panel by right-clicking the panel and selecting 'add to panel'.

That said, if you really want to try to make the light work, let me know and I'll give you instructions on what to try.

---

### Post by oli1997 on 2008-12-30
my dad said he's getting a new router so i think i'll wait and see if it doesn't fasten up the Internet if not then yea ill give it a go 

p.s i'll let you know if it does or doesn't (sorry 4 the hassle)

---

### Post by taffyviking on 2008-12-30
Thanks to James_vanb for his concise and easy to read post.  I've been trying to get my ralink rt73 based Gigabyte GN-WB01GS USB wireless stick working for weeks now, and everything I've read has been incomprehensible, but finally I have the wretched thing connected thanks to you!

---

### Post by james_vanb on 2009-01-01
Glad it worked for you.

Happy New Year!!

---

### Post by oli1997 on 2009-01-03
my internet doesn't seem to be faster so can you tell me what to do to tune it up 


thanxs oliver:D

---

### Post by pytheas22 on 2009-01-03
> my internet doesn't seem to be faster so can you tell me what to do to tune it up


oliver: sure, I'll give you instructions for getting the card working under ndiswrapper.  But first I just need to know a little more information.  Could you please post the output of these commands:
```

lshw -C Network
uname -rm
lsmod | grep rt
```

---

### Post by oli1997 on 2009-01-04
oliver@oliver-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:16:17:75:e6:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:c2:f8:f2:cf:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:11:50:46:7f:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11bg
oliver@oliver-desktop:~$ uname -rm
2.6.27-9-generic i686
oliver@oliver-desktop:~$ lsmod | grep rt
gameport               19468  1 snd_via82xx
rt73usb                30464  0 
crc_itu_t              10112  2 udf,rt73usb
snd_mpu401_uart        15360  1 snd_via82xx
rt2500usb              27904  0 
rt2x00usb              18816  2 rt73usb,rt2500usb
rt2x00lib              36224  3 rt73usb,rt2500usb,rt2x00usb
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  4 p54usb,p54common,rt2x00usb,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd                    63268  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
agpgart                42184  2 drm,via_agp
usbcore               148848  8 p54usb,rt73usb,rt2500usb,rt2x00usb,usbhid,uhci_h

---

### Post by pytheas22 on 2009-01-04
Oliver: thanks for that information.  Please run these commands to get your card working using ndiswrapper (you will need to have an Internet connection for these commands to work):
```

mkdir wifi
cd wifi
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://burnthesorbonne.com/files/050d_7050_win32.tar.gz
tar -xzvf 050d*
sudo ndiswrapper -i BLKWGU.inf
sudo -s
sudo modprobe -r rt73usb rt2x00usb rt2500usb rt2x00lib
echo ndiswrapper | sudo tee -a /etc/modules
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
lshw -C Network
lsmod | grep rt
ndiswrapper -l
```

Please post all the output from the commands above so that I can make sure they complete successfully.

At this point, your card should be working under ndiswrapper and will hopefully provide a better connection that it did before (if it doesn't work and you've lost your Internet connection completely, just reboot your computer and it should come back).  However, if you reboot your computer, you will default back to your current configuration.  Once we determine that ndiswrapper works, we can make the change permanent so that it will always be used; but I don't want to make permanent changes until we know that ndiswrapper will solve your problem.

---

### Post by oli1997 on 2009-01-05
oliver@oliver-desktop:~$ mkdir wifi
oliver@oliver-desktop:~$ cd wifi
oliver@oliver-desktop:~/wifi$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for oliver: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  evolution-common evolution-webcal linux-headers-2.6.27-7
  linux-headers-2.6.27-7-generic libsnack2 amsn-data tcl8.5 tk8.5 tcl-tls
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.4kB of archives.
After this operation, 225kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main ndiswrapper-common 1.52-1ubuntu1 [20.2kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.1kB]
Fetched 55.4kB in 0s (173kB/s)             
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 127390 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.52-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.52-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ 
oliver@oliver-desktop:~/wifi$ wget [http://burnthesorbonne.com/files/050d_7050_win32.tar.gz](http://burnthesorbonne.com/files/050d_7050_win32.tar.gz)
--2009-01-05 17:26:19--  [http://burnthesorbonne.com/files/050d_7050_win32.tar.gz](http://burnthesorbonne.com/files/050d_7050_win32.tar.gz)
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139472 (136K) [application/x-gzip]
Saving to: `050d_7050_win32.tar.gz'

100%[======================================>] 139,472      127K/s   in 1.1s    

2009-01-05 17:26:20 (127 KB/s) - `050d_7050_win32.tar.gz' saved [139472/139472]

oliver@oliver-desktop:~/wifi$ tar -xzvf 050d*
blkwgu.cat
BLKWGU.inf
BLKWGU.sys
oliver@oliver-desktop:~/wifi$ sudo ndiswrapper -i BLKWGU.inf
installing blkwgu ...
oliver@oliver-desktop:~/wifi$ sudo -s
root@oliver-desktop:~/wifi# sudo modprobe -r rt73usb rt2x00usb rt2500usb rt2x00lib
FATAL: Module rt2x00usb is in use.
root@oliver-desktop:~/wifi# echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
root@oliver-desktop:~/wifi# sudo modprobe ndiswrapper
root@oliver-desktop:~/wifi# dmesg | grep -e ndis -e wlan
[   71.807422] wlan0: authenticate with AP 00:30:f1:ff:98:38
[   71.838612] wlan0: authenticated
[   71.838630] wlan0: associate with AP 00:30:f1:ff:98:38
[   71.846990] wlan0: RX AssocResp from 00:30:f1:ff:98:38 (capab=0x431 status=0 aid=1)
[   71.847013] wlan0: associated
[   84.592012] wlan0: no IPv6 routers present
[  261.473660] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  261.518346] usbcore: registered new interface driver ndiswrapper
root@oliver-desktop:~/wifi# lshw -C Network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:16:17:75:e6:7c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:46:7f:e1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.2 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5e:23:83:2f:c3:46
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@oliver-desktop:~/wifi# lsmod | grep rt
gameport               19468  1 snd_via82xx
snd_mpu401_uart        15360  1 snd_via82xx
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
snd                    63268  17 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2500usb              27904  0 
rt2x00usb              18816  1 rt2500usb
rt2x00lib              36224  2 rt2500usb,rt2x00usb
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  4 p54usb,p54common,rt2x00usb,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
agpgart                42184  2 drm,via_agp
usbcore               148848  10 ndiswrapper,p54usb,rt2500usb,rt2x00usb,usb_storage,libusual,usbhid,uhci_hcd,ehci_hcd
root@oliver-desktop:~/wifi# ndiswrapper -l
blkwgu : driver installed

---

### Post by pytheas22 on 2009-01-05
Oliver: it looks like everything went smoothly, but the Windows driver that I had you install was not the correct one--I assumed it was but didn't double-check.  However, I've spent a few minutes now trying to find the right Windows driver and am not having luck.  Could you provide a link to the driver that you used to install your wireless card in Windows?  If the driver came on a CD, could you upload the .exe or .zip file here please?  I'm sorry to have to ask you to do this, but I'm googled quite a bit for 'f5d7051 driver' and have not turned up anything containing the right files.

---

### Post by theDaveTheRave on 2009-01-06
Pytheas22

I must say you are doing a grand job here,

I had an old version of the belkin f5d7051 USB stick working on Gibbon. I don't have the CD with me at the moment, and having just moved house it could be anywhere! but I seem to recall that if you head to the belkin web site they have all the driver downloads that you are talking about.

good luck and keep up the good work

David

---

### Post by pytheas22 on 2009-01-06
Thanks David.  I did find [this page]("http://www.belkin.com/support/article/?lid=en&pid=F5D7051&aid=6070&scid=221") on the Belkin site, but the only .inf file that I could extract from the driver there was for a Broadcom chipset.  Oliver's device is Ralink-based according to everything I read, and the ID numbers in the Broadcom .inf file don't match his PCI ID.  I'll keep looking, however, and if you happen to find that driver CD, please see if you can get a .exe or .zip uploaded here!

---

### Post by theDaveTheRave on 2009-01-07
pythaes22

I've just found this other thread [here ]("http://ubuntuforums.org/showthread.php?t=225206") by javajake that I used originally to get my usb stick to work.

He may have other links to other chipsets also.

its a nuisance that the OP isn't able to use lsusb to find the details of the stick.

I'm guessing that lshw and iwconfig or ifconfig won't work either?

I find this a bit of a surprise, and is one of the things I really like about linux compared to windows, the ability to find all this extra hardware info that can be so useful.



David

---

### Post by pytheas22 on 2009-01-07
David: thanks for that link.  Unfortunately I still can't find any Windows drivers containing the right files for Oliver's card.  The problem isn't getting the lsusb information--we have that--it's finding a Windows driver that matches the information given by lsusb.  I've tried a dozen different Windows packages, but none contains the right file.  I think the confusion is due partially to the fact that Belkin has sold a number of different devices under the F5d705x name.

I did remember, however, that the [rt2x00 legacy drivers]("http://rt2x00.serialmonkey.com/wiki/index.php/Downloads") may help in this situation.  So instead of ndiswrapper, let's give those a try.  Oliver, please run these commands:
```

sudo apt-get install rutilt build-essential
wget http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz
tar -xzvf rt73*
cd rt73*/Module
make
sudo make install
echo rt73 | sudo tee -a /etc/modules
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
```

Then reboot.  After rebooting, go to System>Administration>Rutilt WLAN Manager and use this utility to connect (you can't use Network Manager).  Does this solve the problem?

---

### Post by BooksDK on 2009-01-19
Believe you should be able to find the files in this thread:
[http://ubuntuforums.org/showthread.php?p=2175921](http://ubuntuforums.org/showthread.php?p=2175921)

---

### Post by BooksDK on 2009-01-19
Sorry, guess I was a little too fast with my first reply. Didn't see that you believe the F5D7051 is based on the Ralink chipset and not Broadcom chipset.

I think that you will find that Belkin F5D7051 is based on Broadcom chipset, but that linux mistakenly takes it for a Ralink chipset (one of the major hassles with this device).

Try to check out this guide:
[http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/](http://thehardsell.wordpress.com/2007/11/08/kubuntu-and-the-belkin-f5d7051-a-saga/)

Cheers

---

### Post by theDaveTheRave on 2009-01-23
Hello again all

Well I've done some searching through the stuff post house move and I thought I should mention that as of this moment in time the CD that I had seems to have "gone missing".

I'm sure that it is around somewhere, but the current state of partially empty boxes with stuff in, and attempting to get an internet connection from home etc etc etc..are conspiring against the available time to have a really good search for the disk.

It will however turn up eventually.... even better once I get the old desktop going the files will no douubt be on the windows partition, if I haven't deleted them (and of course on the ubuntu partition)!

questions is, it is such a long time since I played with this type of stuff (hard wired connection and current wifi laptop work "out of the box") I'm not sure where I would have placed the files!

so if you still require them drop a note to the forum and tell me where the files "should" be!

Sorry to have not been particularly helpfull.... again!

David

---

### Post by pytheas22 on 2009-01-23
> so if you still require them drop a note to the forum and tell me where the files "should" be!

I'm not sure if this issue is still a concern for oli1997; if not then there's no reason to find those files.  I am still curious as to why I couldn't find the right Windows driver for this device anywhere, but that's not a big deal.  Maybe it is really a Broadcom chipset, but that seems very unlikely to me...

---

### Post by Post Monkeh on 2009-01-27
sorry to butt in on the thread, but since there seems to be a few fairly linux-wise folk in here i thought i'd ask a little question

i'm also having a bit of a problem with the belkin wireless g (050d:705e is the device code when i lsusb it)

however, the device isn't actually installed. when i do an lshw, it doesn't appear.  i think if i could get it as far as having the wrong driver installed i could get it working with the help of the numerous other threads dotted around the place, but i haven't seen anyone with exactly the same fault as mine.

incidentally, i have a wireless usb keyboard/mouse that works fine, a usb bluetooth doongle that works fine, and i've tried the wireless adapter in several different usb ports without success (though i can always lsusb it)

another thing, i don't know if it's important, but if i lsusb, then remove the adapter and put it back in the same usb port, it comes back with a totally different buss/device number.

---

### Post by Post Monkeh on 2009-01-27
ooh, i found [http://linuxsoftwareblog.com/blog/?p=30]("http://linuxsoftwareblog.com/blog/?p=30") this.

currently downloading the updates, fingers crossed.

---

### Post by Post Monkeh on 2009-01-27
ok, i dunno if my wireless adapter worked because my video card was screwed lol

---

### Post by pytheas22 on 2009-01-27
> ok, i dunno if my wireless adapter worked because my video card was screwed lol

What happened to your video exactly?  Can you no longer log in?

The tutorial that you followed had you enable the intrepid-proposed repository, which contains non-stable software; this is likely what broke your video.

You could try booting into an older kernel to get your screen back.  To do that, you would want to select one of the kernels towards the bottom of the list at the grub boot screen, which is the screen you see shortly after turning on your computer, after BIOS finishes but before Ubuntu starts loading (with the orange bar).  You may need to press 'escape' to get into grub; if so, you should see a message on your screen that says something like 'Press escape now to enter boot menu'.

If an older kernel works, we can try to make your card work in ndiswrapper using it.

If an older kernel doesn't work, then your system is probably badly broken and you might want to consider reinstalling, then coming back here so we can make your wireless work.

You could also try applying the updates again to see if that will fix your system--the packages in intrepid-proposed are updated rapidly, and within a few days they might make your computer work again.  To apply updates without being able to log in graphically, you would do this:

1. plug your computer into ethernet
2. once Ubuntu finishes loading, press control-alt-F2.  This brings you to a command prompt.
3. log in on the command prompt, then run these commands:
```

sudo ifconfig eth0 up #bring up ethernet interface
sudo dhclient eth0 #request IP address
sudo apt-get update #update software package list
sudo apt-get upgrade #download and install updates
```

Then reboot by typing:
```

sudo reboot
```

and see if your video and/or wireless work again.

---

### Post by Post Monkeh on 2009-01-28
thanks for the reply.

i got it working again, i posted that message last night from it.  yeah, i just immediately rebooted to the 27-9 kernel and removed the 27-11 one from my grub boot list for the time being. the screen was basically comprised of various multi coloured ubuntu symbols and would not even let me into a terminal using alt & f1-f6.  think i'll wait a while before i try anymore unsupported kernels, i have to say though, i love how linux lets you go back to your previous settings, when i stuff windows up it's usually a lot harder to fix :D.

i have tried before (and failed miserably might i add) to use ndiswrapper) the computer basically would not load up after i used it, but then i may have been installing a few things at the same time like the proprietary driver for my ati hd3850 video card that i found out last night didn't work quite right either.  i got it sorted by downloading the latest one from the amdati website.  it may well have been the fact that the new kernal was trying to use a different version of that driver that screwed up my screen, but that's besides the point.

i'm not at home tonight, posting this from my laptop, but if i get a chance tomorrow night i might give ndiswrapper another try, i think i could manage to uninstall it now using the recovery terminal if it buggers anything up.

before, i got as far as actually installing the blkwgu (think that was it) driver from my cd by installing wine, installing the cd then copying the inf file from there.  once i tried to reload the pc though it just refused to do anything, the whole system lagged, but i'm not sure if at that point ubuntu was maybe trying to use 2 drivers for my adapter.
the problem now seems to be that it isn't trying to use any.

i'll give it another blast tomorrow, cheers

---

### Post by Post Monkeh on 2009-01-28
lol just noticed the 27-11 kernel is now available as a supported update. i think i'll take the ati driver out before i update again on the main pc.

---

### Post by pytheas22 on 2009-01-28
> lol just noticed the 27-11 kernel is now available as a supported update. i think i'll take the ati driver out before i update again on the main pc.

Yes, I have 2.6.27-11 in updates today as well (and I don't have the testing repositories enabled).  I would install that and see if it makes your card work.  According to what I read, the rtl8187 driver in this latest kernel should support your card out-of-the-box, abrogating the need for all the ndiswrapper nonsense.

If, after installing the new kernel and rebooting, your wireless still seems not to work, make sure that the rtl8187 driver is inserted and that ndsiwrapper is not by typing:
```

sudo modprobe -r ndiswrapper
sudo modprobe rtl8187
```

If that still fails, please post the output of:
```

dmesg | grep -e wlan -e rtl
lsmod | grep rtl
lshw -C Network
sudo iwlist scan
```

---

### Post by Post Monkeh on 2009-01-29
strange.  i managed to get round the video card problem by uninstalling it and going through an xorg & package repair.

adapter was recognised and i got connected to my network but i can't access the internet.  can't ping my router ip either, although when i disconnect then reconnect the connection, i can ping 2, sometimes 3 packets, then i get a destination host unreachable.

will get the cable back in and post the results of those commands

---

### Post by Post Monkeh on 2009-01-29
```
will@will-desktop:~$ dmesg | grep -e wlan -e rtl
[   12.063600] rtl8187: 8187B chip detected. Support is EXPERIMENTAL, and could damage your
[   12.499016] phy0: hwaddr 00:1c:df:37:ce:4b, RTL8187BvE V0 + rtl8225z2
[   12.499049] usbcore: registered new interface driver rtl8187
[   40.563632] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   61.817264] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   62.016021] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   62.216024] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   62.416020] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[   74.617278] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   74.785278] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   74.984015] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   75.184017] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   75.384018] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[   87.405294] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   87.573296] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   87.772013] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   87.972016] wlan0: authenticate with AP 00:21:63:7a:66:f1
[   88.172015] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  100.021309] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  100.349310] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  100.548010] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  100.748016] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  100.948011] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  112.977203] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  113.305203] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  113.504016] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  113.704013] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  113.904016] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  124.149326] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  124.337328] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  124.536020] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  124.736021] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  124.936011] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  136.765215] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  137.093216] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  137.292015] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  137.492017] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  137.692012] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  149.717232] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  150.045233] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  150.244047] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  150.444014] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  150.644012] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  162.857249] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  163.021250] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  163.220017] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  163.420011] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  163.620010] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  175.657268] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  175.856020] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  176.056014] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  176.256020] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  196.437246] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  196.601248] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  196.805017] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  197.004015] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  197.204020] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  209.057261] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  209.389262] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  209.588015] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  209.788018] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  209.988011] wlan0: authentication with AP 00:21:63:7a:66:f1 timed out
[  222.009279] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  222.337279] wlan0: authenticate with AP 00:21:63:7a:66:f1
[  222.337294] wlan0: authenticated
[  222.337298] wlan0: associate with AP 00:21:63:7a:66:f1
[  222.343414] wlan0: RX AssocResp from 00:21:63:7a:66:f1 (capab=0x411 status=0 aid=1)
[  222.343421] wlan0: associated
[  222.343857] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  233.284006] wlan0: no IPv6 routers present
will@will-desktop:~$
```




```
will@will-desktop:~$ lsmod | grep rtl
rtl8187                53248  0 
mac80211              216820  1 rtl8187
eeprom_93cx6           10240  1 rtl8187
cfg80211               32392  2 rtl8187,mac80211
usbcore               149360  6 rtl8187,btusb,usbhid,ehci_hcd,uhci_hcd
will@will-desktop:~$ 

```


```
will@will-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:61:fe:60
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 module=atl1 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:37:ce:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.22 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:a0:95:67:c5:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
will@will-desktop:~$ sudo lshw -C network
[sudo] password for will: 
  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:61:fe:60
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 link=no module=atl1 multicast=yes port=twisted pair
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:37:ce:4b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.22 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0e:a0:95:67:c5:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
will@will-desktop:~$ 
```



```
will@will-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1F:9F:4E:1C:C5
                    ESSID:"BTHomeHub-02AA"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/100  Signal level:-55 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000319dc37a9a1
                    Extra: Last beacon: 2332ms ago
          Cell 02 - Address: 00:1B:2F:45:C4:48
                    ESSID:"SKY05519"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/100  Signal level:-41 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000027ee26c86
                    Extra: Last beacon: 2332ms ago
          Cell 03 - Address: 00:21:63:7A:66:F1
                    ESSID:"the oval"
                    Mode:Master
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=66/100  Signal level:-38 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000004414e2ac
                    Extra: Last beacon: 580ms ago

pan0      Interface doesn't support scanning.

will@will-desktop:~$ 
```

they were all with my wireless adapter connected to my network (the oval) and the ethernet cable unplugged.

my ethernet stops working when my wireless is connected too, btw.

---

### Post by pytheas22 on 2009-01-29
hmmm, it looks like the rtl8187 driver might have some association issues.  Could you please connect wirelessly and post the output of these commands:
```

cat /etc/resolv.conf
ping -c 10 google.com
ping -c 10 74.125.67.100
time wget google.com
```

Also, if possible, it may be worth it to turn off security on your router just to see if that makes a difference.  Which network is yours, by the way?

---

### Post by Post Monkeh on 2009-01-29
```
will@will-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
will@will-desktop:~$ ping -c 10 google.com
ping: unknown host google.com
will@will-desktop:~$ ping -c 10 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
From 192.168.0.22 icmp_seq=1 Destination Host Unreachable
From 192.168.0.22 icmp_seq=2 Destination Host Unreachable
From 192.168.0.22 icmp_seq=3 Destination Host Unreachable
From 192.168.0.22 icmp_seq=5 Destination Host Unreachable
From 192.168.0.22 icmp_seq=6 Destination Host Unreachable
From 192.168.0.22 icmp_seq=7 Destination Host Unreachable
From 192.168.0.22 icmp_seq=8 Destination Host Unreachable
From 192.168.0.22 icmp_seq=9 Destination Host Unreachable
From 192.168.0.22 icmp_seq=10 Destination Host Unreachable

--- 74.125.67.100 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9021ms
, pipe 3
will@will-desktop:~$ time wget google.com
--2009-01-29 17:52:44--  http://google.com/
Resolving google.com... failed: Name or service not known.
wget: unable to resolve host address `google.com'

real	0m20.060s
user	0m0.000s
sys	0m0.004s
will@will-desktop:~$ 
```

i'm connected to the oval.

couldn't connect without encryption, i couldn't leave it off too long because the rest of the house were using the network too, but it just wouldn't connect.

---

### Post by pytheas22 on 2009-01-29
That's strange.  What happens if you try to ping your router:
```

ping -c 10 192.168.0.1
```

Also, does your connectivity improve if you run these commands:

```
sudo dhclient -r eth0
sudo ifconfig eth0 down
```

before connecting?

---

### Post by Post Monkeh on 2009-01-29
like i said, if i ping my router, i get a host unreachable message. if i disconnect/reconnect the wireless, i can ping maybe 3 packets then it starts dropping.


btw, i got this

```
will@will-desktop:~$ ping -c 10 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.

--- 74.125.67.100 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9013ms

will@will-desktop:~$ sudo ifconfig eth0 up
[sudo] password for will: 
will@will-desktop:~$ ping -c 10 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
64 bytes from 74.125.67.100: icmp_seq=1 ttl=238 time=144 ms
64 bytes from 74.125.67.100: icmp_seq=2 ttl=238 time=131 ms
64 bytes from 74.125.67.100: icmp_seq=3 ttl=238 time=130 ms
64 bytes from 74.125.67.100: icmp_seq=4 ttl=238 time=142 ms
64 bytes from 74.125.67.100: icmp_seq=5 ttl=238 time=134 ms
64 bytes from 74.125.67.100: icmp_seq=6 ttl=238 time=135 ms
64 bytes from 74.125.67.100: icmp_seq=7 ttl=238 time=132 ms
64 bytes from 74.125.67.100: icmp_seq=8 ttl=238 time=129 ms
64 bytes from 74.125.67.100: icmp_seq=9 ttl=238 time=133 ms
64 bytes from 74.125.67.100: icmp_seq=10 ttl=238 time=129 ms

--- 74.125.67.100 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9042ms
rtt min/avg/max/mdev = 129.989/134.424/144.396/4.863 ms
will@will-desktop:~$ ping -c 10 74.125.67.100
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
64 bytes from 74.125.67.100: icmp_seq=1 ttl=238 time=131 ms
64 bytes from 74.125.67.100: icmp_seq=2 ttl=238 time=129 ms
64 bytes from 74.125.67.100: icmp_seq=3 ttl=238 time=135 ms
64 bytes from 74.125.67.100: icmp_seq=4 ttl=238 time=129 ms
64 bytes from 74.125.67.100: icmp_seq=5 ttl=238 time=130 ms
64 bytes from 74.125.67.100: icmp_seq=6 ttl=238 time=136 ms
64 bytes from 74.125.67.100: icmp_seq=7 ttl=238 time=130 ms
64 bytes from 74.125.67.100: icmp_seq=8 ttl=238 time=130 ms
64 bytes from 74.125.67.100: icmp_seq=9 ttl=238 time=130 ms
64 bytes from 74.125.67.100: icmp_seq=10 ttl=238 time=130 ms

--- 74.125.67.100 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9047ms
rtt min/avg/max/mdev = 129.392/131.647/136.675/2.431 ms
will@will-desktop:~$ 

```

when i tried it after connecting my cable and BEFORE switching off my wireless.

i still couldn't ping my router.

---

### Post by Post Monkeh on 2009-01-29
i'm thinking it must be something to do with my settings.

i have my ip addresses configured manually, they should work, but it seems it isn't getting its dns properly to me.

---

### Post by Post Monkeh on 2009-01-29
ahh, of course, i had my network cable connected.  but that explains why that won't work.

i'll give my settings to you in case they're messing with each other.

eth0
ip 192.168.1.2
sub 255.255.255.0
gateway 192.168.1.1
dns 192.168.0.1
wlan0
ip 192.168.0.2 (also tried 22 instead of 2 in case i'd set anything else as 2)
sub 255.255.255.0
gateway/dns 192.168.0.1

---

### Post by pytheas22 on 2009-01-29
Are you positive that everything is configured properly on your router's end to grant an IP of 192.168.0.22 to your wireless card?  Note that you may need to specify the wireless card's MAC address, not just its hostname, if you're not already doing so.

I also notice in your last post that eth0's gateway is set to 192.168.1.1, but its DNS is 192.168.0.1.  wlan0, in contrast, is using 192.168.0.1 for both gateway and DNS.  Maybe this was just a typo in your post, but if not, did you specify the wrong gateway for wlan0?  Which devices are at 192.168.0.1 and 192.168.1.1, respectively?

Is there a way you could switch to dynamic IP via dhcp just to see what happens there?  Knowing the outcome of that would be useful because there are two possible sources of your problem--1) a misconfiguration with the IP/gateway/DNS settings on wlan0, which is easy to fix; or 2) some problem with the rtl8187 driver, which is more complicated.  If your wireless connection also fails using dynamic IPs, then we would know with relative certainty that this comes down to a driver issue.

---

### Post by Post Monkeh on 2009-01-29
i have always set up my ip addresses manually since i set up my first wireless network nigh on 7 years ago, i've checked and double checked them, i'm certain they're right.

i can't set up dhcp because it would then screw up the other computers connecting to the router, but i'm pretty sure the problem's not with the router settings or my settings on the pc, because when i click my connection in connection manager and it re-initialises, i can ping my router with 3 or 4 (i got up to 5 one time) packets then i get a "destination host unreachable" response.

i downloaded and tried wicd again, it gave me a "not allowed" when i pinged my router.  my router doesn't currently have any ip/mac address filtering.

the reason for the differences in gateway/dns is beause my eth connection isn't connected directly to the router, i set it up to connect through my laptop and they were the only settings that would allow me to access the internet (it's working right now)  just in case, i did try earlier to set the ethernet connection to use dchp to test the wireless.  this obviously had the effect of not allowing my ethernet connection to connect because there was no dhcp server for it to get an ip address from, but it made no difference to my wireless

i also did a modprobe -r rtl8187  followed by a modprobe rtl8187, i got a bit excited because it was after that i got my 5 pings, then it stopped.  dirty prick tease :D

---

### Post by Post Monkeh on 2009-01-29
i also tried it in a different usb port

---

### Post by pytheas22 on 2009-01-29
It does sound like a driver issue then.  The only thing I can think of is to download the latest compat-wireless tarball from [this page]("http://linuxwireless.org/download/compat-wireless-2.6/"), then compile it (it's a pretty straight-forward compilation--just make; make install--but if you need help I'll give specific commands).  Do you have any better luck using the rtl8187 driver built from that source code, rather than the one that comes with Ubuntu (remember to reboot for changes to take effect)?

N.B.: if for some reason these new drivers make things worse, cd back into the compat-wireless directory and run 'sudo make uninstall' to reverse changes.

---

### Post by taronski on 2009-01-30
Hello and apologies for sneaking in this thread.  I am new to Ubuntu and to the etiquette of the forum.

I have followed the instructions from pytheas22 to Olli and I think I am getting somewhere but not all the way.

I have pasted my "progress" 

taron@Beast:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 002: ID 04b8:0849 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
taron@Beast:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth1
       version: 13
       serial: 00:13:d4:9f:8e:21
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:17:3f:b1:b7:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
taron@Beast:~$ uname -rm
2.6.27-11-generic i686
taron@Beast:~$ lsmod | gewp rt
bash: gewp: command not found
taron@Beast:~$ lsmod | grep rt
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
taron@Beast:~$ mkdir wifi
taron@Beast:~$ cd wifi
taron@Beast:~/wifi$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
[sudo] password for taron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
The following packages were automatically installed and are no longer required:
  fakeroot linux-headers-2.6.27-7 nvidia-settings
  linux-headers-2.6.27-7-generic dkms patch
Use 'apt-get autoremove' to remove them.
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  ndiswrapper-utils-1.9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.1kB of archives.
After this operation, 127kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main ndiswrapper-utils-1.9 1.52-1ubuntu1 [35.1kB]
Fetched 35.1kB in 0s (148kB/s)             
debconf: Unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package ndiswrapper-utils-1.9.
(Reading database ... 165908 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.52-1ubuntu1) ...
taron@Beast:~/wifi$ wget [http://burnthesorbonne.com/files/050d_7050_win32.tar.gz--2009-01-30](http://burnthesorbonne.com/files/050d_7050_win32.tar.gz--2009-01-30) 11:37:31--  [http://burnthesorbonne.com/files/050d_7050_win32.tar.gz](http://burnthesorbonne.com/files/050d_7050_win32.tar.gz)
Resolving burnthesorbonne.com... 174.133.198.114
Connecting to burnthesorbonne.com|174.133.198.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 139472 (136K) [application/x-gzip]
Saving to: `050d_7050_win32.tar.gz'

100%[======================================>] 139,472      164K/s   in 0.8s    

2009-01-30 11:37:32 (164 KB/s) - `050d_7050_win32.tar.gz' saved [139472/139472]

taron@Beast:~/wifi$ sudo ndiswrapper -i BLKWGU.inf
couldn't open BLKWGU.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
taron@Beast:~/wifi$ tar -xzvf 050d*
blkwgu.cat
BLKWGU.inf
BLKWGU.sys
taron@Beast:~/wifi$ sudo ndiswrapper -i BLKWGU.inf
installing blkwgu ...
taron@Beast:~/wifi$ sudo -s
root@Beast:~/wifi# sudo modprobe -r rt73usb rt2x00usb rt2500usb rt2x00lib
root@Beast:~/wifi# echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
root@Beast:~/wifi# sudo modprobe ndiswrapper
root@Beast:~/wifi# dmesg | grep -e ndis -e wlan
[   28.149753] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1507.056437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2350.488862] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 2350.522873] usbcore: registered new interface driver ndiswrapper
root@Beast:~/wifi# lshw -C Network
  *-network               
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth1
       version: 13
       serial: 00:13:d4:9f:8e:21
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:b1:b7:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
root@Beast:~/wifi# lsmod | grep rt
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
root@Beast:~/wifi# ndiswrapper -l
blkwgu : driver installed
root@Beast:~/wifi# lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 002: ID 04b8:0849 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Beast:~/wifi# 
root@Beast:~/wifi# sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:4D:F5:2B:E4
                    ESSID:"Bristle"
                    Mode:Master
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=100/100  Signal level:23/100  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000003ad013c3234
                    Extra: Last beacon: 348ms ago


i get to see wifi nets so I am hoping I am almost there. 

Thanks a lot for any help.

Taron

---

### Post by pytheas22 on 2009-01-30
**taronski**: I think that the instructions I gave to Oli regarding ndiswrapper aren't going to work for you, because you have a different version of this wireless card.  However, it looks like Ubuntu already has a driver for your card out-of-the-box, and you can use it to see networks with no problem.

Are you unable to connect to your network or is there some other problem?

Also, it would probably be better if you started a new thread, because this one is already fractured enough.  Please open a new thread, tell me the URL and I'll respond there.

---

### Post by taronski on 2009-01-30
Hi pytheas22,

Got it to work (don't know how!?) thanks for the advice anyway.

Taron

---

### Post by Post Monkeh on 2009-01-30
it lives!

sort of. i'm dropping a lot of packets and the ping response time is very high compared to my laptop for instance. laptop pings at anywhere from 0.5 - 3 ms (normally under 1ms), desktop is currently pinging at around 3 ms, but occasionally it is droping maybe 10 packets in a row.

at least there's some life to it and it's certainly useable for browsing. have to go on a callout now so i can't fiddle with it anymore at the minute, but thanks for all your help.

---

### Post by pytheas22 on 2009-01-30
> it lives!

sort of. i'm dropping a lot of packets and the ping response time is very high compared to my laptop for instance. laptop pings at anywhere from 0.5 - 3 ms (normally under 1ms), desktop is currently pinging at around 3 ms, but occasionally it is droping maybe 10 packets in a row.

at least there's some life to it and it's certainly useable for browsing. have to go on a callout now so i can't fiddle with it anymore at the minute, but thanks for all your help.

Post Monkeh: that's certainly good news, but to be clear (and for the sake of others who read this thread): was it compiling compat-wireless that fixed it?  Or did it suddenly start working better using the stock rtl8187 driver that shipped with the 2.6.27-11 kernel?

If it was compat-wireless that did the trick, you might want to save a copy of the source that made it work more or less for now (so that you can go back to it if necessary), then keep compiling newer versions of compat-wireless every few days to see if they solve the problem more definitively.  My guess is that rtl8187's support for your card will continue to improve rapidly with the rest of compat-wireless over the next few weeks.

---

### Post by Post Monkeh on 2009-01-30
it was compat wireless that did it.

what kinds of things will make it compile differently? any specific updates i should compile after?  or does compiling it actually download new content from the internet, meaning it'll compile differently even if my system hasn't updated itself?

---

### Post by pytheas22 on 2009-01-30
> what kinds of things will make it compile differently? any specific updates i should compile after? or does compiling it actually download new content from the internet, meaning it'll compile differently even if my system hasn't updated itself?

Very frequently, the compat-wireless source code gets modified and a new version is uploaded--if you go to [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) today, for example, you see that the code was last modified at 2009-Jan-30 17:13:29.  I just meant that you should keep trying newer versions of the code, because they may include updates that make your card work better.

But keep your current version of the code on hand just in case an updated version is broken and you need to revert.

---

### Post by Post Monkeh on 2009-01-30
ah right, so you mean i should download their updates.

it seems to have stopped working again for some reason, but i did a modprobe -r rtl8187  & modprobe rtl8187 about half an hour ago when it started happenning so might have stuffed it up myself.  i might try uninstalling compat and reinstalling it

---

### Post by Post Monkeh on 2009-01-30
stopped working altogether there for a while, it just wouldn't connect.

i booted into windows to have some trouble free browsing and found i couldn't connect there either.  removed the device from the usb port and reconnected it, connected to my network straight away.

i rebooted back into ubuntu and bingo, it's working perfectly.  fingers crossed it stays like this.

---

### Post by pytheas22 on 2009-01-31
> i booted into windows to have some trouble free browsing and found i couldn't connect there either. removed the device from the usb port and reconnected it, connected to my network straight away.

Well, that sounds like a flaky wireless card or USB bus (which may have been the source of the packet loss all along, even using the default rtl8387 driver that shipped with the latest kernel), but at least it's working now.  Let's hope it stays that way.

---

### Post by Post Monkeh on 2009-01-31
haven't been able to get it to work today.  it worked perfectly in xp before i switched to ubuntu, and still works perfectly in xp once i get it up and running once, just seems there's something ubuntu's doing to it that's making something go mad.

probably won't be back to my own house til tuesday probably so hopefully compat wireless will have an update that makes it work a little better.  i also wonder if  my wireless mouse/keyboard may be interfering so i'll have to dust off my wired ones and try it.

at least i know it works, just not very well. hopefully it can only get better.

---

### Post by pytheas22 on 2009-01-31
> haven't been able to get it to work today. it worked perfectly in xp before i switched to ubuntu, and still works perfectly in xp once i get it up and running once, just seems there's something ubuntu's doing to it that's making something go mad.

probably won't be back to my own house til tuesday probably so hopefully compat wireless will have an update that makes it work a little better. i also wonder if my wireless mouse/keyboard may be interfering so i'll have to dust off my wired ones and try it.

You should check dmesg to see if there's anything regarding hardware failure or address conflicts that might explain the behavior.  Also, when the device stops working, does it still show up in lsusb?

---

### Post by Post Monkeh on 2009-01-31
didn't check it earlier but i would imagine so - it still appears in my network adapters, and i can see all wireless networks around me and try to connect, but it won't let me (to mine at least)  it just keeps trying and trying.

occasionally i can connect, but it won't let me access the internet or ping my router, and normally disconnects after a short while.

i'm starting to think i may be having problems with my actual network - i couldn't connect properly earlier on my laptop either but i've ended up back home and now both are connecting fine. the only difference is that there's one less system connected to the network, my brother's, and he has a habit of downloading constantly. i'm beginning to wonder if his computer is clogging up the network.

might have a fiddle with the router and see if i can restrict his bandwidth and see if that makes any difference

---

### Post by Post Monkeh on 2009-02-02
quick update.

my adapter is working flawlessly.  except when my brother's laptop is connected.

rather bizarrely, the adapter works 100%, good signal, good transfer rates, no drops,  then as soon as my brother turns his laptop on in his room, it immediately stops working.  it stays connected, but it won't send or receive data.
to compound the mystery, when i bring the laptop into my room to attempt to diagnose the problem, my connection starts working again!  and i've had a pc as long as i can remember and i've never seen anything like this, it doesn't make sense to me.  i set up my first wireless network i think in 2001ish, and had quite a few teething problems before i got the hardware to work for me.  i actually still used my old netgear ma101 until last month when i bought the belkin adapter. i would go back to it but when i try to use it it doesn't let me use wpa.

i'm pretty much stumped. if it was a matter of his signal interfering with mine then surely the closer the devices were to each other the worse it would be. not so. if i have his laptop in my room my connection works perfectly. as soon as it's in his room (maybe 10 m away) my connection just dies.

his room would be slightly closer to the router than mine  - mine would be maybe 15m in a straight line, his would be almost directly above it (the router sits at the front door), so maybe 5m away, but it was never a problem when i used my old netgear adapter.

he has just got a new laptop (dell vostro something or other) but when i think about it now, back last week when i was having all the problems his laptop would have been on pretty much constantly (at that point he was using my dad's old sony vaio)

anyone have any ideas? 

i'm not going to be home for a few days, staying with the mrs until thursday, but i bought her an identical belkin usb adapter, i'm going to take that home with me and try it in case it's just a dodgy device, but even at that it's still strange how the problem is manifesting itself.

---

### Post by pytheas22 on 2009-02-02
Yes, that's quite strange.  The only thing I can think of is that there's possibly an IP address conflict, especially since you're using static IP.  That doesn't really explain why the performance improves when your computer is moved closer to your brother's, but it's the only thing that makes any sense to me.

---

### Post by Post Monkeh on 2009-02-03
i thought that myself, so i've tried various ip addresses on my pc without success.

besides, i set the whole network up myself so there's definitely no conflicts (no dhcp is enabled on the router either)

really is strange.  next port of call is trying the woman's dongle  in my machine (ooo err).  i really hope it works because at least then it's just a faulty device.

by the way, it's my brother's pc being moved closer to mine. might not sound important but my pc has remained static in all this - proving that the signal is ok. it works perfectly until my bro's laptop is switched on. 
i'm going to be moving into my own house within the next couple of months too and i'll have enough to worry about getting the place in shape without my network causing me stress, i just hope it turns out to be something stupid causing the problem.

---

### Post by pytheas22 on 2009-02-03
If you had a lot of time on your hands and wanted to learn about low-level wireless networking, you could run a sniffer like kismet or airodump-ng to see what kind of traffic is in the air when your computer disconnects.  Maybe your brother's machine is triggering deauthentication packets from the router or something strange like that.  You'd probably need to look at the packets in Wireshark to figure out exactly what they're doing.

But again, this would probably be a lot of work for minimal return if you're going to be moving soon anyway.

---

### Post by Post Monkeh on 2009-02-03
i'm a stubborn bar steward though, and i hate being beaten :D

more likely the problem will be that i won't have time, i spend most of my time in the mrs' house atm.

pretty annoying.

doubt i'll get the time to learn a great deal about it this time, which is a pity, would have been a good oportunity to become more of a geek.  oh well, i suppose it'll give me something to do :D

---

### Post by Post Monkeh on 2009-02-05
tried the second belkin adapter in my pc, same result.

tried both adapters in my laptop and they did the same thing, it's obviously some sort of issue with this type of adapter or more likely just the driver, downloaded the latest version of compat wireless and it's still doing the same thing so i'll keep my fingers crossed that the driver gets improved at some stage to fix this problem.

---

### Post by pytheas22 on 2009-02-05
Yes, it's probably the driver then (although the last variable that you'd need to test would be your router--does the same problem occur on a different network?).

If you don't want to wait for compat-wireless to fix the issue (which you may want to [report to them]("http://sourceforge.net/tracker/?group_id=186406")--or to [Ubuntu]("https://help.ubuntu.com/community/ReportingBugs") because I'm not sure if the rtl8187 bug tracker is still active), you could always give ndiswrapper a try...

---

### Post by oli1997 on 2009-02-21
hi pytheas22 i've been playing with ubuntu and finally i did it i reinstalled ubuntu 8.10, and now it seems to flash (i think it might have been beacuse of the driver), but i went into synaptic and typed in "rt2500usb" and there it was there so i installed it, restarted my computer and it was flashing but with a better signal and speed.:D

---

### Post by ukulele_ninja on 2009-03-22
This seems to be the thread to be for the Belkin adapter! I have a 2day old mythbuntu install that im trying to get the adapter working on. Last night I plugged it in and didnt immediatly see that I had to click on the network adapter to switch to wireless signal, so I spent some time running through different how tos and such just to finally realize it was working right from the get go!

So it worked fine last night and this morning, but after a reboot earlier it dissappeared! I assume this is because i mucked around with settings that I shouldnt have. I followed the guide on the first page of this thread and now when I click the network icon I can see 'wireless networks' and below it a greyed message that says 'device is unmanaged'. So I know the system sees it but I cant get it to scan for networks or anything really. Any help would be fantastic!

EDIT: my exact adapter is the Belkin 7050 version 3000

---

### Post by pytheas22 on 2009-03-22
ukulele_ninja: please post the output of these commands to provide a clearer picture of what's going on:
```

lsusb
lshw -C Network
sudo iwlist scan
uname -rm
```

---

### Post by ukulele_ninja on 2009-03-22
Hope you can help me out! Thanks! :)

ryan@ryan-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c01d Logitech, Inc. MX510 Optical Mouse
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 050d:705a Belkin Components F5D7050A Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ryan@ryan-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth0
       version: 10
       serial: 00:01:6c:cc:f5:4f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.141 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:a0:e9:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 96:b5:d0:8a:7f:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ryan@ryan-desktop:~$ sudo iwlist scan
[sudo] password for ryan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:2E:7B:1A
                    ESSID:"linksys1234"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:1C:DF:57:72:07
                    ESSID:"Belkin_G_Plus_MIMO_577207"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 03 - Address: 00:90:4C:7E:00:10
                    ESSID:"NETGEAR S"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 04 - Address: 00:14:BF:31:19:2D
                    ESSID:"dd-wrt"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:148 Mb/s

pan0      Interface doesn't support scanning.

ryan@ryan-desktop:~$ uname -rm
2.6.27-11-generic i686
ryan@ryan-desktop:~$

---

### Post by pytheas22 on 2009-03-23
**ukulele_ninja**: according to this [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417") and [this post]("http://ubuntuforums.org/showthread.php?p=5926426"), it looks like there's just a problem with Network Manager--the wireless card itself is working fine, but the program that Ubuntu uses to manage connections has some misconfiguration.  Please try running these commands to fix it:
```

sudo killall nm-system-settings
sudo /etc/init.d/NetworkManager restart
```

Hopefully that will fix it.  If not, please post the output of this command:
```

cat /etc/NetworkManager/nm-system-settings.conf
```

That will dump out a configuration file, which might need to be changed in order to fix NetworkManager.

---

### Post by ukulele_ninja on 2009-03-23
Thanks man! I will be home from work in about 6 hours so I will let you know how it goes. :)

---

### Post by ukulele_ninja on 2009-03-23
All it seemed to do was reset my wired connection, still nothing from the Belkin. heres the output you requested:

ryan@ryan-desktop:~$ cat /etc/NetworkManager/nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

---

### Post by pytheas22 on 2009-03-23
Sorry that didn't work.  Let's try editing the configuration file.  To do so, first open it by typing:
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Then edit the last line so that it reads:
```

managed=**true**
```

Then save and close the file, and reboot.  Any luck?

---

### Post by ukulele_ninja on 2009-03-23
After a reboot its now detecting my network! Only issue is that its asking for my network passkey but it only gives me the option of WEP encryption and our network uses WPA and thats not an option in the drop down menu

---

### Post by ukulele_ninja on 2009-03-23
Alright I think I got it! Went back and checked the blacklist file and I had two items a previous guide had told me to blacklist. After I took them off, I restarted and it connected! After multiple restarts its staying on. The only complaint I have is that it keeps asking for my keyring password which I asusme I can turn off somehow. Anyway, Thanks for all your help I really really appreciate it! :D

---

### Post by pytheas22 on 2009-03-24
I'm glad it's working.  It should only be asking for your keyring password once after reach reboot, but I don't know of any way to get around that.

---

### Post by Psultan on 2009-05-05
Hello,

I am very much in the same boat as Tim who originally posted this thread.

I have no user experience of Ubuntu or CLI.

I have thoroughly read the thread so far and am not sure if any of the solutions apply to me. 

Here is what I have done so far.

I have installed an .INF file from the driver for F5D7051 using indsgtk, but have had no luck connecting to my network. I have input the SSID & WEP values but still cant connect.

Below are the values of lsusb, lshw -C Network, lsmod dmesg | tail (with belkin usb adapter plugged in), lspci and lshw

I also have the problem of a start up error before login alerting me with this: 
(EE) intel (0): No valid modes
(EE) screen(s): found no useable configuration

I ran in low graphics mode (it informed me it was using display1) then changed the reolution in the Ubuntu dektop to 1024x768, which seems ok, but i'm not sure if it is still low graphics.

Sorry for the long post but I am mega Linux newb with a growing distaste for Vista. Please Help! Thanks! 

psultan@ubuntu:~$ lsusb
Bus 001 Device 004: ID 050d:7051 Belkin Components F5D7051 54g USB Network Adapter
Bus 001 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05fe:1010 Chic Technology Corp. Optical Wireless
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
psultan@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: eth0
       version: 10
       serial: 00:01:6c:1a:bf:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:4f:93:55:fe:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
psultan@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  39844  0 
udf                    87716  1 
crc_itu_t              10112  1 udf
binfmt_misc            16776  1 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video
lp                     17156  0 
iTCO_wdt               19108  0 
psmouse                61972  0 
iTCO_vendor_support    11652  1 iTCO_wdt
pcspkr                 10496  0 
serio_raw              13316  0 
ppdev                  15620  0 
ndiswrapper           193436  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              34108  1 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                42696  1 intel_agp
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
8139too                32128  0 
8139cp                 27776  0 
mii                    13312  2 8139too,8139cp
floppy                 64324  0 
usb_storage            82880  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
psultan@ubuntu:~$ dmesg | tail
[   18.455690] type=1505 audit(1241562566.543:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2069
[   18.487489] type=1505 audit(1241562566.575:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2073
[   20.319917] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.319921] Bluetooth: BNEP filters: protocol multicast
[   20.341860] Bridge firewalling registered
[   25.909699] eth0: link down
[   25.909954] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.198155] mtrr: no MTRR for d0000000,7b0000 found
[   90.183107] UDF-fs: Filesystem marked read-only because writing to pseudooverwrite partition is not implemented.
[   90.207232] UDF-fs INFO UDF: Mounting volume 'UDF Volume', timestamp 2009/05/05 18:13 (103c)
psultan@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
psultan@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 993MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU          430  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          size: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up arch_perfmon pebs bts pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm lahf_lm
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:01:03.0
                logical name: eth0
                version: 10
                serial: 00:01:6c:1a:bf:4e
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
           *-cdrom
                description: DVD-RAM writer
                product: DVD A  DH16A1P
                vendor: ATAPI
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: RG11
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
        *-ide:1
             description: IDE interface
             product: 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:4f:93:55:fe:0d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by pytheas22 on 2009-05-05
Psultan: I'm sorry to hear you're having so many problems.  The wireless and graphics are separate issues, so let's take care of wireless first.  When that's fixed, we can figure out why your video card isn't working properly (which is strange because it's an Intel device, which should always work out-of-the-box in Linux thanks to Intel's open-source drivers...).

In order to figure out why the wireless interface isn't coming up, please post the output of these commands (some of them may have no output):
```

lsmod | grep ndis
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
uname -rm
```

---

### Post by Psultan on 2009-05-06
> **pytheas22 said:**
> Psultan: I'm sorry to hear you're having so many problems.  The wireless and graphics are separate issues, so let's take care of wireless first.  When that's fixed, we can figure out why your video card isn't working properly (which is strange because it's an Intel device, which should always work out-of-the-box in Linux thanks to Intel's open-source drivers...).

In order to figure out why the wireless interface isn't coming up, please post the output of these commands (some of them may have no output):
```

lsmod | grep ndis
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
uname -rm
```


Thank you very much for your speedy reply pytheas22!!!

Here are the results  for the values you requested

psultan@ubuntu:~$ lsmod | grep ndis
ndiswrapper           193436  0 
psultan@ubuntu:~$ ndiswrapper -l
bcmrndis : invalid driver!
psultan@ubuntu:~$ sudo modprobe ndiswrapper
[sudo] password for psultan: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
psultan@ubuntu:~$ dmesg | grep -e ndis -e wlan
[    9.230723] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    9.684146] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmrndis; check system log for messages from 'loadndisdriver'
[    9.684191] usbcore: registered new interface driver ndiswrapper
psultan@ubuntu:~$ uname -rm
2.6.28-11-generic i686

I hope this gets the ball rolling. Again, endless thanks :)

---

### Post by pytheas22 on 2009-05-06
Psultan: one more question: could you please post a link to the Windows driver that you are trying to use with ndiswrapper for this device, or upload it to the forums?  The ndiswrapper database says that you need to copy some extra files manually in order to get the Windows driver working with your card--this is probably why you get the 'invalid driver' message now.  If I get access to the Windows driver, I'll try to tell you which extra steps you need to run to get things working.

---

### Post by Psultan on 2009-05-06
> **pytheas22 said:**
> Psultan: one more question: could you please post a link to the Windows driver that you are trying to use with ndiswrapper for this device, or upload it to the forums?  The ndiswrapper database says that you need to copy some extra files manually in order to get the Windows driver working with your card--this is probably why you get the 'invalid driver' message now.  If I get access to the Windows driver, I'll try to tell you which extra steps you need to run to get things working.

Pytheas22: I went to this site: 
[http://www.belkin.com/support/article/?lid=en&pid=F5D7051&aid=6070&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D7051&aid=6070&scid=221)

and downloaded this:
[http://www.belkin.com/support/article/?lid=en&pid=f5d7051&aid=6070&scid=221&fid=2411&fn=f5d7051.exe](http://www.belkin.com/support/article/?lid=en&pid=f5d7051&aid=6070&scid=221&fid=2411&fn=f5d7051.exe)

I then saved it to a blank DVD with stuff I wanted to take from Vista like pics music etc. then used ndisgtk to install the .INF file.

Hope this help!

---

### Post by pytheas22 on 2009-05-06
Thanks for that link.  I think these are the commands you should run to get the driver installed properly via ndiswrapper:
```

sudo ndiswrapper -r bcmrndis
wget http://www.belkin.com/support/article/?lid=en&pid=f5d7051&aid=6070&scid=221&fid=2411&fn=f5d7051.exe
unzip f5d7051.exe
sudo ndiswrapper -i BCMRNDIS.INF
sudo cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys
sudo cp USB8023K.SYS /etc/ndiswrapper/bcmrndis/usb8023k.sys
echo ndiswrapper | sudo tee -a /etc/modules
```

The trick is apparently to copy those two .sys files manually into /etc/ndiswrapper/bcmrndis.  I did this on my machine (even though I don't actually have the same wireless card), and it changed the 'invalid driver!' message to 'driver installed'.

After this, reboot.  If the device still doesn't work, please post the output of:
```

ls /etc/ndiswrapper/bcmrndis
ndiswrapper -l
dmesg | grep -e ndis -e wlan
lshw -C Network
sudo iwlist scan
```

---

### Post by Psultan on 2009-05-06
> **pytheas22 said:**
> Thanks for that link.  I think these are the commands you should run to get the driver installed properly via ndiswrapper:
```

sudo ndiswrapper -r bcmrndis
wget http://www.belkin.com/support/article/?lid=en&pid=f5d7051&aid=6070&scid=221&fid=2411&fn=f5d7051.exe
unzip f5d7051.exe
sudo ndiswrapper -i BCMRNDIS.INF
sudo cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys
sudo cp USB8023K.SYS /etc/ndiswrapper/bcmrndis/usb8023k.sys
echo ndiswrapper | sudo tee -a /etc/modules
```The trick is apparently to copy those two .sys files manually into /etc/ndiswrapper/bcmrndis.  I did this on my machine (even though I don't actually have the same wireless card), and it changed the 'invalid driver!' message to 'driver installed'.

After this, reboot.  If the device still doesn't work, please post the output of:
```

ls /etc/ndiswrapper/bcmrndis
ndiswrapper -l
dmesg | grep -e ndis -e wlan
lshw -C Network
sudo iwlist scan
```

Hello Pytheas22,

I briefly tried the first few of your command lines and saw that the wget command not working? could this be because Ubuntu can't connect to the internet? What if I just copied the contents of the driver onto the ubuntu desktop? what commands can I use to install the driver without internet connectivity?

---

### Post by pytheas22 on 2009-05-06
> I briefly tried the first few of your command lines and saw that the wget command not working? could this be because Ubuntu can't connect to the internet? What if I just copied the contents of the driver onto the ubuntu desktop? what commands can I use to install the driver without internet connectivity?

Yes, the problem is that you need an Internet connection for the wget command to work--my apologies; I didn't realize you had no connection at all.  If you have an ethernet connection available that you can plug into temporarily, that would be the easiest way to run those commands.  If not, however, it should work for you to download the f5d7051.exe file and save it to your desktop on Ubuntu, then run these commands to extract the necessary files:

```
cd ~/Desktop
unzip f5d7051.exe
sudo ndiswrapper -i BCMRNDIS.INF
sudo cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys
sudo cp USB8023K.SYS /etc/ndiswrapper/bcmrndis/usb8023k.sys
echo ndiswrapper | sudo tee -a /etc/modules
```

---

### Post by Psultan on 2009-05-06
> **pytheas22 said:**
> Yes, the problem is that you need an Internet connection for the wget command to work--my apologies; I didn't realize you had no connection at all.  If you have an ethernet connection available that you can plug into temporarily, that would be the easiest way to run those commands.  If not, however, it should work for you to download the f5d7051.exe file and save it to your desktop on Ubuntu, then run these commands to extract the necessary files:

```
cd ~/Desktop
unzip f5d7051.exe
sudo ndiswrapper -i BCMRNDIS.INF
sudo cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys
sudo cp USB8023K.SYS /etc/ndiswrapper/bcmrndis/usb8023k.sys
echo ndiswrapper | sudo tee -a /etc/modules
```


Outstanding! 8) Your instructions worked perfectly, straight after the reboot I got a permissions request for Keyring and it connected immediately. A Thousand Thank yous! I'm stoked!

Okay, so what can we now do about my graphics situation? I found an article that might be relevant here: 
[http://www.itwriting.com/blog/1358-ubuntu-904-not-so-jaunty.html](http://www.itwriting.com/blog/1358-ubuntu-904-not-so-jaunty.html)

his third bullet point and update are the relevant points.

Where to next?

---

### Post by pytheas22 on 2009-05-06
Glad to hear it connected.

As for the graphics: the first thing to do is to apply Ubuntu updates, in case that solves the problem (it probably won't, but it doesn't hurt to try).  If it doesn't, please post the output of this command so I know exactly which graphics chipset you have:
```

lspci -nn | grep -i vga
```

From there, we can google around to see if a straight-forward solution comes up.  The blog post you linked to might help, but it's hard to be sure until we know exactly which video card you have.

---

### Post by Psultan on 2009-05-06
> **pytheas22 said:**
> Glad to hear it connected.

As for the graphics: the first thing to do is to apply Ubuntu updates, in case that solves the problem (it probably won't, but it doesn't hurt to try).  If it doesn't, please post the output of this command so I know exactly which graphics chipset you have:
```

lspci -nn | grep -i vga
```From there, we can google around to see if a straight-forward solution comes up.  The blog post you linked to might help, but it's hard to be sure until we know exactly which video card you have.

How do I get updates for Ubuntu Jaunty? Do I have to select them or is there an archive I can download from? I'm slightly out of my depth here.

Here is the output anyway:

00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)

I'll get googling too and see what's about. Thanks again :)

---

### Post by pytheas22 on 2009-05-06
After a few minutes logged into your desktop, the Update Manager icon should appear in the system tray in the upper-right corner of your screen.  You can left-click on it to open the utility to apply updates.  You can also update manually from the command line by typing:
```

sudo apt-get update
sudo apt-get upgrade
```

I'll do some googling and get back with instructions that will hopefully fix the graphics situation.

---

### Post by pytheas22 on 2009-05-06
I read a couple bug reports (like [this one]("https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/304871?comments=all")) that suggest that the issue may indeed have been fixed by Ubuntu updates.  So apply the updates, then run this command to tell your computer to use normal graphics mode:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot and see if you can log in normal.  If you can, go to System>Preferences>Appearance and try to enable desktop effects.

If this still doesn't work, I think the next thing to try is the fix described on this [wiki page]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").

---

### Post by clydew1 on 2009-05-10
Hi 
I am trying to get F5D7051 to work with my ubuntu installation . I have done the following
0. used f5d7051 on pc with xp and it works 
1. used ndiswrapper with ndis driver on cd which came with F5D7051. The ndis driver is different from above , this usb wifi was brought less than a month ago , so its new . I think it may have a different chipset to the previous ones , its still broadcom but 438? or something similar. I may be wrong here. The ndis driver causes the ndswrapper to abend , and hang if i do ndswrapper -l . There is "core" dump messages in the messages.log file . I used the latest ndiswrapper as well as the one supplied with the latest release ubuntu , same result.
2. tried the method suggest above with the f5d7051.exe driver . This does loads but has an error 22 , and says it cannot initialise the device , in the messages log 
Has anyone any suggestion on how I should proceed ? 
Thanks
Clyde

---

### Post by pytheas22 on 2009-05-10
Clyde: what is the output of this command with your device plugged in:
```

lsusb
```

---

### Post by clydew1 on 2009-05-11
Hi 
Thanks , 4317:0711 is the device . The line 6 is a guitar / usb effects processor . 

Bus 001 Device 003: ID 4317:0711  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x4317 
  idProduct          0x0711 
  bcdDevice            0.01
  iManufacturer           1 Broadcom
  iProduct                2 802.11b/g LP/SC USB
  iSerial                 3 43860000
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              200mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      2 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.7
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0503 highspeed power enable connect
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.1
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0x092f QuickCam Express Plus
  bcdDevice            0.00
  iManufacturer           1         
  iProduct                2 Camera
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          233
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0370  1x 880 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0280  1x 640 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0380  1x 896 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       8
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0220  1x 544 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       9
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0290  1x 656 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      10
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x02c0  1x 704 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      11
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0360  1x 864 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      12
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03c0  1x 960 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting      13
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x034d  1x 845 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0001 1.1 root hub
  bcdDevice            2.06
  iManufacturer           3 Linux 2.6.28-11-generic uhci_hcd
  iProduct                2 UHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             255
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood        1 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0103 power enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

---

### Post by pytheas22 on 2009-05-11
I googled a bit and unfortunately couldn't find a single person who's gotten this to work with ndiswrapper.  But we can still try.  Could you please post the output of:
```

dmesg | grep -e ndis -e wlan
```

If you could upload the f5d7051.exe file somewhere so I could take a look at it, that would be helpful as well.

---

### Post by pupiddo on 2009-09-24
> **pytheas22 said:**
> Thanks for that link.  I think these are the commands you should run to get the driver installed properly via ndiswrapper:
```

sudo ndiswrapper -r bcmrndis
wget http://www.belkin.com/support/article/?lid=en&pid=f5d7051&aid=6070&scid=221&fid=2411&fn=f5d7051.exe
unzip f5d7051.exe
sudo ndiswrapper -i BCMRNDIS.INF
sudo cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys
sudo cp USB8023K.SYS /etc/ndiswrapper/bcmrndis/usb8023k.sys
echo ndiswrapper | sudo tee -a /etc/modules
```The trick is apparently to copy those two .sys files manually into /etc/ndiswrapper/bcmrndis.  I did this on my machine (even though I don't actually have the same wireless card), and it changed the 'invalid driver!' message to 'driver installed'.

After this, reboot.  If the device still doesn't work, please post the output of:
```

ls /etc/ndiswrapper/bcmrndis
ndiswrapper -l
dmesg | grep -e ndis -e wlan
lshw -C Network
sudo iwlist scan
```

I tried many time to install this driver
this is my lsusb:

Bus 001 Device 003: ID 4317:0711
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
and uname -a
Linux vulcano 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux on kubuntu Jaunty

pupiddo@vulcano:~$ cd f5d7051/
pupiddo@vulcano:~/f5d7051$ sudo ndiswrapper -i BCMRNDIS.INF
[sudo] password for pupiddo:
installing bcmrndis ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
pupiddo@vulcano:~/f5d7051$ sudo cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys
pupiddo@vulcano:~/f5d7051$ sudo cp USB8023K.SYS /etc/ndiswrapper/bcmrndis/usb8023k.sys
pupiddo@vulcano:~/f5d7051$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
pupiddo@vulcano:~/f5d7051$ ndiswrapper -l
bcmrndis : driver installed

pupiddo@vulcano:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

the led on the key don't blink infact

pupiddo@vulcano:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

This is the output you had opreviusly requested:
pupiddo@vulcano:~$ ls /etc/ndiswrapper/bcmrndis
050D:7051.F.conf  1799:7051.F.conf  bcmrndis.inf  rndismpk.sys  usb8023k.sys

pupiddo@vulcano:~$ dmesg | grep -e ndis -e wlan
[   13.568087] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.165591] usbcore: registered new interface driver ndiswrapper



pupiddo@vulcano:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:16:ec:60:b2:62
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.1.100 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

According to this how-to([http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206))

I made this file sudo gedit /etc/udev/rules.d/99-custom.rules
and put into this line:
BUS=="usb", SYSFS{idProduct}=="0711", SYSFS{idVendor}=="4713", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

Have you any other suggestion?

---

### Post by pytheas22 on 2009-09-26
pupiddo: the only suggestion I can make is to downgrade to Ubuntu 8.04 and then try following [the tutorial]("http://ubuntuforums.org/showthread.php?t=225206") you linked to.  I think the /etc/udev/rules.d/99-custom.rules file you made won't work in Ubuntu 8.10 and higher because of changes to udev, but on 8.04, it should work.

That said, the 4317:0711 device (which you have) is extremely problematic.  I've worked with other users to try to get it working using both ndiswrapper and the native driver (called rndis) and have had no success with either.

Sorry I can't offer more help.

---

### Post by Bilal Haddad on 2009-09-26
i just instaled the ubuntu 9.4 on my system and it didn't recognise the driver for the wireless card, i have the driver for the linux operating system, it came with the laptop,but have no idea on how to instal it,thanks in advance.

---

### Post by pupiddo on 2009-09-27
> **pytheas22 said:**
> pupiddo: the only suggestion I can make is to downgrade to Ubuntu 8.04 and then try following [the tutorial]("http://ubuntuforums.org/showthread.php?t=225206") you linked to.  I think the /etc/udev/rules.d/99-custom.rules file you made won't work in Ubuntu 8.10 and higher because of changes to udev, but on 8.04, it should work.

That said, the 4317:0711 device (which you have) is extremely problematic.  I've worked with other users to try to get it working using both ndiswrapper and the native driver (called rndis) and have had no success with either.

Sorry I can't offer more help.

It's very strange because works on windows XP virtualized on my distro with virtualbox!
Thank's for all.
Bye

---

### Post by pytheas22 on 2009-09-27
pupiddo: what do you mean when you say the device works in virtualized Windows XP?  Are you passing the USB bus directly to the guest operating system and then using the Windows driver to make it work?  If so, that's basically the same thing as using the card on a normal Windows computer.

Bilal Haddad: please open a terminal from the Applications>Accessories menu and post the output of these commands, and I'll try to help:
```

lsusb
lspci -nn
sudo iwlist scan
uname -rm
```

---

### Post by pupiddo on 2009-09-29
> **pytheas22 said:**
> pupiddo: what do you mean when you say the device works in virtualized Windows XP?  Are you passing the USB bus directly to the guest operating system and then using the Windows driver to make it work?  If so, that's basically the same thing as using the card on a normal Windows computer.



pytheas22: damn, it's true!

---

### Post by pytheas22 on 2009-09-29
> pytheas22: damn, it's true!

Sorry to hear that.  I wish there were a way for you to use the wireless card in the guest operating system to give connectivity to the Ubuntu host, but I don't think that's possible (I [started a thread]("http://ubuntuforums.org/showthread.php?p=8025584#post8025584") to ask anyway, though, because it's an interesting concept to me).

So I think your only options are to buy a different wireless card, or wait and hope that support for this one is added to Ubuntu soon.  I'm really sorry about this, and really wish I knew how to make your wireless card work.  But as I said, I've spent weeks working with other users to try to figure out what's wrong with this particular model, and have had no success...

---

### Post by pupiddo on 2009-09-30
> **pytheas22 said:**
> Sorry to hear that.  I wish there were a way for you to use the wireless card in the guest operating system to give connectivity to the Ubuntu host, but I don't think that's possible (I [started a thread]("http://ubuntuforums.org/showthread.php?p=8025584#post8025584") to ask anyway, though, because it's an interesting concept to me).

So I think your only options are to buy a different wireless card, or wait and hope that support for this one is added to Ubuntu soon.  I'm really sorry about this, and really wish I knew how to make your wireless card work.  But as I said, I've spent weeks working with other users to try to figure out what's wrong with this particular model, and have had no success...

Do you Know how can I help to insert this support on karmic?

---

### Post by pytheas22 on 2009-10-01
> Do you Know how can I help to insert this support on karmic? 

The best way to get developers' support on this would be to [file a bug report on Launchpad]("https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net").  Ultimately it's an upstream issue that will need to be solved by someone other than the Ubuntu developers, but hopefully a report on Launchpad will get the attention of the right people.

Include the output of the commands you posted previously, and mention that ndiswrapper doesn't work for this device, even when installed properly, so it's clear that a native Linux driver needs to be written.  Let me know if you need any help.

---

### Post by pupiddo on 2009-10-01
> **pytheas22 said:**
> The best way to get developers' support on this would be to [file a bug report on Launchpad]("https://help.ubuntu.com/community/ReportingBugs#Filing%20bugs%20at%20Launchpad.net").  Ultimately it's an upstream issue that will need to be solved by someone other than the Ubuntu developers, but hopefully a report on Launchpad will get the attention of the right people.

Include the output of the commands you posted previously, and mention that ndiswrapper doesn't work for this device, even when installed properly, so it's clear that a native Linux driver needs to be written.  Let me know if you need any help.

Thank's, done!

---

### Post by Bebis on 2009-11-19
Hello, I am also a newbie at least concerning debian linux and would like to ask a very simple question. If I want to enable my wireless usb adapter to work on scanning mode which of all this methods should I try? (want to play with iwpriv and tels me "no private ioctls." so I just considered it can not go in scanning mode with the drivers I am currently using...)

---

### Post by pytheas22 on 2009-11-19
> Hello, I am also a newbie at least concerning debian linux and would like to ask a very simple question. If I want to enable my wireless usb adapter to work on scanning mode which of all this methods should I try? (want to play with iwpriv and tels me "no private ioctls." so I just considered it can not go in scanning mode with the drivers I am currently using...)

By scanning mode do you mean monitor mode, the mode in which you can listen to all wireless traffic in range?  If so, it may be the case that your driver simply doesn't support monitor mode, or you may not be starting it correctly.  Are you trying to use an application for sniffing, such as Wireshark, kismet or airodump?  If so, each of those should have its own method for enabling monitor mode.  Otherwise, in general the command:
```

sudo iwconfig wlan0 mode monitor
```

should put it into monitor mode, but sometimes this can vary by driver (some drivers require special utilities for configuring the mode instead of iwconfig).

If you post the output of these commands, I should know which driver you're using:
```

lshw -C Network
lsusb
```

---

### Post by theDaveTheRave on 2009-11-20
> **pupiddo said:**
> It's very strange because works on windows XP virtualized on my distro with virtualbox!
Thank's for all.
Bye

I know that this is a bit slow off the mark for a response, but can't you "share a network connection" within XP?

If you have the card fucntioning in XP it should be a simple matter of sharing the connection to other pcs, and you'll be done.

It may require instalation of a DHCP server or some how turn your virtual XP into a "router" for the system to enable the "pass through" to work. But technically I'm sure it should be quite a simple procedure.

---

### Post by Bebis on 2009-12-11
> **pytheas22 said:**
> By scanning mode do you mean monitor mode, the mode in which you can listen to all wireless traffic in range?  If so, it may be the case that your driver simply doesn't support monitor mode, or you may not be starting it correctly.  Are you trying to use an application for sniffing, such as Wireshark, kismet or airodump?  If so, each of those should have its own method for enabling monitor mode.  Otherwise, in general the command:
```

sudo iwconfig wlan0 mode monitor
```should put it into monitor mode, but sometimes this can vary by driver (some drivers require special utilities for configuring the mode instead of iwconfig).

If you post the output of these commands, I should know which driver you're using:
```

lshw -C Network
lsusb
```


Ok here they come:




  *-network:0             
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth1
       version: 08
       serial: 00:d0:b7:0b:e4:47
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:66:10:75:d1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:16:87:92:2e:2f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:17:3f:c7:12:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device ip=192.168.0.3 link=yes multicast=yes wireless=IEEE802.11bg



And




Bus 005 Device 002: ID 050d:7051 Belkin Components F5D7051 54g USB Network Adapter
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0df7:0620 Mobile Action Technology, Inc. MA-620 Infrared Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



And sorry for the late answer but i was away from home...

(connected with the card we are speaking for)

---

### Post by pytheas22 on 2009-12-12
**Bebis**: I'm afraid you're out of luck for using monitor mode with this device.  It uses the rndis_wlan driver, the only Linux driver available for this chip, and according to [http://www.aircrack-ng.org/doku.php?id=compatibility_drivers:](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers:)
> 
Like Madwifi, b43 offers no support for Broadcom-based USB devices. For those, a separate driver called rndis_wlan exists, which doesn't support monitor mode (and will never do so, as the chipset has no raw mode).

If you need to use monitor mode, your best bet would be to look for a USB stick with a Ralink chipset, as those are relatively cheap and should all support monitor mode with no problems.  I think Prism chipsets in USB devices would also do monitor mode.  Avoid Atheros-based USB sticks; those probably won't be able to sniff.

You could also just get an internal wireless card; with a few notable exceptions (the Broadcom b/g/n chips, for example), almost every PCI-based wireless device should support monitor mode these days.

---

### Post by jmmL on 2010-01-10
> **pytheas22 said:**
> If you need to use monitor mode, your best bet would be to look for a USB stick with a Ralink chipset, as those are relatively cheap and should all support monitor mode with no problems.  I think Prism chipsets in USB devices would also do monitor mode.  Avoid Atheros-based USB sticks; those probably won't be able to sniff.


I'm interested in buying this device. Basically, I need any wifi USB stick that will (preferably easily) run in master mode so I can set up a wifi hotspot for my phone (which can't connect to ad-hoc networks). According to [this page]("http://wiki.debian.org/rt2500usb#SupportedDevices") the Belkin F5D7051 has a chipset supported by the rt2500usb driver. [This page]("http://linuxwireless.org/en/users/Drivers") says that the rt2500usb driver can be used as an access point (which means it supports master mode, right?). If I get this stick, will I be able to put it into master mode and create my own (non ad-hoc) hotspot?

---

### Post by pytheas22 on 2010-01-11
jmmL: yes, the rt2500usb driver is supposed to support master mode.  I've never tried it personally (I just do ad-hoc since that's so much easier), but you should be able to get it working.

---

### Post by Post Monkeh on 2010-01-14
> **Post Monkeh said:**
> sorry to butt in on the thread, but since there seems to be a few fairly linux-wise folk in here i thought i'd ask a little question

i'm also having a bit of a problem with the belkin wireless g (050d:705e is the device code when i lsusb it)

however, the device isn't actually installed. when i do an lshw, it doesn't appear.  i think if i could get it as far as having the wrong driver installed i could get it working with the help of the numerous other threads dotted around the place, but i haven't seen anyone with exactly the same fault as mine.

incidentally, i have a wireless usb keyboard/mouse that works fine, a usb bluetooth doongle that works fine, and i've tried the wireless adapter in several different usb ports without success (though i can always lsusb it)

another thing, i don't know if it's important, but if i lsusb, then remove the adapter and put it back in the same usb port, it comes back with a totally different buss/device number.

quick update to the problems i was having a while back.

this chipset seems to be much better supported in the newer kernels, i tried a number of different distros on my desktop last week and the wireless worked pretty much perfectly on all of them (although after the weird problems i had with my signal dropping when my brother's laptop was connected, i would have to point out that he doesn't live with my folks anymore)

---

### Post by deeptingler on 2010-01-15
I have just followed these instructions on Karmic 64bit for a Belkin Wireless N usb adapter  model 3015uk with driver rt2870.inf and it worked first time!!!!   not done any long term testing yet but thankyou for the hand in using ndiswrapper as it was a very clear and easy process as you laid it out VERY clearly.....  to everyone else... please do the reboot and install the usb adapter only when instructed.

---

