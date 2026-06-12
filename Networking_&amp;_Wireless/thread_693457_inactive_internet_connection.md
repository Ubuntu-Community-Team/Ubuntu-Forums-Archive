---
title: "inactive internet connection"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by naveedahmed on 2008-02-11
i have  installed ubuntu on my system. later i installed suse 10.3.

when i boot into my ubuntu the internet connection does not work. repeated attempts of activating are useless.
so by booting  into suse 10.3 i will have to manually activate the connection which is inactive there sometimes.. then rebooting into ubuntu is making it active. provide me a solution for this please.

---

### Post by jan quark on 2008-02-11
I don't really think there is a connection between two separate OS that can influence your network device

please post the output of the following terminal commands

```
lspci
```
```

sudo lshw -C network
```

```
sudo iwlist scan
```
```

iwconfig
```

```
ifconfig
```

---

### Post by naveedahmed on 2008-02-11
[attach]59344[/attach]

---

