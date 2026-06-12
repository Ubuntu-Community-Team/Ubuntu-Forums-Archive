---
title: "Ubuntu 16.04.1 LTS - Network reset every night"
date: 2017-02-23
forum: Networking &amp; Wireless
---

### Post by ozziegt on 2017-02-23
I am connected through ethernet to my router, and I have an instance of the irssi IRC client running on it. The client is reporting a network reset every night at exactly 5:03 am. I've confirmed that the IRC server itself doesn't do any kind of reset every day. I have no idea where to start diagnosing this issue, can someone help me out? 

```


########## wireless info START ##########

Report from: 23 Feb 2017 21:11 EST -0500

Booted last: 23 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/osman/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)
	Subsystem: Hewlett-Packard Company NC107i Integrated PCI Express Gigabit Server Adapter [103c:705d]
	Kernel driver in use: tg3

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85527207 errors:0 dropped:264 overruns:0 frame:0
          TX packets:104921863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69469437255 (69.4 GB)  TX bytes:91596682743 (91.5 GB)
          Interrupt:18 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver xxx
nameserver xxx
nameserver 192.168.1.1
search xxx

##### network managers ##################

Installed:

	None found.

Running:

	None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

loop
lp

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
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:06.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   26.062980] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.067142] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
[   29.067168] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
[   29.067203] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############


```

---

### Post by ozziegt on 2017-02-25
No suggestions? Does "booted last" mean the network adapter was rebooted at midnight?

---

### Post by jeremy31 on 2017-02-25
Do you have a server install?  The booted last should be the date and time of the last reboot

---

### Post by bearlake on 2017-02-25
Can it be possible that the ISP (Internet service provider) is refreshing their ip address at 05:03 am?

---

### Post by ozziegt on 2017-02-25
Yes it's a server install. I just ran wireless-info again and its says: 

```

########## wireless info START ##########

Report from: 25 Feb 2017 22:07 EST -0500

Booted last: 25 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

```

So it says "booted last" at midnight but running uptime: 

```

 22:08:30 up 22 days, 23:18,  1 user,  load average: 0.62, 0.32, 0.26

```

> **bearlake said:**
> Can it be possible that the ISP (Internet service provider) is refreshing their ip address at 05:03 am?

My IP address hasn't changed in a really long time, over a year I imagine.

---

### Post by bhartsfield on 2017-03-26
> **ozziegt said:**
> My IP address hasn't changed in a really long time, over a year I imagine.

That doesn't mean your lease isn't expiring nightly, it just means you are getting back the preferred address with each renewal (which is typical with most ISPs).

I was having a nightly issue like this as well on 16.10. After digging into syslog and iptables logs (which are both in syslog unless you split them out like I do), I found that, each night, my WAN would attempt to renew and network manager would "crash" and cause the system to freeze up. I found some corresponding iptables DENY logs every time for ports 67 (DHCP). I added rules to allow outbound DHCP (port 67) on the WAN interface and the problem went away.

At first I was like, "I get an IP when I boot up so what gives?" then remembered that my firewall script (which is just iptables rules) runs AFTER the network comes up.

So, that fixed it for me on 16.10 and I only mention it because, on 16.10, the time was consistent. Same time around midnight each night.

I had to roll back to 16.04 due to some unrelated issues (PPTP forwarding isn't working through the 4.8 kernel... ugh!!) and now I'm having another nightly freeze-up issue but that one is at random times and while it does look to be network-manager related, it's not the same DHCP issue I mentioned above. 

I'd check the logs to see if you can solve your issue the same way. And, if I ever figure out what's going on with the new issue on 16.04, I'll check back in and let you know.

---

