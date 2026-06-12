---
title: "connecting with wpa_supplicant works, howto with network-manager?"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by Lieter on 2007-05-22
Hi, i finally got my wifi working at school (EAP-TTLS/Radius), but how do i put those things in network manager(cause it looks nicer :))

this is what my wpa-supplicant.conf looks:

```
eapol_version=1
fast_reauth=0
ap_scan=2

network={
        ssid="eduroam"
        key_mgmt=IEEE8021X
        eap=TTLS
        # Phase1 / outer authentication
        identity="XXXXX@YYY.ZZ"
        password="XYZXYZXYZ"
        # Phase 2 / inner authentication
        phase2="auth=PAP"
}
```

and i start my wpa_supplicant with this:
```
wpa_supplicant -Dwext -i eth1 -c /etc/wpa_supplicant.conf
```

and it works, but how can i get network-manager to use those settings?
thanks in advance, Lieter

PS at home i use network-manager cause that is only WPA and that works fine :)

---

### Post by handaxe on 2007-05-22
I do not think the current version of NM handles EAP, LEAP etc.  Is in v. 0.6.5, AFAIK.

You could in the interim try out WIcd as your wireless connection manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
 
 You can always re-install NM if you will, so nothing lost...
 
 Wicd has worked for many folks in dealing with issues apparent under NM and it handles a huge array of encryption types.

Please note that Wicd cannot help where there are fundamental problems between card/driver and "helper" progs like wpa_supplicant, iwlist etc.

HA

---

### Post by Lieter on 2007-05-22
ive tried wicd before, but it didnt work either (or i couldnt get set it up right) any way i'll give it another look

---

### Post by handaxe on 2007-05-22
Ah well.... falling between 2 stools then...

And WiFiRadar ?

HA

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

