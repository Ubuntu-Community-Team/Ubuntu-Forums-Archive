---
title: "Wired not working CLEVO RTL8111/8168/8411 Ubuntu 18.04"
date: 2019-02-27
forum: Networking &amp; Wireless
---

### Post by JoniJnm on 2019-02-27
Hi,

My wireless is working well but my wired not. It did work and suddenly (i don't know why) it stopped to work. Ubuntu says:

Activation of network connection failed.

The pastebin file: [https://pastebin.com/am0GV3AP](https://pastebin.com/am0GV3AP)

Thanks!

---

### Post by praseodym on 2019-02-27
Please show the output of
```

lsmod
```

---

### Post by JoniJnm on 2019-02-27
[https://pastebin.com/FSR1Uh5M](https://pastebin.com/FSR1Uh5M)

---

### Post by praseodym on 2019-02-27
Hm, did you configure the firewall? Do you need it? If no, run

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```
Reboot

---

### Post by JoniJnm on 2019-02-27
Done!

But it still doesn't work :(

The new lsmod output:

[https://pastebin.com/CFMfQttG](https://pastebin.com/CFMfQttG)

---

### Post by praseodym on 2019-03-03
Did you reboot? Can you show it again?

---

