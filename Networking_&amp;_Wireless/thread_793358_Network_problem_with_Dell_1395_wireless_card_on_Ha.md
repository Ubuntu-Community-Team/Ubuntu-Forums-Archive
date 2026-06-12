---
title: "Network problem with Dell 1395 wireless card on Hardy Heron"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by - 000 - on 2008-05-13
I don't know how to install a driver for my wireless adapter.  It is a Dell 1395 card.  Any help?

---

### Post by - 000 - on 2008-05-13
Anyone?

---

### Post by chili555 on 2008-05-13
Open up a terminal and do:```
sudo lshw -C network
```You may find this is a Broadcom 43xxx. Search for your specific model, 4311, 4308, 43whatever or check here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Post back if you get stuck.

---

### Post by - 000 - on 2008-05-13
Ok, ill try that

---

### Post by - 000 - on 2008-05-13
I did steps 1, 2e and 3, and it did absolutely nothing

It also tells me if module=ssb instead of module=ndiswrapper, then it is a problem I have to fix.  However, for me, module=sky2

---

### Post by chili555 on 2008-05-14
Oops! You want to put b43 in the blacklist command and then do the command again with ssb in it. When a command 'does absolutely nothing,' it's saying to you, 'OK, I executed that command and I have no errors, warnings or complaints to report. What's next?'

I believe sky2 is the module that your wired ethernet uses. Please don't touch that one!

---

### Post by - 000 - on 2008-05-14
Umm, how exactly do I blacklist?

---

### Post by - 000 - on 2008-05-14
Ok, I am at the blacklist, but at the bottom, all it says is:

blacklist bcm43xx

---

### Post by chili555 on 2008-05-15
Add to the blacklist file:```
blacklist b43
blacklist ssb
```Save and close.

---

### Post by - 000 - on 2008-05-16
Thanks.  It works now

---

