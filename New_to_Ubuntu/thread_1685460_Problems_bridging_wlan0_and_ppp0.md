---
title: "Problems bridging wlan0 and ppp0"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by Eric.B on 2011-02-10
[SIZE=3]I'm trying to create an AP that is bridged to a GSM USB card on ppp0 (10.2.112.188 ).

I have configured my wlan0 as an AP at 192.168.3.0.  The dhcp3-server is passing out IPs to clients correctly, however I am unable to bridge the connection.  And hostapd generates a "deauthenticated due to local deauth request" and drops the connection.

In the dhcp.conf I tried to point to my ppp0 port with this "option routers" as suggested elsewhere.
[PHP]subnet 192.168.3.0 netmask 255.255.255.0 {
range 192.168.3.10 192.168.3.49;
option routers 10.2.112.188;
option ip-forwarding off;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.3.255;
}[/PHP]I've also tried using the wireless-tools to make a bridge with the ppp0 and wlan0 but apparently ppp0 won't work:
[PHP]sudo brctl addif br0 ppp0
can't add ppp0 to bridge br0: Invalid argument
[/PHP]Also I tried adding the bridge command inside the hostpad.conf file
[PHP]interface=wlan0
driver=nl80211
bridge=ppp0
ssid=TEST
channel=2
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=testtest
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP[/PHP]I'm pretty stuck on this.  Does anyone know the magic or see what I'm doing wrong?  Obviously I'm just taking stabs in the dark here....
[/SIZE]

---

### Post by Eric.B on 2011-02-13
[SIZE=3]Turns out the dropping due to [/SIZE][SIZE=3]"deauthenticated due to local deauth request" was due to the WPA setup.  I just opened the connection (removed the WPA config lines) and that problem went away.

I finally found a way to bridge the ppp0 and wlan0 using a firewall (FIRESTARTER) that setup the IPTABLES for me.  So now it is working.
[/SIZE]

---

### Post by Eric.B on 2011-02-16
See[ this tutorial in progress ]("http://ubuntuforums.org/showthread.php?t=1688432")for more info.

---

