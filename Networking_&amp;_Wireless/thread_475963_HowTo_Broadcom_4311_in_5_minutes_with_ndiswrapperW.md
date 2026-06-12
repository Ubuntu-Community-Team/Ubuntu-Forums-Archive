---
title: "HowTo: Broadcom 4311 in 5 minutes with ndiswrapper/WPA for fresh Feisty installs"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-06-16
***[This thread is read only, see this thread]("http://ubuntuforums.org/showthread.php?p=5456980")***

*Edit: Since I originally posted this I've also added support for other devices, so it now supports the BCM4306, BCM4310, BCM4311, BCM4312, BCM4318, and BCM4328*
*Edit 2: Update (Oct 2007): Gutsy Gibbon (*Ubuntu 7.10) has native support (via the restricted driver manager) that actually works, so this guide isn't strictly necessary for Gutsy. However, Gutsy's native support isn't capable of quite the same bandwidth as this ndiswrapper solution. Further, it doesn't seem to work for everyone. Fortunately, this guide also appears to be compatible with Gutsy.*
***Edit 3: Update (Apr 26 2008): This howto works with Hardy Heron (*Ubuntu 8.04) for many users. I've added some Hardy-specific commands that workaround an outstanding (ssb) module loading bug. Note, this howto still doesn't work for some Hardy users, for reasons we haven't fully hashed out yet, but almost certainly related to the ssb issue. Hardy users, please refrain from voting until this is worked out, but feel free to make thread posts.***

I created a quick howto for myself, since I've had to install this card a few times. This howto works well for fresh installs of Feisty (and Gutsy, and Hardy), and requires no compiled packages. (This means simple apt-get installs only for most people, but there are ndiswrapper compilation instructions for those who need it.)

[BCM43xx HowTo.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

This should take less than 5 minutes.

Please report your results here or on the wiki. Others benefit from detailed feedback, so you get bonus points if you provide all of the following:

**HARDY Users, Before Following the Wiki**: (I need this to try to develop a module-reloading script, since Hardy users ideally should use a custom module reloader for their particular hardware.)
[LIST]
[*]Modules and Dependencies: [COLOR="DarkRed"][FONT="Courier New"]lsmod[/FONT][/COLOR]
[/LIST]

**All Users, After Following the Wiki** 
[LIST]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): [COLOR="DarkRed"][FONT="Courier New"]lspci | grep Broadcom[/FONT][/COLOR]
[*]Wireless Chipset: [COLOR="DarkRed"][FONT="Courier New"]lspci -n | grep '14e4:43'[/FONT][/COLOR]
[*]Ubuntu Version:  [COLOR="DarkRed"][FONT="Courier New"]lsb_release -d[/FONT][/COLOR]
[*]Kernel / Architecture:  [COLOR="DarkRed"][FONT="Courier New"]uname -mr[/FONT][/COLOR]
[*]Any *extra* boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[/LIST]

Good luck,
Jamie

---

### Post by maxdaemon on 2007-07-06
It worked for me, thank you so much, that took days to do in Edgy.  I had to reboot several times after following the instructions before it actually connected and I could browse the internet, but it's great now.

---

### Post by Jamie Jackson on 2007-07-06
Glad to hear it, thanks for the feedback!

---

### Post by fredj on 2007-07-07
That is interesting but it seems to depend upon having an internet connection so that you can 
download some software. How would this work for people who only have a wireless connection
that doesn't work?

---

### Post by kevdog on 2007-07-07
Why is this statment needed??

> sudo cp /etc/ndiswrapper/bcmwl5/XXXX:XXXX.5.conf /etc/ndiswrapper/bcmwl5/.conf

I didnt use this method to install my driver, but did install ndiswrapper according the instructions posted at the sourceforge website: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

There was no mention of this step.  I know I didnt do this step and everything is working for me!

---

### Post by Jamie Jackson on 2007-07-09
> **kevdog said:**
> Why is this statment needed??



I didnt use this method to install my driver, but did install ndiswrapper according the instructions posted at the sourceforge website: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

There was no mention of this step.  I know I didnt do this step and everything is working for me!

Hmm, I don't want any extraneous steps in there. If I get a chance, I'll start clean and try it without that step. I'll scrap it if I don't need it either. (Or unless someone tells me why it's necessary.)

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-07-09
> **fredj said:**
> That is interesting but it seems to depend upon having an internet connection so that you can 
download some software. How would this work for people who only have a wireless connection
that doesn't work?

I plug in an ethernet cable until I've got it set it up, so I don't have instructions for how to do it offline. Maybe someone else can help with that.

---

### Post by Jamie Jackson on 2007-07-09
> **kevdog said:**
> Why is this statment needed??



I didnt use this method to install my driver, but did install ndiswrapper according the instructions posted at the sourceforge website: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

There was no mention of this step.  I know I didnt do this step and everything is working for me!

It turns out it's part of a step that I didn't fully flesh out, so I've removed it. I've read that some people can't get this card to work with Linksys routers when *Afterburner* (a proprietary Broadcom extension) is enabled (as it is by default).

I'll have to play with a Linksys router when I get a chance, and try it with and without Afterburner. If this makes a difference, I'll add that step back in with the disabling instructions. In the meantime let me know if my instructions fail for Linksys routers, and try disabling Afterburner as described a bit down the page [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-f1b6201d0b5822506a2df08fa5b8314f4237e765")

---

### Post by johnaaronrose on 2007-07-11
I have a Dell Inspiron 1501 with the 1390 mini card. I've tried a few variants of getting it to work using ndiswrapper:
using the sp33008.exe in the [https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff) tutorial;
using Wicd in the [http://wicd.sourceforge.net/wiki/doku.php?id=faq;](http://wicd.sourceforge.net/wiki/doku.php?id=faq;)
using R151517.EXE in this tutorial.

All of them result in Ubuntu Feisty (either Network Manager or Wicd as appropriate) being able to to see the network but no joy in using Swiftfox or Evolution.

My guess is that it's to do with wpa (see attached archive 1390TxtFiles.tar.gz). Help please!

lspci output
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)

lspci -n output:
00:00.0 0600: 1002:5950 (rev 10)
00:01.0 0604: 1002:5a3f
00:05.0 0604: 1002:5a37
00:06.0 0604: 1002:5a38
00:12.0 0106: 1002:4380
00:13.0 0c03: 1002:4387
00:13.1 0c03: 1002:4388
00:13.2 0c03: 1002:4389
00:13.3 0c03: 1002:438a
00:13.4 0c03: 1002:438b
00:13.5 0c03: 1002:4386
00:14.0 0c05: 1002:4385 (rev 13)
00:14.1 0101: 1002:438c
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:438d
00:14.4 0604: 1002:4384
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:05.0 0300: 1002:5975
05:00.0 0280: 14e4:4311 (rev 01)
08:00.0 0200: 14e4:170c (rev 02)
08:01.0 0805: 1180:0822 (rev 19)
08:01.1 0880: 1180:0843 (rev 01)

/etc/modules:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper

/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp


/etc/modprobe.d/blacklist:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

# broadcom 1390
blacklist bcm43xx


/etc/ndiswrapper:
alias eth1 ndiswrapper
alias wlan0 ndiswrapper


/etc/default/wpasupplicant:
ENABLED=0


/var/log/syslog & dmesg relevant parts are in an attached archive (1390TxtFiles.tar.gz).

---

### Post by reuben on 2007-07-11
I had a compiled ndiswrapper installed (and no longer working) on my HP laptop with this card. I followed the instructions on the No-Fluff howto, after completely removing (make uninstall, rmmod, etc) the previous. However, now when I try the modprobe line, I get:

> sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

What's going wrong? I will try the full-fluff, when I get a second, but I'd rather use the No-Fluff.

Thanks

---

### Post by RainKap on 2007-07-11
:) Great stuff - I followed the "no fluff" instructions for my Acer Ferrari 4005WLmi and it worked exactly as it said on the tin! Only thing that stopped it being 5 mins as promised was that SWMBO told me to go and set the table for dinner ;)

Thanks again

Ian

---

### Post by Jamie Jackson on 2007-07-12
You seem to be really close.

> **johnaaronrose said:**
> 
/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp


I think you missed the second command, below:
```

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

```

Run them both again, and you should only be left with two lines (referencing "lo")  in the /etc/network/interfaces file.

After this, issue the following for good measure (to get NetworkManager restarted):

```

sudo /etc/init.d/dbus restart

```

Good luck,
Jamie

---

### Post by Jamie Jackson on 2007-07-12
> **reuben said:**
> I had a compiled ndiswrapper installed (and no longer working) on my HP laptop with this card. I followed the instructions on the No-Fluff howto, after completely removing (make uninstall, rmmod, etc) the previous. However, now when I try the modprobe line, I get:

> sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

What's going wrong? I will try the full-fluff, when I get a second, but I'd rather use the No-Fluff.

Thanks

My best guess is that your ndiswrapper uninstallation was incomplete. Please try [this short section]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)#head-f744e28e6c78eb83d22be77819b130016a8e51f3") of the fluffy howto. *Particularly the part about rebooting after ndiswrapper unistallation*. (I have a feeling that the reboot might be the part you missed.)

So, after uninstalling ndiswrapper as shown above, try my distilled directions again, then report back.

Thanks,
Jamie

---

### Post by Zarboon on 2007-07-12
Jamie your a godsend! I have an Acer 9410-2028 laptop with a Broadcom 4311 wireless card and I have had nothing but trouble with other distros.  Im happy to report that your tutorial worked flawlessly.  Three Cheers!! Im now a Ubuntu user thanks to you!

---

### Post by xe1ufo on 2007-07-12
Jamie Jackson:

Thanks a trillion!! I have never been able to get my HP Pavilion L2005CO Lance Armstrong Special to work on the built-in Broadcom with Ubuntu (but it worked great with Mandriva 2006, though Mandriva never recognized my PCMCIA cards.) So I would have to use an antique Enterasys RoamAbout 16-bit PCMCIA WiFi card.

Now, Jamie, thanks to you, I am up 100%!  YOU ARE THE BEST!!!

:popcorn:
 

Dr. Steve, central old Mexico

---

### Post by johnaaronrose on 2007-07-12
Jamie,


I tried, as you suggested:
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces

followed by the 'network restart' command.

Same as before: shows connection established to my network (Wolverhampton) but not sufficient to connect to internet. I actually did this previously on one of my previous attempts. One interesting thing is that the Network Manager (when opened using Manual Connection by clicking on the systray icon) does not allow input of a WPA key (i.e. only WEP key) for the wireless connection. This is one reason why I tried Wicd, because it allows WPA to be set. I have previously tried amending the /etc/wpa_supplicant/wpa_supplicant_conf file to include parameters for the ssid and wpa key, but with no success. Since then I've cleared down the  /etc/wpa_supplicant/wpa_supplicant_conf file.

I'm going round in circles!

---

### Post by Jamie Jackson on 2007-07-12
I figure something that you've tried before is spoiling the "freshness" of your install.

FYI, here's what my ndiswrapper file looks like:
```

jamie@mercury:~$ cat /etc/modprobe.d/ndiswrapper 
alias wlan0 ndiswrapper

```

You *might* try removing the other entry from it, so it matches mine.

Also, I have no wpa supplicant conf at all:
```

jamie@mercury:~$ ls /etc/wpa_supplicant/
functions.sh  ifupdown.sh

```

Also, could you re-post your /etc/network/interfaces file, so I can see what it looks like now?

Oh, also, please send the output of "uname -a"

---

### Post by johnaaronrose on 2007-07-12
Jamie,

I've deleted the empty wpa_supplicant.conf file.

Here are the results you requested:

administrator@jess-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp


administrator@jess-laptop:~$ uname -a
Linux jess-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
administrator@jess-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias eth1 ndiswrapper
alias wlan0 ndiswrapper

administrator@jess-laptop:~$ ls /etc/wpa_supplicant
functions.sh  ifupdown.sh
administrator@jess-laptop:~$ 


I guess that the extra line (iface eth0 inet dhcp) in the /etc/network/interfaces file is due to Network Manager amending the file upon switching to 'wired'?

I guess that the 'eth1' line in the /etc/modprobe.d/ndiswrapper file is because Network Manager uses eth1 (rather than wlan0) for the 1390 wireless card?

I have had the device working on wep (to a British Telecom wireless hotspot).

---

### Post by Jamie Jackson on 2007-07-13
I see two things that are still suspect in your setup:

I don't know where the "iface eth0 inet dhcp" line came from in your /etc/network/interfaces file, as no matter what kind of network Network Manager connects to, it has never modified my /etc/network/interfaces file.

Second, your /etc/modprobe.d/ndiswrapper file still shows two interfaces.

So, where to go from here:

1. I'm pretty confident that you don't want anything but the first two lines in /etc/network/interfaces, so re-delete that eth0 line.
2. Modify /etc/modprobe.d/ndiswrapper so it *only* has the line:  "alias wlan0 ndiswrapper"
3. Reboot
4. Send the output of "cat /etc/iftab"
5. Send the output of "iwconfig"
6. Send the output of "ifconfig"

I'm willing to keep trying if you are...

---

### Post by gtgenter on 2007-07-14
HP Pavilion ze4430.  Great "How to"!  Now my wireless is running at 54Mbps whereas before it would only connect at 11 Mb/s.  Super!  Thanks!!

---

### Post by ugm6hr on 2007-07-15
> **fredj said:**
> That is interesting but it seems to depend upon having an internet connection so that you can 
download some software. How would this work for people who only have a wireless connection
that doesn't work?

Haven't tried this - but maybe someone could check it works?  Obviously you need access to the internet somewhere to download the following packages (and a USB stick to transfer).

Go to the following sites and click on the appropriate Architecture in the download table, and then on a download mirror to get the packages.  Copy to* /var/cache/apt/archives* on your Feisty computer.
[http://packages.ubuntu.com/feisty/utils/cabextract](http://packages.ubuntu.com/feisty/utils/cabextract)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)

Go to the following site to get the package and copy to /home/*user* on your Feisty computer.
[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

Then the how-to should work fine (in theory).

---

### Post by badfcar on 2007-07-15
Just wanted to say a quick thanks. Just installed Ubuntu and this was my only major sticking point. I don't really understand what all I just did yet, but it worked great! 

gateway 4025gz laptop with bcm4306 wireless.

---

### Post by johnaaronrose on 2007-07-19
Jamie,

Thanks for your continuing help. Sorry for the delay in replying: I was in France for a few days. 

Below is the output you requested:
administrator@jess-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

administrator@jess-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

administrator@jess-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:19:b9:65:cc:83 arp 1
eth1 mac 00:19:7e:06:44:82 arp 1

administrator@jess-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

administrator@jess-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:B9:65:CC:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:19:7E:06:44:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:726 (726.0 b)  TX bytes:1250 (1.2 KiB)
          Interrupt:19 Memory:d0200000-d0204000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

administrator@jess-laptop:~$ 

I have tried amending the /etc/modprobe.d/ndiswrapper file so that wlan0 is replaced by eth1, but no go.

---

### Post by ShutterAce on 2007-07-19
Jamie,

I've tried all kinds of things that I found here on the forums to get mine working with no luck. Your instructions worked though!

Thank You!!!

FYI: Machine is an HP zv6130us Athlon64 512ram Fiesty Fawn 32 bit

---

### Post by Jamie Jackson on 2007-07-19
> **ShutterAce said:**
> Jamie,

I've tried all kinds of things that I found here on the forums to get mine working with no luck. Your instructions worked though!

Thank You!!!

FYI: Machine is an HP zv6130us Athlon64 512ram Fiesty Fawn 32 bit

Glad to hear it, thanks for the feedback and system specs!

Jamie

---

### Post by Jamie Jackson on 2007-07-19
johnaaronrose,

Have any of the symptoms changed for you? In any case, could you describe the symptoms you're having?

I noticed in some other threads that you've done some things with DHCP/DNS. Are you able to connect to your AP now, but you just can't browse Web sites? If that's the case, can you hit anything by IP (e.g., Google at [http://64.233.167.99](http://64.233.167.99))?

Or... are you simply unable to connect with your AP?

Also, I may have asked this already, but what's the make and model of the router?

Thanks,
Jamie

---

### Post by johnaaronrose on 2007-07-20
Jamie,

Symptoms haven't changed. Network Manager icon on systray shows 'Attempting to join wireless network Wolverhampton'. 

Can't connect to AP or browse web. In fact, I think that can't even connect to router (as ping to it failed).

In Swiftfox, URL of [http://64.233.167.99](http://64.233.167.99) & [http://192.168.16.1](http://192.168.16.1) (i.e. router) both give standard 'not found,  try again' screen. Ping [http://64.233.167.99](http://64.233.167.99) & ping [http://192.168.16.1](http://192.168.16.1) (i.e. router) both give 'Network unreachable'.

Router is Micronetwork SP3367 wireless ADSL+Router.

---

### Post by illumin on 2007-07-20
Jamie you are a prince amongst men! Tried lots of instructions like everyone else but your instructions worked first time. I only wish they were highlighted in the wifi docs better as it was only sheer chance i found them and gave them a go. Im runnin a dell d420, 1390 wifi card on gutsy gibbon tribe 3 and it works flawlessly. Thanks again your a star :)

---

### Post by johnaaronrose on 2007-07-21
Jamie,

The wireless works with only WEP showing on Network Manager and no password on it. So the problem is down to WPA. The router wants 4 13character WEP keys, which is not consistent with Network Manager's one 10character WEP key. Obviously it's not satisfactory to run without password protection and I don't really want to use WEP instead of WPA due to its crackability. I'm going to have a think about this. Any suggestions?

---

### Post by illumin on 2007-07-21
is there anyway of automatically connecting to the wireless connection as i have to connect to it each time when i log on which is annoying. My ssid is hidden. I tried a bash batch file posted elsewhere on this forum with no joy :(

---

### Post by Jamie Jackson on 2007-07-21
> **illumin said:**
> is there anyway of automatically connecting to the wireless connection as i have to connect to it each time when i log on which is annoying. My ssid is hidden. I tried a bash batch file posted elsewhere on this forum with no joy :(

I'm glad you've got it mostly working.

Do you have access to the router settings? My suggestion would simply be to enable SSID broadcasting. WPA (or, more poorly, WEP) provides the security, whereas there's really no benefit in hiding your SSID (or requiring certain MAC IDs, etc.).

If you disagree, or don't have access to the router config, maybe we can figure something else out.

Thanks,
Jamie

---

### Post by samk on 2007-07-23
Thanks Jamie,
I have a HP Pavilion dv5040us with ubuntustudio installed. the title of the thread is true only five minutes and my wireless card is working very well.
06:02.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

samk

---

### Post by rb89 on 2007-07-23
Hey. Your guide worked like a charm when followed to a T. However, the first time I tried it, I used a different driver, and it didn't work. How can I make sure the other driver is gone?

---

### Post by Jamie Jackson on 2007-07-25
> **rb89 said:**
> Hey. Your guide worked like a charm when followed to a T. However, the first time I tried it, I used a different driver, and it didn't work. How can I make sure the other driver is gone?

What's the output of "ndiswrapper -l"?

---

### Post by Jamie Jackson on 2007-07-25
> **johnaaronrose said:**
> Jamie,

The wireless works with only WEP showing on Network Manager and no password on it. So the problem is down to WPA. The router wants 4 13character WEP keys, which is not consistent with Network Manager's one 10character WEP key. Obviously it's not satisfactory to run without password protection and I don't really want to use WEP instead of WPA due to its crackability. I'm going to have a think about this. Any suggestions?

Unfortunately there's so little I needed to do to get wpa_supplicant working properly, that I don't know much about its configuration/troubleshooting. :(

I don't know how invested you are in your current installation, but there's always the option of reinstalling, since the tutorial works well for fresh installs. Alternatively, if you can backtrack, and figure out what changes you might have made (following the other tutorials) before the No Fluff tutorial, that might get you somewhere.

Anyway, good luck. I hope you get it figured out...

---

### Post by gheywood on 2007-07-26
I must be doing something a little wrong:

greg@mediapc:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist 
Password:
blacklist bcm43xx
greg@mediapc:~$ sudo apt-get install ndiswrapper-utils-1.9 cabextractReading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ndiswrapper-common
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed
  cabextract ndiswrapper-common ndiswrapper-utils-1.9
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 104kB of archives.
After unpacking 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe cabextract 1.2-2 [53.9kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main ndiswrapper-common 1.38-1ubuntu1 [18.0kB]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main ndiswrapper-utils-1.9 1.38-1ubuntu1 [32.1kB]
Fetched 104kB in 0s (201kB/s)              
debconf: Unable to initialise frontend: Dialog
debconf: (Dialogue frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
Selecting previously deselected package cabextract.
(Reading database ... 104968 files and directories currently installed.)
Unpacking cabextract (from .../cabextract_1.2-2_i386.deb) ...
Selecting previously deselected package ndiswrapper-common.
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.38-1ubuntu1_all.deb) ...
Selecting previously deselected package ndiswrapper-utils-1.9.
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb) ...
Setting up cabextract (1.2-2) ...
Setting up ndiswrapper-common (1.38-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.38-1ubuntu1) ...
greg@mediapc:~$ sudo wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) 
--21:39:32--  [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe'
Resolving ftp.hp.com... 15.200.30.24
Connecting to ftp.hp.com|15.200.30.24|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656    207.15K/s    ETA 00:00

21:39:55 (206.14 KB/s) - `sp33008.exe' saved [4318656]

greg@mediapc:~$ -0${HOME}/sp33008.exe
bash: -0/home/greg/sp33008.exe: No such file or directory

The last line doesn't seem to have worked. Not sure what it actually does so not really sure where to start looking!!

Any suggestions?

---

### Post by Jamie Jackson on 2007-07-26
gheywood,

Yikes! Yes, I know the problem, you must have had a narrow window when you were copying commands. The last command you entered was part of the wget command that preceded it. So, until I figure out how to disable wrapping on the wiki, here it is on the forum (which doesn't have the wrapping problem).

It looks like you can just resume on line 4 (cd ~;...)

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9 cabextract
sudo wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe -O${HOME}/sp33008.exe
cd ~; mkdir bcm4311; mv sp33008.exe bcm4311; cd bcm4311
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

---

### Post by gheywood on 2007-07-26
Thanks.

After spending a few minutes reading it, I just skipped it and copied the file using my nose. Seemed to work!

All working. The wireless connection wouldn't pick up a DHCP address (wouldn't work in roaming mode), but worked when I set all the details manually. So, woohoo, still, much more painless than I was expecting!

---

### Post by Jamie Jackson on 2007-07-27
> **gheywood said:**
> Thanks.

After spending a few minutes reading it, I just skipped it and copied the file using my nose. Seemed to work!

All working. The wireless connection wouldn't pick up a DHCP address (wouldn't work in roaming mode), but worked when I set all the details manually. So, woohoo, still, much more painless than I was expecting!

What kind of router was it that you had DHCP problems with, by the way?

---

### Post by gheywood on 2007-07-28
Draytek Vigor 2600G.

---

### Post by LaGzo on 2007-07-29
Hey guys, I have a Compaq F572US with the Broadcom 4311 Rev 02

I just installed Ubuntu again and followed the no fluff steps and I got nothing. Before I followed the steps when I left clicked the network manager it showed Wired network AND Wireless network. After I followed the steps Wireless network is gone. Does that mean the tutorial deleted drivers or firmware for my wireless card? I've been trying to get this working for days :(

---

### Post by Jamie Jackson on 2007-07-29
Is this after rebooting?

If so, could you let me know the output of the following commands?

ndiswrapper -l
cat /etc/network/interfaces
grep bcm /etc/modprobe.d/blacklist
grep ndiswrapper /etc/modules
cat /etc/default/wpasupplicant
lsmod | grep ndiswrapper

---

### Post by fastpakr on 2007-07-30
> **Jamie Jackson said:**
> Is this after rebooting?

If so, could you let me know the output of the following commands?

ndiswrapper -l
cat /etc/network/interfaces
grep bcm /etc/modprobe.d/blacklist
grep ndiswrapper /etc/modules
cat /etc/default/wpasupplicant
lsmod | grep ndiswrapper

He and I have the same laptop and symptoms (after restarting, btw), so I'll jump in here... 

ndiswrapper -l
> bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)


cat /etc/network/interfaces
> auto lo
iface lo inet loopback


grep ndiswrapper /etc/modules
> ndiswrapper




grep bcm /etc/modprobe.d/blacklist
> blacklist bcm43xx


cat /etc/default/wpasupplicant
> ENABLED=0


lsmod | grep ndiswrapper
> ndiswrapper           194608  0
usbcore               134280  4 ndiswrapper,ehci_hcd,ohci_hcd


---

### Post by Jamie Jackson on 2007-07-30
You might be the first 64 bit users to try this howto. I think there's a problem with that driver on 64 bit machines that I didn't know about. I'll have to look into that.

---

### Post by fastpakr on 2007-07-30
Perhaps, but I'm running the 32 bit OS at the moment.  Surely some of the other guys are also running 64 bit processors?

---

### Post by Jamie Jackson on 2007-07-30
Okay, would one of you 64 bit folks try the following, please?

```

sudo ndiswrapper -r bcmwl5
sudo wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe -O${HOME}/sp33008.exe
cd ~; mkdir bcm4311; mv sp33008.exe bcm4311; cd bcm4311
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl564.sys

```

Then, reboot and see what happens?

If still no luck, could you then report the output of "ndiswrapper -l" again?

---

### Post by Jamie Jackson on 2007-07-30
> **fastpakr said:**
> Perhaps, but I'm running the 32 bit OS at the moment.  Surely some of the other guys are also running 64 bit processors?

Ohhhh, I made the false assumption that since you had a 64 bit processor, that you were using the 64 bit OS, sorry. All of your output looks fine, so I'm at a loss, for the time being. I don't know if it makes sense for you to try the 64 bit instructions above, or not. (I suspect not.)

I wonder if, for some reason, you'll need to compile ndiswrapper...

---

### Post by fastpakr on 2007-07-30
> **Jamie Jackson said:**
> Okay, would one of you 64 bit folks try the following, please?

```

ndiswrapper -r bcmwl5
sudo wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe -O${HOME}/sp33008.exe
cd ~; mkdir bcm4311; mv sp33008.exe bcm4311; cd bcm4311
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl564.sys

```

Then, reboot and see what happens?

If still no luck, could you then report the output of "ndiswrapper -l" again?

I had so much trouble getting Ubuntu on this thing in the first place that when I finally got the right info to make it work, I installed the nearest CD rather than digging for a 64 bit copy.  I'm getting:
> Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4312.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf: Permission denied at /usr/sbin/ndiswrapper-1.9 line 128
couldn't delete /etc/ndiswrapper/bcmwl5: Permission denied
 on the first command.  Should I be running that as 'sudo'?

edit - I tried it as 'sudo' and got through fine.  On the last command, though, I get:
> installing bcmwl564.sys ...
couldn't get manufacturer section - installation may be incomplete


Any idea about that?  Thanks for your help.

---

### Post by fastpakr on 2007-07-30
I installed ndiswrapper 1.47 from [here](http://ubuntuforums.org/showthread.php?p=3089800).  It didn't affect much, other than the error I get when trying to add in the driver is slightly different:
> installing bcmwl564.sys ...
couldn't find SourceDisksFiles section - continuing anyway...
couldn't get manufacturer section - installation may be incomplete


'sudo ndiswrapper -l' returns:
> bcmwl564.sys : invalid driver!


Hopefully that helps somehow...

---

### Post by Jamie Jackson on 2007-07-30
> **fastpakr said:**
> I installed ndiswrapper 1.47 from [here](http://ubuntuforums.org/showthread.php?p=3089800).  It didn't affect much, other than the error I get when trying to add in the driver is slightly different:

Hopefully that helps somehow...

Yeah, I think I led you astray before, with the *.sys suggestion. Now that you've got ndiswrapper compiled, though, could you try this again?

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo ndiswrapper -m
```

Then reboot, and report the output of "ndiswrapper -l" and "ndiswrapper -v" if it's not working?

---

### Post by kevdog on 2007-07-30
Can I jump in for a second and ask for clarification.  You are using 64 bit driver with a 32 version of Ubuntu??

---

### Post by fastpakr on 2007-07-30
> **Jamie Jackson said:**
> Yeah, I think I led you astray before, with the *.sys suggestion. Now that you've got ndiswrapper compiled, though, could you try this again?

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo ndiswrapper -m
```

Then reboot, and report the output of "ndiswrapper -l" and "ndiswrapper -v" if it's not working?

Worked like a charm - thank you much!  Between this and the other fix last night to get this thing on Ubuntu in the first place, I'm happy!

---

### Post by Jamie Jackson on 2007-07-30
> **fastpakr said:**
> Worked like a charm - thank you much!  Between this and the other fix last night to get this thing on Ubuntu in the first place, I'm happy!

Interesting, so for whatever reason, it seems that your machine requires a compiled ndiswrapper. I'll make a note on the wiki...

---

### Post by Jamasony on 2007-07-30
Excellent!  I have been struggling with the same problem (same laptop as the other two), I'll try this out this evening.  Nice job guys :)

---

### Post by Jamie Jackson on 2007-07-30
> **Jamasony said:**
> Excellent!  I have been struggling with the same problem (same laptop as the other two), I'll try this out this evening.  Nice job guys :)

I've added instructions the to the [no-fluff howto]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") to account for the extra steps needed for the Compaq F572US.

Please follow those instructions, and let me know how it goes. Also, please report back as to whether you're running the 64 bit OS, or if you're running the 32 bit OS on your 64 bit processor, as fastpakr was.

---

### Post by fastpakr on 2007-07-30
At this rate, I'm going to be rebuilding the laptop in a couple of weeks since Compaq is planning to flash it (against my wishes) when I send it in for work.  I may toss the 64 bit OS on when I get it back just for testing if nobody else has been able to by then.  I will say that the simplicity of the 32 bit software installs was a breath of fresh air.  I've been able to get most everything working on my 64 bit installation on the desktop, but some things have required investing a lot of time into research, trial, and error.

Thanks again for all your help on this!

---

### Post by Jamie Jackson on 2007-07-30
You're welcome, I'm glad we got it working. :)

---

### Post by Jamasony on 2007-07-30
Well, I'm sure I'm close, just not quite there yet.  I'm using the 64-bit installation.  I went through the no-fluff install from top to bottom, and when I got to the part "Remove Stock ndiswrapper" had trouble:

jason@jason-laptop:~$ sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.

I don't think I had any trouble in the first section, so I'm not sure why I got this, perhaps i did do something wrong somewhere.

I just continued from there, and got the following:
 sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed

I'll try again from the top and see if I get the same thing.  also, is there a quick way to just remove all the ndiswrapper stuff and start over?  I'm quite new to linux and have had trouble doing it, so I've just reinstalled the OS each time.

Here are a few outputs that might help (ndiswrapper -l and -v, and -r bcmwl5):
jason@jason-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
jason@jason-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.47
vermagic:       2.6.20-15-generic SMP mod_unload 
jason@jason-laptop:~$ ndiswrapper -r bcmwl5
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied at /usr/sbin/ndiswrapper line 126
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4311.5.conf: Permission denied at /usr/sbin/ndiswrapper line 126
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied at /usr/sbin/ndiswrapper line 126
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied at /usr/sbin/ndiswrapper line 126
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied at /usr/sbin/ndiswrapper line 126
Can't unlink file /etc/ndiswrapper/bcmwl5/14E4:4312.5.conf: Permission denied at /usr/sbin/ndiswrapper line 126
couldn't delete /etc/ndiswrapper/bcmwl5: Permission denied

Thanks for all the help!

Edit:  I tried sudo ndiswrapper -r bcmwl5, removed it fine.  Got the same error when I tried sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.  I went through the steps from there down again, with no luck.

---

### Post by kevdog on 2007-07-31
Isnt this a bcm43xx thread.... Oh well I digress

Its 
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5

Try not to confuse the two.  As far as removing the stock ndiswrapper, you better take a look at this page:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

---

### Post by igeterrors on 2007-07-31
A bit frustrated right now as I went straight from installing Feisty to setting up wireless and the "5 minutes" method failed miserably:

```
~$ sudo apt-get install ndiswrapper-utils-1.9 cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract

```

Then:
```
~$ sudo modprobe -r bcmwl5 
FATAL: Module bcmwl5 not found.

```

Obviously I'm missing some files or something.  It sure would be nice if one Feisty install contained all the same files as every other install.

---

### Post by kevdog on 2007-07-31
Its
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5

---

### Post by Jamasony on 2007-07-31
> **igeterrors said:**
> A bit frustrated right now as I went straight from installing Feisty to setting up wireless and the "5 minutes" method failed miserably:

```
~$ sudo apt-get install ndiswrapper-utils-1.9 cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract

```

Then:
```
~$ sudo modprobe -r bcmwl5 
FATAL: Module bcmwl5 not found.

```

Obviously I'm missing some files or something.  It sure would be nice if one Feisty install contained all the same files as every other install.

I had to install cabextract first as well.

Thanks Kev for your response, I'll see if that works.

---

### Post by Jamie Jackson on 2007-07-31
> **kevdog said:**
> Its
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5

Whoops, thanks, I changed it from:

```
sudo modprobe -r bcmwl5 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
```
to:

```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
```

How's that look? I can't test at the moment...

---

### Post by Jamie Jackson on 2007-07-31
> **igeterrors said:**
> A bit frustrated right now as I went straight from installing Feisty to setting up wireless and the "5 minutes" method failed miserably:

```
~$ sudo apt-get install ndiswrapper-utils-1.9 cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cabextract

```

Then:
```
~$ sudo modprobe -r bcmwl5 
FATAL: Module bcmwl5 not found.

```

Obviously I'm missing some files or something.  It sure would be nice if one Feisty install contained all the same files as every other install.

I had thought universe was enabled in a fresh install, but maybe that's not (always?) the case.

Here's what I added to the wiki: 
[Note, if you get "Couldn't find package cabextract" after line 2, then go to Synaptic and enable the "universe" repository. (System >> Administrator >> Synaptic Package Manager >> Settings >> Repositories >> Ubuntu Software (Tab) >> Check "Community-maintained Open Source Software; Click "Close" button of "Software Sources" dialog; Click Synaptic's "Reload" button; Close Synaptic. Then, re-run line two.]

I added some instructions for enabling "universe" through Synaptic, because I couldn't think of a concise and reliable way to explain the edit needed to sources.list. If anyone has instructions that meet those requirements, please let me know.

---

### Post by soadownz on 2007-08-01
Hmm, this method seemed to work fine for me, but it turns out i'm having the same issues as the other bloke; I can see wireless networks but am only able to connect with WEP security not WPA. This is from a clean install as well.

Anyone know of a fix for this or can point me in the right direction?

---

### Post by fastpakr on 2007-08-01
I'm not sure why you can't connect with WPA as it worked from the beginning for me.  However, I will say that my wireless connectivity is about as flaky as it gets - the entire connection drops fairly frequently, and I seem to be getting minor hiccups often enough that I can't maintain a VPN connection across wireless for more than a minute without it inexplicably dropping the tunnel.

---

### Post by Jamie Jackson on 2007-08-01
> **soadownz said:**
> Hmm, this method seemed to work fine for me, but it turns out i'm having the same issues as the other bloke; I can see wireless networks but am only able to connect with WEP security not WPA. This is from a clean install as well.

Anyone know of a fix for this or can point me in the right direction?

Let's start with the basics. Please send the output of the following commands:

```
ndiswrapper -l
cat /etc/network/interfaces
grep bcm /etc/modprobe.d/blacklist
grep ndiswrapper /etc/modules
cat /etc/default/wpasupplicant
lsmod | grep ndiswrapper
```

---

### Post by Jamie Jackson on 2007-08-01
> **fastpakr said:**
> I'm not sure why you can't connect with WPA as it worked from the beginning for me.  However, I will say that my wireless connectivity is about as flaky as it gets - the entire connection drops fairly frequently, and I seem to be getting minor hiccups often enough that I can't maintain a VPN connection across wireless for more than a minute without it inexplicably dropping the tunnel.

How was the wireless under Windows (assuming you've tried that)? With some routers, I've had problems that were unrelated to the client, so I'm trying to rule that out...

---

### Post by fastpakr on 2007-08-01
> **Jamie Jackson said:**
> How was the wireless under Windows (assuming you've tried that)? With some routers, I've had problems that were unrelated to the client, so I'm trying to rule that out...

Never had a chance to try it - I think I booted this laptop once under Windows before blasting it.  However, I'll be sending it in for repair (bad power jack) today or tomorrow and they're going to throw Windows back on it.  I might give it a try when it comes back to see how it behaves before reinstalling Ubuntu.

---

### Post by Snipersnest on 2007-08-01
Just a quick note. I'm using an HP dv9010us laptop with bcm4311 ..this tutorial did  not work for me because I have to load the system with noacpi . The only way I was able to get my wireless work was to use Gusty Gibbon (I'm guessing because of the newer kernel) and by using fwcutter on a fresh install.

But I did try your tutorial it was so easy but I just got to many errors and conflicts because of noacpi :( Thank you.

---

### Post by Jamie Jackson on 2007-08-01
> **Snipersnest said:**
> Just a quick note. I'm using an HP dv9010us laptop with bcm4311 ..this tutorial did  not work for me because I have to load the system with noacpi . The only way I was able to get my wireless work was to use Gusty Gibbon (I'm guessing because of the newer kernel) and by using fwcutter on a fresh install.

But I did try your tutorial it was so easy but I just got to many errors and conflicts because of noacpi :( Thank you.

Well, that's lame. I'll add your experience as a failure to the WIki. Do you happen to remember at which point during the tutorial you started to get the errors?

---

### Post by Jamie Jackson on 2007-08-02
I added instructions for the BCM4318 (which doesn't work well with the BCM4311 drivers). I don't have a BCM4318, so if you do, let me know how it goes (or doesn't).

---

### Post by Snipersnest on 2007-08-02
**Jamie Jackson - this tutorial now works for me. But not for Ubuntu 7.04.  It works for me on Ubuntu 7.10 with the 2.6.22 kernel and NDISwrapper 1.48rc1 compiled from source. Gusty also uses WPA_Supplicant in the Network Manager so its as easy as Windows to setup.**

I don't recall seeing WPA_Supplicant built in Network Manager on Fiesty Fawn.

I found that in my case the 2.6.20-15/16 kernel and having to use noacpi makes ndiswrapper incompatible. This can be fixed by compiling a new 2.6.22 kernel OR wait till October and install Gusty Gibbon 7.10. If your feeling adventurous I guess you could try Gusty like I did. It fixed my problems.

Now maybe I can help a few other people from my expierence thus far.

---

### Post by Jamie Jackson on 2007-08-02
Snipersnest,

Thanks for the follow up, I'm glad you got it working. I've updated the wiki with your notes, for other potential noacpi folks.

---

### Post by muppis on 2007-08-04
Worked for me, or finds my router at least. Didn't connect, but Windows has also connection difficulties so I don't think problem is in this.  Waiting for an extra antenna to make it sure.
My sys:  Buffalo Tech WLI2-PCI-G54S ( with Broadcom 4306 -chip) with  2.6.20-16-generic kernel and Ubuntu 7.04

---

### Post by jamvegan on 2007-08-05
Fresh install of Feisty on a Compaq Presario 2500 with Broadcom BCM4306.

I followed the quick directions, which did not work for me (at least, I could not connect to the network--the device and driver were apparently recognized by Network Manager).  I then tried the compilation method, with the same results.

Then I installed wifi-radar, and connected with no problem.  I should have tried that before I did the compilation, since I suspect that Network Manager was the problem all along.  I now recall that with a previous Ubuntu install I could only connect to unsecured networks with Network Manager, and had to use wifi-radar to connect with WEP.  This time, Network Manager wouldn't even connect to an unsecured network.

---

### Post by Jamie Jackson on 2007-08-05
> **jamvegan said:**
> Fresh install of Feisty on a Compaq Presario 2500 with Broadcom BCM4306.

I followed the quick directions, which did not work for me (at least, I could not connect to the network--the device and driver were apparently recognized by Network Manager).  I then tried the compilation method, with the same results.

Then I installed wifi-radar, and connected with no problem.  I should have tried that before I did the compilation, since I suspect that Network Manager was the problem all along.  I now recall that with a previous Ubuntu install I could only connect to unsecured networks with Network Manager, and had to use wifi-radar to connect with WEP.  This time, Network Manager wouldn't even connect to an unsecured network.

I'm a stumped as to why you might be able to connect with wifi-radar and not NeworkManager.

If you get a chance, could you post the output of "cat /etc/iftab" and  "iwconfig"

---

### Post by fbati on 2007-08-06
Wow, very easy to use directions and it worked perfectly. All what I tried before this was to no aviail. Thanks!

---

### Post by DarkW0lf on 2007-08-07
I am one of the other ones with the Compaq Presario F572

I have 64 bit xubuntu on the 64 bit processor, and the INF and SYS file from the original Vista partition. Booting without the noapic command (but seems card may still be disabled, orange indicator lit on card).

Just a little clarification, what are the 64 bit variant instructions for no fluff install.
I'll try no fluff first and compile if that doesn't work.

---

### Post by Jamie Jackson on 2007-08-07
> **DarkW0lf said:**
> I am one of the other ones with the Compaq Presario F572

I have 64 bit xubuntu on the 64 bit processor, and the INF and SYS file from the original Vista partition. Booting without the noapic command (but seems card may still be disabled, orange indicator lit on card).

Just a little clarification, what are the 64 bit variant instructions for no fluff install.
I'll try no fluff first and compile if that doesn't work.

As far as I know so far, there are no special instructions needed for 64 bit.

Also, I can't vouch for the Vista drivers, so I would simply try the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") instructions. 

See if you have any success with the packaged ndiswrapper (the short instructions), but according to others' F572 experience, you'll probably have to continue on to installing ndiswrapper from source (the extended instructions).

Let us know how it goes. Good luck!

---

### Post by fastpakr on 2007-08-07
I do not suggest usign the Vista drivers - I tried the BCMWL6.inf file on my own system after getting bcmwl5 working, and on reboot I don't see the wireless card listed in network manager.

---

### Post by DarkW0lf on 2007-08-08
Followed the no_fluff howto.

Now I need to check the card ( it is still orange if that means anything anymore :) )
xubuntu does not have the network manager that I can find (just the admin tool)
I don't care if I need to do this manually instead of the manager connecting.

But I cannot find a wlan0 or eth1 device, what output should I post ?

---

### Post by Jamie Jackson on 2007-08-08
> **DarkW0lf said:**
> Followed the no_fluff howto.

Now I need to check the card ( it is still orange if that means anything anymore :) )
xubuntu does not have the network manager that I can find (just the admin tool)
I don't care if I need to do this manually instead of the manager connecting.

But I cannot find a wlan0 or eth1 device, what output should I post ?

Let's quickly try the NetworkManager route:

Please try [these instructions]("http://ubuntuforums.org/showthread.php?t=239178") for getting NetworkManager going in Xubuntu.

Let us know what happens...

Oh, and please post the output of iwconfig?

---

### Post by blackscribe on 2007-08-08
Yes! Yes! Yes!

After almost deciding to try MEPIS instead of Ubuntu because it seemed like it was such a hassle to get my wireless card working, I decided to give it one more try.  After a little bit of searching I came across this How To.  I followed all the instructions to the letter and did not have to compile anything.

I rebooted and was able to connect via my wireless card.  I then, out of curiosity, went over to the Speakeasy site to test my speed.  My speed was off the charts!  (Over 10000 kbps download and nearly 1600 kbps upload)  With my previous Windows XP set-up I never went over 6000 kbps download.  I am so hyped now.

The reason I gave Ubuntu another try was that the community support seemed so deep and extensive, and threads like this proved my initial impression to be true.  Plus, Ubuntu has a much cooler logo!  Rock on, you Ubuntuans!!

---

### Post by Jamie Jackson on 2007-08-08
Congrats, blackscribe,

For posterity, can you post your laptop make & model and card model? Also, are you running Ubuntu (Feisty?) 32 bit?

---

### Post by boomcat on 2007-08-10
Specs: T20 Thinkpad, Pentium III at 700 mHz, 256M RAM, 100G HD, Feisty Faun i86 clean install, no other OS on this machine, Linksys WPC54G V3 PCMCIA wireless card.

Home network using static Ips and a Linksys WRT54G router and a mixed bag of wired and wireless Win 2K PCs, a wireless printer and even an Xbox 360.

I followed the instructions here: 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
and it worked beautifully. My card uses the BCM4318 chipset, so I used step 2b.

There is a LOT of info on the Web on how to do this and a lot of it is stale. One particular procedure was going beautifully until it turned up a 404 error: Google had moved the file!

Long story short, my formerly worthless wireless card is now working great!

---

### Post by Jamie Jackson on 2007-08-10
> **boomcat said:**
> Home network using static Ips and a Linksys WRT54G

Thanks for the detailed report!

Site note: I have had issues connecting to WRT54G (slow Internet surfing, etc.).  I'm at a beach cottage right now, and we've got a WRT54G v6 here. I had the same issues with it, but I hacked the router and installed DD-WRT (micro) on it. Internet's been fine ever since. I'm not sure what the sticking point is on some stock WRT54G routers, though.

---

### Post by DarkW0lf on 2007-08-11
Stuck in circular hell

network manager gnome relies on libbonobo2 and libbonobo2-common
And those two depend on each other (damn circular dependencies)

Otherwise I have the network manager (but not gnome applet) installed

iwconfig reports that there are no wireless extansions for either lo or eth0.

---

### Post by Jamie Jackson on 2007-08-11
> **DarkW0lf said:**
> iwconfig reports that there are no wireless extansions for either lo or eth0.

Just to be clear: My wireless happens to be eth1. Are you not getting any wireless info from any interface?

```
guest@mercury:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=24 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

```

---

### Post by DarkW0lf on 2007-08-12
Nope none (wireless device is not listed)

lo is the loopback and eth0 is my wired card

Guess next step is to to compile ndiswrapper

---

### Post by Jamie Jackson on 2007-08-12
Can you post the output of 

dmesg | egrep -i "ndis"
and
lspci | egrep -i "(broadcom|wireless)"

Otherwise, sure, let's see what happens after a compilation...

---

### Post by DarkW0lf on 2007-08-13
outputs of dmesg and lspci attached

dmesg:

```

dmesg | egrep -i "ndis"
[   41.175872] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   41.287261] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   41.288759] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   41.294587] ndiswrapper (NdisWriteErrorLogEntry:231): log: C000138D, count: 1, return_address: ffffffff882ef8be
[   41.294592] ndiswrapper (NdisWriteErrorLogEntry:234): code: 0x10e
[   41.294602] ndiswrapper (miniport_init:275): couldn't initialize device: C0000001
[   41.294609] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
[   41.294628] ndiswrapper (miniport_halt:339): device ffff8100348aa500 is not initialized - not halting
[   41.294635] ndiswrapper: device eth%d removed
[   41.294656] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[   41.296150] usbcore: registered new interface driver ndiswrapper


```

lspci:

```

lspci | egrep -i "(broadcom|wireless)"
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)

```

---

### Post by Jamie Jackson on 2007-08-13
Darkwolf,

Yeah, ndiswrapper's not happy. Had you tried any other tutorials before this one? 

If so, you might want to try the "Remove Stock ndiswrapper" instructions (on the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")) and start again. 

If not, I guess compiling ndiswrapper's the next step.

---

### Post by fastpakr on 2007-08-16
My success story with the F572US isn't all that successful...

When connected to a wireless network, the system randomly locks up SOLID.  I can't move the mouse, hit Ctrl-Alt-F1/Backspc, ping it from another pc, or do anything that indicates it's remotely alive.

Beyond that, I can't seem to get more than about 80% successful ping packets even when 4 feet from the AP.  No explanation - it indicates 100% signal and drops packets.  I tried dumping WPA encryption for WEP with no change (other than I can't use network-manager to connect now and seem to be forced into a CLI connection).

Tried swapping to a Gigabyte card with an atheros chipset only to find out that Compaq whitelists a few cards and won't allow anything else.  Doesn't even boot with the new card...

---

### Post by Jamie Jackson on 2007-08-16
I went to look at an [old bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57355") I remembered regarding nvidia conflicts with the 4311, but it seems it's resolved. This is just a shot in the dark (I'm out of my element here), but do you see any IRQ issues in dmesg, that might lead us to believe that it's conflicting with, say, nvidia drivers?

dmesg | grep -i irq

---

### Post by fastpakr on 2007-08-16
Wow - good call (and I'm an IDIOT).  I do occasionally get errors from dmesg when in the terminal emulator indicating that IRQ7 has been disabled.  I don't have the laptop handy, but I'll get the message later and look it up.  That's a message I kept forgetting to research more in the midst of all the other little things I've had trouble with on the laptop.  For whatever reason I didn't think to tie it into the wireless problems.

---

### Post by fastpakr on 2007-08-16
OK, skimmed through the whole read.  I'm obviously on the latest Feisty kernel, so that issue ought to be resolved as you said.  I'll take a look when I go home for lunch and try to get a copy of the error.

---

### Post by fastpakr on 2007-08-16
Crap.  Thought I'd try fwcutter instead of ndiswrapper to see if it eliminated the problem, but fwcutter is [broken](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/127624).    I swear this laptop is destined to make me lose it.  :-)

---

### Post by ctt1wbw on 2007-08-16
Sweet!  It works like a charm!

---

### Post by Jamie Jackson on 2007-08-16
> **fastpakr said:**
> Crap.  Thought I'd try fwcutter instead of ndiswrapper to see if it eliminated the problem, but fwcutter is [broken](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/127624).    I swear this laptop is destined to make me lose it.  :-)

Coincidentally, a fix was posted to that bug ticket after you posted this. Does that help you with fwcutter? FWIW, I hear fwcutter has reduced bandwidth, but it sounds like anything (stable) will do better that what you have now...

BTW, what happened with the IRQ dmesg stuff? Did you find that wasn't an issue?

---

### Post by Jamie Jackson on 2007-08-16
> **ctt1wbw said:**
> Sweet!  It works like a charm!

Good to hear! Did you have to compile ndiswrapper, or not?  Also, would you mind posting your system specs and wireless model? Finally, are you really still on Edgy, as your profile claims, or are you on Feisty now?

---

### Post by ctt1wbw on 2007-08-16
> **Jamie Jackson said:**
> Good to hear! Did you have to compile ndiswrapper, or not?  Also, would you mind posting your system specs and wireless model? Finally, are you really still on Edgy, as your profile claims, or are you on Feisty now?

Oh no, I didn't have to compile ndiswrapper.  And I have the broadcom 4318 chip.  Worked the first time.

And I am using Ubuntu 7.04 now.  I guess I should change it, huh?

I have an HP Pavillion dv8000 laptop.

---

### Post by Jamie Jackson on 2007-08-16
> **ctt1wbw said:**
> Oh no, I didn't have to compile ndiswrapper.  And I have the broadcom 4318 chip.  Worked the first time.

And I am using Ubuntu 7.04 now.  I guess I should change it, huh?

I have an HP Pavillion dv8000 laptop.

Got it, thanks!

---

### Post by fastpakr on 2007-08-16
> **Jamie Jackson said:**
> Coincidentally, a fix was posted to that bug ticket after you posted this. Does that help you with fwcutter? FWIW, I hear fwcutter has reduced bandwidth, but it sounds like anything (stable) will do better that what you have now...

BTW, what happened with the IRQ dmesg stuff? Did you find that wasn't an issue?

I'm not sure I follow how to proceed with that fix...  However, I did follow the 'if that doesn't work' line from [url=https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty]these[/i] instructions and got as far as the card being detected.   I get 'no scan results' under 'sudo iwlist scanning' for the eth1 interface.  It shows up under iwconfig as a Broadcom 4311...  Nothing using network manager.

I was wrong about it being dmesg.  Here's what I get:
> Message from syslogd@cjohnson-laptop at Thu Aug 16 17:40:06 2007 ...
cjohnson-laptop kernel: [   88.384000] Disabling IRQ #7

---

### Post by DarkW0lf on 2007-08-17
I traced IRQ 7 to USB1 (i'll need to look to see what is the controller)
(i found it when using lshw command from a wifi troubleshooter, killing two birds :-) )
not sure why that may be an issue and I don't seem to have a problem with any usb ports.
I'll try all of them later but haven't had any problem with at least two.

Jamie: your compile instructions, how much of that needs to be repeated when the kernel is updated ? And do i need to recompile for every kernel change ?
I cleaned up and reran your no-fluff instructions and ended up with the same results.

I have compiled an Intel536 driver for another machine and don't need to recompile for a change in the last digit ie 2.6.20-xx (I never needed to recompile for the xx part just reinstall) Same condition for compiling ndiswrapper ?

---

### Post by ctt1wbw on 2007-08-17
> **Jamie Jackson said:**
> Got it, thanks!

A few questions, though.  Do you have to redo this for each kernel upgrade?  And what about when Gutsy is released?

---

### Post by DarkW0lf on 2007-08-17
Same output with compiled ndiswrapper.

I'll see if it likes the Vista driver better.

dmesg:
```

[   33.127931] ndiswrapper version 1.47 loaded (smp=yes)
[   33.206680] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   33.208189] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   33.213979] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff882eb80e
[   33.213984] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[   33.213995] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   33.214001] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   33.214013] ndiswrapper (mp_halt:258): device ffff810032daa500 is not initialized - not halting
[   33.214022] ndiswrapper: device eth%d removed
[   33.214042] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[   33.214086] usbcore: registered new interface driver ndiswrapper

```

lspci:
```

03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)

```

---

### Post by DarkW0lf on 2007-08-17
Still a no go here is output from using Vista driver.
That was a stupid idea :(
Anyway, it's look ndis still won't load the driver and there is still no wireless device listed in iwconfig or in the Network Admin app

dmesg:
```

[   40.122542] ndiswrapper version 1.47 loaded (smp=yes)
[   40.211595] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   40.211609] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   40.211616] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   40.211626] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   40.211641] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   40.211649] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   40.211661] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   40.211675] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   40.211686] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   40.211696] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   40.211706] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   40.211715] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   40.211726] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   40.211733] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   40.211741] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   40.211748] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   40.211765] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   40.211773] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   40.211781] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   40.211789] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   40.211796] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   40.211807] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   40.211815] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   40.211823] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   40.211831] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   40.211835] ndiswrapper (load_sys_files:216): couldn't prepare driver 'bcmwl6'
[   40.212357] ndiswrapper (load_wrap_driver:118): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   40.212416] usbcore: registered new interface driver ndiswrapper

```

lspci:
```

03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)

```

---

### Post by Jamie Jackson on 2007-08-17
Darkwolf and/or faskpakr,

I certainly could be wrong, but my suspicions revolve around IRQ problems.
[INDENT]
**tizbad99's sixth post on [this  thread]("http://forum.defcon.org/archive/index.php/t-5136.html")**:
"when ndiswrapper shows errors in dmesg which say somthing like "windows drivers couldnt load the device" and then it cites an error code 22.

I looked it up in the ndiswrapper FAQ and it says the following, if the error code is present then it means that there is an irq problem. It recommends looking to see what is using what interrupts and stuff like that and then to free it up. ALso it mentions check your bios and acpi settings to see how irq are assigned."
[ed: I can't find the referenced docs, unfortunately.]
[/INDENT]

[INDENT][**Ndiswrapper Docs:**]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/")
If, instead, the module loading never finishes or immediately you see &#8220;Disabling IRQ&#8221;, then you have issues with interrupts in the kernel (nothing ndiswrapper can do about it). You may try booting with &#8220;acpi=noirq&#8221; if ACPI is being used. Alternately, try a different kernel or disable ACPI. [/INDENT]

Could you run this (I hope I got the syntax right), so we can see any potential irq messages along with ndiswrapper messages?
dmesg | egrep -i "(irq|pci|ndis)"

---

### Post by Jamie Jackson on 2007-08-17
DarkW0lf/ctt1wbw

I don't really know the answer to this. My guess is that update revision updates (xx.xx.XX) won't need recompilation, though minor revision updates (xx.XX.xx) will.

---

### Post by Jamie Jackson on 2007-08-17
> **ctt1wbw said:**
> A few questions, though.  Do you have to redo this for each kernel upgrade?  And what about when Gutsy is released?

Oh, I forgot that you didn't have to compile ndiswrapper. So, no, I think when you upgrade to Gutsy, I *think* it will be seamless, but don't hold me to that.

---

### Post by kevdog on 2007-08-17
Since Gusty offers a new kernel version, you will have to add ndiswrapper as a kernel module (sudo modprobe ndiswrapper) with the new release.

---

### Post by fastpakr on 2007-08-17
> **Jamie Jackson said:**
> Darkwolf and/or faskpakr,

I certainly could be wrong, but my suspicions revolve around IRQ problems.
[INDENT]
**tizbad99's sixth post on [this  thread]("http://forum.defcon.org/archive/index.php/t-5136.html")**:
"when ndiswrapper shows errors in dmesg which say somthing like "windows drivers couldnt load the device" and then it cites an error code 22.

I looked it up in the ndiswrapper FAQ and it says the following, if the error code is present then it means that there is an irq problem. It recommends looking to see what is using what interrupts and stuff like that and then to free it up. ALso it mentions check your bios and acpi settings to see how irq are assigned."
[ed: I can't find the referenced docs, unfortunately.]
[/INDENT]

[INDENT][**Ndiswrapper Docs:**]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/")
If, instead, the module loading never finishes or immediately you see &#8220;Disabling IRQ&#8221;, then you have issues with interrupts in the kernel (nothing ndiswrapper can do about it). You may try booting with &#8220;acpi=noirq&#8221; if ACPI is being used. Alternately, try a different kernel or disable ACPI. [/INDENT]

Could you run this (I hope I got the syntax right), so we can see any potential irq messages along with ndiswrapper messages?
dmesg | egrep -i "(irq|pci|ndis)"

Thanks for all your help with this.  I'll try the acpi=noirq boot parameter and see what happens.

Edit:  Tried the boot parameter - I lose wireless by doing that.  The second attachment is the dmesg output with the parameter added...

Edit 2:  Yanked 'acpi=noirq', and also removed 'noapic'.  Initially, I was NEVER able to get the laptop to boot without that specified.  Apparently that's not the case any more?  Not sure what's up with that...  The third dmesg attachment contains the information grabbed with neither acpi=noirq or noapic...  Wireless works in this configuration, although it's still dropping packets constantly.

---

### Post by Jamie Jackson on 2007-08-17
FWIW, I just discovered [this blog post]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated"). It gives instructions on using an updated native module. I haven't tried this method, but it seems promising.

I hope my howto becomes obsolete in Gutsy (final), if the native driver becomes usable. I don't know if this will be the case or not, but I've asked some questions in the comments to try to get some clarification.

Does anyone have any thoughts as to the native driver method vs. the ndiswrapper route?

---

### Post by fastpakr on 2007-08-17
> **Jamie Jackson said:**
> FWIW, I just discovered [this blog post]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated"). It gives instructions on using an updated native module. I haven't tried this method, but it seems promising.

I hope my howto becomes obsolete in Gutsy (final), if the native driver becomes usable. I don't know if this will be the case or not, but I've asked some questions in the comments to try to get some clarification.

Does anyone have any thoughts as to the native driver method vs. the ndiswrapper route?

Using that method, I get 'no scan results' for eth1 (wireless interface).  Your command from before gives the attached output.  Thanks again!

---

### Post by Jamie Jackson on 2007-08-17
fastpakr,

Sorry, I'm not clear on your situation as of your last post. Could you summarize your current status?

Last I knew, you had working wireless, but had a lot of dropped packets. Is this still true? If so, is your throughput satisfactory, despite the dropped packets?

If not, what's the scoop, exactly?

---

### Post by fastpakr on 2007-08-18
First output was with ndiswrapper the way we had it working - dropping 20% or more packets and occasionally locking up, but working.

Second output is with acpi=noirq added as a boot parameter.  ndiswrapper does not work in this configuration.

Third output is after removing both acpi=noirq and noapic.  ndiswrapper works the same as the first output - lossy and slow, but kind of working.

Fourth output is following the thread you linked at linux-geek.org using the native driver.  The laptop sees the wireless card but I get no scan results and all the errors you'll find at the end of the output.

Hope that helps?

---

### Post by josephedwardmartinez on 2007-08-19
I purchased an Acer Aspire 3690-2970 for the mom.  I loaded Ubuntu Feisty flawlessly. I have Feisty installed on 4 system and am determined to get the damn wireless NIC to work.  I have yet to get them to work on either one.

After several hours of research and failures, I found your HowTo.  It was great.  I was able to get the system to recognize the NIC and find the access point.  The only defect is that it does not want to connect.  I've seen a few posts mentioning the same problem without resolution.

Can you please help a brother out?  I need to get this system to mom within the next few days or she'll beat my ****.

I also downloading Wifi Radar which also finds my access point but again, does not want to connect. I've also shut off WEP and still no luck.

Anything reply would be awesome. Thank you for your time and awesome dedication.

---

### Post by Jamie Jackson on 2007-08-19
We've gotta work fast to avoid the beat-down.

What do you have in there?
```
lspci | egrep -i '(broad|wireless)'
```

---

### Post by josephedwardmartinez on 2007-08-19
Jamie,

Here's what I have:

dolores@dolores-laptop:~$ lspci | egrep -i '(broad|wireless)'
05:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

---

### Post by DarkW0lf on 2007-08-19
IRQ 7 is USB1 that I tracked to be the usb port found on the left side of the laptop (the back one), this port is not hot-swappable but the others are. I don't know why acpi is disabling that port's IRQ. The port works but I have to insert a device then boot the PC and I cannot eject the device afterwards (have to shutdown then remove).

Except just now I couldn't hot-swap any port (??). Was trying to copy the dmesg output to my usb drive.

*Warning lots of output*:)

ndiswrapper -i bcmwl5.inf:
```

installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

```

dmesg:
```

[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[   22.150297] spurious 8259A interrupt: IRQ7.
[   22.407907] ACPI: bus type pci registered
[   22.407914] PCI: Using configuration type 1
[   22.415175] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.415181] PCI: Probing PCI hardware (bus 00)
[   22.415383] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   22.416501] PCI: Transparent bridge - 0000:00:10.0
[   22.416537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.459266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   22.460787] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   22.460991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   22.461399] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.461751] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   22.462095] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.462446] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.462791] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.463139] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.463484] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 *11 14 15)
[   22.463830] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.464176] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   22.464526] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   22.464914] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   22.465262] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   22.465606] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   22.465953] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.466296] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.466644] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.466988] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   22.467350] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   22.467695] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   22.471369] PCI: Using ACPI for IRQ routing
[   22.471374] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.471492] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   22.473556] PCI: Bridge: 0000:00:02.0
[   22.473676] PCI: Bridge: 0000:00:03.0
[   22.473686] PCI: Bridge: 0000:00:10.0
[   22.473705] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   22.473712] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   22.473720] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   23.451813] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   23.451839] Allocate Port Service[0000:00:02.0:pcie00]
[   23.451916] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   23.451941] Allocate Port Service[0000:00:03.0:pcie00]
[   23.485726] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.487840] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   23.502631] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.502639] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.354527] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   25.354862] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   25.354865] PCI: setting IRQ 5 as level-triggered
[   25.354869] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   25.354896] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.354960] ata1: SATA max UDMA/133 cmd 0x00000000000130c0 ctl 0x00000000000130b6 bmdma 0x0000000000013090 irq 5
[   25.354991] ata2: SATA max UDMA/133 cmd 0x00000000000130b8 ctl 0x00000000000130b2 bmdma 0x0000000000013098 irq 5
[   26.163108] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   26.163134] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   27.581937] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.582942] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   27.582946] PCI: setting IRQ 11 as level-triggered
[   27.582951] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   27.582968] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.583183] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xb0004000
[   27.740014] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   27.740019] PCI: setting IRQ 7 as level-triggered
[   27.740024] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   27.740041] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   27.740122] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   27.740132] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xb0005000
[   27.843904] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   27.843909] PCI: setting IRQ 10 as level-triggered
[   27.843914] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   27.843921] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   37.627531] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.630196] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.094093] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   38.094098] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[   38.094121] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   39.028392] ndiswrapper version 1.47 loaded (smp=yes)
[   39.113045] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   39.114529] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   39.115155] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 10
[   39.115159] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 10 (level, low) -> IRQ 10
[   39.115198] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   39.120309] ndiswrapper (NdisWriteErrorLogEntry:192): log: C000138D, count: 1, return_address: ffffffff882ed80e
[   39.120314] ndiswrapper (NdisWriteErrorLogEntry:195): code: 0x10e
[   39.120324] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   39.120331] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   39.120343] ndiswrapper (mp_halt:258): device ffff810034962500 is not initialized - not halting
[   39.120352] ndiswrapper: device eth%d removed
[   39.120360] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[   39.120372] ndiswrapper: probe of 0000:03:00.0 failed with error -22
[   39.120416] usbcore: registered new interface driver ndiswrapper
[  174.707706] irq 7: nobody cared (try booting with the "irqpoll" option)
[  174.707716]  <IRQ>  [<ffffffff802bd285>] __report_bad_irq+0x35/0x90
[  174.707771]  [<ffffffff88044465>] :usbcore:usb_hcd_irq+0x25/0x60
[  174.707781]  [<ffffffff802be243>] handle_level_irq+0xe3/0x140
[  174.707787]  [<ffffffff8026223c>] call_softirq+0x1c/0x28
[  174.707796]  [<ffffffff80270189>] do_IRQ+0x89/0x100
[  174.707867] [<ffffffff88044440>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  174.707883] Disabling IRQ #7

```

---

### Post by Jamie Jackson on 2007-08-19
> **DarkW0lf said:**
> 
ndiswrapper -i bcmwl5.inf:
```

installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
...

```


This part is perfectly normal. However, that IRQ thing is a problem. Unfortunately, I don't know anything about resolving IRQ issues in Linux.

Are you running with any added boot options right now? If so, you could try booting without them. If not, you could experiment with adding some, as in [this post]("http://ubuntuforums.org/showpost.php?p=3208790&postcount=113").

---

### Post by Jamie Jackson on 2007-08-19
While my method works well for me, I'm still searching for the "perfect" way to configure these cards (with the right balance between performance and ease of configuration).

In that vein:

> **Jamie Jackson said:**
> FWIW, I just discovered [this blog post]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated"). It gives instructions on using an updated native module. I haven't tried this method, but it seems promising.

Well, I tried the above method of installing the backported native driver. It is a VERY easy method to implement, but I'm having some major issues with speed and connection reliability. I posted the following as a comment on this guy's blog, but the last two comments that I posted eventually disappeared.

> (Note: Running 2.6.20-16-generic on Feisty 32 bit; Dell D620 with BCM4311/Dell 1390)

ndiswrapper got me max sustained throughput of 23 Mbps through WPA and 25 Mbps unencrypted. (I'm happy with ndiswrapper, but it's a pain to set up, and I'm looking for the "ultimate" way to set up these cards.)

Undid my ndiswrapper config to try your method, then ran
    cd ~
    wget [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)
    sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
    rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb

It works, but now I'm getting between 1 and 2 Mbps with my Laptop inches from my router.
Further, I'm having problems on, say, YouTube: It will buffer and play 10-20 seconds of video and then stop. (This was not a problem with ndiswrapper.)

Any ideas as to why it's so slow and sketchy?

Finally, do you know if your method works for all 43xx cards (e.g., 4318 & 4306)?

---

### Post by schredhead on 2007-08-19
As another new CompaqF572US user, I also struggled with these directions, same error in the log, that the card failed to initialize.  One thing that concerned me was that the date of the bcmwl5 type files from the suggested HP softPaq were form early 2006.  I thought there might be a newer version of the Broadcomm drivers somewhere on the HP support site... and there is, found them looking at Model dv6000t, more or less the same guts as this one.

I substituted sp34152.exe in place of the suggested sp33008.  

I am using 64-bit Feisty on this machine.  Grub boot line includes "noapic irqpoll" at the end.

---

### Post by Jamie Jackson on 2007-08-19
> **schredhead said:**
> As another new CompaqF572US user, I also struggled with these directions, same error in the log, that the card failed to initialize.  One thing that concerned me was that the date of the bcmwl5 type files from the suggested HP softPaq were form early 2006.  I thought there might be a newer version of the Broadcomm drivers somewhere on the HP support site... and there is, found them looking at Model dv6000t, more or less the same guts as this one.

I substituted sp34152.exe in place of the suggested sp33008.  

I am using 64-bit Feisty on this machine.  Grub boot line includes "noapic irqpoll" at the end.

What's the bottom line now?

1. Is it working fine for you with the other driver you found? 
1a. If so, is it dropping packets, or does that look good, too?
2. Are those boot options something you added?
3. Were the boot options the same while you tried both "my" driver *and* your driver?

Thanks for the feedback!

[Note to self: As long as we're looking for updated drivers, why don't we consider [the drivers from Dell]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=LATITUDE%20D620&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136"), which claim to be released 3/23/2007, and whose SYS and INF files are different--as shown by the diff utility--from both mine and schredhead's?)

---

### Post by schredhead on 2007-08-21
1 ) So far so good, in terms of working no dropped packets but I haven't really stressed it either.  However, there does seem to be a sort of instability between wpa_supplicant and something in here.  A fresh connect after boot seems to stay up fine, but if I disconnect and then try to reconnect, sometimes the reconnect will not stay up.  Possibly this is the router because I occasionally have the same issue with a different Centrino based laptop/Windows  machine.  Something gets flaky.   I'll keep an eye on things...  Signal strength seems low compared t other laptops I have...

2) Yes, I added them, irqpoll came out of a reference I got to from this forum, can't quite remember where.....

3) Boot options exactly the same - an obvious signal that the newer driver worked, Wireless light turned from orange to blue shortly after reboot, never saw that with the "older" driver.  This was confirmed in the syslog which no longer had an error indicating a problem bringing the interface up.

Newer drivers might even be better, when I get a chance maybe I'll give it a shot too.

---

### Post by Jamie Jackson on 2007-08-21
Okay, maybe DarkW0lf, or another F72US user, could try this alternative "Step 2," which uses a driver suggested by schredhead.
```

sudo apt-get install cabextract
wget ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe

```

---

### Post by fastpakr on 2007-08-21
I'm pretty sure that I used that driver when getting mine running, but I'll go back and make sure as soon as I get a chance...

---

### Post by RagingOcelot on 2007-08-24
Brilliant!  

sp34152.exe  worked for me where the drivers in your original "...in 5 minutes" post didn't.  I am now an even happier user of a Compaq F572US (using the 64-bit install).  I also have noapic and irqpoll in the kernel boot list.  

I'll have to keep this post updated on my experience (to compare with fastpakr's).  Hopefully, we can iron out his wireless woes.  Thanks everyone!

---

### Post by RagingOcelot on 2007-08-24
Ok, so it hasn't completely been fun and games.  After the first bootup, I had the wireless connection about 5 minutes tops, long enough to write the previous message.  Then, suddenly, nothing - a complete drop-off.  I rebooted and I'm transmitting this after the second bootup.  The connection has now been up around 15 - 20 mins.  I'll see how this goes...

---

### Post by Jamie Jackson on 2007-08-24
> **RagingOcelot said:**
> Ok, so it hasn't completely been fun and games.  After the first bootup, I had the wireless connection about 5 minutes tops, long enough to write the previous message.  Then, suddenly, nothing - a complete drop-off.  I rebooted and I'm transmitting this after the second bootup.  The connection has now been up around 15 - 20 mins.  I'll see how this goes...

Okay, well it sounds like it's a *better* driver for F572US than the first, anyway.

If it drops again, try re-associating with the AP, or restarting network manager:
sudo /etc/dbus-1/event.d/25NetworkManager restart

Could you report the output of "lshw -C network"? I'm just curious...

Side note: I'm experimenting with different versions of ndiswrapper, and currently, I'm using the bleeding edge release. That version of ndiswrapper gives me wireless for 5-15 seconds, then drops it permanently, even though NetworkManager reports that I'm still associated. For me, a re-association or restart of NM does the trick, but again, it's only for a few seconds. So it seems ndiswrapper 1.48rc1 won't work on my system. For me, the stock Ubuntu ndiswrapper ( 1.38 ) from the repos does better.

---

### Post by RagingOcelot on 2007-08-24
output of lshw -C network:

```
*-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:7b:27:79
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=Broadcom,10/12/2006, 4.100.15.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:b8000000-b8003fff irq:10
```

Ever since I booted up today, I haven't been able to connect to the router.  I'm getting these messages in the router's log like, "Wireless PC connected" with my laptop's MAC address but it seems like maybe my router doesn't want to give out a DHCP address.  Can't tell if that's what it really is or not...

NetworkManager restart doesn't help either.

---

### Post by Jamie Jackson on 2007-08-24
Is there anything suspicious in your "dmesg"?

BTW, if/when you get sick of trying ndiswrapper, you can try a completely [different method]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated"). I'm curious as to whether you F572US users would benefit.

If I read the thread right, this will apply to kernel 2.6.20-16, both 32 and 64 bit. (Feel free to sanity check.)

```
# REMOVING PACKAGED (NOT COMPILED) NDISWRAPPER, ETC.
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo rm -r /etc/default/wpasupplicant
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo sh -c "sed '/^blacklist bcm43xx$/d' /etc/modprobe.d/blacklist > /etc/modprobe.d/blacklist.rm; mv /etc/modprobe.d/blacklist.rm /etc/modprobe.d/blacklist"

# INSTALLING THE NATIVE DRIVER STUFF
wget http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo /etc/dbus-1/event.d/25NetworkManager restart
```

If your throughput isn't satisfactory after this, try tweaking the rate. For instance:
```

sudo iwconfig eth1 rate 36M
```

---

### Post by DarkW0lf on 2007-08-24
Jamie the modified step 2 works for me.
I am still using the comiled ndiswrapper so I don't know if the driver would work with stock ndiswrappermpackage. I didn't know how to undo and revert to stock package.

I am not having any dropped packets issue yet, connected to wap @ 24 Mb/s
Network manager is telling me I am connected at 20% (is that signal strength?).

Attached the most recent dmesg output.

There are still IRQ issues, but seems related to usb ports I don't think that is causing any wireless issues. My card works but there is still some flakiness with the hot-swapping usb drives.

Quick note: the latest kernel lets me connect to the WAP but not the internet, seems I don't get an IP lease. Booted to the older kernel and I have an IP now.
I'll keep trying maybe it was a fluke but it did that twice now so that might be something.

Another note: 2.6.20-15 can get a IP lease but 2.6.20-16 connects/detects the WAP but no IP lease.

---

### Post by fastpakr on 2007-08-24
Interesting - so if you start a ping to the router from terminal and let it run for a few minutes, you get 0% packet loss and fairly consistent ping times?  I don't know what's going on here...  I've tried the most recent driver Jamie suggested and I'm still getting the exact same issues.  15% or higher packet loss, with ping times ranging anywhere from 5-400 ms.

---

### Post by Jamie Jackson on 2007-08-24
> **DarkW0lf said:**
> Jamie the modified step 2 works for me.
I am still using the comiled ndiswrapper so I don't know if the driver would work with stock ndiswrappermpackage. I didn't know how to undo and revert to stock package.

I am not having any dropped packets issue yet, connected to wap @ 24 Mb/s
Network manager is telling me I am connected at 20% (is that signal strength?).

Attached the most recent dmesg output.

There are still IRQ issues, but seems related to usb ports I don't think that is causing any wireless issues. My card works but there is still some flakiness with the hot-swapping usb drives.

Quick note: the latest kernel lets me connect to the WAP but not the internet, seems I don't get an IP lease. Booted to the older kernel and I have an IP now.
I'll keep trying maybe it was a fluke but it did that twice now so that might be something.

Another note: 2.6.20-15 can get a IP lease but 2.6.20-16 connects/detects the WAP but no IP lease.

I don't know how to troubleshoot the DHCP stuff. Hopefully somebody can jump in on that one, so you can get back on 2.6.20-16.

Yes, 20% is the signal strength. You should see the same in iwconfig. Is 24Mb/s the tested throughput, or the reported Bit Rate? 24Mb/s happens to be about my max tested bit rate when my signal strength is 100% (laptop ON router).

Unfortunately, at this point, the F572US still seems so dodgy that I hesitate to really "endorse" a procedure for it.

---

### Post by Jamie Jackson on 2007-08-25
I'm off on vacation for a week, so I'll be thinking fishing for a while, instead of Ubuntu. :)

---

### Post by RagingOcelot on 2007-08-25
Thanks for all your help.  I've been running the Feisty 64-bit version for 5-6 hours with no problems with the wireless.  No locking up, just a consistent connection.

Now I have to go figure out why I wanted the hassle of 64-bit.

Happy hooking!

---

### Post by DarkW0lf on 2007-08-25
24 Mb/s is what the network manager reports.
Though after installing updated kernel it is 11 Mb/s for both kernels.
I am going to try again tommorrow and if I remember get some pings for fastpakr.

fastpakr: I custom built ndiswrapper from latest source (1.47) and used the modified step2 Jamie posted above.

Jamie: I know you'll be thinking of us, you'll hook the biggest catfish you've ever seen and it will hit you; 'That's why it doesn't work !!'   :-)

Note: I voted as a partial success. Works compiled from source with that alternate driver but not on the latest kernel.

---

### Post by mootpoint on 2007-08-25
I had a very uneventful install of Linux Mint (Ubuntu Feisty with a few different bells and whistles) this afternoon. I used noapic apci=off irqpoll flags for the install, then took out the apci=off, followed the   modified step 2 (with the newer sp34152.exe driver set). No wireless dropouts or other anomalies so far. I am using a wide open AP for the moment. If I start having issues with WPA later on I'll post, but for now, I'm in the unqualified success category. 

Thanks for paving the nice smooth road in front of me guys!

mootpoint

---

### Post by DarkW0lf on 2007-08-26
Cannot get an IP with latest kernel, doesn't even seem to connect to WAP now.

With 2.6.20-15, there are no dropped packets but there are a few that took a while to respond.

---

### Post by bigbee79 on 2007-08-28
I just registered for the first time on this forum just to leave this message.

I'm another frustrated F572US user, or I was frustrated.  I used the new 2nd step and after rebooting my wireless card is now working for the first time.  Everything seems to be working great.  Thank you so much to everyone on this forum.   I really can't say thank you enough.

I'm using the 64 bit version of Ubuntu and I used the suggested "noapic" during booting and install.  I didn't use the irqpoll one though.  Is that necessary for people with the F572US?  And what exactly would that do?  (And I'm sorry for being so new to all of this.  I promise I'm going to read a good beginners book all about Ubuntu as soon as possible)

---

### Post by mootpoint on 2007-08-30
> **mootpoint said:**
> I had a very uneventful install of Linux Mint (Ubuntu Feisty with a few different bells and whistles) this afternoon. I used noapic apci=off irqpoll flags for the install, then took out the apci=off, followed the   modified step 2 (with the newer sp34152.exe driver set). No wireless dropouts or other anomalies so far. I am using a wide open AP for the moment. If I start having issues with WPA later on I'll post, but for now, I'm in the unqualified success category. 

Thanks for paving the nice smooth road in front of me guys!

mootpoint

All remains well. It also looks like I forgot to note that my laptop is an F572US as well.

Running the current ndiswrapper package from the repos, I have 0 problems with DHCP. And when I looked at Dark's iwconfig output, I noticed that he's connecting at 802.11b, even though the WAP is a .11g. That should not happen; it should connect as g even if the speed is really low due to signal problems. 

I wonder if Dark's issues aren't simply signal strength/interference, something flaky in the firmware on his WAP, or maybe the WAP and the Broadcomm don't play nice together. Any way to test with another WAP Dark? 

m00t

---

### Post by mootpoint on 2007-08-30
> **bigbee79 said:**
> I just registered for the first time on this forum just to leave this message.

I'm another frustrated F572US user, or I was frustrated.  I used the new 2nd step and after rebooting my wireless card is now working for the first time.  Everything seems to be working great.  Thank you so much to everyone on this forum.   I really can't say thank you enough.

I'm using the 64 bit version of Ubuntu and I used the suggested "noapic" during booting and install.  I didn't use the irqpoll one though.

irqpoll, as I understand it, dumbs down how the kernel handles hardware IRQ requests; instead of waiting for the BIOS to say, "Hey, interrupt request from IRQ X," it actively polls each IRQ looking for activity. I saw it recommended on some forum or another when getting ready for my install. When I took it out after my install, I started getting the following at the tail end of my dmesg output about 30 seconds after the bootup completed:

[  235.484000] irq 7: nobody cared (try booting with the "irqpoll" option)
[  235.484000]  [<c012f657>] run_timer_softirq+0x37/0x1a0
[  235.484000]  [<f88a7f32>] usb_hcd_irq+0x22/0x60 [usbcore]
[  235.484000]  [<c0105b70>] do_IRQ+0x40/0x80
[  235.484000] [<f88a7f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  235.484000] Disabling IRQ #7

Doesn't seem to have broken anything, though, so I've left it out. I'm on a 32-bit install with the current 2.6.20-16-generic kernel.

mootpoint

---

### Post by fastpakr on 2007-08-31
Looks like we need to remove my issues from this discussion entirely.  I'm deploying in about two weeks and simply ran out of time to fool with getting Ubuntu running right on the laptop.  I installed XP and all the drivers yesterday.  Got everything working great except wireless.  Turns out that whatever problem I had with the Broadcom card in Linux is a hardware issue that I'm experiencing in Windows as well.  With no warning it will stop being able to transmit data across the connection (even though it indicates that it's still connected), and it could come back in ten minutes, or it might require doing an ipconfig /release to get it back up.  After multiple calls with Compaq last night, I'll be sending it in (again) for repair.

---

### Post by DarkW0lf on 2007-08-31
mootpoint:

Where in my iwconfig I posted does it show I am connecting at 802.11b ?
All I see is a note at the beginning saying IEEE 802.11g.

---

### Post by mootpoint on 2007-08-31
Dark:

I must have been hallucinating; although your link speed is reported as 11 mb/s, .11b ain't in there!

However, there remain items of some concern: Link Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm. The noise is louder than the signal, and the link quality is not good. That's why you're only getting an 11 mb/s connection. 

Can you retest closer to your router?

mootpoint

---

### Post by fastpakr on 2007-08-31
> **mootpoint said:**
> Dark:

I must have been hallucinating; although your link speed is reported as 11 mb/s, .11b ain't in there!

However, there remain items of some concern: Link Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm. The noise is louder than the signal, and the link quality is not good. That's why you're only getting an 11 mb/s connection. 

Can you retest closer to your router?

mootpoint

Huh?  I'll admit that his signal isn't extremely strong, but at -80dBm it's fourty times greater than the noise at -96dBm.

---

### Post by mootpoint on 2007-08-31
Sigh. The - signs .... I guess I do need those bifocals the eye Dr. recommends. 

I'll shut up now before becoming a bigger id10t!

mootpoint

---

### Post by Jamie Jackson on 2007-08-31
> **fastpakr said:**
> Looks like we need to remove my issues from this discussion entirely.  I'm deploying in about two weeks and simply ran out of time to fool with getting Ubuntu running right on the laptop.  I installed XP and all the drivers yesterday.  Got everything working great except wireless.  Turns out that whatever problem I had with the Broadcom card in Linux is a hardware issue that I'm experiencing in Windows as well.  With no warning it will stop being able to transmit data across the connection (even though it indicates that it's still connected), and it could come back in ten minutes, or it might require doing an ipconfig /release to get it back up.  After multiple calls with Compaq last night, I'll be sending it in (again) for repair.

Doh! Sorry to hear that, but thanks for reporting back, it's definitely interesting to compare how the same device works under Windows as compared to Linux. Good luck when you get that poor  laptop back from repair.

---

### Post by Jamie Jackson on 2007-08-31
> **bigbee79 said:**
> I just registered for the first time on this forum just to leave this message.

I'm another frustrated F572US user, or I was frustrated.  I used the new 2nd step and after rebooting my wireless card is now working for the first time.  Everything seems to be working great.  Thank you so much to everyone on this forum.   I really can't say thank you enough.

I'm using the 64 bit version of Ubuntu and I used the suggested "noapic" during booting and install.  I didn't use the irqpoll one though.  Is that necessary for people with the F572US?  And what exactly would that do?  (And I'm sorry for being so new to all of this.  I promise I'm going to read a good beginners book all about Ubuntu as soon as possible)

Thanks for the report. I've added that alternate step 2 to the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#preview"). Oh, and did you have to compile ndiswrapper, or are you set with the repo version?

---

### Post by RagingOcelot on 2007-08-31
> **fastpakr said:**
> Looks like we need to remove my issues from this discussion entirely.  I'm deploying in about two weeks and simply ran out of time to fool with getting Ubuntu running right on the laptop.  I installed XP and all the drivers yesterday.  Got everything working great except wireless.  Turns out that whatever problem I had with the Broadcom card in Linux is a hardware issue that I'm experiencing in Windows as well.  With no warning it will stop being able to transmit data across the connection (even though it indicates that it's still connected), and it could come back in ten minutes, or it might require doing an ipconfig /release to get it back up.  After multiple calls with Compaq last night, I'll be sending it in (again) for repair.

Did you have any chance to boot up into Vista via your recovery DVDs?  Oh wait, were you the one who didn't make them?

It'd be interesting to see if all the problems you had in Ubuntu with the wireless card were also present in Vista.

---

### Post by ctt1wbw on 2007-09-01
I just upgraded to the new kernel and kernel headers and rebooted.  Wifi still works.  =D>

---

### Post by DarkW0lf on 2007-09-01
ctt1wbw:

Are you using the stock ndiswrapper and driver from alternate step 2 ?
Is the new kernel you are using 2.6.20-16.31 ?
I just updated today and it won't get an IP.

moot:

dB are a ratio -3dB would be half power and +3dB would be double.
I am not worried about the connection speed 11 Mb/s is still faster than dial-up.
My issue is it doesn't connect at all under the new kernel (b or g).

I am going to try and see if I need to redo some steps under the new kernel.

Jamie:

In Vista I had the same issue, the card could connect to the WAP but not get an IP for the Internet.

---

### Post by Evil Blu Jedi on 2007-09-01
Another satisfied customer.  Thanks so much for this how-to.  It works great on my HP dv5139 laptop running Feisty 64-bit.

---

### Post by DarkW0lf on 2007-09-01
Jamie I am trying to redo the configuration on the latest kernel.
But it complains that the alias already exists when I run 'sudo ndiswrapper -m'

I am trying to see if those lasts steps after compiling need to be run again on my system for the new kernel, or if I need to recompile again. Either way is there something I need to undo to rerun those last steps.

---

### Post by Jamie Jackson on 2007-09-02
> **DarkW0lf said:**
> Jamie I am trying to redo the configuration on the latest kernel.
But it complains that the alias already exists when I run 'sudo ndiswrapper -m'

I am trying to see if those lasts steps after compiling need to be run again on my system for the new kernel, or if I need to recompile again. Either way is there something I need to undo to rerun those last steps.

I think you just need the following before re-running the post-compilation commands:
```

sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5

```

---

### Post by Jamie Jackson on 2007-09-02
> **Evil Blu Jedi said:**
> Another satisfied customer.  Thanks so much for this how-to.  It works great on my HP dv5139 laptop running Feisty 64-bit.

Great! What version of the device do you have in there? ("lspci | grep Broadcom")

---

### Post by Jamie Jackson on 2007-09-02
> **DarkW0lf said:**
> In Vista I had the same issue, the card could connect to the WAP but not get an IP for the Internet.

Hmm, do other wireless machines have any trouble getting a DHCP lease from that AP?

---

### Post by ctt1wbw on 2007-09-02
> **DarkW0lf said:**
> ctt1wbw:

Are you using the stock ndiswrapper and driver from alternate step 2 ?
Is the new kernel you are using 2.6.20-16.31 ?
I just updated today and it won't get an IP.

moot:

dB are a ratio -3dB would be half power and +3dB would be double.
I am not worried about the connection speed 11 Mb/s is still faster than dial-up.
My issue is it doesn't connect at all under the new kernel (b or g).

I am going to try and see if I need to redo some steps under the new kernel.

Jamie:

In Vista I had the same issue, the card could connect to the WAP but not get an IP for the Internet.

Yeah I'm using the stock stuff from step 2.  And that's my new kernel.  And I started using the Network Selector Panel Applet and the Wifi Radar app to connect to my wireless router.  It works every time.

---

### Post by DarkW0lf on 2007-09-03
> **Jamie Jackson said:**
> Hmm, do other wireless machines have any trouble getting a DHCP lease from that AP?

No just this one.

---

### Post by DarkW0lf on 2007-09-03
Get this, I just rebooted into 2.6.20-16 to redo some post compiling steps.
And guess what, just after loading X, I see a notice that I am connected to the WAP.
?? Your guess is as good as mine ?? (I need a head scratching emote) :confused:

---

### Post by Jamie Jackson on 2007-09-03
Hmm, did you do happen to do any voodoo, such as animal sacrifice or an incantation before rebooting? That's gotta be it. :shock:

---

### Post by zanteian on 2007-09-05
This worked for me with a Belkin F5D7000 PCI card. It has BCM4306 chipset. I am using Ubuntu Feisty Fawn 7.04. Have not got WPA to work. WEP works OK

---

### Post by Jamie Jackson on 2007-09-05
> **zanteian said:**
> This worked for me with a Belkin F5D7000 PCI card. It has BCM4306 chipset. I am using Ubuntu Feisty Fawn 7.04. Have not got WPA to work. WEP works OK

Thanks for the reply. I think it is by default, but do you have wpa_supplicant installed? (Issue "*wpa_supplicant -v*".)

---

### Post by Loatar on 2007-09-05
Thanks for the info.  It worked for me now I'm at 54mps instead of 11.  I'm still not 100% sure exactly what is going on with this OS, but its getting easier.

---

### Post by Jamie Jackson on 2007-09-05
> **Loatar said:**
> Thanks for the info.  It worked for me now I'm at 54mps instead of 11.  I'm still not 100% sure exactly what is going on with this OS, but its getting easier.

Great! Could you post your laptop specs (make, model, wireless brand/chipset) and Ubuntu version, please? Also, if you've tried WPA, let us know how you made out.

---

### Post by may04 on 2007-09-06
I am a new user and installed 7.04 a few times but could not get my Linksys WMP54G to work.  Tonight I reinstalled and right after the updates I copied and pasted the commands, rebooted and opened Wireless Assistant 0.5.5 and it worked.  Thank you

---

### Post by Jamie Jackson on 2007-09-06
> **may04 said:**
> I am a new user and installed 7.04 a few times but could not get my Linksys WMP54G to work.  Tonight I reinstalled and right after the updates I copied and pasted the commands, rebooted and opened Wireless Assistant 0.5.5 and it worked.  Thank you

Congrats! I've added your testimonial to the wiki.

---

### Post by hambudge on 2007-09-08
Success hp dv6000 broadcomwireless 4318 
Ubuntu 7.04 alternative cd (booted via F6 "noapic nolapic" added to command line). 
Great post now off to install my built in webcam ...

---

### Post by YMLiew on 2007-09-08
Wireless work.. finally. B4 I follow those steps, I tried to use ndiswrapper on HP Compaq V3000 WindowXP and Vista 64 bit drivers (bcml5.inf, bcml6.inf).  Did not work for me. Below are my system details :

Ubuntu 7.04, 64 Bit AMD - Desktop 
Compaq Presario V3000(V3010AU) , WLAN : Broadcom BCM4311 KFBG
Working Great - 8/Sep/07 ! 

01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
Linux 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

Good luck for the one still trying !

---

### Post by YMLiew on 2007-09-08
Wireless work.. finally. B4 I follow those steps, I tried to use ndiswrapper on HP Compaq V3000 WindowXP and Vista 64 bit drivers (bcml5.inf, bcml6.inf).  Did not work for me. Below are my system details :

Ubuntu 7.04, 64 Bit AMD - Desktop 
Compaq Presario V3000(V3010AU) , WLAN : Broadcom BCM4311 KFBG
Working Great - 8/Sep/07 ! 

01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
Linux 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

Good luck !

---

### Post by Jamie Jackson on 2007-09-08
Thanks for the detailed feedback, YMLiew and hambudge, I've added your notes to the wiki.

---

### Post by Tonny Hooijer on 2007-09-09
I have a Dell Lattitude D610 with the following wireless device according to lspci : Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

The only thing working for me was the last part, i did have to compile the ndiswrapper...and reboot. But it works now!:D

Thank you very much! As a Linux newbie i couldn't have done this myself.
:popcorn:

---

### Post by Jamie Jackson on 2007-09-09
Tonny, thanks for the feedback. I've added it to the wiki.

---

### Post by him610 on 2007-09-11
Success! :)
Dell Optiplex GX1 with a PII
Linksys WMP54G with Broadcom bcm4306
Xubuntu 7.04 with XFCE
Used Step 2b of the procedure.
No compilation of ndiswrapper was necessary

Thank you to all who have contributed. :KS

---

### Post by Jamie Jackson on 2007-09-11
Congrats, and thanks for all the details! You're up on the wiki.

---

### Post by muppis on 2007-09-12
> **muppis said:**
> Worked for me, or finds my router at least. Didn't connect, but Windows has also connection difficulties so I don't think problem is in this.  Waiting for an extra antenna to make it sure.
My sys:  Buffalo Tech WLI2-PCI-G54S ( with Broadcom 4306 -chip) with  2.6.20-16-generic kernel and Ubuntu 7.04
So I got an extra antenna now (and got time to tune up), now I got better  signal strength. Works like trains toilet (as we say here in Finland, when old toilet's dropped all directly on the track..). 
To be more specific, lspci gives up this: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03). Didn't need compile ndiswrapper. Didn't work with Buffalo's drivers so I used HP's ones as mentioned in Step 2b. WPA works as well.

---

### Post by Jamie Jackson on 2007-09-12
> **muppis said:**
> Works like trains toilet (as we say here in Finland, when old toilet's dropped all directly on the track..).

Hmm, in the States, most expressions involving toilets are negative ones. ;-)

I'm assuming "works like a train's toilet" is a good thing? :-s

Thanks for the feedback!

---

### Post by AB34125 on 2007-09-12
thank you,, thank you, thank you.,   have been trying to get wireless going for a long time and with you guide it took me around 10 minutes.

---

### Post by Jamie Jackson on 2007-09-12
> **AB34125 said:**
> thank you,, thank you, thank you.,   have been trying to get wireless going for a long time and with you guide it took me around 10 minutes.

That's disappointing, it was supposed to take less than 5. ;-)

If you have time, could you take a look at the very first post in this thread, and post the info it asks about? Also, please vote, if you haven't already.

---

### Post by Senathon on 2007-09-12
Can you make sure that you put the following instructions to do before doing anything else?

sudo apt-get update
sudo apt-get upgrade


I spent two weeks and 10 Ubuntu installation before I realize that I never upgraded the drivers in Ubuntu.  ](*,)

Senathon

---

### Post by Jamie Jackson on 2007-09-12
> **Senathon said:**
> Can you make sure that you put the following instructions to do before doing anything else?

sudo apt-get update
sudo apt-get upgrade


Hi Senathon, what did this buy you in the context of this HowTo. Were you unable to do a certain step until you ran these commands? If so, what step was it, and how did it fail?

---

### Post by ForTheOrca on 2007-09-13
* Machine Brand and Model:
Compaq Presario C571NR

* Wireless Brand, Model, and Chipset ("lspci | grep Broadcom")
Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

* Ubuntu Version (including 32 vs. 64 bit) and Kernel Version ("uname -a")
Linux zombah-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

* Any boot options you might be using (e.g., noacpi, irqpoll, etc.)
No particular boot options that I'm aware of.

* Whether or not you had to compile NDISWrapper
Didn't need to compile NDISWrapper.

* Which version of Step 2 you used
I tried 3 ways:

First, I used the prescribed steps, but used step 2a of the tutorial to be experimental with the install.  It didn't work, even after I compiled NDISWrapper.

Strike 1.

Second, I tried to use the driver supplied to me by HP ([ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34489.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34489.exe)).  This driver set didn't contain the bcmwl5.inf file, which may be why it wouldn't work.  The only INF files contained within it are NETw39x5 and w29n51.  NETw39x5 was the only one I could get to install with NDISWrapper.  However, this didn't get the wireless card to work, even after compiling NDISWrapper.  The reason for this not working is probably completely obvious to some of you.

Strike 2.

Third, I followed all of the steps, using step 2b for the driver.  Once I installed the driver and rebooted, the wireless light turned on.  Now I am here writing this follow-up feedback using a wireless connection.  In short, step 2b worked for me.  No need to compile NDISWrapper.

Thanks for putting together this tutorial, as it saved me a lot of heartache and frustration.  I just bought this laptop from Best Buy (of all places) for $450.  Oddly enough, the sales person told me that no other operating system (XP and Ubuntu explicitly mentioned) other than Vista would work on this computer due to Vista proprietary drivers being used.  I thought it sounded quite suspicious, especially considering that if it were true then I wouldn't be the true owner of the computer.  Microsoft would.  

I bought it anyway because it was a great deal and my other laptop just died.  Went home, made a system restore disc for the factory settings, and then wiped out the drive to put a clean Ubuntu install on it.  I didn't have a single problem with the install.  This wireless configuration stuff I knew would be a pain because it always is, but I had faith that it would eventually work.  Thanks to this tutorial, it's up and running.  

Anyway, sorry for the long post.

Cheers!

---

### Post by Jamie Jackson on 2007-09-13
> **ForTheOrca said:**
> Thanks to this tutorial, it's up and running.

Congrats, and thanks for the detailed feedback! Especially, thanks for experimenting with 2a. I guess I'll remove the line about the experimentation!

Update, I didn't remove that line, but now we know that 2a doesn't work for BCM4311 Rev 1, which is something I wanted to find out. I still suspect that this might be the right driver for any BCM4311 Rev *2*, though. So now I'm hoping for a non-F572US user to test 2a with their BCM4311 Rev 2.

---

### Post by AB34125 on 2007-09-14
> **Jamie Jackson said:**
> That's disappointing, it was supposed to take less than 5. ;-)

If you have time, could you take a look at the very first post in this thread, and post the info it asks about? Also, please vote, if you haven't already.

The guide was great,  I am new to this linux stuff

* Compaq Pasario v2000
* Broadcom Corporation BCM4318
* Xubuntu, 32 bit  Linux laptop 2.6.20-16-generic 
* Had to Complie

---

### Post by Jamie Jackson on 2007-09-14
> **AB34125 said:**
> The guide was great,  I am new to this linux stuff

* Compaq Pasario v2000
* Broadcom Corporation BCM4318
* Xubuntu, 32 bit  Linux laptop 2.6.20-16-generic 
* Had to Complie

Congrats, and thanks for the info! Your specs are up on the wiki.

---

### Post by appye on 2007-09-17
> **ForTheOrca said:**
> * Machine Brand and Model:
Compaq Presario C571NR
...
Cheers!

Okay, I have the same exact machine as ForTheOrca.  I ran a fresh install of 7.04 less than a week ago and ran all the updates.  Before I ran this tutorial, I was running (for a couple days) the tutorial found [here]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated").  I ran it with the injection capable module.  Anyway, it was running at only 11 megabit (byte? bort?) and the range was terrible.  So I uninstalled the firmware package, restored the original module and decided to give the method in outlined in this HOWTO a try.

At first, I was happy and feeling all warm and cuddly about it.  I followed the 2b instructions and all seemed well.  It ran at 54 megablasts and range was greatly improved.  However, I found that my power management events went haywire.

Now, when I manually go into hibernation using the menu options everything works great.  However, if I simply close the lid, it does not always go into hibernation.  When it is in this state, it also does not go into hibernation when I leave it alone for the prescribed amount of time.  This effect appears to be inconsistent, as sometimes closing the lid works.

I believe things return to normal when unloading and reloading the module, though this may have just been wishful thinking, as I have not had the chance to really test this theory.

On another note, I have found that upon returning from hibernation, it tries first to connect through the standard wired nic, and after a while claims to have established a connection (with ip address and company of 0.0.0.0).  It then "disconnects" after about 20 seconds and finally successfully connects to the wireless network.  This whole process takes about a minute, so it is a minor inconvenience I can learn to live with.  Strange.

Anyone have any suggestions to make these things work correctly?

---

### Post by Jamie Jackson on 2007-09-17
> **appye said:**
> Okay, I have the same exact machine as ForTheOrca.  I ran a fresh install of 7.04 less than a week ago and ran all the updates.  Before I ran this tutorial, I was running (for a couple days) the tutorial found [here]("http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated").  I ran it with the injection capable module.  Anyway, it was running at only 11 megabit (byte? bort?) and the range was terrible.

Did you see my comments on the bottom of that howto? When I followed that howto, I was left with a very slow connection, which I was able to tweak to a certain extent (but had to do so every time I connected). But I do still like my howto the best...

> 
At first, I was happy and feeling all warm and cuddly about it.  I followed the 2b instructions and all seemed well.  It ran at 54 megablasts and range was greatly improved.  However, I found that my power management events went haywire.

Now, when I manually go into hibernation using the menu options everything works great.  However, if I simply close the lid, it does not always go into hibernation.  When it is in this state, it also does not go into hibernation when I leave it alone for the prescribed amount of time.  This effect appears to be inconsistent, as sometimes closing the lid works.

I believe things return to normal when unloading and reloading the module, though this may have just been wishful thinking, as I have not had the chance to really test this theory.


I wish I knew more about the power management issues, but unfortunately, I don't.

> 
On another note, I have found that upon returning from hibernation, it tries first to connect through the standard wired nic, and after a while claims to have established a connection (with ip address and company of 0.0.0.0).  It then "disconnects" after about 20 seconds and finally successfully connects to the wireless network.  This whole process takes about a minute, so it is a minor inconvenience I can learn to live with.  Strange.

This happens to me occasionally, too. I've just been ignoring it. This is probably a minor NetworkManager bug.

Hopefully, this stuff is fixed in Gutsy.

Thanks for the feedback.

---

### Post by hrimhari on 2007-09-18
How-to worked for me, using step 2a.

My system is an HP Pavilion dv2404. lspci gives me the following about my wireless:

01:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)

Took me about 5 minutes ; ) Only thing is that I had to try my wireless network twice before it would connect. No clues why.

Before that, I tried different yet similar how-tos for Dapper. I'm now on Feisty. I dunno if the 2a firmware would work on Dapper... maybe so. Other firmwares would let me see networks but wouldn't allow me to connect.

Cheers!

---

### Post by hrimhari on 2007-09-18
Looks like the stablishment of a connection to my network is quite moody. This time it took about 5 times. I wonder if there are some sneaky parameters I should set to have it easier...

---

### Post by muppis on 2007-09-18
> **Jamie Jackson said:**
> Hmm, in the States, most expressions involving toilets are negative ones. ;-)

I'm assuming "works like a train's toilet" is a good thing? :-s

Thanks for the feedback!
Yes, it is a good thing. :D
Thanks for the guide.

---

### Post by Jamie Jackson on 2007-09-18
Thanks, hrimhari. It's looking like 2a is probably the best bet for "Rev 02" Dell 1390 (BCM4311). I'll probably add that info to the wiki.

---

### Post by appye on 2007-09-18
> **Jamie Jackson said:**
> When I followed that howto, I was left with a very slow connection, which I was able to tweak to a certain extent (but had to do so every time I connected). But I do still like my howto the best...


This was similar to my own result.  Now, what about [this other HOWTO]("http://ubuntuforums.org/showthread.php?t=405990") using a python script?  I have not tried this one, have you?  I am noticing that your method seems to work okay for me except for the power management issues that I already mentioned, and now last night I have discovered that BitTorrent downloads stall out pretty often.  I am able to download large files from say an ftp or http server, but not through bittorrent, perhaps because of the way bittorrent uses many different connections and the overhead is too much?

How did you come across sp33008.exe?  For my Compaq C571NR, I see [sp36684.exe]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&product=3441641&os=228&lang=en") for XP and  [sp36542.exe]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-52936-1&lc=en&cc=us&dlc=en&product=3441641&os=2093&lang=en") for Vista, both of these are from the HP/Compaq driver pages for my laptop.  I am wondering if my problems with this could be fixed by using a different firmware?  I would have no idea how to go about using a different firmware though

> **Jamie Jackson said:**
> Thanks, hrimhari. It's looking like 2a is probably the best bet for "Rev 02" Dell 1390 (BCM4311). I'll probably add that info to the wiki.

Mine is definately a Broadcom Dell 1390 Revision 01, but when I look at the physical chip itself it shows 4311 on there.  Sorry, I cannot be more specific as I am currently at work and do not have the laptop in front of me.

And on another note, here is a quote from you from the BlackNight howto:
"could you compare/contrast your native driver method vs. ndiswrapper vs. fwcutter, please?"

What method is there to try with fwcutter?  I would like to try that.  I am a little bit of a noob and was under the assumption that using fwcutter was the same thing as ndiswrapper.  Maybe you could point me in the right direction?

---

### Post by Jamie Jackson on 2007-09-18
> **appye said:**
> This was similar to my own result.  Now, what about [this other HOWTO]("http://ubuntuforums.org/showthread.php?t=405990") using a python script?  I have not tried this one, have you?  I am noticing that your method seems to work okay for me except for the power management issues that I already mentioned, and now last night I have discovered that BitTorrent downloads stall out pretty often.  I am able to download large files from say an ftp or http server, but not through bittorrent, perhaps because of the way bittorrent uses many different connections and the overhead is too much?


I use azureus, and it requires that I have both my router and azureus settings tuned properly. Have you gone through those exercises?

> 
How did you come across sp33008.exe?


I don't remember, some other howto, I think. Probably the one I call the "fluffy" howto.
> 
 For my Compaq C571NR, I see [sp36684.exe]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-53245-1&lc=en&cc=us&dlc=en&product=3441641&os=228&lang=en") for XP and  [sp36542.exe]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-52936-1&lc=en&cc=us&dlc=en&product=3441641&os=2093&lang=en") for Vista, both of these are from the HP/Compaq driver pages for my laptop.  I am wondering if my problems with this could be fixed by using a different firmware?


I wouldn't even try the Vista driver. If you want to experiment with other drivers, I think you'll want to:

```

# remove a driver with ndiswrapper, so you can try another
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5

```

Then, start back, and do your modified version of step 2, and continue on to pertinent steps of step 3:

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper
sudo ndiswrapper -m
#reboot

```

> 
And on another note, here is a quote from you from the BlackNight howto:
"could you compare/contrast your native driver method vs. ndiswrapper vs. fwcutter, please?"

What method is there to try with fwcutter?  I would like to try that.  I am a little bit of a noob and was under the assumption that using fwcutter was the same thing as ndiswrapper.  Maybe you could point me in the right direction?


Ndiswrapper, AFAIK, lets you use the Windows native driver and firmware. It's somewhat harder to set up (5 minutes), but it has the best speed, in theory.
Fwcutter, AFAIK, uses a Linux native driver, but still uses the Windows firmware.
(Folks, correct me if I'm wrong, above.)

fwcutter limits you to 11Mb/s, but the setup is super-easy. The package that installs it is broken currently, so I'd avoid experimenting with it at the moment, until it's fixed. (It's still do-able, but it's not as easy as it should be.)

---

### Post by biggyfred on 2007-09-18
HP Pavilion zv5000
Broadcom Corporation BCM4306
Ubuntu, 32 bit Linux laptop 2.6.20-16-generic
Followed step 2b.

No compiling. Just worked. Thanks a ton.

---

### Post by appye on 2007-09-18
> **Jamie Jackson said:**
> I use azureus, and it requires that I have both my router and azureus settings tuned properly. Have you gone through those exercises?

Of course.  Definately not a port forwarding issue.  Several other BT clients I tried had similar stalling/restarting issues.  Curiously, I found Azureus to be a bit flaky on my machine as it crashed a few times.  Perhaps this was related?  Normally, I use Azureus as well and was disappointed to see it be so buggy.

> **Jamie Jackson said:**
> I don't remember, some other howto, I think. Probably the one I call the "fluffy" howto.


So perhaps your wiki could be helped by a newer driver!  I see a ray of hope.  I will definately experiment with different drivers using your method...

---

### Post by Jamie Jackson on 2007-09-18
> **biggyfred said:**
> HP Pavilion zv5000
Broadcom Corporation BCM4306
Ubuntu, 32 bit Linux laptop 2.6.20-16-generic
Followed step 2b.

No compiling. Just worked. Thanks a ton.

Thanks! Your info's up on the wiki.

---

### Post by marq06 on 2007-09-20
**HP Compaq NX 7300**
Broadcom Corporation BCM**4311**
Ubuntu, 32 bit Linux laptop 2.6.20-16-generic
Followed step 2b.

No compiling. Just worked. 

You guyz rock !:guitar:

---

### Post by Jamie Jackson on 2007-09-20
> **marq06 said:**
> **HP Compaq NX 7300**
Broadcom Corporation BCM**4311**
Ubuntu, 32 bit Linux laptop 2.6.20-16-generic
Followed step 2b.

No compiling. Just worked. 

You guyz rock !:guitar:

Great! I think the howto's pretty solid now... Your info's up on the wiki. Thanks!

---

### Post by appye on 2007-09-21
Whoa.  Dude.  DUDE!  DUUUUUUUUUUUUUUUUUUUUUUDE!!!

I used the XP driver I mentioned in my previous post.  I haven't had a stalled torrent in the last 20 minutes at least.  

I have a compaq c571nr with a 4311 rev. a 

I will report if this is actually working the way I want or if I am just wishfully thinking after more testing...

---

### Post by DarkW0lf on 2007-09-22
Make/Model
Compaq Presario F572US
lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)
uname -r
Linux node3 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
(xubuntu 64 bit AMD)
Boot Options:
quiet splash noapic
Compiled ndiswrapper
Step 2a

Works

---

### Post by DarkW0lf on 2007-09-22
Make/Model
Compaq Presario F572US
lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02)
uname -a
Linux node3 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux
(xubuntu 64 bit AMD)
Boot Options:
quiet splash noapic
Compiled ndiswrapper
Step 2a

Wierd am I the only one having issues with the newest kernel ?
I found multiple entries in /etc/default/wpasupplicant and in /etc/modules.
Could that have been the issue with the newer kernel ?

Works after removing the extraneous entries.

---

### Post by Jamie Jackson on 2007-09-23
> **appye said:**
> Whoa.  Dude.  DUDE!  DUUUUUUUUUUUUUUUUUUUUUUDE!!!

I used the XP driver I mentioned in my previous post.  I haven't had a stalled torrent in the last 20 minutes at least.  

I have a compaq c571nr with a 4311 rev. a 

I will report if this is actually working the way I want or if I am just wishfully thinking after more testing...

Well, let us know how it goes. 

Also, could you please post the output of the following?
```
lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'
```

Also, I suspect that this is the case, but I'd like to establish that 1390 Rev 01 always equals 4311 Rev 01, and that 1390 Rev 02 always equals 4311 Rev 02.

---

### Post by Jamie Jackson on 2007-09-23
DarkW0lf, your last two posts with system specs: Could you edit them and add whether they're working or not? Given your past experiences, it's not clear whether they're successes or failures.

---

### Post by DooBeDooBeDo on 2007-09-26
It worked a treat for Kubuntu, I have 4318 in an acer laptop :KS

---

### Post by DarkW0lf on 2007-09-29
Oops sorry.

So far the newer kernel works after removing those extraneous entries.

So I was wondering if that kept the new kernel from working or why the old kernel worked with them. Guess it doesn't matter, it has been working so far.

Though twice I have had system freezes like fastpkr.
But that seems to happen when uploading a wiki page edit or I had left mousepad open for awhile. Can't tell if it is ndiswrapper related or not.

---

### Post by GunnerH on 2007-10-01
* Machine Brand and Model: HP Pavillion dv6424ca
    * Wireless Brand and Model: BCM4310 (rev 02)
    * Wireless Chipset: 14e4:4312
    * Ubuntu Version 32-bit Ubuntu 7.04 (Fiesty Fawn) Kernel 2.6.20-16-generic on AMD 64x2 Turion
    * Any extra boot options you might be using: noapic
    * Whether or not you had to compile NDISWrapper: yes
    * Which version of Step 2 you used: 2a

3-step process worked flawlessly!  Didn't time myself, but I'm a quick typer, so I'll give you the under 5-mins!  Thanks!!

---

### Post by Kidchaos on 2007-10-01
Solution completely failed on my system, then i found following on an other webforum and this did the trick for me.

<code>
wget [http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb](http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb)
sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
</code>

Worked for me with Deisty and on an Dell Inspiron 8k and Asus wl-100g (4306 b/g)

---

### Post by Jamie Jackson on 2007-10-02
> **Kidchaos said:**
> Solution completely failed on my system, then i found following on an other webforum and this did the trick for me.

<code>
wget [http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb](http://ubuntu.cafuego.net/pool/feist...buntu2_all.deb)
sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
sudo rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
</code>

Worked for me with Deisty and on an Dell Inspiron 8k and Asus wl-100g (4306 b/g)

The solution you settled on: I've commented about that procedure before: It was a super-easy installation for me, but my txpower/bandwidth was reduced, especially at any distance from the AP. I hope you fare better.

Can you give any more details as to how my process failed? Did the installation process go alright, but it just wouldn't associate? Could you not see APs? Etc...

---

### Post by Jamie Jackson on 2007-10-02
> **GunnerH said:**
> * Machine Brand and Model: HP Pavillion dv6424ca
    * Wireless Brand and Model: BCM4310 (rev 02)
    * Wireless Chipset: 14e4:4312
    * Ubuntu Version 32-bit Ubuntu 7.04 (Fiesty Fawn) Kernel 2.6.20-16-generic on AMD 64x2 Turion
    * Any extra boot options you might be using: noapic
    * Whether or not you had to compile NDISWrapper: yes
    * Which version of Step 2 you used: 2a

3-step process worked flawlessly!  Didn't time myself, but I'm a quick typer, so I'll give you the under 5-mins!  Thanks!!

Great, thanks for the details. I think you're the first BCM4310 (4312) owner to give feedback.

---

### Post by Kidchaos on 2007-10-02
Well all the steps worked fine without any errormessages but it wasn assigning the wlan into networks, i found no way to handle this, so i searched on and found this solution which from first time worked properly for me and i cant say yet if i have reduces in bandwith really its quite fast on this old mashine still, far faster as it was on win 2k pro. The ubuntu instalation gave for me a big increase in mashine performance at all. I had to import this file by disk to finaly get this running, i have to give in im very neewborn at linux (Using linux now my 4th day =)) ) .

cheers mike

---

### Post by Kidchaos on 2007-10-02
* Machine Brand and Model: Dell Inspiron 8000
* Wireless Brand and Model: BCM4306  (rev 03)
* Wireless Chipset: 14e4:4320
* Ubuntu Version 32-bit Ubuntu 7.04 (Fiesty Fawn) Kernel 2.6.20-16-generic on P III 700 Mobile
* Whether or not you had to compile NDISWrapper: yes
* Which version of Step 2 you used: 2c (and also used the Win driver given on manufactures cd)

---

### Post by Jamie Jackson on 2007-10-02
> **Kidchaos said:**
> * Machine Brand and Model: Dell Inspiron 8000
* Wireless Brand and Model: BCM4306  (rev 03)
* Wireless Chipset: 14e4:4320
* Ubuntu Version 32-bit Ubuntu 7.04 (Fiesty Fawn) Kernel 2.6.20-16-generic on P III 700 Mobile
* Whether or not you had to compile NDISWrapper: yes
* Which version of Step 2 you used: 2c (and also used the Win driver given on manufactures cd)

Edit: Ahhh, you used step 2c. It was 2b that you wanted. 2c is for the bcm4318.

---

### Post by Jamie Jackson on 2007-10-02
I added a [table]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851") to try to clear up any confusion over which version of step 2 to use.

---

### Post by mOOky on 2007-10-02
Jame, you totally ROCK!

After much searching and googling, I stumbled upon a page that led me to the fluffy version, and then to your "no fluff" version.

I followed the steps faithfully, with the only exception being that I downloaded the driver directly from Dell's support site and *poof* I had working WiFi.  Cheers!

I edited the testimonials section of your page, hope you don't mind.

Details:

Dell XPS M1210 laptop
Dell Wireless 1500 Draft 802.11n WLAN mini Card [uses Broadcom 4328 chip]

For step 2 I downloaded the driver (on a wired connection using Firefox) from [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=3&catid=5&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=3&catid=5&impid=-1&formatcnt=1&libid=5&fileid=202136)

After downloading it, I issued "unzip R151517.EXE" and it unpacked everything, notably the driver files needed in the DRIVER directory.

Followed the rest of your superbly written dox and I am a happy WiFi toting Ubuntu person now.

I first connected to my neighbors non-protected 802.11g network, and then connected to my WPA-PSK protected 802.11g network, both with no issues.  Ubuntu prompted me to create a keyring master password, which I did.

You basically made my night.  Cheers!

---

### Post by Jamie Jackson on 2007-10-03
> **mOOky said:**
> Jame, you totally ROCK!

After much searching and googling, I stumbled upon a page that led me to the fluffy version, and then to your "no fluff" version.

I followed the steps faithfully, with the only exception being that I downloaded the driver directly from Dell's support site and *poof* I had working WiFi.  Cheers!

I edited the testimonials section of your page, hope you don't mind.

Details:

Dell XPS M1210 laptop
Dell Wireless 1500 Draft 802.11n WLAN mini Card [uses Broadcom 4328 chip]

For step 2 I downloaded the driver (on a wired connection using Firefox) from [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=3&catid=5&impid=-1&formatcnt=1&libid=5&fileid=202136](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151517&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=8043&devlib=0&typecnt=0&vercnt=3&catid=5&impid=-1&formatcnt=1&libid=5&fileid=202136)

After downloading it, I issued "unzip R151517.EXE" and it unpacked everything, notably the driver files needed in the DRIVER directory.

Followed the rest of your superbly written dox and I am a happy WiFi toting Ubuntu person now.

I first connected to my neighbors non-protected 802.11g network, and then connected to my WPA-PSK protected 802.11g network, both with no issues.  Ubuntu prompted me to create a keyring master password, which I did.

You basically made my night.  Cheers!

Great, thanks. I think you're the first 4328 user to provide feedback.

A few questions: Please post the following, so I can learn more about that device.:
[LIST]
[*]Wireless Brand and Model (please post the whole line): [COLOR="DarkRed"][FONT="Courier New"]lspci | grep Broadcom[/FONT][/COLOR]
[*]Wireless Chipset: [COLOR="DarkRed"][FONT="Courier New"]lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'[/FONT][/COLOR]
[*]Did you have to compile NDISWrapper, or did the apt-get installed one work fine?
[/LIST]

Finally, I don't suppose you tried any of the drivers in any of the existing steps 2, did you? It would be nice to know whether one of the existing drivers would have worked for it. If I don't get this figured out, I could add the driver you used.

---

### Post by kevdog on 2007-10-03
Jamie

Great guide -- I particularly like the step 2 section that allows people to download the bcmwl5 driver files from a particular site.  That's the most useful part in my opinion.  Great work.

Ive seen some posts with people telling me the dell internal wireless card (broadcom) are shipped with a bcmwl6 driver version (not 5).  Any experience with this??  I dont know the changes in 5 vs 6.

---

### Post by Jamie Jackson on 2007-10-03
> **kevdog said:**
> Jamie

Great guide -- I particularly like the step 2 section that allows people to download the bcmwl5 driver files from a particular site.  That's the most useful part in my opinion.  Great work.


Thanks! That's my favorite part, too. It's a waste of time going to a browser and looking for a driver that somebody's tried to describe, guessing at the driver, downloading, unpacking, etc. I like the efficiency and fool-proof wgets and unpacking instructions.

> 
Ive seen some posts with people telling me the dell internal wireless card (broadcom) are shipped with a bcmwl6 driver version (not 5).  Any experience with this??  I dont know the changes in 5 vs 6.

Nope, I haven't heard about the bcmwl6 versions yet.

---

### Post by Jamie Jackson on 2007-10-03
> **Jamie Jackson said:**
> Great, thanks. I think you're the first 4328 user to provide feedback.
....
If I don't get this figured out, I could add the driver you used.

Hmm, that's a 52MB download, which sorta violates the "No-Fluff" ethos, so I'm holding off for a bit.

---

### Post by samuraiCat on 2007-10-10
> **Jamie Jackson said:**
> Thanks for the detailed report!

Site note: I have had issues connecting to WRT54G (slow Internet surfing, etc.).  I'm at a beach cottage right now, and we've got a WRT54G v6 here. I had the same issues with it, but I hacked the router and installed DD-WRT (micro) on it. Internet's been fine ever since. I'm not sure what the sticking point is on some stock WRT54G routers, though.

Thanks for all the info. I just bought that WRT54G router and a new Compac Presario F500 with the 4311 card, so this is all very good to know.

By the way, is there a HOWTO to hack the router and install DD-WRT? I have absolutely no idea what that even means. Thanks!

---

### Post by samuraiCat on 2007-10-10
> **fastpakr said:**
> First output was with ndiswrapper the way we had it working - dropping 20% or more packets and occasionally locking up, but working.

Second output is with acpi=noirq added as a boot parameter.  ndiswrapper does not work in this configuration.

Third output is after removing both acpi=noirq and noapic.  ndiswrapper works the same as the first output - lossy and slow, but kind of working.

Fourth output is following the thread you linked at linux-geek.org using the native driver.  The laptop sees the wireless card but I get no scan results and all the errors you'll find at the end of the output.

Hope that helps?

I'm late to this discussion, but are you adding those boot perameters because of issues with your laptop monitor? If so, I added all the same stuff you did, with similar crappy results. It turns out that adding "vga=792" to the boot will fix it. Follow the instructions here: [http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/](http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/)

---

### Post by cscotty on 2007-10-10
It worked great for me.  I have a Toshiba Tecra 9000 using the broadcom 4318.  The initial instructions did not work, but I followed the further instructions and it worked great!

Thanks!
Scott

---

### Post by Jamie Jackson on 2007-10-10
> **samuraiCat said:**
> Thanks for all the info. I just bought that WRT54G router and a new Compac Presario F500 with the 4311 card, so this is all very good to know.

By the way, is there a HOWTO to hack the router and install DD-WRT? I have absolutely no idea what that even means. Thanks!

I'd recommend just trying it with the latest Linksys firmware first. It will probably work without the hack, but if not, you might consider it.

DD-WRT is an open source, Linux-based replacement of the Linksys firmware. On older (vintage) WRT54G routers, DD-WRT can really upgrade it to give it some professional-grade features. Newer routers aren't quite as tweakable, but I found the DD-WRT more compatible with my wireless card, for whatever reason.

Anyway, [here's some info on DD-WRT]("http://www.dd-wrt.com/wiki/index.php/Main_Page").

---

### Post by mustang50187 on 2007-10-11
Method work great and it aint no lie it took about 5 minutes. No problem at all. I have a Dell wireless 1390 WLAN mini PCI card rev. 02.

---

### Post by DarkW0lf on 2007-10-13
I have the bcmwl6 files from my Vista partition still and they do not work.
The bcmwl5 version works with ndiswrapper.
I don't know the difference between them.

But it is becoming a pain, often it still does not work in the latest kernel (2.6.20-16.32) and it is starting to freeze up like fastpakr has been reporting. Or it just looses the association with the WAP. I have to use 2.6.20-15 when I want to use the WiFi. This bouncing between working and non-working 2.6.20-16 kernels is getting annoying.

---

### Post by kevdog on 2007-10-13
Compile ndiswrapper against your kernel might help.  Each kernel has different header files, hence maybe the problem.

---

### Post by DarkW0lf on 2007-10-19
That's true but typically you don't need to recompile for the revision (the number after the dash or the third number). I'll also try the newer ndiswrapper package, there was only 1.47 available when I first installed and there are updated sources.

---

### Post by MeteoraLP on 2007-10-23
* Dell inspiron 6400
    * Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
    * 14e4:4328 (rev 01)
    * 7.10 x86 2.6.22-14-generic #1 SMP
    * Did not compile 
    * Used my own version of drivers found from dell support site.

I first had sort of a mess going on. I had originally installed the driver for this using the GUI version of ndiswrapper. And it caused some problems with your method. But i then went and removed the first drivers i had and then used your method and everything worked perfectly! Used drivers found on the dell support site for my wireless card. Its a Dell 1500 draft-n wireless card.

EDIT: I should mention that i have been a linux user for 2 days. Although i have prior experience using command line for writing C++ and using the CC/G++ compilers, i have no background in any other linux activity, but this guide was easy to follow!

---

### Post by kevdog on 2007-10-23
Seems like the bcmwl6 drivers are those for broadcom chipsets included with Vista. To the best of my knowledge vista drivers and ndiswrapper do not work together.

---

### Post by michael37 on 2007-10-24
No fluff instructions worked great for GUTSY!!!   Added testimonial on Gutsy.

Yeehaw.

---

### Post by Jamie Jackson on 2007-10-25
> **kevdog said:**
> Seems like the bcmwl6 drivers are those for broadcom chipsets included with Vista. To the best of my knowledge vista drivers and ndiswrapper do not work together.

Ahh, got it. Thanks for the info.

---

### Post by Jamie Jackson on 2007-10-25
I've added support for the BCM4328. I was reluctant to link to the 52MB download, so I repackaged the files into a much more manageable 731KB zip file.

This is now step 2, option "D" (2d).

---

### Post by Jamie Jackson on 2007-10-25
> **michael37 said:**
> No fluff instructions worked great for GUTSY!!!   Added testimonial on Gutsy.

Yeehaw.

Thanks. If I get a few more Gutsy success reports, I'll rename the wiki post to reflect Gutsy, as well.

---

### Post by james957 on 2007-10-26
The how-to is great, and works for Gutsy.
I tried several other procedures before I tried this one, and this worked like a charm!
I had to start with a fresh install, though.

By the way, my wireless info is:

0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by soumo on 2007-10-26
Perfect!!!   After many, many attempts, directories and drivers scattered everywhere.
All I had to do was uninstall all drivers (System > Administration > Windows Wireless Drivers)

Lenovo 3000 N100  
0768-E2F (French)

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
03:00.0 0280: 14e4:4328 (rev 01)
Ubuntu-32bit 7.10 Gutsy Gibbon (heavily tweaked, not even close to fresh)
2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
No boot options 
No need to compile Ndiswrapper
Step2d used

Thanks a ton!

---

### Post by Jamie Jackson on 2007-10-26
> **soumo said:**
> Perfect!!!   After many, many attempts, directories and drivers scattered everywhere.
All I had to do was uninstall all drivers (System > Administration > Windows Wireless Drivers)

Lenovo 3000 N100  
0768-E2F (French)

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)
03:00.0 0280: 14e4:4328 (rev 01)
Ubuntu-32bit 7.10 Gutsy Gibbon (heavily tweaked, not even close to fresh)
2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
No boot options 
No need to compile Ndiswrapper
Step2d used

Thanks a ton!

Great, you're the first step 2d guinea pig, so I'm glad it worked. Thanks for the details! Extra points for you. :)

---

### Post by DarkW0lf on 2007-10-26
I need to cleanup my system.

I upgraded and need to reinstall the firmware.
The native gutsy support isn't working or I did something wrong (probably the later).
I also have two nm-applets in the systray, I need to get rid of one.

I pointed the restricted driver manager to bcmwl5.sys, was that the right file ?
It says it is in use but the card is not enabled.

---

### Post by Jamie Jackson on 2007-10-27
> **DarkW0lf said:**
> I need to cleanup my system.

I upgraded and need to reinstall the firmware.
The native gutsy support isn't working or I did something wrong (probably the later).
I also have two nm-applets in the systray, I need to get rid of one.

I pointed the restricted driver manager to bcmwl5.sys, was that the right file ?
It says it is in use but the card is not enabled.

Okay, so you're not doing ndiswrapper, and you're going with the native driver... that's fine. Let's deal with the restricted drivers manager first:

1. Disable the driver you've got in there
2. Reenable it, but this time, opt for the "Download from the Internet" option, and let it use the default URL ([http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o)).

Jamie

---

### Post by DarkW0lf on 2007-10-27
Default firmware loads and device is enabled.
I was trying to get it working with the existing firmware I had on disk when I was using ndiswrapper.

I'll check it out more later, I am busy right now and have a Hamfest (as in ham radio) to go to tomorrow.

---

### Post by Jamie Jackson on 2007-10-27
> **DarkW0lf said:**
> Default firmware loads and device is enabled.
I was trying to get it working with the existing firmware I had on disk when I was using ndiswrapper.

I'll check it out more later, I am busy right now and have a Hamfest (as in ham radio) to go to tomorrow.

Ahh, okay. By the way, you get extra geek points for both running Linux and going to a Hamfest.

---

### Post by syga on 2007-10-31
Instructions worked perfectly on Gutsy 64. Had to use ndiswrapper and step 2 of the instructions.
Dell Inspiron 1501
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Chipset: 
14e4:4311 (rev 01)

Thanks for the instructions. Without it, I'd still be using windows...

---

### Post by Jamie Jackson on 2007-10-31
> **syga said:**
> Instructions worked perfectly on Gutsy 64. Had to use ndiswrapper and step 2 of the instructions.
Dell Inspiron 1501
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Chipset: 
14e4:4311 (rev 01)


Thanks for the feedback. To be clear: Do you mean you had to *compile* ndiswrapper?

---

### Post by syga on 2007-10-31
>Thanks for the feedback. To be clear: Do you mean you had to compile ndiswrapper?

Yes, I did compile ndiswrapper. 

Before I followed your instructions, I tried to use Ubuntu's restricted driver manager to install the Broadcom drivers. It partly worked, I could see the network. but could not connect. I don't understand why the restricted driver manager  worked for some people but not for me...

---

### Post by oppo on 2007-11-01
Presario V3000,4311 rev 01. Gutsy. Worked perfectly! I tried many other posts over 3 days and this is the one that finally works. Thanks

---

### Post by syga on 2007-11-02
This link step 2b, 

sudo wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

does not work as of nov 2. 

Is there anywhere else we can get this?

I did try to google it, but did not get any results...

---

### Post by Jamie Jackson on 2007-11-02
Well, that's a pain, they took it right out of the [downloads directory]("ftp://www.hp.com/pub/softpaq/sp33001-33500/")... 

I'll figure it out and fix it when I can...

---

### Post by syga on 2007-11-02
I found a link that works with step 2b

wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)

---

### Post by Jamie Jackson on 2007-11-02
Added it, thanks!

---

### Post by bbrg548 on 2007-11-02
> **syga said:**
> This link step 2b, 

sudo wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

does not work as of nov 2. 

Is there anywhere else we can get this?

I did try to google it, but did not get any results...

I had the same problem with step 2a.

The same solution fixes it. Change it to this:
 wget [ftp://ftp.compaq.com/pub/softpaq/sp34001-34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34152.exe)

After this, and following your guide, it works! :)

-----
Machine = HP Pavilion dv9628nr
Wireless Brand + Model = Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
Wireless Chipset = 03:00.0 0280: 14e4:4311 (rev 02)
Ubuntu Version = 7.10 (64 bit) Kernel 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
No extra boot options
I did not have to compile ndiswrapper
I used step 2a (with the change shown above
-----

Thanks!
Jake

---

### Post by Jamie Jackson on 2007-11-03
Thanks for the feedback, Jake. I couldn't get your link to work, but I browsed around until I found it:
```

wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe

```
I added it to the wiki.

---

### Post by drs305 on 2007-11-04
Success. Followed step 2a. No compiling necessary.

Broadcom 4311 rev 2,  BCM94311MCG wlan mini-PCI (rev 02)
Lenovo N100, Gutsy 7.10 32-bit, 2.6.22-14-generic
Chipset: 03:00.0 0280: 14e4:4311 (rev 01)

Previously could see the network but not connect with the proprietary Broadcom restricted drivers enabled.  Gutsy broadcom 43xx restricted driver is now unchecked/uninstalled.

Thanks.

---

### Post by besseresser on 2007-11-05
Hi, Thank you for this helpful guide :)

I have an HP G7000 laptop. Everything seems to work fine, except the laptop's w-lan on/off switch, It does nothing. I didn't have to compile ndiswrapper manually, and step 2a was used.

**lspci output:** 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

**chipset**: 01:00.0 0280: 14e4:4311 (rev 02)

Ubuntu 7.10; 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

---

### Post by kekegg on 2007-11-06
Finally, it works.

Would you please add some detail on BCM4311 (Rev 02) .

I waste several hours only becuase I performed step 2b, while I should take 2a.

BCM4311 (Rev 01) 	
14e4:4311 (rev 01) 	
Step 2b 	
In Gutsy, lspci shows this card as "Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)". Feisty shows the card as "Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)" 

BCM4311 (Rev 02) 	
	
Step 2a

---

### Post by Cod on 2007-11-06
Thanks for the HowTo.  Got my wireless working.  For the record:

Dell Latitude D420 with a fairly fresh Gutsy install

lspci tells me:

Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

I went for option 2b and did not have to compile ndiswrapper.

Part way through Step 3, the little wireless light on my laptop lit up like a tiny beacon of joy.  After resetting, it was still lit up and I am now writing this from the comfort of my lounge using my wireless network, drinking a beer and breaking wind.

---

### Post by syga on 2007-11-07
Will these instructions work on all linux distros or just ubuntu?

---

### Post by bbrg548 on 2007-11-09
> **Jamie Jackson said:**
> Thanks for the feedback, Jake. I couldn't get your link to work, but I browsed around until I found it:
```

wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe

```
I added it to the wiki.

Oops! My typo, sorry. I left out the "3400/" part.  ](*,)

-Jake

---

### Post by Praxicoide on 2007-11-10
Success! Everything went smoothly.

The computer is a Compaq Presario V300 with fresh Gusty Gibbon.

---

### Post by yopines on 2007-11-10
Dear Jamie,
you have great instructions and I have followed them step by step but without any success.
Here are the details of my machine:
Compaq Presario F572US

yaron@yaron-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

yaron@yaron-laptop:~$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'
03:00.0 0280: 14e4:4311 (rev 02)

yaron@yaron-laptop:~$ uname -rmv
2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

I use NOACPI as additional boot option.
I compiled the NDISWrapper - but no help
I used verion 2a from your guide

The drivers are simply not loaded (with and without the Restricted Broadcom drivers) and the LED remains Orange (supposed to turn blue when drivers are loaded)

This machine boots into Windows Vista Ultimate 64bit without problems and Wifi works great.

Any suggestions?  I have spent 2 full days with this and don't know what else to do?
Thanks
Yaron

---

### Post by Jamie Jackson on 2007-11-11
> **yopines said:**
> Dear Jamie,
you have great instructions and I have followed them step by step but without any success.
Here are the details of my machine:
Compaq Presario F572US

yaron@yaron-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

yaron@yaron-laptop:~$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'
03:00.0 0280: 14e4:4311 (rev 02)

yaron@yaron-laptop:~$ uname -rmv
2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

I use NOACPI as additional boot option.
I compiled the NDISWrapper - but no help
I used verion 2a from your guide

The drivers are simply not loaded (with and without the Restricted Broadcom drivers) and the LED remains Orange (supposed to turn blue when drivers are loaded)

This machine boots into Windows Vista Ultimate 64bit without problems and Wifi works great.

Any suggestions?  I have spent 2 full days with this and don't know what else to do?
Thanks
Yaron

A couple things:
Did you do a firmware upgrade of this device in Vista?
What's the output of "lshw -C network"?

Thanks,
Jamie

---

### Post by yopines on 2007-11-11
Hi Jamie and thanks for your reply.
I do "windows updates" on a regular basis, but don't recall in specific any firmware update for the wlan-mini-PCI

Here is the output:

root@yaron-laptop:/home/yaron# lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


Thanks
Yaron

---

### Post by tcaldwell on 2007-11-11
I followed the directions for the wrong chipset, how do I fix what I have done and try again with the correct chipset? (If It makes any difference I am using 7.1)

also I am connected wirelessly for short periods of time using the restricted driver manager, should I hardline before doing this going through those steps or can I stay connected wirelessly?

---

### Post by Hamditter on 2007-11-11
Jamie- this worked great for me.  It took me a bit longer then 5 minutes, because I'm a slow typist, and I double checked each line for accuracy before hitting return.  I'm using an old Dell Inspiron 2650, with Gutsy.  The card is a Linksys WPC54G, with the BCM4318 chipset.  Thanks for taking the time and effort to work out this solution for us.

---

### Post by DarkW0lf on 2007-11-11
Thanks Jamie, I am indeed a geek.

I had to reinstall 7.04 due to a bad upgrade.
And upgraded fresh from there.

So on this new, clean 7.10 I followed the steps and it works with the ndiswrapper packages. Yea, didn't have to compile on this F572US.

Model: Compaq F572US
1st lspci: 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PC (rev 02)
2nd lspci: 03.00.0 0280: 14e4:4311 (rev 02)
OS: xubuntu 7.10 AMD64
uname -rmv: 2.6.22-14-generic #1 SMP x86_64
Added Boot Option: noapic
Compile: No
Step: 2a

Jamie the second lspci command in your first post has 21 listed twice in the regex, is that right ?

---

### Post by guggero on 2007-11-13
Hi

First I want to thank all the people who helped to write this tutorial!
It worked, finally, after I tried several other tutorials.

It worked with ndiswrapper without compiling it new.

Machine: HP Compaq 6910p
Wireless: 10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
Wireless Chipset: 10:00.0 0280: 14e4:4311 (rev 02)
Ubuntu: 7.10
Kernel: 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Boot options: Default boot options
Compile ndiswrapper: No
Used Step: 2a

---

### Post by optimusmedia on 2007-11-13
> **Jamie Jackson said:**
> [I]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
[*]Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'
[*]Ubuntu Version (including 32 vs. 64 bit) and Kernel: uname -rmv
[*]Any *extra* boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used
[/LIST] 

After trying 2b - I found a post saying my chipset worked for a instead - which I found to be true.  Thanks to whoever posted that info.  Here are my details hoping it helps:  

First, an FYI: A fresh install of 7.10 did not get my wireless working with restricted drivers. (Note to Broadcom: Take a look at what's going on here with Ubuntu (and Linux in general) -- Your lack of support for the Linux revolution makes me unlikely to use your hardware in the future.) Okay, that feels better.  On with my info.

Machine: Compaq Presario V6000
Wireless Card: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Wireless chipset: 03:00.0 0280: 14e4:4311 (rev 01)
Ubuntu Version: 7.10 Gutsy 32bit
Kernel: 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Extra boot options: noacpi
Did not have to compile NDISWrapper
Step 2a Used to great success!  (Previously tried 2b)

Now the only steps remaining are to get my Nvidia video drivers working and to get Dreamweaver working on it.  Then my vista partition will be gone. Yeah!!!!

Thanks again to all who helped with this tutorial.  My newbie shell is flaking away already :)

Ron

---

### Post by Jamie Jackson on 2007-11-13
Just a note that I haven't forgotten about this thread or the wiki howto. I've been busy at home and at work, but hope to catch up here soon.

---

### Post by Jamie Jackson on 2007-11-13
> **besseresser said:**
> Hi, Thank you for this helpful guide :)

I have an HP G7000 laptop. Everything seems to work fine, except the laptop's w-lan on/off switch, It does nothing. I didn't have to compile ndiswrapper manually, and step 2a was used.

**lspci output:** 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

**chipset**: 01:00.0 0280: 14e4:4311 (rev 02)

Ubuntu 7.10; 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

To clarify: Your wireless works fine, but the switching the hardware switch does not turn the wireless of in its "off" position?

---

### Post by Jamie Jackson on 2007-11-13
> **kekegg said:**
> Finally, it works.

Would you please add some detail on BCM4311 (Rev 02) .

I waste several hours only becuase I performed step 2b, while I should take 2a.

BCM4311 (Rev 01) 	
14e4:4311 (rev 01) 	
Step 2b 	
In Gutsy, lspci shows this card as "Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)". Feisty shows the card as "Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)" 

BCM4311 (Rev 02) 	
	
Step 2a

Let me get this straight (please confirm or correct the following):
You have a BCM4311 (Rev 01)
You tried step 2b, according to the instructions.
That didn't work, so you tried step 2a, which worked.

Also, can you explain why you're curious about the BCM4311 (Rev 02), or what sort of detail you're looking for?

UPDATE: Also, please take a look at the first post of this thread, and post the details it requests, as [optimusmedia]("http://ubuntuforums.org/showpost.php?p=3763555&postcount=266") had the same issue, and I want to see if you two have anything in common.

---

### Post by Jamie Jackson on 2007-11-13
> **Cod said:**
> Thanks for the HowTo.  Got my wireless working.  For the record:

Dell Latitude D420 with a fairly fresh Gutsy install

lspci tells me:

Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

I went for option 2b and did not have to compile ndiswrapper.

Part way through Step 3, the little wireless light on my laptop lit up like a tiny beacon of joy.  After resetting, it was still lit up and I am now writing this from the comfort of my lounge using my wireless network, drinking a beer and breaking wind.

Ahh, the sweet smell of wireless. By the way, would you please post the output of:
```
lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'
```

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-11-13
> **syga said:**
> Will these instructions work on all linux distros or just ubuntu?

I don't personally know, but there's a good chance that it work with Debian variants. (What with all the apt-get stuff.)

---

### Post by Jamie Jackson on 2007-11-13
> **Praxicoide said:**
> Success! Everything went smoothly.

The computer is a Compaq Presario V300 with fresh Gusty Gibbon.

Congrats, and thanks for the feedback. If you get a chance, please look at the first post of this thread, and provide the details it requests.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-11-13
> **tcaldwell said:**
> I followed the directions for the wrong chipset, how do I fix what I have done and try again with the correct chipset? (If It makes any difference I am using 7.1)

also I am connected wirelessly for short periods of time using the restricted driver manager, should I hardline before doing this going through those steps or can I stay connected wirelessly?

It shouldn't matter whether you've got wireless or a wired network connection, since you can download the new driver in advance.

To try a new driver, run:
```
# remove an incompatible driver with ndiswrapper, so you can try another
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
```

Then, run the appropriate step 2.

If before, you didn't get to step 3, then just do step 3. If you did get through step 3 before, then just run this subset of step 3:

```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper
```

You might have wireless now, or you might need to reboot...

Good luck.

---

### Post by Jamie Jackson on 2007-11-13
> **Hamditter said:**
> Jamie- this worked great for me.  It took me a bit longer then 5 minutes, because I'm a slow typist, and I double checked each line for accuracy before hitting return.  I'm using an old Dell Inspiron 2650, with Gutsy.  The card is a Linksys WPC54G, with the BCM4318 chipset.  Thanks for taking the time and effort to work out this solution for us.

You're welcome! and thanks for the feedback. If you could post some further details (see the first post of this thread), that would also be great.

---

### Post by Jamie Jackson on 2007-11-13
> **DarkW0lf said:**
> Thanks Jamie, I am indeed a geek.

I had to reinstall 7.04 due to a bad upgrade.
And upgraded fresh from there.

So on this new, clean 7.10 I followed the steps and it works with the ndiswrapper packages. Yea, didn't have to compile on this F572US.

Model: Compaq F572US
1st lspci: 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PC (rev 02)
2nd lspci: 03.00.0 0280: 14e4:4311 (rev 02)
OS: xubuntu 7.10 AMD64
uname -rmv: 2.6.22-14-generic #1 SMP x86_64
Added Boot Option: noapic
Compile: No
Step: 2a

Jamie the second lspci command in your first post has 21 listed twice in the regex, is that right ?

What, no problems?! I don't believe it. ;-)

I'm really glad to hear it. Also, you're right about the regex, thanks.

---

### Post by raichle on 2007-11-13
Success!   Wireless + WPA!!!
This is with a fresh install of Gutsy, was using Restricted Driver Manager but it was lousy.  

Did not have to compile ndiswrapper and I used step 2c.  

Here's the machine info:
Machine Brand and Model:  Dell Inspiron B130
Wireless Brand and Model: 02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Wireless Chipset:  02:03.0 0280: 14e4:4318 (rev 02)
Ubuntu Version: 32bit  2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

Thanks for the help!

---

### Post by Jamie Jackson on 2007-11-13
> **raichle said:**
> Success!   Wireless + WPA!!!
This is with a fresh install of Gutsy, was using Restricted Driver Manager but it was lousy.  

Did not have to compile ndiswrapper and I used step 2c.  

Here's the machine info:
Machine Brand and Model:  Dell Inspiron B130
Wireless Brand and Model: 02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Wireless Chipset:  02:03.0 0280: 14e4:4318 (rev 02)
Ubuntu Version: 32bit  2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

Thanks for the help!

You're welcome, and thanks for the detailed feedback.

---

### Post by Jamie Jackson on 2007-11-14
> **yopines said:**
> Dear Jamie,
you have great instructions and I have followed them step by step but without any success.
Here are the details of my machine:
Compaq Presario F572US

yaron@yaron-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

yaron@yaron-laptop:~$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|21|24|25|28)'
03:00.0 0280: 14e4:4311 (rev 02)

yaron@yaron-laptop:~$ uname -rmv
2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

I use NOACPI as additional boot option.
I compiled the NDISWrapper - but no help
I used verion 2a from your guide

The drivers are simply not loaded (with and without the Restricted Broadcom drivers) and the LED remains Orange (supposed to turn blue when drivers are loaded)

This machine boots into Windows Vista Ultimate 64bit without problems and Wifi works great.

Any suggestions?  I have spent 2 full days with this and don't know what else to do?
Thanks
Yaron

Okay, please list the output of the following:
ndiswrapper -l
cat /etc/modules
cat /etc/network/interfaces
cat /etc/modprobe.d/blacklist

---

### Post by yopines on 2007-11-14
Hi Jamie,
Here it is:  Please note that I had to copy it by hand.  Ndiswrapper in /etc/modules  below is actually shown as Ndiswrappe (without the r in the file)

ndiswrapper -l
bmcwl5 : driver installed
               device (14E4:4311) present (alternate driver: bcm43xx)

cat /etc/modules
# /etc/modules: kernel modules to load at boot time
#
#
#

fuse
lp
rtc
ndiswrappe

cat /etc/network/interfaces
auto lo
iface lo inet loopback

cat /etc/modprobe.d/blacklist
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist i2c_i801
blacklist bcm43xx

---

### Post by yopines on 2007-11-14
Jamie...

I realized that not having the "r" at the end of the NdisWrappe causes the NDISwrapper to not load on boot therefore I edited /etc/modules/ and added the "r"

EVERYTHING IS WORKING!!!   Awesome!!!!

Thanks for your help
Yaron

---

### Post by Jamie Jackson on 2007-11-14
> **yopines said:**
> Jamie...

I realized that not having the "r" at the end of the NdisWrappe causes the NDISwrapper to not load on boot therefore I edited /etc/modules/ and added the "r"

EVERYTHING IS WORKING!!!   Awesome!!!!

Thanks for your help
Yaron

Nice work! You must have accidentally mistyped this line from the instructions:
echo 'ndiswrapper' | sudo tee -a /etc/modules

Congrats,
Jamie

---

### Post by Threeethan on 2007-11-15
I got this to work with a new MacBook (Santa Rosa/X3100) which has the broadcom bcm4328 rev. 03.

I used this file: [ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)

And this is in gutsy gibbon amd64.  I had to use unzip on that file, but that's about it. No compilation or anything.

---

### Post by Jamie Jackson on 2007-11-15
> **Threeethan said:**
> I got this to work with a new MacBook (Santa Rosa/X3100) which has the broadcom bcm4328 rev. 03.

I used this file: [ftp://ftp.us.dell.com/network/R151517.EXE](ftp://ftp.us.dell.com/network/R151517.EXE)

And this is in gutsy gibbon amd64.  I had to use unzip on that file, but that's about it. No compilation or anything.

Thanks for the feedback. This device is new to me, would you mind posting the details specified in the first post of this thread, please?

---

### Post by coolclassic on 2007-11-17
Every thing worked first time:

Dell Inspiron 1501,Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01), 14e4:4311 (rev 01), kubuntu 7.10, 2.6.22-14-generic i686 no boot options, Did not compile ndiswrapper, Step 2b

---

### Post by Jamie Jackson on 2007-11-17
> **coolclassic said:**
> Every thing worked first time:

Dell Inspiron 1501,Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01), 14e4:4311 (rev 01), kubuntu 7.10, 2.6.22-14-generic i686 no boot options, Did not compile ndiswrapper, Step 2b

Congrats, and thanks for the details. I've added you to the wiki.

---

### Post by ghasek on 2007-11-18
Thanks, works great!

HP Compaq 6720s
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
10:00.0 0280: 14e4:4311 (rev 02)
Ubuntu 7.10 2.6.22-14-generic x86_64
no extra boot options
didn't have to compile
2a

:D

---

### Post by Jamie Jackson on 2007-11-18
> **ghasek said:**
> Thanks, works great!

HP Compaq 6720s
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
10:00.0 0280: 14e4:4311 (rev 02)
Ubuntu 7.10 2.6.22-14-generic x86_64
no extra boot options
didn't have to compile
2a

:D

Thanks for all the details, they're up on the wiki.

---

### Post by leoperbo on 2007-11-22
It works for me in a Dell Inspiron 640m with Ubuntu 7.10 using the 2b step.

I had to compile ndiswrapper in this How-To's way.

Thank you and congratulations.

P.D.
In the numerous attemps to have this working (before this how-to) my system turns too slow at boot (it was standing in "Starting NFS kernel daemon..." for a long time), the solution to those with the same problem: 

[http://ubuntuforums.org/showthread.php?t=344804](http://ubuntuforums.org/showthread.php?t=344804)

Thank you again.

---

### Post by Jamie Jackson on 2007-11-25
> **leoperbo said:**
> It works for me in a Dell Inspiron 640m with Ubuntu 7.10 using the 2b step.

I had to compile ndiswrapper in this How-To's way.

Thank you and congratulations.

P.D.
In the numerous attemps to have this working (before this how-to) my system turns too slow at boot (it was standing in "Starting NFS kernel daemon..." for a long time), the solution to those with the same problem: 

[http://ubuntuforums.org/showthread.php?t=344804](http://ubuntuforums.org/showthread.php?t=344804)

Thank you again.

Congrats! Would you post the details specified in the first post of this thread, please? I'd then be able to add your system specs to the wiki.

---

### Post by davidbaldwin on 2007-11-25
Total noob here. This is my first laptop, and I just switched to Linux 3 months ago.I have spent the last 3 days trying to figure out my wireless problem. I have looked through and followed I think every thread on this. If I install 7.10 then I can install the restricted driver and the wireless works. Then about 1 hour later my connection bogs down until I lose the connection, even though my laptop says its still connected. I can uninstall, reboot then reinstall the driver and it works again(a big pain for wireless). Any other options on setting up wireless never works, I don't see wireless networks on the network connection icon. Any help would be great. Here are my specs:

HP Compaq Presario V6171CL
AMD Turion(tm) 64 X2 Mobile Technology TL-50

Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Wireless chipset: 03:00.0 0280: 14e4:4311 (rev 01)
Ubuntu 7.10
Kernel / Architecture: 2.6.22-14-generic x86_64
Boot option noapic

---

### Post by kevdog on 2007-11-25
Try using ndiswrapper and not the restricted bcm43xx drivers.  The bcm43xx drivers are buggy -- if you haven't figured that out by now!!

---

### Post by davidbaldwin on 2007-11-25
I tried following the threads on how to do that but thats where I never got it to work.

---

### Post by kevdog on 2007-11-25
You stated that already, but if you want help, you need to post specifics -- how far did you get -- what step do you think didnt work.  

I want you to read Jamie's tutorial in conjuction with my tutorial found here: [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

A lot of it is the same information.  His tutorial provides links for the actual drivers (mine does not).  My tutorial gives possible problems found a long the way and suggests possible work arounds.  With both of these tutorials, you can probably work through the process up to a point that you can say -- its not working for me at this point.

---

### Post by davidbaldwin on 2007-11-27
Thank you that link. At first I had problems with the driver part but I reinstalled ubuntu then downloded the driver then followed your tutorial. My wireless is finally working good. When I do  lshw -C network the logical name is always eth1, is that going to be a problem? The only thing left to figure out is to set up for WPA filtering. Thank you for you help.

---

### Post by kevdog on 2007-11-27
eth1 or wlan0 -- It doesnt matter.  It will not cause you problems.

---

### Post by Jamie Jackson on 2007-11-27
> **davidbaldwin said:**
> Thank you that link. At first I had problems with the driver part but I reinstalled ubuntu then downloded the driver then followed your tutorial. My wireless is finally working good. When I do  lshw -C network the logical name is always eth1, is that going to be a problem? The only thing left to figure out is to set up for WPA filtering. Thank you for you help.

What are you using to manage your network connections, NetworkManager? (This comes stock with Ubuntu.)

If so, and if you mean WPA *encryption* (I don't know what WPA *filtering* means), then make sure /etc/default/wpasupplicant has the line ```
ENABLED=0
```
...which, AFAIK, will enable NetworkManager to handle WPA connections.

---

### Post by davidbaldwin on 2007-11-27
Yes WPA encryption. I just followed your tutoril on the driver and kevdog's tutorial for the ndiswrapper. I havent set any wpasupplicant yet (my next feat). I am not managing my network connection, just turn on my computer and wireless work.

---

### Post by Jamie Jackson on 2007-11-29
Okay, it should be easy on the Linux side of things.

---

### Post by HW_Hack on 2007-12-02
Jamie

Great job in doing both this thread AND the How To Page !!!  Us poor sots who unknowingly bought or got a laptop with this Anti-Christ chipset owe you some thanks !!

I ended up having to do the ndiswrapper compile to make it work. And there is no surprise there - I've reloaded Ubuntu a few time on my Dell B130 Inspiron and learned to muddle through following various how to's ---- so far the other best how to is at the Ndiswrapper site 

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

And in my recollection this particular demonic version of the 4318 requires a very specific windows driver  ..... and its not the one that Dell offers on its site for my B130.

Doing your standard install for a    14e4:4318 (rev 02)   led me to step 2C   -- on reboot my wireless LED lit up - but no wireless networks were listed. Your instructions mentioned trying step 2A if that failed ---- but looking at the recompile section I recognized several steps from past forays  in getting wireless to work.

Meanwhile THATS THAT !!!  No more fiddling around -- I'm going to make a disk image copy of this install and moving on:guitar:
    *

      Machine Brand and Model               Dell Inspiron B130
    *

      Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


    *

      Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
02:03.0 0280: 14e4:4318 (rev 02)
    *

      Ubuntu Version: lsb_release -d
Description:    Ubuntu 7.04

    *

      Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.20-16-generic i686

    *

      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)      No boot options used
    *

      Whether or not you had to compile NDISWrapper    Yes 
    *

      Which version of Step 2 you used              2C

---

### Post by ufis on 2007-12-02
> **Jamie Jackson said:**
> [BCM43xx HowTo.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
If I ever meet you, drinks are on me.

It works perfectly on my Dell inspiron 1520.

---

### Post by Steenmeijer on 2007-12-02
Awesome. First reboot the connection died after a few minutes but that may have been the router. Details:

_Machine Brand and Model:_
Acer Aspire 9305AWSMi
_Wireless Brand and Model_:
```
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```
_Wireless Chipset:_
```
01:00.0 0280: 14e4:4311 (rev 01) 
```
_Ubuntu Version:_
Ubuntu 7.10 - Fresh install
_Kernel / Architecture:_
2.6.22-14-generic i686
No compiling NDISWrapper
Step 2b

---

### Post by aatiis on 2007-12-04
HP nx6325
30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
30:00.0 0280: 14e4:4312 (rev 01)
Ubuntu 7.10 (actually it's a Kubuntu)
2.6.22-14-generic x86_64
no extra boot options - sudo cat /boot/grub/menu.lst | grep vmlinuz-2.6.22:
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f57d068d-506b-4d83-ad68-3df96c18c56d ro quiet splash

The reason I have compiled ndiswrapper 1.50 is that I tried with the wrong windows driver first, so I thought that was the problem. I think it should have worked with the binaries from the repo.

I used step 2b ([ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe))

It works perfectly.

---

### Post by Jamie Jackson on 2007-12-05
> **aatiis said:**
> HP nx6325
30:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
30:00.0 0280: 14e4:4312 (rev 01)
Ubuntu 7.10 (actually it's a Kubuntu)
2.6.22-14-generic x86_64
no extra boot options - sudo cat /boot/grub/menu.lst | grep vmlinuz-2.6.22:
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f57d068d-506b-4d83-ad68-3df96c18c56d ro quiet splash

The reason I have compiled ndiswrapper 1.50 is that I tried with the wrong windows driver first, so I thought that was the problem. I think it should have worked with the binaries from the repo.

I used step 2b ([ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe))

It works perfectly.

Congrats! That's a new device to the wiki, so thanks for all the details--I've added them.

Jamie

---

### Post by Lorac1949 on 2007-12-05
Sorry to say I'm one of the failures for this fix.  I hope that someone can help me get my wireless connection.  Here's what I have:

Dell Inspiron 1520
Ethernet:  Broadcom Corp BCM4401-BO 100 Base-TX (rev 02)
Network:  Broadcom Corp BCM94311MCG wlan min-PC (rev 01)
Chipset: 0c:00.0 0280: 14c4:4311 (rev 01)
Ubuntu 7.10
Kernel:  2.6.22-14-generic i686
I did have to compile NDISWrapper in fact, I got a "couldn't find package" message at one point
I used step 2b

After I went through the first 3 steps, I was totally encouranged.  For the first time, I saw the wireless signals when I clicked on the Network Manager.  Ah!  Progress, I thought.  However, when I entered my passphrase the 2 computer icon changed to two dots and a swirling graphic.  This continued for several minutes and finally - I was asked for my passphrase again.  This continued until I cancelled it.

I went to System, Administration, Network and where there had NOT been a Wireless icon, there WAS one.  However, there were no settings.  Once I put these in, I rebooted again.  But, this time, when I clicked on Network Manager my only option was "Wired Network."  Aargh!  I could no longer see the wireless connections.

That's when I went to the "Compile and Install New NDISWrapper" section.  After entering the second line, it asked me for my disk and I put it in and it ran a lot of lines of code.  I typed in "sudo apt-get install linux-headers-'uname -r' and the following message came up - at which time I gave up and typed exit:

"couldn't find package linux-headers-uname -r"

I would appreciate whatever help you can give me.  I've just about reached the end of my rope.

---

### Post by rotundrory on 2007-12-08
-Dell Inspiron 6000
-03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
-03:03.0 0280: 14e4:4318 (rev 02)
-Ubuntu 7.10
-2.6.22-14-generic i686

I first used step 2c.  This did not make any wireless networks be recognized.
I then compiled the ndiswrapper from Source.  This didn't change anything.  
I then used step 2a.  This didn't change anything.  I still see no wireless netmorks.  

Any help would be much appreciated.

---

### Post by Lorac1949 on 2007-12-08
For those BCM43xx folks who still can't connect to the Internet via wireless, I'm going to call Dell support tomorrow (Sunday, 9 Dec 07).  Will post the outcome of that call.

---

### Post by benson on 2007-12-08
Acer Aspire 4310
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 14e4:4311 (rev 01)
Ubuntu 7.10 2.6.22-14-generic i686
No boot options
Did not compile ndiswrapper
Step 2b

---

### Post by rotundrory on 2007-12-08
I posted above.  After restarting, I am now getting the list of wireless networks to show up.  When I select the appropriate network, however, I get the "swirling," and the attempt at connecting times out.  Is there a documented fix to this?

---

### Post by JPotter on 2007-12-09
**Wireless Brand and Model:** 00:0b.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
**Wireless Chipset**: 00:0b.0 0280: 14e4:4320 (rev 03)
**Ubuntu Version:** 7.10
**Kernel / Architecture:** 2.6.22-14-generic i686
Step 2b

Thanks a ton! I'm almost brand new to linux  and i've been fighting with my wireless card for a while.  After a clean installation, this guide got me through it in the advertised 5 minutes.  Thanks again!

---

### Post by Jamie Jackson on 2007-12-12
> **Lorac1949 said:**
> Sorry to say I'm one of the failures for this fix.  I hope that someone can help me get my wireless connection.  Here's what I have:

Dell Inspiron 1520
Ethernet:  Broadcom Corp BCM4401-BO 100 Base-TX (rev 02)
Network:  Broadcom Corp BCM94311MCG wlan min-PC (rev 01)
Chipset: 0c:00.0 0280: 14c4:4311 (rev 01)
Ubuntu 7.10
Kernel:  2.6.22-14-generic i686
I did have to compile NDISWrapper in fact, I got a "couldn't find package" message at one point
I used step 2b

After I went through the first 3 steps, I was totally encouranged.  For the first time, I saw the wireless signals when I clicked on the Network Manager.  Ah!  Progress, I thought.  However, when I entered my passphrase the 2 computer icon changed to two dots and a swirling graphic.  This continued for several minutes and finally - I was asked for my passphrase again.  This continued until I cancelled it.

I went to System, Administration, Network and where there had NOT been a Wireless icon, there WAS one.  However, there were no settings.  Once I put these in, I rebooted again.  But, this time, when I clicked on Network Manager my only option was "Wired Network."  Aargh!  I could no longer see the wireless connections.

Sorry about the bad luck. However, when you went into System > Administration > Network and entered wireless info, you took control away from NetworkManager (which, confusingly, is a different application from the System > Administration > Network).

Give control back to NetworkManager with the following
```

echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo /etc/dbus-1/event.d/25NetworkManager restart

```

> 
That's when I went to the "Compile and Install New NDISWrapper" section.  After entering the second line, it asked me for my disk and I put it in and it ran a lot of lines of code.  I typed in "sudo apt-get install linux-headers-'uname -r' and the following message came up - at which time I gave up and typed exit:

"couldn't find package linux-headers-uname -r"


You must have used single quotes around `uname -r`. Instead, you need backticks (the character below the ~ on your keyboard).

```
sudo apt-get install linux-headers-`uname -r`
```

> 

I would appreciate whatever help you can give me.  I've just about reached the end of my rope.

Let's see if that gets you anywhere.

---

### Post by Jamie Jackson on 2007-12-12
> **Lorac1949 said:**
> For those BCM43xx folks who still can't connect to the Internet via wireless, I'm going to call Dell support tomorrow (Sunday, 9 Dec 07).  Will post the outcome of that call.

If they give you any useful information whatsoever, I would be shocked. Therefore, I hope my previous post does you some good. :)

---

### Post by Jamie Jackson on 2007-12-12
> **rotundrory said:**
> I posted above.  After restarting, I am now getting the list of wireless networks to show up.  When I select the appropriate network, however, I get the "swirling," and the attempt at connecting times out.  Is there a documented fix to this?

Could you post the output of "lshw -C network", please?

---

### Post by Jamie Jackson on 2007-12-12
> **Steenmeijer said:**
> Awesome. First reboot the connection died after a few minutes but that may have been the router. Details:

_Machine Brand and Model:_
Acer Aspire 9305AWSMi
_Wireless Brand and Model_:
```
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```
_Wireless Chipset:_
```
01:00.0 0280: 14e4:4311 (rev 01) 
```
_Ubuntu Version:_
Ubuntu 7.10 - Fresh install
_Kernel / Architecture:_
2.6.22-14-generic i686
No compiling NDISWrapper
Step 2b

Thanks for the details, they're up on the wiki.

---

### Post by Jamie Jackson on 2007-12-12
> **benson said:**
> Acer Aspire 4310
Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01) 14e4:4311 (rev 01)
Ubuntu 7.10 2.6.22-14-generic i686
No boot options
Did not compile ndiswrapper
Step 2b

Thanks for the details, I've added them to the wiki.

---

### Post by Lorac1949 on 2007-12-12
> **Jamie Jackson said:**
> Sorry about the bad luck. However, when you went into System > Administration > Network and entered wireless info, you took control away from NetworkManager (which, confusingly, is a different application from the System > Administration > Network).

Give control back to NetworkManager with the following
```

echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo /etc/dbus-1/event.d/25NetworkManager restart

```



You must have used single quotes around `uname -r`. Instead, you need backticks (the character below the ~ on your keyboard).

```
sudo apt-get install linux-headers-`uname -r`
```



Let's see if that gets you anywhere.

I returned control to Network Manager and ran the correct code for `uname -r`  Then I restarted the system.  When I chose my wireless connection I was asked for my passphrase.  It keeps timing out because the request for passphrase box keeps coming up.  Any further suggestions?

---

### Post by Lorac1949 on 2007-12-12
> **Jamie Jackson said:**
> If they give you any useful information whatsoever, I would be shocked. Therefore, I hope my previous post does you some good. :)

You were right about the Dell folks.  My wireless went south in Windows, too.  They helped me connect the Windows side, but the rep didn't even *know* what Ubuntu was.  I talked to her supervisor and he said my driver wasn't designed for Ubuntu.  He said that the various work arounds might work for a short time, but that they would eventually fail.  I even asked to talk to the Dell reps that are working with the Dells that come with Ubuntu installed.  He just repeated that the driver wouldn't handle wireless for Ubuntu.  That's a challenge I'd like to prove wrong.  [Seems like some folks already have!]

---

### Post by xylo04 on 2007-12-13
* Machine Brand and Model: HP dv2415nr
    * Wireless Brand and Model (please post the whole line): 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
    * Wireless Chipset: 01:00.0 0280: 14e4:4311 (rev 02)
    * Ubuntu Version: Ubuntu 7.10 (Gutsy)
    * Kernel / Architecture: 2.6.22-14-generic x86_64
    * Any extra boot options you might be using: none
    * Whether or not you had to compile NDISWrapper: no
    * Which version of Step 2 you used: 2a

This guide worked perfectly for me! The native support in Gutsy was inoperative for me. I tried several other howto's around the forum, some with native support and some with ndiswrapper, with no success. The difference, I think, was the fact that I used the fresh download of sp34125.exe instead of the bcmwl6.inf and bcmwl664.sys I copied from my Vista partition. Either that, or it was the depmod step. Dunno. I'm thrilled that this worked on the x86_64, I thought it might throw me for a loop. Thanks a lot! I just hope it's stable...

---

### Post by Jamie Jackson on 2007-12-13
> **Lorac1949 said:**
> I returned control to Network Manager and ran the correct code for `uname -r`  Then I restarted the system.  When I chose my wireless connection I was asked for my passphrase.  It keeps timing out because the request for passphrase box keeps coming up.  Any further suggestions?

There are two password prompts that come into play: 1) When you first enter your router's passphrase (for WEP or WPA, etc.). 2) Once you've entered that and let Ubuntu's keyring remember it, you will simply use your Ubuntu login password when you get the generic keyring prompt.

So, do you or don't you have a password protected router? If you do, is it not accepting the proper password? Alternatively, have you tried temporarily removing the encryption, so that you can see if you can connect without it?

---

### Post by Jamie Jackson on 2007-12-13
> **Lorac1949 said:**
> You were right about the Dell folks.  My wireless went south in Windows, too.  They helped me connect the Windows side, but the rep didn't even *know* what Ubuntu was.  I talked to her supervisor and he said my driver wasn't designed for Ubuntu.  He said that the various work arounds might work for a short time, but that they would eventually fail.

That's just a strange thing to say. He is a confused person.

---

### Post by kvonb on 2007-12-14
-

---

### Post by Lorac1949 on 2007-12-14
> **Jamie Jackson said:**
> There are two password prompts that come into play: 1) When you first enter your router's passphrase (for WEP or WPA, etc.). 2) Once you've entered that and let Ubuntu's keyring remember it, you will simply use your Ubuntu login password when you get the generic keyring prompt.

So, do you or don't you have a password protected router? If you do, is it not accepting the proper password? Alternatively, have you tried temporarily removing the encryption, so that you can see if you can connect without it?

In the steps above, I entered my WEP passphrase when the login screen came up and clicked Log into Network.  I placed my cursor over the spinning icon and it said Waiting for Network Key for [name of my network]  I don't think it was sent and Keyring doesn't come up nor does it show anything when I open Keyring.

The router is password protected [with a different password than the WEP one].  I've tried both passwords and I still can't connect to the Internet.

I haven't tried removing the encryption.  First, is that a good idea?  Do I open my system up to attack?  Second, how would I go about that?  Would that be through the access to the router?  Network savvy, I am not.

---

### Post by Jamie Jackson on 2007-12-16
> **Lorac1949 said:**
> In the steps above, I entered my WEP passphrase when the login screen came up and clicked Log into Network.  I placed my cursor over the spinning icon and it said Waiting for Network Key for [name of my network]  I don't think it was sent and Keyring doesn't come up nor does it show anything when I open Keyring.

The router is password protected [with a different password than the WEP one].  I've tried both passwords and I still can't connect to the Internet.

I haven't tried removing the encryption.  First, is that a good idea?  Do I open my system up to attack?  Second, how would I go about that?  Would that be through the access to the router?  Network savvy, I am not.

Some people never run encryption on their routers, and the worst that usually happens is that a neighbor uses their Internet.

So, it should definitely not be a problem to temporarily remove the WEP encryption. You're just doing it long enough for you to check to see whether you can connect without it. Even if you left it unprotected for years, it's unlikely that you'd ever have a hack attempt, though it's likely that someone would eventually borrow your bandwidth.

Another note: Sometimes, my keyring password prompt hides behind other windows, so watch out for that. 

With that said, most people do decide to use encryption, so if you get a successful unencrypted connection, you could take the next step and try encryption. If your router supports WPA encryption use that, because WEP is fairly easily crackable. Therefore, if you're security-conscious, you might as well use an encryption protocol that works.

---

### Post by Jamie Jackson on 2007-12-16
> **kvonb said:**
> Hewlett Packard Pavilion 6645eg (KA057EA#ABD) laptop.

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

03:00.0 0280: 14e4:4312 (rev 02)

Description:    Ubuntu 7.10  

2.6.22-14-generic i686

NO extra boot options, standard ndiswrapper from repos, used step 2a (sp34152.exe)

Kubuntu, new install but I did install the restricted drivers for both the Broadcom & Nvidia video card.  The wireless didn't work with the "restricted driver" so I followed the instructions here:
 [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-d8ce0e35a4ccdbeddd6cf36f9cb23a11d8e0e9dc)

and the blue light came on and I got a list of wireless networks.

My network uses WPA2 personal which was automatically detected and all I had to do was enter my network password.

It is running at 54mbps as well :).

Excellent work, thanks :D.

That's a new device to this thread (and the wiki), so extra thanks for the juicy details--they've been incorporated into the wiki.

---

### Post by Lorac1949 on 2007-12-16
Some of the folks who've posted here may want to check this out:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by Jamie Jackson on 2007-12-17
> **Lorac1949 said:**
> Some of the folks who've posted here may want to check this out:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

It's not clear whether or not your problem is solved. If it is, what was the trick?

---

### Post by Lorac1949 on 2007-12-17
> **Jamie Jackson said:**
> It's not clear whether or not your problem is solved. If it is, what was the trick?

Thanks for asking.  I'm still using a cable for Ubuntu Internet connections.  After a bit more work, I'm down to doing a fresh install or buying a compatible ExpressCard.  I posted the link in response to one of the posts in this thread.  Thought it might save some time for folks with this problem.

---

### Post by Yves-Michel on 2007-12-17
I am very happy that WiFi works now.
HP Compaq 6715b Turion X2 TL60 AMD64, Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
I tried many HowTo's, but this is the one that worked right after 5 minutes.
Many thanks

p.s. First i tried bcmwl6.inf, but did not work, but bcmwl5.inf trouble-free.

---

### Post by Jamie Jackson on 2007-12-17
> **Yves-Michel said:**
> I am very happy that WiFi works now.
HP Compaq 6715b Turion X2 TL60 AMD64, Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
I tried many HowTo's, but this is the one that worked right after 5 minutes.
Many thanks

p.s. First i tried bcmwl6.inf, but did not work, but bcmwl5.inf trouble-free.

Congrats, Yves-Michel. If you get a chance, could you please provide the details specified in the first post of this thread? Thanks!

---

### Post by Jamie Jackson on 2007-12-18
> **HW_Hack said:**
> Jamie

Great job in doing both this thread AND the How To Page !!!  Us poor sots who unknowingly bought or got a laptop with this Anti-Christ chipset owe you some thanks !!

I ended up having to do the ndiswrapper compile to make it work. And there is no surprise there - I've reloaded Ubuntu a few time on my Dell B130 Inspiron and learned to muddle through following various how to's ---- so far the other best how to is at the Ndiswrapper site 

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

And in my recollection this particular demonic version of the 4318 requires a very specific windows driver  ..... and its not the one that Dell offers on its site for my B130.

Doing your standard install for a    14e4:4318 (rev 02)   led me to step 2C   -- on reboot my wireless LED lit up - but no wireless networks were listed. Your instructions mentioned trying step 2A if that failed ---- but looking at the recompile section I recognized several steps from past forays  in getting wireless to work.

Meanwhile THATS THAT !!!  No more fiddling around -- I'm going to make a disk image copy of this install and moving on:guitar:
    *

      Machine Brand and Model               Dell Inspiron B130
    *

      Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


    *

      Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
02:03.0 0280: 14e4:4318 (rev 02)
    *

      Ubuntu Version: lsb_release -d
Description:    Ubuntu 7.04

    *

      Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.20-16-generic i686

    *

      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)      No boot options used
    *

      Whether or not you had to compile NDISWrapper    Yes 
    *

      Which version of Step 2 you used              2C

I somehow missed this post before. Thanks for the details and the nice words. You're info's up on the wiki.

---

### Post by Jamie Jackson on 2007-12-18
> **besseresser said:**
> Hi, Thank you for this helpful guide :)

I have an HP G7000 laptop. Everything seems to work fine, except the laptop's w-lan on/off switch, It does nothing. I didn't have to compile ndiswrapper manually, and step 2a was used.

**lspci output:** 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

**chipset**: 01:00.0 0280: 14e4:4311 (rev 02)

Ubuntu 7.10; 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64

Thanks, I missed your post before. Your details are on the wiki now.

---

### Post by marcabru07 on 2007-12-21
Hello

I had partial success. I mean my wifi light is on and I can recognize some wireless networks but when I try to get connected it just don't work. I can not have connection even in a open (not password) network

I have an DELL INSPIRON 6400 with 0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
I followed up each step and did the 2b step according to the table, I also tried with the "No Luck Yet? Compile ndiswrapper from Source" steps but I had the same, so if you have any suggestion for me, you are welcome


PLZ HELP!!!

---

### Post by bhavinjo on 2007-12-28
Hi,
    Had complete success using the tutorial. Thanks so much.

Heres all the details:

      Machine Brand and Model
    * Gateway 7508GX laptop

      Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
    *03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

      Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
    *03:07.0 0280: 14e4:4318 (rev 02)

      Ubuntu Version: lsb_release -d
    *Description:    Ubuntu 7.10


      Kernel/architecture (including 32 vs. 64 bit) : uname -mr
    *2.6.22-14-generic i686

      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
    *none

      Whether or not you had to compile NDISWrapper
    *no

      Which version of Step 2 you used
      2c

-Bhavin

---

### Post by evertmantel on 2007-12-28
It worked well, but only after the latest kernel update to 2.6.22.14.Before the light went on, but I could not see any wireless networks. At last I got rid of the dongle I used as a work around! 
<newbie> on HP pavillion dv6550 laptop

---

### Post by obsidiandh on 2007-12-28
This worked perfectly on my acer aspire 5051AWXMi, using broadcom 4318 rev2, no issues at all and no need to compile anything :) thank you very much

---

### Post by jbloodwo on 2007-12-29
I will give this a try in a few min after i boot back over to 7.10 form xp
here is the information from the draft N card in my Vostro 1400.

<hr>
john@john-laptop:/media/sda5/ubuntu$ lspci |grep -i broad
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
john@john-laptop:/media/sda5/ubuntu$ lspci -n|grep -i 0c:00.0
0c:00.0 0280: 14e4:4328 (rev 03)
john@john-laptop:/media/sda5/ubuntu$ sudo lspci -v -v -d 14e4:4328
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        Region 2: Memory at f0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [d0] Express Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM unknown, Port 0
                Link: Latency L0s <4us, L1 <64us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

john@john-laptop:/media/sda5/ubuntu$

---

### Post by Jamie Jackson on 2007-12-29
> **marcabru07 said:**
> Hello

I had partial success. I mean my wifi light is on and I can recognize some wireless networks but when I try to get connected it just don't work. I can not have connection even in a open (not password) network

I have an DELL INSPIRON 6400 with 0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
I followed up each step and did the 2b step according to the table, I also tried with the "No Luck Yet? Compile ndiswrapper from Source" steps but I had the same, so if you have any suggestion for me, you are welcome


PLZ HELP!!!

You might want to try using step 2a instead of step 2b. There are a couple of users that reported success with 2a when 2b wouldn't work. [Here]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273")'s how to try another driver.

---

### Post by Jamie Jackson on 2007-12-29
> **jbloodwo said:**
> I will give this a try in a few min after i boot back over to 7.10 form xp
here is the information from the draft N card in my Vostro 1400.

<hr>
john@john-laptop:/media/sda5/ubuntu$ lspci |grep -i broad
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
john@john-laptop:/media/sda5/ubuntu$ lspci -n|grep -i 0c:00.0
0c:00.0 0280: 14e4:4328 (rev 03)
john@john-laptop:/media/sda5/ubuntu$ sudo lspci -v -v -d 14e4:4328
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
        Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-card
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at fe8fc000 (64-bit, non-prefetchable) [size=16K]
        Region 2: Memory at f0000000 (64-bit, prefetchable) [size=1M]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [d0] Express Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s <4us, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM unknown, Port 0
                Link: Latency L0s <4us, L1 <64us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

john@john-laptop:/media/sda5/ubuntu$

I have some special instructions for you, if you're game. First, I'd like you to try step 2d. If that doesn't work,* don't* go on to the ndiswrapper compilation instructions. You probably don't need to compile, you probably just need another driver. So, if 2d fails, please try the other drivers (the other step 2s) listed on the wiki. [Here]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273") are instructions for trying different drivers.

If none of those drivers work, this one is near certain to. [Another user]("http://ubuntuforums.org/showpost.php?p=3776902&postcount=282") reported that this driver works with the 4328 rev 03: [ftp://ftp.us.dell.com/network/R151517.EXE]("ftp://ftp.us.dell.com/network/R151517.EXE")

Let me know if you need instructions on unpacking and installing this driver.

You might be wondering why I'm asking you to try the drivers that are already on the wiki, even though I'm near certain that this new driver will work. This is because if one of the existing drivers works, then I don't have to add any extraneous new drivers to the wiki. I want to avoid adding anything unnecessary. However, if none of the existing drivers work, and the new one does, I'll be happy to add it to the wiki.

Finally, when you get wireless working, *please* post all of the information that I ask for in the first post of this thread, as it's especially important that I have all the information for any new (to the wiki) devices.

---

### Post by jbloodwo on 2007-12-30
ok here is the list of the stuff from your first post.  I was running out the door when i made the first post and all is working now using 2d. I had already done 2d before i saw your reply. 
<hr>


      Machine Brand and Model : 

Dell Vostro 1400

      Wireless Brand and Model : 

john@john-laptop:~$ lspci | grep Broadcom
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

      Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
0c:00.0 0280: 14e4:4328 (rev 03)
    *

      Ubuntu Version: lsb_release -d
Description:    Ubuntu 7.10


      Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.22-14-generic x86_64
    *

      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
    *

      Whether or not you had to compile NDISWrapper

Nope. 

      Which version of Step 2 you used 
sorta 2d
I was in process of downloading 151517 when i saw the repackage and just unziped the self extracting archive. 
then i used the drivers in the driver folder.  The only strange this is I was not aple to get DHCP to assign an ip adress after entering my wepkey until after i assigned a static adress and then went back to DHCP

<hr>
anyway I am posting this from 7.10 and all is working well with the wireless.

---

### Post by Jamie Jackson on 2007-12-30
> **jbloodwo said:**
> ok here is the list of the stuff from your first post.  I was running out the door when i made the first post and all is working now using 2d. I had already done 2d before i saw your reply. 
<hr>


      Machine Brand and Model : 

Dell Vostro 1400

      Wireless Brand and Model : 

john@john-laptop:~$ lspci | grep Broadcom
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

      Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
0c:00.0 0280: 14e4:4328 (rev 03)
    *

      Ubuntu Version: lsb_release -d
Description:    Ubuntu 7.10


      Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.22-14-generic x86_64
    *

      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
    *

      Whether or not you had to compile NDISWrapper

Nope. 

      Which version of Step 2 you used 
sorta 2d
I was in process of downloading 151517 when i saw the repackage and just unziped the self extracting archive. 
then i used the drivers in the driver folder.  The only strange this is I was not aple to get DHCP to assign an ip adress after entering my wepkey until after i assigned a static adress and then went back to DHCP

<hr>
anyway I am posting this from 7.10 and all is working well with the wireless.

Thanks for the details. By the way, roughly after the latest kernel upgrade (2.6.22-14-generic i686), DHCP stopped working for me too, so I reset my router and removed encryption, for the time being (at which point, DHCP began to work again). I thought it was a router problem, but I now wonder if the kernel upgrade broke DHCP when encryption is on. I don't know... I'll have to look into it some more...

---

### Post by gmcauley on 2008-01-01
Worked perfectly (although I did not want to try WPA yet).

HP dv2312us, Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01), 14e4:4311 (rev 01),  Ubuntu 7.10, 2.6.22-14-generic i686, did not have to compile, used 2b with 'ftp.hp.com' link.

Previously used restricted driver. Now with ndis I can connect in a corner of my house that I could not before.  Thank you for the HowTo!

---

### Post by greenagain on 2008-01-02
This worked great to get my d800 with the following card up an running under Gutsy

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


If you're having speed problems with the broadcom restricted driver via the fwcutter, I would recommend this.

---

### Post by Dr. Cox on 2008-01-02
hi there,

I'm using a dell vostro 1000 with the following wireless components.
i'm running ubuntu 7.10
> 05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


> 05:00.0 0280: 14e4:4311 (rev 01)

> 2.6.22-14-generic i686

i've followed your easy to use howto (am very grateful as it is not the first i've unsuccessfully tried).
however, i made a littel mistake and used step 2d instead of 2b as i should've. it is still working, though.

HOWEVER, i have the feeling that at the same spot in which vista gives me 80% signal ubuntu only comes up with 30% and less. could that be due to my faulty installation? should i try to undo it and try 2a or 2b correctly?

EDIT:
I've reversed that and followed the appropriate step 2b for my chipset. still, when in the room 2m away from my wireless router network-manager still only shows 80% connection? is that problem a broadcom prob? is it ndiswrapper?

---

### Post by Jamie Jackson on 2008-01-05
> **Dr. Cox said:**
> hi there,

I'm using a dell vostro 1000 with the following wireless components.
i'm running ubuntu 7.10

i've followed your easy to use howto (am very grateful as it is not the first i've unsuccessfully tried).
however, i made a littel mistake and used step 2d instead of 2b as i should've. it is still working, though.

HOWEVER, i have the feeling that at the same spot in which vista gives me 80% signal ubuntu only comes up with 30% and less. could that be due to my faulty installation? should i try to undo it and try 2a or 2b correctly?

EDIT:
I've reversed that and followed the appropriate step 2b for my chipset. still, when in the room 2m away from my wireless router network-manager still only shows 80% connection? is that problem a broadcom prob? is it ndiswrapper?

Unfortunately, I don't have any experience troubleshooting ndiswrapper speed/connection strength issues. FWIW, could you post the output of "lshw -C network" and "iwlist" (just the parts relevant to your wireless device)?

---

### Post by gmcauley on 2008-01-06
> **Dr. Cox said:**
> 
I've reversed that and followed the appropriate step 2b for my chipset. still, when in the room 2m away from my wireless router network-manager still only shows 80% connection? is that problem a broadcom prob? is it ndiswrapper?
 

I am seeing something similar - connection with lower percentages than with Vista.  What is weird is before I used the restricted driver and there was a place in my house that I could not connect to.  With ndis now I can connect at this location, however the displayed percentage is *lower* than with the restricted driver.  This is not an issue at home b/c I can now connect and stay connected.  However, at the most important location at school the connection quality is low enough that only Windows allows a usable connection.  This is a bit frustrating since I really do not want to use Windows there.

---

### Post by Jamie Jackson on 2008-01-06
> **gmcauley said:**
> I am seeing something similar - connection with lower percentages than with Vista.  What is weird is before I used the restricted driver and there was a place in my house that I could not connect to.  With ndis now I can connect at this location, however the displayed percentage is *lower* than with the restricted driver.  This is not an issue at home b/c I can now connect and stay connected.  However, at the most important location at school the connection quality is low enough that only Windows allows a usable connection.  This is a bit frustrating since I really do not want to use Windows there.

Yeah, that *would* be frustrating.

It could be a difference between XP and Vista drivers, as we're using XP drivers in the wiki ([ndiswrapper doesn't support vista drivers yet]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")).

---

### Post by Jamie Jackson on 2008-01-09
Note: For folks who have to compile ndiswrapper, the download now points to the new 1.51 version.

---

### Post by kij01 on 2008-01-13
My laptop and wlan configuration is Acer (Aspire 3004WLMI), BCM4318(rev 02), Ubuntu 7.04 (2.6.20-15-generic i686).
I did not need to compile NDISWrapper (Step 2c) and my network connection working with success.

---

### Post by ebe0 on 2008-01-15
Hi,
I have the following notebook specs and ndiswrapper(did not need to compile it) works great with it...

Machine Brand and Model: [[COLOR="Blue"]_HP Pavilion dv6502AU Notebook PC_[/COLOR]]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01184507&cc=in&dlc=en&lc=en&jumpid=reg_R1002_INEN#")
Wireless Brand and Model: Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
Wireless Chipset: 14e4:4312 (rev 02)
Ubuntu Version: Ubuntu 7.10
Kernel/architecture (including 32 vs. 64 bit) : 2.6.22-14-generic i686
Any extra boot options you might be using: none
Whether or not you had to compile NDISWrapper: No
Which version of Step 2 you used: Step 2a

Thanks all for your help and support.

---

### Post by ptuamyim on 2008-01-16
I have following NB detail, and it's work great, Thank you for this help,

Machine Brand and Model: **Compaq, B1917TU**
Wireless Brand and Model: **02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)**
Wireless Chipset: **02:00.0 0280: 14e4:4311 (rev 01)**
Ubuntu Version: **Ubuntu 7.10**
Kernel/architecture (including 32 vs. 64 bit) : **2.6.22-14-generic i686**
Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.): **NA**
Whether or not you had to compile NDISWrapper: **No**

---

### Post by slim shady on 2008-01-21
Success, Dell Inspiron 1721, AMD 64 , 64 bit Gutsy for AMD , Dell Mini 1502, Wlan card BCM 4328.  

0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
 14e4:4328 (rev 03)
Ubuntu 7.10
2.6.22-14-generic x86_64
did not compile NDIS
step 2d
 
Thanks for the how to, I have been at this for months and now can use my wireless. I am grateful for the work.

---

### Post by YQuaresma on 2008-01-23
SUCCESS

Machine Brand and Model: HP Pavillion DV2000
Wireless Brand and Model: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Wireless Chipset: 14e4:4311 (rev 01)
Ubuntu Version: Ubuntu 7.10
Kernel/architecture (including 32 vs. 64 bit) : 2.6.22-14-generic i686 (32bits) 
Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.) : None
Whether or not you had to compile NDISWrapper: I had not to compile
Which version of Step 2 you used : Step 2a

I needed to download the file SP34152.exe from HP site. Here is the location:
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe]("ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe")

Thanks

Yuri Quaresma

---

### Post by olegas on 2008-01-25
SUCCESS

    * Machine Brand and Model: Dell Ispiron 1501
    * Wireless Brand and Model (please post the whole line): 05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

    * Wireless Chipset:05:00.0 0280: 14e4:4311 (rev 01)

    * Ubuntu Version: Ubuntu 7.10

    * Kernel / Architecture: 2.6.22-14-generic x86_64

    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)  none
    * Whether or not you had to compile NDISWrapper  not
    * Which version of Step 2 you used: 2a

---

### Post by thogland on 2008-01-27
Success. 

      Machine Brand and Model - Dell Inspiron 8000
      Wireless Brand and Model (please post the whole line): Motorola WN825G
      Wireless Chipset: Broadcom 4306
      Ubuntu Version: 7.10 - Gutsy Gibbon
      Kernel/architecture (including 32 vs. 64 bit) : 2.6.22 generic 32bit
      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.) noapic nolapic pci=noacpi
      Whether or not you had to compile NDISWrapper: Nope - installed from synaptic
      Which version of Step 2 you used: step 2b

The restricted firmware *said* it connected, but never actually let me in. Didn't spend a ton of time with it, though - entirely possible it would have worked if I spent a bit working on it. Having said that, giving it the connect info did *not* work, while providing the same info to ndiswrapper worked immediately.

Also, this connects to a FON router, thence to a Motorola router and out via DSL.

---

### Post by 12ax7 on 2008-02-01
SUCCESS

my first post but had to say thanks for the great writeup.  I tried all of them and finally found this one.  I am a total n00b with ubuntu but am liking it.  The "distilled" version of the article was perfect.  I followed the steps exactly, now I have wireless!

HP Pavillion dv6445 with a Broadcom 4312 rev 02 chipset.  USE STEP 2A

gutsy 7.10 amd64 build
gnome 2.20.0


Thanks again!

---

### Post by Growlor on 2008-02-02
Success.

Machine Brand and Model - Acer Extensa 5420-5687
Wireless Brand and Model (please post the whole line): 05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Wireless chipset: 05:00.0 0280: 14e4:4311 (rev 01)
Ubuntu Version: Description:    Ubuntu 7.10
Kernel/architecture (including 32 vs. 64 bit) : 2.6.22-14-generic x86_64
Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.) I don't know how to check this-sorry.
Whether or not you had to compile NDISWrapper: No. I followed your instructions and had no significant issues.
Which version of Step 2 you used: Step 2b.

Your directions worked very well, thank you! The only issue so far (no big deal at all) is that the wireless light doesn't turn-on. 
I tried some other instructions for using the native bcm43xx driver, but could not get it to actually connect (maybe it doesn't like WPA with AES or doesn't like it in AM64 mode? - just guessing.) Using NDIS wrapper via your guide has me up and running now with my encryption in place.
Now I need to get some feedback to the guys running the Hardy project as I tried to boot from the latest Alpha CD (just downloaded and burned it tonight) and it didn't even complete the boot process (the b43 driver kept complaining about missing firmware rev 4 over and over) Hopefully they can get the native mode driver running 100% with the new b43 driver. For now, I can play with Ubuntu (I have mostly used Mandriva in the past) and see how I like all this apt-get... stuff instead of rpm...

Thanks again,
Growlor

---

### Post by Jamie Jackson on 2008-02-02
> **12ax7 said:**
> SUCCESS

my first post but had to say thanks for the great writeup.  I tried all of them and finally found this one.  I am a total n00b with ubuntu but am liking it.  The "distilled" version of the article was perfect.  I followed the steps exactly, now I have wireless!

HP Pavillion dv6445 with a Broadcom 4312 rev 02 chipset.  USE STEP 2A

gutsy 7.10 amd64 build
gnome 2.20.0


Thanks again!

Nice nickname. :guitar:

---

### Post by marildo on 2008-02-04
Did somebody try this on Hardy Heron? I'm testing 8.04 on my dv6220BR and I would wish some reports about this experience.

marildo@marildo-laptop:~$ uname -mr
2.6.24-5-generic i686
marildo@marildo-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
marildo@marildo-laptop:~$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
03:00.0 0280: 14e4:4311 (rev 01)
marildo@marildo-laptop:~$ lsb_release -d
Description:	Ubuntu hardy (development branch)
 
thanks,
Marildo

---

### Post by Jamie Jackson on 2008-02-04
> **marildo said:**
> Did somebody try this on Hardy Heron? I'm testing 8.04 on my dv6220BR and I would wish some reports about this experience.

marildo@marildo-laptop:~$ uname -mr
2.6.24-5-generic i686
marildo@marildo-laptop:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
marildo@marildo-laptop:~$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
03:00.0 0280: 14e4:4311 (rev 01)
marildo@marildo-laptop:~$ lsb_release -d
Description:	Ubuntu hardy (development branch)
 
thanks,
Marildo

I can't imagine that it wouldn't work (unless there are major underlying networking bugs in Hardy). 

How's native support working, by the way? (I guess via the Restricted Drivers Manager?) I guess it's not working, considering you're trying this howto?

---

### Post by marildo on 2008-02-05
> **Jamie Jackson said:**
> I can't imagine that it wouldn't work (unless there are major underlying networking bugs in Hardy). 

How's native support working, by the way? (I guess via the Restricted Drivers Manager?) I guess it's not working, considering you're trying this howto?

It seems that it worked. I just (still) don't have a wireless net nearby to test it. When it's possible, I'll post it.

thanks,
Marildo

---

### Post by gtantot on 2008-02-05
Success, without having to compile ndiswrapper =D>
With Step 2a

HP / Compaq 6720s
 Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

 lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
 14e4:4311 (rev 02)

Ubuntu 7.10
generic i686

---

### Post by mmbates on 2008-02-11
It worked for me!

Machine Brand and Model: Home assembled -- Gigabyte GA-MA790FX-DQ6 motherboard, AMD Phenom 9600 processor, ASUS WL-138g V2 wireless PCI card

$ lspci | grep Broadcom
06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
06:06.0 0280: 14e4:4318 (rev 02)

$ lsb_release -d
Description:    Ubuntu 7.10

$ uname -mr
2.6.22-14-generic x86_64

I have had a similar experience as Poobslag, I had to use 2a, rather than 2c as initially suggested.  While I did recompile Ndiswrapper after following 2c, and before trying 2a, I am not sure whether this had anything to do with it working using 2a (I doubt it -- recompiling and then trying step 2c did not work).

I also did a fresh install, as I had tried mucking about with the settings using other howto's previously.

Thanks for this howto, I definitely would not have been able to get this working without it.

I had trouble connecting to my router after the driver started working, but Kevdog's fantastic howto saved the day.  [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) -- so thanks for that Kevdog too.

cheers,
Michael

Epilogue:
G'day again,
I had troubles getting this card to behave once the drivers were properly installed (it scanned ok, would sometimes get a connection, but the connection was slow and unstable) .  You can read about it on this post [http://ubuntuforums.org/showthread.php?p=4391951#post4391951](http://ubuntuforums.org/showthread.php?p=4391951#post4391951) (and ones that follow) for the specifics.  It is worth mentioning that I am still using the above card on my old dinosaur and this card worked out of the box without any problems in 32 bit Gutsy.  I now have an atheros chipset card which worked out of the box (in Sidux Eros at least, I haven't tested it in Gutsy -- that's another long story in itself).

cheers,
Michael

---

### Post by verydeep on 2008-02-14
Hello..

Here are my specs..

Machine Brand and Model = Compaq Presario V3702AU
Wireless Brand and Model = 04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
Wireless Chipset = 04:00.0 0280: 14e4:4315 (rev 01)
Ubuntu Version = Kubuntu 7.04 64-bit
Kernel = 2.6.20-15-generic
Extra boot options = none
Had to compile NDISWrapper 1.51
Had to download a different file : [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

Wow! Dell driver for Compaq laptop! And the best part is official Compaq drivers won't work :)

After a whole month of struggle, i managed to get my wifi running :guitar:

---

### Post by brunoscunha on 2008-02-22
* **Machine Brand and Model:** hp-compaq 6910p
* **Wireless Brand and Model (please post the whole line):** 10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
* **Wireless Chipset: 10:00.0 0280:** 14e4:4312 (rev 02)
* **Ubuntu Version:** Ubuntu 7.10 64 bits
* **Kernel / Architecture:** 2.6.22-14-generic x86_64
* **Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.):** None
* **Whether or not you had to compile NDISWrapper:**No
* **Which version of Step 2 you used:**sp34152

Sometimes it works, sometimes it does not work :(

---

### Post by harry000 on 2008-02-23
**_Testimonial_**

**Machine Brand and Model:** HP Pavillion dv5000 (AMD64)

**Wireless Brand and Model:** :06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**Wireless Chipset:** lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'

**Ubuntu Version:** Ubuntu 7.10 (Gutsy)

**Kernel/architecture (including 32 vs. 64 bit):** 2.6.22-14-generic x86_64

**Any extra boot options:** No

**Whether or not you had to compile NDISWrapper:** NO

**Which version of Step 2 you used:** 2c was recommended, but did not worked. **2a worked for me** (same as Poobslag)

---

### Post by Nordkraft on 2008-03-03
Hi there!

First of all, thanks for the brilliant how-to :)

It worked like a charm for me initially. However, having upgraded to 2.6.22-14, it all of sudden stopped working. I really have no idea what causes this but the wifi is not functioning at all, it seems. Any suggestions?

Specs: 
hp dv6000-series
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) (i.e. install method 2a)

Any help would be much appreciated.

---

### Post by Liberator on 2008-03-04
GREAT GUIDE!

    * Machine Brand and Model:  Dell Vostro 1000 laptop

    * Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

    * Wireless Chipset: lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
05:00.0 0280: 14e4:4311 (rev 01)

    * Ubuntu Version: lsb_release -d
Description:    Ubuntu 7.10

    * Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.22-14-generic i686

    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
None that I know of (where would I find this?)

    * Whether or not you had to compile NDISWrapper
No; I had already installed it via Synaptic.

    * Which version of Step 2 you used
2B

NOTE:  None of the "Gutsy" drivers work reliably.  The restricted drivers are flakey and will work intermittently just enough to drive you crazy debugging the problems.  After firing up using your method it all just works.  THANK YOU!  :)

---

### Post by Worp8d on 2008-03-04
Dell Latitude D531

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

glen@rhd-88kjt1s:~$ lspci -n | egrep '14e4:43(06|07|11|12|18|19|21|24|25|28)'
0b:00.0 0280: 14e4:4311 (rev 01)

glen@rhd-88kjt1s:~$ lsb_release -d
Description:    Ubuntu 7.10

glen@rhd-88kjt1s:~$ uname -mr
2.6.22-14-generic i686

Step 2b installed okay but didn't work.
Tried step 2a and it works.

Got 45% signal strength from one room away; not prepared to see whether or not the connection is slow at this stage.  Thanks to all concerned for the help!

---

### Post by Jamie Jackson on 2008-03-04
> **Nordkraft said:**
> Hi there!

First of all, thanks for the brilliant how-to :)

It worked like a charm for me initially. However, having upgraded to 2.6.22-14, it all of sudden stopped working. I really have no idea what causes this but the wifi is not functioning at all, it seems. Any suggestions?

Specs: 
hp dv6000-series
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) (i.e. install method 2a)

Any help would be much appreciated.

Did you compile ndiswrapper the first go-round? If so, you might want to uninstall that and try the packaged ndiswrapper (or recompile and reinstall ndiswrapper).

Also, would you please paste the output of "lshw -C network"?

---

### Post by Jamie Jackson on 2008-03-04
> **brunoscunha said:**
> * **Machine Brand and Model:** hp-compaq 6910p
* **Wireless Brand and Model (please post the whole line):** 10:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
* **Wireless Chipset: 10:00.0 0280:** 14e4:4312 (rev 02)
* **Ubuntu Version:** Ubuntu 7.10 64 bits
* **Kernel / Architecture:** 2.6.22-14-generic x86_64
* **Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.):** None
* **Whether or not you had to compile NDISWrapper:**No
* **Which version of Step 2 you used:**sp34152

Sometimes it works, sometimes it does not work :(

It's hard for me to diagnose intermittent issues, unfortunately, but what's the output of "lshw -C network", by the way?

---

### Post by Nordkraft on 2008-03-04
Thanks for your reply:)

No I did not compile the ndiswrapper - method 2a simply worked...before the kernel upgrade that is. 

Here's the output:

```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 0a:56:73:24:1b:00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=192.168.1.34 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:83:ea:4d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

Would you recommend that I install the ndiswrapper then (either via Synaptic or compiling)?

Thanks

---

### Post by Worp8d on 2008-03-05
Just for completeness I'll add that downloads are running at about 1/5th the speed they would if the connection was wired.

---

### Post by Jamie Jackson on 2008-03-06
> **Nordkraft said:**
> Thanks for your reply:)

No I did not compile the ndiswrapper - method 2a simply worked...before the kernel upgrade that is. 

Would you recommend that I install the ndiswrapper then (either via Synaptic or compiling)?

Thanks

I doubt ndiswrapper's the problem. Trying step 2b might be worth a shot, though. [Here are some instructions]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273") for trying a new driver.

---

### Post by Nordkraft on 2008-03-07
Thank you for your reply! 
I will try this as soon as I get home... I'm still quite puzzled about the sudden break down of my wireless connection though. I wonder what happened during the kernel upgrade. In the wiki, you mention: "With the 2.6.22-14-generic kernel upgrade, there may be a problem with DHCP when encryption is enabled on the router"; do you think this could somehow (don't ask me how) be connected to that specific issue?
Thanks

---

### Post by Jamie Jackson on 2008-03-07
> **Nordkraft said:**
> Thank you for your reply! 
I will try this as soon as I get home... I'm still quite puzzled about the sudden break down of my wireless connection though. I wonder what happened during the kernel upgrade. In the wiki, you mention: "With the 2.6.22-14-generic kernel upgrade, there may be a problem with DHCP when encryption is enabled on the router"; do you think this could somehow (don't ask me how) be connected to that specific issue?
Thanks

Yeah, I guess it could be. I hardly remember writing that note (that's why I write things down, I guess), but I guess you could try disabling encryption temporarily, and seeing if you can connect afterwards.

If you've got two green circles in your nm-applet icon (showing you're connected with your router), but you can't access the internet, it seems likely that it's a DHCP problem.

---

### Post by Chxta on 2008-03-09
The instructions given [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") worked like a drug.

---

### Post by ryan22158 on 2008-03-11
I finally got my wireless to work, I did follow another walk through before I had tried this one so i think some thing was messed up. So I had to compile ndsiwrapper but after I did that and figured out my WPA key and I am up and running. Thank you so much!!!

Specs
Hp dv2615nr
Amd turion 64 x2 TL-58 1.9ghz
160gb(110 vista, 10 hp recovery, and 40 for ubuntu)
2gb RAM
Geforce 7150m
broadcom 4311(rev 2)

---

### Post by feminaexlux on 2008-03-12
**Failure? :(**

* Machine Brand and Model
**Dell Vostro 1000 AMD64 Athlon X2**
    * Wireless Brand and Model (please post the whole line):
**05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)**
    * Wireless Chipset:
**05:00.0 0280: 14e4:4311 (rev 01)**
    * Ubuntu Version:
**Ubuntu hardy (development branch)**
    * Kernel / Architecture:
**2.6.24-11-generic x86_64**
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
**Nothing special. Fresh install, changed nothing.**
    * Whether or not you had to compile NDISWrapper
**Compiled 1.52**
    * Which version of Step 2 you used
**Step 2b**

I had to compile the firmware from the linuxwireless site. Trying the 4311 WinXP drivers with ndiswrapper itself didn't work. Compiled the b42-fwcutter-011, as well as the broadcom-wl-4.80.53.0 offered [here]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old") and am using the stock b43 driver to get anything. A spotty connection, however, I get about 20kb/s max, and the signal drops out sometimes for no apparent reason. The download limit is probably due to the firmware. Does anyone know how to bypass this since I can't get ndiswrapper+driver to work by itself? Is this a problem for Hardy since other 64 bit users can get up to 54 Mb/s while iwconfig reports that mine is limited to 11 Mb/s?

I'm using the driver provided on the Dell site [here.]("ftp://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe") 90 Mb.

---

### Post by Jamie Jackson on 2008-03-12
> **feminaexlux said:**
> **Failure? :(**

I haven't had upgraded to Hardy yet, so I don't have any experience with that yet. What happened, though?

Could you:

[LIST=1]
[*]See available networks?
[*]Connect to unencrypted access points?
[*]Connect to encrypted access points?
[*]Browse the Internet?
[/LIST]

Since there are so many ways something can fail, I'm interested to know how *exactly* it failed, or how you perceived it failing.

Also, did you try step 2a? As time goes on, more and more people are having luck with 2a for 4311 rev 01, and fewer and fewer people are having luck with 2b, for whatever reason.

---

### Post by feminaexlux on 2008-03-12
> **Jamie Jackson said:**
> Could you:

[LIST=1]
[*]See available networks?
[*]Connect to unencrypted access points?
[*]Connect to encrypted access points?
[*]Browse the Internet?
[/LIST]

Also, did you try step 2a? As time goes on, more and more people are having luck with 2a for 4311 rev 01, and fewer and fewer people are having luck with 2b, for whatever reason.

The Hardy development came with an updated driver for bcm43xx, it's just b43. I'm using that driver to get wireless, but I want to be uncrippled, so I blacklisted b43 and opted for ndiswrapper with the winxp drivers. However, the hardware itself wasn't recognized by the network manager, nor iwconfig, even though ndiswrapper -l reported:

```
bcmwl5 : driver installed
device (14E4:4311) present (alternate driver: ssb)
```

(iwconfig output):

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

With no wireless devices detected, I couldn't do any of the above. I guess it's a Hardy thing? I've tried 2a to no avail, as well as about 4 other drivers, and generic bcm43xx 64 bit drivers from linuxent...

---

### Post by Jamie Jackson on 2008-03-12
feminaexlux,

Sounds like you know what you're doing, but let me throw something at you, since you're the first Hardy Guinea Pig here (I think?).

Did you see ndiswrapper load up in dmesg? For details, look at kevdog's nice, detailed troubleshooting tips [here]("http://ubuntuforums.org/showthread.php?t=574501"). Specifically, use your browser's search to find the first instance of "ndiswrapper -l" and read from there, if you need tips on what to look for in dmesg.

I'd also be interested in seeing the output of "lshw -C network", to see if that interface indeed gets associated with ndiswrapper.

If I need to make any changes to the HowTo based on Hardy, I'd like to knock that out before the masses (and I) upgrade.

Thanks a lot for the feedback!

Jamie

---

### Post by feminaexlux on 2008-03-12
```
[ 5334.952816] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 5335.007991] usbcore: registered new interface driver ndiswrapper
```

```
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a2:bf:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:ba:69:df
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11g
```

Is there anything else you'd like me to try? (Though, if anything the b43 DOES work, just not very well for me.)

The ssb module seems to be the culprit according to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558"). Looking at workarounds.

Okay! I'm using ndiswrapper for my wireless! Though I had to remove and reload my b44, ssb, and ndiswrapper modules first in this order:

```
divinya@elithewerewolf:~$ sudo rmmod b44
divinya@elithewerewolf:~$ sudo rmmod ssb
divinya@elithewerewolf:~$ sudo rmmod ndiswrapper
divinya@elithewerewolf:~$ sudo modprobe ndiswrapper
divinya@elithewerewolf:~$ sudo modprobe ssb
divinya@elithewerewolf:~$ sudo modprobe b44
```

I hope there's some fix in the ordering for the Hardy release so I don't have to do this manually all the time. :/

So, I guess this is a **partial success**?

Here's the updated lshw -C network output, that finally shows ndiswrapper being used for wireless:

```
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1d:60:ba:69:df
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=192.168.1.100 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:a2:bf:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
```

Sorry for the suuuuper long post, guys, but I didn't want to be quadruple posting... -_-

---

### Post by Jamie Jackson on 2008-03-12
feminaexlux,

I'm looking at that [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558") now. Thanks for contributing to its comments. I really hope this gets worked out in Hardy!

---

### Post by feminaexlux on 2008-03-12
Hooray to the development team! I think they've all ready sorted out the ordering issue, since I booted into 2.6.24-12 (after partial upgrade and update to the 2.6.24-12-generic kernel), and ndiswrapper loaded up just fine :)

So, here's my updated statement:

Success!
**Dell Vostro 1000 AMD64 Athlon X2**
**05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)**
**05:00.0 0280: 14e4:4311 (rev 01)**
**Ubuntu hardy (development branch)**
**2.6.24-12-generic x86_64** at least on March 13th, 15:44 -7 GMT... don't remember when it updated...
**Nothing special. Fresh install, changed nothing.**
**Compiled 1.52**
**Step 2b**

---

### Post by jonnd on 2008-03-17
I have a Compaq Presario 2100.  Broadcom BCM4306.  Running 7.10.  Restricted Driver Manager in 7.10 did not work for me but these instructions worked perfectly using step 2b.  Did not have to compile ndiswrapper.  Thanks.

---

### Post by Jamie Jackson on 2008-03-17
> **jonnd said:**
> I have a Compaq Presario 2100.  Broadcom BCM4306.  Running 7.10.  Restricted Driver Manager in 7.10 did not work for me but these instructions worked perfectly using step 2b.  Did not have to compile ndiswrapper.  Thanks.

I could really use more information on the BCM4306! Could you please post all of the information that I ask for in the very first post of this thread?

Thanks, and congrats,

Jamie

---

### Post by Jamie Jackson on 2008-03-17
> **feminaexlux said:**
> Hooray to the development team! I think they've all ready sorted out the ordering issue, since I booted into 2.6.24-12 (after partial upgrade and update to the 2.6.24-12-generic kernel), and ndiswrapper loaded up just fine :)

So, here's my updated statement:

Success!
**Dell Vostro 1000 AMD64 Athlon X2**
**05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)**
**05:00.0 0280: 14e4:4311 (rev 01)**
**Ubuntu hardy (development branch)**
**2.6.24-12-generic x86_64** at least on March 13th, 15:44 -7 GMT... don't remember when it updated...
**Nothing special. Fresh install, changed nothing.**
**Compiled 1.52**
**Step 2b**

Brilliant, thanks for keeping us posted!  Let us know if anything changes as Hardy development continues.

---

### Post by fitzman49 on 2008-03-17
> **Jamie Jackson said:**
> I could really use more information on the BCM4306! Could you please post all of the information that I ask for in the very first post of this thread?

Thanks, and congrats,

Jamie

I have a Dell Inspiron 5150 with the BCM4306 wireless card.  I tried to use ndiswrapper but it looked like the module had trouble loading because my network did not show up in the network-manager.  Since I am at work right now I don't have access to that machine, but I'll post my dmesg and other things when I get back home  so maybe we can get through this since I know this was a popular card back in the day.

Fitz

Edit: I am running Hardy alpha 6 on that machine.

---

### Post by Jamie Jackson on 2008-03-17
> **fitzman49 said:**
> I have a Dell Inspiron 5150 with the BCM4306 wireless card.  I tried to use ndiswrapper but it looked like the module had trouble loading because my network did not show up in the network-manager.  Since I am at work right now I don't have access to that machine, but I'll post my dmesg and other things when I get back home  so maybe we can get through this since I know this was a popular card back in the day.

Fitz

Edit: I am running Hardy alpha 6 on that machine.

If you're running Hardy, you may want to be sure you're *as* up to date as [feminaexlux.]("http://ubuntuforums.org/showpost.php?p=4504933&postcount=383") Anyway, let me know how it goes.

---

### Post by angusmac on 2008-03-19
Great howto! Worked first time!

My spec as follows:

>     
    * Machine Brand and Model
    * Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
    * Wireless Chipset: lspci -n | grep '14e4:43'
    * Ubuntu Version: lsb_release -d
    * Kernel / Architecture: uname -mr
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
    * Whether or not you had to compile NDISWrapper
    * Which version of Step 2 you used


Compaq Presario V2000 notebook
06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 0280: 14e4:4318 (rev 02)
Xubuntu 7.10
2.6.22-14-generic i686
No compile required
Step 2c

Thanks very much.

---

### Post by TimelessRogue on 2008-03-19
[LIST]
[*] Machine Brand and Model:  HP dv9623ed
[*]Wireless Brand and Model:  03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
[*] Wireless Chipset: [FONT=monospace]03:00.0 0280: 14e4:4312 (rev 02)[/FONT]
[*] Ubuntu Version: [FONT=monospace] Hardy (development branch)[/FONT]
[*] Kernel/architecture (including 32 vs. 64 bit) : 2.6.24-12-generic x86_64
[*] Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.):  None
[*] Whether or not you had to compile NDISWrapper:  No. Part of Hardy installation
[*] Which version of Step 2 you use:  2a[/LIST]This worked great!  Been futzing with this Broadcom wireless set-up since I installed Hardy (for testing purposes but also as primary OS) on my new HP dv9623 with Broadom 4312 last week.  Your "How To" guide turned out to be the final solution.  Kudos to you!  And I'll pass the tip on ...

---

### Post by fitzman49 on 2008-03-19
So after fighting with hardy for a few days on my machine, it appears that the BCM4306 does not work with ndiswrapper.  In fact it looks like the module isn't even loading which is strange.  dmesg and lspci have no record of the card being present.  I can get the card to be recognized with b43 but will not connect to any networks.  Anyone else have this same sort of problem with this card and hardy?

---

### Post by hermitical on 2008-03-20
I seem to have got this partially working, but I need to have an ethernet connection to be able to turn the wireless on (with the button), then I can unplug the wired connection...
any ideas or pointers??

---

### Post by Jamie Jackson on 2008-03-21
> **hermitical said:**
> I seem to have got this partially working, but I need to have an ethernet connection to be able to turn the wireless on (with the button), then I can unplug the wired connection...
any ideas or pointers??

I'm not following, could you go into more detail about the workaround you're using? (Also explain the "button.")

---

### Post by Jamie Jackson on 2008-03-21
> **fitzman49 said:**
> So after fighting with hardy for a few days on my machine, it appears that the BCM4306 does not work with ndiswrapper.  In fact it looks like the module isn't even loading which is strange.  dmesg and lspci have no record of the card being present.  I can get the card to be recognized with b43 but will not connect to any networks.  Anyone else have this same sort of problem with this card and hardy?

Do you have the very latest alpha? [Another user reported a bug]("http://ubuntuforums.org/showpost.php?p=4504933&postcount=383") with Hardy's module loading in a previous post.

If you've got the latest Hardy, please reply with the responses to the following:
```

ndiswrapper -v
ndiswrapper -l
lsmod | grep '^ndiswrapper'
grep 'ndiswrapper' /etc/modules

```

---

### Post by kevdog on 2008-03-21
The mysterious Jamie Jackson makes a rogue appearance :)

---

### Post by kevdog on 2008-03-22
Jamie Jackson

I noticed this chipset was not only your list

KewlFuzz has found the following to work with the WPC54G
lspcr-nn
returns:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

lspci -n | grep '14e4:43'
returns:
02:00.0 0280: 14e4:4320 (rev 02)

it worked after i got the driver from here:
[http://www.linksys.com/servlet/Satel...#versiondetail](http://www.linksys.com/servlet/Satel...#versiondetail)

---

### Post by Aellus on 2008-03-22
I'm using the current hardy beta, and I too am having problems with the wireless. I've got a BCM4318 in my machine: 

```
$ lspci | grep 'BCM'
03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

$ lspci -n | grep '14e4:43'
03:07.0 0280: 14e4:4318 (rev 02)
```

The native support didnt work, and in fact when I used the "Hardware Drivers" tool to 'enable' the drivers, my system completely locked up and i had to do a hard reboot. The odd thing is that the "Hardware Drivers" tool notes that the drivers are *not* enabled, but the status is "In use". Wireless networks do not appear in the network manage list. The wifi status indicator light on my laptop is not lit up, and pushing the wifi "on/off" button on the keyboard doesnt affect that. (This may be the "button" that the previous poster was referring to).

I followed the instructions in the wiki in the OP of this thread, the normal ndiswrapper package did nothing, so i compiled from source and still no results. I am going to try finding some other drivers, but i figured i would post my issue and see if anyone else had similar issue with the 4318.

For the record, it worked in Gutsy right from a clean install, which is an amazing feeling in linux :)

---

### Post by Jamie Jackson on 2008-03-22
> **kevdog said:**
> Jamie Jackson

I noticed this chipset was not only your list

KewlFuzz has found the following to work with the WPC54G
lspcr-nn
returns:
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

lspci -n | grep '14e4:43'
returns:
02:00.0 0280: 14e4:4320 (rev 02)

it worked after i got the driver from here:
[http://www.linksys.com/servlet/Satel...#versiondetail](http://www.linksys.com/servlet/Satel...#versiondetail)

Hey kevdog,

Would you post that link again, please? It got mangled.

Thanks,
Jamie

---

### Post by kevdog on 2008-03-22
```
http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download#versiondetail
```

Hopefully that will help

---

### Post by Jamie Jackson on 2008-03-22
> **kevdog said:**
> The mysterious Jamie Jackson makes a rogue appearance :)

Well, things were on autopilot until this pesky Hardy came out. Have you had reports of ndiswrapper problems on Hardy? I haven't upgraded yet, so I don't have any firsthand experience.

Also, are you still truly on Feisty, as your profile suggests?

Thanks,
Jamie

P.S. My five-year-old is sitting next to me, and he insists that I add the following smiley:  :KS

---

### Post by Jamie Jackson on 2008-03-22
> **kevdog said:**
> ```
http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859842300&packedargs=sku%3D1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4230081921B03&displaypage=download#versiondetail
```

Hopefully that will help

Dang, that's not a direct download link. This page wants me to select a version of WPC54G, and then it provides links to the downloads. Can you tell me how to navigate from the link above?

---

### Post by kevdog on 2008-03-22
Hmm -- it was the revision2 driver but the direct link I can't find either.  There has to be an answer!!

---

### Post by Jamie Jackson on 2008-03-22
> **kevdog said:**
> Hmm -- it was the revision2 driver but the direct link I can't find either.  There has to be an answer!!

Okay, I've downloaded it, pruned out unnecessary files, and hosted it. Now it's a snappy, wget-able download. It's now [step 2f]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-2b435303abdabe070c57502f8afbb765bc56ad57").

The *.inf file is a little different than I'm used to, so hopefully this will work for non-Linksys BCM4306 rev 02s as well, but I guess we'll see, eventually.

Thanks for the info, kevdog.

---

### Post by him610 on 2008-03-30
Feedback to Re: BCM43xx HowTo

Sony PCG-FXA36 AMD Athlon 1GHz 512MB RAM
$ lspci | grep Broadcom 02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
$ lspci -n | grep '14e4:43' 02:00.0 0280: 14e4:4320 (rev 02)
$ lsb_release -d Description:    Ubuntu 7.10
$ uname -mr 2.6.22-14-generic i686

No extra boot options
No need to compile NDISWrapper
Used Step 2f
Step 3. Substituted lsbcmnds.inf for bcmwl5.inf

```
hughm@pilgrim:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.
hughm@pilgrim:~/bcm43xx$ sudo ndiswrapper -i lsbcmnds.inf
installing lsbcmnds ...
hughm@pilgrim:~/bcm43xx$ ndiswrapper -l
bcmwl5 : invalid driver!
lsbcmnds : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```

This is the second time I have used this procedure successfully on some variation of the BCM4306.
It works great!
Thanks

---

### Post by Jamie Jackson on 2008-04-01
> **hgh9mrp said:**
> Used Step 2f
Step 3. Substituted lsbcmnds.inf for bcmwl5.inf

Thanks for the detailed feedback. Because of this info, I just re-re-packaged the zip so that you don't have to stray at all from the instructions for step 2f.

---

### Post by Jamie Jackson on 2008-04-01
> **Jamie Jackson said:**
> Okay, I've downloaded it, pruned out unnecessary files, and hosted it. Now it's a snappy, wget-able download. It's now [step 2f]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-2b435303abdabe070c57502f8afbb765bc56ad57").

The *.inf file is a little different than I'm used to, so hopefully this will work for non-Linksys BCM4306 rev 02s as well, but I guess we'll see, eventually.

Thanks for the info, kevdog.

Yup, I now know it works, thanks to hgh9mrp's post.

---

### Post by schezel2000 on 2008-04-05
I am running fedora core 7 and i got my wireless working on a 
compaq V6305nr  with dell broadcom 1390 (broadcom)4311 revision 1
things ubuntu guys for helping out. The steps that i did were based upon what was done on this tutorial
if it works for Fedora, it will more then likely work for ubuntu.
(switching yum for apt-get i think)
i also blacklisted the bm43xx by editing the 
/etc/modprobe.d/blacklist
I got my firmware from the ndiswrapper site

---

### Post by bwmichaud on 2008-04-08
Machine Brand and Model
Dell Inspiron B120 laptop

      Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

      Wireless Chipset: lspci -n | grep '14e4:43'
02:03.0 0280: 14e4:4318 (rev 02)


      Ubuntu Version: lsb_release -d
Description:    Ubuntu 7.10

      Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.22-14-generic i686


      Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
None

      Whether or not you had to compile NDISWrapper
I did not have to compile NDISWrapper

      Which version of Step 2 you used
I used version 2C of Step 2

I tried many other fixes but this is the only one that worked. At first, I tried this fix without a fresh install and it did not work. (Just as you stated) After a fresh install, it worked flawlessly. Thanks for all the hard work you have put into this project. I greatly appreciate it and I can guarantee that others do as well.

Thanks,
Brian

---

### Post by vikram on 2008-04-09
worked flawlessly - thanks !

Dell Latitude 630

#spci -n | grep '14e4:43'
0c:00.0 0280: 14e4:4311 (rev 01)

#uname -r
2.6.22-14-generic

# ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.45
vermagic:       2.6.22-14-generic SMP mod_unload 586

---

### Post by woodsmanvr on 2008-04-12
Dell Inspiron 8500
BCM4309 Dell Truemobile 1400

I am new to ubuntu.  I fought with the default bcm43xx for a couple of days. after several fresh installs and partial access. I knew I would have to learn more about the NDISwrapper. 

From a  fresh install of 7.10. (my 7th in as many days)  fully patched with updates. 
I used instructions 2a on the [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) how to.  I had to download the correct driver from dell.  I had to install the drivers on a windows system because cabextract could not open the files. Copied the drivers onto the ubuntu system with a usb drive. Fought bad drivers (wrong inf files) from other links for a couple of hours. Finally found the correct file on dell's website from the service tag of the laptop. Once I had the right driver worked like a champ.  Connecting at normal speeds.  No more slowness and and no more drop offs.  I almost gave up.  Thanks for the article, I could not have succeeded without it. 

another useful article that helped confirm some of the steps. Used as a reference point.  

[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)  

Thanks for all the posts out there.  :)

---

### Post by David Robertson on 2008-04-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Compaq Presario V6000
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
03:00.0 0280: 14e4:4311 (rev 02)
Description:	Ubuntu hardy (development branch)
2.6.24-16-generic x86_64
No extra boot options
YES had to compile ndiswrapper
Used 2a

Notes:
There were a couple of problems, but basically the instructions are very good on this post.
1. I had to compile to get the ndiswrapper modules to turn up with modprobe.
2. There is currently a bug with Hardy (as at April 14 - reported in this report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558)
Basically ssb grabs the adaptor and ndiswrapper can get to it
To fix this I added these lines to rc.local:
[B]# Reorder ssb and ndiswrapper to get wireless running
modprobe -r ndiswrapper
modprobe -r ssb
modprobe ndiswrapper
modprobe ssb
[/B]
The last line is not needed, just seems symetrical.
I wasn't sure where else to put this fix
3. Worked best on a fresh install or 8.04 (install from beta, then take all upgrades)
4. Hopefully these problems will just go away with the final release of 8.04

Anyway, excellent howto, it very clear.

---

### Post by Jamie Jackson on 2008-04-14
> **woodsmanvr said:**
> Dell Inspiron 8500
BCM4309 Dell Truemobile 1400

I am new to ubuntu.  I fought with the default bcm43xx for a couple of days. after several fresh installs and partial access. I knew I would have to learn more about the NDISwrapper. 

From a  fresh install of 7.10. (my 7th in as many days)  fully patched with updates. 
I used instructions 2a on the [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) how to.  I had to download the correct driver from dell.  I had to install the drivers on a windows system because cabextract could not open the files. Copied the drivers onto the ubuntu system with a usb drive. Fought bad drivers (wrong inf files) from other links for a couple of hours. Finally found the correct file on dell's website from the service tag of the laptop. Once I had the right driver worked like a champ.  Connecting at normal speeds.  No more slowness and and no more drop offs.  I almost gave up.  Thanks for the article, I could not have succeeded without it. 

another useful article that helped confirm some of the steps. Used as a reference point.  

[http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)  

Thanks for all the posts out there.  :)

Hi woodsmanvr,

Favor, please? Take a look at the very first post of this thread, and provide all of the details I ask for. Also, please post a link to the Dell download that you used.

With this information, I can update the wiki, and  the next 4309 user will be up in running in 5 minutes instead of a week!

Thanks, and congrats,
Jamie

---

### Post by Jamie Jackson on 2008-04-14
> **David Robertson said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Compaq Presario V6000
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
03:00.0 0280: 14e4:4311 (rev 02)
Description:	Ubuntu hardy (development branch)
2.6.24-16-generic x86_64
No extra boot options
YES had to compile ndiswrapper
Used 2a

Notes:
There were a couple of problems, but basically the instructions are very good on this post.
1. I had to compile to get the ndiswrapper modules to turn up with modprobe.
2. There is currently a bug with Hardy (as at April 14 - reported in this report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197558)
Basically ssb grabs the adaptor and ndiswrapper can get to it
To fix this I added these lines to rc.local:
[B]# Reorder ssb and ndiswrapper to get wireless running
modprobe -r ndiswrapper
modprobe -r ssb
modprobe ndiswrapper
modprobe ssb
[/B]
The last line is not needed, just seems symetrical.
I wasn't sure where else to put this fix
3. Worked best on a fresh install or 8.04 (install from beta, then take all upgrades)
4. Hopefully these problems will just go away with the final release of 8.04

Anyway, excellent howto, it very clear.

Congrats!

That module loading bug, I mentioned it in the wiki (fourth paragraph under Introduction heading.)

I'm wondering if you missed that note, or whether you saw it and it helped you.

If you missed it, I might consider trying to make it more prominent, somehow.

Thanks,
Jamie

Update: This is reported to be fixed (as of 4/8 ). If you find that the "fix" had reportedly made it into the Hardy version that you ran, would you reopen that bug, please?

---

### Post by oldvultureface on 2008-04-17
Flawless.

user@ubuntu:~$ lspci | grep Broadcom
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
user@ubuntu:~$ lspci -n | grep '14e4:43'
00:09.0 0280: 14e4:4320 (rev 02)
user@ubuntu:~$ lsb_release -d
Description:    Ubuntu 7.04 (32 bit)

Compaq Presario 2570US, standard install, no special boot options.
Did not have to compile NDISWrapper.
Step 2f.

---

### Post by Jamie Jackson on 2008-04-17
> **oldvultureface said:**
> Flawless.

user@ubuntu:~$ lspci | grep Broadcom
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
user@ubuntu:~$ lspci -n | grep '14e4:43'
00:09.0 0280: 14e4:4320 (rev 02)
user@ubuntu:~$ lsb_release -d
Description:    Ubuntu 7.04 (32 bit)

Compaq Presario 2570US, standard install, no special boot options.
Did not have to compile NDISWrapper.
Step 2f.

Thanks, with this, step 2f is no longer "beta." :)

---

### Post by oldvultureface on 2008-04-18
Thanks again. My association with the command line ended with CP/M on a Commodore 128. However, reading and copying/pasting are well within my capabilities. This is the first time since Linspire 5.0 (my first taste of Linux, $50 at BestBuy a long time ago) that the supplied internal card has worked outside of Windows, then only with WEP and frequent dropouts. After several hours and reboots, this connection is rock solid with WPA. I worship at your feet.

---

### Post by kutjara on 2008-04-20
I've managed to get the Broadcom 4321AG working under Hardy 64 bit on my HP tx1420us, but only with unsecured or WEP-secured access points. I used the version of Ndiswrapper in the Ubuntu repositories and the Windows XP drivers for my machine from HP's support site, and made things a bit easier for myself by using the ndisgtk GUI to install and uninstall the various drivers I tested.

I tried out the bcmwl5.inf and bcmwl6.inf drivers. Both worked sufficiently to scan for and find local networks, but only the bcmwl5 driver was able to connect to them. I also tried what appeared to be the 64 bit version of the bcmwl5 (the bcmwl564), but Ndiswrapper wouldn't even install it. In the end, I settled for bcmwl5 (and kissed goodbye to the draft-n capabilities of my card).

The next step looks like a battle with wpa-supplicant to figure out why it doesn't want to work with ndiswrapper on my setup. I've messed around with a lot of settings, though, so I think I'm going to do a fresh install and see if the methods outlined in this thread give better results. I'll report back on my progress.

---

### Post by Jamie Jackson on 2008-04-20
> **kutjara said:**
> I've managed to get the Broadcom 4321AG working under Hardy 64 bit on my HP tx1420us, but only with unsecured or WEP-secured access points. I used the version of Ndiswrapper in the Ubuntu repositories and the Windows XP drivers for my machine from HP's support site, and made things a bit easier for myself by using the ndisgtk GUI to install and uninstall the various drivers I tested.

I tried out the bcmwl5.inf and bcmwl6.inf drivers. Both worked sufficiently to scan for and find local networks, but only the bcmwl5 driver was able to connect to them. I also tried what appeared to be the 64 bit version of the bcmwl5 (the bcmwl564), but Ndiswrapper wouldn't even install it. In the end, I settled for bcmwl5 (and kissed goodbye to the draft-n capabilities of my card).

The next step looks like a battle with wpa-supplicant to figure out why it doesn't want to work with ndiswrapper on my setup. I've messed around with a lot of settings, though, so I think I'm going to do a fresh install and see if the methods outlined in this thread give better results. I'll report back on my progress.

The bcmwl6 is a Vista driver, which won't work with ndiswrapper, so your experience is in line with expectations.

The WPA config (from a fresh install) should be a quick one-liner from the command line. Some other how-tos make it much more complicated.

Once you do get your card working with ndiswrapper, please post all of the information that I ask for in my original post in this thread, and also provide a direct link to the driver download that you use. With this information, I'll be able to add your device to the wiki.

Good luck,
Jamie

---

### Post by kevdog on 2008-04-20
What are you using to attempt to make a WPA connection (meaning network manager, wicd, or the command line)?  It looks like you probably don't have some parameters entered correctly!

---

### Post by kutjara on 2008-04-21
OK, I finally got around to my fresh install this evening, and then followed your process in the Wifi HOWTO. Here are my results. First, the 411 on my setup:

- Machine Brand and Model - HP Pavilion tx1420us (64bit AMD Turion 2.2GHz, 4GB RAM)
- Wireless Brand and Model - Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
- Wireless Chipset: 14e4:4328 (rev 03)
- Ubuntu Version: Ubuntu 8.04 (64 bit)
- Kernel Architecture: 2.6.24-16-generic x86_64
- Boot options: default
- NDISWrapper compile? - yes
- Version of Step 2 used - 2d

The ndiswrapper/driver installation process was clear and painless (thanks very much!), and got the card up and running with bcmwl5.inf. It didn't immediately load up on reboot, though, so I had to modprobe for it again, whereupon it was back (this was easily fixed by manually entering 'ndiswrapper' in /etc/modules). So far so good.

Unfortunately, the WPA problem I had last night is still present. I can connect perfectly to wireless routers using no security or WEP, but not to ones running WPA. I've experimented a bit on both my current Linksys WRT600N and my old Airport Extreme Base Station (as well as on my neighbor's unsecured 802.11b box) and the story is the same on all of them: unsecured is fine, WEP (40/64/128 ASCII or HEX) is fine, WPA (1 or 2) is no go. Wpa-supplicant is installed by default in Hardy, so I'm a bit baffled by its refusal to step up and do the job. I've got Hardy installed on an Acer laptop with Atheros wireless card, and WPA 'just worked' without any intervention on my part (other than choosing "madwifi" in WICDs preferences panel).

I've tried to connect using 'network manager,' which correctly recognized my home network as using WPA (Personal). I entered the passphrase, clicked connect, and watched while nm spun its wheels (neither of the connection lights in the gnome-panel applet illuminated) before popping up the connect window again and asking for my passphrase. No matter how many times I entered it, nm would just repeat the cycle.

I then decided to try WICD (which works extremely well on my Acer). I enabled encryption in the main panel, selected 'WPA1/2', entered my passphrase, and chose wext from the preferences dropdown (the preferred WPA method for ndiswrapper, apparently). Again, WICD just spun its wheels before crapping out, only this time by crashing and requiring a reboot to get working again (just to add a little variety).

Next, I created and edited wpa_supplicant.conf and used various command line tools (such as "sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf) to make wpa_supplicant use the ESSID and passkey information I'd configured. The process proceeded successfully, according to the threads I found the procedures on, and didn't throw up any unpleasant messages. A few times, even, for brief intervals, WICD gave indications that it had established connectivity after some of these exercises, but the green bars vanished within seconds and I was back to square one. In every case, after all the configuring and ifconfig upping and downing, the wpa_supplicanting, the mode Managing and dhclienting, the wifi card finds the router, associates with it, handshakes with it, goes out for dinner and a movie with it, dances round the Maypole with it, and then times-out during authentication.

I'm really at a loss about this. I can't make do with no wireless security, but this damned card defies every effort I can think of to enable WPA (even though it supports it, according to one of the messages it spewed out in response to the countless commands I issued to get it to tell me what the hell it thinks it's doing). My googling has led me to posts from people using all sorts of distributions, with the same problem, and none of the suggested resolutions appear to work for more than a tiny minority. I'm beginning to think the 4328 card just can't do WPA under Linux.

If you guys have got any ideas, I'd be grateful for them. I'm pretty much up against a brick wall here and totally out of ideas.

---

### Post by kevdog on 2008-04-21
Rather than using WICD -- why don't you strictly use the command line and attempt a connection as per here:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by kutjara on 2008-04-21
> **kevdog said:**
> Rather than using WICD -- why don't you strictly use the command line and attempt a connection as per here:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

That was one of the HOWTOs I used. It got me close on a couple of occasions (all the bars in the WICD gnome-tray applet lit up for a few seconds about halfway through, before going immediately dark again), but still couldn't make the card stop timing out under authentication.

After setting up the wpa_supplicant.conf file, I typed the following, as per the HOWTO

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig <interface> up
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

The first two instructions were unproblematic, while the third one produced a number of lines of "associating with <my router's MAC address>". When that process finished, I typed 'sudo ifconfig wlan0 up'. This was when the WICD applet started showing full bars for a few seconds, before dropping out, then showing the bars, then dropping out, over and over. It was like the card was connecting, running through the authentication cycle, failing, dropping, then retrying, over and over.

Just to see what would happen, I closed the terminal window, opened another and typed in the final two commands ('mode Managed' and 'dhclient') The dhclient command stopped at the same "authentication timeout" stage in the lease-creation process.

My wireless card has no trouble finding and connecting to routers, it just doesn't seem to speak the same dialect of WPA as the rest of the world. I don't know if this is some flaw in wext, in the way Linksys and Apple routers work (I've seen threads hypothesizing about that topic at length), or just an inauspicious conjunction of the planets. What's frustrating is that both gnome network manager and WICD need no configuration to know it's a WPA connection (WICD, for example, displays the MAC address and encryption type of every router in range, and next to the entry for mine is a prominent 'WPA"), yet can't use the WPA credentials I supply to create a connection.

I'll try your HOWTO again after uninstalling WICD completely, to see if a "pure" command line method works better, but I suspect I'll hit the same wall at the "authentication" stage.

---

### Post by kevdog on 2008-04-21
If you can post the following it would be great

Your wpa_supplicant.conf file 
lshw -C network

Thanks.

---

### Post by kutjara on 2008-04-21
> **kevdog said:**
> If you can post the following it would be great

Your wpa_supplicant.conf file 
lshw -C network

Thanks.

wpa_supplicant.conf:

```

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
   ssid="mySSID"
   scan_ssid=0
   proto=WPA
   key_mgmt=WPA-PSK
   psk="myASCIIPassphrase"
   pairwise=TKIP
   group=TKIP
}

```

lshw -C network:

```

  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:e7:50:2b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

---

### Post by kutjara on 2008-04-23
Well, after a long and tortuous road, I must regretfully declare the BCM4328 not ready for primetime under 64 bit Hardy. I must qualify this a bit, because the card actually works when installed using the method outlined in the original post (specifically, Step 2d). What doesn't work is WPA. Unsecured and WEP connections are fine. WPA doesn't even partially work.

Complicating the issue is the fact that this problem may be an artifact of my specific setup. I'm using a Linksys WRT600N router. When I switch on its WPA encryption, the Broadcom card in my laptop thinks encryption has been switched off. What's puzzling is that the same card can see all my neighbors' networks, and can recognize when they have WPA switched on.

I'm not sure what this means, other than some link in the card/firmware/NDISWrapper/WPA/router chain is not playing well with others.

I've shelved this problem for the time being and shoved in a Belkin F5D7050 USB card, which took about ten seconds to set up with Serialmonkey's rt73 driver. And, yes, WPA works perfectly.

---

### Post by Jamie Jackson on 2008-04-23
> **kutjara said:**
> Well, after a long and tortuous road, I must regretfully declare the BCM4328 not ready for primetime under 64 bit Hardy. I must qualify this a bit, because the card actually works when installed using the method outlined in the original post (specifically, Step 2d). What doesn't work is WPA. Unsecured and WEP connections are fine. WPA doesn't even partially work.

Complicating the issue is the fact that this problem may be an artifact of my specific setup. I'm using a Linksys WRT600N router. When I switch on its WPA encryption, the Broadcom card in my laptop thinks encryption has been switched off. What's puzzling is that the same card can see all my neighbors' networks, and can recognize when they have WPA switched on.

I'm not sure what this means, other than some link in the card/firmware/NDISWrapper/WPA/router chain is not playing well with others.

I've shelved this problem for the time being and shoved in a Belkin F5D7050 USB card, which took about ten seconds to set up with Serialmonkey's rt73 driver. And, yes, WPA works perfectly.

Bah, I hate when that happens. I stuck a $10 Belkin (rebranded to "Ativa," I think) dongle on another laptop that I had been struggling with for weeks, and the darn thing worked with WPA with zero configuration.

BTW, I have read before about problems with SSIDs (and maybe passwords) that contain spaces (and other funny characters, I think in the case of SSIDs). I don't know much about this issue, and the fact that your Belkin worked with the same configuration would seem to invalidate my vague suspicions, but did your SSID/password meet those criteria?

---

### Post by kutjara on 2008-04-23
> **Jamie Jackson said:**
> Bah, I hate when that happens. I stuck a $10 Belkin (rebranded to "Ativa," I think) dongle on another laptop that I had been struggling with for weeks, and the darn thing worked with WPA with zero configuration.

BTW, I have read before about problems with SSIDs (and maybe passwords) that contain spaces (and other funny characters, I think in the case of SSIDs). I don't know much about this issue, and the fact that your Belkin worked with the same configuration would seem to invalidate my vague suspicions, but did your SSID/password meet those criteria?

No, my SSID and password are all contiguous and don't even use any special characters (because I've had those cause problems in the past too). Also,  my Acer Aspire 4315 laptop with Atheros AG5007 wireless card connects to this router. The Acer has been running Hardy 32 bit since Alpha 2 and connects perfectly with full WPA1/2, using the same credentials. I use the madwifi driver on the 4315 and manage the connection with WICD, using the "madwifi" option for WPA in the Preferences menu. No further WPA configuration was necessary.

That's why I think the problem with my tx1420us may strictly be limited to my precise setup (hardware and software). It would be easy to blame NDISWrapper, but I honestly can't say that's the problem. Since I can see the encryption protocols used by my neighbors' networks when I run a iwlist scan, the card is clearly able to see WPA when it's running on those routers. The only network out of the eight near me that it misreads the encryption status on is my own. It reads as "on" when WEP is on, but "off" when WPA is active. No amount of wpa_supplicant configuration can fix this, because the hardware itself is reporting encryption as "off." From the computer's perspective, therefore, there's nothing for it to handshake with. So it doesn't even try.

No, the more I think about it, the more this looks like a specific "Kutjara's Broadcom BCM4328 NDISWrapper Linksys WRT600N" problem. Somewhere in all that hardware and software, I'll bet there's one tiny bit in the wrong place, and that's throwing everything off.

So I guess the entry in your testimonial panel should read that the BCM4328 does work with 64 bit Hardy using NDISWrapper and the instructions in Step 2d of your HowTo, but can only allows WEP security. Maybe.

---

### Post by Jamie Jackson on 2008-04-23
> **kutjara said:**
> So I guess the entry in your testimonial panel should read that the BCM4328 does work with 64 bit Hardy using NDISWrapper and the instructions in Step 2d of your HowTo, but can only allows WEP security. Maybe.

Thanks for the info. Actually, earlier today, I did mention this sort of caveat in the wiki where it addresses specific chipsets: "In Gutsy, lspci shows "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)" NOTE: There has only been one person who has tried this card with this howto. He tried it with Hardy, and it worked for the most part; HOWEVER, even after a lot of work troubleshooting, he was unable to get WPA working. Check out this post [link to your post] and his subsequent ones."

I'll add the 64 bit variable in there as well.

---

### Post by Jamie Jackson on 2008-04-23
Well, I know I won't be upgrading to Hardy for a while. I'm going to a conference next week where I need my wireless to be tip-top.

There seems to be [too much in flux]("http://www.google.com/search?hl=en&q=ndiswrapper+hardy+bug+site%3Abugs.launchpad.net&btnG=Search") with ndiswrapper and Hardy.

---

### Post by kutjara on 2008-04-24
> **Jamie Jackson said:**
> Well, I know I won't be upgrading to Hardy for a while. I'm going to a conference next week where I need my wireless to be tip-top.

There seems to be [too much in flux]("http://www.google.com/search?hl=en&q=ndiswrapper+hardy+bug+site%3Abugs.launchpad.net&btnG=Search") with ndiswrapper and Hardy.

Wow, there certainly does! I had a hard time finding any info about NDISWrapper with 64 bit systems last week, but lots of people seem to be trying it out with Hardy this week. And the problems really do span the whole range. I almost feel fortunate it was "only" WPA I couldn't make work.

I agree that it may be prudent to give the NDISWrapper guys some time to tune the software for 64 bit (assuming, again, my problem wasn't just due to a cantankerous Broadcom card).

Thanks again for all the help. Without your HOWTO, I doubt I would have got as far as I did. It's an excellent guide, and much needed in the wooly world of Linux wireless (as is KevDog's excellent wpa-supplicant HOWTO).

---

### Post by Windows_Apple_Linux on 2008-04-24
Hardy FAIL:

On 7.10 my wireless Broadcom BCM94311MCG worked fine using the following tutorial: [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

After the Hardy installation I did try on uninstall and installing again and nothing, added bcm43xx to blacklist, tried your guide and still didn't work.

Any possible ideas? 
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/)
^Before hardy. 

Oh gosh, there it goes my 4 hours on making ubuntu "my ubuntu":lolflag:

---

### Post by Jamie Jackson on 2008-04-24
> **Windows_Apple_Linux said:**
> Hardy FAIL:

On 7.10 my wireless Broadcom BCM94311MCG worked fine using the following tutorial: [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)

After the Hardy installation I did try on uninstall and installing again and nothing, added bcm43xx to blacklist, tried your guide and still didn't work.

Any possible ideas? 
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/help-needed-with-broadcom-bcm94311mcg-617483/)
^Before hardy. 

Oh gosh, there it goes my 4 hours on making ubuntu "my ubuntu":lolflag:

Did you check out my note in the introduction about the Hardy (ssb) module loading bug? (I want to make sure you saw that.)

Oh, and the output from "lshw -C network" is always helpful--please send that.

---

### Post by Windows_Apple_Linux on 2008-04-24
> **Jamie Jackson said:**
> Did you check out my note in the introduction about the Hardy (ssb) module loading bug? (I want to make sure you saw that.)

Oh, and the output from "lshw -C network" is always helpful--please send that.

Yea I did..

Just wish that I had seem that before I installed Hardy. =[

Anyway way around?

alright, going to get you the lshw -C network =P

---

### Post by Windows_Apple_Linux on 2008-04-24
*-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:1d:c8:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

here it is

---

### Post by pmaconi on 2008-04-25
- Machine Brand and Model - HP Pavilion tx1000z (64bit AMD Turion 2.4GHz, 4GB RAM)
- Wireless Brand and Model - Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
- Wireless Chipset: 14e4:4328 (rev 03)
- Ubuntu Version: Ubuntu 8.04 (64 bit)
- Kernel Architecture: 2.6.24-16-generic x86_64
- Boot options: default
- Version of Step 2 used - 2d

My wireless card is working perfectly without modifying any steps of the HowTo - I do not have a problem with connecting to a WPA network.

---

### Post by jader2toesbumpy on 2008-04-25
> **pmaconi said:**
> - Machine Brand and Model - HP Pavilion tx1000z (64bit AMD Turion 2.4GHz, 4GB RAM)
- Wireless Brand and Model - Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
- Wireless Chipset: 14e4:4328 (rev 03)
- Ubuntu Version: Ubuntu 8.04 (64 bit)
- Kernel Architecture: 2.6.24-16-generic x86_64
- Boot options: default
- Version of Step 2 used - 2d

My wireless card is working perfectly without modifying any steps of the HowTo - I do not have a problem with connecting to a WPA network.

Really? I still have feisty because I couldn't get gusty to work with my chipset (which is the same chipset as you). Are you positive with all your info? Have you tried WPA2?

---

### Post by devosion on 2008-04-25
Im using BCM94311MCG rev 2 in my Acer laptop, and where I was able to install ndiswrapper and the bcmwl5 windows drivers before now my wifi isnt working. When I run lshw -C network im noticing that the last line for the configuration isn't set correctly. I am receiving the following:

> configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 latency=0 module=tg3 multicast=yes 

I have installed ndiswrapper from source and blacklisted ssb and tg3 just to be safe, and still am unable to pull up the wireless networks in my area. Any assistance would be appreciated.

Im using the 64bit version of 8.04.

---

### Post by pmaconi on 2008-04-25
> **jader2toesbumpy said:**
> Really? I still have feisty because I couldn't get gusty to work with my chipset (which is the same chipset as you). Are you positive with all your info? Have you tried WPA2?

Yeah, I am sure of all of my info. I couldn't get Gutsy working either - Hardy, however, ran pretty much without messing with it. The only changes I have made so far are for the wireless card (which works for the most part) and the touch screen (which works horizontal but not vertical).

As a correction to my original statement: WPA works fine for me, WPA2 does not. It times out before connecting.

---

### Post by jader2toesbumpy on 2008-04-25
> **pmaconi said:**
> Yeah, I am sure of all of my info. I couldn't get Gutsy working either - Hardy, however, ran pretty much without messing with it. The only changes I have made so far are for the wireless card (which works for the most part) and the touch screen (which works horizontal but not vertical).

As a correction to my original statement: WPA works fine for me, WPA2 does not. It times out before connecting.

all right dude im going to upgrade when I get home today then, hopefully every thing goes fine.

---

### Post by Tech Provider on 2008-04-25
1.Run in terminal for testing :

Rmmod = remove modules
Modprobe = adds modules

The ssb module seems to be the problem and is has to be terminated.

[LIST]
[*]rmmod b43
[*]rmmod b44
[*]rmmod ssb
[*]rmmod ndiswrapper
[*]modprobe ndiswrapper
[*]modprobe b44
[/LIST]

2.If it works use a bash script to run the commands and install wifi-radar to detect wireless networks and connect to them!

---

### Post by jader2toesbumpy on 2008-04-25
I can also confirm AMD 64, BCM4328, and Hardy working with WPA :)

---

### Post by Jamie Jackson on 2008-04-26
While I've been reluctant to upgrade my machine, I did download and run the Hardy Live CD, and have been doing some troubleshooting in that environment. As a result, I have a new "Hardy Bug Fix" section that explains how to fix the ssb module bug (for those who need it).

Consider this "Hardy Bug Fix" section as a "beta," until I get some users that confirm that the instructions are solid.

In the end, I hope I can remove this section completely when/if Ubuntu fixes this bug.

Please give me your feedback!

---

### Post by Jamie Jackson on 2008-04-26
Note: I now think step 2a is probably the best step 2 for anyone with a BCM4311 (Rev 01). I've made a note on the wiki.

---

### Post by Jamie Jackson on 2008-04-26
> **devosion said:**
> Im using BCM94311MCG rev 2 in my Acer laptop, and where I was able to install ndiswrapper and the bcmwl5 windows drivers before now my wifi isnt working. When I run lshw -C network im noticing that the last line for the configuration isn't set correctly. I am receiving the following:

 

I have installed ndiswrapper from source and blacklisted ssb and tg3 just to be safe, and still am unable to pull up the wireless networks in my area. Any assistance would be appreciated.

Im using the 64bit version of 8.04.

Haven't seen that one before. What's "lsh2 -C network" show after you blacklisted tg3? Also, did you try installing from the restricted drivers manager before trying ndiswrapper? (I'm wondering where tg3 came from?)

I guess you could try ```

sudo rmmod tg3
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

```

...and see if that helps... but then again, I don't know squat about tg3.

---

### Post by Jamie Jackson on 2008-04-26
> **Windows_Apple_Linux said:**
> *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:1a:73:1d:c8:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

here it is

The pervasive ssb bug. I've put a fix section for this in the wiki. (See the "Hardy Bug Fix" section.) Please try it out and provide feedback.

---

### Post by Jamie Jackson on 2008-04-26
> **Tech Provider said:**
> 1.Run in terminal for testing :

Rmmod = remove modules
Modprobe = adds modules

The ssb module seems to be the problem and is has to be terminated.

[LIST]
[*]rmmod b43
[*]rmmod b44
[*]rmmod ssb
[*]rmmod ndiswrapper
[*]modprobe ndiswrapper
[*]modprobe b44
[/LIST]

2.If it works use a bash script to run the commands and install wifi-radar to detect wireless networks and connect to them!

I've (just now) posted an (almost identical) variant of this on the wiki. However, the article sticks with native Ubuntu apps wherever possible, so the wiki opts for the native NetworkManager over the optional wifi-radar. Although either app is fine, I just wanted to point out that wifi-radar isn't part of the fix.

---

### Post by abrigham on 2008-04-26
Just thought I would add my comments here. I'm having the EXACT same issue as kutjara. My setup is as follows:

System: Dell Inspiron 1720
Wireless card: Dell Wireless 1505 (lspci shows as: BCM4328 802.11a/b/g/n (rev 03))
Router: Netgear WGR614 v7
Version: 64-bit Hardy Heron

I can connect to WEP and open networks, but cannot connect to WPA. Used the steps in the HOWTO to get the card working using NDISWrapper and the bcmwl5 drivers downloaded from Dell (R151517.EXE)

Just wanted kutjara to know he's not alone. :)

---

### Post by Jamie Jackson on 2008-04-26
> **abrigham said:**
> Just thought I would add my comments here. I'm having the EXACT same issue as kutjara. My setup is as follows:

System: Dell Inspiron 1720
Wireless card: Dell Wireless 1505 (lspci shows as: BCM4328 802.11a/b/g/n (rev 03))
Router: Netgear WGR614 v7
Version: 64-bit Hardy Heron

I can connect to WEP and open networks, but cannot connect to WPA. Used the steps in the HOWTO to get the card working using NDISWrapper and the bcmwl5 drivers downloaded from Dell (R151517.EXE)

Just wanted kutjara to know he's not alone. :)

You might want to try other drivers, either other step twos, or whatever XP driver is recommended by DELL. I wonder if the driver you guys are using is just "almost" the right one, and if another driver might be the ticket for WPA.

If you do find the magic combo, let me know what it is, and I'll put it up on the wiki.

---

### Post by bhdenterprises on 2008-04-26
Machine Brand/Model: Acer Aspire 4310
Wireless Brand/Model: 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
Wireless Chipset: lspci -n | grep '14e4:43'
Ubuntu Version: Ubuntu 8.04
Kernel/Architecture: 2.6.24-16-generic i686

I have to confirm that Step 2a worked for me in Hardy. When I was using Gutsy I used to perform Step 2b.

Just tried the ndiswrapper solution in Hardy tonight since my wireless chip is working out of the box. But it only gets 1Mb/s to 5Mb/s so I tried using ndiswrapper again.

What I did was remove the b43-fwcutter drivers first, then I executed the steps specified in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").
But instead of using NetworkManger or Wifiradar, I used Wicd instead. You can get Wicd by adding a third-party repository and installing it from there:

```

sudo echo "deb http://apt.wicd.net hardy extras" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wicd

```

If you're using Gutsy, just replace the word "hardy" above with "gutsy".

You can find Wicd from Application > Internet > Wicd

For more information on Wicd, please check [http://wicd.sourceforge.net]("http://wicd.sourceforge.net").

---

### Post by Jamie Jackson on 2008-04-26
> **bhdenterprises said:**
> Just tried the ndiswrapper solution in Hardy tonight since my wireless chip is working out of the box. But it only gets 1Mb/s to 5Mb/s so I tried using ndiswrapper again.

Did you mean, "I just tried the *fw-cutter* solution in Hardy tonight since my wireless chip is working out of the box. But it only gets 1Mb/s to 5Mb/s so I tried using ndiswrapper again?"

Never mind, I re-read and get what you're saying. However, let me get another thing straight: Did NetworkManager *not work*, or do you just *prefer* wicd?

---

### Post by Jamie Jackson on 2008-04-26
> **bhdenterprises said:**
> I have to confirm that Step 2a worked for me in Hardy. When I was using Gutsy I used to perform Step 2b.

Just to clarify: I think 2a would have also worked for you in *Gutsy*, it's just that I suspect 100% of users with this card can use 2a, but only 95% of users can use 2b for it.

That's why (last night) I updated the wiki to recommend 2a over 2b: I had just tried it myself, and it worked for me. I had always used 2b, too, but the feedback I was getting led me to believe that 2a was a more universal solution.

---

### Post by hessianmatrix on 2008-04-26
Hi,

Just upgraded to Hardy from Gutsy last night and had troubles with wireless. Here is the info that may help you in assisting me. Thanks.

Machine Brand and Model
HP COMPAQ nx6110

Wireless Brand and Model
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Wireless Chipset
02:04.0 0280: 14e4:4320 (rev 03)

Ubuntu Version
Description:    Ubuntu 8.04

Kernel/architecture
Linux my-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Used step 2f

Output of lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:12:79:bd:d3:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.106 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:90:4b:aa:58:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by syga on 2008-04-26
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

05:00.0 0280: 14e4:4311 (rev 01)

Ubuntu 8.04

2.6.24-16-generic i686
 

I have a Dell Inspiron 1501 with the specs as listed above. 

Just installed Hardy and used the restricted Broadcom driver. I can connect to any non secured wireless network but could not connect to any secured wireless network. Also I could not turn the wireless card on or off using the keyboard, it was stuck on all the time.

I tried the Hardy bug fix from:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This worked, but the connection was too slow and I still could not control my wireless card from the keyboard.

Next, I tried the full procedure from the above website and used step 2a along with the Hardy bug fix.

Now, I have a fast connection and everything seems to work properly.

This wireless card seems to have a lot of problems and I tried different ways to get it to work properly. The full procedure from the above website seems to fix the problem the first time.

---

### Post by Jamie Jackson on 2008-04-26
> **hessianmatrix said:**
> Hi,

Just upgraded to Hardy from Gutsy last night and had troubles with wireless. Here is the info that may help you in assisting me. Thanks.

Machine Brand and Model
HP COMPAQ nx6110

Wireless Brand and Model
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Wireless Chipset
02:04.0 0280: 14e4:4320 (rev 03)

Ubuntu Version
Description:    Ubuntu 8.04

Kernel/architecture
Linux my-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Used step 2f

Output of lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:12:79:bd:d3:81
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.106 latency=64 module=ssb multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:90:4b:aa:58:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Seems like you just need to do the section entitled "Hardy Bug Fix." Try that out and report back.

---

### Post by Jamie Jackson on 2008-04-26
> **syga said:**
> 05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

05:00.0 0280: 14e4:4311 (rev 01)

Ubuntu 8.04

2.6.24-16-generic i686
 

I have a Dell Inspiron 1501 with the specs as listed above. 

Just installed Hardy and used the restricted Broadcom driver. I can connect to any non secured wireless network but could not connect to any secured wireless network. Also I could not turn the wireless card on or off using the keyboard, it was stuck on all the time.

I tried the Hardy bug fix from:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

This worked, but the connection was too slow and I still could not control my wireless card from the keyboard.

Next, I tried the full procedure from the above website and used step 2a along with the Hardy bug fix.

Now, I have a fast connection and everything seems to work properly.

This wireless card seems to have a lot of problems and I tried different ways to get it to work properly. The full procedure from the above website seems to fix the problem the first time.

That's good news, thanks for the feedback. Did the fix work after a reboot? Just checking if my init script is doing its job (I can't easily test that part of it, as I haven't *installed* Hardy to try it out).

---

### Post by hessianmatrix on 2008-04-26
> **Jamie Jackson said:**
> Seems like you just need to do the section entitled "Hardy Bug Fix." Try that out and report back.

I am writing this message from a different computer.

When I executed the Remove Stock Ndiswrapper part, it killed my wired connection and result of which is no wireless and no wired connection for me. 

I have very little internet for me.

I got hold of some friend's PC, and trying to get the wired connection back so that I can continue with the remaining hardy bug fix thing.

Any ideas...to grant me more internet.

---

### Post by Jamie Jackson on 2008-04-26
> **hessianmatrix said:**
> I am writing this message from a different computer.

When I executed the Remove Stock Ndiswrapper part, it killed my wired connection and result of which is no wireless and no wired connection for me. 

I have very little internet for me.

I got hold of some friend's PC, and trying to get the wired connection back so that I can continue with the remaining hardy bug fix thing.

Any ideas...to grant me more internet.

A couple things: 

I'm just now noticing you have a third-generation version of this card [14e4:4320 (rev 03)]. I don't think anybody's done this one before with my howto, so we've gotta figure out what driver you need, but anyway, let's ignore that for the moment...

Okay, you were supposed to apply the Hardy Bug Fix, and then stop and see if you had wireless.

I doubt you will need to compile ndiswrapper, and that's really just a last resort.

So, did you check, after applying the Hardy fix, to see if you had wireless at that point?

Once I have the answer to that question, I can help you.

---

### Post by hessianmatrix on 2008-04-27
I don't have wireless at this point.

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> I don't have wireless at this point.

I know you don't at *this point*, but... well never mind. Which was the last line you issued from the "remove stock ndiswrapper" instructions?

---

### Post by hessianmatrix on 2008-04-27
> **Jamie Jackson said:**
> I know you don't at *this point*, but... well never mind. Which was the last line you issued from the "remove stock ndiswrapper" instructions?

sudo rm -r /etc/modprobe.d/ndiswrapper

The above command is the last one I issued, and rebooted as suggested. It resulted into no wired connection at all. 

I don't know if this thing helps you in anyway. I see this blue light glowing on, the wireless indicator on the laptop, but I have no wireless network connection.

Thanks a million for your patience and help.

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> sudo rm -r /etc/modprobe.d/ndiswrapper

The above command is the last one I issued, and rebooted as suggested. It resulted into no wired connection at all. 

I don't know if this thing helps you in anyway. I see this blue light glowing on, the wireless indicator on the laptop, but I have no wireless network connection.

Thanks a million for your patience and help.

No problem. Let's take smaller steps this time, and try (just) this first:

```

sudo apt-get install ndiswrapper-utils-1.9
cd ~/bcm43xx #stop here if you get an error
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```

Can you see wireless access points in NetworkManager now?

If you can't, issue the following, and send the output. ```
lshw -C network
```

Then stop there, and wait for my reply.

---

### Post by hessianmatrix on 2008-04-27
> **Jamie Jackson said:**
> No problem. Let's take smaller steps this time, and try (just) this first:

```

sudo apt-get install ndiswrapper-utils-1.9
cd ~/bcm43xx #stop here if you get an error
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

```

Can you see wireless access points in NetworkManager now?

If you can't, issue the following, and send the output. ```
lshw -C network
```

Then stop there, and wait for my reply.

I don't see wireless access points in NetworkManager after running the above commands, without any errors.

Here is the out from the command, lshw -C network

*-network:0
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 4
bus info: pci@0000:02:04.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1 UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64 
*-network
description: Wireless interface
physical id: 1
logical name: eth1
serial: 00:90:4b:aa:58:3f
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> I don't see wireless access points in NetworkManager after running the above commands, without any errors.

You're almost there. Now, run the following. (Ignore any errors that might happen at the first or second line.) ```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb

```

If you can't see wireless networks, give the output of "lshw -C network" again, then stop.

If you CAN see wireless networks, issue:
```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local
```

Now, you should be able to reboot, and still have wireless.

---

### Post by hessianmatrix on 2008-04-27
> **Jamie Jackson said:**
> You're almost there. Now, run the following. (Ignore any errors that might happen at the first or second line.) ```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb

```

If you can't see wireless networks, give the output of "lshw -C network" again, then stop.

If you CAN see wireless networks, issue:
```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local
```

Now, you should be able to reboot, and still have wireless.

I don't see any wireless access points. Here is the output from the command, lshw - C network.

Here is the out from the command, lshw -C network

*-network:0
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 4
bus info: pci@0000:02:04.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1 UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64
*-network
description: Wireless interface
physical id: 1
logical name: eth1
serial: 00:90:4b:aa:58:3f
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by isacvale on 2008-04-27
Hey,
I'm on a HP Pavilion dv9000 with Hardy 64 and Broadcom BCM 4312 rev 2. This notebook had never, EVER, had a working wireless connection up to 5 minutes ago.
It indeed had the HardyBug, and yes, the instructions fixed it like a charm - already restarted the system and it's up and running, "don't had no need to compile no nothing", thankyou.
I must say, I had never seen instructions/tutorials work so perfectly before. Congratulations!

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> I don't see any wireless access points. Here is the output from the command, lshw - C network.

Here is the out from the command, lshw -C network

*-network:0
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 4
bus info: pci@0000:02:04.0
version: 03
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1 UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64
*-network
description: Wireless interface
physical id: 1
logical name: eth1
serial: 00:90:4b:aa:58:3f
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Bah! ssb still has control. What happens if you do:
```
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
lshw -C network
```

(If wireless works at this point, it's not permanent, because you'll want ssb back, but taking over your wireless card.)

---

### Post by Jamie Jackson on 2008-04-27
> **isacvale said:**
> Hey,
I'm on a HP Pavilion dv9000 with Hardy 64 and Broadcom BCM 4312 rev 2. This notebook had never, EVER, had a working wireless connection up to 5 minutes ago.
It indeed had the HardyBug, and yes, the instructions fixed it like a charm - already restarted the system and it's up and running, "don't had no need to compile no nothing", thankyou.
I must say, I had never seen instructions/tutorials work so perfectly before. Congratulations!

Nice! As payment for services rendered, would you please post all of the details that I ask for in the first post? ;-)

---

### Post by hessianmatrix on 2008-04-27
> **Jamie Jackson said:**
> Bah! ssb still has control. What happens if you do:
```
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
lshw -C network
```

(If wireless works at this point, it's not permanent, because you'll want ssb back, but taking over your wireless card.)

I had to use sudo rmmod b43 to use sudo rmmod ssb. When I did that, here is the out from the command, lshw -C network.


*-network:0 UNCLAIMED
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 4
bus info: pci@0000:02:04.0
version: 03
width: 32 bits
clock: 33MHz
configuration: latency=64 
*-network:1 UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64 

No wireless access points yet.

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> I had to use sudo rmmod b43 to use sudo rmmod ssb. When I did that, here is the out from the command, lshw -C network.


*-network:0 UNCLAIMED
description: Network controller
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 4
bus info: pci@0000:02:04.0
version: 03
width: 32 bits
clock: 33MHz
configuration: latency=64 
*-network:1 UNCLAIMED
description: Ethernet controller
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: e
bus info: pci@0000:02:0e.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=64 

No wireless access points yet.

Well, at least I'm not seeing ssb now. Please let me know what "ndiswrapper -l" shows.

---

### Post by hessianmatrix on 2008-04-27
> **Jamie Jackson said:**
> Well, at least I'm not seeing ssb now. Please let me know what "ndiswrapper -l" shows.

The output from the command, ndiswrapper -l is as follows.

bcmwl5: driver installed
       device (14E4:4320) present (alternate driver: ssb)

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> The output from the command, ndiswrapper -l is as follows.

bcmwl5: driver installed
       device (14E4:4320) present (alternate driver: ssb)

You haven't rebooted since issuing the rmmod and modprobes have you? (Rebooting resets these temporary changes.)

I'm heading to bed now, but might be back tomorrow...

---

### Post by hessianmatrix on 2008-04-27
> **Jamie Jackson said:**
> You haven't rebooted since issuing the rmmod and modprobes have you? (Rebooting resets these temporary changes.)

I'm heading to bed now, but might be back tomorrow...

Yes, you are correct. I didn't reboot since the sequence of rmmod and modprobe commands.

Thanks a lot for your help and patience. Have a good night and sweet dreams.

Later.

---

### Post by laflo on 2008-04-27
Hey there. 

Thank you for this great how to, so it is the first that get my Broadcom 4306 running. 

Even though there is a problem: 
**What  I did:**
I followed your how to and choosed option 2b
I did not compiled the ndiswrapper
**My Problems**
1) I can scan for networks. (working in an wpa2 secured network which i want to join) And in Network Manager I can see my network.
BUT I cannot connect to my Network. The Symbol of the Network Manager is just turning into a circle.

2)At restart i always have to enter
```
"sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb"

```
to see the networks. 

Of course i tried to enter
```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local
```
to make this permanent, but that didn't work for me. 

Hope u can help me.

---

### Post by jeffd3w on 2008-04-27
Many thanks, it seemed to work fine for me. Details are

Machine: Compaq Presario V3000

$ lspci | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

$ lspci -n | grep '14e4:43'
01:00.0 0280: 14e4:4312 (rev 01)

$ lsb_release -d
Description:	Ubuntu 8.04

$ uname -mr
2.6.24-16-generic x86_64

No extra boot options
Didn't need to compile ndiswrapper
Used Step 2b
Had to apply the "Hardy Bug Fix"
Added changes to /etc/init.d/rc.local, and all seems to work after reboot
:)

---

### Post by Metaleks on 2008-04-27
Would like to add that under 64 bit Hardy, I have managed to get it to work.  My chipset was 4328.  According to the wiki, I'm the second one to get it to work :)

I didn't need to compile ndiswrapper from source, or even use the hardy 'beta' steps.  Just the regular guide worked.  Many thanks for it.

---

### Post by Jamie Jackson on 2008-04-27
> **laflo said:**
> Hey there. 

Thank you for this great how to, so it is the first that get my Broadcom 4306 running. 

Even though there is a problem: 
**What  I did:**
I followed your how to and choosed option 2b
I did not compiled the ndiswrapper
**My Problems**
1) I can scan for networks. (working in an wpa2 secured network which i want to join) And in Network Manager I can see my network.
BUT I cannot connect to my Network. The Symbol of the Network Manager is just turning into a circle.

2)At restart i always have to enter
```
"sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb"

```
to see the networks. 

Of course i tried to enter
```
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local
```
to make this permanent, but that didn't work for me. 

Hope u can help me.

I'm wondering if you've tried other encryption (WEP, WPA, or unencrypted), and what cipher type you're using (TKIP, AES).

If you can connect to other types of networks, but not WPA2, this is sorta outside my range of expertise. The only thing that I could suggest is possibly trying other step 2 versions (starting with step 2a). I figure it might be possible that a particular driver can get a device partially working, but only the ideal driver can get all functions working. This is just a shot in the dark, half-baked theory, though.

Googling 4306 WPA2 yields a mixed bag of people struggling with and/or succeeding with it. I don't have this device to try to troubleshoot. (I've got the BCM4311 rev 01, which *is* working with WPA2/TKIP.)

---

### Post by Jamie Jackson on 2008-04-27
> **Metaleks said:**
> Would like to add that under 64 bit Hardy, I have managed to get it to work.  My chipset was 4328.  According to the wiki, I'm the second one to get it to work :)

I didn't need to compile ndiswrapper from source, or even use the hardy 'beta' steps.  Just the regular guide worked.  Many thanks for it.

The previous 4328 user couldn't get WPA working. Have you tried that? If so, is it WPA or WPA2? Also, what cipher type?

---

### Post by Jamie Jackson on 2008-04-27
> **hessianmatrix said:**
> Yes, you are correct. I didn't reboot since the sequence of rmmod and modprobe commands.

Thanks a lot for your help and patience. Have a good night and sweet dreams.

Later.

Hey, my dreams *were* better than average. :D

Anyway, I'm running out of ideas, but I'm wondering about one thing: On the ssb bug report, one user claimed he needed to remove and re-add one more module. You might try giving this a shot:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ohci_hcd
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe ohci_hcd
sudo modprobe b44

```

If this doesn't work, we might try doing something over AIM, or something.

---

### Post by mick129 on 2008-04-27
[WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") worked for me!  I'm so happy to have WiFi working.

Machine: Dell Latitude D800

$ lspci | grep Broadcom
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

$ lspci -n | grep '14e4:43'
02:03.0 0280: 14e4:4320 (rev 02)

$ lsb_release -d
Description: Ubuntu 8.04

$ uname -mr
2.6.24-16-generic x86_64

I didn't have to compile ndiswrapper.  I used step "2f" with the Hardy Bug Fix.  I didn't exactly follow the Hardy Bug fix though.  Instead of rmmod b43 and rmmod b44, I used rmmod b43legacy because I got a "b43legacy depends on ssb" error.  And now I can see WiFi access points.

Thanks!
-mick

---

### Post by Jamie Jackson on 2008-04-27
> **mick129 said:**
> 
I didn't have to compile ndiswrapper.  I used step "2f" with the Hardy Bug Fix.  I didn't exactly follow the Hardy Bug fix though.  Instead of rmmod b43 and rmmod b44, I used rmmod b43legacy because I got a "b43legacy depends on ssb" error.  And now I can see WiFi access points.

Good information! Did you add that rmmod just before the ssb rmmod?

---

### Post by siruiw on 2008-04-27
This method solved problem *temporarily*. 
I used Hardy bug fix, but it only worked for few minutes, so do the "permanent" solution. Still, it's confusing. Sometimes it works, sometimes it doesn't. 

Laptop model: HP Dv2404ca
Hardy Heron 8.04

---

### Post by Jamie Jackson on 2008-04-27
> **siruiw said:**
> This method solved problem *temporarily*. 
I used Hardy bug fix, but it only worked for few minutes, so do the "permanent" solution. Still, it's confusing. Sometimes it works, sometimes it doesn't. 

Laptop model: HP Dv2404ca
Hardy Heron 8.04

Please post the details I ask for in the first post. Also, provide the output of ```
lshw -C network
```

---

### Post by Damakin on 2008-04-27
I'm using the 64-bit Hardy release with a 4306 chipset and I have NOT been successful in getting my wireless card to work. The exact problem that I've been having that this guide has not solved is that I cannot seem to see any wireless networks even though there are plenty in range, and the router itself is in the hallway only several feet away. This was the first thing that I have done after a fresh install from the alternate CD. 

Here is the output of "lshw -C network"
```

  *-network
	description: Ethernet interface
	product: 88EE8056 PCI-E Gigabit Ethernet Controller
	vendor: Marvell Technology Group Ltd.
	physical id: 0
	bus info: pci@0000:04:00.0
	logical name: eth0
	version: 14
	serial: 00:16:e6:df:c7:57
	width: 64 bits
	clock: 33MHz
	capabilities: bus_master cap_list ethernet physical
	configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
	description: Network controller
	product: BCM4306 802.11b/g Wireless LAN Controller
	vendor: Broadcom Corporation
	physical id: 2
	bus info: pci@0000:05:02.0
	version: 02
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master
	configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
	description: Wireless interface
	physical id: 1
	logical name: wlan0
	serial: 00:30:bd:f2:17:a9
	capabilities: ethernet physical wireless
	configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

I would be extremely grateful if someone could help me out with getting this whole thing working. I don't mind doing a reinstall of the OS if necessary.

[EDIT] I also tried compiling ndiswrapper by following the guide but nothing appeared to change

---

### Post by Jamie Jackson on 2008-04-27
> **Damakin said:**
> 
I would be extremely grateful if someone could help me out with getting this whole thing working. I don't mind doing a reinstall of the OS if necessary.

[EDIT] I also tried compiling ndiswrapper by following the guide but nothing appeared to change

I doubt if anybody in Gutsy or Hardy really has to do an ndiswrapper compilation. I think it's really a last resort for Feisty (or less) users.

But anyway, I *think* you just need to do the [Hardy Bug Fix]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0").

Let me know what happens.

---

### Post by Damakin on 2008-04-27
Oh yes, that's something I forgot to add. I did try the Hardy fix but nothing happened. I still could not see any wireless networks. The output from lshw that I pasted in my last post above is the output that I see after trying the Hardy fix. It seems to me that for some reason it did not change the module to ndiswrapper although I am unsure why.

---

### Post by Jamie Jackson on 2008-04-27
> **Damakin said:**
> Oh yes, that's something I forgot to add. I did try the Hardy fix but nothing happened. I still could not see any wireless networks. The output from lshw that I pasted in my last post above is the output that I see after trying the Hardy fix. It seems to me that for some reason it did not change the module to ndiswrapper although I am unsure why.

Did you get any errors (including the ones I advised you to ignore) during the Hardy Bug Fix? (I'm especially interested in potential errors during "sudo rmmod ssb".)

---

### Post by Damakin on 2008-04-27
The only errors that I get are:
```

ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules

```

All of the other commands did not give any output

---

### Post by Jamie Jackson on 2008-04-27
> **Damakin said:**
> The only errors that I get are:
```

ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules

```

All of the other commands did not give any output

One other thing: Just today, I added the line `sudo rmmod b43legacy` to the Hardy Bug Fix, did you try the bug fix before or after I added that line?

---

### Post by Damakin on 2008-04-27
Yeah, I did run that command as your guide instructed.

---

### Post by Jamie Jackson on 2008-04-27
> **Damakin said:**
> ...

Another thing, I'm no modules expert by any stretch, so I don't know if this will tell me what I want to know, but could you provide the output of "lsmod"?

Something's either preventing your ndiswrapper from loading or preventing ssb from unloading, and we haven't seemed to have figured out what that is yet.

---

### Post by Damakin on 2008-04-27
```

Module                  Size  Used by
b43legacy             142120  0 
ssb                    37252  1 b43legacy
ndiswrapper           243872  0 
ipv6                  311720  14 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
acpi_cpufreq           10832  0 
cpufreq_ondemand       11152  2 
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
cpufreq_conservative    10632  0 
cpufreq_stats           8416  0 
freq_table              6464  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               6656  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
ac                      8328  0 
lp                     14916  0 
loop                   21508  0 
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
evdev                  14976  3 
parport_pc             41128  1 
parport                44300  3 ppdev,lp,parport_pc
mac80211              192532  1 b43legacy
lmpcm_usb               8192  0 
pcspkr                  4992  0 
cfg80211               17680  1 mac80211
snd_emu10k1_synth       9472  0 
snd_emux_synth         40960  1 snd_emu10k1_synth
snd_seq_virmidi         9344  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_emu10k1           162272  3 snd_emu10k1_synth
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
snd_ac97_codec        123224  1 snd_emu10k1
ac97_bus                3840  1 snd_ac97_codec
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_usb_audio         100384  1 
snd_usb_lib            21120  1 snd_usb_audio
snd_hda_intel         440408  3 
usblp                  17664  0 
sky2                   53892  0 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  5 snd_emu10k1,snd_ac97_codec,snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  3 snd_emu10k1,snd_hda_intel,snd_pcm
snd_hwdep              12552  4 snd_emux_synth,snd_emu10k1,snd_usb_audio,snd_hda_intel
i2c_core               28544  0 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  4 snd_seq_virmidi,snd_emu10k1,snd_usb_lib,snd_seq_midi
snd_seq_midi_event     10112  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                63232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10644  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 10912  0 
snd                    70856  29 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_usb_audio,snd_usb_lib,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               15312  0 
iTCO_vendor_support     5764  1 iTCO_wdt
intel_agp              30624  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sd_mod                 33280  2 
pata_jmicron            8448  0 
ata_generic             9988  0 
usbhid                 35168  0 
hid                    44992  1 usbhid
ahci                   33028  0 
pata_acpi               9856  0 
ata_piix               24196  1 
libata                176304  5 pata_jmicron,ata_generic,ahci,pata_acpi,ata_piix
scsi_mod              178488  4 sr_mod,sg,sd_mod,libata
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               169904  9 ndiswrapper,lmpcm_usb,snd_usb_audio,snd_usb_lib,usblp,usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  3 

```

Thanks for stepping through this with me by the way :)

---

### Post by Jamie Jackson on 2008-04-27
> **Damakin said:**
> 
Thanks for stepping through this with me by the way :)

This is annoying, and you're not the only one who can't break the surly bonds of ssb.

If I am interpreting your lsmod correctly, it seems that this ought to do it:

```
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

...but obviously, that's not cutting it.

Unless something went wrong earlier in the process with ndiswrapper driver installation, I'm at a loss.

For kicks, what's "ndiswrapper -l;ndiswrapper -v" yield?

---

### Post by Damakin on 2008-04-27
Nothing appeared to go wrong when I was installing it (both times, one after compiling ndiswrapper myself). I could uninstall it and reinstall it, and give you the entire output of the process if you would like.

```

bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:	/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:	1.52
vermagic:	2.6.24-16-generic SMP mod_unload

```

---

### Post by Jamie Jackson on 2008-04-27
> **Damakin said:**
> Nothing appeared to go wrong when I was installing it (both times, one after compiling ndiswrapper myself). I could uninstall it and reinstall it, and give you the entire output of the process if you would like.

```

bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:	/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:	1.52
vermagic:	2.6.24-16-generic SMP mod_unload

```

Nah, I figure you've done the steps right. I've called on the help of kevdog (who is way better at the low level nuts and bolts than I am) to help us figure out how to give ssb the knockout punch.

Stay tuned...

---

### Post by fmaks12345 on 2008-04-27
I had issues with the ssb bug in Hardy that your explanation fixed nicely. Thank you.

---

### Post by kevdog on 2008-04-27
I havent tried this -- so be forewarned -- just to let everyone know that yes I have a Broadcom card, but no I haven't upgraded (or plain old installed from scratch Hardy yet -- hopefully tonight).

Ive seen others report that you post add b43 and ssb to the blacklist file.  I guess ssb is the user space utilities of the b43 wireless driver, similar to how ndiswrapper has a user space utilty.  

What happens if you just do the following:

sudo modprobe -r ndiswrapper
sudo modprobe -r b43
sudo modprobe -r bcm43xx
sudo modprobe -r ssb
sudo modprobe ndiswrapper

Does the ndiswrapper kernel module show up without any errors when checking lshw -C network?  Also check dmesg to see if the custom ndiswrapper kernel module was loaded appropriately.

---

### Post by kevdog on 2008-04-27
From what I was reading on the Arch Forums ssb attempts to be loaded by the b43 wireless driver and the b44 wired driver.  In order to prevent ssb from being associated with the wireless card, ndiswrapper must be loaded prior to ssb.  Of course if you dont have a wired Broadcom NIC then you really dont need b44 or ssb at all.

One thing Im not clear about is the order drivers load in Ubuntu.  b44, b43, ssb, and mac80211 are built-into the kernel (come in by default from the vanilla kernel release) whereas ndiswrapper is a custom kernel module.  I dont know what file controls the order of driver loading.  

If you dont need the b44 wired driver, Ive seen other report that adding bcm43xx b43 mac80211 cfg80211 ssb to the blacklist file and then adding ndiswrapper the the /etc/modules file works.

If you need the b44 driver in addition to ndiswrapper -- this is the problem.  You want to load ndiswrapper prior to b44 and ssb -- I dont know how to specify this.  Perhaps one way would be to blacklist the modules listed above, and then in the /etc/modules file put ndiswrapper above b44, ssb, and mac80211.  I don't have a Broadcom wired NIC so its impossible for me to try this assumption.

---

### Post by kevdog on 2008-04-27
One user npallet reports this as a successful strategy (I have not confirmed this approach although its similar to what I was thinking):

In short, I did the following:

1. Disabled the "restricted Driver" (b43 using b43-fwcutter)

2. Installed ndisgtk,ndiswrapper-common, and ndiswrapper-utils, from the standard "hardy" repositories using "apt-get".

3. removed existing modules as follows:

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb


4. Installed ndiswrapper driver as follows (as root):

ndiswrapper -i /path/to/bcmwl5a.inf
ndiswrapper -m
modprobe ndiswrapper

5. added entry for ndiswrapper in "/etc/modules"

6.removed entry for b43 from "/etc/modules"

7. Added the following lines to "/etc/rc.local"

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

8. rebooted the laptop.

When the system came back up, it connected immediately to the office access point using ndiswrapper at 48Mb

9. Issued the following command (as root):

iwconfig wlan0 rate 54M

The connection now shows up as 54Mb in iwconfig, network-manager, and gnome-nettool (Network Tools).


Im not sure about steps 5,6,7.  Seems like if ndiswrapper is mentioned before b44 in the /etc/modules file and the remainder of the drivers are blacklist the the /etc/modprobe.d/blacklist file, the use of the rc.local file would be unnecessary.

---

### Post by Damakin on 2008-04-27
I have tried using npallet's approach, and I have found out that whenever ssb/b43legacy is unloaded my wireless interface appears as "UNCLAIMED" under "lshw -C network" which is very strange, ndiswrapper should be loaded...

---

### Post by kevdog on 2008-04-27
Did you verify ndiswrapper was loaded with lsmod or did you look in dmesg for any errors that may have occurred with ndiswrapper upon loading the module?

---

### Post by SpectralDesign on 2008-04-27
* Machine Brand and Model
HP/Compaq Presario V6000 (6402ca)

    * Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

    * Wireless Chipset: lspci -n | grep '14e4:43'
02:00.0 0280: 14e4:4311 (rev 02)

    * Ubuntu Version: lsb_release -d
Description:	Ubuntu 8.04

    * Kernel / Architecture: uname -mr
2.6.24-16-generic i686

    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)

    * Whether or not you had to compile NDISWrapper
positive

    * Which version of Step 2 you used
2a

    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
positive (had orange wlan light & module=ssb before Hardy Bug Fix, blue wlan light and module=ndiswrapper (etc) after)

Additional Info:
I've tried reconfiguring my wireless router to different security states.  No matter what I try, the laptop interface won't get online wirelessly...

---

### Post by adamitj on 2008-04-27
* Machine Brand and Model
HP Pavilion dv6500 (dv6000 series)

* Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

* Wireless Chipset: lspci -n | grep '14e4:43'
03:00.0 0280: 14e4:4311 (rev 02)

* Ubuntu Version: lsb_release -d
Description: Ubuntu Desktop 8.04

* Kernel / Architecture: uname -mr
2.6.24-16-generic i686

* Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
No one.

* Whether or not you had to compile NDISWrapper
Yes, but first I tried with the ubuntu packages from repository.

* Which version of Step 2 you used
2a

* If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
Yes, but does not have any result.

Additional Info:
I do not know what to do. After cleaned the entire hd by formatting it, reinstalled Ubuntu Hardy Heron 8.04, I tried all of those steps and the wireless card does not want to work.
The orange light does not turn blue, as it should. Never.
There is another problem to me, I tried these commands below, I get these results:

```
**sudo lshw -C network:**
PCI (sysfs) --> I needed to close it with CTRL+C, it stayed more than 10 minutes and does not show anything.
```

```
**ndiswrapper -l**
bcmwl5 : driver installed
	device (14E4:4311) present. (alternate driver: ssb)
```

Plase, someone help me...

---

### Post by siruiw on 2008-04-27
> **Jamie Jackson said:**
> Please post the details I ask for in the first post. Also, provide the output of ```
lshw -C network
```

Sorry, here it is:

    * Machine Brand and Model: HP Dv2404ca
    * Wireless Brand and Model: 01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
    * Wireless Chipset:```

00:00.0 0500: 10de:02f0 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:05.0 0300: 10de:0244 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0260 (rev a3)
00:0a.1 0c05: 10de:0264 (rev a3)
00:0a.3 0b40: 10de:0271 (rev a3)
00:0b.0 0c03: 10de:026d (rev a3)
00:0b.1 0c03: 10de:026e (rev a3)
00:0d.0 0101: 10de:0265 (rev f1)
00:0e.0 0101: 10de:0266 (rev f1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a3)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0280: 14e4:4311 (rev 02)
03:09.0 0c00: 1180:0832
03:09.1 0805: 1180:0822 (rev 19)
03:09.2 0880: 1180:0843 (rev 0a)
03:09.3 0880: 1180:0592 (rev 05)
03:09.4 0880: 1180:0852 (rev ff)
```
    * Ubuntu Version: Ubuntu 8.04
    * Kernel / Architecture: 2.6.24-16-generic i686
    * No extra boot option using
    * Did not compile NDISWrapper
    * Step 2a was being used.
    * Hardy Bug Fix was used.

> **adamitj said:**
> ```
**sudo lshw -C network:**
PCI (sysfs) --> I needed to close it with CTRL+C, it stayed more than 10 minutes and does not show anything.
```

Same Here!

One more thing: this model comes with Windows Vista, which works well with the wireless. I hacked it into XP and used driver you mentioned on the wiki (sp34152.exe). Interesting thing is, the wireless have the similar problem with both Ubuntu and XP: The wireless *sometimes* available immediately after the first log on of a startup, then became unavailable shortly. I could confirm that this is a problem with the laptop rather than router because the laptop can't even scan for networks (most of my neighbors have wifi) and my NintendoDS works with my wifi. 

I was wondering if the Vista 32 bit driver (sp36542.exe) could work.

Update: It seems the "Permanent" Hardy (8.04) solution is not working for me after reboot. (It's not showing up on the network menu and System->Admin->Network)

---

### Post by adamitj on 2008-04-28
> **adamitj said:**
> * Machine Brand and Model
HP Pavilion dv6500 (dv6000 series)...

After hours of expensive tries, I found the problem.

The script below was inserted on /etc/rc.local file before the exit 0 command, and does not work.

If I run it AFTER the login, the card works perfectly.

The script is:
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
```

---

### Post by abrigham on 2008-04-28
> **Jamie Jackson said:**
> You might want to try other drivers, either other step twos, or whatever XP driver is recommended by DELL. I wonder if the driver you guys are using is just "almost" the right one, and if another driver might be the ticket for WPA.

If you do find the magic combo, let me know what it is, and I'll put it up on the wiki.

Sorry I didn't get back to you sooner, but I tried both of the Dell downloads listed on the Wiki (steps 2d and 2e) both of which are a BCMWL5 driver. I pulled the latest driver from Dell's website for my card (Dell Wireless 1505, BCM4328 ) under WinXP (R174291), and it's actually a BCMWL6. I tried loading that driver, and it recognizes hardware available but then my wifi light doesn't come on like it does with the bcmwl5. I'll keep playing around with it. I'm thinking it MIGHT be related to the SSB bug as I don't even need to do the workaround when using the bcmwl5 and haven't tried it w/ 6.

---

### Post by kevdog on 2008-04-28
version 6 is the vista driver and will not work.  Just an FYI.  A further clarification about the rc.local script may be needed.

---

### Post by SpectralDesign on 2008-04-28
speaking of the rc.local.....

I managed to get the card working, and with WEP even, using your link to the [command line goodies]("http://ubuntuforums.org/showthread.php?t=571188"), but after a reboot - nada.  I turned the command lines into a shell script... if I call said shell script from rc.local, it will run before I login to the GUI, right?

Of course I can just run it manually, but it'd be nice to be done with that!

---

### Post by hessianmatrix on 2008-04-28
> **Jamie Jackson said:**
> Hey, my dreams *were* better than average. :D

Anyway, I'm running out of ideas, but I'm wondering about one thing: On the ssb bug report, one user claimed he needed to remove and re-add one more module. You might try giving this a shot:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ohci_hcd
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe ohci_hcd
sudo modprobe b44

```

If this doesn't work, we might try doing something over AIM, or something.

This didn't work. But the command, modprobe b44 gave me back my wired network connection.

---

### Post by adamitj on 2008-04-28
> **SpectralDesign said:**
> speaking of the rc.local.....

I managed to get the card working, and with WEP even, using your link to the [command line goodies]("http://ubuntuforums.org/showthread.php?t=571188"), but after a reboot - nada.  I turned the command lines into a shell script... if I call said shell script from rc.local, it will run before I login to the GUI, right?

Of course I can just run it manually, but it'd be nice to be done with that!

Yeah, It will be very appreciable if anyone have a solution to turn on wireless for all users, without manual execution of the script I mentioned in my last post.

The thing is: rc.local is not activating ndiswrapper drivers... the script works only after login on gnome.

---

### Post by kevdog on 2008-04-28
You need to understand that I'm no expert at this subject (as far as messing with rc calls) and I'm figuring this out with you as we go along.

The use of the rc.local file (while it works for many) is a HACKED solution.  The debian docs do not recommend this particular way of getting these things to work, rather creating specific run level scripts (which isn't that much different that the rc.local method however its more elegant):

11.5 Every distribution seems to have a different boot-up method. Tell me about Debian's.

Like all Unices, Debian boots up by executing the program init. The configuration file for init (which is /etc/inittab) specifies that the first script to be executed should be /etc/init.d/rcS. This script runs all of the scripts in /etc/rcS.d/ by sourcing or forking subprocess depending on their file extension to perform initialization such as to check and to mount file systems, to load modules, to start the network services, to set the clock, and to perform other initialization. Then, for compatibility, it runs the files (except those with a `.'in the filename) in /etc/rc.boot/ too. Any scripts in the latter directory are usually reserved for system administrator use, and using them in packages is deprecated.

After completing the boot process, init executes all start scripts in a directory specified by the default runlevel (this runlevel is given by the entry for id in /etc/inittab). Like most System V compatible Unices, Linux has 7 runlevels:

    *

      0 (halt the system),

    *

      1 (single-user mode),

    *

      2 through 5 (various multi-user modes), and

    *

      6 (reboot the system).

Debian systems come with id=2, which indicates that the default runlevel will be '2' when the multi-user state is entered, and the scripts in /etc/rc2.d/ will be run.

In fact, the scripts in any of the directories, /etc/rcN.d/ are just symbolic links back to scripts in /etc/init.d/. However, the names of the files in each of the /etc/rcN.d/ directories are selected to indicate the way the scripts in /etc/init.d/ will be run. Specifically, before entering any runlevel, all the scripts beginning with 'K' are run; these scripts kill services. Then all the scripts beginning with 'S' are run; these scripts start services. The two-digit number following the 'K' or 'S' indicates the order in which the script is run. Lower numbered scripts are executed first.

This approach works because the scripts in /etc/init.d/ all take an argument which can be either `start', `stop', `reload', `restart' or `force-reload' and will then do the task indicated by the argument. These scripts can be used even after a system has been booted, to control various processes.

For example, with the argument `reload' the command

     /etc/init.d/sendmail reload

sends the sendmail daemon a signal to reread its configuration file. (BTW, Debian supplies invoke-rc.d as a wrapper for invoking the scripts in /etc/init.d/.)
11.6 It looks as if Debian does not use rc.local to customize the boot process; what facilities are provided?

Suppose a system needs to execute script foo on start-up, or on entry to a particular (System V) runlevel. Then the system administrator should:

    *

      Enter the script foo into the directory /etc/init.d/.

    *

      Run the Debian command update-rc.d with appropriate arguments, to set up links between the (command-line-specified) directories rc?.d and /etc/init.d/foo. Here, '?' is a number from 0 through 6 and corresponds to each of the System V runlevels.

    *

      Reboot the system.

The command update-rc.d will set up links between files in the directories rc?.d and the script in /etc/init.d/. Each link will begin with a 'S' or a 'K', followed by a number, followed by the name of the script. Scripts beginning with 'S' in /etc/rcN.d/ are executed when runlevel N is entered. Scripts beginning with a 'K' are executed when leaving runlevel N.

One might, for example, cause the script foo to execute at boot-up, by putting it in /etc/init.d/ and installing the links with update-rc.d foo defaults 19. The argument 'defaults' refers to the default runlevels, which are 2 through 5. The argument '19' ensures that foo is called before any scripts containing numbers 20 or larger. 

As soon as I figure how to use the above method, I will report back.  For the meantime, you probably need to run either a rc.local script or a script after loggin in, or just type the commands manually.

---

### Post by adamitj on 2008-04-28
Thanks for the explication, kevdog.

I'm a linux intermediate level user, and you answered me an old question that no one could help me in this way.

One more thing: all rc.d scripts are supposed to be runned as root, right?

---

### Post by joemirando on 2008-04-28
Jamie,

This worked perfectly for me! Thank you! Thank you! Thank you!

I did a fresh install of Hardy, leaving my /home partition intact.
Originally, I had used the b43-fwcutter thing, and it worked, but the system reported a connection of 1mb/sec. (which was incorrect, since I was getting speed test results from [www.speakeasy.net/speedtest](www.speakeasy.net/speedtest) of ~3.8 mb/sec. while a desktop machine ethernetted to the router was giving me ~5 mb/sec.) It seemed like a waste to have a 802.11g wireless router and only a 10mb/sec. connection to it.

Once I figured out that I had to defeat the line-wrapping on that one long string of commands, all went well, and am getting ~5Mb/sec. transfer via wireless (and the network manager now reports a 54 Mb/sec. connection).

The wireless card is designated by Dell as a Dell TrueMobile 1300 Mini-PCI.
The router is a LinkSys WRT54G Firmware Version: v4.21.1


Here is my info:

[LIST]
[*]Dell Inspiron 5100
[*]02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
[*]02:02.0 0280: 14e4:4320 (rev 02)
[*]Ubuntu 8.04
[*]2.6.24-16-generic i686
[*]No user-added extra boot options
[*]I used Step 2f with the driver downloaded from the provided link
[*]ndiswrapper 1.50 package from distro
[*]"Hardy Bug Fix" workaround used
[/LIST]

After using your how-to, I installed kubuntu-desktop, and everything is as I want it. The wireless connection now comes up on boot, which it DID NOT do when using ndiswrapper with 7.10 (I used to have to 'start' the connection twice to get it to work).

My only complaint is that it took some digging to find your how-to in the first place. But I'm a happy camper now! All's well that ends well. :)


Thanks again,

Joe Mirando

---

### Post by kevdog on 2008-04-28
Yes all rc scripts are run as root.  Im an intermediate user also and figuring out some of this stuff for the first time.  I know enough when things are hacked together that work -- meaning its not the proper way of doing things -- however figuring out how to solve the problem once its identified is another level of understanding.

---

### Post by abrigham on 2008-04-28
> **kevdog said:**
> version 6 is the vista driver and will not work.  Just an FYI.  A further clarification about the rc.local script may be needed.

LOL yeah, I figured that out after I posted. When I pulled the XP drivers down again, it was version 5, and I realized it was the same file mentioned in step 2e :) I still haven't tried any of the other drivers from step 2. Also, I never really mentioned this before, but I work in Tech Support at Dell (just not on the Linux side LOL), so I'm going to ask around to some of my internal sources and will certainly share any insight I may receive.

---

### Post by him610 on 2008-04-28
Today I upgraded my vintage Sony Vaio PCG-FXA36 AMD Athlon 1GHz 512MB RAM from Xubuntu 7.10 to 8.04. See post 404. 
Everything seemed to go okay until I figured out I had the dreaded "SSB" bug. Fortunately for me, a kind soul or two had already experienced this problem and worked through a solution. 
Using your Hardy Bug Fix, I was able to get my wireless back up with no other problems encountered. By the way, the way you posted the loooong entry worked just fine with a copy and paste, it wraps.

Thanks again, Jamie. If I could figure out how to make it official I would.:)

---

### Post by marcw on 2008-04-28
Your how-to worked well for my Presario v5000 and a 4311 rev 01 with a fresh install of Hardy.  No compiling necessary.  Nice job!  (You might want to drop the "Feisty" from the title).

One thing though...  After a restart my NetworkManager will sit and spin while trying to connect to ...  somewhere?  It will eventually time out and a click of my network will get it connected within seconds.  Alternately, if I don't wait for the time out and simply interupt the spinning by connecting to my network, it will then also connect right away.  It seems to be just that first connection attempt after a restart that gives it problems.  I've deleted the entry in the nm-editor and created it from scratch but I get the same results.  Any suggections?

---

### Post by kutjara on 2008-04-28
> **marcw said:**
> Your how-to worked well for my Presario v5000 and a 4311 rev 01 with a fresh install of Hardy.  No compiling necessary.  Nice job!  (You might want to drop the "Feisty" from the title).

One thing though...  After a restart my NetworkManager will sit and spin while trying to connect to ...  somewhere?  It will eventually time out and a click of my network will get it connected within seconds.  Alternately, if I don't wait for the time out and simply interupt the spinning by connecting to my network, it will then also connect right away.  It seems to be just that first connection attempt after a restart that gives it problems.  I've deleted the entry in the nm-editor and created it from scratch but I get the same results.  Any suggections?

That was the main reason I switched from Gnome NM to WICD. NM had an almost perverse tendency of trying to connect to any network in my area...except my own. Even though it was set up to connect to my home network, it would spend its time uselessly knocking against my neighbors' secured networks, before finally giving up. When someone moved into the apartment opposite and set up an insecure wifi network, that became the one NM selected as its first choice every time I booted up. I had to manually select my network to force NM to use it, whereupon it would connect instantly.

In the end, the only logical reason I could see for NM's behavior was that it hated me. So I switched to WICD.

WICD avoids the problem completely by the simple inclusion of a "preferred network" checkbox next to each available network entry. I select my home network as the preferred one, and my computer connects to it immediately every time.

---

### Post by Jamie Jackson on 2008-04-29
> **marcw said:**
> Your how-to worked well for my Presario v5000 and a 4311 rev 01 with a fresh install of Hardy.  No compiling necessary.  Nice job!  (You might want to drop the "Feisty" from the title).

One thing though...  After a restart my NetworkManager will sit and spin while trying to connect to ...  somewhere?  It will eventually time out and a click of my network will get it connected within seconds.  Alternately, if I don't wait for the time out and simply interupt the spinning by connecting to my network, it will then also connect right away.  It seems to be just that first connection attempt after a restart that gives it problems.  I've deleted the entry in the nm-editor and created it from scratch but I get the same results.  Any suggections?

Dropping Feisty from the titles is a can of worms I'm not prepared to handle yet. ;-) Someday... Besides, some Hardy users aren't able to break the bonds of ssb yet. There's something still missing for those users, so I don't want to make any Hardy promises I can't keep. :)

As for NM, it's a goofy animal. It always wants to connect to the wrong AP for me, before associating with my home AP. Don't know what to tell you, other than "hopefully NM will get the kinks worked out soon."

I encourage NM in this wiki, because it's stock ubuntu, and I want it to get better: I don't want all users abandoning it, and for that to slow its development.

What's this nm-editor thing you're talking about? Is there some way to actually *control* NM that I don't know about? I'll look it up if I get a minute.

---

### Post by Jamie Jackson on 2008-04-29
> **kevdog said:**
> One user npallet reports this as a successful strategy (I have not confirmed this approach although its similar to what I was thinking):

In short, I did the following:

1. Disabled the "restricted Driver" (b43 using b43-fwcutter)

2. Installed ndisgtk,ndiswrapper-common, and ndiswrapper-utils, from the standard "hardy" repositories using "apt-get".

3. removed existing modules as follows:

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb


4. Installed ndiswrapper driver as follows (as root):

ndiswrapper -i /path/to/bcmwl5a.inf
ndiswrapper -m
modprobe ndiswrapper

5. added entry for ndiswrapper in "/etc/modules"

6.removed entry for b43 from "/etc/modules"

7. Added the following lines to "/etc/rc.local"

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

8. rebooted the laptop.

When the system came back up, it connected immediately to the office access point using ndiswrapper at 48Mb

9. Issued the following command (as root):

iwconfig wlan0 rate 54M

The connection now shows up as 54Mb in iwconfig, network-manager, and gnome-nettool (Network Tools).


Im not sure about steps 5,6,7.  Seems like if ndiswrapper is mentioned before b44 in the /etc/modules file and the remainder of the drivers are blacklist the the /etc/modprobe.d/blacklist file, the use of the rc.local file would be unnecessary.

I'm not sure what's voodoo and what's not with the above steps. I also wonder whether I can specify a one-size-fits all solution for all of the Broadcom devices in the module unload/reload routine. I don't mind having *extraneous* steps in there, which help one user, but are extraneous for another, but I'm wondering whether each device potentially needs its own unload/reload routine. I'm not convinced that it makes any difference whether one installs ndiswrapper while ssb is disabled vs. while its enabled. But maybe that *is* what it takes for *some* users. We need some users to try it both ways, I think. (Proving it works one way and not the other.)

Unfortunately, I have a card for which the wiki *works*, so I can't do this testing...

---

### Post by Jamie Jackson on 2008-04-29
> **Damakin said:**
> I have tried using npallet's approach, and I have found out that whenever ssb/b43legacy is unloaded my wireless interface appears as "UNCLAIMED" under "lshw -C network" which is very strange, ndiswrapper should be loaded...

Let us know what ends up flipping the magic switch, and I'll let the thread know if I find anything out about cases related to yours.

---

### Post by Jamie Jackson on 2008-04-29
> **adamitj said:**
> ```
**sudo lshw -C network:**
PCI (sysfs) --> I needed to close it with CTRL+C, it stayed more than 10 minutes and does not show anything.
```

That's awfully strange. Do you see any problems in dmesg that would seem to indicate a problem in this area? (Note: I'm no expert with dmesg output.)

---

### Post by Jamie Jackson on 2008-04-29
> **hessianmatrix said:**
> This didn't work. But the command, modprobe b44 gave me back my wired network connection.

I'm not clear on what you're saying here. Could you clarify?

---

### Post by Jamie Jackson on 2008-04-29
> **kevdog said:**
> Yes all rc scripts are run as root.  Im an intermediate user also and figuring out some of this stuff for the first time.  I know enough when things are hacked together that work -- meaning its not the proper way of doing things -- however figuring out how to solve the problem once its identified is another level of understanding.

Just want to say that I'm no init script expert, so an rc.local workaround could very well be a hack. (In other words, I don't disagree with kevdog, here.) So, I'm waiting for someone to come through with something cleaner.

---

### Post by Jamie Jackson on 2008-04-29
> **abrigham said:**
> LOL yeah, I figured that out after I posted. When I pulled the XP drivers down again, it was version 5, and I realized it was the same file mentioned in step 2e :) I still haven't tried any of the other drivers from step 2. Also, I never really mentioned this before, but I work in Tech Support at Dell (just not on the Linux side LOL), so I'm going to ask around to some of my internal sources and will certainly share any insight I may receive.

Just wanted to make sure that you know that 95% of the BCM43** drivers call the file bcmwl5, and you won't know there's a difference between them until you diff them (or checksum, or whatever).

---

### Post by Jamie Jackson on 2008-04-29
> **marcw said:**
> Your how-to worked well for my Presario v5000 and a 4311 rev 01 with a fresh install of Hardy.  No compiling necessary.  Nice job!  (You might want to drop the "Feisty" from the title).

One thing though...  After a restart my NetworkManager will sit and spin while trying to connect to ...  somewhere?  It will eventually time out and a click of my network will get it connected within seconds.  Alternately, if I don't wait for the time out and simply interupt the spinning by connecting to my network, it will then also connect right away.  It seems to be just that first connection attempt after a restart that gives it problems.  I've deleted the entry in the nm-editor and created it from scratch but I get the same results.  Any suggections?

Wondering which version of nm-applet you got with Hardy: "dpkg -l network-manager-gnome"

Devs claim to have fixed an nm-editor bug as of network-manager-applet (0.6.6-0ubuntu3).

For reference, in Gutsy, I've got network-manager-gnome 0.6.5-0ubuntu11~7.10.0 (And Gutsy doesn't seem to have nm-editor, nor the literal package network-manager-applet.)

Here's the [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/204155"), FWIW.

---

### Post by abrigham on 2008-04-29
> **Jamie Jackson said:**
> Just wanted to make sure that you know that 95% of the BCM43** drivers call the file bcmwl5, and you won't know there's a difference between them until you diff them (or checksum, or whatever).

Yeah, I assumed that was the case, which is why I went ahead and tried both of the Dell drivers mentioned in the Wiki (steps 2d and 2e). Incidentally, the file in step 2e is the one that Dell provides for my laptop (Inspiron 1720) under WinXP, tho I'm not sure if WPA works under XP since I'm currently dual-booting Hardy and Vista. I also just re-did my Hardy install (I'd done so much trying to get the wireless working, I'd lost track, so wanted to start with a fresh load). I also found a bug report [here]("https://bugs.launchpad.net/ubuntu/+bug/197558") that relates. The last comment seems to wrap it up nicely and I'm going to try that, too, although that worked for a Rev 01 card and mine is a Rev 03, but its worth a shot. I'll post my results here...

---

### Post by jimjackson on 2008-04-29
Hello Jamie,

Great Job!! Thank-You much for your posts. Here is the info on my machine:

Machine Brand and Model
Compaq Presario Model c302nr / c300

Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Wireless Chipset: lspci -n | grep '14e4:43'
06:00.0 0280: 14e4:4311 (rev 01)

Ubuntu Version: lsb_release -d
Description:	Ubuntu 8.04

Kernel / Architecture: uname -mr
2.6.24-16-generic i686

Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
None

Whether or not you had to compile NDISWrapper
No

Which version of Step 2 you used
2a

If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
I had to apply the "Hardy Bug Fix"

I do thank all the folks who were and are instrumental in making this software possible. I switched from XP on a full time basis for my personal laptop. It runs nice and smooth and things just work! That is such a wonderful thing. I really like the work that has been done.

Respectfully,
Jim

---

### Post by Jamie Jackson on 2008-04-29
> **abrigham said:**
> Yeah, I assumed that was the case, which is why I went ahead and tried both of the Dell drivers mentioned in the Wiki (steps 2d and 2e). Incidentally, the file in step 2e is the one that Dell provides for my laptop (Inspiron 1720) under WinXP, tho I'm not sure if WPA works under XP since I'm currently dual-booting Hardy and Vista. I also just re-did my Hardy install (I'd done so much trying to get the wireless working, I'd lost track, so wanted to start with a fresh load). I also found a bug report [here]("https://bugs.launchpad.net/ubuntu/+bug/197558") that relates. The last comment seems to wrap it up nicely and I'm going to try that, too, although that worked for a Rev 01 card and mine is a Rev 03, but its worth a shot. I'll post my results here...

> _[dtx  wrote on 2008-04-25:]("https://bugs.launchpad.net/ubuntu/+bug/197558/comments/42")_


I can confirm that adding
install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd

to

/etc/modprobe.d/ndiswrapper

and then following these directions:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Worked for me! I have wifi (with WPA) and USB after reboot.

lspci
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)


I like the idea of modifying /etc/modprobe.d/ndiswrapper to overcome the ssb bug. (Seems like a more natural place for it, anyway.)

However, can anyone explain this arcane line piece-by-piece?
```

install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd
```

Update: Reading through some good info [here]("http://linux.die.net/man/5/modprobe.d").

Update2: #debian on freenode:
[LIST]
 [*]jamiejackson: i looked at a modprobe.d explanation page, but i can't completely figure out what this line would do in /etc/modprobe.d/ndiswrapper: "install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd"
 [*]jamiejackson: First segment: does it mean that ohci_hcd & ssb are removed from the kernel whenever ndiswrapper is added?
 [*]blubberdiblub: jamiejackson: yes, it looks like it unloads ohci_hcd and ssb modules, then loads the ndiswrapper module (while preventing going through the config file again, so it doesn't recurse indefinitely), and then reinserts the ohci_hcd module.
 [*]jamiejackson: oohhhhhh, blubberdiblub, that quick explanation clears everything up, i think
 [*]jamiejackson: oh, one more thing, i've never done it, i don't think, but when ndiswrapper is installed to the kernel, there can be some config options, so the second segement includes those for you?
 [*]blubberdiblub: jamiejackson: yes, it looks like it will carry over the command line options you gave to modprobe ndiswrapper (or in a config file in /etc/modprobe.d/ )
 [*]jamiejackson: brilliant, i'm all sorted, thanks!!
[/LIST]

In summary the line says:
If you modprobe ndiswrapper (i.e., if you add ndiswrapper to the kernel):
[LIST=1]
[*]uninstall ohci_hcd and ssb
[*]run the modprobe command that you (or the machine) specified in the first place
[*]reinstall ohci_hcd
[/LIST]

But what becomes of ssb after this? I don't see how ssb gets reloaded, and ssb is some requirement for USB, isn't it? Won't this kill USB?

Update 3: Might this be better?```

install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd; modprobe ssb;
```

(However, I don't know what ohci_hcd is, or how it relates to ssb/ndiswrapper. I don't even see that in my lsmod, though I do see **u**hci_hcd.)

---

### Post by kevdog on 2008-04-30
This could seriously be the smoothest fix someone has suggested:

```
install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci_hcd; modprobe ssb;
```

I love this solution.  I found the documentation for the command here in case people are wondering:
[http://linux.die.net/man/5/modprobe.conf](http://linux.die.net/man/5/modprobe.conf)

Again I'm really unclear what modules must be removed and then reloaded.  Again the order in which the modules are loaded are critical, since ssb must be inserted after ndiswrapper.

I took my hand at writing a startup script (not the sloppy rc.local approach, however I don't think its needed now)  This module checks to see if ssb and the mysterious ohci_hcd are loaded inside the kernel -- if loaded, it removes the modules, inserts ndiswrapper, and then reinserts them (if they were loaded in the first place):

(NOTE - I included a restart option in case the modules somehow needed to be reloaded after hibernation or any such behavior in which you might need to reload the modules -- Strange things have happened in the past -- would reload modules with
sudo /etc/init.d/wireless-broadcom-ndiswrapper restart


```
gksu gedit /etc/init.d/wireless-broadcom-ndiswrapper &

#!/bin/bash

#wireless-broadcom-ndiswrapper - This script takes care of loading ndiswrapper
#with broadcom chipsets to avoid the associated b44/ssb bug

case "$1" in
start)
# Unload conflicting modules
echo "Unloading conflicting broadcom/ndiswrapper conflicting modules.."
modules=`lsmod`
echo $modules | grep -q ohci_hcd && rmmod ohci_hcd
echo $modules | grep -q ssb && rmmod ssb
echo $modules | grep -q ndiswrapper && rmmod ndiswrapper

echo "Loading ndiswrapper/Broadcom modules.."
modprobe ndiswrapper
echo $modules | grep -q ohci_hcd && modprobe ohci_hcd
echo $modules | grep -q ssb && modprobe ssb
;;
stop)
# I dont believe there is anything to do here.

;;
restart)
# $0 stop
$0 start
;;
*)
echo "Usage: wireless-broadcom-ndiswrapper {start|stop|restart}"
exit 1
esac

exit 0

Make file executable
cd /etc/init.d && sudo chmod 755 wireless-broadcom-ndiswrapper

Add the script to the rc levels
#To the best of my knowledge networking scripts are completed at runlevel 40
#Default is runlevel 20
#I need this script to be run after the wired/wireless modules have loaded in order
#to reload the ndiswrapper kernel module prior to the ssb module
#Unclear if script needs to be run in runlevel =1

sudo update-rc.d wireless-broadcom-ndiswrapper start 50 2 3 4 5 .
```

Ive also seen this approach in the launchpad section -- its by far the easiest if however have no idea if it works:

```

I make ndiswrapper works with a broadcom wirelles board with a following procedure on a clean install of hardy

First, install the packages ndis and ndiswrapper-utils-1.9

Second, install driver from broadcom using

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l

you should see a message that says driver present, hardware detected

THE RELEVANT PART: Install aliases on /etc/modprobe.d

sudo ndiswrapper -ma

AGAIN, It's "-ma", NOT "-m". Finally add ndiswrapper to /etc/modules

```

---

### Post by abrigham on 2008-04-30
> But what becomes of ssb after this? I don't see how ssb gets reloaded, and ssb is some requirement for USB, isn't it? Won't this kill USB?

So, from what I read on that bug report, some people at least initially were blacklisting ssb, which as you suspected would kill USB - that's where they came to the conclusion to use the command I referenced and you posted. also according to the comments on that bug report, ssb is used by ohci_hcd so when reloading ohci_hcd, the ssb module gets reloaded automatically as a dependant... at least that's according to what I've read.

> (However, I don't know what ohci_hcd is, or how it relates to ssb/ndiswrapper. I don't even see that in my lsmod, though I do see uhci_hcd.)

ohci and uhci are both types of USB controllers, which explains why when some people were blacklisting ssb (and thereby preventing the ohci_hci module from loading) they were killing USB.

---

### Post by kilrizzy on 2008-04-30
I dont know what I am missing. I am so close!!! My driver is a .exe so when I try to use ndiswrapper it says I need an .inf so I use cabextract but says it cannot extract a binary file. Noone else seems to have problems with .exe's I am so lost! Thanks for any help

---

### Post by abrigham on 2008-04-30
Alright... tried the adding the line suggested from the bug report to /etc/modprobe.d/ndiswrapper but it was no joy. Like you, Jamie, I didn't have the ochi_hcd module, only the uhci_hcd, which does NOT depend on ssb (verified with modinfo). So, I changed the line to read:
```
install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44
```
Notice, I replaced ochi_hcd with b44, which DOES rely on ssb. Still no joy. Everything remains the same. I can connect to open and WEP-enabled networks, but not WPA Personal. I'm honestly not sure if the ssb module is the cause, since even when I completely unload the b44/ssb combo and leave it unloaded I still cannot connect to any WPA Personal network.

---

### Post by adamitj on 2008-04-30
> **kevdog said:**
> Yes all rc scripts are run as root.  Im an intermediate user also and figuring out some of this stuff for the first time.  I know enough when things are hacked together that work -- meaning its not the proper way of doing things -- however figuring out how to solve the problem once its identified is another level of understanding.

Returning to this post, I solve the problem, so I don't need to manually start the wireless card. This is what I found:

Originally, I used this script at /etc/rc.local:
```
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

exit 0
```

But at the first line, it returns an error because b44 module aren't available. So all subsequent lines are disabled, it stops on the first error found.

Then I put all the code above into a regular file called /etc/wireless-activate.sh. At /etc/rc.local, I writed:

```
sh /etc/wireless-activate.sh
exit 0
```

And it was enough. Everything is work fine now.

---

### Post by Jamie Jackson on 2008-04-30
> **kilrizzy said:**
> I dont know what I am missing. I am so close!!! My driver is a .exe so when I try to use ndiswrapper it says I need an .inf so I use cabextract but says it cannot extract a binary file. Noone else seems to have problems with .exe's I am so lost! Thanks for any help

Any reason you're not using one of the drivers from the wiki? Also, which chipset do you have? "lspci -n | grep '14e4:43'"

Where's the URL from which you're downloading the exe?

---

### Post by joemirando on 2008-04-30
> **joemirando said:**
> 
Here is my info:

[LIST]
[*]Dell Inspiron 5100
[*]02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
[*]02:02.0 0280: 14e4:4320 (rev 02)
[*]Ubuntu 8.04
[*]2.6.24-16-generic i686
[*]No user-added extra boot options
[*]I used Step 2f with the driver downloaded from the provided link
[*]ndiswrapper 1.50 package from distro
[*]"Hardy Bug Fix" workaround used
[/LIST]


I just noticed that applying this fix seems to have wiped out eth0 in the network manager. 

lshw -C network gives me (I'm only encluding the eth0 info):

 [INDENT]
*-network:0 UNCLAIMED
       description: Ethernet controller
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
[/INDENT]

Can someone please point me in the right direction (I'm a long-time noob) to get eth0 funtionality back?


Any and all help would be appreciated,

Joe Mirando

---

### Post by abrigham on 2008-04-30
@joemirando: double check what you changed for the Hardy Bug Fix workaround. Make sure you're reloading the b44 module as this is used by your onboard Broadcom 440x NIC.

---

### Post by joemirando on 2008-04-30
> **abrigham said:**
> @joemirando: double check what you changed for the Hardy Bug Fix workaround. Make sure you're reloading the b44 module as this is used by your onboard Broadcom 440x NIC.

Ahhh... boy, do I feel dumb. That's exactly what it was. I forgot about adding the b44 module afterwards.


Thanks a bunch for your help!

Joe Mirando

---

### Post by kilrizzy on 2008-04-30
> **Jamie Jackson said:**
> Any reason you're not using one of the drivers from the wiki? Also, which chipset do you have? "lspci -n | grep '14e4:43'"

Where's the URL from which you're downloading the exe?


I was hoping to be able to install the driver for my sprint broadband evdo also but right now anything would do so I was on dells website to get my drivers. 

I ran that code and got - 0b:00.0 0280: 14e4:4312 (rev 01)

thank you!

---

### Post by kilrizzy on 2008-04-30
Tried extracting the exe's in windows and it just extracted another setup.exe. ugh

---

### Post by kilrizzy on 2008-04-30
Just tried with the listed driver - R129083.EXE cant run ndis because it needs to be .inf and when I use cabextract it says no valid cabs found

---

### Post by abrigham on 2008-04-30
> **kilrizzy said:**
> Just tried with the listed driver - R129083.EXE cant run ndis because it needs to be .inf and when I use cabextract it says no valid cabs found
Dell driver files are self-extracting zip files. cabextract will not work, however unzip (or archive manager) will allow you to extract the files. In the extracted files should be a DRIVER or DRIVER_US directory that will have the .inf file you need for ndiswrapper.

---

### Post by Jamie Jackson on 2008-04-30
> **kilrizzy said:**
> I was hoping to be able to install the driver for my sprint broadband evdo also but right now anything would do so I was on dells website to get my drivers. 

I ran that code and got - 0b:00.0 0280: 14e4:4312 (rev 01)

thank you!

Why not just follow step 2b, then? Have you tried that, and it didn't work, or did you miss the step 2 instructions?

---

### Post by Jamie Jackson on 2008-04-30
> **abrigham said:**
> @joemirando: double check what you changed for the Hardy Bug Fix workaround. Make sure you're reloading the b44 module as this is used by your onboard Broadcom 440x NIC.

Should I add "modprobe b44" to the wiki then? The main question is: Is it harmless for even non-b44 device owners to modprobe b44 at the end?

I'd hate to have all these hairy conditionals in the wiki (step 2 variations are a necessary evil, however). I'm after the most universal solution possible, and if one procedure (even if it's got some innocuous "fluff" for some users--uggh) can suit everyone, that's the approach I'd like to figure out.

Of course, if a universal approach isn't feasible, then of course we'll need to get fancy, and maybe create some kind of module detecting, /etc/modules.d/ndiswrapper-configuring script. ](*,)

---

### Post by kilrizzy on 2008-04-30
Finally got the driver installed and finished those last steps, but nothing new, my wireless network is still not showing up. I noticed in my hardware drivers menu the broadcom driver enabled box is not checked, but when I check it it says to restart but after I do it is still unchecked

---

### Post by Jamie Jackson on 2008-04-30
> **kilrizzy said:**
> Finally got the driver installed and finished those last steps, but nothing new, my wireless network is still not showing up. I noticed in my hardware drivers menu the broadcom driver enabled box is not checked, but when I check it it says to restart but after I do it is still unchecked

Check out three posts up, and post back?

Update: Oh, and please show the output of "lsmod"

---

### Post by kilrizzy on 2008-04-30
> **Jamie Jackson said:**
> Check out three posts up, and post back?

Update: Oh, and please show the output of "lsmod"

```
Module                  Size  Used by
ipv6                  311720  10 
af_packet              27272  2 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
rfkill_input            6528  0 
ppdev                  11400  0 
powernow_k8            16608  1 
cpufreq_powersave       3200  0 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_conservative    10632  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
dock                   12960  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
sbp2                   27272  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
joydev                 15488  0 
snd_hda_intel         440408  3 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
dcdbas                 11312  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                    3456  2 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               9092  0 
sdhci                  21508  0 
ecb                     5248  2 
blkcipher               9476  1 ecb
evdev                  14976  17 
psmouse                46236  0 
uvcvideo               62084  0 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mmc_core               59272  1 sdhci
compat_ioctl32         11136  1 uvcvideo
b43                   126760  0 
videodev               30720  1 uvcvideo
pcspkr                  4992  0 
soundcore              10400  1 snd
k8temp                  7680  0 
v4l1_compat            15492  2 uvcvideo,videodev
rfkill                 10128  12 rfkill_input,b43
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
mac80211              192532  1 b43
cfg80211               17680  1 mac80211
led_class               7176  1 b43
input_polldev           6928  1 b43
i2c_piix4              11148  0 
i2c_core               28544  1 i2c_piix4
ndiswrapper           243872  0 
video                  23444  0 
output                  5632  1 video
wmi_acer               11076  0 
button                 10912  0 
battery                16776  0 
ac                      8328  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
loop                   21508  2 
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
atiixp                  6672  0 [permanent]
ide_core              136600  1 atiixp
pata_acpi               9856  0 
ata_generic             9988  0 
sg                     41880  0 
sd_mod                 33280  2 
b44                    33168  0 
ehci_hcd               41996  0 
pata_atiixp            10496  0 
ohci1394               36532  0 
ahci                   33028  1 
ssb                    37252  2 b43,b44
ohci_hcd               27524  0 
mii                     7552  1 b44
ieee1394              106968  2 sbp2,ohci1394
libata                176304  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              178488  5 sbp2,sr_mod,sg,sd_mod,libata
usbcore               169904  5 uvcvideo,ndiswrapper,ehci_hcd,ohci_hcd
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  5 

```

After it was doing this with the method I first used I deleted it and used the step two method with still no luck. I am very new to this so if you notice something in this it would be awesome. Thanks again!

---

### Post by Jamie Jackson on 2008-05-01
> **kilrizzy said:**
> After it was doing this with the method I first used I deleted it and used the step two method with still no luck. I am very new to this so if you notice something in this it would be awesome. Thanks again!

Well, I don't have much new to tell you, but I *can* tell you that b44 needs to be part of your reload process, so your custom reload would look like this. (You don't have, and don't need to remove, b43legacy, but your wired NIC likely uses b44, so here it is with both things taken into consideration.)

Try this one more time on the command line, just for kicks:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```

---

### Post by kilrizzy on 2008-05-01
> **Jamie Jackson said:**
> Well, I don't have much new to tell you, but I *can* tell you that b44 needs to be part of your reload process, so your custom reload would look like this. (You don't have, and don't need to remove, b43legacy, but your wired NIC likely uses b44, so here it is with both things taken into consideration.)

Try this one more time on the command line, just for kicks:
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```
Dont know why now but that did the trick! Its working perfectly!!! Could also be that I just updated to hardy from fawn?

Now I know this is pushing it but does anyone know if its possible to use a sprint broadband evdo card?

---

### Post by kevdog on 2008-05-01
If you dont have a wired broadcom nic - I highly doubt that you need the b44 driver.  Also for some crazy reason if you don't have a USB port, you don't need ssb.  I understand the quandry you are in with trying to make a general guide.  Whether or not however to add the b44 module is going to really depend on the individual's computer hardware.  I guess adding another active module into the kernel wouldn't help, but it goes against the minimalist theory.  Why add and load kernel modules you don't need?  There are probably some memory (RAM) ramifications!

---

### Post by omnibot on 2008-05-01
[LIST]
[*]Machine Brand and Model: Compaq Presarcio C700
[*]Wireless Brand and Model (please post the whole line):Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
[*]Wireless Chipset: 14e4:4311 (rev 02)
[*]Ubuntu Version: the command wasn't working but it's Hardy Heron, latest release
[*]Kernel / Architecture: [COLOR=DarkRed][FONT=Courier New] [/FONT][/COLOR]14e4:4311 (rev 02)
[*]Any *extra* boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper:no
[*]Which version of Step 2 you used: 2a
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not Yes
[/LIST]

So, my machine has finally got the wireless card working and I can see my network in the manager, but it's not connecting (and trust me I have the passphrase right)


**edit. i can connect to unsecure networks but not my own, so it's a problem with WPA?

---

### Post by deviant on 2008-05-02
Ok, there is something wrong with you how-to :(
I tried on 7.10 and 8.04, steps 2a and 2b, also tried with ndiswrapper compiled from sources. None of that worked for me. You can check [**here**](http://ubuntuforums.org/showthread.php?t=766560&page=5) the problems I encountered.
Today I followed [**this**](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper+bcm) how-to and everything worked as a charm.
Here are my system specs:

Dell Inspiron 6400 
```
itch@Sisif:~$ lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

```
itch@Sisif:~$ lspci -n | grep '14e4:43'
0b:00.0 0280: 14e4:4311 (rev 01)
```

```
itch@Sisif:~$ lsb_release -d
Description:    Ubuntu 7.10
```

```
itch@Sisif:~$ uname -mr
2.6.22-14-generic i686
```

I am not using any extra boot options (e.g., noacpi, irqpoll, etc.), I tried with ndiswrapper from reppos and compiled from sources, I tried both on Ubuntu 7.10 and 8.04, and also tried with "Hardy Bug Fix" (rc.local, modifying /etc/modprobe.d/ndiswrapper).

Maybe you could "merge" the 2 how-to`s or something like that, because you obviously worked hard on your how-to and is it very well written and explained and it is a shame that it does not work for everyone.

---

### Post by Aemer on 2008-05-02
Concerning the 4328, I wrote this to the guy that was having trouble with WPA:

"
I thought you should know that I'm posting this using a 4328 wireless card on an hp tx2020eo on my own little WPA secured wireless network.

I don't need to use WPA anywhere else so I cannot verify if there's something special going on with my ASUS hub, but as far as I know it's fairly standard.

I followed the bcm43xx guide on here to the letter, on a fresh install of hardy heron ubuntu. I used wubi for the install; I must admit, I'm no linux geek, and I have yet to reboot the machine after the install was successfully completed, but so far everything seems fine.
 
I installed Ndiswrapper, prior to following the guide, using synaptic (there was another guide that said to install ndiswrapper-common, ndiswrapper-utils-1.9, and cabextract, so that's what I'd done just prior to following this one), and I did some commands to get the sound to work prior to that, but other than that, absolutely everything is set up exactly as the installation did it.

It's running 64 bit too =]

So, it seems either you have a faulty card somehow, or theres a device conflict somewhere - more than likely it's the latter.
"

Hope that helps anybody in the same boat as him..

(And thanks for the guide!)

---

### Post by marcw on 2008-05-02
> **deviant said:**
> Ok, there is something wrong with you how-to :(
I tried on 7.10 and 8.04, steps 2a and 2b, also tried with ndiswrapper compiled from sources. None of that worked for me. You can check [**here**](http://ubuntuforums.org/showthread.php?t=766560&page=5) the problems I encountered.
Today I followed [**this**](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper+bcm) how-to and everything worked as a charm.

I think you might be making the classic mistake of thinking what works for you must work for all and whatever doesn't work for you must be flawed.  Did you notice the poll in the thread that worked for you?  Over 21% of the poll respondents said that it did not work absolutely correctly for them.  Also, if you'll read this entire thread the method outlined here *did* work me and many others.

---

### Post by Jamie Jackson on 2008-05-02
> **deviant said:**
> Ok, there is something wrong with you how-to :(
I tried on 7.10 and 8.04, steps 2a and 2b, also tried with ndiswrapper compiled from sources. None of that worked for me. You can check [**here**](http://ubuntuforums.org/showthread.php?t=766560&page=5) the problems I encountered.
Today I followed [**this**](http://ubuntuforums.org/showthread.php?t=297092&highlight=ndiswrapper+bcm) how-to and everything worked as a charm.
Here are my system specs:

Maybe you could "merge" the 2 how-to`s or something like that, because you obviously worked hard on your how-to and is it very well written and explained and it is a shame that it does not work for everyone.

I'm not spotting the substantive differences between the two methods. Are you saying you actually used the driver that was specified on that howto? If so, then *that's* the difference. That driver corresponds to my 2d driver.

I'd appreciate if you can call out which parts were different for you between the two.

---

### Post by Jamie Jackson on 2008-05-02
> **marcw said:**
> I think you might be making the classic mistake of thinking what works for you must work for all and whatever doesn't work for you must be flawed.  Did you notice the poll in the thread that worked for you?  Over 21% of the poll respondents said that it did not work absolutely correctly for them.  Also, if you'll read this entire thread the method outlined here *did* work me and many others.

A lot of that 21% failure rate is due to the early days of the howto, before the kinks were worked out. By the time of Gutsy, I think the success rate was not quite, but pretty close to 100%

HOWEVER, with Hardy, I'm making no promises. I have not found the silver bullet that will fix things for all users. In fact, it seems more and more probable that because of this silly ssb thing in Hardy, that there might potentially need to be a fork for each of the devices.

One approach that I have in my head is to get Hardy users with fresh installs to report the following:
[LIST]
[*]lshw -C network
[*]lspci -n | grep '14e4:43'
[*]lsmod
[/LIST]

Then, we could come up with custom ssb-disabling modprobe sequences, and after we've got a sample of those for each device, we could refactor to find out what forks are necessary. However, that begs the question that a given device has the same modprobe requirements on all machines.

Frustrating...

---

### Post by kutjara on 2008-05-02
> **Aemer said:**
> Concerning the 4328, I wrote this to the guy that was having trouble with WPA:

"
I thought you should know that I'm posting this using a 4328 wireless card on an hp tx2020eo on my own little WPA secured wireless network.

I don't need to use WPA anywhere else so I cannot verify if there's something special going on with my ASUS hub, but as far as I know it's fairly standard.

I followed the bcm43xx guide on here to the letter, on a fresh install of hardy heron ubuntu. I used wubi for the install; I must admit, I'm no linux geek, and I have yet to reboot the machine after the install was successfully completed, but so far everything seems fine.
 
I installed Ndiswrapper, prior to following the guide, using synaptic (there was another guide that said to install ndiswrapper-common, ndiswrapper-utils-1.9, and cabextract, so that's what I'd done just prior to following this one), and I did some commands to get the sound to work prior to that, but other than that, absolutely everything is set up exactly as the installation did it.

It's running 64 bit too =]

So, it seems either you have a faulty card somehow, or theres a device conflict somewhere - more than likely it's the latter.
"

Hope that helps anybody in the same boat as him..

(And thanks for the guide!)

I replied to your PM, Aemer, but thanks again for the info. Just for the sake of completeness, let me summarize here what I said to you, so anyone having a similar problem can benefit.

I think my problem is specifically related to my particular 4328 card and Linksys WRT600N router. I've subsequently logged onto a neighbor's WPA-enabled network (with his permission, I hasten to add), and it worked fine.

So the card works with other routers using WPA, and the router works with other cards using WPA, but the card and the router won't work with each other using WPA. All I can think of is that either my card or my router, or both, was/were manufactured very near to the limit of acceptable tolerance. They work fine with other, less "on the edge" equipment, but fall outside each other's margins of error.

That's complete gibberish, of course, but I'm way past grasping at straws on this one. Fortunately, the Belkin USB card I slapped in after giving up on the 4328 works fine, or I'd probably still be messing around with this.

---

### Post by marcw on 2008-05-02
> **Jamie Jackson said:**
> A lot of that 21% failure rate is due to the early days of the howto, before the kinks were worked out. By the time of Gutsy, I think the success rate was not quite, but pretty close to 100%


ummm...  You do know I was replying to Deviant and referring to Deviant's quoted poll and not your poll, right?  It sounds like you think I was talking about your poll.

---

### Post by Jamie Jackson on 2008-05-03
> **marcw said:**
> ummm...  You do know I was replying to Deviant and referring to Deviant's quoted poll and not your poll, right?  It sounds like you think I was talking about your poll.

Oh, I see what you were saying. The stats seem similar, though.

---

### Post by hessianmatrix on 2008-05-03
> **Jamie Jackson said:**
> I'm not clear on what you're saying here. Could you clarify?

Somewhere in the chain of my replies I said that I lost my wired connection to with those sudo rmmode set of commands. I had to use my XO (OLPC) to read the forums and reply to this thread. Invoking sudo modprobe b44 activated the wired network.

---

### Post by monolisp on 2008-05-04
Your tutorial rocks. I had wireless working with Ubuntu 7.10 and then upgraded to 8.04 Hardy Heron and it stopped working. 

I had used your tutorial before to get it working in 7.10 and your Hardy workaround worked first time!! Love it.

I have a HP Pavilion dv2415nr with Broadcom - used step 2a (rev 02) laptop

The only necessary change after upgrade to Hardy was the changeover from module = ssb to module = ndiswrapper.

Thanks again!!

now if only I could get my sound card to sound less like my clock radio...!

---

### Post by ryanwhit on 2008-05-04
> **Jamie Jackson said:**
> Thanks for the info. Actually, earlier today, I did mention this sort of caveat in the wiki where it addresses specific chipsets: "In Gutsy, lspci shows "Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)" NOTE: There has only been one person who has tried this card with this howto. He tried it with Hardy, and it worked for the most part; HOWEVER, even after a lot of work troubleshooting, he was unable to get WPA working. Check out this post [link to your post] and his subsequent ones."

I'll add the 64 bit variable in there as well.
I managed to get WPA-PSK my BCM4328 (rev 03) working on my 64 bit Hardy by following your tutorial exactly using step 2d (thanks a bunch btw!!!) I am using that connection to post this right now. I am somewhat new to Linux, but I'd like to help out with this problem in any way that I can. Here is some of my info. Let me know if there is anything else you would like from me or if you want me to test some things out that might be beneficial to others. 

Dell Inspiron 1420

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

0c:00.0 0280: 14e4:4328 (rev 03)

Description:	Ubuntu 8.04

2.6.24-16-generic x86_64

No extra boot options

Did NOT have to compile NDISWrapper

Step 2d

Did NOT have to apply "Hardy Bug Fix" workaround

Hope I can be of some help. Thanks again!:-)

P.S. My connection is saying 53% power and the Connection Information in Network Manager is claiming 130 Mb/s!!! It's running really fast :-)

---

### Post by ThePenguinKnight on 2008-05-05
Howdy fellas. I played around with SUSE and Fedora 6-7 years ago, and since then have been stuck in windows. As such, I consider myself a complete noob to Linux, not really having any clue about anything. Keep that in mind ;)

Forgive me ahead of time for the massive post. This is frustrating me and I needed some help from someone I suspect knows what they're talking about, and I figure whoever is interested could use as much info as possible.

I bought meself a laptop (Dell Inspiron 1520, new from factory) last year and have just loaded Ubuntu 8.4 (Hardy Heron) on it for a dual-boot with WinXP Pro. Everything I've tested so far is working out of the box, except for my Broadcom 4328 Wireless card. Hardy recognizes that it's there (using System>Hardware Testing), but it is not active.

I've reviewed a large number of "fixes" for the issue, most of which are very similar (ndiswrapper, use the R11517.EXE driver files, modprobe, etc.), and each one would hang up at the same point, the "sudo modprobe ndiswrapper" input. It spits out the following:
> tim@Pheonix:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

From my readings, I've gathered that this error spits out due to Hardy trying to use the wrong module (ssb instead of ndiswrapper?), and the Hardy workaround mentioned at the linked wiki (first post here, the one I'm using) is meant to instruct Hardy to use ndiswrapper without disabling anything from ssb. Correct or clarify as necessary, please; I like to learn about this stuff :D

Here's the "lshw -C network" output:
> tim@Pheonix:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:96:44:92
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.78 latency=64 module=ssb multicast=yes


This was the output both before and AFTER I had tried the temporary and the workaround. 

Here's my try at the temporary:
> tim@Pheonix:~/bcm43xx$ sudo rmmod b43
[sudo] password for tim: 
ERROR: Module b43 does not exist in /proc/modules
tim@Pheonix:~/bcm43xx$ sudo rmmod b44
tim@Pheonix:~/bcm43xx$ sudo rmmod b43legacy #this step added Apr 27 2008
ERROR: Module b43legacy does not exist in /proc/modules
tim@Pheonix:~/bcm43xx$ sudo rmmod ssb
tim@Pheonix:~/bcm43xx$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
tim@Pheonix:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
tim@Pheonix:~/bcm43xx$ sudo modprobe ssb
tim@Pheonix:~/bcm43xx$ sudo modprobe b44
tim@Pheonix:~/bcm43xx$ 


And the workaround:
> tim@Pheonix:~/bcm43xx$ echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Mon May 5 12:26:53 CDT 2008 
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
tim@Pheonix:~/bcm43xx$ 


It still lists it "module=ssb" (using "lshw -C network").

I'm having a more experienced buddy f mine take a look at it later today, but hopefully someone can use this info to help out. If not me, someone else.

---

### Post by bjohansen on 2008-05-05
I've followed this guide, using step 2a.

Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
logging in as anonymous ... logged in!
==> SYST ... done   ==> PWD ... done.
==> TYPE I ... done. ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... and here it stops.. whats wrong?

---

### Post by platukem on 2008-05-06
Thanks. It works well for me.

My computer specifications are

    * Compaq presario b1227tu
    * 10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
    * Wireless Chipset: 10:00.0 0280: 14e4:4311 (rev 02)
    * Ubuntu Version: Ubuntu 8.04
    * Kernel / Architecture: 2.6.24-16-generic i686
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.): none
    * Whether or not you had to compile NDISWrapper: no
    * Which version of Step 2 you used: 2a
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not: version 0.3 is ok.

---

### Post by platukem on 2008-05-06
> **bjohansen said:**
> I've followed this guide, using step 2a.

Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
logging in as anonymous ... logged in!
==> SYST ... done   ==> PWD ... done.
==> TYPE I ... done. ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... and here it stops.. whats wrong?

Put this link instead the old one
[ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)

Hope you come back and see this answer :-)

---

### Post by Jamie Jackson on 2008-05-06
> **ryanwhit said:**
> I managed to get WPA-PSK my BCM4328 (rev 03) working on my 64 bit Hardy by following your tutorial exactly using step 2d (thanks a bunch btw!!!) I am using that connection to post this right now. I am somewhat new to Linux, but I'd like to help out with this problem in any way that I can. Here is some of my info. Let me know if there is anything else you would like from me or if you want me to test some things out that might be beneficial to others. 

Dell Inspiron 1420

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

0c:00.0 0280: 14e4:4328 (rev 03)

Description:	Ubuntu 8.04

2.6.24-16-generic x86_64

No extra boot options

Did NOT have to compile NDISWrapper

Step 2d

Did NOT have to apply "Hardy Bug Fix" workaround

Hope I can be of some help. Thanks again!:-)

P.S. My connection is saying 53% power and the Connection Information in Network Manager is claiming 130 Mb/s!!! It's running really fast :-)

Thanks for all the details. The only other thing you could provide is the output of "lsmod".

---

### Post by Jamie Jackson on 2008-05-06
> **ThePenguinKnight said:**
> ...

Tell us the output of:
```

ndiswrapper -v
# then get in the directory that has the bcmwl5.inf file
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l

```

---

### Post by Jamie Jackson on 2008-05-06
> **bjohansen said:**
> I've followed this guide, using step 2a.

Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
logging in as anonymous ... logged in!
==> SYST ... done   ==> PWD ... done.
==> TYPE I ... done. ==> CWD /pub/softpaq/sp34001-34500 ... done.
==> PASV ... and here it stops.. whats wrong?

It's probably because these giant companies have some seriously flaky servers. At this step, I list an alternate (HP) wget URL for when one or the other flakes out... there's a note about it just above that block of commands. Try that, and let us know how it goes.

UPDATE: Whoops, platukem beat me to the punch. :)

---

### Post by ouwe_man on 2008-05-07
Thanks a lot for this.....

IBM X22 Thinkpad with 640 ram, 20 Gb harddisk. 800Mhz PII, LINKSYS PCMIA CARD

john@Thinkpad:~$ lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

john@Thinkpad:~$ lspci -n | grep '14e4:43'
john@Thinkpad:~$ lsb_release -d
Description:	Ubuntu 8.04
john@Thinkpad:~$ uname -mr
2.6.24-17-generic i686
john@Thinkpad:~$ 

Used 2f for correction and followed your instructions to the point with a cut and paste method. I had a connection on the 7.09 but on 8.04 fresh install via alternate CD I was lost. Tried a Debian distro fresh install but nothing either. Back to the 8.04 fresh install and I got a message somehow saying that I had new hard (soft?) ware to be installed. When I pushed the OK button a lot of things happened but at the end there was a failed notice. Funny thing is, I had connection but could not configure in the networks tool. I decided after a lot of research to do it the ndiswrapper way with your method.

As they say: it worked out of the box!

This is fantastic!

Thanks

John

---

### Post by ouwe_man on 2008-05-07
The above comments show once again that you should never cry victory before the war is won....

I was sur that finally every thing worked: I disconnected my linksys card and lo and behold: the mouse froze and only the power off button could take me back to a new power on off the system....

Once logged in I reinstalled my linksys card and had my little 2-screen icon with manual config....

I applied one of the suggested remedies:

john@Thinkpad:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:ca:8f:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:10:ed:f5:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11g
john@Thinkpad:~$ sudo lshw -C network
[sudo] password for john: 
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:ca:8f:fd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:10:ed:f5:cf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=IEEE 802.11g
john@Thinkpad:~$ sudo rmmod b43
john@Thinkpad:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
john@Thinkpad:~$ sudo rmmod b43legacy
ERROR: Module b43legacy does not exist in /proc/modules
john@Thinkpad:~$ sudo rmmod ssb
john@Thinkpad:~$ sudo rmmod ndiswrapper
john@Thinkpad:~$ sudo modprobe ndiswrapper
john@Thinkpad:~$ sudo modprobe ssb
john@Thinkpad:~$ sudo modprobe b44
john@Thinkpad:~$ sudo lshw -C network
  *-network               
       description: 802.11b CardBus
       vendor: Broadcom
       physical id: 0
       version: 8.0
       slot: Socket 0
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:d0:59:ca:8f:fd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:13:10:ed:f5:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+The Linksys Group, Inc.,07/ ip=192.168.1.103 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
john@Thinkpad:~$ 

This again froze the mouse and again a powerbutton off. 

Starting the system again let me use the wifi but with a manual config and nu info on any wifi signals (there are thee total around my house)

So far so good, How now, pussycat?

thanks

John

---

### Post by kevdog on 2008-05-08
Try the same process again, but DO NOT reload these modules:

john@Thinkpad:~$ sudo modprobe ssb
john@Thinkpad:~$ sudo modprobe b44

Just skip this step -- you definitely dont need the b44 module since your wired NIC is not a broadcom, and ssb -- skip it for now.

---

### Post by DaleVandy on 2008-05-08
I am a newbie to Ubuntu. I started with Gutsy and got the card to work finally. But when I upgraded to Hardy I lost what I had gained.  I have been looking and trying things on and off for over a week. I finally came upon this article and tried it. Here are my results and statistics that you wanted:

    * Machine Brand and Model: Acer Aspire 3680
    * Wireless Brand and Model (please post the whole line): 03:00.0 Network Controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
    * Wireless Chipset: 14e4:4311 (rev 01)
    * Ubuntu Version: Ubuntu 8.04
    * Kernel / Architecture: 2.6.24-16generic i686
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)None as far as I know
    * Whether or not you had to compile NDISWrapper: No
    * Which version of Step 2 you used: 2a
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not: Yes


First, I hate to say this (go easy on me here :-), but, I had trouble distinguishing between l (lower case L) and 1 in the documentation.):confused:  Here it looks different, but what ever font I was looking at had me confused.  I guessed wrong more than once! The line-wrapping was also an issue.  A suggestion may be to have each line separated with a blank line in between so that if a line takes up more than one line it looks obvious. Did that make sense?

I followed the directions and it worked.  I did not have a fresh install, because I had upgraded from the prior version. 

A tip for those who do not have a wired connection: I used a USB wireless stick to connect to my router so that I could get what I needed for the built-in card.  It worked. The only thing was that I had to reboot after finishing these directions because the Wireless Stick was set up as eth0 and that is what the other card needed. After I got it taken care of things were okay.

However, the Network Manager (or whatever it is called--the one with the 2 black monitors at the top of the screen) is useless.  After I got the WiFi stick to work, I also downloaded some stuff from the repositories. One of them was *WiFi Radar*, and I am glad that I did. It will connect to my WiFi.  It won't do it automatically, but, I can choose my Network from the list and click "connect" and it will work. The Network Manager is useless.

When I was trying to get the Network Manager to work, I was amazed, because Ubuntu was crashing like crazy!  It made Windows look stable!!

I finally downloaded *WiFi Radar*, as I have already said, and also *KWiFi Manager*.

So, other than the Network Manager being useless, my only other problem was that it took me more than 5 minutes to do this--I can't type!  I am "hunt-and-peck", so it takes me awhile. Add to that the fact that I had to type several commands over because of the "l" vs "1" problem.:lolflag: And line wraps also, as I have said.

Also, as the article stated, the download site was flaky, but when I used the other one in the article, it worked!!

So, Thanks a bunch :KS :KS :KS :KS :KS 
5 Stars for this wonderful article!!  Thanks for everyone who contributed.  I am a newbie, but I hope I helped someone--this is a great community and I want to give back!

---

### Post by Jamie Jackson on 2008-05-09
> **DaleVandy said:**
> ...

I'll take your suggestions into consideration, but in the meantime, I want to make sure you know how to paste into the console. (It's not obvious how to do it.)

In non-console apps, ctrl-c = copy. However, in the console, you need to use ctrl-shift-c (since ctrl-c means "interrupt currently running command"). Likewise, to paste into the console, it's not ctrl-v, as it is in other apps; instead, it's ctrl-shift-v.

---

### Post by CyChess on 2008-05-09
hey, having followed the third version of the hardy fix, it can be said that it sort of works, but it prevents the computer from booting the next time (it hangs waiting for manual drivers). the computer will boot correctly again by flipping the wifi switch on or off during next boot. it's quirky, but after that you can turn it on with the nm applet and voila!
many thanks for your endeavors on this subject.
*bow*

---

### Post by Jamie Jackson on 2008-05-09
> **CyChess said:**
> ...

If you get a chance, comment ndiswrapper out of /etc/modules, reboot, and post the output of lsmod. I want to see what the dependencies are on your system (in a state where ndiswrapper hasn't been loaded).

---

### Post by TrinityOmega on 2008-05-09
First off, I just wanted to thank you guys for all this wonderful info.  This is the first guide I have found, that actually listed step by step, line by line, exactly how to make this Broadcom card work.  I am a new Ubuntu 8.04 users, exactly 4 days new.  I bought a HP 530 Laptop around Xmas season, got it cheap.  Thought Windows Vista would be good, but from day one was plagued with 5 minute bootups, system locking, and horrible performance issues.  I had always been intrigued with Linux, and had thought about taking the plunge.  So I did with the laptop.  I was impressed with Ubuntu, I liked that layout, bootup speeds, performance.  I was crushed when I found the Broadcom card problems.  But I found this page, and now the laptop works like I want it to.  I figure I have a few more months of tweaking and learning about Ubuntu and Linux, and lots of reading, before I can really move around it.  Thanks again for the guide, it was supremely helpful.

---

### Post by djbarroso on 2008-05-09
Just another big THANK YOU ! to Jamie Jackson and all of you who have been working on this and taking care of the debugging. 

When I upgraded to Hardy Heron, I thought I would be able to stop using ndiswrapper and just use the native drivers. However, although they work great at close range, the room I usually work in is rather far from the access point, making the connection hit-and-miss. Therefore, I reverted to ndiswrapper, which now works great for me. 

These are my specs:
----------------------
Brand and Model: Gateway MX6448

Wireless Brand and Model: 05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Wireless Chipset:05:00.0 0280: 14e4:4311 (rev 01)

Ubuntu Version: Description:    Ubuntu 8.04 (Ubuntu Studio 8.04, AMD64 version)

Kernel/architecture: 2.6.24-16-rt x86_64

Extra Boot options: none

Compiled NDISWrapper? No. Installed from Ubuntu Repository with Synaptic.
Version of Step2 used: 2a
Applied "Hardy Bug Fix" workaround?
	Yes:
	sudo rmmod b43
	sudo rmmod b44
	sudo rmmod b43legacy
	sudo rmmod ssb
	sudo rmmod ndiswrapper
	sudo modprobe ndiswrapper
	sudo modprobe ssb
	sudo modprobe b44

*Note: I did have to "re-apply" the "Hardy Bug Fix" workaround because I didn't have NetworkManager installed beforehand (after installing NetworkManager, <lshw -C network> changed from the correct "module=ndiswrapper" to "module=ssb".) I only "re-applied" the pertinent parts -- I kind of guessed, but it works! I might recommend having NetworkManager installed *before* applying the "Hardy Bug Fix" workaround; in my case, I think that would have been better.

Also, in order to make it permanent, I copied and pasted Version 0.3 (WITH WRAPPING in post).:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
---------------------------

     So, everything works great now! Although the connection strength at this distance from the AP is only around 17 or 18 %, the speed is listed at 36 Mbps, and there are no "packets lost" when I ping some IP to test the connection. 

My only remaining doubts would be regarding some error messages that appear when the computer is shutting down -- something along the lines of not being able to execute something related to the WLAN because some network daemon is no longer running -- but I suspect this is normal and is just due to the order in which the shutdown steps are being carried out. Any ideas on how I could take a look at these logs? I'm still kind of a newb!

     Thanks again!

---

### Post by xtopher.brandt on 2008-05-10
Thanks a bunch. This is the first time my wireless card has worked in a year!

Sorry didn't get the lsmod pre-fix. But here are the other statistics:

    * Machine Brand and Model: Dell Inspiron 8100
    * Wireless Brand and Model: 03:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    * Wireless Chipset: 03:00.0 0280: 14e4:4320 (rev 03)
    * Ubuntu Version: Description:	Ubuntu 8.04
    * Kernel / Architecture: 2.6.24-16-generic i686
    * Any extra boot options you might be using: none
    * Whether or not you had to compile NDISWrapper: No
    * Which version of Step 2 you used: 2b
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not: yes, and used V0.3 of the permenant fix which seems to work.

---

### Post by DaleVandy on 2008-05-10
> **Jamie Jackson said:**
> I'll take your suggestions into consideration, but in the meantime, I want to make sure you know how to paste into the console. (It's not obvious how to do it.)

In non-console apps, ctrl-c = copy. However, in the console, you need to use ctrl-shift-c (since ctrl-c means "interrupt currently running command"). Likewise, to paste into the console, it's not ctrl-v, as it is in other apps; instead, it's ctrl-shift-v.

Thanks for the tips. I have been using the menu options for copy and paste, since the "usual" (from my Windows point of view) methods didn't seem to work.

---

### Post by kingbilly on 2008-05-10
Thanks!

---

### Post by klick.here on 2008-05-11
Worked fine for me didn't have to compile.  Perfect instructions making it permanent works fine too. Thank Yoy:guitar:AWESOME!

---

### Post by Jamie Jackson on 2008-05-11
I finally bit the bullet and upgraded to Hardy tonight. FWIW, here is the the unload/reload script that was required on *my* machine:

Temporary fix:
```

sudo modprobe -r b43 ssb
sudo modprobe ndiswrapper
sudo modprobe ssb

```

Permanent fix (persists through a reboot):
```

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;' | sudo tee -a /etc/modprobe.d/ndiswrapper

```

Note: Each machine is different, as some machines have more/different modules depending on ssb. Therefore, what works on my machine is not necessarily what will work on yours. If you want me to tell you exactly what your module unload/reload sequence needs to be, post the output of "lsmod" before starting the steps in the wiki.

---

### Post by Mark003 on 2008-05-11
Ordering Rx Drugs online?



>[HERE](http://www.rxtrue.com/?aff_id=38492/url)<[color=blue][/color][size=24][/size]

---

### Post by marekwit on 2008-05-12
Success!!

Machine Brand and Model:
Dell Inspiron 1520

Wireless Brand and Model:
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Wireless Chipset:
0c:00.0 0280: 14e4:4311 (rev 01)

Ubuntu Version:
Description:	Ubuntu 8.04

Kernel / Architecture:
2.6.24-16-generic i686

No extra boot options

I didn't need to compile Ndiswrapper

I used wersion a of step 2

I had to apply the "Hardy Bug Fix" and for permanent solution modified /etc/modprobe.d/ndiswrapper file.


Thanks

marekwit

---

### Post by kutjara on 2008-05-12
Hi again Jamie. I just thought I'd give you a heads-up on the latest with my tx1420us (the machine with the BCM4328 card that couldn't connect using WPA under 64 bit Hardy.)

I installed 64 bit Debian Lenny last night, and your tutorial (again, option 2d) worked great for getting the basic features working. Version 0.3 of the Hardy bug fix sorted out the SSB problem, and I was able to scan and connect to unsecured networks.

Once again, however, WPA doesn't work. The only difference this time is that the card can actually see that my router is using WPA (iwlist scan reports the router's status correctly), whereas under Hardy it reported security as being "off." I don't yet know if this is significant, or just another red herring. As I said before, this problem is no doubt limited to my particular hardware, so it's unsurprising it persists under Lenny.

Obviously, this doesn't get me any closer to using the built-in card in my laptop, but it does mean that your tutorial should be directly applicable to machines running pure Debian as well. I'm putting this out there so any Debian Lenny users having problems can find this thread.

---

### Post by Insperatus on 2008-05-12
Followed https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff to success!  One additional step was required however!

#

Machine Brand and Model:

Dell Inspiron 1505E (AKA Inspiron 6400)

Wireless Brand and Model:

Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01) (Dell Wireless 1500 Draft 802.11n WLAN mini Card)

Wireless Chipset:

0b:00.0 0280: 14e4:4328 (rev 01)

Ubuntu Version: 

Ubuntu 8.04

Kernel/architecture (including 32 vs. 64 bit) : 

2.6.24-16-generic i686

No extra boot options

Didn't compile NDISWrapper

Which version of Step 2 you used:

Step '2d'

Hardy Bug Fix:

So sorry I don't remember which "Hardy Bug Fix" I used but I did use one.

Anyhow on to my extra step!  After following [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") Ubuntu was recognizing my wireless card but no wireless APs were showing up.  Then I remembered having had a similar problem under Vista.  The solution was to disable the "Bluetooth Collaboration" built into the wireless driver.  To do this in Ubuntu follow these instructions:

1. Open Terminal and enter:

sudo gedit /etc/ndiswrapper/bcmwl5/14E4:4328.5.conf

2. Scroll down to where it says 'BTCoexist|1' and change to 'BTCoexist|0'

3. Click Save and close 

That's it! :guitar:

I really hope this helps someone as frustrated as I was!

---

### Post by hessianmatrix on 2008-05-13
I am writing this to say that when I reinstalled Hardy using alternate CD my wireless worked just out of the box. I have couple of posts here crying for help to get my wireless working on Hardy. This was installed using the desktop CD and not alternate CD version. 

I do not know why it worked with alternate CD but not with desktop CD version. If I can be of any help if someone wants to investigate this problem, I'll be glad to share any relevant info.

Thanks again for all your help and patience.

---

### Post by GrandpaLeaman on 2008-05-13
Wow, thanks a million. It took me only 15 minutes to get my wireless up and running after upgrading to Hardy. I appreciate all the work you put into this quick fix Mr. Jackson. Here is my info.

Computer: Dell E1505/6400

Wireless brand/model: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Wireless chipset: 14e4:4311 (rev 01)

Ubuntu version: Ubuntu 8.04

Kernel: 2.6.24-16-generic i686

Did not have to compile NDISWrapper

Used step 2A

And yes, I had to apply the Hardy bug fix

I made it permanent with version 0.3 and everything is running great. Even better than in Gutsy I believe.

A tip of the ol' hat to you Jamie Jackson!!!

---

### Post by Alienhunter2010 on 2008-05-14
I'm using a Dell Inspiron 1501.

I follow with SUCCESS the step on the tutorial (Step 2a + Hardy Heron Bug Fix), but - at the end - the Wireless card still DON'T WORK.

[FONT="Fixedsys"]lshw -C network[/FONT] says me that I'm using module=ndiswrapper correctly, But I can't see my WiFi Networks. [FONT="Fixedsys"]iwlist wlan0 scan[/FONT] says:

 wlan0     No scan results

As suggest I follow the Step 2b without having trouble. But I continue to not found any Wireless net. Following I report my [FONT="Fixedsys"]lshw -C network[/FONT] output:

       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:53:84:f6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

Hardy Heron installation is a week old. I try to make the wireless card working using b43 module with b43fwcutter (on the old 7.10 it was working good with the bcm43xx module) and it was the first time I try to use ndiswrapper.

I hope to be usefull to the test of the tutorial, and I also hope that the tutorial wiull help me to solve the problem. ;-)

Bye, Alex.

---

### Post by SurferGTO on 2008-05-14
hey i just figured id post my results with attempting to get wireless using the hardy work around you have described in another post (this thread was linked to in another thread) 

Machine is an HP DV2000 with the bcm4310 rev01 wireless. so far i have had absolutely no problem installing or running ndiswrapper, or installing the driver and having ndiswrapper recognize it, however i cant seem to get ndiswrapper to see the hardware as beeing installed. (hardware not present when windows wireless drivers is run). 

when i run lshw -c network here is what i get:
> master@master-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: a2
       serial: 00:1d:72:48:08:20
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
master@master-laptop:~$ 



that module=forcedeth thingie looks scary. what is it.

---

### Post by paledread on 2008-05-14
Brilliant. I now have wifi working, after tooling around for hours trying to find out why something that worked in Gutsy without any input from me is suddenly broken in Hardy.

HP Pavilion dv9620us
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
Ubuntu 8.04
2.6.24-17-generic i686
no extra boot options

Your HowTo was modified as follows for my case.

Step 1 as written
Step 2a as written
Step 3 as written

---

### Post by paledread on 2008-05-14
Sorry but I managed to make the previous post without completing the message.

Brilliant. I now have wifi working, after tooling around for hours trying to find out why something that worked in Gutsy without any input from me is suddenly broken in Hardy.

HP Pavilion dv9620us
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
Ubuntu 8.04
2.6.24-17-generic i686
no extra boot options

Your HowTo was modified as follows for my case.

Insert (from bug 1 on the ssb modules loading issue) the following line in /etc/modules.d/ndiswrapper :

install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci

Step 1 as written
Step 2a as written
Step 3 as written except that there was an error message after "sudo ndiswrapper -m" and I had to remove the pre-existing line "alias wlan0 ndiswrapper" from /etc/modules.d/ndiswrapper in order to succeed.

After completing step 3 "modules=ssb" was in the last line of output from running "sudo lshw -C network".

So I then followed Hardy Bug Fix, Trying it Temporarily, and had to make some changes as follows :

"sudo rmmod b44" and "sudo rmmod b43legacy" failed as these modules were apparently not loaded.

After "sudo modprobe ndiswrapper" received a "Fatal Error Module OHCI not found". However this did not seem to be completely fatal, perhaps just an injury, as my wifi light turned blue at this point, and "sudo lshw -C network" was now giving a good result.

By trial and error I discovered that the last line "sudo modprobe b44" needed to be omitted (for me).

At this point there seemed to be a working wifi card but still no connecton to the WAP, and I had to reinstate the following lines in /etc/network/interfaces :

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

Then after running "sudo /etc/init.d/networking restart", MAGIC, a working Internet connection via the wifi card and the linksys WAP.

Of course it all crashed after a reboot, but now the card can be consistently brought up again by running the lines under "Trying it Temporarily" as modified above.

Now to follow on and get these lines in a script so that I can simply run the script after a reboot (or have it run automagically as you suggest).

---

### Post by Ph83drus on 2008-05-14
Hi,

I've been trying for two weeks to get my broadcom 4306 working on my Dell d600.   FRUSTRATING!  I've tried everything to no avail.

I think it is the ssb module thing.  Unfortunately, my linux understanding is rather poor.  I don't know what all these comands in the terminal are doing.

I would really like some help.  Or maybe I should just go buy that intel wireless card for 39 bucks down the street.

Could anyone help me?  What do I need to post?

---

### Post by Jamie Jackson on 2008-05-15
> **SurferGTO said:**
> hey i just figured id post my results with attempting to get wireless using the hardy work around you have described in another post (this thread was linked to in another thread) 

Machine is an HP DV2000 with the bcm4310 rev01 wireless. so far i have had absolutely no problem installing or running ndiswrapper, or installing the driver and having ndiswrapper recognize it, however i cant seem to get ndiswrapper to see the hardware as beeing installed. (hardware not present when windows wireless drivers is run). 

when i run lshw -c network here is what i get:


that module=forcedeth thingie looks scary. what is it.

Thankfully, that's for the wired NIC, anyway, so I'm pretty sure you won't be forcefully executed.

What's "ndiswrapper -l" give?

---

### Post by Jamie Jackson on 2008-05-15
> **paledread said:**
> Sorry but I managed to make the previous post without completing the message.

Brilliant. I now have wifi working, after tooling around for hours trying to find out why something that worked in Gutsy without any input from me is suddenly broken in Hardy.

HP Pavilion dv9620us
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
Ubuntu 8.04
2.6.24-17-generic i686
no extra boot options

Your HowTo was modified as follows for my case.

Insert (from bug 1 on the ssb modules loading issue) the following line in /etc/modules.d/ndiswrapper :

install ndiswrapper modprobe -r ohci_hcd ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ohci

Step 1 as written
Step 2a as written
Step 3 as written except that there was an error message after "sudo ndiswrapper -m" and I had to remove the pre-existing line "alias wlan0 ndiswrapper" from /etc/modules.d/ndiswrapper in order to succeed.

After completing step 3 "modules=ssb" was in the last line of output from running "sudo lshw -C network".

So I then followed Hardy Bug Fix, Trying it Temporarily, and had to make some changes as follows :

"sudo rmmod b44" and "sudo rmmod b43legacy" failed as these modules were apparently not loaded.

After "sudo modprobe ndiswrapper" received a "Fatal Error Module OHCI not found". However this did not seem to be completely fatal, perhaps just an injury, as my wifi light turned blue at this point, and "sudo lshw -C network" was now giving a good result.

By trial and error I discovered that the last line "sudo modprobe b44" needed to be omitted (for me).

At this point there seemed to be a working wifi card but still no connecton to the WAP, and I had to reinstate the following lines in /etc/network/interfaces :

auto wlan0
iface wlan0 inet dhcp
wireless-essid linksys

Then after running "sudo /etc/init.d/networking restart", MAGIC, a working Internet connection via the wifi card and the linksys WAP.

Of course it all crashed after a reboot, but now the card can be consistently brought up again by running the lines under "Trying it Temporarily" as modified above.

Now to follow on and get these lines in a script so that I can simply run the script after a reboot (or have it run automagically as you suggest).

Try commenting out the line that we added to /etc/modprobe.d/ndiswrapper, reboot, and paste the results of "lsmod" in a post. I want to see what your machine's ssb dependencies are exactly.

---

### Post by Jamie Jackson on 2008-05-15
> **Ph83drus said:**
> Hi,

I've been trying for two weeks to get my broadcom 4306 working on my Dell d600.   FRUSTRATING!  I've tried everything to no avail.

I think it is the ssb module thing.  Unfortunately, my linux understanding is rather poor.  I don't know what all these comands in the terminal are doing.

I would really like some help.  Or maybe I should just go buy that intel wireless card for 39 bucks down the street.

Could anyone help me?  What do I need to post?

I'm not going to talk you out of buying a new, compatible wireless card (I bought a $10 usb wireless device for another machine, and it works great out of the box in Linux.)

Anyway, reboot with the Hardy fix disabled and paste the output of "lsmod" in this thread.

---

### Post by Ph83drus on 2008-05-15
Thanks!  How do I disable the hardy fix??  by rebooting?

---

### Post by Ph83drus on 2008-05-15
Here's my lsmod right now, I haven't rebooted yet.

phaedrus@ubuntu:~$ lsmod
Module                  Size  Used by
af_packet              21636  2 
b43legacy             126880  0 
b44                    27024  0 
ssb                    31236  2 b43legacy,b44
binfmt_misc            11272  1 
mac80211              162708  1 b43legacy
cfg80211               14088  1 mac80211
mii                     5504  1 b44
radeon                123296  2 
drm                    80788  3 radeon
snd_atiixp_modem       16008  0 
snd_via82xx_modem      14984  0 
snd_intel8x0m          17804  5 
speedstep_centrino      6920  0 
cpufreq_userspace       4120  0 
cpufreq_stats           5124  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  1 
freq_table              4484  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7200  0 
sbs                    14216  0 
sbshc                   6784  1 sbs
dock                   10124  0 
container               4736  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
aes_i586               32640  0 
dm_crypt               14340  0 
lp                     11332  0 
pcmcia                 39852  0 
joydev                 11840  0 
arc4                    2048  2 
ecb                     3584  2 
blkcipher               7428  1 ecb
yenta_socket           26380  4 
rsrc_nonstatic         12800  1 yenta_socket
pcmcia_core            39440  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  18832  0 
output                  3712  1 video
snd_intel8x0           33948  3 
snd_ac97_codec         99876  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            40736  0 
snd_mixer_oss          16896  1 snd_pcm_oss
snd_pcm                75400  9 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3972  0 
serio_raw               7044  0 
button                  8336  0 
snd_seq_oss            34048  0 
snd_seq_midi            8480  0 
battery                13316  0 
snd_rawmidi            24608  1 snd_seq_midi
ac                      6020  0 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51152  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23556  2 snd_pcm,snd_seq
snd_seq_device          8588  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 33428  0 
snd                    54692  27 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  7968  0 
evdev                  11776  6 
pci_hotplug            29728  1 shpchp
parport_pc             35108  1 
parport                35912  2 lp,parport_pc
intel_agp              24596  1 
agpgart                33328  2 drm,intel_agp
iTCO_wdt               11808  0 
iTCO_vendor_support     3972  1 iTCO_wdt
soundcore               7520  1 snd
snd_page_alloc         10504  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
pcspkr                  3072  0 
psmouse                39056  0 
rtc                    13212  0 
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
sd_mod                 29584  3 
usbhid                 30592  0 
hid                    36480  1 usbhid
ata_piix               18692  2 
pata_acpi               7424  0 
ata_generic             7428  0 
tg3                   113540  0 
libata                159600  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151180  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36748  0 
uhci_hcd               25616  0 
usbcore               143724  4 usbhid,ehci_hcd,uhci_hcd
raid10                 24192  0 
raid456               125712  0 
async_xor               4096  1 raid456
async_memcpy            2816  1 raid456
async_tx                7496  3 raid456,async_xor,async_memcpy
xor                    15240  2 raid456,async_xor
raid1                  24192  0 
raid0                   8320  0 
multipath               8448  0 
linear                  6272  0 
md_mod                 79508  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              22912  0 
dm_snapshot            18592  0 
dm_mod                 60484  3 dm_crypt,dm_mirror,dm_snapshot
thermal                15772  0 
processor              28080  2 thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  1 
phaedrus@ubuntu:~$

---

### Post by Jamie Jackson on 2008-05-15
> **Ph83drus said:**
> Here's my lsmod right now, I haven't rebooted yet.

Okay, now post the lsmod after a reboot (after having disabled the hardy fix):

```
gksu gedit /etc/modprobe.d/ndiswrapper
```

In the file that's opened up, comment out (add a # before) the third line, then reboot.

---

### Post by Ph83drus on 2008-05-15
OKay, I'll reboot.

Just so you know, the line I commented out was:

install pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* /sbin/modprobe ndiswrapper


I put a # in front of it, as you said.

rebooting!

---

### Post by Ph83drus on 2008-05-15
Here's my lsmod after rebooting:

phaedrus@ubuntu:~$ lsmod
Module                  Size  Used by
af_packet              21636  2 
b43legacy             126880  0 
b44                    27024  0 
ssb                    31236  2 b43legacy,b44
binfmt_misc            11272  1 
mac80211              162708  1 b43legacy
cfg80211               14088  1 mac80211
mii                     5504  1 b44
radeon                123296  2 
drm                    80788  3 radeon
snd_atiixp_modem       16008  0 
snd_via82xx_modem      14984  0 
snd_intel8x0m          17804  5 
speedstep_centrino      6920  0 
cpufreq_userspace       4120  0 
cpufreq_stats           5124  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  1 
freq_table              4484  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7200  0 
sbs                    14216  0 
sbshc                   6784  1 sbs
dock                   10124  0 
container               4736  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
aes_i586               32640  0 
dm_crypt               14340  0 
lp                     11332  0 
pcmcia                 39852  0 
joydev                 11840  0 
arc4                    2048  2 
ecb                     3584  2 
blkcipher               7428  1 ecb
yenta_socket           26380  4 
rsrc_nonstatic         12800  1 yenta_socket
pcmcia_core            39440  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           33948  2 
snd_ac97_codec         99876  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
snd_pcm_oss            40736  0 
snd_mixer_oss          16896  1 snd_pcm_oss
video                  18832  0 
output                  3712  1 video
snd_pcm                75400  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3972  0 
serio_raw               7044  0 
snd_seq_oss            34048  0 
snd_seq_midi            8480  0 
snd_rawmidi            24608  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
button                  8336  0 
battery                13316  0 
snd_seq                51152  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ac                      6020  0 
snd_timer              23556  2 snd_pcm,snd_seq
snd_seq_device          8588  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54692  26 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24596  1 
shpchp                 33428  0 
evdev                  11776  6 
dcdbas                  7968  0 
parport_pc             35108  1 
parport                35912  2 lp,parport_pc
soundcore               7520  1 snd
agpgart                33328  2 drm,intel_agp
pci_hotplug            29728  1 shpchp
iTCO_wdt               11808  0 
iTCO_vendor_support     3972  1 iTCO_wdt
snd_page_alloc         10504  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
pcspkr                  3072  0 
psmouse                39056  0 
rtc                    13212  0 
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
sd_mod                 29584  3 
usbhid                 30592  0 
hid                    36480  1 usbhid
ata_piix               18692  2 
pata_acpi               7424  0 
ata_generic             7428  0 
tg3                   113540  0 
libata                159600  3 ata_piix,pata_acpi,ata_generic
scsi_mod              151180  4 sg,sr_mod,sd_mod,libata
ehci_hcd               36748  0 
uhci_hcd               25616  0 
usbcore               143724  4 usbhid,ehci_hcd,uhci_hcd
raid10                 24192  0 
raid456               125712  0 
async_xor               4096  1 raid456
async_memcpy            2816  1 raid456
async_tx                7496  3 raid456,async_xor,async_memcpy
xor                    15240  2 raid456,async_xor
raid1                  24192  0 
raid0                   8320  0 
multipath               8448  0 
linear                  6272  0 
md_mod                 79508  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              22912  0 
dm_snapshot            18592  0 
dm_mod                 60484  3 dm_crypt,dm_mirror,dm_snapshot
thermal                15772  0 
processor              28080  2 thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  1 
phaedrus@ubuntu:~$

---

### Post by Ph83drus on 2008-05-15
by the way, this is what the ndiswrapper file looks like that you had me modify:

install pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000014E4d00004301sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
#install pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000014E4d00004320sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper

---

### Post by paledread on 2008-05-16
In reponse to yours in # 594 here is the output of lsmod :

Module                  Size  Used by
ppdev                  10372  0
ipv6                  267780  14
powernow_k8            16704  1
cpufreq_conservative     8712  0
cpufreq_userspace       5284  0
cpufreq_stats           7104  0
cpufreq_ondemand        9740  1
freq_table              5536  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0
sbs                    15112  0
sbshc                   7680  1 sbs
dock                   11280  0
container               5632  0
af_packet              23812  0
iptable_filter          3840  0
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
aes_i586               33536  0
dm_crypt               15364  0
dm_mod                 62660  1 dm_crypt
ndiswrapper           192920  0
b43                   115104  0
rfkill                  8592  1 b43
mac80211              165652  1 b43
cfg80211               15112  1 mac80211
led_class               6020  1 b43
input_polldev           5896  1 b43
sbp2                   24072  0
parport_pc             36260  0
lp                     12324  0
parport                37832  3 ppdev,parport_pc,lp
loop                   18948  0
joydev                 13120  0
uvcvideo               58116  0
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            18304  2 uvcvideo,videodev
snd_hda_intel         344728  3
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
serio_raw               7940  0
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
video                  19856  8
output                  4736  1 video
sdhci                  19076  0
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ricoh_mmc               4352  0
psmouse                40336  0
mmc_core               51460  1 sdhci
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi_acer                9644  0
nvidia               7825536  26
ac                      6916  0
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
battery                14212  0
button                  9232  0
agpgart                34760  1 nvidia
k8temp                  6656  0
soundcore               8800  1 snd
shpchp                 34452  0
pci_hotplug            30880  1 shpchp
evdev                  13056  7
i2c_core               24832  1 nvidia
pcspkr                  4224  0
ext3                  136712  1
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0
sr_mod                 17956  0
sd_mod                 30720  3
cdrom                  37408  1 sr_mod
pata_acpi               8320  0
ata_generic             8324  0
ssb                    32260  1 b43
ohci1394               33584  0
ieee1394               93752  2 sbp2,ohci1394
forcedeth              51980  0
ahci                   28420  2
pata_amd               14212  0
libata                159344  4 pata_acpi,ata_generic,ahci,pata_amd
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ohci_hcd               25348  0
ehci_hcd               37900  0
usbcore               146028  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
thermal                16796  0
processor              36872  3 powernow_k8,thermal
fan                     5636  0
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1

---

### Post by Jamie Jackson on 2008-05-16
> **Ph83drus said:**
> by the way, this is what the ndiswrapper file looks like that you had me modify:

install pci:v000014E4d00004301sv00004301sd00001737bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000014E4d00004301sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
#install pci:v000014E4d00004320sv00000417sd000014E4bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000014E4d00004320sv00004320sd00001737bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v000014E4d00004320sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper

Gah! That's completely Greek to me. Are we looking at the same file?

Here's what my personal /etc/modprobe.d/ndiswrapper file looks like. Line 1 is stock ndiswrapper stuff, lines two and three were added when I ran the Hardy fix v3 (customized slightly for my machine).
```
alias wlan0 ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Sat May 10 23:58:42 EDT 2008 
install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;
```

The third line is the one I wanted you to comment out, but I wasn't expecting your file to look like that. Which version of the Hardy fix had you applied?

---

### Post by Jamie Jackson on 2008-05-16
> **paledread said:**
> In reponse to yours in # 594 here is the output of lsmod : ...

Okay, your /etc/modprobe.d/ndiswrapper line needs to look just like mine (listed in the above post to Ph83drus).

So just "gksu gedit /etc/modprobe.d/ndiswrapper" and edit it to look like mine, and see how your reboot works.

---

### Post by Ph83drus on 2008-05-16
Hi Jamie!

I gave in.  I went to the store and bought a Intel wireless card 2200BG.

I wanted something easier, and it only cost 27 dollars.

But guess what?!  It doesn't work either!!

It's a little better,

I can SEE the networks that I could connect to, using Wicd instead of network manager.   I'm using WPA encryption.   But I still can't connect to the networks.

I'm not sure if you could help with this problem too!

I started a thread so that I don't hijack this one.

[http://ubuntuforums.org/showthread.php?t=796877](http://ubuntuforums.org/showthread.php?t=796877)

Thank you!

---

### Post by kutjara on 2008-05-16
> **SurferGTO said:**
> that module=forcedeth thingie looks scary. what is it.

It's the somewhat alarmingly-named driver for your ethernet card. Don't mess with it unless you want ethernet to stop working.

---

### Post by well_r on 2008-05-17
Hi
thank you so much..
your guide helped me, and it seems to work after reboot..

my specs are:
HP Pavilion dv6545eo Notebook PC
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

---

### Post by lilmagnus on 2008-05-17
Great job on the Wiki! Thanks alot! All running fine now.

Driver section 2a with Hardy fix v0.3

Compaq Presario v5000 (v5101us)
Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
Ubuntu 8.04   2.6.24-16-generic i686

---

### Post by DarkW0lf on 2008-05-17
Am I still the only xubuntu AMD64 user here ? :)

Before I try to update is there any more on this Hardy Bug ?
Right now this and KVM's intereference with Virtualbox are the only things keeping me back from upgrading.

---

### Post by ThePenguinKnight on 2008-05-18
Well, I had tried Ubuntu and using the Wiki for my Dell Inspiron 1520 w/ broadcom 4328 a couple weeks ago and couldn't get it working. On the advice of a buddy who's more versed than I am, I scrapped Ubuntu for a week and used Mepis 7.0, under which I could get some functionality for all my hardware. I liked Mepis, but I like Ubuntu moreso, thus with some lappy troubles I'm back into a Hardy build and playing around.

I re-tried the wiki to no initial success; network manager didn't even see the signal from the router 10 feet away. Without rebooting (meaning ndiswrapper had the drivers and the modprobe stuff/Hardy fix were active), I continued scanning for solutions. Fortunately, DaleVandy back on pg 58 mentioned using WifiRadar instead of the stock network manager. After a Synaptic install of WifiRadar, my wireless connection fired right up automatically with basic WEP.

I discovered on reboot the settings don't stick. The module reverts and I have to manually enter "sudo modprobe ndiswrapper" to enable the driver. Once done, I have full functionality on WEP. I have not yet tested WAP.

I tried v0.2 and v0.3 of the Hardy fix, but neither made it stick. I didn't try v0.1, as I'm not confident I could easily restore wired connectivity :P.

All in all, I'm greatly pleased. My wifi works again, even with an extra button press or keystroke or two, so I am happy. Thanks for the guide :). Small suggestion, you may want to include a note in the Wiki about WifiRadar and Hardy. 

   [quote=* Machine Brand and Model:]   Dell Inspiron 1520[/quote]
    [quote=* Wireless Brand and Model (please post the whole line): lspci | grep Broadcom ]03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
[/quote]
    [quote=* Wireless Chipset: lspci -n | grep '14e4:43']0c:00.0 0280:] 14e4:4328 (rev 03)[/quote]
    [quote=* Ubuntu Version: lsb_release -d]Description:	Ubuntu 8.04
[/quote]
    [quote=* Kernel / Architecture: uname -mr]2.6.24-16-generic i686
[/quote]
    * No Extras
    * Did not compile Ndiswrapper
    * Used step 2d
    * I applied the Hardy fix, and while the temporary one works, the permanents don't stick (v0.2 and v0.3)

Thanks again :)

---

### Post by Jamie Jackson on 2008-05-18
> **DarkW0lf said:**
> Am I still the only xubuntu AMD64 user here ? :)

Before I try to update is there any more on this Hardy Bug ?
Right now this and KVM's intereference with Virtualbox are the only things keeping me back from upgrading.

Hey there, DarkW0lf.

I don't know if I would consider this a Hardy bug anymore as much as a ndiswrapper bug. Or maybe it's not a bug at all, and just something one has to take into consideration with ndiswrapper.

Anyway, to prepare for an update, you could run from the LiveCD and take a look at the output of your lsmod to figure out what modules are dependent on ssb, to get the proper sequence for the module unload/reload thing.

Or, if you want, post the lsmod here and I'll tell you what your "Hardy Bug Fix" procedure should be.

The /etc/modprobe.d/ndiswrapper trick seems to be an elegant/appropriate way to handle the ndiswrapper/ssb contention, so I don't feel like it's a hack anymore.

---

### Post by Jamie Jackson on 2008-05-18
> **ThePenguinKnight said:**
> ...
You only need one version of the Hardy fix, and I'd recommend version 3. If you get a chance, and know how to do it, I'd like you to disable the Hardy fix and post the output of "lsmod", so I can give you the module unload/load sequence that suits your particular machine.

Actually, here's how to do the disabling:

Open up the /etc/modprobe.d/ndiswrapper file (gksu gedit /etc/modprobe.d/ndiswrapper), and comment out (put a # before) the line *after* "#Hardy ssb/ndiswrapper workaround..."

Then open up the /etc/init.d/rc.local file (gksu gedit /etc/init.d/rc.local) and *delete* the following lines (delete them, because I no longer recommend this fix):
```

#hardy ssb bug-fix
rmmod b43
rmmod b44
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44
```

Then, reboot and post the output of "lsmod"

---

### Post by ThePenguinKnight on 2008-05-18
Thank you, Jamie Jackson. I removed the Hardy fix per your instructions, but I should note that there were none of the lines you indicated in my "rc.local" file. It is as follows:

rc.local file:
```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

For fun, here's the  /etc/modprobe.d/ndiswrapper file:
```
#Hardy ssb/ndiswrapper workaround, added Sat May 17 22:34:48 CDT 2008 
#install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

lsmod output.
```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
dcdbas                  9504  0 
evdev                  13056  8 
serio_raw               7940  0 
psmouse                40336  0 
snd_hda_intel         344728  3 
pcspkr                  4224  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
sdhci                  19076  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
snd_seq_dummy           4868  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
nvidia               7825536  36 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
i2c_core               24832  1 nvidia
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  14 
output                  4736  1 video
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  0 
button                  9232  0 
battery                14212  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
ac                      6916  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
b44                    28432  0 
ata_piix               19588  2 
ohci1394               33584  0 
libata                159344  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ssb                    32260  1 b44
ehci_hcd               37900  0 
uhci_hcd               27024  0 
mii                     6400  1 b44
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

"sudo modprobe ndiswrapper" still activates WifiRadar and allows me to use my 4328, despite undoing the Hardy fix. Any ideas on having Ndiswrapper run the modprobe on startup automatically would be well appreciated. Thanks again :)

---

### Post by Feenix3k on 2008-05-18
My wireless now works but lost the b44 driver for the wired bcm card. I copied and pasted:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper


In to a terminal window, but I must be missing something.

---

### Post by bhdenterprises on 2008-05-19
> **Jamie Jackson said:**
> Did you mean, "I just tried the *fw-cutter* solution in Hardy tonight since my wireless chip is working out of the box. But it only gets 1Mb/s to 5Mb/s so I tried using ndiswrapper again?"

Never mind, I re-read and get what you're saying. However, let me get another thing straight: Did NetworkManager *not work*, or do you just *prefer* wicd?

hi jaime,

sorry i wasn't able to reply immediately. Network Manager worked out fine with wireless. I just have some issues roaming between wired and wireless connection. But after some updates from Ubuntu the Network Manager worked again as before so I had uninstalled wicd and just use Network Manager.

Thanks a lot for the great howto!

---

### Post by kevdog on 2008-05-19
Jamie

Is there a way on your testimonials that you could (or perhaps make it sortable) so it would be easy to sort by chipset number?  Right now its organized by date -- and although useful, makes it difficult to search specifically for a certain chipset.

---

### Post by Jamie Jackson on 2008-05-19
> **ThePenguinKnight said:**
> Thank you, Jamie Jackson. I removed the Hardy fix per your instructions, but I should note that there were none of the lines you indicated in my "rc.local" file. It is as follows:

rc.local file:
```
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
	if [ -x /etc/rc.local ]; then
		log_begin_msg "Running local boot scripts (/etc/rc.local)"
		/etc/rc.local
		log_end_msg $?
	fi
}

case "$1" in
    start)
	do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

For fun, here's the  /etc/modprobe.d/ndiswrapper file:
```
#Hardy ssb/ndiswrapper workaround, added Sat May 17 22:34:48 CDT 2008 
#install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

lsmod output.
```
Module                  Size  Used by
ipv6                  267780  10 
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
joydev                 13120  0 
dcdbas                  9504  0 
evdev                  13056  8 
serio_raw               7940  0 
psmouse                40336  0 
snd_hda_intel         344728  3 
pcspkr                  4224  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
sdhci                  19076  0 
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
mmc_core               51460  1 sdhci
ricoh_mmc               4352  0 
snd_seq_dummy           4868  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
nvidia               7825536  36 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
i2c_core               24832  1 nvidia
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  14 
output                  4736  1 video
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi_acer                9644  0 
button                  9232  0 
battery                14212  0 
soundcore               8800  1 snd
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
ac                      6916  0 
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  3 
pata_acpi               8320  0 
ata_generic             8324  0 
b44                    28432  0 
ata_piix               19588  2 
ohci1394               33584  0 
libata                159344  3 pata_acpi,ata_generic,ata_piix
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata
ieee1394               93752  2 sbp2,ohci1394
ssb                    32260  1 b44
ehci_hcd               37900  0 
uhci_hcd               27024  0 
mii                     6400  1 b44
usbcore               146028  3 ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3 

```

"sudo modprobe ndiswrapper" still activates WifiRadar and allows me to use my 4328, despite undoing the Hardy fix. Any ideas on having Ndiswrapper run the modprobe on startup automatically would be well appreciated. Thanks again :)

It's unusual that you've got no reference to b43 or b43legacy, but anyway...

Looks like your /etc/modprobe.d/ndiswrapper line should look like this:
```

install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

```

Also, make sure that your /etc/modules file has a line that reads [FONT="Courier New"]ndiswrapper[/FONT] all by itself (gksu gedit /etc/modules).

---

### Post by Jamie Jackson on 2008-05-19
> **Feenix3k said:**
> My wireless now works but lost the b44 driver for the wired bcm card. I copied and pasted:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper


In to a terminal window, but I must be missing something.

Open up /etc/modprobe.d/ndiswrapper (gksu gedit /etc/modprobe.d/ndiswrapper) and comment out (put a "#" before) the line starting with "install ndiswrapper..."

Then reboot, and post the output of [FONT="Courier New"]lsmod[/FONT].

---

### Post by Jamie Jackson on 2008-05-19
> **kevdog said:**
> Jamie

Is there a way on your testimonials that you could (or perhaps make it sortable) so it would be easy to sort by chipset number?  Right now its organized by date -- and although useful, makes it difficult to search specifically for a certain chipset.

I've just been using my browser's find for chipset searching within the testimonials. As far as making it sortable, there are javascript libraries that could work, but I don't know how well JS can be incorporated in to the wiki (or how Kosher that would be). 

With regard to just adding a column for the chipset: I'm on the fence about it. I think it would be easy for there to be a column proliferation (Ubuntu version, 32 vs. 64 bit, etc.) which could make adding a testimonial more confusing.

---

### Post by ThePenguinKnight on 2008-05-21
Thanks, Jamie Jackson. After yet another install of Ubuntu, I've successfully got the wireless utility configured and starting on bootup. Good work :D

---

### Post by Feenix3k on 2008-05-21
Jamie Jackson   Here is the copy of lsmod with fix commented out. I also added the ifconfig for it has a line I donn't know what is does.

feenix@James-Laptop:~$ lsmod 
Module                  Size  Used by 
b44                    28432  0 
mii                     6400  1 b44 
ssb                    32260  1 b44 
ndiswrapper           192920  0 
binfmt_misc            12808  1 
af_packet              23812  2 
ipv6                  267780  14 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm 
bluetooth              61156  4 rfcomm,l2cap 
ppdev                  10372  0 
speedstep_ich           6288  0 
speedstep_lib           6532  1 speedstep_ich 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  1 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
freq_table              5536  3 speedstep_ich,cpufreq_ondemand,cpufreq_stats 
cpufreq_conservative     8712  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs 
dock                   11280  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter 
x_tables               16132  1 ip_tables 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp 
loop                   18948  0 
pcmcia                 40876  0 
joydev                 13120  0 
arc4                    2944  0 
ecb                     4480  0 
blkcipher               8324  1 ecb 
usblp                  15872  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0 
ac97_bus                3072  1 snd_ac97_codec 
yenta_socket           27276  1 
rsrc_nonstatic         13696  1 yenta_socket 
pcmcia_core            40596  3 pcmcia,yenta_socket,rsrc_nonstatic 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss 
nvidia               7825536  26 
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
video                  19856  5 
output                  4736  1 video 
i2c_core               24832  1 nvidia 
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi 
serio_raw               7940  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi 
ac                      6916  0 
button                  9232  0 
battery                14212  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              24836  2 snd_pcm,snd_seq 
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
evdev                  13056  6 
intel_agp              25492  1 
agpgart                34760  2 nvidia,intel_agp 
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp 
dcdbas                  9504  0 
snd                    56996  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               8800  1 snd 
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm 
pcspkr                  4224  0 
psmouse                40336  0 
ext3                  136712  2 
jbd                    48404  1 ext3 
mbcache                 9600  1 ext3 
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  3 
cdrom                  37408  1 sr_mod 
ata_generic             8324  0 
ata_piix               19588  2 
pata_acpi               8320  0 
ohci1394               33584  0 
libata                159344  3 ata_generic,ata_piix,pata_acpi 
scsi_mod              151436  5 sbp2,sg,sr_mod,sd_mod,libata 
ieee1394               93752  2 sbp2,ohci1394 
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  5 ndiswrapper,usblp,ehci_hcd,uhci_hcd 
dm_mirror              24832  0 
dm_snapshot            19620  0 
dm_mod                 62660  7 dm_mirror,dm_snapshot 
thermal                16796  0 
processor              36872  2 thermal 
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon 
font                    9472  1 fbcon 
bitblit                 6784  1 fbcon 
softcursor              3072  1 bitblit 
fuse                   50580  1 
feenix@James-Laptop:~$ 


The ifconfig 

feenix@James-Laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:450 errors:0 dropped:0 overruns:0 frame:0
TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:42306 (41.3 KB) TX bytes:13370 (13.0 KB)
Interrupt:17

eth0:avahi Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
inet addr:169.254.6.161 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8191 errors:0 dropped:0 overruns:0 frame:0
TX packets:8191 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1398266 (1.3 MB) TX bytes:1398266 (1.3 MB)

wlan0 Link encap:Ethernet HWaddr 00:90:4b:63:82:b2
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1184 errors:0 dropped:0 overruns:0 frame:0
TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:869832 (849.4 KB) TX bytes:158031 (154.3 KB)
Interrupt:19 Memory:faffc000-faffe000


I have no idea whast this line is or what it does, I have never seen it befor in ifconfig



eth0:avahi Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
inet addr:169.254.6.161 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:17

---

### Post by Feenix3k on 2008-05-22
> **Jamie Jackson said:**
> I'm not clear on what you're saying here. Could you clarify?


On my Dell 5150 the b44 is the driver for the wired card. Wireless uses the bcmwl5.

---

### Post by Jamie Jackson on 2008-05-22
> **Feenix3k said:**
> 
feenix@James-Laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:450 errors:0 dropped:0 overruns:0 frame:0
TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:42306 (41.3 KB) TX bytes:13370 (13.0 KB)
Interrupt:17

eth0:avahi Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
inet addr:169.254.6.161 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8191 errors:0 dropped:0 overruns:0 frame:0
TX packets:8191 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1398266 (1.3 MB) TX bytes:1398266 (1.3 MB)

wlan0 Link encap:Ethernet HWaddr 00:90:4b:63:82:b2
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1184 errors:0 dropped:0 overruns:0 frame:0
TX packets:1164 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:869832 (849.4 KB) TX bytes:158031 (154.3 KB)
Interrupt:19 Memory:faffc000-faffe000


I have no idea whast this line is or what it does, I have never seen it befor in ifconfig



eth0:avahi Link encap:Ethernet HWaddr 00:0b:db:9d:04:98
inet addr:169.254.6.161 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:17

I'm not used to that either. Please post the output of "lshw -C network" and "cat /etc/network/interfaces"

However, your "temporary" sequence should be:
```

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```

And your /etc/modprobe.d/ndiswrapper file should contain:

```

#Hardy ssb/ndiswrapper workaround, added ...
install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

If it doesn't work after a reboot, then maybe the second modprobe (b44) isn't happening when ndiswrapper is loaded. We'll cross that bridge if we get there...

---

### Post by Feenix3k on 2008-05-22
b44 is for the wired card, it worked until I did the fix for wireless. b44 is in 8.04 when I installed it and wirer worked. Did the wireless fix and it wireless  works fine, but losted the wire connection in the process.


> **Jamie Jackson said:**
> I'm not used to that either. Please post the output of "lshw -C network" and "cat /etc/network/interfaces"

However, your "temporary" sequence should be:
```

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```

And your /etc/modprobe.d/ndiswrapper file should contain:

```

#Hardy ssb/ndiswrapper workaround, added ...
install ndiswrapper modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;
```

If it doesn't work after a reboot, then maybe the second modprobe (b44) isn't happening when ndiswrapper is loaded. We'll cross that bridge if we get there...

---

### Post by Jamie Jackson on 2008-05-23
> **Feenix3k said:**
> b44 is for the wired card, it worked until I did the fix for wireless. b44 is in 8.04 when I installed it and wirer worked. Did the wireless fix and it wireless  works fine, but losted the wire connection in the process.

I follow, but my last post offers a *modified* (tailored to your machine) version of the steps you've already tried. Please re-read my last post with that in mind. I've also asked for some additional information in the last post.

---

### Post by mringer on 2008-05-23
Success, thank you.

OUTLINE:

Dell Inspiron 1525 model PP29L

~/$ lspci | grep Broadcom
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
~/$ lspci -n | grep '14e4:43'
0b:00.0 0280: 14e4:4315 (rev 01)
~/$ lsb_release -d
Description:	Ubuntu 8.04
~/$ uname -mr
2.6.24-16-generic i686
~/$ 

Boot opts: none
Compile NDISWrapper: no

Step 2e

Hardy bug fix: no

(This may be affected by my previous failed attempts.) 

The unzip command failed, I unpacked the zip file with Thunar.

I could send more details (copious, boring) if asked.

---

### Post by housefly7k on 2008-05-24
* HP Pavillion dv2808ca
    * 04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

    * Wireless Chipset: 04:00.0 0280: 14e4:4328 (rev 03)
    * Ubuntu Version: Ubuntu 8.04
    * Kernel / Architecture: 2.6.24-16-generic i686
    * Any extra boot options you might be using : None
    * Whether or not you had to compile NDISWrapper : No
    * Which version of Step 2 you used : 2d
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not :No

Thanks alot for the howto, on hardy and it worked following 2d, WPA works thanks again.

---

### Post by u18b on 2008-05-24
It worked!!  Thanks!!!  Here's my report.

Brand new  laptop
HP Pavillion dv2840se, AMD 64 bit, 4 gig ram

wireless card
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
Special Note: Windows Vista Control Panel &#8211; System &#8211; Hardware Devices lists this as a bcm4321AG

Maybe it might be helpful to put in your document that how Linux identifies the device and how Windows identifies the device may (sometimes) not be the same?


wireless chipset
04:00.0 0280: 14e4:4328 (rev 03)


Ubuntu version:  8.04 

kernel/architecture:     2.6.24-16-generic i686  /  32 version  

boot options: none

Compiling?  Nope.  Everything worked.  1st try.

Version of step 2:  version D

If on Hardy, use bug fix?  Did not need it.

Comments:  

Pros:  THANK YOU!!!   it worked on the FIRST try!!!  Whohoooo!!!!


Cons for improvement:

Since I'm a newbie, I would have like a warning from you at this step toward the end.

When I loaded this:   &#8220;lshw -C network&#8221;      
terminal said this ominous thing:  

&#8220;WARNING: you should run this program as super-user.&#8221;

My first thought was UhOh- did I do something wrong?

and then it did its thing.  I think you should edit the directions to warn users.  Say something like, &#8220;You will get a warning message, but don't worry about it.  Just wait for the report.&#8221;


I also felt lost by that report for a bit.  The directions say:
&#8220;If the wireless interface says "module=ssb" instead of "module=ndiswrapper", you've got a problem...&#8221;

But look at what came out of my terminal:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:4e:e7:e9
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.194 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 03
       serial: 00:1a:73:fa:6c:c6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


WOW!  That's a lot of info.  I wasn't even sure if I had done the correct thing.  And I wasn't sure at first where to look.  I assume that the info I'm supposed to find in all that mess is at the very long last line (that I assume wraps around) and starts out    CONFIGURATION:

Is that correct?  And the part I'm looking for is the part toward the end that says &#8220;module=ndiswrapper&#8221;
I assumed that had to be it.

If these reports are all the same, maybe telling the user that there will be a long report and to look toward the very end.  That might have been helpful to a lost newbie like me.


Well anyway.  THANK YOU for being a lifesaver.  This brings me one step closer to abandoning Windows altogether.  I'm now wireless!

---

### Post by DarkW0lf on 2008-05-24
finally got to download the livecd and ran lsmod.

this is xubuntu AMD64
lsmod output:
```

Module                  Size  Used by
nls_iso8859_1           6656  1 
vfat                   16256  1 
fat                    60592  1 vfat
ipv6                  311720  10 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
powernow_k8            16608  1 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
container               6656  0 
dock                   12960  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
joydev                 15488  0 
snd_hda_intel         440408  1 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  23444  0 
i2c_nforce2             8704  0 
output                  5632  1 video
battery                16776  0 
button                 10912  0 
snd                    70856  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                46236  0 
serio_raw               9092  0 
ac                      8328  0 
wmi_acer               11076  0 
k8temp                  7680  0 
shpchp                 38172  0 
evdev                  14976  8 
i2c_core               28544  1 i2c_nforce2
soundcore              10400  1 snd
pci_hotplug            34608  1 shpchp
pcspkr                  4992  0 
squashfs               46352  1 
loop                   21508  2 
unionfs                87264  1 
nls_cp437               8320  2 
isofs                  39464  1 
ext3                  149264  0 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sr_mod                 20132  1 
cdrom                  41512  1 sr_mod
sg                     41880  0 
sd_mod                 33280  4 
usbhid                 35168  0 
hid                    44992  1 usbhid
usb_storage            82496  1 
libusual               23520  1 usb_storage
pata_amd               16772  1 
sata_nv                31624  1 
pata_acpi               9856  0 
ata_generic             9988  0 
forcedeth              55564  0 
ehci_hcd               41996  0 
ohci_hcd               27524  0 
libata                176304  4 pata_amd,sata_nv,pata_acpi,ata_generic
scsi_mod              178488  5 sr_mod,sg,sd_mod,usb_storage,libata
usbcore               169904  6 usbhid,usb_storage,libusual,ehci_hcd,ohci_hcd
ssb                    37252  0 
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  1 

```

livecd does not detect wlan by default.
did you want me to try loading ndiswrapper before running lsmod ?

---

### Post by claudio99 on 2008-05-25
The howto worked like a charm except for the part of making it permanent (8.04 ssb bug).

My solution is to ditch the ndiswrapper init code and remove and load the modules from rc.local (with some added tests). More info [here]("http://nxadm.wordpress.com/2008/05/21/broadcom-wifi-bcm4312-speedup-on-ubuntu-804-on-a-hp-nc6320-laptop/").

claudio@brisbane:~/Downloads$ uname -a
Linux brisbane 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

claudio@brisbane:~/Downloads$ lspci |grep BCM4312
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

claudio@brisbane:~/Downloads$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: xxxxxxxxxxxxxxxxxx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 ip=192.168.1.101 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by larrycz on 2008-05-25
Thanks a million! Works perfect

---

### Post by Jamie Jackson on 2008-05-25
> **mringer said:**
> 
The unzip command failed, I unpacked the zip file with Thunar.

I could send more details (copious, boring) if asked.

I'm assuming you're on Xubuntu? In any case, how did the unzip fail? I just tried it from an Xubuntu box and it worked for me, but maybe there's something different about my environment.

---

### Post by Jamie Jackson on 2008-05-25
> **u18b said:**
> Cons for improvement: ...

Feedback incorporated. Thanks for the details.

---

### Post by Jamie Jackson on 2008-05-25
> **DarkW0lf said:**
> ssb                    37252  0[code]

livecd does not detect wlan by default.
did you want me to try loading ndiswrapper before running lsmod ?

Is this "virgin" output? In other words, is this from the live cd on a fresh boot, without trying to configure anything? If so, you'll have a very simple hardy fix, since there aren't any other modules depending on ssb.

Your temporary fix (issued at the command line) will look like this:
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb

And your "persistent" solution should be this:
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;' | sudo tee -a /etc/modprobe.d/ndiswrapper

---

### Post by Jamie Jackson on 2008-05-25
I just noticed that a well-intentioned, but confused, user had scrambled the /etc/modprobe.d/ndiswrapper configuring line in the wiki. I've changed it back.

---

### Post by tmac503 on 2008-05-25
This guide worked for me which was really exciting after the painful hours of trying other random crap. I did have to use the hardy work around but it seemed to work fine. However, I just hibernated my computer and not only did it undo the workaround but I can't do the work around again to fix it. This is the error I hit:

```
sudo modprobe ndiswrapper
sh: mdoprobe: not found
```

This would be a lot stranger had I actually typoed modprobe in the first line but I didn't. I've checked this multiple times.
Strangely enough, "sudo modprobe ssb" and "sudo modprobe b44" actually do work.

thanks for the great guide and thanks in advance to anyone who can help me with this

edit:
i gave up and reinstalled everything and tried again. it works now.

---

### Post by swordsmith on 2008-05-26
> **Jamie Jackson said:**
> *Edit: Since I originally posted this I've also added support for other devices, so it now supports the BCM4306, BCM4310, BCM4311, BCM4312, BCM4318, and BCM4328*
*Edit 2: Update (Oct 2007): Gutsy Gibbon (*Ubuntu 7.10) has native support (via the restricted driver manager) that actually works, so this guide isn't strictly necessary for Gutsy. However, Gutsy's native support isn't capable of quite the same bandwidth as this ndiswrapper solution. Further, it doesn't seem to work for everyone. Fortunately, this guide also appears to be compatible with Gutsy.*
***Edit 3: Update (Apr 26 2008): This howto works with Hardy Heron (*Ubuntu 8.04) for many users. I've added some Hardy-specific commands that workaround an outstanding (ssb) module loading bug. Note, this howto still doesn't work for some Hardy users, for reasons we haven't fully hashed out yet, but almost certainly related to the ssb issue. Hardy users, please refrain from voting until this is worked out, but feel free to make thread posts.***

I created a quick howto for myself, since I've had to install this card a few times. This howto works well for fresh installs of Feisty (and Gutsy, and Hardy), and requires no compiled packages. (This means simple apt-get installs only for most people, but there are ndiswrapper compilation instructions for those who need it.)

[BCM43xx HowTo.]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

This should take less than 5 minutes.

Please report your results here or on the wiki. Others benefit from detailed feedback, so you get bonus points if you provide all of the following:

**HARDY Users, Before Following the Wiki**: (I need this to try to develop a module-reloading script, since Hardy users ideally should use a custom module reloader for their particular hardware.)
[LIST]
[*]Modules and Dependencies: [COLOR="DarkRed"][FONT="Courier New"]lsmod[/FONT][/COLOR]
[/LIST]

**All Users, After Following the Wiki** 
[LIST]
[*]Machine Brand and Model
[*]Wireless Brand and Model (please post the whole line): [COLOR="DarkRed"][FONT="Courier New"]lspci | grep Broadcom[/FONT][/COLOR]
[*]Wireless Chipset: [COLOR="DarkRed"][FONT="Courier New"]lspci -n | grep '14e4:43'[/FONT][/COLOR]
[*]Ubuntu Version:  [COLOR="DarkRed"][FONT="Courier New"]lsb_release -d[/FONT][/COLOR]
[*]Kernel / Architecture:  [COLOR="DarkRed"][FONT="Courier New"]uname -mr[/FONT][/COLOR]
[*]Any *extra* boot options you might be using (e.g., noacpi, irqpoll, etc.)
[*]Whether or not you had to compile NDISWrapper
[*]Which version of Step 2 you used
[*]If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not
[/LIST]

Good luck,
Jamie

Brand and Model: Dell Latitude D830
'lspci | grep Broadcom' output: 09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

`lspci -n | grep '14e4:43' ` output: 0c:00.0 0280: 14e4:4311 (rev 01)

lsb_release -d: Description: Ubuntu 8.04

uname -mr: 2.6.24-16-generic i686

did not compile ndiswrapper

I used 2a first, then used 2b without using the method in [http://ubuntuforums.org/showpost.php?p=3767216&postcount=273](http://ubuntuforums.org/showpost.php?p=3767216&postcount=273)
Didnt work, so I used the switching method in that link, tried 2a, didnt work. Switched to 2b, didnt work. And then I used 2a again, finally i can connect to wireless, but it's only under the roaming mode. Whenever I manually configure it to connect to a specific network, wireless dies, even though the light still lights up.
Now I have not rebooted yet (I did the permanent workaround steps already). Going to report what happens after that...

____________________________________Edit__________________________________
After rebooting, my computer successfully connected to the wireless network, under roaming mode. In network settings, manual configuration, I can see all the different networks available. However, after setting the DHCP settings in manual configuration, wireless no longer connects.
Any ideas?

---

### Post by yurib on 2008-05-26
wow, finally !
its been about a month since i installed ubuntu and didnt have wireless until now. i really loved it but was baout to give up since i tried every guide/howto i could find and nothing worked...
at last i decided to give it one last chance after a fresh install and violla... works like a charm :D
thanks to everyone who's been helping on this thread and on the wiki ! thanks a lot!

my system details:
hp dv408nr winxp and hardy dual boot bcm94311 rev 02. used step 2a and hardy bug fix v0.3

---

### Post by daviescr on 2008-05-26
thanks Jamoe,
I ended up compiling and trying every method under the sun, but in the end reading through your posts help me realize I had everything correct on the laptop. My error was that I use mac filtering on my router and entered the wrong mac address. I put in the eth0 address... whoops



router:
linksys WRT54G   


laptop
HP Pavilion DV6000 64bit
ubuntu 7.04 amd64

afterburner both ways didn't make a difference

---

### Post by Ubhuti on 2008-05-26
Success, without having to compile ndiswrapper!  Thank you.  Almost thought of junking the damn wireless network card!

---

### Post by Jamie Jackson on 2008-05-27
> **swordsmith said:**
> Brand and Model: Dell Latitude D830
'lspci | grep Broadcom' output: 09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

`lspci -n | grep '14e4:43' ` output: 0c:00.0 0280: 14e4:4311 (rev 01)

lsb_release -d: Description: Ubuntu 8.04

uname -mr: 2.6.24-16-generic i686

did not compile ndiswrapper

I used 2a first, then used 2b without using the method in [http://ubuntuforums.org/showpost.php?p=3767216&postcount=273](http://ubuntuforums.org/showpost.php?p=3767216&postcount=273)
Didnt work, so I used the switching method in that link, tried 2a, didnt work. Switched to 2b, didnt work. And then I used 2a again, finally i can connect to wireless, but it's only under the roaming mode. Whenever I manually configure it to connect to a specific network, wireless dies, even though the light still lights up.
Now I have not rebooted yet (I did the permanent workaround steps already). Going to report what happens after that...

____________________________________Edit__________________________________
After rebooting, my computer successfully connected to the wireless network, under roaming mode. In network settings, manual configuration, I can see all the different networks available. However, after setting the DHCP settings in manual configuration, wireless no longer connects.
Any ideas?

If you want to roam *and* be able to set static IP, etc., you might want to try wicd. I don't think network-manager is as configurable.

For now, you'll probably want to go in and edit /etc/network/interfaces, and comment out all lines that don't have to do with the "lo" interface. I don't think that manual configurations play nice with network-manager.

---

### Post by TheNatealator on 2008-05-29
Isn't working for me so far (and this is after giving up on the b43 method). When I connect to my network, the loading icon appears, but after a short time, it gives up and returns to my wired connection. I am 5 ft from the router.

The problem appears to be that I do not have ndiswrapper properly installed, because modprobe can't find it...

Machine: Dell Inspiron 1501
Wireless: 05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
Ubuntu: 8.04
Kernel: 2.6.25.4 x86_64 (self-compiled from kernelcheck-1.0.5)

Steps taken (with only the erroneous outputs, sorry it's still so long!)
```
:~$ # Step 1
:~$ echo 'blacklist bcm43xx'|sudo tee -a /etc/modprobe.d/blacklist
:~$ sudo apt-get install ndiswrapper-utils-1.9
:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
:~/bcm43xx$ # Step 2a
:~/bcm43xx$ sudo apt-get install cabextract
:~/bcm43xx$ cabextract sp34152.exe
:~/bcm43xx$ wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
:~/bcm43xx$ cabextract sp34152.exe sp34152.exe: library not compiled to support large files.
:~/bcm43xx$ # step 3
:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
:~/bcm43xx$ bcmwl5.inf
:~/bcm43xx$ ndiswrapper -l
:~/bcm43xx$ sudo depmod -a
:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
:~/bcm43xx$ sudo ndiswrapper -m
:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
:~/bcm43xx$ # Rolling back steps 2a and 3 to try 2b
:~/bcm43xx$ sudo modprobe -r ndiswrapper
FATAL: Module ndiswrapper not found.
:~/bcm43xx$ sudo apt-get install ndiswrapper-utils-1.9
:~/bcm43xx$ sudo modprobe -r ndiswrapper
ndiswrapper-utils-1.9 is already the newest version.
:~/bcm43xx$ sudo ndiswrapper -r bcmwl5
:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
:~/bcm43xx$ sudo ndiswrapper -r bcmwl5
:~/bcm43xx$ # Step 2b
:~/bcm43xx$ wget ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe
:~/bcm43xx$ cabextract sp33008.exe 
:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
:~/bcm43xx$ ndiswrapper -l
:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

---

### Post by Jamie Jackson on 2008-05-29
> **TheNatealator said:**
> Isn't working for me so far (and this is after giving up on the b43 method). When I connect to my network, the loading icon appears, but after a short time, it gives up and returns to my wired connection. I am 5 ft from the router.

The problem appears to be that I do not have ndiswrapper properly installed, because modprobe can't find it...

Machine: Dell Inspiron 1501
Wireless: 05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
Ubuntu: 8.04
Kernel: 2.6.25.4 x86_64 (self-compiled from kernelcheck-1.0.5)

Steps taken (with only the erroneous outputs, sorry it's still so long!)
```
:~$ # Step 1
:~$ echo 'blacklist bcm43xx'|sudo tee -a /etc/modprobe.d/blacklist
:~$ sudo apt-get install ndiswrapper-utils-1.9
:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
:~/bcm43xx$ # Step 2a
:~/bcm43xx$ sudo apt-get install cabextract
:~/bcm43xx$ cabextract sp34152.exe
:~/bcm43xx$ wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
:~/bcm43xx$ cabextract sp34152.exe sp34152.exe: library not compiled to support large files.
:~/bcm43xx$ # step 3
:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
:~/bcm43xx$ bcmwl5.inf
:~/bcm43xx$ ndiswrapper -l
:~/bcm43xx$ sudo depmod -a
:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
:~/bcm43xx$ sudo ndiswrapper -m
:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
:~/bcm43xx$ # Rolling back steps 2a and 3 to try 2b
:~/bcm43xx$ sudo modprobe -r ndiswrapper
FATAL: Module ndiswrapper not found.
:~/bcm43xx$ sudo apt-get install ndiswrapper-utils-1.9
:~/bcm43xx$ sudo modprobe -r ndiswrapper
ndiswrapper-utils-1.9 is already the newest version.
:~/bcm43xx$ sudo ndiswrapper -r bcmwl5
:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
:~/bcm43xx$ sudo ndiswrapper -r bcmwl5
:~/bcm43xx$ # Step 2b
:~/bcm43xx$ wget ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe
:~/bcm43xx$ cabextract sp33008.exe 
:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
:~/bcm43xx$ ndiswrapper -l
:~/bcm43xx$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```

What does "ndiswrapper -v" yield?

Also, what happened when you ran "sudo apt-get install ndiswrapper-utils-1.9"? (You can run it again.) [Update: I see that you did run it again, and it says you've already installed it.]

I suppose there could be issues with the packaged version of ndiswrapper against your custom kernel, but we'll see what the answers to the above show...

[Update: I'm more suspicious now that the packaged ndiswrapper conflicts with your kernel, but I could be wrong. You can try following the ndiswrapper *compilation* instructions on the Wiki to test this theory.]

---

### Post by DarkW0lf on 2008-05-31
> **Jamie Jackson said:**
> Is this "virgin" output? 

Yes.

[QUOTE=Jamie Jackson]
If so, you'll have a very simple hardy fix, since there aren't any other modules depending on ssb.[/QUOTE]

Cool, I'll try it out.

[QUOTE=Jamie Jackson]
Your temporary fix (issued at the command line) will look like this:
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
[/QUOTE]

I'll try the liveCD again and see if the temp fix works before upgrading (And make sure VirtualBox works, argh I have two Hardy issues).

[QUOTE=Jamie Jackson]
And your "persistent" solution should be this:
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;' | sudo tee -a /etc/modprobe.d/ndiswrapper[/QUOTE]

Single line right ?

---

### Post by Jamie Jackson on 2008-06-01
> **DarkW0lf said:**
> Yes.



Cool, I'll try it out.



I'll try the liveCD again and see if the temp fix works before upgrading (And make sure VirtualBox works, argh I have two Hardy issues).



Single line right ?

Yes, single line. 

I've got the VirtualBox blues, too. It worked fine in the last kernel (2.6.24-16-generic), but the recent kernel upgrade (2.6.24-17-generic) killed it. Last week, I was reading a bug where the vbox modules had supposedly been added to the "proposed" repos, but I wasn't seeing it there.

---

### Post by bytebuster on 2008-06-02
Acer TravelMate 5520-5283
dmidecode -- 
Phoenix Technologies LTD V1.16 11/14/2007
Acer TravelMate 5520 0100           
Opteron AMD Engineering Samplenology 1900 MHz

lspci --- networking
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 15)
05:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

uname -asrm
Linux TM5520-laptop 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

Ubuntu release 8.04 i386 [on AMDx64 hardware]

steps followed
  sudo apt-get remove bcm43xx-fwcutter
  sudo vi  /etc/modprobe.d/blacklist
  sudo lspci | grep -i network
  sudo apt-get remove --purge b43-fwcutter
  sudo apt-get install b43-fwcutter
  sudo rmmod b44
  sudo rmmod b43
  sudo rmmod ssb
  sudo rmmod ndiswrapper
  iwconfig 
  lspci -nn | grep Net
---------------------------------------------------------------
    mkdir 4310
    cd 4310 
   wget [http://myspamb8.googlepages.com/R174291-pruned.zip](http://myspamb8.googlepages.com/R174291-pruned.zip)
    unzip R174291-pruned.zip 
    sudo apt-get install ndiswrapper-utils-1.9
    sudo ndiswrapper -i bcmwl5.inf 
    ndiswrapper -l
   sudo modprobe ndiswrapper 
   sudo cp /etc/network/interfaces /etc/network/interfaces.orig
   echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
   sudo ndiswrapper -m
   echo 'ndiswrapper' | sudo tee -a /etc/modules
   echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
---------------------------------------------------------------   
iwconfig 
   ifconfig 
   sudo lshw -C NETWORK
   iwlist scan

Yippe except I don't want ndiswrapper :-( 
I want raw supported bcm4312 
Actual Hardware Sticker 
Broadcom BCM94312MCG    [hardware reports BCM4310_rev01]

---

### Post by Jamie Jackson on 2008-06-02
> **bytebuster said:**
> Yippe except I don't want ndiswrapper :-( 
I want raw supported bcm4312

I hear you. Bottom line is we should boycott Broadcom. I know that this is hard, since so many resellers use this brand; however, even after all this clever NDISWrapper stuff, a $10 Ativa (Belkin clone) USB WiFi dongle blows it out of the water in terms of:
[LIST]
[*]Reliability (connects faster, and always does so *the first time*)
[*]Seemingly more accurate reporting of AP signal strength
[*]Connection distance/quality
[*]100% Plug-and-play
[/LIST]

---

### Post by hollowhead on 2008-06-03
Jamie thankyou for the effort you have put in with very clear instructions unfortunately this has has not worked for me.  Do you really think I need to compile ndiswrapper?  I also tried this [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) which is where I am at the moment.  No success.

HP compaq nx6110
lspci | grep Broadcom
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

lspci -n | grep '14e4:43'
 02:04.0 0280: 14e4:4318 (rev 02)

lsb_release -d
Description:	Ubuntu 8.04

 uname -mr
2.6.24-17-386 i686
noacpi

initially 2a then 2c

Neil

---

### Post by DarkW0lf on 2008-06-03
Jamie all your steps upto the Hardy fix has worked. (The default blacklist from Hardy includes bcm43xx)

Except when I try to reload the modules, I get a 'cannot resolve host' error. Something about my laptops hostname not resolving to IP or something.

I have been having that problem with 7.10, which I don't understand.

---

### Post by Jamie Jackson on 2008-06-03
> **hollowhead said:**
> Jamie thankyou for the effort you have put in with very clear instructions unfortunately this has has not worked for me.  Do you really think I need to compile ndiswrapper?  I also tried this [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560) which is where I am at the moment.  No success.

HP compaq nx6110
lspci | grep Broadcom
02:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

lspci -n | grep '14e4:43'
 02:04.0 0280: 14e4:4318 (rev 02)

lsb_release -d
Description:	Ubuntu 8.04

 uname -mr
2.6.24-17-386 i686
noacpi

initially 2a then 2c

Neil

I don't think you'll need to compile ndiswrapper. Please use 2a again, then:

Open up /etc/modprobe.d/ndiswrapper (gksu gedit /etc/modprobe.d/ndiswrapper) and comment out (put a "#" before) the line starting with "install ndiswrapper..."

Then reboot, and post the output of lsmod. Let's figure out exactly what Hardy/ssb workaround sequence *your* machine needs, and go from there.

---

### Post by Jamie Jackson on 2008-06-03
> **DarkW0lf said:**
> Jamie all your steps upto the Hardy fix has worked. (The default blacklist from Hardy includes bcm43xx)

Except when I try to reload the modules, I get a 'cannot resolve host' error. Something about my laptops hostname not resolving to IP or something.

I have been having that problem with 7.10, which I don't understand.

Please clarify: Can you hit the Internet over wireless, after having done these things?

I'm not clear whether, in addition to the "cannot resolve host" message, you are also unable to use the wireless.

---

### Post by Roberto_Lapuente on 2008-06-04
It worked perfectly, thanks alot!
my computer is a compaq presario v3000
my broadcom model is BCM4311 (Rev 02) 
and i did not have to use the hardy bug fix

---

### Post by maxime-olivier on 2008-06-04
For a Compaq Presario R4000 (R4145 EA) with a Broadcom Wlan 4318 - 54g Air Force One WIFI, 

This How to > 

_[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)_

works just perfectly > I have Kubuntu 8.04 Hardy Heron

I have followed the method with Ndiswrapper, the step 1), the step 2 a) and step 3)

I ended with the step called "Hardy Bug Fix" :

Inside this step, the "Trying it temporarily" and the "Making it Permanent" works perfectly (and obviously after a re-boot) with the method :

 Modifying /etc/modprobe.d/ndiswrapper,
             Version 0.3.

After that, the wireless card scan is working, and it's okay to connect Wireless Networks with WPA key or WEP key (the blue led of the wifi button is on ! )


[COLOR="Black"]Thank You so Much Jamie Jackson ![/COLOR]

> I'm a pure newbie in computer and almost completely with the GNU/linux system even if I'm 26-years old lol

I totally removed my previous OS (WinXP) when installing Kubuntu 8.04 by accident and after some things I did (like upgrade my KDE to KDE 4.0 and remove it) my entire OS just didn't restart.
So I had to install it again and to reconfigure again my Wifi.

Thanks Again and regards from France, Paris.

---

### Post by hollowhead on 2008-06-04
Thnkas for your help Jamie it is much appreciated whatever happens...

Here is the contents of /etc/modprobe.d/ndiswrapper does it matter that everything seems to be on the same line with ; in between?

Hardy ssb/ndiswrapper workaround, added Wed Jun 4 11:59:12 BST 2008 
#install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

Two I have not altered the permissions for this file I assume that is correct?

Three output of lsmod its quite long...  Ta.  NH



lsmod
Module                  Size  Used by
ipv6                  255044  8 
af_packet              21636  2 
binfmt_misc            11272  1 
i915                   31360  2 
drm                    80788  3 i915
rfcomm                 39188  2 
l2cap                  23300  13 rfcomm
bluetooth              56964  4 rfcomm,l2cap
rfkill_input            4608  0 
ppdev                   9348  0 
snd_atiixp_modem       16008  0 
snd_via82xx_modem      14984  0 
snd_intel8x0m          17804  5 
cpufreq_userspace       4120  0 
cpufreq_stats           5124  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  0 
freq_table              4484  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     7200  0 
sbs                    14216  0 
sbshc                   6784  1 sbs
dock                   10124  0 
iptable_filter          2944  0 
ip_tables              13000  1 iptable_filter
x_tables               14852  1 ip_tables
ndiswrapper           185104  0 
sbp2                   22920  0 
parport_pc             35108  0 
lp                     11332  0 
parport                35912  3 ppdev,parport_pc,lp
serial_cs              22276  1 
joydev                 11840  0 
pcmcia                 39852  1 serial_cs
arc4                    2048  2 
ecb                     3584  2 
blkcipher               7428  1 ecb
b43                   113952  0 
rfkill                  7568  26 rfkill_input,b43
mac80211              162708  1 b43
cfg80211               14088  1 mac80211
led_class               5124  1 b43
input_polldev           5000  1 b43
container               4736  0 
video                  18832  0 
output                  3712  1 video
snd_intel8x0           33948  3 
psmouse                39056  0 
snd_ac97_codec         99876  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
ac97_bus                2176  1 snd_ac97_codec
serio_raw               7044  0 
snd_pcm_oss            40736  0 
snd_mixer_oss          16896  1 snd_pcm_oss
yenta_socket           26380  3 
rsrc_nonstatic         12800  1 yenta_socket
snd_pcm                75400  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia_core            39440  4 serial_cs,pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy           3972  0 
battery                13316  0 
wmi_acer                8748  0 
ac                      6020  0 
button                  8336  0 
snd_seq_oss            34048  0 
snd_seq_midi            8480  0 
snd_rawmidi            24608  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51152  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23556  2 snd_pcm,snd_seq
snd_seq_device          8588  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
intel_agp              24596  1 
snd                    54692  28 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
agpgart                33328  3 drm,intel_agp
snd_page_alloc         10504  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
iTCO_wdt               11808  0 
iTCO_vendor_support     3972  1 iTCO_wdt
evdev                  11776  29 
pcspkr                  3072  0 
rtc                    13212  0 
ext3                  132872  1 
jbd                    43028  1 ext3
mbcache                 8192  1 ext3
usbhid                 30592  0 
hid                    36480  1 usbhid
sg                     36256  0 
sr_mod                 16804  0 
cdrom                  36512  1 sr_mod
sd_mod                 29584  2 
ata_piix               18692  1 
pata_acpi               7424  0 
b44                    27024  0 
ata_generic             7428  0 
libata                159600  3 ata_piix,pata_acpi,ata_generic
ohci1394               32688  0 
scsi_mod              151180  5 sbp2,sg,sr_mod,sd_mod,libata
mii                     5504  1 b44
ieee1394               92216  2 sbp2,ohci1394
ssb                    31236  2 b43,b44
ehci_hcd               36748  0 
uhci_hcd               25616  0 
usbcore               143724  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
raid10                 24192  0 
raid456               125712  0 
async_xor               4096  1 raid456
async_memcpy            2816  1 raid456
async_tx                7496  3 raid456,async_xor,async_memcpy
xor                    15240  2 raid456,async_xor
raid1                  24192  0 
raid0                   8320  0 
multipath               8448  0 
linear                  6272  0 
md_mod                 79508  6 raid10,raid456,raid1,raid0,multipath,linear
dm_mirror              22912  0 
dm_snapshot            18592  0 
dm_mod                 60484  2 dm_mirror,dm_snapshot
thermal                15772  0 
processor              28080  2 thermal
fan                     4740  0 
fbcon                  41888  0 
tileblit                2560  1 fbcon
font                    8576  1 fbcon
bitblit                 5888  1 fbcon
softcursor              2176  1 bitblit
fuse                   48404  1

---

### Post by Jamie Jackson on 2008-06-04
> **hollowhead said:**
> Thnkas for your help Jamie it is much appreciated whatever happens...

Here is the contents of /etc/modprobe.d/ndiswrapper does it matter that everything seems to be on the same line with ; in between?

Hardy ssb/ndiswrapper workaround, added Wed Jun 4 11:59:12 BST 2008 
#install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

Two I have not altered the permissions for this file I assume that is correct?

Three output of lsmod its quite long...  Ta.  NH
...


No prob...

Next, try these from the command line, and let me know if any of them return any messages to you.
```

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```

Can you scan for networks now? If not, please post the output of "lshw -C network"

---

### Post by johnthebillionaire on 2008-06-05
Machine Brand and Model:

HP compaq presario V3633AU aka Presario V3000 range

lspci | grep Broadcom:
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

lspci -n | grep '14e4:43'
04:00.0 0280: 14e4:4311 (rev 02)


Description:	Ubuntu 8.04

2.6.24-16-generic x86_64

No need to Compile ndiswrapper

used  Step 2a: sp34152 Driver Download/Extraction

I had to apply the bugfix work around

---

### Post by DarkW0lf on 2008-06-05
> **Jamie Jackson said:**
> Please clarify: Can you hit the Internet over wireless, after having done these things?


No, I can't execute the rmmod commands.

[QUOTE=Jamie Jackson]
I'm not clear whether, in addition to the "cannot resolve host" message, you are also unable to use the wireless.[/QUOTE]

Yeah, I am at the point where I need to change the order the mods are loaded in but when I try I get the message about not being able to resolve the local host.

XFCE is acting flaky or something, it can't find an IP on boot (which makes since as there is no network available then). I never tried to reload the modules in 7.10 so I don't know if this same issue was there back then.

I got something screwed up in configuration somewhere, I just don't know what.

---

### Post by Jamie Jackson on 2008-06-05
> **DarkW0lf said:**
> No, I can't execute the rmmod commands.



Yeah, I am at the point where I need to change the order the mods are loaded in but when I try I get the message about not being able to resolve the local host.

XFCE is acting flaky or something, it can't find an IP on boot (which makes since as there is no network available then). I never tried to reload the modules in 7.10 so I don't know if this same issue was there back then.

I got something screwed up in configuration somewhere, I just don't know what.

Please post the output of [FONT="Courier New"]cat /etc/network/interfaces[/FONT]

---

### Post by hollowhead on 2008-06-06
unhashed /etc//modprobe.d/ndiswrapper

then rebooted

sudo rmmod b43
[sudo] password for nrh1: 
ERROR: Module b43 does not exist in /proc/modules

all others no message no wireless either

lshw -C network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:65:71:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:e5:b9:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.2 latency=64 module=ssb multicast=yes

Ta.  NH

---

### Post by JackSpratt on 2008-06-07
Just giving feedback about the community doc that points to this thread.

Thank You Thank You Thank You Thank You Thank You.

Thank You.

I tried for many hours (don't want to count them) to get my ASUS WL-138G V2 wireless card (Broadcom 4318) to work after upgrading to 8.04 from 7.10 and could not. I could "see" the networks around me and their broadcast strength, whether they were "locked" or not, I just couldn't connect to any of them.(Very strange)

The final solution was ndiswrapper, which I installed by adding the "ndisgtk" module in synaptic package manager (system/admin/synaptic package manager) and then adding the windows xp driver for my ASUS WL-138G V2 in system/admin/windows wireless drivers.

Then the magic..... I performed the magic code in terminal,

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008


and BINGO, the card worked for the first time in 8.04!!! (I had tried once before but had become too frustrated and reinstalled 7.10)

Now, this is temporary and does not survive a reboot, so I tried the 0.3 solution first and system would hand as it tried to boot up (waited 3 or 4 minutes). If I forced another reboot it would start up, but I would be back to ssb in *lshw -C network*.

Same with 0.2 solution.

Tried the 0.1 solution and it now survives reboot.

echo -e '\n#hardy ssb bug-fix\nrmod b43\nrmod b44\nrmod b43legacy\nrmod ssb\nrmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local

I couldn't be happier and couldn't care less that the 0.1 solution is obsolete.

Thank you once again.

---

### Post by djwild on 2008-06-08
WPA Failed using Broadcom 4328 (rev 03). Works fine without encryption.

I have a Dell Vostro 1510 Laptop with the Dell 1505 wireless mini-card (bcm4328). I have tried everything but it just won't connect. It is exactly the same problem as a few of the guys here: everything works just fine if the wireless network is not encrypted. When WPA is enabled however it will not connect. I can see the AP and it is correctly recognized as using encryption but if I select it, network manager just keeps on spinning and nothing ... Recompiling ndiswrapper didn't help, using different drivers didn't do the trick either.

What is interesting is that on some very rare occasions (2 times in the past 2 weeks) it did manage to connect and the connection was stable - I could browse pages and download stuff. I have no idea what was different then and why it failed after a restart.

I am using an almost plain hardy installation and reinstalled several times just because of the wireless not working.

If there is anything you have in mind that I can try I am more than happy to help. 

Here is all the info you requested.

Ubuntu version:
```
Description:	Ubuntu 8.04
2.6.24-18-generic i686
```

lspci:
```
06:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

lsmod:
```
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
uinput                 10240  2 
joydev                 13120  0 
snd_hda_intel         344728  3 
uvcvideo               58116  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
v4l2_common            18304  2 uvcvideo,videodev
usbhid                 31872  0 
hid                    38784  1 usbhid
nvidia               7825536  36 
snd_seq_dummy           4868  0 
r8168                  34704  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
i2c_core               24832  1 nvidia
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
battery                14212  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  8 
sdhci                  19076  0 
ac                      6916  0 
output                  4736  1 video
psmouse                40336  0 
mmc_core               51460  1 sdhci
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  9504  0 
wmi_acer                9644  0 
button                  9232  0 
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
pcspkr                  4224  0 
evdev                  13056  12 
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
ahci                   28420  2 
libata                159344  4 ata_generic,pata_acpi,ata_piix,ahci
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3
```

No extra boot options.

Tried both without and with recompiling diswrapper, no difference.

Used step 2d and also tried the winxp drivers from dell's site.

Not using the hardy bug fix since the ssb module is not in use on my system.

---

### Post by Jamie Jackson on 2008-06-08
> **hollowhead said:**
> unhashed /etc//modprobe.d/ndiswrapper

then rebooted

sudo rmmod b43
[sudo] password for nrh1: 
ERROR: Module b43 does not exist in /proc/modules

all others no message no wireless either

lshw -C network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:65:71:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:e5:b9:43
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.2 latency=64 module=ssb multicast=yes

Ta.  NH

Let me be more explicit.

1. Comment out the line in /etc/modprobe.d/ndiswrapper again.
2. Reboot
3. Run the following series again (noting any errors):
```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
```
4. Before doing *anything else*, see if you can scan for/connect to WiFi APs now. If you can't, post [FONT="Courier New"]lshw -C network[/FONT].

Last time, the ndiswrapper workaround was in effect before you did step 3 above, so modules were already removed. We want to try this stuff with the "hardy bug fix" disabled, hence the steps 1 and 2 above.

---

### Post by Jamie Jackson on 2008-06-08
> **djwild said:**
> WPA Failed using Broadcom 4328 (rev 03). Works fine without encryption.

I have a Dell Vostro 1510 Laptop with the Dell 1505 wireless mini-card (bcm4328). I have tried everything but it just won't connect. It is exactly the same problem as a few of the guys here: everything works just fine if the wireless network is not encrypted. When WPA is enabled however it will not connect. I can see the AP and it is correctly recognized as using encryption but if I select it, network manager just keeps on spinning and nothing ... Recompiling ndiswrapper didn't help, using different drivers didn't do the trick either.

What is interesting is that on some very rare occasions (2 times in the past 2 weeks) it did manage to connect and the connection was stable - I could browse pages and download stuff. I have no idea what was different then and why it failed after a restart.

I am using an almost plain hardy installation and reinstalled several times just because of the wireless not working.

If there is anything you have in mind that I can try I am more than happy to help. 

Here is all the info you requested.

Ubuntu version:
```
Description:	Ubuntu 8.04
2.6.24-18-generic i686
```

lspci:
```
06:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

lsmod:
```
ipv6                  267780  10 
af_packet              23812  2 
rfcomm                 41744  2 
l2cap                  25728  13 rfcomm
bluetooth              61156  4 rfcomm,l2cap
ppdev                  10372  0 
acpi_cpufreq           10796  2 
cpufreq_conservative     8712  0 
cpufreq_userspace       5284  0 
cpufreq_stats           7104  0 
cpufreq_ondemand        9740  1 
freq_table              5536  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
dock                   11280  0 
container               5632  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ndiswrapper           192920  0 
sbp2                   24072  0 
parport_pc             36260  0 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
uinput                 10240  2 
joydev                 13120  0 
snd_hda_intel         344728  3 
uvcvideo               58116  0 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
compat_ioctl32          2304  1 uvcvideo
videodev               29440  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
v4l2_common            18304  2 uvcvideo,videodev
usbhid                 31872  0 
hid                    38784  1 usbhid
nvidia               7825536  36 
snd_seq_dummy           4868  0 
r8168                  34704  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
i2c_core               24832  1 nvidia
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
battery                14212  0 
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
serio_raw               7940  0 
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  19856  8 
sdhci                  19076  0 
ac                      6916  0 
output                  4736  1 video
psmouse                40336  0 
mmc_core               51460  1 sdhci
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  9504  0 
wmi_acer                9644  0 
button                  9232  0 
intel_agp              25492  0 
agpgart                34760  2 nvidia,intel_agp
pcspkr                  4224  0 
evdev                  13056  12 
soundcore               8800  1 snd
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34452  0 
pci_hotplug            30880  1 shpchp
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
ata_generic             8324  0 
pata_acpi               8320  0 
sg                     36880  0 
sd_mod                 30720  3 
ata_piix               19588  0 
ahci                   28420  2 
libata                159344  4 ata_generic,pata_acpi,ata_piix,ahci
scsi_mod              151436  5 sbp2,sr_mod,sg,sd_mod,libata
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 ndiswrapper,uvcvideo,usbhid,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  4 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  3
```

No extra boot options.

Tried both without and with recompiling diswrapper, no difference.

Used step 2d and also tried the winxp drivers from dell's site.

Not using the hardy bug fix since the ssb module is not in use on my system.

I don't really have any strong suspicions here, but...

1. Do you still have WPA issues even when you're right next to the AP? (I have intermittent problems when signal strength is low, which trick me into thinking WPA won't authenticate, when it's actually a low signal problem.)
2. Try connecting to a neighbor's AP (even if it's encrypted). Sometimes, just trying to connect to another AP before connecting to my own will knock some sense into network-manager (assuming it's network-manager that's flaky in these cases).
3. What make/model router do you have?
4. What's the output of [FONT="Courier New"]cat /etc/default/wpasupplicant[/FONT]

---

### Post by DarkW0lf on 2008-06-08
cat /etc/network/interfaces output:
```

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```

---

### Post by djwild on 2008-06-08
Regarding Jamie's suggestions:

1. I am quite close to the AP so signal strength is not an issue.
2. Trying to connect to a neighbor didn't help.
3. The router is a D-Link 524 with the latest firmware update.
4. The /etc/default/wpasupplicant file does not exist now. It was created when I followed the HOWTO process and containded a single line ENABLED=0. Afterwards I removed it when it didn't fix my problem.

Despite that I managed to find a way to make my wireless card connect using WPA. However this requires manual configuration, manual startup and a lot of patience. Following this POST: [http://ubuntuforums.org/showthread.php?t=797414](http://ubuntuforums.org/showthread.php?t=797414)

I editted /etc/network/interfaces and /etc/wpa_supplicant/wpa_supplicant.conf. Now they contain the settings for my network.

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid Zero-net
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk <hex_key>
```

/etc/wpa_supplicant/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1
fast_reauth=1


network={
        ssid="Zero-Net"
        psk=<hex_key>
        scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        #pairwise=CCMP TKIP
        pairwise=CCMP
        #group=CCMP TKIP
        group=CCMP
        priority=5
        }
```

With the above mentioned settings I can get my wireless to connect after a fresh restart by using these commands in the terminal:
```
sudo killall wpa_supplicant
sudo wpa_supplicant -i wlan0 -Dwext -c /etc/wpa_supplicant/wpa_supplicant.conf -dd
```

The strange thing here is that every time I start wpa_supplicant I have to wait about 10 minutes and then the connection works. Before that it seems that it is not connected and nothing really changes in the terminal output. However after some time I am able to use the internet. Even now I am writing this message from that connection.

Here is the output of wpa_supplicant when it manages to connect. All these messages are displayed in a matter of seconds. Roughly 5-10 minutes after "EAPOL: startWhen --> 0" is displayed I can use my wireless connection.

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=1
fast_reauth=1
Line: 6 - start of a new network block
ssid - hexdump_ascii(len=8):
     5a 65 72 6f 2d 4e 65 74                           Zero-Net        
PSK - hexdump(len=32): [REMOVED]
scan_ssid=1 (0x1)
key_mgmt: 0x2
proto: 0x1
pairwise: 0x10
group: 0x10
priority=5 (0x5)
Priority group 5
   id=0 ssid='Zero-Net'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1f:3a:63:c5:c1
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=8):
     5a 65 72 6f 2d 4e 65 74                           Zero-Net        
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 1932 bytes of scan results (8 BSSes)
Scan results: 8
Selecting BSS from priority group 5
Try to find WPA-enabled AP
0: 00:1b:11:a8:03:dc ssid='Zero-Net' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1b:11:a8:03:dc ssid='Zero-Net'
Try to find non-WPA AP
Trying to associate with 00:1b:11:a8:03:dc (SSID='Zero-Net' freq=2462 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=87
AssocReq IE wireless event - hexdump(len=79): 00 08 5a 65 72 6f 2d 4e 65 74 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 01 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1b:11:a8:03:dc
Association info event
req_ies - hexdump(len=79): 00 08 5a 65 72 6f 2d 4e 65 74 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 01 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1b:11:a8:03:dc
No keys have been configured - skip key clearing
Associated with 00:1b:11:a8:03:dc
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 03 9b 6e e9 f7 d6 0e 85 9a 71 d6 37 60 09 22 af 3a 00 fe c0 e7 04 d6 a3 f7 d3 79 e7 ce e8 c6 58 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9b
  key_nonce - hexdump(len=32): 6e e9 f7 d6 0e 85 9a 71 d6 37 60 09 22 af 3a 00 fe c0 e7 04 d6 a3 f7 d3 79 e7 ce e8 c6 58 07 c3
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 03 9b 6e e9 f7 d6 0e 85 9a 71 d6 37 60 09 22 af 3a 00 fe c0 e7 04 d6 a3 f7 d3 79 e7 ce e8 c6 58 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1b:11:a8:03:dc (ver=2)
WPA: Renewed SNonce - hexdump(len=32): b5 83 89 67 29 11 47 32 e7 32 83 1d cd 44 9d 06 7a 98 67 90 c7 8d 7d 4f e8 22 01 1d c2 2e 2e f7
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 0a 00 10 00 00 00 00 00 00 03 9b b5 83 89 67 29 11 47 32 e7 32 83 1d cd 44 9d 06 7a 98 67 90 c7 8d 7d 4f e8 22 01 1d c2 2e 2e f7 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cf 31 fb 61 11 9c 7a f2 90 74 74 d0 a6 47 13 61 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 ca 00 10 00 00 00 00 00 00 03 9c 6e e9 f7 d6 0e 85 9a 71 d6 37 60 09 22 af 3a 00 fe c0 e7 04 d6 a3 f7 d3 79 e7 ce e8 c6 58 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2c 51 0f eb 3f 17 6e 55 3a 46 ce ab e9 84 e6 93 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=16 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9c
  key_nonce - hexdump(len=32): 6e e9 f7 d6 0e 85 9a 71 d6 37 60 09 22 af 3a 00 fe c0 e7 04 d6 a3 f7 d3 79 e7 ce e8 c6 58 07 c3
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 2c 51 0f eb 3f 17 6e 55 3a 46 ce ab e9 84 e6 93
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 ca 00 10 00 00 00 00 00 00 03 9c 6e e9 f7 d6 0e 85 9a 71 d6 37 60 09 22 af 3a 00 fe c0 e7 04 d6 a3 f7 d3 79 e7 ce e8 c6 58 07 c3 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 2c 51 0f eb 3f 17 6e 55 3a 46 ce ab e9 84 e6 93 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1b:11:a8:03:dc (ver=2)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 0a 00 10 00 00 00 00 00 00 03 9c 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 c3 48 57 7d a4 65 05 7b c5 c0 b7 1e ad 85 56 74 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=87
AssocReq IE wireless event - hexdump(len=79): 00 08 5a 65 72 6f 2d 4e 65 74 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 01 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1b:11:a8:03:dc
Association info event
req_ies - hexdump(len=79): 00 08 5a 65 72 6f 2d 4e 65 74 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 01 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
State: GROUP_HANDSHAKE -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:1b:11:a8:03:dc
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 03 9d c4 6b 0e 90 f8 21 61 62 19 19 b3 ae 30 40 41 ef 98 3c 84 ad f7 6f c6 5b 52 c9 7b f6 35 2a 74 aa 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9d
  key_nonce - hexdump(len=32): c4 6b 0e 90 f8 21 61 62 19 19 b3 ae 30 40 41 ef 98 3c 84 ad f7 6f c6 5b 52 c9 7b f6 35 2a 74 aa
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 03 9d c4 6b 0e 90 f8 21 61 62 19 19 b3 ae 30 40 41 ef 98 3c 84 ad f7 6f c6 5b 52 c9 7b f6 35 2a 74 aa 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1b:11:a8:03:dc (ver=2)
WPA: Renewed SNonce - hexdump(len=32): c4 cf f6 1b ce 28 8c 1b b2 5c ad e1 c8 78 9f c4 ca 7f b3 b1 9e 2a 8d 17 16 13 de f7 78 69 bd 74
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 0a 00 10 00 00 00 00 00 00 03 9d c4 cf f6 1b ce 28 8c 1b b2 5c ad e1 c8 78 9f c4 ca 7f b3 b1 9e 2a 8d 17 16 13 de f7 78 69 bd 74 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 89 05 cb 26 cc 5a c3 00 a2 35 97 08 37 c1 0c d8 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 ca 00 10 00 00 00 00 00 00 03 9e c4 6b 0e 90 f8 21 61 62 19 19 b3 ae 30 40 41 ef 98 3c 84 ad f7 6f c6 5b 52 c9 7b f6 35 2a 74 aa 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 d3 05 83 66 39 b9 37 36 12 bf 2d 14 6c a0 30 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=16 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9e
  key_nonce - hexdump(len=32): c4 6b 0e 90 f8 21 61 62 19 19 b3 ae 30 40 41 ef 98 3c 84 ad f7 6f c6 5b 52 c9 7b f6 35 2a 74 aa
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 12 d3 05 83 66 39 b9 37 36 12 bf 2d 14 6c a0 30
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 ca 00 10 00 00 00 00 00 00 03 9e c4 6b 0e 90 f8 21 61 62 19 19 b3 ae 30 40 41 ef 98 3c 84 ad f7 6f c6 5b 52 c9 7b f6 35 2a 74 aa 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 12 d3 05 83 66 39 b9 37 36 12 bf 2d 14 6c a0 30 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1b:11:a8:03:dc (ver=2)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 0a 00 10 00 00 00 00 00 00 03 9e 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 8b 5b 55 5d 50 b6 d2 6c 04 b7 77 9a 9c 62 32 a0 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=87
AssocReq IE wireless event - hexdump(len=79): 00 08 5a 65 72 6f 2d 4e 65 74 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 01 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=24
AssocResp IE wireless event - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1b:11:a8:03:dc
Association info event
req_ies - hexdump(len=79): 00 08 5a 65 72 6f 2d 4e 65 74 01 08 82 84 8b 96 24 30 48 6c 21 02 08 12 24 02 01 0e 32 04 0c 12 18 60 dd 09 00 10 18 02 00 10 01 00 00 dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00 dd 06 00 40 96 01 01 00
resp_ies - hexdump(len=16): 01 04 82 84 8b 96 32 08 0c 12 18 24 30 48 60 6c
WPA: set own WPA/RSN IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
State: GROUP_HANDSHAKE -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated with 00:1b:11:a8:03:dc
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 03 9f 12 00 49 20 f4 d0 29 ad a2 76 1e e7 a9 cd 1f ea e9 74 92 c9 89 5f 9e 8e a0 8e da 1f 4c 21 3b ce 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x8a (ver=2 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=16 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 9f
  key_nonce - hexdump(len=32): 12 00 49 20 f4 d0 29 ad a2 76 1e e7 a9 cd 1f ea e9 74 92 c9 89 5f 9e 8e a0 8e da 1f 4c 21 3b ce
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
WPA: RX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 00 8a 00 10 00 00 00 00 00 00 03 9f 12 00 49 20 f4 d0 29 ad a2 76 1e e7 a9 cd 1f ea e9 74 92 c9 89 5f 9e 8e a0 8e da 1f 4c 21 3b ce 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1b:11:a8:03:dc (ver=2)
WPA: Renewed SNonce - hexdump(len=32): 56 5e ba d8 46 32 0a b8 f1 9f 2d 8b 2a 02 0b d2 66 28 65 a7 95 51 12 98 fa 70 c8 a6 cd 6b 19 dd
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
WPA: Sending EAPOL-Key 2/4
WPA: TX EAPOL-Key - hexdump(len=125): 01 03 00 79 fe 01 0a 00 10 00 00 00 00 00 00 03 9f 56 5e ba d8 46 32 0a b8 f1 9f 2d 8b 2a 02 0b d2 66 28 65 a7 95 51 12 98 fa 70 c8 a6 cd 6b 19 dd 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d2 99 2f 9a 3e 7e 47 4f da 2f d8 c9 58 d4 54 5d 00 1a dd 18 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02 08 00
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 01 ca 00 10 00 00 00 00 00 00 03 a0 12 00 49 20 f4 d0 29 ad a2 76 1e e7 a9 cd 1f ea e9 74 92 c9 89 5f 9e 8e a0 8e da 1f 4c 21 3b ce 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d7 99 4e 81 62 c7 8a e1 a9 66 1a 46 72 c5 0b 8c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1ca (ver=2 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=16 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a0
  key_nonce - hexdump(len=32): 12 00 49 20 f4 d0 29 ad a2 76 1e e7 a9 cd 1f ea e9 74 92 c9 89 5f 9e 8e a0 8e da 1f 4c 21 3b ce
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): d7 99 4e 81 62 c7 8a e1 a9 66 1a 46 72 c5 0b 8c
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 01 ca 00 10 00 00 00 00 00 00 03 a0 12 00 49 20 f4 d0 29 ad a2 76 1e e7 a9 cd 1f ea e9 74 92 c9 89 5f 9e 8e a0 8e da 1f 4c 21 3b ce 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d7 99 4e 81 62 c7 8a e1 a9 66 1a 46 72 c5 0b 8c 00 18 dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1b:11:a8:03:dc (ver=2)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 04 01 00 00 50 f2 04 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 01 0a 00 10 00 00 00 00 00 00 03 a0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 e0 0a a5 7b 94 9d bf af f5 f7 50 07 9d 56 fe 4c 00 00
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=0 set_tx=1 seq_len=6 key_len=16
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 03 92 00 10 00 00 00 00 00 00 03 a1 41 cb 31 fa 30 5a 4f d6 93 24 04 04 f0 87 0e dd 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 57 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 59 ff 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cf cd 6e 0a e8 83 fe 4e 99 8a c6 55 5a 62 2e 2c 00 18 cb 3f fa ef 51 b8 a6 15 2e 07 6e f7 e6 93 ba 6c f6 6a 22 ed 2e c8 06 47
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x392 (ver=2 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=16 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a1
  key_nonce - hexdump(len=32): 41 cb 31 fa 30 5a 4f d6 93 24 04 04 f0 87 0e dd 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 57
  key_iv - hexdump(len=16): 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 59
  key_rsc - hexdump(len=8): ff 07 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): cf cd 6e 0a e8 83 fe 4e 99 8a c6 55 5a 62 2e 2c
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 03 92 00 10 00 00 00 00 00 00 03 a1 41 cb 31 fa 30 5a 4f d6 93 24 04 04 f0 87 0e dd 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 57 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 59 ff 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cf cd 6e 0a e8 83 fe 4e 99 8a c6 55 5a 62 2e 2c 00 18 cb 3f fa ef 51 b8 a6 15 2e 07 6e f7 e6 93 ba 6c f6 6a 22 ed 2e c8 06 47
WPA: RX message 1 of Group Key Handshake from 00:1b:11:a8:03:dc (ver=2)
State: GROUP_HANDSHAKE -> GROUP_HANDSHAKE
WPA: Group Key - hexdump(len=16): [REMOVED]
WPA: Installing GTK to the driver (keyidx=1 tx=0).
WPA: RSC - hexdump(len=6): ff 07 00 00 00 00
wpa_driver_wext_set_key: alg=3 key_idx=1 set_tx=0 seq_len=6 key_len=16
WPA: Sending EAPOL-Key 2/2
WPA: TX EAPOL-Key - hexdump(len=99): 01 03 00 5f fe 03 12 00 10 00 00 00 00 00 00 03 a1 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 d3 f0 a3 e7 3b af 43 65 14 27 e5 64 f1 c6 8e 51 00 00
WPA: Key negotiation completed with 00:1b:11:a8:03:dc [PTK=CCMP GTK=CCMP]
Cancelling authentication timeout
State: GROUP_HANDSHAKE -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1b:11:a8:03:dc completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
EAPOL: External notification - portValid=1
EAPOL: External notification - EAP success=1
EAPOL: SUPP_PAE entering state AUTHENTICATING
EAPOL: SUPP_BE entering state SUCCESS
EAP: EAP entering state DISABLED
EAPOL: SUPP_PAE entering state AUTHENTICATED
EAPOL: SUPP_BE entering state IDLE
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1b:11:a8:03:dc
RX EAPOL - hexdump(len=123): 01 03 00 77 fe 03 92 00 10 00 00 00 00 00 00 03 a1 41 cb 31 fa 30 5a 4f d6 93 24 04 04 f0 87 0e dd 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 57 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 59 ff 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cf cd 6e 0a e8 83 fe 4e 99 8a c6 55 5a 62 2e 2c 00 18 cb 3f fa ef 51 b8 a6 15 2e 07 6e f7 e6 93 ba 6c f6 6a 22 ed 2e c8 06 47
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x392 (ver=2 keyidx=1 rsvd=0 Group Ack MIC Secure)
  key_length=16 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 03 a1
  key_nonce - hexdump(len=32): 41 cb 31 fa 30 5a 4f d6 93 24 04 04 f0 87 0e dd 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 57
  key_iv - hexdump(len=16): 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 59
  key_rsc - hexdump(len=8): ff 07 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): cf cd 6e 0a e8 83 fe 4e 99 8a c6 55 5a 62 2e 2c
WPA: RX EAPOL-Key - hexdump(len=123): 01 03 00 77 fe 03 92 00 10 00 00 00 00 00 00 03 a1 41 cb 31 fa 30 5a 4f d6 93 24 04 04 f0 87 0e dd 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 57 3a 09 a4 d5 34 08 f5 1a 0e cd a6 ef 07 74 69 59 ff 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 cf cd 6e 0a e8 83 fe 4e 99 8a c6 55 5a 62 2e 2c 00 18 cb 3f fa ef 51 b8 a6 15 2e 07 6e f7 e6 93 ba 6c f6 6a 22 ed 2e c8 06 47
WPA: EAPOL-Key Replay Counter did not increase - dropping packet
EAPOL: startWhen --> 0
```


It is not really useful in this current state. Any ideas what could the problem be? Something else I might try?

---

### Post by Jamie Jackson on 2008-06-08
> **djwild said:**
> Regarding Jamie's suggestions:
It is not really useful in this current state. Any ideas what could the problem be? Something else I might try?

Sorry, I've got nothin'. Hopefully, someone else can troubleshoot.

---

### Post by Jamie Jackson on 2008-06-08
> **DarkW0lf said:**
> No, I can't execute the rmmod commands.



Yeah, I am at the point where I need to change the order the mods are loaded in but when I try I get the message about not being able to resolve the local host.

XFCE is acting flaky or something, it can't find an IP on boot (which makes since as there is no network available then). I never tried to reload the modules in 7.10 so I don't know if this same issue was there back then.

I got something screwed up in configuration somewhere, I just don't know what.

Could you post the module remove/add commands and output as they appear? I don't know if I'll be able to help, but it will show me what you're seeing, at least.

---

### Post by TheSlipstream on 2008-06-08
Hey, thanks man. I've been having major problems with my wireless, and thanks to your tutorial, it now works. Cheers!

---

### Post by hollowhead on 2008-06-09
Thanks for your reply I didn't understand.  Followed your instructions, no errors at all no wifi either so ran


 sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:65:71:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 02
       serial: 00:14:c2:e5:b9:43
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.2 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

---

### Post by Jamie Jackson on 2008-06-09
> **hollowhead said:**
> Thanks for your reply I didn't understand.  Followed your instructions, no errors at all no wifi either

Sorry if you've answered this before (I lose track), but what's the manner in which you have no wifi?

1. Does the wifi hardware light come on?
2. Does the network-manager applet (nm-applet) show your device?
3. Does the nm-applet show you any APs?
4. Can you connect to your router (two green lights in the nm-applet)?
5. Can you ping your router?

---

### Post by cascagrossa on 2008-06-09
I have a HPDV2240BR (HPDV2000 series) notebook with a Broadcom Wireless:
lspci: 05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

I have to use ndiswrapper, the b43 driver do not work if I go to more than 5 meters from the AP.

Only to be up-to-date, I compiled ndiswrapper 1.53 (as per instructions in ndiswrapper website) and used the workaround that modifies the way ndiswrapper loads Just altered the /etc/modprobe.d/ndiswrapper from:

"alias wlan0 ndiswrapper"  to

"alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
install ndiswrapper modprobe -r ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS;"

My notebook doesn't need the ssb module to work and so with only this modification I am able to remove ndiswrapper from /etc/modules and it allways loads on boot and resumes after suspend to RAM.

Now the news. After updating to the last kernel (2.6.24-19), I realized that blacklisting b43 and ssb (/etc/modprobe.d/blacklist) now works and those modules don't load, and so don't interfere with ndiswrapper.

Because of it, I returned all to the original instructions to install ndiswrapper and everything is working again.

---

### Post by hollowhead on 2008-06-10
Jamie thanks for your help and reply again.  The answer is no to all questions apart from the last and I cannot see any point in ping when the blue hardware light is not on.  Neil.

---

### Post by mrmarkers on 2008-06-11
Thank you for writing this guide. I am running Ubuntu 8.04 on an Acer Aspire 5003. Ubuntu quickly recognized and allowed me to install proprietary drivers for the wireless adapter which I believe worked for a day or two. Sometime after that, the adapter continued to function but would not detect any wireless networks. I came across this guide and within a few minutes everything was up and running again.

**Machine Brand and Model:** Acer Aspire 5003 WLMi

**Wireless Brand and Model:**
[INDENT]00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/INDENT]

**Wireless Chipset:**
[INDENT]00:0b.0 0280: 14e4:4318 (rev 02)[/INDENT]

**Ubuntu Version:** Ubuntu 8.04

**Kernel / Architecture:** 2.6.24-18-generic x86_64

**Other:**
[INDENT]*I did not have to compile the NDISWrapper.*

*I used Step 2a.*

*I did have to use the Hardy work around.*[/INDENT]


Thanks again,
Mark

---

### Post by Jamie Jackson on 2008-06-11
> **hollowhead said:**
> The answer is no to all questions apart from the last and I cannot see any point in ping when the blue hardware light is not on.  Neil.

Right, each question builds on the previous. Was easier to ask them all at once. ;-)

Anyway, I'm out of ideas. 

However, there's also kevdog's guide: It's completely the opposite of mine: His goes into much more detail, and does lots of manual steps. It's more helpful with troubleshooting, etc., and gets you walking before getting you running; whereas my guide tries to get you to hit the ground running, but isn't as helpful if something doesn't go quite right.

[kevdog's guide]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=574501")

Good luck, and let us know what happens. If all else fails, you can always go out and get a cheapo, better supported USB dongle, and forget all about your broadcom troubles. (I've got a $10 ativa dongle that *destroys* the built-in broadcom card in every possible category.. except for its protuberant form factor.)

---

### Post by Jackarow on 2008-06-12
Thank you for all the help. Your guide was very helpful. Perhaps you could expand/clarify the section on making the Hardy Bug Fix Permanent.

----------------------------------------------------------------
**Machine Brand and Model**: Gateway Model: MA2A

**Wireless Brand and Model**: 06:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

**Wireless Chipset**: 06:04.0 0280: 14e4:4318 (rev 02)

**Ubuntu Version:**: Ubuntu 8.04 Hardy

**Kernel/architecture**: 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

**-**I did not have to compile ndiswrapper.

**-**I did require the Hardy Bug Fix version 0.3

---

### Post by Jamie Jackson on 2008-06-12
> **Jackarow said:**
> Thank you for all the help. Your guide was very helpful. Perhaps you could expand/clarify the section on making the Hardy Bug Fix Permanent.

Let me know what you had in mind, with regard to clarifying this section.

---

### Post by hollowhead on 2008-06-14
Jamie, thanks for your help.  I have made some progress... This might be useful for people having the same problem.... I decided to try the restricted drivers again, especially since there was an upgrade for these and a linux headers upgrade.  After upgrade I went into system->admin->hardware drivers clicked on enable which installed the broadcom driver, previously this had dome much but fw-cutter and loads of other stuff was installed.  Going back into this dialog the wifi card driver checkbox was ticked which didn't happen before.  I rebooted and the blue wifi LED comes on.  Unfortunately I still cannot see wifi networks should unblacklist BCM34XXX in modules blacklist?  Neil.

---

### Post by Jamie Jackson on 2008-06-14
> **hollowhead said:**
> Jamie, thanks for your help.  I have made some progress... This might be useful for people having the same problem.... I decided to try the restricted drivers again, especially since there was an upgrade for these and a linux headers upgrade.  After upgrade I went into system->admin->hardware drivers clicked on enable which installed the broadcom driver, previously this had dome much but fw-cutter and loads of other stuff was installed.  Going back into this dialog the wifi card driver checkbox was ticked which didn't happen before.  I rebooted and the blue wifi LED comes on.  Unfortunately I still cannot see wifi networks should unblacklist BCM34XXX in modules blacklist?  Neil.

I'm pretty sure the bcm43xx module is what the restricted drivers install you did is based on, so you probably don't want to blacklist it. (No harm in experimenting, though.)

Side question: Have you had any other OS on this machine, and did the wireless work with it?

---

### Post by Angelbeast on 2008-06-15
hey everyone.I eed just a little here...I'm trying to follow the Hardy bug fi for broadcom as shown here: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0)

The temp fix works fine enogh but the way to make it permanent is a little confusing. It is as follows...

The following are experimental methods to get the device working upon reboot. All of these are long commands, so watch for line wraps!
Modifying /etc/modprobe.d/ndiswrapper
Version 0.3

This is a much slicker solution than the previous versions (listed below), but it's unproven. This will [WWW] customize how ndiswrapper loads:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 


Now in the ndiswrapper file do i remove what is already there Do i insert it after? do i paste it just as is? the directions were not the clearest so any firther help woud be much appreciated, thanks :-)

---

### Post by DarkW0lf on 2008-06-15
I don't know the whole output is wierd and just had the same thing happen on my desktop when I was trying to compile a modem driver.

Seems related to sudo, I have no clue but it was something about the hostname of the computer and sudo couldn't resolve the local host (no freaking clue ???) After logging out of gnome (desktop) and re-login it works fine.

But in XFCE (on the laptop) no such luck, it doesn't like the hostname.
Don't know why sudo is checking it. I'll try again and see what happens.

---

### Post by Angelbeast on 2008-06-15
> **Angelbeast said:**
> hey everyone.I eed just a little here...I'm trying to follow the Hardy bug fi for broadcom as shown here: 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-cbc75fcb762da2057fa8dbe904358e4b611353c0)

The temp fix works fine enogh but the way to make it permanent is a little confusing. It is as follows...

The following are experimental methods to get the device working upon reboot. All of these are long commands, so watch for line wraps!
Modifying /etc/modprobe.d/ndiswrapper
Version 0.3

This is a much slicker solution than the previous versions (listed below), but it's unproven. This will [WWW] customize how ndiswrapper loads:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 


Now in the ndiswrapper file do i remove what is already there Do i insert it after? do i paste it just as is? the directions were not the clearest so any firther help woud be much appreciated, thanks :-)

No one at all has any clue how to mke this work? *LOL*

---

### Post by net4home on 2008-06-15
Your "Feisty No-Fluff" document worked wonderfully on my system below with Ubuntu 8.04 LTS installed.

Machine Brand & Model:
Dell Inspiron 1300 

Wireless Brand and Model:
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Wireless Chipset:
02:03.0 0280: 14e4:4318 (rev 02)

Ubuntu Version:
Description:    Ubuntu 8.04.1

Kernel/architecture (including 32 vs. 64 bit) :
2.6.24-19-generic i686  -  (32 bit)

No extra boot options were needed, I did not need to compile the NDISWrapper, I used Step 2A, and I did have to apply the Hardy Bug Fix and used Version 0.3 to make it permanent.  I used what was put in the "Trying it Temporarily" and then later ran what was under the Version 0.3.  I have yet to reboot my computer to verify everything works again.  

Thank you so much for taking the time to write this How-To.  
Kevin

---

### Post by net4home on 2008-06-15
One little issue remains...When I reboot the settings do not stay.  I have these statements in my /etc/modprobe.d/ndiswrapper file:

alias wlan0 ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Sun Jun 15 17:23:08 CDT 2008
install ndiswrapper modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

The only thing I can think of doing would be to put the alias after the ndiswrapper is installed.

I was able to re-run the following commands from the Feisty_No-Fluff document:

**Trying It Temporarily**

   sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

After running these commands my wireless worked again.  I'm currently looking for a place to put these commands so that my wireless will work every time.  I might just put them in a script that I can run to enable my wireless whenever I need it.  If anyone has a better idea as to where these commands should be put, please let me know.

Thanks
Kevin

---

### Post by Angelbeast on 2008-06-15
> **net4home said:**
> One little issue remains...When I reboot the settings do not stay.  I have these statements in my /etc/modprobe.d/ndiswrapper file:

alias wlan0 ndiswrapper
#Hardy ssb/ndiswrapper workaround, added Sun Jun 15 17:23:08 CDT 2008
install ndiswrapper modprobe -r b43 b44 b43legacy ssb ndiswrapper; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

The only thing I can think of doing would be to put the alias after the ndiswrapper is installed.

I was able to re-run the following commands from the Feisty_No-Fluff document:

**Trying It Temporarily**

   sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

After running these commands my wireless worked again.  I'm currently looking for a place to put these commands so that my wireless will work every time.  I might just put them in a script that I can run to enable my wireless whenever I need it.  If anyone has a better idea as to where these commands should be put, please let me know.

Thanks
Kevin

ah well i'm glad i'm not the only one...If you ever get an answer or get worked out how to fix this let me know please...no one else seems to know :-)

---

### Post by net4home on 2008-06-15
OK, Here is the fix that has worked for me.

I did the following from the WiFiDoc Feisty_No-Fluff
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Long story short, I applied the Version 0.2 solution to making this fix persistent. 

It says it's is obsolete but, it is what has worked for me.  I previously had applied the version 0.3 fix to make the changes persistent with no effect, but I have not removed those lines from the file /etc/modprobe.d/ndiswrapper to see if they make any difference or not.  Maybe sometime this week I will be able to get the chane to try this and post back my findings.  So in other words I have applied both Version 0.3 & 0.2 methods for making this fix persistent.

echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local
[FONT=Verdana][B]
Hope this helps those of you having some of the same issues I was.

Thanks
Kevin
[/B][/FONT]

---

### Post by Angelbeast on 2008-06-16
> **net4home said:**
> OK, Here is the fix that has worked for me.

I did the following from the WiFiDoc Feisty_No-Fluff
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Long story short, I applied the Version 0.2 solution to making this fix persistent. 

It says it's is obsolete but, it is what has worked for me.  I previously had applied the version 0.3 fix to make the changes persistent with no effect, but I have not removed those lines from the file /etc/modprobe.d/ndiswrapper to see if they make any difference or not.  Maybe sometime this week I will be able to get the chane to try this and post back my findings.  So in other words I have applied both Version 0.3 & 0.2 methods for making this fix persistent.

echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local
[FONT=Verdana][B]
Hope this helps those of you having some of the same issues I was.

Thanks
Kevin
[/B][/FONT]

Thanks i'll try that/ But where do i put it? Do i replace what's in there already with that or add it before or after?

---

### Post by net4home on 2008-06-16
Just copy and paste the line on a terminal session and hit enter.  It will place it in the correct file.  It shouldn't really matter where it is in the file just that it is.  

Thanks
Kevin

---

### Post by Angelbeast on 2008-06-16
> **net4home said:**
> Just copy and paste the line on a terminal session and hit enter.  It will place it in the correct file.  It shouldn't really matter where it is in the file just that it is.  

Thanks
Kevin

AHHHHHH it goes in a TERMINAL window...Than you so much  :-)

---

### Post by Angelbeast on 2008-06-16
> **net4home said:**
> Just copy and paste the line on a terminal session and hit enter.  It will place it in the correct file.  It shouldn't really matter where it is in the file just that it is.  

Thanks
Kevin

Works great...Thanks for telling me where to put it :-)

---

### Post by agntsmyth on 2008-06-16
HP DV6000z broadcom 4312 rev 2 amd64 ubuntu 8.04 the wiki didn't work but the drivers i downloaded did work with the "windows wireless drivers" program that came on the dvd I simply selected the bcmwl5.inf file and tada wireless works. so thanx for the drivers

---

### Post by hollowhead on 2008-06-16
I unblacklisted it (put a # in front of it) rebooted no joy.  Still get a blue wifi light but no wifi.  

I had win xp on briefly when I bought the laptop just to check hardware was working, but have used ubuntu since 5.1.  The wifi didn't work then but has worked since 6.04 so this is very irritating.  This is why I don't to buy a wifi device.

What an earth is the difference between my 4318 and others who have managed to follow your instructions and get it going?  Has anyone managed to get wifi going on nx6110?  

Thanks Neil.

---

### Post by deaddudehangin on 2008-06-16
Hey, thank you for the fix, it worked!
The only problem that I'm faceing is trying to get the permanent fix to work.
The temporary fix for Hardy works fine, but I can't get the permanent fix to work
I think the problem is that I'm putting the command into terminal wrong

BTW I'm using a Linksys WPC54Gv2 on Hardy 8.4 xubuntu.

Nevermind I got it to work by using the fix on the page before this one:guitar: and I had to reboot for the fix to take effect

---

### Post by Jackarow on 2008-06-19
Just a little feedback...

It seems as though I too was able to make the Hardy bug fix permanent by utilizing version 0.2. The current version 0.3 didn't seem to work for me.

On a side note: Can anyone recommend an external wireless card (USB) that works well with Ubuntu? I seem to be witnessing a serious drop in the performance of my wireless card (Broadcom bcm4318). For example, my router in the next room of my apartment indicates only a 48% signal strength. Price is an issue...

---

### Post by hollowhead on 2008-06-20
Jamie thanks again solved it don't know how see [http://ubuntuforums.org/showthread.php?t=831242](http://ubuntuforums.org/showthread.php?t=831242)

Speed is variable but range is much improved.  NH

---

### Post by CGH on 2008-06-22
Dell Inspiron 1525

0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

0b:00.0 0280: 14e4:4315 (rev 01)

Ubuntu 7.10

2.6.22-14-generic i686

 Whether or not you had to compile NDISWrapper: yes

Which version of Step 2 you used: 2e

it worked perfectly!

---

### Post by Scorpions4ever on 2008-06-27
Had my laptop working fine with native drivers until I got a new wireless router (DLink WBR-1310). My old wireless router was a Linksys BEFW1154. Both had WEP enabled, but with my new router I was getting "TODO: Incomplete code in keymac_write()" messages in /var/log/messages when attempting to connect to it. Switched over to using ndiswrapper using your guide and everything worked first class.

For the record:
Machine: Gateway M350 WVN laptop
OS: Ubuntu Gutsy (7.10)
Wireless brand and model: 02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
Wireless chipset: 02:03.0 0280: 14e4:4320 (rev 02)
Kernel: 2.6.22-15-generic #1 SMP (2.6.22-15-generic i686)
Whether or not you had to compile NDISWrapper?: No. apt-get worked fine for me
Which version of Step 2 you used: 2f

---

### Post by kristersaurus on 2008-06-27
Im on a fresh install of Hardy - I've followed all the steps including the workaround and am still having the module=ssb bug. If anyone wants more info let me know. I will post any success fixing it.

---

### Post by DarkW0lf on 2008-06-28
Well I got the whole sudo thing fixed (ubuntu was having issue with /etc/hostname and /etc/hosts files).

Any way used permanment fix and wireless worked.
After partial upgrade, Network Manager cannot connect to a WAP. Device is listed as eth1 now instead of wlan0. And even though I type in the network name, the ESSID comes up as blank (using iwconfig) but listed in NM ???

Now what broke ?

---

### Post by b3n5p34km4n on 2008-06-29
HP dv6000
    02:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
02:00.0 0280: 14e4:4315 (rev 01)

    Description:	Ubuntu 8.04

    2.6.24-16-generic i686

   don't know about any other boot options i might be using
   didn't even try compiling ndiswrapper
   used step 2e
   it said to apply the hardy bug fix if the configuration line said "module=ssb" instead of "module=ndiswrapper".  too bad it doesn't say what to do if the configuration line says "latency=0" because that's what mine says.  please help me.

---

### Post by letank on 2008-07-02
Almost there, I can see the network, but cannot connect (works fine under XP)

HP Omnibook XE4100
Feisty 7.04 
Kernel 2.6.20-17
Skipped step 2, and installed the driver from my original CD: the generic bcmwl5.inf
Wireless card: macwireless 802.11g (basically a broadcom  3.10.52.0)
ndiswrapper-1.52 (needed compiling)

with this issue

laptop:~$ lspci | grep Broadcom                 
pcilib: Cannot open /sys/bus/pci/devices/0000:02:00.0/config 
Unable to read the standard header from device 0000:02:00.0 

edited but
~$ lspci -v
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)


otherwise

laptop:~$ iwconfig 
lo        no wireless extensions. 
eth0      no wireless extensions. 
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:16 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

laptop:~$ iwlist wlan0 scan 
wlan0     Scan completed : 
          Cell 01 - Address: 00:03:93:E8:9B:B2 
                    ESSID:"1801 Airport Network" 
                    Protocol:IEEE 802.11b 
                    Mode:Managed 
                    Frequency:2.457 GHz (Channel 10) 
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 


Any help appreciated, i have been slaving for a few days.... 

Michel

---

### Post by davidpeace on 2008-07-02
I think it worked. Network manager shows two (for my current location) wireless networks. Thanks. Here is the hardware info you asked for (hope it's what you asked for):

davidpeace2002@ms:~$ lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
davidpeace2002@ms:~$ lsmod
Module                  Size  Used by
isofs                  39464  1 
udf                    91048  0 
ipv6                  311848  10 
binfmt_misc            14860  1 
af_packet              27272  2 
powernow_k8            16608  1 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0 
sbs                    17808  0 
sbshc                   8960  1 sbs
bay                     8064  0 
dock                   12960  1 bay
container               6656  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
parport_pc             41128  0 
lp                     14916  0 
parport                44300  2 parport_pc,lp
joydev                 15488  0 
usbtouchscreen         13316  0 
uvcvideo               62084  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
hci_usb                19228  0 
bluetooth              67748  1 hci_usb
usbhid                 35296  0 
hid                    44992  1 usbhid
snd_hda_intel         440408  5 
snd_pcm_oss            47648  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                92168  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_hwdep              12552  1 snd_hda_intel
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
video                  23444  8 
output                  5632  1 video
psmouse                46236  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
wmi_acer               11076  0 
serio_raw               9092  0 
ac                      8328  0 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               8858052  36 
battery                16776  0 
evdev                  14976  8 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_nforce2             8704  0 
button                 10912  0 
snd                    70856  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               28544  2 nvidia,i2c_nforce2
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
k8temp                  7680  0 
pcspkr                  4992  0 
soundcore              10400  1 snd
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
sg                     41880  0 
sr_mod                 20132  1 
cdrom                  41512  1 sr_mod
sd_mod                 33280  3 
pata_amd               16772  1 
sata_nv                31752  2 
ehci_hcd               41996  0 
ata_generic             9988  0 
forcedeth              55564  0 
ohci_hcd               27524  0 
pata_acpi               9856  0 
usbcore               169904  7 usbtouchscreen,uvcvideo,hci_usb,usbhid,ehci_hcd,ohci_hcd
libata                176432  4 pata_amd,sata_nv,ata_generic,pata_acpi
scsi_mod              178488  4 sg,sr_mod,sd_mod,libata
thermal                19744  0 
processor              41448  2 powernow_k8,thermal
fan                     6792  0 
fuse                   56112  3 
vesafb                 10504  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
davidpeace2002@ms:~$ 
________________________________________________________

---

### Post by Jamie Jackson on 2008-07-03
> **kristersaurus said:**
> Im on a fresh install of Hardy - I've followed all the steps including the workaround and am still having the module=ssb bug. If anyone wants more info let me know. I will post any success fixing it.

Please post the output of "lsmod" and "cat /etc/modprobe.d/ndiswrapper"

---

### Post by Jamie Jackson on 2008-07-03
> **DarkW0lf said:**
> Well I got the whole sudo thing fixed (ubuntu was having issue with /etc/hostname and /etc/hosts files).

Any way used permanment fix and wireless worked.
After partial upgrade, Network Manager cannot connect to a WAP. Device is listed as eth1 now instead of wlan0. And even though I type in the network name, the ESSID comes up as blank (using iwconfig) but listed in NM ???

Now what broke ?

You get the blue ribbon for worst luck. ;-)

Please post the output of the same two commands I asked for in the post immediately preceding this one?

---

### Post by Jamie Jackson on 2008-07-03
> **Jackarow said:**
> Just a little feedback...

It seems as though I too was able to make the Hardy bug fix permanent by utilizing version 0.2. The current version 0.3 didn't seem to work for me.

On a side note: Can anyone recommend an external wireless card (USB) that works well with Ubuntu? I seem to be witnessing a serious drop in the performance of my wireless card (Broadcom bcm4318). For example, my router in the next room of my apartment indicates only a 48% signal strength. Price is an issue...

I can vouch for the [Ativa device]("http://www.ativasupport.com/product/?pid=AWGUA54"). I picked one up for $10 on sale, and it kicks the snot out of the Broadcom in every category, and it requires zero configuration (except that it sticks out... it is a dongle, after all).

---

### Post by kevdog on 2008-07-03
What chipset is contained in the Ativa -- RaLink?

---

### Post by DarkW0lf on 2008-07-04
> **Jamie Jackson said:**
> You get the blue ribbon for worst luck. ;-)

Yea, ya think they'll give it to the whiny bitch instead who got second, just because she can cry.

> Please post the output of the same two commands I asked for in the post immediately preceding this one?

Done and in the archive are outputs (lshw -c and your 1st post) from before and after installation that I never posted what with the sudo crap.

---

### Post by letank on 2008-07-05
> **letank said:**
> Almost there, I can see the network, but cannot connect (works fine under XP)

HP Omnibook XE4100
Feisty 7.04 
Kernel 2.6.20-17
Skipped step 2, and installed the driver from my original CD: the generic bcmwl5.inf
Wireless card: macwireless 802.11g (basically a broadcom  3.10.52.0)
ndiswrapper-1.52 (needed compiling)

~$ lspci -v
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)



Solved:

Instead of logging in w the default open network, i used the alternate menu pasword to join the keyring,  then enter the network password.

It is not self installing, i need to repeat the procedure... but all least it is on.

Now i need to work on the gps... and may be the ipod

cheers

Michel

---

### Post by Jamie Jackson on 2008-07-05
> **DarkW0lf said:**
> Yea, ya think they'll give it to the whiny bitch instead who got second, just because she can cry.



Done and in the archive are outputs (lshw -c and your 1st post) from before and after installation that I never posted what with the sudo crap.

Okay, your /etc/modprobe.d/ndiswrapper has this line:
```
install ndiswrapper modprobe -r ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;
```

But from your lsmod, it looks like you need:
```
install ndiswrapper modprobe -r b43 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb;
```

---

### Post by Jamie Jackson on 2008-07-05
> **letank said:**
> Solved:

Instead of logging in w the default open network, i used the alternate menu pasword to join the keyring,  then enter the network password.

It is not self installing, i need to repeat the procedure... but all least it is on.

Now i need to work on the gps... and may be the ipod

cheers

Michel

You mean you used NetworkManager's "Connect to Other Wireless Network" dialog?

---

### Post by Jamie Jackson on 2008-07-05
> **kevdog said:**
> What chipset is contained in the Ativa -- RaLink?

I didn't know until I just now looked. (It's funny how little you come to know about something when it "just works" ;-) )

According to some posts online, it's a ZyDas chipset.

---

### Post by Z_o-s-o on 2008-07-06
I've got a semi-unique issue going on here.

Ive got a BCM94311, and the guide for hardy worked well for a while, but then I started having issues.

It's not that it wont connect at all to my network (WPA), but it take FOREVER to finally connect to it. Open networks are just fine, but WPA takes sometimes hours to finally connect.


Any ideas?

---

### Post by DarkW0lf on 2008-07-07
That worked Jamie.

Added b43 to the line for the fix and it is working again.

---

### Post by vanix on 2008-07-07
* Machine Brand and Model** DELL VOSTRO 1500 PP22L (T7250)**
    * Wireless Brand and Model*** 0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)***

    * Wireless Chipset: **0c:00.0 0280: 14e4:4311 (rev 01)**
    * Ubuntu Version: **8.04 HARDY HERON**
    * Kernel / Architecture: **2.6.24-16-generic i686**
    * Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.) NONE
    * Whether or not you had to compile NDISWrapper **WITHOUT COMPILE**
    * Which version of Step 2 you used NONE, USED BCOM DRV I HAD 
    * If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not **USED VER. 0.3**

Excellent guide!
thanks a lot!
:lolflag:

---

### Post by Jamie Jackson on 2008-07-07
> **Z_o-s-o said:**
> I've got a semi-unique issue going on here.

Ive got a BCM94311, and the guide for hardy worked well for a while, but then I started having issues.

It's not that it wont connect at all to my network (WPA), but it take FOREVER to finally connect to it. Open networks are just fine, but WPA takes sometimes hours to finally connect.


Any ideas?

I have also had WPA problems in some of the latest kernel releases. I haven't had time to investigate it yet, so I switched to WEP a couple weeks ago in order to connect. I'm not saying this is an acceptable solution, but it's a pain that sometimes, something flakes out between a kernel upgrade and one or a combination of ndiswrapper, wpa_supplicant, network-manager and/or a particular AP.

---

### Post by Jamie Jackson on 2008-07-07
> **DarkW0lf said:**
> That worked Jamie.

Added b43 to the line for the fix and it is working again.

Yay! See you in two weeks when it breaks again. :P

---

### Post by Z_o-s-o on 2008-07-07
Yeah...

I have huge problems with WPA....


Its been sketchy for me ever since I did some updates back at -16.

---

### Post by s1337m on 2008-07-07
Im not sure how to edit the wiki, but am reporting success:


# Machine Brand and Model
#

Dell Inspiron E1705

Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
#

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)


Wireless Chipset: lspci -n | grep '14e4:43'
#

0c:00.0 0280: 14e4:4328 (rev 01)


Ubuntu Version: lsb_release -d
#

Description:	Ubuntu 8.04.1


Kernel/architecture (including 32 vs. 64 bit) : uname -mr
# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
# Whether or not you had to compile NDISWrapper
# Which version of Step 2 you used
# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not, and if you used it, which version you used. 


2.6.24-19-generic i686
No hardy bug fix needed.

IMPORTANT:  FOR STEP 2, USE THE DRIVERS IN THE FOLLOWING EXE:
[http://ftp.us.dell.com/network/R140746.EXE](http://ftp.us.dell.com/network/R140746.EXE)

---

### Post by Jamie Jackson on 2008-07-08
> **s1337m said:**
> Im not sure how to edit the wiki, but am reporting success:


# Machine Brand and Model
#

Dell Inspiron E1705

Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
#

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)


Wireless Chipset: lspci -n | grep '14e4:43'
#

0c:00.0 0280: 14e4:4328 (rev 01)


Ubuntu Version: lsb_release -d
#

Description:	Ubuntu 8.04.1


Kernel/architecture (including 32 vs. 64 bit) : uname -mr
# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
# Whether or not you had to compile NDISWrapper
# Which version of Step 2 you used
# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not, and if you used it, which version you used. 


2.6.24-19-generic i686
No hardy bug fix needed.

IMPORTANT:  FOR STEP 2, USE THE DRIVERS IN THE FOLLOWING EXE:
[http://ftp.us.dell.com/network/R140746.EXE](http://ftp.us.dell.com/network/R140746.EXE)

Did you try step 2d before trying the above driver, or did you just go straight to the driver you mentioned?

---

### Post by s1337m on 2008-07-08
> **Jamie Jackson said:**
> Did you try step 2d before trying the above driver, or did you just go straight to the driver you mentioned?

I did try Step 2d but it didnt work for me, so I went with those I linked

---

### Post by hudarsono on 2008-07-08
Success for me as far. Wireless network detected.:)

Machine Brand and Model  : Macbook White MB403 v4,1

Wireless Brand and MOdel :
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Wireless Chipset	 : 02:00.0 0280: 14e4:4328 (rev 03)

Ubuntu Version		 : Ubuntu 8.04

Kernel/architecture 	 : 2.6.24-16-generic x86_64

Not compiled ndiswrapper, used step 2d and apply bug fix 0.3

---

### Post by Jamie Jackson on 2008-07-10
> **s1337m said:**
> I did try Step 2d but it didnt work for me, so I went with those I linked

Okay, thanks for the info.

---

### Post by PrimeRisk on 2008-07-12
First, let me say thank you to Jamie and all the others that have contributed to this How-To.  I'm writing this on my laptop with Hardy 8.04 on wireless right now!

Success Report:
# Machine Brand and Model
Compaq Presario F500 (F560US)


#Wireless Brand and Model (please post the whole line): lspci | grep Broadcom
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

#Wireless Chipset: lspci a-n | grep '14e4:43'
03:00.0 0280: 14e4:4311 (rev 02)

#Ubuntu Version: lsb_release -d
Ubuntu 8.04.1

#Kernel/architecture (including 32 vs. 64 bit) : uname -mr
2.6.24-19-generic i686

# Any extra boot options you might be using (e.g., noacpi, irqpoll, etc.)
<none>

# Whether or not you had to compile NDISWrapper
No

# Which version of Step 2 you used
2a

# If you're on Hardy, whether you had to apply the "Hardy Bug Fix" workaround or not, and if you used it, which version you used.

Yes. Version 0.3

---

### Post by fbnewtz on 2008-07-12
* HP dv9000 - dv9500z
    * 03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
    * 03:00.0 0280: 14e4:4328 (rev 03)
    * Description:	Ubuntu 8.04.1
    * 2.6.24-19-generic i686
    * No extra boot options other than the default options.
    * I did not have to compile the boot options
    * Step 2d
    * I did not have to apply the "Hardy Bug Fix" workaround


Thanks for an excellent howto!  I have been dying to get a linux distro to work on my laptop for a while now and was at a training class for python and someone mentioned that they had never had any issues getting hardware to work with Ubuntu on any laptop so I decided to give it a whirl!  Good bye Vista!

Thanks,

Fred

---

### Post by mrhighnotes on 2008-07-12
mrhighnotes@mrhighnotes-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I cannot get it to work. 

*-network DISABLED

Does this have something to do with it?

---

### Post by Jamie Jackson on 2008-07-14
> **mrhighnotes said:**
> mrhighnotes@mrhighnotes-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I cannot get it to work. 

*-network DISABLED

Does this have something to do with it?

First, please post the output of "lsmod"

---

### Post by David Robertson on 2008-07-17
Excellent Post

You have done well to collect this issue

It has help me solve my current problem - transition from 2.6.24-18 to 2.6.24-19.

I have a (hp) compaq presario v6500 series notebook containing bcm94311 rev 2 wireless.

Short History:

Beta 8.04 CD - great native wireless (it included a patch for my card that broke a heap of other cards)

Official Release & upgrade - my card failed, but other things worked better.

Couldn't get native drivers working ([http://linuxwireless.org/en/users/Drivers/b43#b43andb43legacy](http://linuxwireless.org/en/users/Drivers/b43#b43andb43legacy)) so dropped back to ndiswrapper; April 2008 ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff))

ndiswrapper died between kernel upgrade (2.6.24-18 to 2.6.24-19). The issue as I see it, the native stack is being developed, more stack now has more things to be unloaded and reloaded (Same reference as above - really good and current howto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Good News: ([http://www.sabayonlinux.org/forum/viewtopic.php?f=52&t=12542&start=0](http://www.sabayonlinux.org/forum/viewtopic.php?f=52&t=12542&start=0)) - Next kernel (2.6.25) indicates better support for native wireless (integration without busting other cards?)

ndiswrapper is great when native won't work. Native will always be better supported well after it's available.

Again Thanks.

---

### Post by Jamie Jackson on 2008-07-17
> **David Robertson said:**
> 
Good News: ([http://www.sabayonlinux.org/forum/viewtopic.php?f=52&t=12542&start=0](http://www.sabayonlinux.org/forum/viewtopic.php?f=52&t=12542&start=0)) - Next kernel (2.6.25) indicates better support for native wireless (integration without busting other cards?)

ndiswrapper is great when native won't work. Native will always be better supported well after it's available.

Again Thanks.

The big question is: Will the native driver *perform* better than the ndiswrapper/windows driver? AFAIK, the native driver isn't capable of the same speeds, but I'd be delighted to be proven wrong.

---

### Post by Rastus on 2008-07-23
OK,
here goes.
brand new Dell inspiron 1525

Ubuntu 8.04.1 clean install

 > *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:5d:bb:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11


wireless driver says "wl"  it will see networks in the network manager and give strengths but will not connect with WEP key.  It thinks for a while and then asks for the key again. (the key is correct)

I went through the how to using option 2a

with no success, driver still shows "wl"

> administrator@laptop4:~/bcm43xx$ lspci -n | grep '14e4:43'
0b:00.0 0280: 14e4:4315 (rev 01)


I did not see a 4315 listed in the chart at the front of the How-To.
Anyway, I followed the suggestion of one of the posters with a "wl" driver and deleted it but still no ndiswrapper listed as driver.  Now I have this> 
administrator@laptop4:~/bcm43xx$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:cd:08:21
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=192.168.100.127 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

any help would be appreciated.
THanks

---

### Post by Jamie Jackson on 2008-07-23
> **Rastus said:**
> OK,
here goes.
brand new Dell inspiron 1525

Ubuntu 8.04.1 clean install

 

wireless driver says "wl"  it will see networks in the network manager and give strengths but will not connect with WEP key.  It thinks for a while and then asks for the key again. (the key is correct)

I went through the how to using option 2a

with no success, driver still shows "wl"



I did not see a 4315 listed in the chart at the front of the How-To.
Anyway, I followed the suggestion of one of the posters with a "wl" driver and deleted it but still no ndiswrapper listed as driver.  Now I have this

any help would be appreciated.
THanks

The chipset is the important part:
```
administrator@laptop4:~/bcm43xx$ lspci -n | grep '14e4:43'
0b:00.0 0280: 14e4:4315 (rev 01) 
```

"14e4:4315" is the chipset, and corresponds to step 2*e* (it's in the chipset table). First [uninstall]("http://ubuntuforums.org/showpost.php?p=3767216&postcount=273") the driver you've got, then install the driver in step 2e.

If that doesn't work. Please post the output of lsmod.

---

### Post by him610 on 2008-07-23
I would like to make a positive statement about this process.

My family and I recently returned from a vacation to the Outer Banks of North Carolina. This year for the first time, wireless internet was available in our vacation cottage. It was available through a Motorola cable modem (gateway) that also had a wireless antenna. The modem was located on the lower level of the cottage next to a TV in the master bedroom.

I originally tried to connect wirelessly using WinXP on my seven year old Athlon Sony Vaio dual-boot laptop from upstairs - maybe 30 feet straight line distance. It would not connect - maybe metal A/C ducts interfered with the signal, or weak signal, or both. Then I went downstairs right next to the modem, maybe three feet; I was able to connect using both WinXP and Xubuntu 8.04.

Since I had to sit on the edge of the bed with the laptop balanced on - where else but on my lap, my back began to bother me after awhile so I moved to a desk about twelve feet away. I could not connect using WinXp; however, booting into Xubuntu it connected right up with an indication of 73% received signal strength.

My wireless card is a five year old Linksys with a Broadcom 4306 version 2 chip which I configured using this very process.

It worked using _buntu when, under the very same conditions, it would NOT work using WinXP.

For all of the folks who are still having problems getting connected, keep at it. It's a learning experience and it's worth it.

Thanks to Jamie Jackson and all the other contributors who have helped out in this thread.

Cheers!

---

### Post by Jamie Jackson on 2008-07-23
> **hgh9mrp said:**
> I would like to make a positive statement about this process.

My family and I recently returned from a vacation to the Outer Banks of North Carolina.

Cheers!

I'm heading to Nags Head August 2. I hope you got the place good and ready for me. ;-)

---

### Post by Rastus on 2008-07-24
OK,
I'm back

I removed the drive from 2a and installed the driver from 2e and followed your instructios above and this is what I have now.

> administrator@laptop4:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:cd:08:21
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0administrator@laptop4:~$ 
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e1:5d:bb:c8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11


the driver still shows "wl".  Isn't it supposed to show ndiswrapper instead?  Should I unclick "enabled" in the Administration > Hardware Drivers dialog for the "wl" driver?

I await further instructions Captain Jackson.
:)

BTW, even though we haven't got my unit working yet, this is the easiest and best maintained resource for this issue on the net that I have found.  I feel sure that the problem lies mainly in my linux N00b status and I really appreciate you taking the time to assist.
R

---

### Post by LaRoza on 2008-07-25
The Archive is now read only. This thread continues here: [http://ubuntuforums.org/showthread.php?p=5456980](http://ubuntuforums.org/showthread.php?p=5456980)

---

