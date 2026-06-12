---
title: "Multiple Wireless Profiles?"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by Falkon MX-5 on 2007-02-19
Okay, I've been looking up how to set up multiple profiles for wifi connection.  Here is exactly what I want.

1.  "Home" profile connects to <ssid> and uses <WEP Key> to connect
2.  "School" profile connects to <ssid> and uses <WPA Key> through wpa_supplicant to connect
3.  "default" profile through wpa_supplicant uses any suitable ssid and no key

All these should use DHCP.  
Wireless Assistant sucks, it doesn't work for ****
Wifi Radar is even worse

wpagui is great, but I'm not using wpa for the home connection.  Can I just handle everything through wpa_supplicant?

Here is the setup in /etc/network/interfaces

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface default inet dhcp

iface uah inet dhcp

iface home inet dhcp
        wireless-channel 11
        wireless-essid HomeTown
        wireless-key abbadabbafadda146906231978

```

and here is wpa_supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
 ctrl_interface_group=root
 network={
        ssid="Student5"
        scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        #pairwise=TKIP
        #group=TKIP
        #psk="Go Chargers!"
        psk=6b478d4e5dd413b48e554afe74144e44823cf57bc183d19d7d410d0737c35fa1
        is_str="uah"
 }

 network={
        #This is default
        ssid=""
        mey_mgmt=NONE
 }

```

Do I need to add a profile for the home connection?  It is currently not wanting to work automatically.  I don't mind having to run wpagui to select which profile.  

Also, is there a way to get wpa_supplicant to start up with the other networking services?

---

### Post by Falkon MX-5 on 2007-02-19
Well, I made a little shell script to start up wpa_supplicant.  Now, I just need to be able to select a network to connect to and have it work whether using wpa or wep.  I'm going to look through the examples and see if WEP can be used through Wpa_supplicant.

Come on, I'm asking a very specific question, not one of these vague "OH GOD MY WIRELESS DOESN'T WORK FIX IT" threads.

---

### Post by Falkon MX-5 on 2007-02-19
Okay, I found out how to get WEP through wpa_supplicant.  Now, I can get it to automatically select the network [or so it seems].  It'll connect, verify WEP keys, but won't get an IP until I type dhclient eth1.

Here is the updated /etc/network/interfaces and /etc/wpa_supplicant/wpa_supplicant.conf

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
        wpa-driver wext
        wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface default inet dhcp

iface uah inet dhcp

iface home inet dhcp
        wireless-channel 11
        wireless-essid HomeTown
        wireless-key abbadabbafadda146906231978

```

```

ctrl_interface=/var/run/wpa_supplicant
 ctrl_interface_group=root
 network={
        ssid="Student5"
        scan_ssid=1
        key_mgmt=WPA-PSK
        proto=WPA
        #pairwise=TKIP
        #group=TKIP
        #psk="Go Chargers!"
        psk=6b478d4e5dd413b48e554afe74144e44823cf57bc183d19d7d410d0737c35fa1
        id_str="uah"
 }

 network={
        #default profile
        ssid=""
        key_mgmt=NONE
 }

 network={
        ssid="HomeTown"
        key_mgmt=NONE
        wep_key0=abbadabbafadda146906231978
 }

```

wpa_supplicant runs on startup and as soon as I run wpa_gui it has selected and connected to my home router.  So, the only issue is it's not running dhclient automatically.

---

### Post by Falkon MX-5 on 2007-02-19
HAH!  Got it working.  I just added auto eth1 to /etc/network/interfaces and id_str="home" to /etc/wpa_supplicant/wpa_supplicant.conf

Thanks anyway.  I should write this up, because it's a hell of a lot easier than some crazy automatic selector script.

All I know is that when I did a reboot it came up, connected, and got ip automatically.  I haven't tried this on the school network yet or at a wifi enabled coffee shop, so we'll have to see.

wifi-radar is useless.  it won't let me change settings at all
wireless-assistant works, but always just reports that connection fails with nothing meaningful.
wavemon is the jam for scanning, but that's about it.  Now, to learn how to use aircrack.

---

### Post by whayong on 2007-03-02
I'm interested in learning more about this.  I need to have mine set up in an almost similar fashion.  WPA at home, WEP (static) at work, Open for hotspots.  Did you write a how to yet?

---

### Post by Jim Darrough on 2007-03-16
I just added another interface in my /etc/network/interfaces file  so that I can connect to the public network at the school (my MAC address is in it's tables so no log-on id needed they tell me). I already access the WEP wireless in my office, and my home network as well (also MAC restricted).

Do I need to do something else besides just editing interfaces, or will it become in effect once I reboot?

Here is a snippet of the /etc/network/interfaces file. The addition is eth3...

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ki7ay

auto eth2
iface eth2 inet dhcp
wireless-essid osurc
wireless-key xxxxxxxxxxx

[I]auto eth3
iface eth3 inet dhcp
wireless-essid osu_pub[/I]
[COLOR="Red"]
I ADDED the above with a text editor[/COLOR]

[I]auto ath0
iface ath0 inet dhcp
[/I]
[COLOR="Red"]What is ath0???[/COLOR]



Great work, guys. I am learning a lot.

Regards, Jim in Springfield, OR

---

