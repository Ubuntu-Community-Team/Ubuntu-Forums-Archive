---
title: "boradcom half working"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by k0zy on 2007-01-03
Heya guys.

I finally got my broadcom wifi card working.
It works perfect with my home network, which I configured via the NetworkManager applet.

However I'm having problems connecting to the network at university.

THe university wiki tells me to create a config like this:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="FBI-WLAN1"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-EAP
        pairwise=TKIP
        group=TKIP
        eap=TTLS
        anonymous_identity="anonymous"
        identity="<login>"
        password="<password>"
        ca_cert="/etc/wpa_supplicant/certs/FB06_RootCA-cacert.pem"
        phase2="auth=PAP"
}
```
(FBI is german for "Fachbereich Informatik" btw.)

I tried using the NetworkManager Aplett again but it won't work.
First question: Why? Is the Networkmanager Applet not able to work with this configuration?
Seems like I can entereverthing in Networkmanager except the "phase2".

So, for now I tried setting up the wpa_supplicant manually.
I tried to start it this way:
```
sudo wpa_supplicant -D broadcom -i eth0 -c /path/to/config/I/can't/remeber
```
and it tells me:
```
Unsupported driver 'broadcom'.
``` while the man page lists the broadcom driver!

I somehow got it working using the wext diver, but sometimes "Unsupported Operations" occour and even worse the connection is dropped or times out all the time.

The fact that I can't connect to the WiFi at university is the only thing that keeps me from dropping Windows.

I hope you guys can help me.
Thanks in advance!

k0zy

---

