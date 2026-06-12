---
title: "Broadcom BCM43231, wireless not connecting"
date: 2014-11-24
forum: Networking &amp; Wireless
---

### Post by rick39 on 2014-11-24
Okay I am really new to  the use of LUBUNTU and I have installed LUBUNTU 14.10 on an old dell dimension 3000 that is running a pentium 4 @3.00 Ghz. The one thing it does have is less than 1 G of ram so theres that. LUBUNTU boots fine and everything but I cant get my wireless adapter to show up or install it. I ran a utility that was suggested in another thread but I am not sure what to do with the information so any help would be appreciated. Thanks in advance! 


```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

machin3-Dimension-3000 3.16.0-23-generic i686,  Ubuntu 14.10, utopic

CPU    : Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory : 745 MB
Uptime : 14:30:04 up 28 min,  1 user,  load average: 0.01, 0.03, 0.07


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: Dell Dimension 3000 [1028:019d]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 12c9:1001  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




module parameters ~~~~~~~~~~~~~~~~~~


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o=============o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State       | Default | Speed     | Support      | HW Addr   
================o=======o========o=============o=========o===========o==============o===========
 eth0           | Wired | e100   | unavailable | no      |           |              | <MAC eth0>
----------------+-------+--------+-------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1050 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.16.0-23-generic root=UUID=b41a4c0d-4886-499a-a898-743f45eef0ba ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.021513] Initializing cgroup subsys net_cls
[    0.021536] Initializing cgroup subsys net_prio
[    0.844411] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.845302] audit: initializing netlink subsys (disabled)
intel_rng: don't want to disable this in firmware setup, and if
[   19.354163] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

    ======== Done ========
```

---

### Post by carl4926 on 2014-11-24
I think the USB device isn't really supported
Eg:
[http://askubuntu.com/questions/276321/getting-ubuntu-to-recognize-a-bcm43231-network-card-what-is-up-with-terminal](http://askubuntu.com/questions/276321/getting-ubuntu-to-recognize-a-bcm43231-network-card-what-is-up-with-terminal)

---

### Post by rick39 on 2014-11-25
Thats not good because its all I have available.

---

### Post by carl4926 on 2014-11-25
USB wireless devices are cheap and easy to come by
I suggest you consider buying a device that will be supported
Depending where you live in the world, ask about it here and look at the consumer reviews of products available to you.
I often find I can sell something on an auction site and buy a replacement at little or no cost overall.

---

### Post by kurt18947 on 2014-11-25
> **carl4926 said:**
> USB wireless devices are cheap and easy to come by
I suggest you consider buying a device that will be supported
Depending where you live in the world, ask about it here and look at the consumer reviews of products available to you.
I often find I can sell something on an auction site and buy a replacement at little or no cost overall.

I'll echo carl's suggestion. You *might* get your Broadcom BCM43231 functioning but you may learn more about linux & NDISwrapper than you ever wanted to know in the process.  The thing with linux & wifi is brands don't matter all that much.  The chip set is what matters; the drivers included in the linux kernel work with chipsets.  Several different devices from different manufacturers may work equally well because they all use the same chipset.  OTOH, different versions of the same model from a given manufacturer may not all work.  For instance Dlink's DWA131 ver. a worked perfectly it used a Realtek RTL8192SU chipset.  Dlink's DWA131 ver. b changed to a Realtek RTL8192CU chipset which did NOT work out of the box (at least not well).  Yet the only way to tell the ver. was to check the label on the device. The packaging did not differentiate. Incidentally, RTL8192CU  is now a viable chipset though it requires a patched driver and is very common.

---

### Post by JeQhdMD on 2014-11-25
First, I'm "assuming" you've gone through the standard process of installing nvidia wireless drivers via the "additional drivers" functionality in Lubuntu.   Sorry I can't provide the specific steps as I don't know Lubuntu's interface or setup applications.   But a search of your system should reveal that without too much struggle.

If the standard method above is not doable for whatever reason(s) . . . you can get a supported usb wireless nano-type dongle (very small) that is plug and play.   One of my favorites is this one, found a Amazon (among other places).   Cost is aprox $10.

[http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1416937052&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter&pebp=1416937056558](http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1416937052&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter&pebp=1416937056558)

Just plug it in a usbv2 port, and voila . . . you will see your proximate wireless networks.   Just need to select it, and input your password.   From then on, it should connect automatically.

---

### Post by Caysho on 2014-12-13
I bought a Netgear N300 (WNA3100) today which is based on this chipset and after several hours got it working, referring to [the other thread]("http://ubuntuforums.org/showthread.php?t=1695036&page=25&highlight=BCM43231") and other resources.

Short version: 
1. If you have the Netgear install CD (or get the installer from the website), run the signed version of the setup in WINE and get the required files from the installation.
2. Set your AP security to WPA PSK.

Install ndisgtk and the other ndiswapper tools and ensure you have a tail of syslog running.  This will help you check the ndiswapper is working.

Of the various archives that are linked on the web, these are my findings:

I found the Broadcom_bcm43xx_USB_32_64bit_v2 linked in the thread referred to above does not work, maybe because I am using 32 bit Ubuntu.
ndisgtk will show the hardware is present but syslog shows the following:
Dec 13 20:20:19 desktop kernel: [22637.268430] ndiswrapper: driver bcmn43xx32 (,08/26/2009, 5.10.79.30) loaded
Dec 13 20:20:20 desktop kernel: [22638.284546] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
Dec 13 20:20:20 desktop kernel: [22638.284561] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
Dec 13 20:20:20 desktop kernel: [22638.284577] ndiswrapper (mp_halt:254): device f7154500 is not initialized - not halting
Dec 13 20:20:20 desktop kernel: [22638.284583] ndiswrapper: device eth%d removed
Dec 13 20:20:20 desktop kernel: [22638.284746] ndiswrapper: probe of 1-5.4:1.0 failed with error -22
Dec 13 20:20:20 desktop kernel: [22638.284824] usbcore: registered new interface driver ndiswrapper

In NetworkManager, the Enable Wifi option will not be present.

The archive called ndis_bcmwl does not work.
ndisgtk reports the hardware is not present.

There was an archive with a bcmwlhigh5.inf dated 07/09/2011 that works but always times out on the first few attempts (takes a while to connect)
This driver causes the 
ndiswrapper (MmBuildMdlForNonPagedPool:1864): f8d72000, 16000, 4
entries in syslog as described in the ndisrapper documentation
This archive is from the dropbox link 
[http://dl.dropbox.com/u/15720903/WNA3100.zip](http://dl.dropbox.com/u/15720903/WNA3100.zip)
described at 
[http://forums.linuxmint.com/viewtopic.php?f=53&t=149890](http://forums.linuxmint.com/viewtopic.php?f=53&t=149890)

The WinXP2000 archive from Netgear's website works (might also cause the MmBuildMdlForNonPagedPool syslog entry).
The website allows you to skip registration.
I pulled the "Software Version 2.2.0.2", ran the signed version of the setup and used the driver from the folder in .wine
\Program Files\NETGEAR\WNA3100\Driver


The device does not support WPA2 PSK.
I spent the better part of a day trying to resolve the following message in syslog (kept getting prompted for the AP's passphrase):
WPA: 4-Way Handshake failed - pre-shared key may be incorrect

I assumed that the driver was faulty, but every advice I found discussing ndiswrapper indicated that simply by loading the binary it should be correct.
Eventually I found I had to do set the AP security to WPA PSK.

---

### Post by giorgos6 on 2014-12-29
So... What can I do with those drivers? Can I just put them to /root/Netgear WNA3100?

---

### Post by carl4926 on 2014-12-30
> **giorgos6 said:**
> So... What can I do with those drivers? Can I just put them to /root/Netgear WNA3100?
It's bad advice to go out and buy a device with the specific intention of using ndiswrapper.

Just get a device that works natively

---

