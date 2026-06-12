---
title: "Wireless Internet not accessible"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by Luje on 2005-07-08
Hey, everyone.
I'm running ubuntu 5.04 and my big problem is that no matter which wireless nic card (PCI) I'm using, I can't connect to the network at my home.  I live with a few roommates who have a wireless router.  I can't even get Linux to recognize that I have (two) PCI wireless cards.  All I need to know is how I can configure it to recognize it and pick up the DHCP.

Any help is appreciated.  I know almost nothing about Linux.

---

### Post by Lunde on 2005-07-08
You need to list the cards you have, and what type of encryption your access point use.

---

### Post by Luje on 2005-07-08
I have no idea what kind of encyrption is used.  I have a Linksys and a Netgear.  The linksys is in right now. Searching on some other sites I found a bit about using ndiswrapper to use the drivers from the CD.  Does ndiswrapper come on Ubuntu?  'Cause if so, I'm all set.  I'm not at home right now because I can't connect there-- so I can't very well check what type of encryption or if Ubuntu has this ndiswrapper.

---

### Post by Lunde on 2005-07-08
The ndiswrapper-source is included I think. check it out in synaptics

**WiFiHowto**
[https://wiki.ubuntu.com//WiFiHowto](https://wiki.ubuntu.com//WiFiHowto)

**HOWTO: WLan via Ndiswrapper**
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

**Linux Wireless Networking**
[http://www.linuxhomenetworking.com/linux-hn/wmp11-linux.htm](http://www.linuxhomenetworking.com/linux-hn/wmp11-linux.htm)
[B]
Some nice reading[/B]
[http://www.linux-wireless.org/](http://www.linux-wireless.org/)

---

### Post by Aphix on 2005-07-08
I have the same problem with my network. I have Ubuntu 5.04 and for some reason I can't seem to connect to my wireless network. Any help would be appreciated for both of us. As for me, I have the following things:

Linksys BEFW11S4 Wirless-B Router
D-Link Air DWL-520 Wireless PCI Card

-WEP Encryption disabled at the moment
-SSID broadcast turned ON

---

### Post by Luje on 2005-07-09
i tried it with the ndiswrapper-- but when I do -l to list it says that they are invalid drivers!  Anything I did wrong?  Anything I can do to fix this?

---

### Post by Lunde on 2005-07-09
[QUOTE=Aphix]I have the same problem with my network. I have Ubuntu 5.04 and for some reason I can't seem to connect to my wireless network. Any help would be appreciated for both of us. As for me, I have the following things:

Linksys BEFW11S4 Wirless-B Router
D-Link Air DWL-520 Wireless PCI Card

-WEP Encryption disabled at the moment
-SSID broadcast turned ON[/QUOTE]
 Can you post the output of:
$ lspci -n
to identify your card?

---

### Post by Lunde on 2005-07-09
[QUOTE=Luje]i tried it with the ndiswrapper-- but when I do -l to list it says that they are invalid drivers!  Anything I did wrong?  Anything I can do to fix this?[/QUOTE]
Do you have the full model number of your cards?

---

### Post by t2kburl on 2005-07-09
I'm following along since I have the same issues ... still working on downloading all the packages I need on a wired (and slower) connection.
My device is a USB, and here is the output of lsusb

Bus 001 Device 002: ID 8086:1111 Intel Corp. PRO/Wireless 2011B 802.11b Adapter

---

### Post by Lunde on 2005-07-09
[QUOTE=t2kburl]I'm following along since I have the same issues ... still working on downloading all the packages I need on a wired (and slower) connection.
My device is a USB, and here is the output of lsusb

Bus 001 Device 002: ID 8086:1111 Intel Corp. PRO/Wireless 2011B 802.11b Adapter[/QUOTE]
 is this your card? 
Intel USB 
**Product number:** WUD 2011B 
**Chipset:** Prism2/2.5/3

The packet **linux-wlan-ng** is included in Ubuntu and can be installed through Synaptics.

For more details, check out the following links:

There's a howto for Linux here:
[http://www.fuw.edu.pl/~pliszka/hints/prism2.html](http://www.fuw.edu.pl/~pliszka/hints/prism2.html)

Faq here:
[ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/FAQ](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/FAQ)

---

### Post by t2kburl on 2005-07-09
ok ... I installed the packages with synaptic, but I can't tell what to do with it based on the other pages, so I tried installing from source. It configures OK, but make all fails with the following error message:

/usr/src/linux-headers-2.6.10-5-686/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
make[2]: *** [.depend] Error 1
make[2]: Leaving directory `/home/ted/linux-wlan-ng-0.2.0/src/p80211'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ted/linux-wlan-ng-0.2.0/src'
make: *** [all] Error 2


so I'm still stuck   ](*,)

---

### Post by t2kburl on 2005-07-09
I have forged ahead ... since the package DID install in Synaptic ... I found some of the files and started reading through scripts to try to find out what is happening and where...

I tried this: 
ted@ubuntu:~$ //etc/init.d/wlan stop
/etc/wlan/shared: line 91: /etc/wlan/shared.*: No such file or directory
ted@ubuntu:~$ /etc/init.d/wlan start
/etc/wlan/shared: line 91: /etc/wlan/shared.*: No such file or directory


Problem is ... /etc/wlan/shared DOES exist   ????
this seems to be the stopping point though ...  no idea why

---

### Post by Lunde on 2005-07-09
[QUOTE=t2kburl]I have forged ahead ... since the package DID install in Synaptic ... I found some of the files and started reading through scripts to try to find out what is happening and where...

I tried this: 
ted@ubuntu:~$ //etc/init.d/wlan stop
/etc/wlan/shared: line 91: /etc/wlan/shared.*: No such file or directory
ted@ubuntu:~$ /etc/init.d/wlan start
/etc/wlan/shared: line 91: /etc/wlan/shared.*: No such file or directory


Problem is ... /etc/wlan/shared DOES exist   ????
this seems to be the stopping point though ...  no idea why[/QUOTE]
 Are you logged in as root? or do you use sudo?
Maybe you have to give the right permissions to the directory 
sudo chmod -R 775 /etc/wlan/shared

---

### Post by Lunde on 2005-07-09
[QUOTE=t2kburl]ok ... I installed the packages with synaptic, but I can't tell what to do with it based on the other pages, so I tried installing from source. It configures OK, but make all fails with the following error message:

/usr/src/linux-headers-2.6.10-5-686/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
make[2]: *** [.depend] Error 1
make[2]: Leaving directory `/home/ted/linux-wlan-ng-0.2.0/src/p80211'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/ted/linux-wlan-ng-0.2.0/src'
make: *** [all] Error 2


so I'm still stuck   ](*,)[/QUOTE]
 Have you installed the linux headers?
$ sudo apt-get install linux-headers-2.6.10-5-686

Anyway it might be better to use the Ubuntu package if you figure it out.

---

### Post by t2kburl on 2005-07-09
yes ... I have the headers installed, but I've given up on that route ...   the install guide is for Red hat and contains commands that do not exist in Ubuntu (chkconfig ??) and lists files and directories that do not exist in Ubuntu. I'm way too much of a nOOb to know what is equivalent.
Anyway ... I just rebooted and ran dmesg ...  found this @ the end :

hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-2: new full speed USB device using uhci_hcd and address 2
usb 1-2: config 1 has an invalid interface number: 1 but max is 0
usb 1-2: config 1 has no interface number 0
prism2usb_init: prism2_usb.o: 0.2.1-pre25 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 11 (level, low) -> IRQ 11
eth0: RealTek RTL8139 at 0xe000, 00:50:22:b0:6d:de, IRQ 11
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 10 (level, low) -> IRQ 10
NET: Registered protocol family 17
usb 1-2: grep timed out on ep0in
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
usb 1-2: epson timed out on ep0in
eth0: no IPv6 routers present
usb 1-2: epson timed out on ep0in
usb 1-2: hald timed out on ep0in
usb 1-2: hald timed out on ep0in
usb 1-2: canon timed out on ep0in
usb 1-2: canon timed out on ep0in


If I could get that interface number to change to a 0 from a 1 I just might get somewhere. Any ideas?

Thanks for all your help

---

### Post by Luje on 2005-07-09
Lunde, my output of the command is as follows:

0000:00:00.0 0600: 1106:3116
0000:00:01.0 0604: 1106:b091
0000:00:05.0 0280: 1814:0201 (rev 01)
0000:00:07.0 0780: 11c1:044e (rev 02)
0000:00:10.0 0c03: 1106:3038 (rev 80)
0000:00:10.1 0c03: 1106:3038 (rev 80)
0000:00:10.2 0c03: 1106:3038 (rev 80)
0000:00:10.3 0c03: 1106:3104 (rev 82)
0000:00:11.0 0601: 1106:3177
0000:00:11.1 0101: 1106:0571 (rev 06)
0000:00:11.5 0401: 1106:3059 (rev 50)
0000:00:12.0 0200: 1106:3065 (rev 74)
0000:01:00.0 0300: 5333:8d04
0000:00:00.0 0600: 1106:3116
0000:00:01.0 0604: 1106:b091
0000:00:05.0 0280: 1814:0201 (rev 01)
0000:00:07.0 0780: 11c1:044e (rev 02)
0000:00:10.0 0c03: 1106:3038 (rev 80)
0000:00:10.1 0c03: 1106:3038 (rev 80)
0000:00:10.2 0c03: 1106:3038 (rev 80)
0000:00:10.3 0c03: 1106:3104 (rev 82)
0000:00:11.0 0601: 1106:3177
0000:00:11.1 0101: 1106:0571 (rev 06)
0000:00:11.5 0401: 1106:3059 (rev 50)
0000:00:12.0 0200: 1106:3065 (rev 74)
0000:01:00.0 0300: 5333:8d04

The model numbers of my wireless pci cards are this:
Netgear wg311T
and
Linksys wmp54g version 4.0

the Linksys is the one I have in my computer right now

---

### Post by Lunde on 2005-07-09
You're getting somewhere it looks like. what have you done until now? do you see tha interface in iwconfig?

---

### Post by t2kburl on 2005-07-09
i have edited the wlan.conf script to include my SSID and WEP key ... got that far with that link to the red hat guide. But that is about all I've done, besides read a lot of scripts.

no wireless extensions anywhere in my iwconfig

---

### Post by Luje on 2005-07-09
what's this iwconfig?  I typed it in the terminal and said the command wasn't found.  I'm in a jam with this!

---

### Post by Lunde on 2005-07-09
[QUOTE=t2kburl]i have edited the wlan.conf script to include my SSID and WEP key ... got that far with that link to the red hat guide. But that is about all I've done, besides read a lot of scripts.

no wireless extensions anywhere in my iwconfig[/QUOTE]
 I found this.. intresting. It's for Warty, the previous release, but it may still work.
[QUOTE=azz]I have the same device.  But I don't use it.  I tried to get it to work once with Ubuntu, but didn't try for very long.

The fact that the correct prism2_usb modules get loaded when plugged it means that the drivers are present in Ubuntu.  Compiling the drivers again will not be neccessary.

I was going to try the command line to get it going.  I remember using the device with sarge and I had to tell the device to reset and to turn on the radio (broadcast) manually before it would actually work.

Here is the quote from the readme:
FOR USB USERS:

A) Make sure your kernel usb support is running
B) Plug in the Prism2.x USB device
C) Run 'modprobe prism2_usb prism2_doreset=1' to load the driver into memory.
D) Run 'wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable' to initialize the
   driver+MAC functions.
E) Run 'wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem'
   to enable the MAC in Infrastructure Station mode.
F) Run 'ifconfig wlan0 <your IP address>'

Or, you can use the provided hotplug scripts, if your distribution has
hotplug support.  :) 

IMPORTANT: Due to an issue with some versions of the Prism USB firmware,
the driver usually needs to perform a port reset.  

Some combinations of usb low-level drivers, kernel releases, and
hardware don't like this, and usually end up generating a kernel OOPS.
newer kernels are much better in this regard.  In particular, Intel usb
controllers are the most trouble-prone.



I also think this is relevant:

Add an alias for wlan0 in /etc/modules.conf.  For example, a usb 
   interface on wlan0 would be set up as:

   alias wlan0 prism2_usb

   Substitute prism2_plx or prism2_pci as appropriate.

I will try this tonight...


Also (just to be a complete geek) I was too lazy to look up the README so I tried to use ndiswrapper.  I think that the version of ndiswrapper in Ubuntu is the one just before DWL-122 was added to their supported cards.  The new version (.11) does work.  I tried making those modules and updating ndiswrapper-utils (I remodes the old packages first...)  But I could not get it to work.  My baby started to cry and so I gave up at that point.

I had not bothered to unload the prism_2 modules which were loaded with hotplug.  That may have been why ndiswrapper did not work...   Something else I can try tonight.[/QUOTE]

Let me know how it goes

---

### Post by Luje on 2005-07-09
I just installed via ndiswrapper the drivers from the netgear CD.  I think I had a success because it said, "driver present." when I typed in: ndiswrapper -l

Now to reboot and put the netgear PCI card in here and see if that does anything.

---

### Post by Lunde on 2005-07-09
[QUOTE=Luje]what's this iwconfig?  I typed it in the terminal and said the command wasn't found.  I'm in a jam with this![/QUOTE]
 ifconfig is a wireless tool. I'm checking up on your card now, get back to you soon

---

### Post by Lunde on 2005-07-09
[QUOTE=Luje]I just installed via ndiswrapper the drivers from the netgear CD.  I think I had a success because it said, "driver present." when I typed in: ndiswrapper -l

Now to reboot and put the netgear PCI card in here and see if that does anything.[/QUOTE]
 Good! hope it's working

---

### Post by Lunde on 2005-07-09
[QUOTE=Lunde]I found this.. intresting. It's for Warty, the previous release, but it may still work.


Let me know how it goes[/QUOTE]
 Forgot to post the link to the tread, here it is:
[http://ubuntuforums.org/showthread.php?t=4041](http://ubuntuforums.org/showthread.php?t=4041)

---

### Post by t2kburl on 2005-07-09
root@ubuntu:/home/ted # wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
message=lnxreq_ifstate
  ifstate=enable
  resultcode=implementation_failure



 ](*,)

root@ubuntu:/home/ted # lsmod | grep prism
prism2_usb             78084  0
p80211                 33328  1 prism2_usb
usbcore               119000  3 prism2_usb,uhci_hcd

the drivers are in there, but it just isn't working

after doing this I ran dmesg again ....

usb 1-2: USB disconnect, address 2
usb 1-1: new full speed USB device using uhci_hcd and address 3
usb 1-1: config 1 has an invalid interface number: 1 but max is 0
usb 1-1: config 1 has no interface number 0
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
usb 1-1: hald timed out on ep0in
hfa384x_docmd: ctlx failure=REQ_TIMEOUT
hfa384x_drvr_start: cmd_initialize() failed, result=-5
prism2sta_ifstate: hfa384x_drvr_start() failed,result=-5


I plugged it in to the other USB port ...   not that it matters, since it should be hotplugging, right?

maybe I should try ndiswrapper too

---

### Post by Lunde on 2005-07-09
did you try this?
[QUOTE=pdaliu]Hi:
  I've just made my DWL-122 work on Ubuntu (Hoary PowerPC) without any other outside package or driver input.  I hope it helps.

0) Make sure your linux-wlan-ng package is installed.

1) Try plug your DWL-122 and use lsmod to see if prism2_usb is appropriately loaded.  If no, your kernel has something wrong.  The module is even bundled in Warty.

2) Find the follwing line in /etc/network/if-pre-up.d/linux-wlan-ng-pre-up

result=`$WLANCTL $IFACE lnxreq_ifstate ifstate=enable`

    And let this line executed TWICE.  Yes, twice.  It seems successful initiation needs two visits.

3) My wireless network is simple, i.e. MAC filter without any WEP.  So I added the following to /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
        wireless_essid  your_essid
        wireless_mode   infrastructure

4) ifup wlan0

Then it should work![/QUOTE]
Not a problem that it's a different card, it's the same chipset

---

### Post by Luje on 2005-07-09
I just installed the Netgear card (the one with the driver that shows up in ndiswrapper -l) but I can't connect wirelessly.  When I go to System | Networking, it only shows modem and eth0.

Can someone point me to the next step please?

---

### Post by Lunde on 2005-07-09
[QUOTE=Luje]I just installed the Netgear card (the one with the driver that shows up in ndiswrapper -l) but I can't connect wirelessly.  When I go to System | Networking, it only shows modem and eth0.

Can someone point me to the next step please?[/QUOTE]
 Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

And maybe you need to install the wireless tools?
$ sudo apt-get install wireless-tools

---

### Post by t2kburl on 2005-07-09
Ok ... I edited the script as the 1 post suggested ... rebooted and here we are now :

root@ubuntu:/home/ted # lsmod | grep prism
prism2_usb             78084  0
p80211                 33328  1 prism2_usb
usbcore               119000  3 prism2_usb,uhci_hcd
root@ubuntu:/home/ted # lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 8086:1111 Intel Corp. PRO/Wireless 2011B 802.11b Adapter
Bus 001 Device 001: ID 0000:0000
root@ubuntu:/home/ted # modprobe prism2_usb prism2_doreset=1
root@ubuntu:/home/ted # wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
message=lnxreq_ifstate
  ifstate=enable
  resultcode=implementation_failure

the wired net works here, but it is a long stretch of cable ...  I'm about to get the staple gun and drill out to just run the freaking wire

it may be noteworthy that at no time do the lights on the USB device ever come on. It is a steady green when I boot this machine into windows.

I'll give ndiswrapper a shot I guess ...  nothing to lose but more frustration, right

Thanks for all your time Lunde, I really appreciate it

---

### Post by Luje on 2005-07-09
Lunde, I tried the page you recommended, but still I'm getting nothing.  In system | networking I'm still only seeing modem and my ethernet (cable connection).  No wireless devices are listed. :(

---

### Post by Lunde on 2005-07-09
I gotta go.. I'll help you out tomorrow if you don't find a solution

---

### Post by t2kburl on 2005-07-09
Hey Luje ... sorry for jumping in on your thread

looks like we're both out of luck today

have a cold one ... on me

---

### Post by Luje on 2005-07-09
trying the page you suggested from the top, I get this message after typing in the first line:

FATAL: Module bcmwl5 not found.

Anything I can do to get around that?

---

### Post by t2kburl on 2005-07-09
Hey  ... something changed !!

I lost eth0 now too    ](*,)  ](*,)  ](*,)

---

### Post by t2kburl on 2005-07-09
DOH!

Turns out I had bumped loose the ethernet cable and it wasn't connected, so eth0 is fine

wlan still isn't there ...  it just refuses to initialize

During bootup I get a sequence of 4 lines that end in:
failed to initialize exit code = -5

no doubt that is the USB wlan device.

---

### Post by Luje on 2005-07-10
Here's an update on my problem-- I followed your link, Lunde, and tried the step-by-step by copying and pasting.  So the driver that was showing up was the one that was listed in that user's example.  When I try to install my own drivers, ndiswrapper -l reveals that the drivers are invalid!  I have no idea what's going on with this!  It seems all I need is to get past those drivers and then I'd be all set.  I'm absolutely lost.  Any help is greatly appreciated.

---

### Post by Lunde on 2005-07-11
[QUOTE=Luje]trying the page you suggested from the top, I get this message after typing in the first line:

FATAL: Module bcmwl5 not found.

Anything I can do to get around that?[/QUOTE]
 Maybe this will help
[http://ubuntuforums.org/showthread.php?t=29046](http://ubuntuforums.org/showthread.php?t=29046)

---

### Post by Lunde on 2005-07-11
[QUOTE=Luje]Here's an update on my problem-- I followed your link, Lunde, and tried the step-by-step by copying and pasting.  So the driver that was showing up was the one that was listed in that user's example.  When I try to install my own drivers, ndiswrapper -l reveals that the drivers are invalid!  I have no idea what's going on with this!  It seems all I need is to get past those drivers and then I'd be all set.  I'm absolutely lost.  Any help is greatly appreciated.[/QUOTE]
 **Netgear wg311T**
They say it's supposed to work out of the box, but some people have problems with it:
[http://ubuntuforums.org/showthread.php?t=25534](http://ubuntuforums.org/showthread.php?t=25534)

As in the link below, the ndiswrapper may not supprt this card:
Here's an Ubuntu user who had the same problem with the Netgear wg311T
[http://lists.ubuntu.com/archives/ubuntu-users/2005-April/031640.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-April/031640.html)
[http://lists.ubuntu.com/archives/ubuntu-users/2005-April/031855.html](http://lists.ubuntu.com/archives/ubuntu-users/2005-April/031855.html)

**He used the Linuxant driver:**
[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)
But you may not want to pay for it... so: 

**Success story of another user with the Netgear wg311T**
[QUOTE=DagaZ]Using the guide of IcemanV9 I got my Netgear WG311T up and running in no-time. My bridged firewall works great![/QUOTE]

[QUOTE=IcemanV9]Your info does help me to resolve the problem with my new cardbus adapter, D-Link DWL-G650.

Here's what I did:

wget [http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz](http://otaku42.de/madwifi/madwifi-cvs-current.tar.gz)
sudo apt-get install build-essential (only if you don't have it)
sudo apt-get install linux-headers-(uname -r) (again, only if you don't have it)
sudo apt-get install sharutils

tar xvzf madwifi-cvs-current.tar.gz
cd madwifi
KERNELPATH=/usr/src/linux-headers-(uname -r); export KERNELPATH
KERNELRELEASE=(uname -r); export KERNELRELEASE
sudo make
sudo make install

sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko.orig
sudo mv /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko.orig

sudo cp /lib/modules/2.6.10-5-686/net/ath_rate_onoe.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_rate/onoe/ath_rate_onoe.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_hal.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath_hal/ath_hal.ko
sudo cp /lib/modules/2.6.10-5-686/net/ath_pci.ko /lib/modules/2.6.10-5-686/kernel/drivers/net/wireless/ath/ath_pci.ko

reboot (leave your cardbus in the slot)

when boot up, it will recongize the cardbus adapter (without an error message)!

To TEST ath0, I just used some commands from jaykay's instruction. AND, it works great.[/QUOTE]
These posts are located in this tread:
[http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972)

**Linksys wmp54g**
If this is the card you try with Ndiswrapper, you may need a different driver
Success story of a Ubuntu user wtih Linksys wmp54g:
[http://www.ubuntuforums.org/showthread.php?t=42193](http://www.ubuntuforums.org/showthread.php?t=42193)

I hope this helped you get your cards running

---

### Post by Lunde on 2005-07-11
[QUOTE=t2kburl]DOH!

Turns out I had bumped loose the ethernet cable and it wasn't connected, so eth0 is fine

wlan still isn't there ...  it just refuses to initialize

During bootup I get a sequence of 4 lines that end in:
failed to initialize exit code = -5

no doubt that is the USB wlan device.[/QUOTE]
 [QUOTE=azz]I blacklisted the prism2_usb and the p80211 modules (/etc/hotplug)
I compiled the most recent ndiswrapper modules and ndiswrapper-utils and installed them

cd to the driver's directory
sudo ndiswrapper -i  NETPRISM.inf

plug the sucker in.

Configure the interface with the networking tool.  This works because ndiswrapper uses wireless extentions.  The linux-wlan-ng uses it's own commands and the Gnome network tool interface does not yet support that.

It is ironic that it is easier to use Windows drivers in Gnome as opposed to the GPL driver for this device...[/QUOTE]

It sais you may have to blacklist the prism2_usb and the p80211 modules before running it with the Ndiswrapper, did you do this?

Located in tread:
[http://ubuntuforums.org/newreply.php?do=newreply&p=15720](http://ubuntuforums.org/newreply.php?do=newreply&p=15720)

---

### Post by t2kburl on 2005-07-11
[QUOTE=Lunde]It sais you may have to blacklist the prism2_usb and the p80211 modules before running it with the Ndiswrapper, did you do this?

Located in tread:
[http://ubuntuforums.org/newreply.php?do=newreply&p=15720](http://ubuntuforums.org/newreply.php?do=newreply&p=15720)[/QUOTE]


nope.   but ndiswrapper said the drivers were invalid, they are not the NETPRISM.inf that azz had they are wlanusb.inf

---

### Post by t2kburl on 2005-07-11
just a hunch ...   on this page : [http://www.fuw.edu.pl/~pliszka/hints/prism2.html](http://www.fuw.edu.pl/~pliszka/hints/prism2.html)

It says some interesting things in the Troubleshooting section, which I think might solve my problem. Except that it refers to Red Hat files and commands that are different in Ubuntu. If I could find the equivalent files to edit, and command to use (in place of chkconfig) I just might have it.

---

### Post by Lunde on 2005-07-11
[QUOTE=t2kburl]nope.   but ndiswrapper said the drivers were invalid, they are not the NETPRISM.inf that azz had they are wlanusb.inf[/QUOTE]
 Did you try the drivers Azz is talking about? it may not be the correct windows drivers for you, but it's the same chipset inside.

I think you should give it a try

---

### Post by t2kburl on 2005-07-11
Ok ... I googled and found the netprism driver ... I'll give it a shot 

[http://www.dynamiclink.nl/inf/info_inf/info_n/184.htm](http://www.dynamiclink.nl/inf/info_inf/info_n/184.htm)

---

### Post by t2kburl on 2005-07-11
how do I blacklist it?

just comment out the line?


-----edit   nm  found it

---

### Post by Lunde on 2005-07-11
[QUOTE=t2kburl]how do I blacklist it?

just comment out the line?


-----edit   nm  found it[/QUOTE]
 I guess it's just like this.. 

$ sudo gedit /etc/hotplug/blacklist

The add these two lines:
prism2_usb
p80211

---

### Post by t2kburl on 2005-07-11
OK ... I got the blacklist right  :)
installed ndiswrapper and the netprism.inf driver ...  rebooted
now :

ed@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
netprism        invalid driver!
in dmesg I still get this:
usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: config 1 has an invalid interface number: 1 but max is 0
usb 1-1: config 1 has no interface number 0

which I think must be the key to moving forward here

---

### Post by t2kburl on 2005-07-11
well ... I may be on to something, because now I have different stuff in my dmesg.

Here's what I've done
1) Completely removed all previous installations of ndiswrapper and linux-wlan-ng
2) Downloaded and compiled from source the latest version of linux-wlan-ng
(no errors during configure or make or make install)
3) edited the /etc/wlan.conf file to include my SSID
4) built the wlan-boot-fix script from this page [http://www.fuw.edu.pl/~pliszka/hints/prism2.html](http://www.fuw.edu.pl/~pliszka/hints/prism2.html) and placed it in /etc/init.d

Now I get this in dmesg:

usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-1: device descriptor read/64, error -71
usb 1-1: device descriptor read/64, error -71
usb 1-1: new full speed USB device using uhci_hcd and address 3
usb 1-1: device descriptor read/64, error -71
usb 1-1: device descriptor read/64, error -71

and no devices appear at all when I do ~lsusb

oddly enough, the lights are on on the device now, but wlan0 does not appear in ~iwconfig

I'm not sure if this is a step in the right direction or not, but it is the 1st time the lights are on and the device appears to at least interface with the USB controller and (I think) initialize before erroring out

google gives me nothing with the same error message
any ideas?

---

### Post by Lunde on 2005-07-11
There may be something wrong with your kernel. Do you use any other USB devices? Are you able to use USB devices at all? Which kernel are you on? 
$ uname -a

---

### Post by t2kburl on 2005-07-11
this is the only USB device I have used on this machine

$ uname -a
Linux ubuntu 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686 GNU/Linux

---

### Post by Lunde on 2005-07-11
[QUOTE=t2kburl]this is the only USB device I have used on this machine

$ uname -a
Linux ubuntu 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686 GNU/Linux[/QUOTE]
 I found something regarding USB and Ubuntu
*I think this is a general Ubuntu problem! Hotplug will install two host controllers: ehci_hcd and uhci_hcd. I noticed that my USB stick would behave funny with both modules in the kernel at the same time. (It seemed that the stick was passed between the two controllers, but never quite being handled by either.) I created the file /etc/hotplub/blacklist.d/local and put ehci_hcd in it to prevent it from being loaded.*

can you try something? 
can you blacklist first the: **ehci_hcd**, not like described above, but like you blacklisted earlier. if this does nothing. remove the blacklisting and try to blacklist **uhci_hcd** and test that. if this does not help then remove the blacklisting.

I assume you have configured a startup script for the Wireless card

---

### Post by t2kburl on 2005-07-11
I think we're getting somewhere ...

with uhci_hcd blacklisted I got this from dmesg:

usbcore: registered new driver usbfs
usbcore: registered new driver hub
prism2usb_init: prism2_usb.o: 0.2.1-pre25 Loaded
prism2usb_init: dev_info is: prism2_usb
usbcore: registered new driver prism2_usb
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
...
NET: Registered protocol family 17
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
NET: Registered protocol family 10

but iwconfig:

no wlano at all

and lsusb ~ nothing at all

as for the startup script - from the page I followed to install the drivers:
[http://www.groomlakelabs.com/grandamp/how-to/usb_wireless-howto.txt](http://www.groomlakelabs.com/grandamp/how-to/usb_wireless-howto.txt)


8. Add the following to: /etc/rc.d/rc.S    (I put this into /etc/init.d/rcS and changed it to read "Intel 2011B USB")

	# Start the Linux-Wlan 802.11 interface
	if [ -x /etc/rc.d/rc.wlan ]; then
	  echo "Starting Linksys WUSB11 v2.5 802.11 interface"
	  /etc/init.d/rc.wlan start
	fi

9. Add the following to: /etc/rc.d/rc.modules   (I put this in /etc/init.d/module-init-tools)   (and changed it to read "Intel 2011B USB")

	### Linksys WUSB11 v2.5 support
	/sbin/modprobe prism2_usb prism2_doreset=1

along with following the rest of the instructions ....
I'm not sure those were the correct files to edit, but the ones referenced do not exist

Step 5 from this page: [http://www.fuw.edu.pl/~pliszka/hints/prism2.html](http://www.fuw.edu.pl/~pliszka/hints/prism2.html)
also refers to creating a script, but the directory does not exist, and I have no idea where to put this, so I have not made it.

---

### Post by Lunde on 2005-07-11
What happens if you type:

$ sudo modprobe prism2_usb prism2_doreset=1
$ sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
$ sudo wlanctl-ng wlan0 lnxreq_autojoin ssid=<my SSID> authtype=opensystem
$ sudo dhclient wlan0

---

### Post by t2kburl on 2005-07-11
I'll give it a try tomorrow ... I am away from that machine for now ....

---

### Post by gkozlyk on 2005-07-11
I am new relatively to Ubuntu.  I have been working on a tower trying to get internet on it.  I have a D-Link DWL-G122 A2 USB card that i am trying to get a Ubuntu fresh install to recognize, so i can download updates, etc.  I have access to internet via a windows system (so i can get .deb files and dpkg them).  I have been able to install ndiswrapper with dependancies, wlanctl-ng, and associated files that were recommended via the Ubuntu Wiki help files.  In lsusb, the card is recognized with a hex address, and under ndiswrapper -l it shows now that i have a prisma02 driver present with hardware present, however under network devices it isn't available, nor is a wlan0 available under ifconfig.  I added headers as well.  Is there anything i am missing?  

thank you for your help.  This thread was the most helpful of all, so i figured i would post it to you guys :)

Email or post if you have ideas.  I do have a 10/100 card in the box, but only have access to wifi due to landlords and walls and such :)

Graham

---

### Post by Lunde on 2005-07-13
[QUOTE=gkozlyk]I am new relatively to Ubuntu.  I have been working on a tower trying to get internet on it.  I have a D-Link DWL-G122 A2 USB card that i am trying to get a Ubuntu fresh install to recognize, so i can download updates, etc.  I have access to internet via a windows system (so i can get .deb files and dpkg them).  I have been able to install ndiswrapper with dependancies, wlanctl-ng, and associated files that were recommended via the Ubuntu Wiki help files.  In lsusb, the card is recognized with a hex address, and under ndiswrapper -l it shows now that i have a prisma02 driver present with hardware present, however under network devices it isn't available, nor is a wlan0 available under ifconfig.  I added headers as well.  Is there anything i am missing?  

thank you for your help.  This thread was the most helpful of all, so i figured i would post it to you guys :)

Email or post if you have ideas.  I do have a 10/100 card in the box, but only have access to wifi due to landlords and walls and such :)

Graham[/QUOTE]
 Is there any error messages in your /var/log/syslog?

---

### Post by gkozlyk on 2005-07-13
There is no error in the /var/log/syslog.  Eth0 is trying to connect to internet, but because it isn't connected, it has no success.  

When i plug in the USB card, the Kernel recognizes it with the following:

localhost kernel: usb 1-1.2: New full speed USB device using address 7

So the computer sees it, but that's about it.  The lights on the card don't even come on.

---

### Post by gkozlyk on 2005-07-13
At the moment, all it tells me is that my ndis driver prisma02 is in there, but hardware is not detected.  iwconfig tells me that i don't have any wireless devices available either...

Thanx,

Graham

---

### Post by Lunde on 2005-07-14
[QUOTE=gkozlyk]At the moment, all it tells me is that my ndis driver prisma02 is in there, but hardware is not detected.  iwconfig tells me that i don't have any wireless devices available either...

Thanx,

Graham[/QUOTE]
 Did you ever try the linux-wlan-ng driver, if so you have to blacklist it because it might be blocking your card.

[QUOTE=azz]I blacklisted the prism2_usb and the p80211 modules (/etc/hotplug)
I compiled the most recent ndiswrapper modules and ndiswrapper-utils and installed them

cd to the driver's directory
sudo ndiswrapper -i  NETPRISM.inf

plug the sucker in.

Configure the interface with the networking tool.  This works because ndiswrapper uses wireless extentions.  The linux-wlan-ng uses it's own commands and the Gnome network tool interface does not yet support that.

It is ironic that it is easier to use Windows drivers in Gnome as opposed to the GPL driver for this device...[/QUOTE]

---

### Post by gkozlyk on 2005-07-14
[QUOTE=Lunde]Did you ever try the linux-wlan-ng driver, if so you have to blacklist it because it might be blocking your card.[/QUOTE]

I added into the /etc/hotplug/blacklist file the prisma2_usb, linux-wlan-ng plus the p80211 as per your quote.

I updated the ndiswrapper modules to 1.1-2 and utils to 1.1-4

when i do a ndiswrapper -l this is what it reads:

Installed ndis drivers:
prisma02       driver present

<still doesn't say hardware present>

hardware is still seen via lsusb

Now is there anything i need to do with modprobe or aliases?

I do now have an error when i modprobe ndiswrapper:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format.

Now could it be that i have been using debian packages instead of ubuntu?  If so, where do i get ubuntu packages, as debian is the first that comes up under google?

Thanx,

Graham

---

### Post by Lunde on 2005-07-14
[QUOTE=gkozlyk]I added into the /etc/hotplug/blacklist file the prisma2_usb, linux-wlan-ng plus the p80211 as per your quote.

I updated the ndiswrapper modules to 1.1-2 and utils to 1.1-4

when i do a ndiswrapper -l this is what it reads:

Installed ndis drivers:
prisma02       driver present

<still doesn't say hardware present>

hardware is still seen via lsusb

Now is there anything i need to do with modprobe or aliases?

I do now have an error when i modprobe ndiswrapper:

FATAL: Error inserting ndiswrapper (/lib/modules/2.6.8.1-5-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid module format.

Now could it be that i have been using debian packages instead of ubuntu?  If so, where do i get ubuntu packages, as debian is the first that comes up under google?

Thanx,

Graham[/QUOTE]
 I have ndiswrapper in my repositories, and I use the same as here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

But in this tread they recommend to use the latest version:
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
Maybe you should give this a try?

---

### Post by t2kburl on 2005-07-16
hey, Lunde   Thanks for all your help

I gave up and got a longer cat5 cable so that machine is now hard wired to the router

---

