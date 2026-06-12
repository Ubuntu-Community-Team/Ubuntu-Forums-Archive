---
title: "Linksys WUSB54Gv2 no WPA"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by cor2y on 2008-09-23
Hi I have a pc that uses the linksys WUSB54Gv2 wireless adapter.
I finally got it working with the new ndiswrapper , however it will only connect with the unencrypted setting ,wep, wpa, wpa2 doesn't seem to work.
I thought maybe wpasupplicant was not installed but it is.
It recognizes the connection is encrypted and asks for a password when in roaming mode but it will not connect when the password is added.
Was anyone able to get this wireless adapter to work with encryption?

---

### Post by panhandle on 2008-09-23
Did you check this thread?

[http://ubuntuforums.org/showthread.php?t=661899&page=2](http://ubuntuforums.org/showthread.php?t=661899&page=2)

Seems like there are quite a few links and it seems the O.P.s problem was solved, though not marked as such.

---

### Post by cor2y on 2008-09-23
that seems to be a different version of ubuntu probably 7.10
I don't have a interfaces.conf file anywhere on my system i DO have a interfaces file but it has none of those settings in there.
Just two lines

auto lo
iface lo inet loopback

---

### Post by willca on 2008-09-24
First of all lets verify if you wifi is even working before proceeding with the next steps as outlined.

sudo iwlist wlan0 scan

If at this point it sees other wireless networks, then great!

So now if you want to use WPA which is better than WEP here is how I go about this. It does not matter if its Gutsy or Hardy or Debian Etch or something. This works across Debian derivatives.

sudo apt-get install wpasupplicant (of course we need this)

Edit /etc/wpa_supplicant.conf

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="YourWiFiSSID"
   psk="YourWiFiPassword"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }

Test if its working....

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

If it does then move onto the next.

Edit /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant


Then /etc/init.d/networking restart

---

### Post by cor2y on 2008-09-24
Thanks a lot for the info willca.
Heres the latest result.
Followed your instructions but it wouldn't connect then i figured out that it was because the router was using AES instead of TKIP so i changed the router setting to TKIP.
Restarted  networking everything says its connected (little wireless icon appears says its connect at 90% like how it is when it was set to unencrypted) however firefox ,synaptic etc says i have no internet connection.

---

### Post by shanix on 2008-09-24
Then it might be the DNS issue. Check at the Network Manager side or router side to see if everything is setup correctly.

You can set the DNS to 4.2.2.2 which is a public DNS server.

---

