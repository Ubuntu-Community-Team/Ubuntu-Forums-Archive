---
title: "My Intel PRO/Wireless 4965 AG is supported, but can't get it to show up (have driver)"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by rickcr on 2008-04-10
I'm confused. Do I need to use ndiswrapper or not to get my Intel PRO/Wireless 4965 AG wireless device to work? It's supposedly now supported (running Hardy Heron), and "lsmod | grep iwl" shows iwl4965 and iwlwifi_mac8021. The thing is that I do not see a way to configure wireless at all. If I go to System > Administration > Network, there is no "Wireless Connection" listed there. 

I've been googling and reading forum posts, but I'm not finding what I'm doing wrong. I suppose I could try the ndsiwrapper solution, but according to everything I'm reading this wireless device is supported (it's a compact 6910p notebook.)

Thanks for any help. I've wasted so much time with this already.

---

### Post by exactopposite on 2008-05-04
I just bought an intel 4965 card and installed it in my laptop to replace a broadcom card. I put it in, booted up and it was automaticaly recognized. I didn't have to do anything to get it working. It's working a lot slower than it should, but it was recognized with no problem.

---

### Post by TheCarNinja on 2008-05-06
If this is still an issue please post the output from the following:
- dmesg
- iwconfig

Can you also make sure that if there is a radio on button that is in fact in the on position? (I doubt its that from what you said already but hey, you never know.)

---

