---
title: "Wireless With Static IP (wifi works only in nm-applet)"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by monkey56657 on 2007-12-06
Hello, 

I am able to connect to my wpa1 wireless network by connecting via the nm-applet. However my network usually uses static IPs with DHCP disabled. I see no option in nm-applet to setup static IPs. 

I have tried to manually configure and connect by using the GUI under System > Administration > Network as well as manually entering details @ /etc/network/interfaces but it fails to connect. I dont really know whats happening in the background but nothing is going on. 

Im not the one to make an obvious mistake and I do know enough about networking...except when it comes to linux, so its linux related answers only please. 

So any ideas on how I should go about getting this wireless working using static IPs?

W-NIC: Atheros 5006EG (in a toshiba A100-027) using the Atheros driver in the 'restricted drivers manager'. 

Thanks in advance...

---

### Post by erfahren on 2007-12-06
It sounds like you're using Gutsy, Feisty had poor WPA support through the Network Manager.

Anyway, once you get your network set up in there do:
```

sudo /etc/init.d/networking restart

```
and see if you can connect.

note: with static IP you need to enter the DNS's as well.

I use the setup shown in this thread (with Feisty), 
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
which basically just sets up everything through the /etc/network/interfaces file manually. There's a script there (2nd post) to restart wifi at boot (I also created little launcher scripts to stop and restart it through Gnome's main menu).

for reference, my /etc/network/interfaces looks like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet static
address 192.168.0.3
gateway 192.168.0.1
dns-nameservers 205.171.3.65
netmask 255.255.255.0
wpa-driver madwifi
wpa-ssid <mySSID>
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <mykey> 

```

---

