---
title: "Not connecting to internet"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by superbungalow on 2008-01-20
Hi, i just installed ubuntu on a computer previously running xp. I plugged in my network adapter and ubuntu found my wireless network. So far so good. It connected, but when I run firefox and go to, for example, google, it just says connecting to "www.google.com" for ages, and eventually tells me the connection timed out. Can anyone help please?

---

### Post by jerome1232 on 2008-01-20
Can you ping/browse to your router?

---

### Post by jerome1232 on 2008-01-20
just in case i'm not sure of your network knowledge most common router ip's are

192.168.0.1
192.168.1.1
192.168.1.254

those are the ones i usually see

to test browse to it, open firefox, type one of those in the address bar, it should prompt you for a user name and password also from a terminal try

ping google.com

dig google.com

ping [router ip]  --whatever ur routers address is and post results

---

### Post by EXCiD3 on 2008-01-20
What wireless card are you using? Some cards can detect the networks but cannot connect.
Open Terminal and type: ```
[SIZE=-1]lshw -C network
``` and post the output for us.
[/SIZE]

---

### Post by superbungalow on 2008-01-21
hey. I   went to try some of the solutions you suggested, but when I logged on, i found i couldnt even connect to my network. It found my network, but never got any firther than "attempting to connect to DLINK_WIRELESS"

---

### Post by superbungalow on 2008-01-21
OK, I tried the "lshw" thing and got:
```

WARNING: you should run this program as a super-user
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial; 00:19:5b:79:7b:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by jerome1232 on 2008-01-22
I see it's disabled when I run that command i get

  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:11:50:b4:2c:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

 my knowledge regarding hardware and linux is limited so i'm not sure how get it enabled/what steps to take from there

---

### Post by superbungalow on 2008-01-22
Hey, now i get:

WARNING: you should run this program as a super-user
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial; 00:19:5b:79:7b:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

But I still can't access the internet, or my router conifguration, at 192.168.1.1

---

### Post by superbungalow on 2008-01-22
Also, This might help. Some info I got about my router:

LAN
	MAC Address 	00:17:9A:D6:9B:B5 	
	IP Address 	192.168.1.1 	
	Subnet Mask 	255.255.255.0 	
	DHCP Server 	Enabled 	
	NAT 	Enabled 	
WAN
	Virtual Circuit 		Pvc0
	Status 	Connected 	  	
	Connection Type 	pppoa 	
	IP Address 	80.42.37.43 	 
	Subnet Mask 	255.255.255.255 	 
	Default Gateway 	212.74.111.224 	 
	DNS Server 	212.139.132.10

---

### Post by superbungalow on 2008-01-22
When I ping 192.168.1.1, I get:

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.1 icmp_seq=2 Destination Host unreachable
From 192.168.1.1 icmp_seq=3 Destination Host unreachable
From 192.168.1.1 icmp_seq=4 Destination Host unreachable
From 192.168.1.1 icmp_seq=5 Destination Host unreachable

etc...

---

### Post by rosegarden78 on 2008-01-22
If you have nm-applet running (Network Manager Applet little wireless bars) and you are connected, the problem is the modem or network.  When this happens to me during bad weather, I unplug the power from the modem and router.  Turning it back on usually does the trick when my network disappears for no reason despite a wireless connection.

---

### Post by jerome1232 on 2008-01-22
Yeah let's see a couple things, is this a laptop? desktop?

what kind of adapter are u using?

if it's a usb one type the following and post the output

```
lsusb -v | less
```

this will tell us what card ur<-- (hehe the bad habits instant messaging teach us) using

if it's built in/pci try this one will be a long list may have to scroll around and find it

```
lspci -v | less
```

then check out [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to see if it's a supported card or not I know with older versions of ubuntu my card couldn't to connect to wep-shared, but could connect to wep-open and wpa-psk, have u tried setting ur network as open and seeing if u can connect?
may want to check out this thread [http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188") another thread that looks promising [http://ubuntuforums.org/showthread.php?t=603154]("http://ubuntuforums.org/showthread.php?t=603154") still not sure why ur card shows as disabled when you run the lsh.... whatever that command was lol

---

### Post by jerome1232 on 2008-01-22
Update

If i right click my nm-applet and uncheck enable wireless then run sudo lshw -C network

```
jeremy@ubuntu-main:~$ sudo lshw -C network
[sudo] password for jeremy:
  *-network               
       description: Ethernet interface
       product: IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY
       vendor: Sundance Technology Inc / IC Plus Corp
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 31
       serial: 00:50:8d:7b:7f:9b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sundance driverversion=1.2 duplex=full ip=192.168.0.2 latency=32 link=yes maxlatency=10 mingnt=10 module=sundance multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:11:50:b4:2c:2d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g
```

now this also happens if i have my hardwired network selected instead of my wireless network, so yeah I've been thinking this whole time hardware 'cuz of that disabled. Try it with open security man, if that works try diff types of security. Try out those threads I posted earlier too, one of 'em is command line based so it'll give ya errors that'll help at the least.

---

### Post by rosegarden78 on 2008-01-22
When this happens to me:

1) Unplug power to modem and router
2) Plug in and wait for reconnect

Then I make sure nm-applet is loaded and/or reload.  Alt+F2 nm-applet.

---

### Post by jerome1232 on 2008-01-22
Along the lines of pwrcycling as rosegarden is suggesting (fixes so many things lol)
```
sudo /etc/init.d/networking restart
```  I was experencing ur exact problem this afternoon on a xubuntu fresh install (uses the same network manager) and that magically fixed it, though the problem was affecting wired and wireless alike. i came home sick and had nothing to do so i've been thinking about ur problem while setting this machine up then had the same problem lol.

---

