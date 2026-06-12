---
title: "Problems with wireless on a server install."
date: 2005-11-30
forum: Networking &amp; Wireless
---

### Post by trevorv on 2005-11-30
Hi,

I am trying to install Xubuntu, and so have firstly done a server install, and need to connect it to the internet to download xubuntu-desktop, but cannot connect. I have previously been using Ubuntu with GNOME and it connects to the internet fine, using my wireless connection. So, I copied the files that I thought were the ones that mattered, and entered them into the fresh install (these being /etc/resolv.conf and /etc/network/interfaces), but the laptop still refuses to connect to either the network or the internet.

I'm not sure if this is of importance, but running "route" returns no information (just the headers; Destination, Gateway, etc.). Looking for advice, I found [this]("http://www.debian-administration.org/articles/254") article, and have tried changing the default route, which returns an error (I think "Network is unreachable", or words to that effect).

I am currently running from the Breezy live CD, which connects fine. I am using a static IP as I've always had problems with DHCP with my router.

Any advice is much appreciated, I'd like to install Xubuntu, preferably not through GNOME. Is there a certain package I need to install, or a file I need to edit?

---

### Post by Lambert on 2005-11-30
The first question I would have is does the device have a working driver?

If you type iwconfig do you get any output? If not then there is no driver.

If you do get output then try 

iwlist <wlan0> scan

to see if you can find the router.

<wlan0> = your device's logical name, maybe eth0 or wlan0 or ath0 etc..
(you might need sudo before the commands)

---

### Post by trevorv on 2005-11-30
Hi, and thanks for your reply. When I run iwconfig I get the following;

```
lo	no wireless connections
eth1	no wireless connections
eth0	IEEE 802.11g ESSID:"TI-AR7WRD"
	Mode:Managed Frequency:2.462 GHz Access Point:00:30:54:75:81:D5
	Bit Rate=54 Mb/s Tx-Power=20dBm
	Retry limit:7 RTS thr:off Fragment thr:off
	Power Management:off
	Link Quality=90/100 Signal level 39 dBm Noise level 85 dBm
	Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
	Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

If I run iwlist eth0 scan I get

```
eth0	Scan completed:
	Cell 01 - 	Address:00:30:54:75:81:D5
			ESSID:"TI-AR7WRD"
			Protocol:IEEE 802.11.bg
			Mode:Master
			Channel:11
			Encryption Key:off
			Bit Rate:54 Mb/s
			Extra:Rates (Mb/s) 1 2 5.5 6 9 11 12 18 22 24 36 48 54
			Quality=85/100 Signal level=-45dBm
			Extra:Last beacon:3830ms ago
```

Apologies if there's any typos in that, I had to copy the lot by hand. To me that makes it look as if everything's running fine, but hopefully you know more than me!

I made a note of the error as well, when I try to ping something, it is

```
connect: Network is unreachable
```

---

### Post by Lambert on 2005-11-30
So you should have an interface file that looks like this

iface eth0 inet static
address <IP>
netmask <MASK>
network <NETWORK>
broadcast <BROADCAST>
gateway <router IP>
wireless-essid <ssid>


and when you run ifconfig the second line should say inet address xxx.xxx.x.x showing an ip is assigned to the device.

you say you can't ping anthing can you ping the router at least?

If this checks out then try

route add default gw <router_ip>

where router_ip = the ip address of the router with out the <>
you may need to add sudo to the begininning of the command

then see if you can ping anything

---

### Post by trevorv on 2005-11-30
My interfaces file currently reads 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid TI-AR7WRD
	address 192.168.1.3
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth0

```

as this is the one that works when running the live CD. If I try changing it to how you suggest, what is it that goes after "Network"? (sorry if this is a dumb question, I thought it would be the "TI-AR7WRD" part, but that appears to go under wireless-essid).

Thanks again.

---

### Post by Lambert on 2005-11-30
The one you have is ok if it works on live cd. Not all options are always needed or used so you can ignore the network part.

---

### Post by trevorv on 2005-12-01
Well, I've tried running the route command, but still get the error "SIOCADDRT: Network is unreachable". Any other ideas?

---

### Post by trevorv on 2005-12-02
I have it working now, it was rather a simple solution; "ifup eth0". I had assumed that it would automatically come up on boot, but apparently not. I'm not quite sure why as it always has done with other installs.

How do I now set it up so it does activate on startup?

---

### Post by trevorv on 2005-12-03
Come on, someone must be able to help me! How do I make it run ifup eth0 on boot time?

---

