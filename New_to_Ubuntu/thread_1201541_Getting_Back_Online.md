---
title: "Getting Back Online"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by daniell59 on 2009-07-01
I am using Ubuntu 9.04. Today I when I booted up, I was off my wireless network. I tried it in Vista, no problem. I would appreciate it if someone could tell me how to get back online.

Thanks

Daniel

---

### Post by nandemonai on 2009-07-01
If you've updated the kernel then you may need to reinstall the drivers for your card (if applicable).

Some more info would be helpful. Chipset? Did you need additional drivers after install? etc etc

---

### Post by Michael.Godawski on 2009-07-01
Input please:

```
sudo iwlist scan
sudo lshw -C network
iwconfig
ifconfig
cat /etc/network/interfaces
```

---

