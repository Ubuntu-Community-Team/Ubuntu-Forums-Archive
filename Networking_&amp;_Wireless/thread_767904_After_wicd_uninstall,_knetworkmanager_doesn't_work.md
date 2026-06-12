---
title: "After wicd uninstall, knetworkmanager doesn't work"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by tessmonsta on 2008-04-26
Recently I was on a business trip and experienced problems with knetworkmanager -- it wouldn't connect to the network. On suggestion from other forum threads, I installed wicd, and managed to get online after some haggling with the system.

There seems to be a conflict between the KDE Control Center and wicd, which causes the latter not to configure anything with success, even a hardline. 

Now that I'm back home, I want to switch back to knetworkmanager but when I did -- it didn't work! It didn't detect any network devices at all, not hardline not wireless.

I'd really like to go back to the seamless integration knetworkmanager had, how can I fix this?

---

### Post by Unix_Slayer on 2008-05-04
Good question...... anyone have an answer?

---

### Post by Unix_Slayer on 2008-05-04
Do the following in terminal......

```
sudo apt-get knetworkmanager --help
```

add the command update upgrade or install
Should correct.

---

