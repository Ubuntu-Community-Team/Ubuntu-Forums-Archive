---
title: "Network Doesn't Always Come Up"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Noggin on 2006-12-17
Ubuntu 6.10
Laptop - HP Pavilion HX635
Wireless - Netgear WG511, no version number, made in China.  DHCP
Wired - Onboard, chipset unknown.  DHCP
Dual boot w/ WinXP using Grub

In short, my network connection doesn't always come up.  I'm using a Linksys router with the DD-WRT micro firmware installed on it.  I have had 0 problems with this router when using Windows with it.  I'm fairly new to linux.  The problem I'm having is that my network doesn't always show up.  The first time I booted up after installing linux, my wired connection worked fine.  I then followed the directions [here](http://www.linuxquestions.org/linux/answers/Networking/Netgear_WG511_v3_Made_in_China_with_WPA_on_Ubuntu_6_06_LTS_Dapper) to work on getting my wireless connection running using WPA-PSK.  I'm using the Win2K driver found at the address given near the top of his guide.  The problem I'm having now is that the majority of the time I book linux neither my wireless or my wired connection works.  

When my wired connection doesn't work, it says its requesting a network address and eventually comes back with a 169(I think).xxx.xxx.xxx number as opposed to the 192.168.1.xxx as expected.  When my wireless connection doesn't work, it either isn't in my network manager list, or more often, it just simply fails.  Right now, I'm online through my wireless connection.  When my wireless fails, ndiswrapper -l lists my driver and hardware as being present.

I am sitting about 10 to 15 feet from my router and I have a full strength signal.

[quote="wpa_supplicant.conf"]ctrl_interface=/var/run/wpa_supplicant


network={
ssid="Noggin"
psk="<key>"
priority=5
}[/quote]

[quote="interfaces"]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid Noggin
wireless-key s:<key>

auto wlan0[/quote]

---

### Post by fredj on 2006-12-17
Like you I have perfect wireless networking in win XP. I tried using network-manager in
Ubuntu because of its apparent flexibility but I found that it was just too unstable, often
the connection would not come up. There were frequent disconnects for no apparent
reason. In the end I gave up and configured my Interfaces file and wpa_supplicant.conf
file. Since then I have had perfect wireless networking in Ubuntu.

Here is my Interfaces file - N.B. My wireless card is eth1. You would have to substitute
the name of your wireless driver module in place of 'wext' 
----------------------------------------------------------------
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
----------------------------------------------------------------


Here is the /etc/wpa_supplicant.conf file
---------------------------------------------------------------
network={
        ssid="G604T_WIRELESS"
        psk=<my encoded wpa passphrase>
}
---------------------------------------------------------------

You can use the  programe wpa_passphrase <ssidname> <wpa passphrase>
to generate the contents of wpa_supplicant.conf and then just copy and paste them
into a /etc/wpa_supplicant.conf file

Since doing it this way I haven't had a single dropped wireless connection.
I am running ver 6.06 of Ubunu (Dapper).

---

### Post by eggdeng on 2006-12-17
> **fredj said:**
>  In the end I gave up and configured my Interfaces file and wpa_supplicant.conf
file. Since then I have had perfect wireless networking in Ubuntu.

Could you tell us what Interfaces file you are talking about?

---

### Post by Noggin on 2006-12-18
> **eggdeng said:**
> Could you tell us what Interfaces file you are talking about?

/etc/network/interfaces

---

### Post by Noggin on 2006-12-18
I havn't verified this with 100% certainty, but I do have strong reason to believe that a reboot from Ubuntu to Ubuntu will cause my wired network to not function, but a reboot from WinXP to Ubuntu or a full power cycle will allow the network to work.

---

