---
title: "WPA-PSK atheros/linksys router help?"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by synaptyx on 2006-11-18
Hi folks,

I've been bashing my brains out all morning trying to get my wireless network set up with WPA-PSK TKIP. I have an atheros card that works fine when I disable encryption on the router and have tried various tutorials on enabling WPA-PSK to no avail. I'm posting through the wired connection for the moment. :-? 

Interfaces:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto ath0
iface ath0 inet dhcp
	network 192.168.1.0
	broadcast 192.168.1.255
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid router
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

iface eth0 inet dhcp
```

wpa_supplicant.conf:```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=1

network={
       ssid="router"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk=<BLAHBLAHBLAH>
}
```

Output of the command - wpa_supplicant -dd -K -t -i ath0 -D madwifi -c /etc/wpa_supplicant.conf:```
Nov 18 13:37:10.331829: Initializing interface 'ath0' conf '/etc/wpa_supplicant.conf' driver 'madwifi' ctrl_interface 'N/A'
Nov 18 13:37:10.336463: Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Nov 18 13:37:10.336807: Reading configuration file '/etc/wpa_supplicant.conf'
Nov 18 13:37:10.337096: ctrl_interface='/var/run/wpa_supplicant'
Nov 18 13:37:10.337172: Line: 4 - start of a new network block
Nov 18 13:37:10.337247: ssid - hexdump_ascii(len=6):
     72 6f 75 74 65 72                                 router
Nov 18 13:37:10.337374: scan_ssid=1 (0x1)
Nov 18 13:37:10.337446: proto: 0x3
Nov 18 13:37:10.337493: key_mgmt: 0x2
Nov 18 13:37:10.337543: pairwise: 0x18
Nov 18 13:37:10.337589: group: 0x18
Nov 18 13:37:10.337636: PSK - hexdump(len=32): 76 c9 94 a8 ad 54 15 a6 6c 66 b4 31 c5 58 52 21 90 1b b6 fa 79 e2 a2 f3 28 24 c4 2e 3c 39 9b ce
Nov 18 13:37:10.337786: Priority group 0
Nov 18 13:37:10.337862:    id=0 ssid='router'
Nov 18 13:37:10.337923: Initializing interface (2) 'ath0'
Nov 18 13:37:10.428161: EAPOL: SUPP_PAE entering state DISCONNECTED
Nov 18 13:37:10.428578: EAPOL: KEY_RX entering state NO_KEY_RECEIVE
Nov 18 13:37:10.429100: EAPOL: SUPP_BE entering state INITIALIZE
Nov 18 13:37:10.429312: EAP: EAP entering state DISABLED
Nov 18 13:37:10.429560: EAPOL: External notification - portEnabled=0
Nov 18 13:37:10.429791: EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not permitted
ioctl[SIOCSIWMODE]: Operation not permitted
Could not configure driver to use managed mode
SIOCSIFFLAGS: Permission denied
Could not set interface 'ath0' UP
Nov 18 13:37:10.452761: SIOCGIWRANGE: WE(compiled)=19 WE(source)=13 enc_capa=0xfNov 18 13:37:10.453023:   capabilities: key_mgmt 0xf enc 0xf
ioctl[IEEE80211_IOCTL_SETPARAM]: Operation not permitted
Nov 18 13:37:10.453746: wpa_driver_madwifi_init: failed to set wpa_supplicant-based roaming
ioctl[SIOCSIWAP]: Operation not permitted
SIOCSIFFLAGS: Permission denied
Failed to initialize driver interface
Nov 18 13:37:10.570509: Failed to add interface ath0
Nov 18 13:37:10.571521: Cancelling scan request
```


I don't know what I have done, haven't done and what I need to do. It's all horribly confusing.

I am a command line n00b, so go easy on me. ;)

---

### Post by synaptyx on 2006-11-18
Noticed that this:```
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```Should have been this:```
pre-up wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```But now getting the error in wpa_gui> ASSOCIATING REQUEST TO THE DRIVER FAILEDHmmm, a little further, but no cigar... yet...

Help?

---

### Post by synaptyx on 2006-11-19
Nobody? I haven't gotten any further with this. Maybe weekends are not the best time for wireless network failures. :lol:

---

### Post by Rob2687 on 2006-11-19
I suddenly started having this problem last week. Played with the drivers all day yesterday until I realized Edgys WPA Supplicant is fubar. So I installed the version from Dapper and all is well now.

Anyways...your interfaces file should be like this
pre-up wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf

Did you use sudo when you pasted that output of wpa_supplicant that time?

---

### Post by synaptyx on 2006-11-19
Oops. I think I looked at it too long to spot a silly mistake like that.

Now posting wirelessly. :D :D :D

Thanks for the gentle slap in the head Rob, I needed that. ;)

---

