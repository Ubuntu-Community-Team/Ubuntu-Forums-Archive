---
title: "Kubuntu will not automatically connect to the wireless lan"
date: 2007-11-23
forum: Networking &amp; Wireless
---

### Post by thefirstM on 2007-11-23
Hello.  I have a problem with Kubuntu 7.10 on my PC where it will not connect to the wireless lan automatically when booted.  It will connect, but I must tell it to connect each time I boot up.  This is getting kind of annoying.  Can anyone help me?

---

### Post by Digger78 on 2007-11-23
you need to edit **/etc/network/interfaces**

```
kdesu kate /etc/network/interfaces
```

add your interface name

i.e. **auto wlan1**

iwconfig will show you the correct name.

---

### Post by thefirstM on 2007-11-23
I tried adding "auto ath0" to the file, but still nothing.

---

