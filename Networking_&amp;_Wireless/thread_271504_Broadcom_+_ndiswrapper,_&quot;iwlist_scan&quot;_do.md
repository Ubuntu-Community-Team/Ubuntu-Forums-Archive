---
title: "Broadcom + ndiswrapper, &quot;iwlist scan&quot; does not work"
date: 2006-10-04
forum: Networking &amp; Wireless
---

### Post by enigma_0Z on 2006-10-04
Has anyone else had iwlist AP scanning/detection problems with broadcom cards+ndiswrapper, using either wpa_supplicant or iwlist to scan for Access Points?

I've got an HP dv6000z, for reference.

[edit]

FIXED!!!!!!!!!!!!! hahahahahaha, i'm soooo happy!!

[quote="/usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf"]
# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode; do not try to associate with
#    APs (i.e., external program needs to control association). This mode must
#    also be used when using wired Ethernet drivers.
# 2: like 0, but associate with APs using security policy and SSID (but not
#    BSSID); this can be used, e.g., with ndiswrapper and NDIS drivers to
#    enable operation with hidden SSIDs and optimized roaming; in this mode,
#    the network blocks in the configuration file are tried one by one until
#    the driver reports successful association; each network block should have
#    explicit security policy (i.e., only one option in the lists) for
#    key_mgmt, pairwise, group, proto variables[/quote]

My ap_scan was set to 1, which does not work with ndiswrapper and hidden SSID's, optimized roaming, etc...

LinuxANT sucks anyways. Set it to 2 and everything is peachy!
[/edit]

---

### Post by wieman01 on 2006-10-04
What the command you have used? 
> iwlist **wlan0** scan

---

### Post by enigma_0Z on 2006-10-04
My command & output was was:

```

# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results.

sit0      Interface doesn't support scanning.

```

It should also be noted that the AP does not broadcast it's SSID (it still sends out beacons though)

---

### Post by wieman01 on 2006-10-04
Try this instead:
> iwlist wlan0 scan
If there is no output, I am afraid your deployment of "ndiswrapper" & wireless driver has failed... What's the ouput of:
> ifconfig
> iwconfig

---

### Post by enigma_0Z on 2006-10-05
Actually, I tried specifying wlan0 on the command line as well, it came up with no search results. However, I have a wifi network at home that I can access just fine (wlan0 scan and just scan both work).

It works sometimes, just not all of the time. In this case, several scans didn't work, then with a little prodding it did. Could this still be an indication of improper ndiswrapper installation? (do I need to run ndiswrapper -i every time I install a new kernel?)

iw and ifconfig both indicate that the device exists and has wireless extensions.

I am fairly sure that the card is *working*, However, in the /etc/ndiswrapper/bcmwl5/*.conf files, are there options that I should enable? (radio, etc?)

---

### Post by wieman01 on 2006-10-05
And you don't have a firewall (e.g. Firestarter) by chance? My favorite question, but very effective sometimes.

---

### Post by enigma_0Z on 2006-10-05
no. personally, I hate personal firewalls... If I did have one, it'd be a custom iptables setup.

---

### Post by wieman01 on 2006-10-05
It's unlikely that "ndiswrapper" is the culprit. Usually it either works or it doesn't work at all.

Do router & PC run on the same wireless network bandwidth (e.g. 54 MBit - G, 11 MBit - B)? They should be in sync, otherwise your network will be unstable.

---

### Post by enigma_0Z on 2006-10-05
Well, it's a b/g card, and the network I know is g,

I can scan for the network just fine in Windows... odd, eh?

---

### Post by wieman01 on 2006-10-05
> **enigma_0Z said:**
> Well, it's a b/g card, and the network I know is g,

I can scan for the network just fine in Windows... odd, eh?
It's odd & I am running out of ideas here... :-(

---

### Post by enigma_0Z on 2006-10-06
Yeah, I really think that ndiswrapper just doesn't like my card... as it is, I'm using the dell driver for my hp laptop because the HP driver doesn't work in ndiswrapper.

I'm gonna try linuxant and see if I have any luck.

---

