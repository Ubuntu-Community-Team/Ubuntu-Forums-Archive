---
title: "[SOLVED] Wired Static IP Network - No Internet"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by tonel on 2008-03-05
I'm new to Linux and ubuntu having yesterday installed Gutsy Gibbon on my laptop.

Since installing it I've spent hours without success trying to get an internet connection through my router both wirelessly and wired.

I've been trawling the forum for a solution but haven't found one or in the suggested posts. 

Here's the situation:

I use static IPs for my network with each device wired to my router - except for my laptop which is normally wireless connected.

I installed ubuntu 7.10 as dual boot on my laptop. Couldn't get a wireless connection and so I decided to try for a wired connection - unplugged wireless card, plugged in Cat5 and rebooted.

Selected Manual configuration, Wired connection, configured a static IP, gave it a Host name (n25-linux) and Domain name (of my Windows Workgroup).

The IP and MAC addresses appear in the list of Attached Devices in my router settings, but as UNKNOWN instead of n24-linux - which to me seems strange, but I'm no network wiz.

From ubuntu I can ping my router and get a response. I can ping two of my computers (wired to my router) and get responses.

From both computers I can ping ubuntu and get a response.

Ping only works with the IP address - not the Host name (XP pings also by name but not to ubuntu)

From ubuntu I cannot ping and get a response from an external address.

It seems the problem is with the router but if I reboot my laptop into WinXP, it connects to the internet - albeit using a different IP address, Host name and MAC address. Thus the problem must be with ubuntu.

I hope that is understandable.

I would greatly appreciate any help. Does anyone have any suggestions or questions?

---

### Post by Eiríkr on 2008-03-05
Consumer-grade routers are usually set up for DHCP, and if I recall, hostnames for machines *not* getting an address from the router's DHCP server sometimes don't show up in the router settings.  

Windows is crazy promiscuous with its info, while Ubuntu (and other Linuxes I'm aware of) is not, and as part of this, it doesn't broadcast its hostname to anyone listening.  Have a look at [post=4458226]this post[/post] regarding host names and how to make sure all the machines know each other.  (NB: Windows XP hosts files are in the [font=courier]C:\WINDOWS\system32\drivers\etc[/font] folder.)

HTH,

Eiríkr

PS -- For the internet connectivity problem, post us the contents of your [font=courier]/etc/network/interfaces[/font] file -- I suspect you don't have a gateway assigned.  This should be the IP address of your router.

---

### Post by tonel on 2008-03-05
That was a very prompt response Eirikr. Thank you.

You're correct about the DHCP but I switched this off when I first set up static IPs for port forwarding. (This may give the impression I know what I'm talking about but it was just someone's procedure I followed.)

I'm not particularly bothered about the name not appearing. I only included it in case it had any bearing.

The info you requested follows. You'll see I have assigned the gateway address for wireless and wired. Although I have a problem with both I always find wireless can be a problem so I'm concentrating on getting wired working first. (I know I have a different static ip for wireless.)

tony@n25-linux:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.20.138
netmask 255.255.255.0
gateway 192.168.20.1
wpa-psk fac509863d596e5b572d72c9c0b64d15b9ab153c79cb4b372c8e46b8fd8038ab
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid TheMatrix

auto wlan0


iface eth0 inet static
address 192.168.20.145
netmask 255.255.255.0
gateway 192.168.20.1

auto eth0

---

### Post by jimv on 2008-03-05
It might be easier (and better) to set up the static IP addresses on your router.  This is done by telling the router which IP's to assign to which MAC addresses.  That way, you leave DHCP on on your computers and don't have to fiddle with settings if you for some reason plug into another network, but you will always have the same address on your home network.

---

### Post by tonel on 2008-03-06
Many thanks, jimv. I did as you suggested and that sorted it. I now get internet access through my wired connection. I can now get on with sorting my wireless connection for which there seems to be much more info available on the forum.

Thanks to you and Eirikr for your help.

Problem Resolved

---

### Post by Eiríkr on 2008-03-06
Glad to hear jimv's suggestion worked for you.  Since you note that your problem is resolved, please also mark the thread as SOLVED in the Thread Tools dropdown at the top of the page.  :)

Cheers,

Eiríkr

---

