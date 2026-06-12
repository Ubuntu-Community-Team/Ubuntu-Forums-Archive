---
title: "WPA Supplicant Help"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by mraineri on 2006-11-26
I have been trying to set up WPA Supplicant for Xubuntu, but I am unable to connect to any wireless network. My card can see the network, but the authentication times out. I am able to get a connection using the basic Network GUI provided by Xubuntu, but my school uses WPA so I'd rather use WPA Supplicant.

The card I am using is a Linksys WPC11v4.
I have loaded the latest drivers from Linksys via ndiswrapper.
A link to a log of when I run wpa_supplicant can be found [here]("http://users.wpi.edu/~mraineri/wpa_supplicant_log.txt").
My wpa_supplicant.conf file contains the following:
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=1

network={
  ssid="linksys"
  scan_ssid=1
  priority=5
  key_mgmt=NONE
  wep_key0=7d8d346b34
  wep_tx_keyidx=0
}

Thanks!

---

### Post by roachk71 on 2006-11-26
Which Ubuntu version are you running?

I dual-boot between Dapper and Edgy, and have WPA working without using wpa_supplicant.conf (in /etc/network/interfaces).

Of course, I had to build NDISwrapper from source in both cases, which is easier than most think, and only takes a few minutes.

---

### Post by mraineri on 2006-11-26
I'm using Xubuntu 6.10 (Edgy).

---

### Post by mraineri on 2006-11-26
I found the problem. I changed from using ndiswrapper to wext as the driver. Works perfectly now.

---

### Post by nebbiauro on 2006-11-29
Hi...i got a problem with wpa supplicant.
I'm using a PCMCIA wireless card(Hamlet HNWP254)
I have a connection that uses a WPA-PSK encryption.
I follow every step in this post but I'm not yet able to connect.
when I digit iwconfig it recognize my ssid but it said access point not associated...
however here is mi iwconfig:
wlan0     IEEE 802.11g  ESSID:"AliceXXXXXXXXX"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 if you have any suggestion that would be useful pleas contact me..
thanks for helping...
Mauro

---

