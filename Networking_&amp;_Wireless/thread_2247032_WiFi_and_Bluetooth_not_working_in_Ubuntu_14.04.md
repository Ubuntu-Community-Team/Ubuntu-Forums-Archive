---
title: "WiFi and Bluetooth not working in Ubuntu 14.04"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by Kajal_V on 2014-10-05
I am running Ubuntu 14.04 on my laptop. Neither WiFi nor Bluetooth works. A wired LAN connection works, though.

I tried testing wireless connectivity using a hotspot on my phone, but my laptop cannot detect any wireless networks.
But the 'create WiFi connection' option is there, if it is of any use.

How do I fix this problem? I am fairly new to Ubuntu so please let me know if I have to provide more information.

Here is the output of wireless-info.txt:

```



########## wireless info START ##########


Report from: 04 Oct 2014 19:22 IST +0530


Booted last: 04 Oct 2014 18:52 IST +0530


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:193e]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b3a6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0bc2:2321 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
mxm_wmi                13021  1 nouveau
wmi                    19177  3 hp_wmi,mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:10.4.9.82  Bcast:10.4.9.255  Mask:255.255.255.0
          inet6 addr: fe80::a21d:48ff:fef9:15e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44496 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81521478 (81.5 MB)  TX bytes:4190541 (4.1 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.4.9.1        0.0.0.0         UG    0      0        0 eth0
10.4.9.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search bits-goa.ac.in


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         10.4.9.82
    Prefix:          24 (255.255.255.0)
    Gateway:         10.4.9.1


    DNS:             10.1.1.61
    DNS:             10.1.1.62


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


[[/etc/NetworkManager/system-connections/KajalWiFi]] (600 root)
[connection] id=KajalWiFi | type=802-11-wireless
[802-11-wireless] ssid=KajalWiFi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############


```

---

### Post by Vladlenin5000 on 2014-10-05
Neither WiFi nor Bluetooth devices are shown in your report. First thing to check is whether or not it has been disabled in BIOS.

---

### Post by Kajal_V on 2014-10-05
Hello,
Sorry for being a n00b, but how exactly do I check it? I am unable to find any such setting in the BIOS menu like 'Wireless' or something similar. Maybe I am not looking in the right place?

---

### Post by Vladlenin5000 on 2014-10-05
Let's see if I can help... Please post the make/model.

---

### Post by varunendra on 2014-10-06
Hello Kajal,

Please give us the exact model no. of your laptop, or if possible, a link to its user manual as Vladlenin5000 asked.

However, even if an internal wifi adapter is disabled in the BIOS, it should show up in the lspci output, but there may always be exceptions, so checking the BIOS is worth it.

If you checked your BIOS and couldn't find it, it is quite possible that the card may have gotten loose, or worse... gone! (is the machine still under warranty).

On the other hand, we have seen really weird things with machines that come with Windows 8 preinstalled. Is yours such a one? If yes, does it show up there?

---

### Post by Kajal_V on 2014-10-06
My laptop model: HP Pavilion m4-1012tx Notebook PC - [http://h10025.www1.hp.com/ewfrf/wc/product?product=5389981&lc=en&cc=in&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/product?product=5389981&lc=en&cc=in&dlc=en)

If it's relevant - I had the motherboard replaced around 1.5 months ago. At that time, the technician tested the WiFi and Bluetooth and they seemed to be working fine. He tested it on the pre-installed Windows 8. However after a while, both stopped working, and the options even got deleted. I tried to reinstall the drivers from the HP website many times, but nothing could fix the issue.

I replaced Windows 8 with Ubuntu (partly by accident :P). And it's the same problem here. I'm assuming it's a hardware fault somewhere, but then how did it work initially just after the motherboard replacement?

Another thing to note is that just before installing Ubuntu, I did a factory reset on my laptop. This brought back the WiFi and Bluetooth options which had somehow been deleted. But neither of them worked - in the sense, neither could detect or connect to any other hotspot/device.

The machine is still under warranty, and will be till December.

Edit:
Some additional details which might be relevant-
Product/model number: E3B43PA#ACJ
BIOS version: F.05
Processor: Intel(R) Core(TM) i5-3230 CPU @ 2.60 GHz

---

### Post by varunendra on 2014-10-06
> **Kajal_V said:**
> The machine is still under warranty, and will be till December.
This ^^ is the most important bit, considering the following -

> **Kajal_V said:**
> I had the motherboard replaced around 1.5 months ago. At that time, the technician tested the WiFi and Bluetooth and they seemed to be working fine. He tested it on the pre-installed Windows 8. However after a while, both stopped working, and the options even got deleted. I tried to reinstall the drivers from the HP website many times, but nothing could fix the issue.
....
....I'm assuming it's a hardware fault somewhere, but then how did it work initially just after the motherboard replacement?
I think your assumption is correct. The fault may be with the motherboard, not the card itself, hence why it worked initially.

Anyway, since it is under warranty, I strongly recommend to take it to the service center if the BIOS reset doesn't show it up again in the BIOS or Ubuntu. DON't open the case or try to handle the card physically by yourself. I've seen these service centers considering the warranty void if they notice that the case has been opened (indicated by deformed screw slots).

---

### Post by Kajal_V on 2014-10-06
Oh, no.. speaking to HP customer care is quite a pain! But, I'll do that for sure. It does seem like the only option. I can't think of what else could have possibly gone wrong.

Just as a last resort, could you tell me exactly how to check it in BIOS? I might have overlooked something.

---

### Post by varunendra on 2014-10-06
Yeah, I've seen their 'quality' here in New Delhi. One of my colleagues has a 14" HP laptop. A couple of its screw bases near the hinges broke (poor quality, the hinge was not too tight) and when she took it to the nearest service center, they accepted it under warranty, but a couple of days later, mailed her a proforma invoice of Rs. 2800 should she choose to get it fixed!

When she complained about it (almost *threatening* that she would email HP's official addresses), they came back with some really cheap excuse and sent an *engineer* (you may already know how they are) to fix it onsite. Okay, it got fixed for no extra price, only a couple of weeks an exchange of some not-so-friendly emails and phone calls (I had told her to not go nuts and remain calm all the time, collect as much evidence of communication as she could, should she need to go to consumer court, keeping the *threat* mode a last resort).

Anyway, just three-four months later, _after_ the warranty was expired, the same problem occurred again and I was the obvious 'service center' this time. :|
When I opened the case, I found that the *engineer* had replaced the base with one that had its iron plate (that supports the plastic bases to strengthen it) already broken (the broken part was absent!). A good amount of araldite and an aluminium plate for support did the job, but geez! So much for the reputation of HP!!

Okay, that was a rant that you're not interested in. Unfortunately, I couldn't find the BIOS screens in the user manual that I downloaded. Can you take screenshots of it and attach it here (or better, upload somewhere else and post links here)?

**EDIT:**
Okay, found a page that shows screenshots of BIOS screens. Please expand the "BIOS Setup Menu screens" link here and let us know which one is yours : [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=bph07110#N1033](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=bph07110#N1033)

---

### Post by Kajal_V on 2014-10-08
Haha! I think a similar "engineer" did something with my laptop's motherboard as well. 

It says BIOS version F.05. "F"? Is that 6 or 7? I guess my screen resembles 6 mostly, though.

---

### Post by Vladlenin5000 on 2014-10-08
> **Kajal_V said:**
> It says BIOS version F.05. "F"? Is that 6 or 7? I guess my screen resembles 6 mostly, though.

Apparently the differences are regarding "6 or less" and "7 or greater". Yours should be the former.

---

### Post by varunendra on 2014-10-08
> **Vladlenin5000 said:**
> Apparently the differences are regarding "6 or less" and "7 or greater". Yours should be the former.

..in which case, the option to enable/disable the WiFi (could be presented as "Wireless" or "WLAN") should be under "Advanced" menu, or "I/O" or "PCI devices configuration" submenu, as the note says :
> NOTE:Onboard devices such as LAN, audio, or video might also appear under PCI or I/O Device configuration.

The BIOS may not present options related to a device that it can't see itself.

---

### Post by Kajal_V on 2014-10-14
Thank you all for your replies :)

Wow, I cannot find any option like the ones you mentioned :/
If the motherboard is faulty and the wireless adapter stops working, it stops showing up in the menu right? Because I have a feeling that that's what has happened.

---

