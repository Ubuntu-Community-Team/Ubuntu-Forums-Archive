---
title: "Wireless configuration still not working...."
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by dumas on 2007-03-10
Hi,

I made a post about a week ago about can't getting on wireless network, but the thread died off as I had only restricted internet access time. I think I can now access the internet about half an hour a day through other PCs, so I hope you guys can help me out this time. I'm putting my information such as iwconfig and lspci results into a zip file so that you guys take a look while I'm not around.

As for my computer, it is a laptop, NEC Versa E6000. It uses Centrino and Atheros. As I understand, the drivers are working. I can detect my router, I think I have access point to it, but I don't have an IP address. Static IP doesn't work, and dhclient doesn't work either. So I am really at a loss of how to solve this problem myself.

Any help would be greatly appreciated.
Thanks in advance.

---

### Post by RomeReactor on 2007-03-10
Hi. I have no experience with your card's chipset, but since it looks to be correctly installed, my guess is your issue has to do with configuration only; so please post your **interfaces** file:

```
gedit /etc/network/interfaces
```

if you are on Ubuntu; if you're using Kubuntu, then:

```
kate /etc/network/interfaces
```

---

### Post by dumas on 2007-03-10
Thanks RomeReactor, this is the interface file:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

iface ath0 inet dhcp
wireless-essid Fung
wireless-key 3141592654
address 220.236.165.77
netmask 255.255.255.0

auto wlan0
iface wlan0 inet dhcp

auto eth0

auto ath0

Another thing is, I tried [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) and things aren't working. It shows the wireless networks but cannot connect, as in the previous situation. However, now I lost the access point too, even though I can detect my network. Using iwconfig to connect to my router doesn't work. I'm not sure how to disable this manager. I tried to uncomment the interface and change wpasupplicant to ENABLED=1, or remove wpasupplicant altogether, but I can't get back to the original situation. How do I disable this manager, or continue with it?

Thanks

---

### Post by RomeReactor on 2007-03-10
I recommend you uninstall Network Manager (look for it in Synaptic); according to the lshw information you provided, the logical name of your wireless card is **wifi0**, so your interfaces file should look like this:

```
auto lo
iface lo inet loopback

#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto wifi0
iface wifi0 inet dhcp
wireless-essid Fung
wireless-channel 6
wireless-mode managed
wireless-key s:3141-5926-54
#address 220.236.165.77
#netmask 255.255.255.0

#auto wlan0
#iface wlan0 inet dhcp

#auto eth0

#auto ath0
```

Then save the file and reboot. If it still doesn't want to connect, then do

```
sudo dhclient wifi0
```

Post back with the results.

---

### Post by dumas on 2007-03-11
Thanks again, but still not working.

I removed the network manager and the network situation resumes the old condition, that is, I can detect the router, have access point, but don't have IP address.

(Aside, a minor problem is some gnome daemon is removed as well, but we can leave it till later)

I changed the interface to the one you give me, but doesn't work. dhclient also doesn't work. The dhclient output is in the zip file attached. Playing around with the configurations a bit, I again enabled ath0 in the interface and now ath0 have AP but not IP. I've attached the altered interface.

My guess now is wifi0 is not supported by the driver, but I don't really know. I've attached some screenshots to see if that helps.

Thanks.

---

### Post by RomeReactor on 2007-03-11
Have you tried disabling WPA in the router? You can enable it after you sort the connection issue; also, perhaps using [ndiswrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") could help: A search for **AR5212** on their list brought this up (along with many other results):

```
# Card: D-Link AirPlus ("Xtreme G") DWL-G520 Wireless PCI Adapter (H/W Ver. B2)

    * Chipset: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
    * pciid: 168c:0013
    * Driver: [here]("ftp://ftp.dlink.it/pub/Wireless%20Extreme%20G/DWL-G520_(108Mbps)/Driver/4.30/D-Link_AirPlus_XtremeG_Utility_(V4.3_Build50406)_G520_WPA2_ww.zip")
    * Other: Works OK with ndiswrapper 1.8 on Ubuntu Dapper Beta with NetworkManager 0.6.2.
    * Other: No signal strength indication. WPA2PSK encryption working.
```

---

### Post by ataranlen on 2007-03-11
I was about to say that it might be a router problem as to why you can see the router, but not get an IP. My Dad tried to mess with the mac adress filter and locked us out completely. Perhaps you should Reset your router?

---

### Post by dumas on 2007-03-13
It's working!

I used ndiswrapper, and my brother happened to have reset the router, I guess he messed up with the router before, and so resetting the router fixes the problem. A really big thank you to you guys for helping out. Ubuntu rocks!

---

