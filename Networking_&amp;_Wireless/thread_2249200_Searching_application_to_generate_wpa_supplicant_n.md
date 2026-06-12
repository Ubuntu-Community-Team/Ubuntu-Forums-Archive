---
title: "Searching application to generate wpa_supplicant network tag from wifi networks"
date: 2014-10-20
forum: Networking &amp; Wireless
---

### Post by rob104 on 2014-10-20
Hi everyone, after some searching on google i can't seem to find any solution to my problem. I'm switching multiple devices over multiple locations with WiFi connection and to make my job easier i would need an app that will scan down networks in range and generate wpa_supplicant network tags that i can just c/p and enter password. Is there such app?

So i would need this app to generate something like this for every network, depending on network ofc

```

network={
    ssid="example"
    scan_ssid=1
    key_mgmt=WPA-EAP
    eap=PEAP
    identity="user@example.com"
    password="foobar"
    ca_cert="/etc/cert/ca.pem"
    phase1="peaplabel=0"
    phase2="auth=MSCHAPV2"
}

```

---

### Post by TheFu on 2014-10-20
If it is on the same machine, just use **wicd-curses**. Almost as quick - ah - EAP?  I dunno if that makes it harder or easier.

It does store connection data inside /etc/wicd/wireless-settings.conf, so perhaps you can speed it up?

---

### Post by rob104 on 2014-10-21
Thx for reply, this might speed things up a bit. I might end up doing it but i would really like an application that can generate it on the fly to save time. Just doing it manually 50 times a day is really exhausting and pointless. Does anyone have any other suggestions?

---

### Post by TheFu on 2014-10-21
The intent was you'd use the GUI to setup one stanza, then clone that with whatever number of mirrored connection using an editor, changing the SSID as needed directly inside the text file. Sorry if that wasn't clear.

A few years ago, I designed a wifi deployment for 1200+ locations ... btw.

---

### Post by slickymaster on 2014-10-21
*Moved to the ***Networking & Wireless*** sub-forum*

---

