---
title: "error in iwconfig"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by espanhol on 2005-10-30
Hi there

i am trying to configure my network and when i:
```
sudo iwconfig essid "SMC" mode Managed key s:blablabla
```

i get an error like this:

```
Error for wireless request "Set Encode" (8B2A) :
SET failed on device wlan0 ; Invalid argument
```

anyone can helpme out here?

---

### Post by [pl]ice on 2005-10-30
hey,maybe the syntax is wrong??
 try putting this to the /etc/network/interfaces file,

---

