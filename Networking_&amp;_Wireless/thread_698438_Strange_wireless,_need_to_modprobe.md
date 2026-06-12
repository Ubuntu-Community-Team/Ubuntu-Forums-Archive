---
title: "Strange wireless, need to modprobe"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by Aslund on 2008-02-16
Heya all

I have a strange problem with my wireless, original it used to be enable/Udisable without probs with my contact at the side of my notebook (Dell M65), but lately it have stopped working well, every time I need to access the wireless network, either at home or university I need to do:
"sudo modprobe ipw3945" 
and restart my PC to make my Ubuntu catche the wireless so I can log on.

Does anyone know what I can to avoid using this solution and get an more stable solution that just works :D

regards

Sebastian Aslund

---

### Post by tangibleorange on 2008-02-16
If that is the kernel module that you need to load at bootup, simply add it to your /etc/modules file like this:

```
echo 'ipw3945' | sudo tee -a /etc/modules
```

Then it should load everytime at bootup!

---

### Post by Aslund on 2008-02-16
think I expressed myself bad, I have no problem to log on the network when I boot my PC, aslong it is on, if I boot my PC iwth the wireless off and try to activate it, it will not catch the wireless.

---

