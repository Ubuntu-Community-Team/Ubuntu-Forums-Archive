---
title: "MSChapV2 PEAP WIFI Authentication with Linux (command line or gui - no support?)"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by blak on 2008-09-24
I am using Ubuntu 8.04 Hardy Heron, on an eeepc 1000h

I have tried network-manager, wpa_supplicant, wicd, the list goes on. I have scoured the WWW, local ITS dept., IRC help channels for any help on this matter. No luck with anything so far.

I cannot find out how to get Linux via command line or via gui to work with a WPA MSchapV2 PEAP wifi network at my university and it seems no one else can either. Either Linux just doesnt feel the need to support "MS"chapV2 (which it really shouldn't possibly since this is "MS" technology..) or there is a way still out there to make this work. Any help would be greatly appreciated, as I'm not done with figuring this out, I'm not giving up!

Here is a direct link to my university's wifi configuration site for everything, but Linux(not supported supposedly): [https://nautical.uwf.edu/utility/serviceinfo/?serviceid=5666](https://nautical.uwf.edu/utility/serviceinfo/?serviceid=5666)  (Click on the "Setting Up ArgoAir" link) (notice the trusted sites, and the certificate handling parts...., this is the main problem)

Thanks,
blak

---

### Post by willca on 2008-09-25
Try this out. 

[http://linux.die.net/man/5/wpa_supplicant.conf](http://linux.die.net/man/5/wpa_supplicant.conf)

---

### Post by blak on 2008-09-25
ca_cert="/etc/cert/ca.pem"

This seems to be handled on WinXP, MacOS X, etc. automatically, gettings this .pem or cert.... that my school provides. I can't just point to some random ca.pem I don't believe? Somehow I need linux to know to say hey I'm looking to receive my schools certs and nowhere on that page does it have any code that says it will do that, and I know wpa_supplicant doesn't seem to support such things? Is this a MS thing only? Is my schools wifi setup to never work with Linux do you think?

-blak

---

### Post by willca on 2008-10-08
Forget about the cert.pem in that example. It seems your IT folks dont want you to validate that then its not needed.

I would just try this out. 

Catch all example that allows more or less all configuration modes. The configuration options are used based on what security policy is used in the selected SSID. This is mostly for testing and is not recommended for normal use.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
network={

    ssid="example"

    scan_ssid=1

    key_mgmt=WPA-EAP WPA-PSK IEEE8021X NONE

    pairwise=CCMP TKIP

    group=CCMP TKIP WEP104 WEP40

    psk="very secret passphrase"

    eap=TTLS PEAP TLS

    identity="user@example.com"

    password="foobar"

   }

---

### Post by CodeAlias on 2008-11-09
Hi ,

Check this out :
[Wireless security (WPA/WAP2) with EAP-PEAP using wpa_supplicant and client SSL certificates Linux setup]("http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-peap_using_wpa_supplicant_and_client_ssl_certificates_linux_setup")

Hope it helps.

---

### Post by psanders on 2009-03-04
blak-
It figures that I would find a fellow UWF student when I did a search to try to figure this problem out. Haha.

I (unsuccessfully) tried to get the wireless to connect on my neighbor's Dell netbook with Ubuntu last semester. He ended up just giving Dell a call and working out a deal to get XP on the machine instead. I haven't worried that much about it since then, until now. I'm craving some Ubuntu, but I don't want to install it only to find that I won't be able to connect to the network.

I would usually not have a problem without wireless, but at the same time I would usually have access to an ethernet hookup. Unfortunately my residence hall is strictly wireless.

CodeAlias: If I end up trying out Ubuntu, I will use that guide to try to get it working and post back with my results. Thanks for the link. :)

---

