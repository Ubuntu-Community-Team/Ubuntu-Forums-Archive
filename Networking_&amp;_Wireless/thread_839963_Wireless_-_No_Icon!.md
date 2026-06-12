---
title: "Wireless - No Icon!"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by seantheman on 2008-06-24
Hey, I have a problem with my Ubuntu hardy setup.  Recently I managed to get the wireless network working 100%, with 4 bars and everything.  I installed a bunch of updates, and everything seemed to be going fine until recently.  You see, to get it working I had to right click the network icon when it booted up, and select wireless.  Now though, when it boots up, the icon isn't even there!  I tried going into network tools, and when I selected "unknown interface (wifi0)" it showed that it was receiving bytes and packets!  This is extremely weird to me... the internet still isn't working.  I am still somewhat of a noob when it comes to linux, so any help whatsoever would be wonderful.  Please! :(

---

### Post by Travisher on 2008-06-25
I have the same problem but at least I've battered it into submission a bit.
Using the examples in the HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. posted by wieman01.

I uninstalled the network manager, edited /etc/network/interfaces, the order of things is important as the man says and the Network Manager makes a horlicks of it.

However, in spite of my  efforts, only running
sudo /etc/init.d/networking force-reload actually starts the network. Thus on boot it fails to bring the interface up when networking is called. It seems to be a timeout thing because if I tail -f dmesg as I call /etc/init.d/networking I sometimes see wlan0 come available after the dhcp has given up. This does not seem to be the case when a force-reload is called.

So for now I have a script to kickstart the network.
It shouldn't be needed but...

> #!/bin/bash

echo "starting Wireless network"
sudo /etc/init.d/networking force-reload
exit

My /etc/network/interfaces looks like this

> auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp


auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <routeressid>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk a46e51e5e32d6bb6648fb9cb4a811626724774468de254421dc3578a3f



you can generate the wpa key for your site 

> wpa_passphrase <your essid> <your ascii key>

If anyone has any idea why networking start fails but force-reload doesn't I'd like to know.

---

### Post by chili555 on 2008-06-25
It's known bug. Please see: [http://ubuntuforums.org/showpost.php?p=1351902&postcount=2](http://ubuntuforums.org/showpost.php?p=1351902&postcount=2)

---

