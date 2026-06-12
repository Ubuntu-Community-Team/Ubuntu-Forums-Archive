---
title: "Wifi with wep doesn't work"
date: 2005-07-11
forum: Networking &amp; Wireless
---

### Post by pietrob71 on 2005-07-11
I have a RTL8180L card on hoary, ndiswrapper and win2000 driver. All works fine without wep encryption, but if I enable wep I can't ping my router and obiously I can't browser anythings. I have read a lot of post and howto and therefore I've tried a lot of syntax in my /etc/network/interfaces like :

"wireless-key on XXXXXXXXXX"
"wireless-key on XXXX-XXXX-XX" 
"wireless-key XXXXXXXXXX"
"wireless-key XXXX-XXXX-XX"
"wireless-key [1] XXXXXXXXXX"
"wireless-key s:XXXXXXXXXX"

but nothing  ](*,) 

My router is a Dlink G604T, authentication type "open", cipher 64 bits; with this settings my ibook works perfectly, therefore there's somethings wrong in my linuxbox.

I hope someone can help me.

Thanks in advance

---

### Post by dave9191 on 2005-07-11
Hey, 

This is stright out of the configuration script for my wireless card I wrote a while back. 


sudo iwconfig eth1 key KEY_IN_HEX_FORMAT 
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 ap MAC_ADDRESS

Note that you cant use a passphrase as they aren't supported yet. The key has to be the full ugly looking hex key. Also on a side note, wep is really bad. I was just talking to guy a doing a php in my department and he can break into a 128bit wep network in less then 30 min. Its his cool project :) 

Dave

---

### Post by pietrob71 on 2005-07-11
This is my /etc/network/interfaces

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
#iface eth0 inet static
# 	address 192.168.1.10
#	netmask 255.255.255.0
#	network 192.168.1.0
#	broadcast 192.168.1.255
#	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
#	dns-nameservers 192.168.1.1

iface wlan0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
dns-nameservers 192.168.1.1
gateway 192.168.1.1

wireless-essid G604T_WIRELESS
wireless-channel 6
wireless-mode managed
wireless-key off

auto wlan0
---------------------------------------------------------------------------------------
It's work fine without wep.

If this is my test wep key -> 0123456789,
the router's MAC address is 00:11:95:96:b0:70
and authentication type is open,
how can I modify the interface file to have wireless up at boot?

---

### Post by dave9191 on 2005-07-11
Hey, sry, my code was from a command line script not from the network interfaces file. I use several wifi networks so i have a seperate script i run for when i am in the range of a different network. in the interfaces file you want to ass something like:

auto wlan0
#iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid   G604T_WIRELESS
wireless_key     132ec42a32d21374ab3d62e7fe
wireless_channel 6
wireless_mode    managed



I put your key as in the example above, becasue thats hows its supposed to look 132ec42a32d21374ab3d62e7fe , 

Dave

---

### Post by pietrob71 on 2005-07-11
Thanks a lot

Only last answer: 0123456789 is what I put in my router and in my ibook. How do you have transformed my 0123456789 in 132ec42a32d21374ab3d62e7fe?

Thanks for your patience  O:)

---

### Post by dave9191 on 2005-07-11
In your router when you set the key you should have 1 or possibly 2 methods of doing this. One will be to type the hex key in full and the other to type a passphrase which generates a hex key. If this is what your router does, it should also be able to tell what the key is in hex format. 

On the 2 routers thats I have used and configured they let you type a passphrase and generated a hex key from it. Im not sure how you would change a pass phrase to a hex key but I could mess around with it when i have some more time. But hopefully your router should tell you :)

Dave

---

