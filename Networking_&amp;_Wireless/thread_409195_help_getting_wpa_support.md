---
title: "help getting wpa support"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by nielsonp on 2007-04-14
after reading these instructions [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) i have a question for you.

once i type all the stuff in the interfaces file i am getting an error when i try to restart the networking interfaces by tying in sudo /etc/init.d/networking restart i get

*reconfiguring network interfaces...
/etc/network/interfaces:9: too few parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"

my interfaces file contains the following: (the stuff in brackets are comments WRITTEN IN THE POST ONLY they are not contained in the interfaces file

#the looback network interface
auto lo
iface lo inet loopback

auto eth0 (my wireless interface)
iface eth0 static
address 192.168.2.86
netmask 255.255.255.0
network 192.168.2.1
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameservers 192.168.2.1
wpa-driver wext
wpa-conf managed
wpa-ssid (my ssid which isn't going to be disclosed, you could be my neighbour with a wireless card :) )
wpa-ap-scan 2
wpa-pronto CCMP
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
(then follolw a long string of numbers and letters which i probably shouldn't share for security reasons, no offence i run this place more secure than the CIA or FBI could ever even hope to)


-----------------------------------------------------------------------------------
extra info which will probably help
my wireless card i am using is just a belkin PCMIA 54g wireless card
the laptop is an Acer travelmate739tlv
my router is a belkin all in one modem/router
the address for it is 192.168.2.1
the subnet mask is 255.255.255.0
the ssid broadcast is disabled
the DHCP server is disabled everything on my network is static
the ip address i intend the machine to have is 192.168.2.85
it may make a difference but this card is also used in my other laptop and i do need to re enter my security settings when i bring it back to my main laptop after using it in the acer.

I hope that you are all able to help and i thank you all heaps, and i hope i have given enough info.

---

### Post by dbott67 on 2007-04-14
I connected to my dad's [D-Link DIR-655]("http://www.dlink.com/products/?pid=530") (using WPA) with [NetworkManager]("http://www.gnome.org/projects/NetworkManager/"):

```
sudo apt-get install network-manager-gnome
```[IMG]http://www.gnome.org/projects/NetworkManager/images/wireless-at-tealuxe.png[/IMG]

Absolutely no futzing around with WPA supplicant or config files.  NM detected the network, I selected "Connect" and it asked me for the WPA passkey.  It just worked! :)

At home, I use 128-bit WEP.  No editing of the /etc/network/interfaces file required.  Here's my interfaces file while using NM:
```
dbott@edgy:~$ cat /etc/network/interfaces
auto lo
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

```So, install NM and give it a try.  You may need to comment out all of your WPA & wireless related settings:
```

#the looback network interface
auto lo
iface lo inet loopback

auto eth0 (my wireless interface)
[COLOR=Red] iface eth0 inet dhcp [COLOR=Blue]*<-- add this line back, even though you use static*[/COLOR][/COLOR]
[COLOR=Red]#  [/COLOR] iface eth0 static
[COLOR=Red]#  [/COLOR]address 192.168.2.86
[COLOR=Red]#  [/COLOR]netmask 255.255.255.0
[COLOR=Red]#  [/COLOR]network 192.168.2.1
[COLOR=Red]#  [/COLOR]broadcast 192.168.2.255
[COLOR=Red]#  [/COLOR]gateway 192.168.2.1
[COLOR=Red]#  [/COLOR]dns-nameservers 192.168.2.1
[COLOR=Red]#  [/COLOR]wpa-driver wext
[COLOR=Red]#  [/COLOR] wpa-conf managed
[COLOR=Red]#  [/COLOR]wpa-ssid (my ssid which isn't going to be disclosed, you could be my neighbour with a wireless card :smile: )
[COLOR=Red]#  [/COLOR]wpa-ap-scan 2
[COLOR=Red]#  [/COLOR]wpa-pronto CCMP
[COLOR=Red]#  [/COLOR]wpa-pairwise CCMP
[COLOR=Red]#  [/COLOR]wpa-group CCMP
[COLOR=Red]#  [/COLOR]wpa-key-mgmt WPA-PSK
```

NM maintains all the settings & you can set static addresses in there, if you wish.


-Dave

---

