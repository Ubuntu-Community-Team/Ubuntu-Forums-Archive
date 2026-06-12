---
title: "Feisty wireless on BCM43xx works great... for a while..."
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by ZCarPilot on 2007-05-11
I recently did a fresh install of Feisty (Ubuntu 7.04) on my HP Pavilion zd8000 laptop, which has a BCM4318 wireless nic built in.  I could not get the drivers created by fwcutter to work reliably, and I didn't want to use network-manager, so I blacklisted the bcm43xx driver, purged network-manager, and installed the driver that came with WinXP using ndiswrapper.  I created the following /etc/network/interfaces file (the names and passwords have been changed):  

auto lo
iface lo inet loopback

# auto eth0
iface eth0 inet dhcp

# auto eth1
iface eth1 inet static
        name Broadcom 802.11 b/g
        wpa-ssid my_ssid
        wpa-psk my_wpa_psk
        address 192.168.14.105
        netmask 255.255.255.0
        network 192.168.14.0
        broadcast 192.168.14.255
        gateway 192.168.14.1
        dns-nameservers 192.168.14.240
        dns-search mynet.net

After adding the line "/sbin/ifup eth1" to my /etc/rc.local file (thanks to the suggestion from another forum member whose name I don't recall), everything works when I boot up and I'm on my local network, etc.

The problem is that after some undetermined amount of time, the wireless network connection stops working.  Output from both ifconfig and iwconfig indicate that everything is still configured and up, but no traffic gets through.  If I 'sudo ifdown eth1' and then 'sudo ifup eth1' everthing is fine again... for a while.

Anyone else seen this?  This is the last thing I need to get taken care of in order to make the switch from Breezy.

BTW, I've been using Breezy Badger (Ubuntu 5.10) since it was released, on this same laptop, using ndiswrapper (a previous version) and the WinXP driver, and it works fine as long as I don't bounce the interface too many times.

Thanks!

---

### Post by ZCarPilot on 2007-05-14
Interestingly enough, this problem seems to have been solved when I added a rule to iptables to just drop packets from my TiVO box (TiVO apparently occasionally broadcasts queries to udp port 2190) instead of logging them and then dropping them.  I'm not sure why trying to log these packets caused a problem, but I now seem to have a stable, reliable wireless connection to my AP using WPA-PSK.  Go figure...

---

### Post by ZCarPilot on 2007-05-14
Well, no, I spoke (wrote) too soon.  It's back to coming and going.  Any (helpful) ideas?

---

### Post by ZCarPilot on 2007-05-16
A little more info... when the connection goes away, everything *seems* to still be fine.  That is, ifconfig shows the interface still up and configured properly, and iwconfig shows the correct ssid and good signal strength.  However, 'sudo iwconfig' shows that the encryption key is missing; this is the only difference I can see so far.  

So evidently, wpa_supplicant is losing the key or not reauthenticating or ???

---

### Post by ZCarPilot on 2007-05-30
An update... I set my access point to use WEP instead of WPA, and the connection has been stable since then.  This was after looking at megabytes worth of wpa_supplicant logs and finding that when the connection went down I could almost always restore it by doing *sudo /etc/init.d/networking restart*. 

So, I think the problem is with the way wpa_supplicant negotiates key changes, but I don't know enough about how it works to have any idea where to look (not that I've got any spare time *to* look).

---

### Post by zeller on 2007-07-31
Could you take me step by step how to set up mine the same way? I haven't been able to get the BCM4318 card to work with ndiswrapper.

---

### Post by newman on 2007-07-31
I managed to get my compaq laptop with the same BCM4318 working with ndiswrapper in ubuntu and fedora, but what a pain! I was really slow. I tried PCLinuxOS and the ndiswrapper setup was so easy, and worked better overall. But I don't like the idea of using flaky windows drivers so I gave up and installed fedora on my other laptop with a RT2500 wireless chipset which seems to have native Linux support. Bottom line - Broadcom + Linux = crap.

---

### Post by zeller on 2007-07-31
Well, I had it working after using a script found elsewhere here on the forums that basically installed some kind of firmware to work with the BCM43XX cards. The max was 11mbps and was flaky at best. Every few minutes it would lose connection and then reconnect. I was hoping that ndiswrapper would provide more stable support and a better range from the AP.

---

### Post by ZCarPilot on 2007-08-18
I've come to the conclusion that this is a problem with either the version of wpa_supplicant included with Feisty or its interaction with the kernel.  The BCM4318 in my laptop works fine with ndiswrapper and WEP, it's just not reliable with WPA.  This same problem is exhibited on another laptop with a PC card wireless nic that has the Atheros chipset.

---

