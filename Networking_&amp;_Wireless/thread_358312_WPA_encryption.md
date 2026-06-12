---
title: "WPA encryption"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by buncas on 2007-02-10
Hello all, most of the help postings I have read, all suggest using hex keys for the encryption, can ascii keys be used for the encryption in a wpa setup for Ubuntu?

thankx,
buncas

:(

---

### Post by starling on 2007-02-17
i've have been unable to get wpa to work with any combination of apps, tutorials and swearing. Until now.
to use ascii, open a terminal and type:
```

wpa_passphrase "your-ssid" "your-psk-string"

```

the hex string that comes out can be entered into the password box in network manager (set to hex) and everything is cool.

---

### Post by wieman01 on 2007-02-18
> **buncas said:**
> Hello all, most of the help postings I have read, all suggest using hex keys for the encryption, can ascii keys be used for the encryption in a wpa setup for Ubuntu?

thankx,
buncas

:(
I don't quite understand the question... But generally you can use ASCII keys for encryption, however, you convert them into hexadecimal when setting upt the client. They key itself remains ASCII although it does not appear so.

---

