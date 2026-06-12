---
title: "wpa_supplicant works, network-manager does not"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by pgilmon on 2007-05-09
Hi all,

I'm trying to connect to eduroam by using ubuntu 7.04. You can see instructions on how this should be done (in theory ;) ) [here]("http://www.eduroam.ro/?id=f9b2e&s=nature").

The previous method does not work for me, authentication just takes forever. However, by starting wpa_supplicant manually and asking for an ip address with dhclient, everything works.

This is the content of my wpa_supplicant.conf file for manual configuration:

```
ctrl_interface=/var/run/wpa_supplicant

     eapol_version=1
        ap_scan=1
        fast_reauth=1
        network={
                ssid="eduroam"
                scan_ssid=1
                key_mgmt=WPA-EAP
                proto=WPA
                eap=TTLS
                identity="XXXXXXX"       
                password="XXXXXXX"              
                priority=2
                phase2="auth=PAP"
                }
```

And this is the command I use to invoke wpa_supplicant:
```
sudo wpa_supplicant -i eth1 -Dwext -c /etc/wpa_supplicant.conf
```

After that, I get an IP address with:
```
sudo dhclient eth1
```

And I have connection.

What am I doing wrong? Isn't there anyway to tell network-manager to use that wpa_supplicant.conf file for that wireless network?

Thanks

---

### Post by pgilmon on 2007-05-15
Does anyone know if this is a bug in this version of NetworkManager or something?

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

### Post by kevdog on 2008-02-27
Network manager is to be revised in the Hardy final release.  For now I would suggest dumping Network Manager and go with WICD, or just continue connecting manually.

---

