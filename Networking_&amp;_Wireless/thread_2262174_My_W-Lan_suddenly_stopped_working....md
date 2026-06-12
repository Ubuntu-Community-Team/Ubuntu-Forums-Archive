---
title: "My W-Lan suddenly stopped working..."
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by anja2 on 2015-01-23
Hello,
I have a problem and I have no idea where it came from or how to fix it. I already did some Internet searching, but I haven't really found anything helpful. I'm not a full beginner, but I've got a loong way to go to be a pro with linux.
Well, here's my problem and what I tried so far:
Yesterday, everything was working fine. Today, I started my computer, and I was immeadiatly told 'Your connection has been severed'. (I also noticed that my keyboard has been resetted from the german keyboard to the US. keyboard.) No network connection at all is shown, even though my external w-lan button is on. On my second operating system, Windows 7, the inernet works just fine-which is the reason why I can write this now. So what I tried now was the following:

I have a 82567L Gigabit Network connection.
I tried to ping google.com using ping-C4 [www.google.com](www.google.com), which just says unknown host
I tried to do sudo iconfig eth0 down/up, as it was suggested in one forum, but this command was not recognized.
I tried ifconfig-a, where I get a list. No errors were shown, but I noted that under lo: UP LOOPBACK RUNNING was written.

Do you have any ideas what I could do/try to get my Internet(or connection to the wlan card) back up and running?

Thank you very much for your help, if you need any more info from me, fire away!

Best regards,
Anja

---

### Post by phidia on 2015-01-23
Take a look at [this guide]("http://www.pcworld.com/article/2455972/how-to-fix-your-internet-connection-in-ubuntu-linux.html") paying specific attention to the enable network and enable wifi sections. There is also a networking section [here]("http://ubuntuforums.org/forumdisplay.php?f=336") at the ubuntu forums.

---

### Post by anja2 on 2015-01-23
I already found this guide. The thing is, when I click on the Networkmanager button, I don't even have something like 'enable wi-fi', it's just not there! The network I previously connected to is still in the Networkmanager, with the option 'automatically connect', but it doesn't seem able to find it.(or any other network) 
And the ping thing gives nothing in return. It's as if the wireless option completly vanished. (BTW: Result of Looking for additional drivers: None found)

---

### Post by phidia on 2015-01-23
Can you use a wired connection? If so do that and then follow the steps [here]("http://ubuntuforums.org/showthread.php?t=370108").
That's pretty much about updating the system you installed through your wired connection and then checking to see if you can enable wireless.

---

### Post by sandyd on 2015-01-23
*moved to networking and wireless*

---

### Post by anja2 on 2015-01-24
Unfortunatly, I don't have access to a wired connection. Only W-lan. Is there any possibility to download the stuff under Windows, save it on an external disk and then try to get it running on ubuntu?

---

### Post by westie457 on 2015-01-24
> **anja2 said:**
> Unfortunatly, I don't have access to a wired connection. Only W-lan. Is there any possibility to download the stuff under Windows, save it on an external disk and then try to get it running on ubuntu?
Yes it is possible and quite easy. Follow method 2 here. [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

---

### Post by anja2 on 2015-01-25
Okay, executed the script. Here's the output:

```
########## wireless info START ##########

Report from: 25 Jan 2015 12:01 CET +0100

Booted last: 25 Jan 2015 11:54 CET +0100

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

Xubuntu (from ~/.dmrc)

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
    Subsystem: Lenovo Device [17aa:20ee]
    Kernel driver in use: e1000e

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:0035]

15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)

##### lsusb #############################

Bus 002 Device 003: ID 07ab:fc9f Freecom Technologies 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

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
          Interrupt:20 Memory:fc000000-fc020000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

[[/etc/NetworkManager/system-connections/ASUS_Guest2]] (600 root)
[connection] id=ASUS_Guest2 | type=802-11-wireless
[802-11-wireless] ssid=ASUS_Guest2 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box 7330]] (600 root)
[connection] id=FRITZ!Box 7330 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7330 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

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
# PCI device 0x8086:0x10f5 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```

For me that's mostly gibberish, I hope you can tell me what the output means...

---

### Post by jeremy31 on 2015-01-25
Not sure exactly what happened but the driver isn't loaded for wifi, so try ```
sudo modprobe ath5k
``` and see if wifi comes to life

---

### Post by anja2 on 2015-01-25
Great, that did it!
Thanks a lot!

---

### Post by jeremy31 on 2015-01-25
> **anja2 said:**
> Great, that did it!
Thanks a lot!

If it fails after another reboot ```
sudo modprobe ath5k && echo ath5k | sudo tee -a /etc/modules
```

---

