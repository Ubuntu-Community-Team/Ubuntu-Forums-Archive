---
title: "configuring samba to share with windows"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by unisol on 2007-05-15
guys, your documentation is great concerning using samba, but i just cant seem to grasp it. im talking about editing smb.conf, and the syntax for mounting a windows share. i seeed to hit a brick wall here and in need of some help. maybe a book titled "samba for tards". i just need some help.

---

### Post by kidders on 2007-05-17
Hi there,

smb.conf doesn't have anything to do with mounting shares ... it's a just a configuration file for your Samba server. Perhaps that's the source of your confusion.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by unisol on 2007-05-17
well how do i mount the windows shares. and how do i share an internet connection?

---

### Post by kidders on 2007-05-17
You should be able to mount network shares with **mount**.

Internet connection sharing requires a firewall (router) configured for NAT. Depending on how much you know about the mechanics of packet routing, it would be worth reading about it before setting up internet connection sharing. It's pretty trivial to do (there are plenty of howtos available on the subject), but many users get confused if they don't follow what's going on.

---

### Post by unisol on 2007-05-19
youre talking network address translation? thanks ill look into it right away. my problem is its working all my windows pcs have an internet connection, even the windows partition on my one pc, its the linux partitions (feisty, and debian etch) i cant share the internet connection with.

---

### Post by kidders on 2007-05-19
Ohhh... so something *else* is doing the sharing (eg a hardware router or another computer)? In that case, ignore my last post!

If you describe how your network is laid out, I'll try to point you in the right direction. Accessing a pre-existing shared internet connection that other PCs are already using should be straightforward enough. :-)

---

### Post by unisol on 2007-05-19
it goes internet- cable modem-wireless router-pc1 to  pc2 to laptop to pc3. the router is set to dhcp which comcast requires. all pcs are set to dhcp with their own ip address. like i said all the windows pcs connect, even the pc that has awindows partition, but the linux partitions i cant figure out. if you want anymore info just say. thanks for your reply.

---

### Post by kidders on 2007-05-20
> **unisol said:**
> it goes internet- cable modem-wireless router-pc1 to  pc2 to laptop to pc3.Hmm... I'm still not quite sure what's connected to what. Essentially, I'm wondering what computer is sharing its internet connection (ie where can you go to look for configuration problems or error messages).

What have you tried on your Linux box so far? Can you post its network configuration? Are there any messages in your system logs that might be helpful?

---

### Post by unisol on 2007-05-20
pc1 has a WRT54G wireless router connected to the cable modem with windows xp home.. pc2 has a WMP54GR wireless network card with winxp professional, pc3 (the laptop) with an atheros wireless chip built in . pc 4 has a RMP54GR wireless pci card , winxp pro hda1, hde4 is ubuntu feisty fawn. the wireless adapter is recognized as a ralin2600. as far  network settings ,host is 127.0.0.1.  it has network manager to help with the network. however while i can get it to connect to my home network, i cant get it to share an internet connection.

---

### Post by kidders on 2007-05-20
> **unisol said:**
> however while i can get it to connect to my home network, i cant get it to share an internet connection.That's odd, but it makes my previous questions important...
[LIST]
[*]What have you tried on your Linux box so far?
[*]Can you post its network configuration?
[*]Are there any messages in your system logs that might be helpful?
[/LIST]

Also, I'm still not quite sure which computer's internet connection is being shared. Are you using a proxy?

---

### Post by unisol on 2007-05-20
iwconfig:lo nowireless extensions
etho no wireless extensions
ra0 rt61 wireless ESSID "nickname"
mode managed Frequency: 2.412 ghz bit rate 54 mbs
rts thr: off Fragment thr: off
Encryption 6777-6179-6066-000-000-00
link quality 0/100 signal level 121 dBm noise level 95 dBm
Rx invalid nwid:0 invalid crypt :0
rx invalid frag :0 Tx excessive retries:0
invalid beacon:0 

ifconfig:Linl encap :Ethernrt Hwaddr :00:18:F8:AF:9B:14
inet6 addr Fe80::218:f8ff:feaf:940/64
Up Broadcast RunningMulticast MTU:1500 metric:1
RX packets:471 errors:0  dropped:0 overruns:0 carrier:0 collisions:0 txqeulen  :1000
Rx Bytes:35549 Txbytes:0
interrupt:10
ra0:dhavi Link encap: Ethernet Hwaddress 00:18f8:AF:9B:14
inet addr 169.254.6.320  Bcast 169.254.255.255 mask:255.255.0.0
UpBroadcast Running Multicast MTU:1500 metric:1 
interrupt 10
/etc/network/interfaces:
auto lo
iface loinet loopback
 iface ra0 inet dhcp
wireless ESSID network nane 
wireless key s: key
auto ra0

---

### Post by kidders on 2007-05-20
Hmm... I'm confused. Your iwconfig/ifconfig post doesn't suggest that you have a working network connection at all. How have you determined that (a) you don't have an internet connection, and (b) you _do_ have a local network connection?

It's difficult to be any more helpful than that without some additional information though...

[LIST]
[*]I still don't know where internet connection sharing comes into the equation. One possible reason you'd be able to connect to a network *without* having access to its internet connection is a misconfiguration on that computer ... not the Linux box. Without a basic description of your network layout, it's impossible to tell.
[*]The use of a proxy could be masking the absence of a sensible default route on your network, depending on what you're using your internet connection for. For that reason, it's important to know if you're using one.
[*]Knowing what you've tried already would help me figure out how much networking expertise you have, and where the problem might lie.
[*]Relevant system log messages very often reveal useful information when something doesn't work as expected.
[/LIST]

---

### Post by unisol on 2007-05-20
no i dont have a proxy. what i have tried is editing /etc/networking/interfaces and commenting out all the wireless devices. installing wpasupplicant. making a file wpasuppicant/default and adding the line ENABLED=0. then i reatart sudo /etc/init.d/dbus restart. but when i try to connect to the home network the mouse and keyboard freezes. i go to system-adminstration/networking and fill in the blanks with roaming turned off. it says im connectedto the network, but when i ping it nothing is received.im really at a loss now being new to networkig ,not so new to linux. i also firestarter and tried to configure it for shared internet access,no luck.

---

### Post by kidders on 2007-05-21
> **unisol said:**
> but when i try to connect to the home network the mouse and keyboard freezes.That sounds like you might have a driver problem. What happens your CPU usage when things lock up? Also, at what point exactly does this happen? Are your system logs any help?

> **unisol said:**
> i also firestarter and tried to configure it for shared internet access,no luck.The best thing to do is get your network connection working before you try to share it. I would suggest deactivating your firewall. Unfortunately, debugging problems with wireless cards is waaaay outside my comfort zone ... but I'll do my best.

What kernel module are you using?

---

