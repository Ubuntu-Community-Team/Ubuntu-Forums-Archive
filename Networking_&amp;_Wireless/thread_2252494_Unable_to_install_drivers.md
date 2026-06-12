---
title: "Unable to install drivers"
date: 2014-11-12
forum: Networking &amp; Wireless
---

### Post by levi5 on 2014-11-12
Hi, I'm on the verge of crying because after spending around £300 on my new computer I found I can't use wifi. I've bought a usb to lan adapter which comes with a minidisk of drivers to install, but in the linux section of the disk there is a help file for installing on linux. All it has in the way of instructions is the cryptic message *To install: make inst* and I cant find anything anywhere on google that gives me the first clue of what this means. Please, help me before I throw this hunk of junk out of my window, I can't afford to spend any more on this. I'm totally new to linux, I'll need a full step-by-step if anyone can provide. I'm using the latest ubuntu downloadable from the official website, 14.something

---

### Post by coffeecat on 2014-11-12
> **levi5 said:**
> I've bought a usb to lan adapter which comes with a minidisk of drivers to install, but in the linux section of the disk there is a help file for installing on linux.

First thing for your peace of mind - ignore the minidisk!

Please clarify. "USB to LAN" made me think of USB to ethernet, most of which "just work" in Linux, but you mention wifi in the previous sentence. Is this a USB wireless device or USB to ethernet adapter?

If wireless, have a look at this sticky.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

With the USB wifi device plugged in, run the wireless script and post the output so that one of our wireless geniuses can help you. If you can't connect via ethernet on your Ubuntu machine there is a link in that post describing how to get the wireless script on another machine.

That all being said, most wireless devices do just work in the latest version of Ubuntu, but sometimes one can make an unlucky choice and get an awkward wireless chipset.

So that others can help you, which version of Ubuntu are you running? You say 14-something. Is it 14.04 or 14.10?

---

### Post by levi5 on 2014-11-12
Thanks a bunch, I'll check the link out and see how I do. The usb insert has the ability to connect to wifi networks, a little like a dongle, but the wifi networks have to be pre-existing e.g. a home hub or wireless router. I found out I'm on 14.04, also I'm barely running this page on my mobile device, I'm unable to use any internet on the machine mentioned above so downloading things is virtually impossible. I'll run that script now if I can work out how to, thanks. Also, ignore the minidisk? Does that mean the drivers on there are useless anyway? How would the problem be solved otherwise?

---

### Post by levi5 on 2014-11-12
Okay, I've run the code and gotten the relevant text file. Consider this thread closed, I'm going to start a new thread with all the details I've just learned and relevant info I've gathered and hope for a speedy reply. Thanks for the help, it's been great.

---

### Post by chili555 on 2014-11-12
> **levi5 said:**
> Okay, I've run the code and gotten the relevant text file. Consider this thread closed, I'm going to start a new thread with all the details I've just learned and relevant info I've gathered and hope for a speedy reply. Thanks for the help, it's been great.Why not just add them here?

---

### Post by levi5 on 2014-11-12
Hi, first off you need to know I'm a COMPLETE newcomer to ubuntu, I'm running ubuntu 14.04 and absolutely everything with the command prompt confuses me, from sudo onwards. I bought a wireless lan adapter usb to allow my computer to use the internet, but I cant install the drivers. It came with a minidisk of drivers but I have no idea how to do so and it has separate folders in the linux folder on the minidisk and all of them appear to be for some version of redhat or another. I've no idea how I would go about installing these anyway, but the readme.txt has an installation guide that just gives the cryptic massage *to install drivers- make inst*, which makes no sense whatsoever to me. Another user told me to run some sort of code he gave me a link to and it gave me an info file he told me to upload for your purposes (I have no idea how I even ran it, I messed around with preferences as per the guide included) and so here it is.  ```


########## wireless info START ##########


Report from: 16 Nov 2014 22:33 EST -0500


Booted last: 12 Nov 2014 09:12 EST -0500


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:230f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 1c4f:0048 SiGma Micro 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1a2c:0c21 China Resource Semico Co., Ltd 
Bus 004 Device 004: ID 0011:7788  
Bus 004 Device 003: ID 0fe6:8101 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


eth1      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### nm-tool ###########################


NetworkManager Tool


State: disconnected


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            dm9601
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


eth1      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (dm9601)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


########## wireless info END ############



```  So yeah, he described you as technological wizards here on the forums, I hope you can work a little magic for me because I'm on the verge of crying. I've bought a shiny £260 black brick plus £50-something worth of peripherals that are completely useless to me unless I can make this thing work. Please help, I'm clueless so your wizardly technospeak is babble to me unless explained clearly in manageable newbie steps. Thanks

---

### Post by overdrank on 2014-11-12
Threads merged :)

---

### Post by levi5 on 2014-11-12
Thanks, I didn't realise threads were bumped on here by new posts, if I'd know I woulda carried on in this one. Storing that one for future use.

---

### Post by chili555 on 2014-11-12
In your lsusb, we don't see a wireless device, we see:> ID 0fe6:8101 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast *Ethernet* AdapterIsn't this it? [http://www.zoobab.com/cheap-usb-ethernet](http://www.zoobab.com/cheap-usb-ethernet) 

Do you have something else that wasn't in the USB slot at the time?

---

### Post by coffeecat on 2014-11-12
> **levi5 said:**
> The usb insert has the ability to connect to wifi networks, a little like a dongle, but the wifi networks have to be pre-existing e.g. a home hub or wireless router. 

That would be a very clever USB dongle that could connect to a wifi network that doesn't exist! But why not reveal the mystery and tell us the make and model of the wifi dongle?

> **levi5 said:**
> It came with a minidisk of drivers but I have no idea how to do so 

For the second time - forget that for now. You are very unlikely to need it. First we need to identify the wireless device, but unless I'm missing something I can't see any wireless device listed in your wireless script output. But what is listed is an ethernet device on the motherboard:

> **levi5 said:**
> ```

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:230f]
	Kernel driver in use: r8169
```

And a USB to ethernet adapter:

> **levi5 said:**
> ```
  
Bus 004 Device 003: ID 0fe6:8101 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter
```

Were you aware that you had a USB to ethernet adapter? Are you sure the thing you think is a wireless adapter is a wireless adapter? If it is, was the wireless adapter plugged in when you ran the script?

---

### Post by levi5 on 2014-11-12
No, the ethernet adapter also allows for wifi capability, my sister uses the same one. As for make/model, I haven't the foggiest. It was bought with the device and the minidisk in a plastic bag type thing with no mention of make or model. Sounds dodgy but thats how I bought it and as I said my sister uses the same thing to enable wifi on her own windows pc.

---

### Post by levi5 on 2014-11-12
Just trust me when I say this is the device that enabled wifi on my sister's pc lol, she had no problems with installation because the windows drivers on the disk have a .exe installation wizard. No such luck for linux.

---

### Post by chili555 on 2014-11-12
I trust you and I trust your sister; I just don't trust the guy that sold you a network device in a ziplock bag! Lots of dodgy things are sold in a ziplock in my part of the woods!

What are the files on the disk?

---

### Post by levi5 on 2014-11-12
I found a sticker on the bottom of the device that may or may not identify the device for some google ultraresearcher or super pro, it says > TC NUMBER 2008-07-888a does this help at all?

---

### Post by levi5 on 2014-11-12
Also, the seller was a reputable (if overpriced) pc shop on our local main street, we have never had problems there before.

---

### Post by chili555 on 2014-11-12
> **levi5 said:**
> Also, the seller was a reputable (if overpriced) pc shop on our local main street, we have never had problems there before.Maybe he just made an understandable mistake. People make mistakes.

What are the files on the driver disk?

Perhaps you'll call or email your sister and ask if she also has a TC NUMBER 2008-07-888a.

---

### Post by levi5 on 2014-11-12
Um, one sec, I'll find a dropbox-y site

---

### Post by levi5 on 2014-11-12
Okay, first is the infamous unclear readme.txt  [https://www.dropbox.com/s/oohutwuo4dclkje/ReadMe.txt?dl=0](https://www.dropbox.com/s/oohutwuo4dclkje/ReadMe.txt?dl=0)     next up is a file simply labelled Makefile, no file extension  [https://www.dropbox.com/s/lh7bl5e5rifv14n/Makefile?dl=0](https://www.dropbox.com/s/lh7bl5e5rifv14n/Makefile?dl=0)  and finally a stange cryptically named file with a .c extension  [https://www.dropbox.com/s/dlf875p5erc56q0/pl2303.c?dl=0](https://www.dropbox.com/s/dlf875p5erc56q0/pl2303.c?dl=0)   this help anyone?

---

### Post by levi5 on 2014-11-12
She's in the other room, I confirmed that one instantly. She has the same thing, only difference is that she is using windows 7 so she had an automatic installer.

---

### Post by levi5 on 2014-11-12
By the way, those files are in a folder labelled RedHat 73, there are also folders with similar setups labelled redhat 8 and redhat 9 in the linux folder, nothing else there.

---

### Post by chili555 on 2014-11-12
Here are quotes from the files:> * Prolific PL2303 USB to serial adaptor driver
 *
 * Copyright (C) 2001 Greg Kroah-Hartman (greg@kroah.com)
 *
 * Original driver for 2.2.x by anonymousYou certainly do not have a USB to serial adapter. You are certainly not running a 2.2 kernel and, I assure you, anything last amended in 2001 won't work on any recent Linux kernel. > She's in the other room, I confirmed that one instantly. She has the same thing, only difference is that she is using windows 7 so she had an automatic installer.Can you borrow it for a few moments, insert it in your computer, open a terminal and run:```
lsusb
```What do you get?

---

### Post by levi5 on 2014-11-13
I'll grab it now, I didn't realise it was so out of date!

---

### Post by levi5 on 2014-11-13
Okay, I ran the code and got this with hers plugged in.  ```
[COLOR=#000000]Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 004: ID 1c4f:0048 SiGma Micro 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1a2c:0c21 China Resource Semico Co., Ltd 
Bus 004 Device 017: ID 0fe6:8101 Kontron (Industrial Computer Source / ICS Advent) DM9601 Fast Ethernet Adapter [COLOR=#000000]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR]
```

---

### Post by chili555 on 2014-11-13
I am stunned and not just a little skeptical. While I would enjoy troubleshooting this to death for a couple of days using both your and your sister's computers, it gets us no closer to the answer. 

Here is what I see; you have:```
0fe6:8101 Kontron (Industrial Computer Source / ICS Advent) [COLOR="#FF0000"]DM9601[/COLOR] Fast Ethernet Adapter
```It has a driver and it loads:```
- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  [COLOR="#FF0000"]Driver:            dm9601[/COLOR]
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off

```When the system is asked what wireless channels it can do, it reports none:```
eth1      no frequency information.
```When it is asked for the result of a scan for nearby wireless access points, it reports that it is incapable of scanning:```
eth1      Interface doesn't support scanning.
```Now, let's look at the details of the driver that loads when the device is inserted:```
chili@T410:~$ modinfo dm9601 
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/usb/dm9601.ko
license:        GPL
description:    Davicom DM96xx USB [COLOR="#FF0000"]10/100 ethernet devices[/COLOR]
author:         Peter Korsgaard <jacmet@sunsite.dk>
srcversion:     8B2420E93E78CEA9AB0E3DA

```Finally, a Google search of the usb.id 0fe6:8101 shows no mention whatever of wireless capability.

I regret that my answer is still the same. Drop this back in the ziplock and return it for a supported wireless device. There are many threads here about supported devices and I urge you to research before you buy.

---

### Post by coffeecat on 2014-11-13
@levi5, I have to concur with chili555, who knows much more about wireless devices than I do anyway. The product ID - 0fe6:8101 - is unique and google hits tell us that it is a USB to ethernet adapter with no wireless capabilities. Perhaps your sister has a separate wireless device or an inbuilt one and her Kontron device is not being used.

Whatever the answer, I can save you further weeping if you are prepared to shell out the equivalent of a small round of beers. I have two of these. They work out of the box in Ubuntu 14.04 and later. No configuration necessary, except for typing in your WPA passkey on first connection. They are plug in and use in Ubuntu.

[http://www.amazon.co.uk/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002SZEOLG/ref=sr_1_1?ie=UTF8&qid=1415887260&sr=8-1&keywords=TP-LINK+TL-WN722N](http://www.amazon.co.uk/TP-Link-TL-WN722N-150Mbps-Wireless-Adapter/dp/B002SZEOLG/ref=sr_1_1?ie=UTF8&qid=1415887260&sr=8-1&keywords=TP-LINK+TL-WN722N)

---

### Post by coffeecat on 2014-11-14
> **coffeecat said:**
> I can save you further weeping if you are prepared to shell out the equivalent of a small round of beers.

@levi5, I've just noticed this on the Amazon site. If you throw in the cost of a bag of salted peanuts, you can get one of those with a USB cradle. :wink: Much more convenient and all for the price of a bag of nuts!

Just click on the link I posted above and then click on the 150M with cradle button. £9.73 (at the moment) compared with £8.00.

---

