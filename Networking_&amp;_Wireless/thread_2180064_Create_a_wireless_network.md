---
title: "Create a wireless network"
date: 2013-10-11
forum: Networking &amp; Wireless
---

### Post by timo2 on 2013-10-11
Hey all,

At the moment I'm using only Ubuntu at my notebook and I'd to create a wireless network like
in Windows 7.
I used the command line and used the 'netsh wlan' command for it.

In Ubuntu I found a function to create a wireless network but with every try a Windows notebook
is throwing me out the following error: 'Wrong password'.

I tried it like this too: [http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)
But  at my computer there are not that much options.

I'm running the newest Ubuntu version :-)

---

### Post by scbingham on 2013-10-11
To create a wireless hotspot your wireless adapter needs to have the capability to act as an access point, not all do.

A very simple solution would be to use a wireless router. That would then create a wireless network for Ubuntu & windows laptops, phones, etc and also enable you to share your existing internet connection.

---

### Post by timo2 on 2013-10-12
Hey,

At home I'm hosting my wireless network with a TP-Link TL-WR1043ND.
But in school I'd like to create a wifi network with my mobile UMTS stick and share
this internet connection over a wifi network.

I can't always take a router with me.

Thanks
Timo

---

### Post by scbingham on 2013-10-12
I'm not quite sure what you are trying to achieve.

Your UMTS stick connects your laptop to a mobile phone wireless network, giving it an internet connection. WiFi doesn't come into it.

A mobile phone can be used as a hotspot to provide an internet connection to a few users.

If this is what you're trying to achieve, then first you need to be able to set your laptop's wifi adaptor to act as a hotspot.
Then you need to set up your UMTS adaptor to give you a connection via the mobile phone network.

Once you get those working, then you need to bridge the two networks together ie your laptop wifi adapter & UMTS adaptor, as they are two separate networks.

---

### Post by timo2 on 2013-10-17
Hey

I wan't to connect with another Windows laptop to my Ubuntu laptop but the
auth always says "Wrong password".

I'm using the "Create hotspot" function in Ubuntu itself.

- Thanks Timo

---

### Post by alivema4ever on 2013-10-18
> **timo2 said:**
> Hey all,

At the moment I'm using only Ubuntu at my notebook and I'd to create a wireless network like
in Windows 7.
I used the command line and used the 'netsh wlan' command for it.

In Ubuntu I found a function to create a wireless network but with every try a Windows notebook
is throwing me out the following error: 'Wrong password'.

I tried it like this too: [http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/)
But  at my computer there are not that much options.

I'm running the newest Ubuntu version :-)

You can't do it with Create Wireless on Network Manager. It's just creating an ad-hoc network. Android phones can't connect over ad-hoc network.
You must use hostapd to create an infrastructure wireless network (Access Point/AP mode). You need an AP-capable wireless adapter. Check your wireless capabilities by issuing
```
sudo iw list | more -d
```
If you find AP bellow supported modes, you can proceed to next step. Else, you need another wireless card.

Install hostapd to act as wireless access point daemon and dnsmasq as dhcp+dns server
```
sudo apt-get install hostapd dnsmasq
```

Then, configure hostapd to act as wireless access point. Make a configuration file [/etc/hostapd/hostapd.conf]("http://wireless.kernel.org/en/users/Documentation/hostapd#Common_Options") to use with hostapd
```
interface=wlan0driver=nl80211
ssid=your_wifi_name_here
hw_mode=g
channel=1
# If your card supports n mode, make these two lines uncommented (remove # sign).
#wme_enabled=1
#ieee80211n=1
# If you want full wireless N speed, uncomment the line bellow
#ht_capab=[HT40+] [SHORT-GI-40]
macaddr_acl=0
auth_algs=1
wpa=2
wpa_passphrase=your_passphrase_here
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```

And add the following line to [/etc/network/interfaces]("http://www.debian.org/doc/manuals/debian-reference/ch05.en.html#_the_basic_syntax_of_etc_network_interfaces") to assign a static ip address on wlan0 (as gateway to other clients)
```
iface wlan0 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255

```

Configure dnsmasq to act as DHCP server on interface wlan0
file [/etc/dnsmasq.conf]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example") (you can copy the original file elsewhere as backup and create a new one)
```

# The line bellow tells dnsmasq to assign ip address randomly between 192.168.1.150 and 192.168.1.160 (11 ip addresses)
# If you need more clients, modify as needed
dhcp-range=wlan0,192.168.1.150,192.168.1.160,2h
# The line bellow fixes a DHCP bug on Windows 7
dhcp-option=252,"\n"

```

Launch these commands in correct order to start your wifi.
```
sudo sysctl net.ipv4.ip_forward=1 #to enable ipv4 forwarding
sudo iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE #to enable routing through ppp0
sudo hostapd -B /etc/hostapd/hostapd.conf #to start hostapd in the background
sudo ifup wlan0 #to bring up wlan0 interface
sudo service dnsmasq restart #to restart dnsmasq with a new configuration
```

That's it! If you want to end your wifi session, issue these commands
```
sudo killall hostapd
sudo ip link set wlan0 down
sudo iptables -t nat -D POSTROUTING -o ppp0 -j MASQUERADE
sudo sysctl net.ipv4.ip_forward=0
```

Good luck.

---

