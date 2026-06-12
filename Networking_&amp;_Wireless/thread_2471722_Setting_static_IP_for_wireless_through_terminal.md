---
title: "Setting static IP for wireless through terminal"
date: 2022-02-07
forum: Networking &amp; Wireless
---

### Post by camaban on 2022-02-07
I've tried scouring the internet for an answer and can't find it.

Does anyone know how to set a static wifi address through terminal? 
I've navigated to [HTML]sudo nano /etc/netplan/00-installer-config-wifi.yaml[/HTML] 

...and have this: 

[HTML]network:  version: 2  wifis:    wlp1s0:      access-points:        (Network name):          password: *****      dhcp4: true[/HTML]
I'm fairly certain I need to set dhcp4 to false, and think I need to enter the static IP in wlp1s0, but am not brave enough to commit to it.
If I wanted to, say set a static IP to 192.168.1.100, how would I need to enter the code?

Are there any other changes that I would need to make elsewhere as well?

---

### Post by chili555 on 2022-02-07
Conveniently, you have the correct template right on your computer!!

Please check:

```
cat /usr/share/doc/netplan/examples/static.yaml

cat /usr/share/doc/netplan/examples/wireless.yaml
```Please note that netplan is very specific about spacing, identation, etc., so please proffread carefully twice. Follow with:

```
sudo netplan generate
sudo netplan apply
```

---

### Post by camaban on 2022-02-08
Great, done and seems to be working. Thanks Chili.

---

