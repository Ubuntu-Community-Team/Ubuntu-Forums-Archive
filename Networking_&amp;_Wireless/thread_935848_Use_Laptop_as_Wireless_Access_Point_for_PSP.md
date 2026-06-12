---
title: "Use Laptop as Wireless Access Point for PSP"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by thedudething on 2008-10-02
Hi, I have a PSP and I heard you can use a laptop with wireless as an access point. How do you do this?

---

### Post by iponeverything on 2008-10-02
It's pretty strait forward of your wireless card supports master mode.

I use the madwifi for atheros based card and it works well

/etc/network/interfaces:

iface ath0 inet static
address 10.111.111.111
netmask 255.255.255.0
wireless-essid  KabulWabble
post-up /etc/tkip


/etc/tkip:

#!/bin/sh
iwconfig ath0 essid KabulWabble
iwpriv ath0 mode 3
ifconfig ath0 10.111.111.111 up
hostapd -B /etc/hostapd.conf

/etc/hostapd.conf:

interface=ath0
driver=madwifi
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
debug=0
dump_file=/tmp/hostapd.dump
ssid=KabulWabble
eapol_key_index_workaround=0
wpa=1
wpa_passphrase=Duck and Cover, Stay Away From the Windows
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP

---

### Post by thedudething on 2008-10-02
umm can u explain step by step? :P

---

