---
title: "wpa_supplicant refuses to connect fir"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by ifmusic on 2007-04-19
Hi!
I'm using Ubuntu 7.04 (beta).
i read the How To get wireless and WPA working. 
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) (HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.)
I am using ndiswrapper and it seems to work ok. The iwlist scan command shows me My AP ssid "CasitaWiFi"
The AP is configured to use WPA-PSK security and lets say that my password is a "ververylongpassphrase". So the AP is using a Ascii key 63 bytes long.
I have no trouble at all in Windows XP to connect to the AP using the "ververylongpassphrase" so i know that the AP works fine with WPA security.
This Ubuntu version has a GUI connection config box, that will prompt you for a WPA Personal password.
I tried with the Ascii key : "ververylongpassphrase" (63bytes) and with the hex that i got from using wpa_passphrase CasitaWifi ververylongpassphrase, But BOTH were rejected. I know the Password is right so why is wpa_supplicant refusing it?!!

Thanks!!!

---

### Post by ifmusic on 2007-04-20
I could post my interfaces file, or any other that could help solving this. It's annoying because i know i must be close!!!!

---

### Post by ifmusic on 2007-04-20
/etc/interfaces:

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.88
netmask 255.255.255.0
gateway 192.168.0.1

auto wlan0
iface wlan0 inet dhcp

```

I know it has no WPA related stuff but the GUI prompts me for a WPA password so i guess it's ok.

Since i wasn't able to get it working i tried using wpa_supplicant directly heres a config file for it:

```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=1
### Example of basic WPA-PSK secured AP
network={
	ssid="CasitaWiFi"
	key_mgmt=WPA-EAP WPA-PSK IEEE8021X NONE
	proto=WPA
	pairwise=CCMP TKIP
	group=CCMP TKIP WEP104 WEP40
         psk="my 63 byte password"
       # and the hex created from the actual 63 byte long passphrase.
         psk=c9fe8d236c31ec1499cbd52af8f4b15ee4c02089df8359f21b20b5e3f8457c6a
  }

```

So i call wpa_supplicant -ieth1 -Dwext -c/home/ifmusic/config. i think that's all the parameters...
It responds that It's "Associated to <the AP mac address>"
but after a couple of seconds authentication fails, over and over again forever.
The gui gives up after some attempts.

PLEASE ! some help!

---

