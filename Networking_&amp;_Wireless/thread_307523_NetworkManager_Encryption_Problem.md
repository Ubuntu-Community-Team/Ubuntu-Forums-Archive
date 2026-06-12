---
title: "NetworkManager Encryption Problem"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by Falcon X on 2006-11-26
I've been struggling with this issue for a day or two now.  I've been combing the forum, but I haven't found a solution yet.

I have a Dell e1405 with a Dual Core (running 686 kernel) and an Intel 3945 PRO Wireless card.  I have networkManager working beautifully and the wpa-supplicant installed.  However, I cannot connect to an encrypted network whether it be WEP or WPA.  In addition, when I turn the SSID off, networkManager cannot connect.

I would appreciate any advice and/or help.

---

### Post by Jamie Jackson on 2006-11-26
I guess you probably already have done this, considering NM is working unencrypted, but... have you already commented out the wireless interface in /etc/network/interfaces ?

Jamie

---

### Post by Falcon X on 2006-11-26
Yup.  It works wonderfully for non-encrypted networks.

---

### Post by Jamie Jackson on 2006-11-30
I don't know if this helps, but I got mine (though it's a different card than yours) going with WPA, NetworkManager, and NDISWrapper. I modified [this wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#preview") to document what I did.

Thanks,
Jamie

---

