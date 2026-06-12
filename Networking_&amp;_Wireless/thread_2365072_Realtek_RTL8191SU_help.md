---
title: "Realtek RTL8191SU help"
date: 2017-07-02
forum: Networking &amp; Wireless
---

### Post by riskymoodsisnottaken on 2017-07-02
Btw I'm duel booting windows7+ubuntu 

The problems I've been having 

- Slow internet on ubuntu 
- Asking for password 
- Can't connect to internet after I get disconnected

Im a noob at this as I just downloaded it

---

### Post by praseodym on 2017-07-02
Lets try

```
echo "options r8712u low_power=0 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
```
and reboot (this is one line, you better c/p it)

---

