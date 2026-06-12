---
title: "Wifi problem, Connecting to a router, says I am connected but I can't access anything"
date: 2005-07-12
forum: Networking &amp; Wireless
---

### Post by Magitek on 2005-07-12
Hi,
I have a 3com OfficeConnect 11g Wireless Router modem. I bought a Netgear WG511T wifi card for my laptop, and it seems to have installed OK, and it is running out of the box like it said it would. I have both GNOME and KDE installed (installed ubuntu, then installed kubuntu-desktop in snyaptic from the Kubuntu CD).My wireless connection is activated, and set as the primary network connection, no other network connections are enabled so I cannot see the problem. On Kwifimanager when I "Scan for Networks", my network 3com comes up and I can connect to it fine. Even though I am supposedly connected to my router, I cannot access any websites or the router itself (192.168.1.1) through any browser. The wifi card is a Super G card, 108MBPS, but says it complies with existing 802.11g and 802.11b networks so I'm stuck. Please help, its hard getting support for my laptop without the internet working! Cheers, Joe.

---

### Post by jeroevi on 2005-07-12
Joe,

Have you tried configuring the card with iwconfig? It is not via a GUI but you know what you're doing. If you simply type iwconfig it will display the wlan card. Check here if everything is set: SSID, WEP key, etc.
If it doesn't seem ok have a look at the iwconfig man page. It is rather easy.
For example I use:
iwconfig *mywlan* essid *myid* mode Managed key open *mykey*

good luck
jeroen

---

### Post by Magitek on 2005-07-13
Thanks. I used these steps:

"
1. start up a root console

2.type: iwconfig ( this will give you your card info and network /wireless info)

3. type: iwconfig ath0 channel 6 ( substitute channel 6 for whichever channel your router is transmitting on)

4. Type: iwlist scan ( this may take a minute, this will give you your routers wireless settings.)

5. Type: iwconfig ath0 essid xxxxxx ( replace xxxxxx with your routers essid)

6. Type: iwconfig ath0 ap xx xx xx xx xx xx( this is the six double digit mac address required and is listed in your iwlist scan message as above.)

7. Type: iwconfig ath0 key XXXXXXXXXX ( replace XXXXXXXX with your own hex wep key )

8. type: dhclient ( this gets your dhcp sorted ) you should now be up and running."

I found in this thread. And it seems to work although, I have to do it every boot up and it can even take a few tries sometimes, This really is a termporary solution as I want it set to a specific IP address as my ports are forwarded there. When I use that dhclient it picks the IP automatically, how can I get the same IP everytime?

---

### Post by Magitek on 2005-07-13
Oh and I got that info from here:

_ Atheros AR5212 Madwifi HowTo_
[http://www.ubuntuforums.org/showthread.php?t=38972&page=1&pp=10&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=38972&page=1&pp=10&highlight=madwifi)

The simplest solution worked for me, so I did not re-install any drivers and mess it up right? I'm not sure whether it is a problem with the drivers, more the confguration. ANy advice how to give it to use the 192.168.1.3 IP everytime and to do this on boot-up is much appreciated. Thanks in advance, Joe.

---

### Post by gruepig on 2005-07-13
To bring up your network up automatically on boot, edit the file /etc/network/interfaces.  For a manual (non-DHCP configuration), it should look something like this (I'm going on memory here, so the syntax may be slightly off.  Check the interfaces man page.): 

auto ath0
iface ath0 inet static
address <your ip>
netmask <your netmask>
network <your network>
broadcast <your broadcast>
gateway <your gateway>
pre-up iwconfig ath0 essid <your essid> && iwconfig ath0 key <your key>

The important part for wireless is the pre-up line which says "run this before bringing up the interface".  (The whole pre-up command needs to be one line; if you need to split it into multiple lines, use a \ at the end of each line as a continuation character to ignore the newline.)

---

