---
title: "[SOLVED] need help connecting to wireless"
date: 2008-11-16
forum: Networking &amp; Wireless
---

### Post by malfist on 2008-11-16
Okay, this is what I know about the wireless network:
```

hidded essid:    eku_secure
Auth:            WPA Enterprise
Data Encryption: AES
EAP Type:        PEAP
Server:          ekuwifi.eku.edu
Cert:            Equifax Secure Certificate Authority
Authentication:  EAP-MSCHAP v2
Username:        known, not tellin
Password:        known, not tellin

```

For some reason I can't get the network-manager to accept this. I don't even see the option for AES. And it complains when I try to connect that it requires a username and password when I have given it one that I know works.

Can someone tell me how to do this manually? Or how to get network manager to accept it?

---

### Post by malfist on 2008-11-16
Anybody?

---

### Post by Xikkub on 2008-11-17
You can't expect to get an answer in less than 8 hours.
BTW: I am having the same problem. I have no clue how to fix it.

---

### Post by malfist on 2008-11-18
Solved. Anoynomous identity was set to my username and I was able to connect.

---

### Post by malfist on 2008-11-18
Update: WRONG! Network manager always returns, needs encryption keys when it cannot connect. The case here was that the signal wasn't good enough. Anoynomous identity had nothing to do with it. I will file a bug report. What package should I name?

---

