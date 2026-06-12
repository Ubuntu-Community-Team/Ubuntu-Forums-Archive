---
title: "DLink DWL 520+ only without WPA?"
date: 2005-07-10
forum: Networking &amp; Wireless
---

### Post by LinuxFan9 on 2005-07-10
Hi,
 
Kubuntu 5.04, Dlink 520+, wpa_supplicant installed with synaptic 
Wlan -> without WPA (and WEP) no problem at all
With WPA - > DWL 520+ and net are found (visible in KWiFi administration, but no access to AP, address of AP only 00:00:00...)
 
Why This?
 
 Sincerely,
 Thadeus.
 
 Existing files:
 1st:
 # /etc/default/wpasupplicant
 # WARNING! Make sure you have a configuration file!
 ENABLED=0
 # Useful flags:
 # -D <driver> Wireless Driver
 # -i <ifname> Interface (required, unless specified in config)
 # -c <config file> Configuration file
 # -d Debugging (-dd for more)
 # -w Wait for interface to come up
 OPTIONS="-w"
 
 2nd:
 # /etc/wpa_supplicant.conf
 ctrl_interface=/usr/sbin/wpa_supplicant
 ctrl_interface_group=0
 eapol_version=1
 ap_scan=1
 fast_reauth=1
 # Only WPA-PSK is used. Any valid cipher combination is accepted.
 network={
 ssid="a12345"
 proto=WPA
 key_mgmt=WPA-PSK
 pairwise=CCMP TKIP
 group=CCMP TKIP WEP104 WEP40
 psk="abc"
 priority=2
 }
 
 3rd:
 in /usr/sbin -> wpa_supplicant
                   -> wpa_cli
                   -> wpa_passphrase
 
 4th:
 # etc/network/interfaces
 auto lo
 iface lo inet loopback
 mapping hotplug
 script grep
 map eth0
 iface eth0 inet static
 address 192.168.0.153
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1
 dns-nameservers 192.168.0.1
 iface wlan0 inet static
 address 192.168.0.154
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 192.168.0.255
 gateway 192.168.0.1
 dns-nameservers 192.168.0.1
 wireless_mode managed
 wireless_essid a12345
 wireless_nick Wlan
 wireless_channel 6
 wireless_rate auto
 wireless_enc off
 
 5th:
 enter in the shell
 sudo ifdown eth0
 sudo wpa_supplicant -c/etc/wpa_supplicant.conf -B -iwlan0 -d -w
 sudo ifup wlan0

 Result: no connection to AP.

---

### Post by badDNA on 2005-07-10
I'm using the Dlink 520+ as well and trying to get the live version to see the card.  No such luck.  lspci does not see the card.  Is there any way for me to get the 520+ card working with the live version??????

---

### Post by funkydan2 on 2005-07-10
Does the DLink-520+ use the acx drivers?  (Running 'lsmod' should tell you that.)

If you're using the acx drivers that come with Ubuntu, you cannot use WEP or WPA - the driver simply doesn't support it.

You can however, upgrade the driver to get WEP support (but not WPA as yet).  There's a few good webpages with instructions on how to do it - I've put [some details of my experience with a 650+ on my blog](http://www.saunders.90megs.com/blog/index.php?entry=entry050705-073812).  My understanding is that the 650+ uses the acx111 chipset and your 520+ will use the acx100 chipset.  Both of these chipsets are supported by the acx drivers.

Daniel

---

