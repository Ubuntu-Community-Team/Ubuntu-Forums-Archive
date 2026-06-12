---
title: "Connecting to university WPA-Enterprise network"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by squirrelplayingtag on 2007-05-07
The university provides a howto for connecting to their secure wireless network in windows and OSX and also provides the generic parameters on their website ([http://www.oit.umd.edu/nts/noc/wireless/connect.html)](http://www.oit.umd.edu/nts/noc/wireless/connect.html)), but I can not manage to connect using knetworkmanager. I started to try and set my wpa_supplicant.conf by following [http://ubuntuforums.org/showthread.php?t=249654&highlight=WPA+enterprise](http://ubuntuforums.org/showthread.php?t=249654&highlight=WPA+enterprise) but I could not figure out what to set everything as from just following my universities generic parameters. Ideally I would like to be able to set knetworkmanager to connect correctly to the network without having to issue any commands before connecting.

---

### Post by Depressed Man on 2007-09-23
I'm trying to connect to umd-secure too. Here's what I found.

[http://www.mail-archive.com/um-linux@listserv.umd.edu/msg01382.html](http://www.mail-archive.com/um-linux@listserv.umd.edu/msg01382.html)

```
network={
        disabled=0        # change to 1 to disable
        mode=0            # infrastructure mode
        ssid="umd-secure"
        scan_ssid=1       # scan for hidden a.p.s
        key_mgmt=WPA-EAP
        proto=WPA2
        pairwise=CCMP TKIP
        group=CCMP TKIP
        eap=TTLS
        identity="UMDusername"
        password="umdpasssword"
        anonymous_identity="anonymous"
        ca_cert="/etc/thawte_server_roots/ThawtePremiumServerCA.cer"
        subject_match="wireless.umd.edu"
        phase2="auth=PAP"
```

Dunno where to download the certificate though.

---

### Post by kepreon on 2007-11-04
The certs can be found at [http://www.thawte.com/roots/](http://www.thawte.com/roots/).  I also was able to connect automagically using NetworkManager in Ubuntu Gutsy.  Just use the relevant parameters from the wpa_supplicant.conf file and it connected for me :-)  I assume Kubuntu would work similarly.  I tried doing it using the way described in the UMLUG group but had to manually start the DHCP client in order for it to take an address -- watch out for this if you're trying it that way.

---

### Post by squirrelplayingtag on 2007-12-15
I got this working under kubuntu following this and using these settings:
[http://zordon.student.umd.edu/~kevin/umd-secure.png](http://zordon.student.umd.edu/~kevin/umd-secure.png)

It took a couple times of entering them with kubuntu network manager but it eventually connected.

---

### Post by silentlun on 2008-02-26
I have been trying to connect using the settings, but the problem I have is that I don't know where to put in the part for wireless.umd.edu. My network manager doesn't have a space for it. I am also unable to see the linked picture with the settings, does anyone have a copy of it? or could they get a screen shot of how the network manager is supposed to look like? Thanks for the help in advance.

---

