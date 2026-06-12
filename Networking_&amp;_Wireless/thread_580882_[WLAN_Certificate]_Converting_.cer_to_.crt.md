---
title: "[WLAN Certificate] Converting .cer to .crt"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by Nuker on 2007-10-19
Hello Ubuntu Users,

I've decided to install Ubuntu on my laptop and I had no problem isntalling is whatsoever. But there's one problem concerning networking. At school we use a certificate in .cer format. But I've been told to use this config:

> ---> /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
network={
        ssid="hanze"
        key_mgmt=IEEE8021X
        eap=TLS PEAP
        auth_alg=OPEN
        phase2="auth=MSCHAPV2"
        identity="<nummer>@hanze.nl"
        password="<wachtwoord>"
        ca_cert="/etc/1x/Hanze.crt"
}
<---

As you can see the certificate is in .crt format. How do I convert my .cer to .crt? I've been searching all over the internet and even our ICT helpdesk didn't knew how to do it. Thanks in advance.

//Brian 'Nuker'

---

### Post by Hero of Time on 2007-10-19
If they use SecureW2 at school, it should work just fine with the following wpa_supplicant.conf entry:
```
network={
	ssid="<school SSID>"
	key_mgmt=IEEE8021X
	eap=TTLS
	identity="<username>"
	password="<password>"
	phase2="auth=PAP"
}

```
No certificate needed. My school has the same kind of setup, they also use certificates, but only for Windows. Somehow, they aren't needed for Linux. See if this works.

---

