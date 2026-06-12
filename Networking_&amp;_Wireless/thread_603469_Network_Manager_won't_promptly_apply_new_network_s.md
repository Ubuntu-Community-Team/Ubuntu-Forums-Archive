---
title: "Network Manager won't promptly apply new network settings"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by macabro22 on 2007-11-05
When changing network locations in network manager, it does not apply the selected settings as it should unless I either log off and log in again or do```
sudo /etc/init.d/networking restart 
```

I think this might be a bug. So I'd like to know how to let developers know this is happening (e.g. how to file a bug wherever) or else, if it's not a bug, how can I diagnose what's wrong with my PC?

Thanks in advance

P.S.
I use my laptop at home with a dynamic ip address (dhcp) and at work with a static IP address and yes I am clicking the apply button.

---

### Post by ddrichardson on 2007-11-05
Look at launchpad, see if there's similar reports and if not then check what they need from you before posting a bug. [https://bugs.launchpad.net/network-manager](https://bugs.launchpad.net/network-manager)

---

