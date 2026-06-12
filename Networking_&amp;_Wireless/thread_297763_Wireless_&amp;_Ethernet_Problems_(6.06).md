---
title: "Wireless &amp; Ethernet Problems (6.06)"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by JerryM on 2006-11-11
Hey folks.

I'm new to this whole Linux stuff, so I will try to explain my problem the best I can.

(I won't be able to post the results of if/wconfig until later)

See, my problem is this: I tried to install my wireless card (Netgear WG111v2). After reading, it seems I am required to have NDIS to use it. So I pulled out another card (forgot the name.. I'll have that for you later as well). This card actually seemed to work with no problems. That is: It acted as if it was connecting, kept a solid light when I was "connected", etc.

I ran a IWConfig, and it appeared as though there was communication with my router, however *DHCP* fails. If I make a static IP address, it appears to connect, however looking at my routers IP assignment tables, it proves negative.

Summary (of this): The card appears to work but is not actually connecting to my router. It detects the router (even tells me the correct access point) but will not connect.

Now, I also have tried connecting to the internet with an Ethernet card. This also did not work. I attempted a direct connection to the router, as well as a direct connection to another computer. The cables I used are not damaged, as they work with other computers. My Ubuntu detects the ethernet card (as seen in both the Device Manager, and the Networking options). However, it appears as no connection is made.

I would consider downloading/building the NDISwrapper (as well as NDIS), however as you can see, I have absolutely no way to access the internet on my Ubuntu machine.

Help on any one of these problems is greatly appreciated. As I've mentioned, I will try to get the results of the if/wconfig (or anything else you might need to help me troubleshoot) in the next few days. I should be able to answer any general question you throw at me from memory.

Thanks in advanced :).

---

### Post by deepwave on 2006-11-11
Let me get this straight...
For the non-ndis card use ran: iwconfig
And that displayed an entry for eth0 or wlan0.
And you ran dhclient (or dhcpd) with eth0 or wlan0, and that errored out?

Strange.

Other places to look for clues include:
dmesg - errors when inserting the card
/var/log/messages

---

### Post by JerryM on 2006-11-11
iwconfig showed me wlan0. It contained the correct access point, etc. When I ran dhclient with wlan0, it said something along the lines of "No DHCP Offers Received".

---

### Post by wieman01 on 2006-11-11
What does this say:
> iwlist scan

---

### Post by JerryM on 2006-12-19
Sorry for my largely delayed answer. I had time today to find the results you wanted, so they are as follows:

> ubuntu@ubuntu:~$ iwlist scan
lo	Interface doesn't support scanning.

eth0	Interface doesn't support scanning.

wlan0	Scan completed :
	Cell 01 - Address: MY ADDRESS
	ESSID: MY ESSID
	Mode:Master
	Frequency:2.437 GHz (Channel 6)
	Quality:44/92  Signal level=-239 dBm Noise level=-256 dBm
	Encryption key:on
	Bit Rates: 1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
		   24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
		   12 Mb/s; 48 Mb/s

sit0	Interface doesn't support scanning.

I apologize for any small mistakes that may be visible there. I had to type it by hand, since my Ubuntu cannot access the internet. As you can see, it finds my address and my essid correctly, and is on the same channel (6) as it should be. I can see the internet card being used, but it's just not connecting correctly..

Thanks.. I hope someone can help me solve my problem.

---

### Post by wieman01 on 2006-12-19
Your network card seems to work just fine. Have you checked out the network applet?

Before you try to establish a connection, please make sure that:

1. all wireless security is turned off
2. MAC filtering is disabled
3. 'network-manager' or 'wifi-radar' are not installed
4. firewall is down (using 'firestarter'?).

---

### Post by JerryM on 2006-12-19
Well, I tried the same day I made this thread to disable my security. I don't usually have MAC filtering on, and I'm not sure that network-manager or wifi-radar are installed (I don't have any internet access with the machine), nor do I think firestarter is on. Can you give me some tips to detect these things and shut them down (primarily the ubuntu parts.. don't need help for the router things).

Thanks a lot for your answer.

---

### Post by wieman01 on 2006-12-19
You can uninstall the packages using this command:
> sudo apt-get remove wifi-radar network-manager firestarter
You network scan says that wireless security is turned on... It's possibly WEP. Can you turn it off please? Have you got access to the router? There should be a section called "wireless security" or similar.

That done, please post the contents of this file:
> sudo gedit /etc/network/interfaces
Try to restart your network:
> sudo /etc/init.d/networking restart

---

### Post by JerryM on 2006-12-19
I have since turned my security back on of course ;) I'll get to these things in a few minutes. Many thanks again for your reply.

---

### Post by JerryM on 2006-12-19
Alright, so none of the packages are installed. I tried a networking restart, and as usual, under wlan0 I get a "No DHCPOFFERS received.".

As for the contents of the /etc/network/interfaces;

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid MY ESSID
wireless-key MY WIRELESS KEY

(note: my wireless key is in hex, in the format FFFFFFFFFF) If you still think I should disable my wireless security, I'll attempt that.

---

### Post by wieman01 on 2006-12-19
Please try this and restart the network...

Update "interfaces" file:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid [COLOR="Red"]your_essid[/COLOR]
Make sure wireless security is turned off & DHCP enabled. Then restart the network:
> sudo /etc/init.d/networking restart

---

### Post by JerryM on 2006-12-19
Fortunately I receive the same message, "No DHCPOFFERS received.".

> DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

Perhaps this could be the cause? My other computers say that the DHCP server is at 192.168.1.1, however I cannot find how to change that. Maybe this isn't the problem, becuase if I assign statically, it doesn't work either...

---

### Post by wieman01 on 2006-12-19
Did you enable DHCP on the router?

---

### Post by JerryM on 2006-12-19
> **wieman01 said:**
> Did you enable DHCP on the router?

Yes, it should be. My current connection on my windows computer says "Assigned by DHCP". So I would think it is enabled.

---

### Post by wieman01 on 2006-12-19
Please also check if your router accepts both Wireless G and Wireless B at the same time. Perhaps wireless adapter & router are not using the same standard? If that's not the problem, either, then I am running out of ideas...

---

### Post by JerryM on 2006-12-19
Well, I noticed a strange thing during the network restart that might be of interest...

> DHCPRELEASE on wlan0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set ESSID" (8B1A) :
      SET failed on device wlan0 ; Invalid argument.


Does Ubuntu 6.06 support ESSID's with spaces? EDIT: It seems this could be the core of my problems.. when I do this statically.. it doesn't go past the DHCPOFFER (as it shouldn't) and gives me a copy of the error above.
Yes, my router is configured for Wireless B and Wireless G simultaneously.

---

### Post by wieman01 on 2006-12-19
Spaces? Oh, this could be a problem... Can you choose one without spaces? This is certainly a problem. If this works, we'll enable encryption again.

---

### Post by JerryM on 2006-12-19
Well, that seemed to be the problem. Over a month of a problem caused by spaces ](*,) Thanks so much for your help :-).

---

### Post by wieman01 on 2006-12-19
Great. Encryption will be a cake walk now. If you need WPA1 or WPA2, take a look at the link in my signature. WEP is a very weak encryption standard.

---

