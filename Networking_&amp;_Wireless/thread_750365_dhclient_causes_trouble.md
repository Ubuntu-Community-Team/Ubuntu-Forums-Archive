---
title: "dhclient causes trouble"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by equity on 2008-04-09
The dhclient causes trouble permanently.
I set up an IP for my WLAN adapter (eth1) and a netmask when enabling with ifconfig but the dhclient permanently acquires an IP from the AP...

Is it possible to connect to APs without the dhclient??

Edit: I use no network manager, only command line

---

### Post by dstew on 2008-04-09
> Is it possible to connect to APs without the dhclient??Yes, I think you just set up your WLAN adapter to use a static IP address in the Network window. You have to assign a proper IP address, and netmask. Then, it should not send any requests to the DHCP server. I think you can also disable dhclient by editing the /etc/network/interfaces file, but I believe that the Network window edits this file for you.

If you want to kill the dhclient process, you can do ```
killall dhclient
```

---

### Post by equity on 2008-04-09
ah sorry,
I did not mention that I do not use any network manager any more since I got too much trouble using nm-applet or wifi-radar.
Now I connect only via CLI using the method kevdog performed:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by dstew on 2008-04-09
Post the contents of your /etc/network/interfaces file.

---

### Post by equity on 2008-04-09
auto lo
iface lo inet loopback








auto eth1
iface eth0 inet static
address 192.168.2.107
gateway 192.168.2.1 
dns-nameservers 192.168.2.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid www.hett.IT
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 363ba68f061979973b5a632b51b192eac995dcef1ebfcbcb3cd03d2f92acd10f

---

### Post by equity on 2008-04-09
but this is not the AP I am currently connected to.

---

### Post by dstew on 2008-04-09
Where is the interface information for eth0? If you are not using eth0, delete the auto eth0 line from the file. If you are using eth0, then you should configure it with an iface statement.

I don't know much about wpa configuration. I would set the SSID by```
sudo iwconfig eth1 essid "Whatever_Your_ESSID_Is"
```Is your router set up with WPA encryption? Is that the correct key?

---

### Post by equity on 2008-04-10
Yes, actually it is WPA2 encrypted. But the key is converted into hey as wieman01 adviced:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

The rest is like kevdog explained:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by wieman01 on 2008-04-10
> auto eth1
iface eth0 inet static
This is obviously wrong. It should read:
> auto eth0
iface eth0 inet static
Or:
> auto eth1
iface eth1 inet static

---

### Post by equity on 2008-04-10
> **wieman01 said:**
> This is obviously wrong. It should read:

Or:


Okay, now it is as following:



auto lo
iface lo inet loopback








auto eth1
iface eth0 inet static
address 192.168.2.107
gateway 192.168.2.1 
dns-nameservers 192.168.2.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid [www.hett.IT](www.hett.IT)
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 363ba68f061979973b5a632b51b192eac995dcef1ebfcbcb3c d03d2f92acd10f

---

### Post by wieman01 on 2008-04-10
Still wrong, see post #9.

---

