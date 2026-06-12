---
title: "WPA2 encryption question"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-03-04
Hi,

Kubuntu Edgy


I've recently enabled WPA2 encryption on a Belkin F5D7000 v5 (atheros) PCI card....by the way of WPA supplicant, NDIS 1.8 & the Windows driver.  All works like a charm, kind of!!!



The only problem is....I need to "manually" restart the wireless network, via Konsole, to enable the WPA2 connection, after booting the PC.:( 

If I run an open/unencrypted network, the PC will boot perfectly with the automatic internet connection at startup.


Any ideas?
Thanks

---

### Post by spd106 on 2007-03-04
Use **sudo iwconfig** to see if you have associated with the AP and have negotiated a key. 

Then check **ifconfig** for an IP address.

Last week I had a lot of trouble with dhclient timing out too quickly. I found that using the scan_ssid=1 option wpasupplicant would associate quicker allowing dhclient to grab an address before it timed out.

---

### Post by DapperMe17 on 2007-03-04
Thanks for your reply.


I do show the key, as well as my router address....of course after I have restarted the network manually.

I do not show the key, or address, just after booting.


There must be a line I'm missing in the network/interfaces file?

Can you tell me more about configuration concerning wpasupplicant...?

---

### Post by spd106 on 2007-03-04
Here's my wpa_supplicant.conf```
$ cat /etc/wpa_supplicant/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="<removed>"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=<removed>
}

```

and in the interfaces file we have```
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

```

I'm using a bcm4306 rev 03 with ndiswrapper 1.37 and driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0).

After reading through the hostap web site about wpasupplicant I thought it would be better to remove the scan_ssid=1 line. I was wrong, so I put it back and haven't had trouble maintaining a connection since.

---

### Post by DapperMe17 on 2007-03-04
I can't seen to locate my wpa_supplicant config file....it appears empty.


I'm running an Belkin (Atheros) PCI using NDIS & the Windows driver, to achieve WPA2.
My network/interfaces file follows the WPA HOW TO by Wieman, to a "T".


Where would I be editing the info which you offered?


Sorry, somewhat a noobie here.

Thanks




UPDATE!!!!   All figured out...simple addition of 'pre-up sleep 10' did the trick.

---

### Post by wieman01 on 2007-03-05
This is a bug I am afraid. This is mentioned in post #2 of [this thread]("http://ubuntuforums.org/showthread.php?t=202834"). You need to restart your network during boot in order for the connection to work. A number of other users have confirmed this problem. Sad but true.

---

