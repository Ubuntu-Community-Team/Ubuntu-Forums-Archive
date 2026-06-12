---
title: "Does it work: Asus EEE 901/1000 Ubuntu &amp; WPA2"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by gaussian on 2008-10-22
I am trying to figure out one thing before putting my money on the line for a netbook (Apologies if this belongs to Laptop and not in Wireless forum). I would like to get a Asus EEE 901 or 1000 and put Ubuntu on it. I know about array.org kernel and/or need to compile drivers. That does not scare me, been there done that (I have a PPC Ubuntu running, so I have had my share of hackish solution).

I have been googling for an hour now and would just like to get a confirmation on one thing: Does anyone have enterprise level WPA (WPA2) working with these things without a hitch? 

This is an absolute dealbreaker for me, since I work for a University and if I cannot connect wireless the thing will be almost totally useless for me. Example of wpa-supplicant settings required for the network here:

```

network={
        ssid="XXXXX"
        proto=RSN
        key_mgmt=WPA-EAP
        pairwise=TKIP
        eap=PEAP
        identity="XXXX"
        password="XXXX"
        phase2="auth=MSCHAPV2"
}

```

Note that we don't require certificates here. Thanks for any info.

---

### Post by surfed on 2008-10-22
wpa2 personal works for me on the 1000

---

### Post by gaussian on 2008-10-22
> **surfed said:**
> wpa2 personal works for me on the 1000

Thanks. I found also some encouraging comments from EEE-Users forum. I think I am going to do the jump.

---

