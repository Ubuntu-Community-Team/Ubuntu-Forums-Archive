---
title: "No Wireless Controller"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by robertosante on 2015-08-19
hi guys im using a gigabyte b85-hd3 motherboard and just recently installed ubuntu, I noticed that there is no internet either wireless or cabled... the wireless button on networks says ethernet network and then shows disconnected..


so I went ahead and typed

```
lspci -nn
```

and I noticed that there werent any network controller in the list... it only showed

Ethernet COntroller [0200]: realtek semi conductor co., ltd. rtl811/8168/8411 pci express gigabit ethernet controller [10ec:8168] (rev 0c)

do you guys have any idea why im not showing any controller for wlan? 

ifconfig shows:

```
eth0 link encap:Ethernet HWaddr 
UP BROADCAST MULTICAST MTU:1500 Metric 1
```

any one know how to active or get the pc to detect the network?


EDIT:

If I do a sudo lshw -c network

I still only get the ethernet interface but no wireless

---

### Post by praseodym on 2015-08-19
Hi,

what kind of computer is it? Check also
```

lsusb
```

---

### Post by robertosante on 2015-08-19
thanks! you can close this one I found reconnected everything and the wireless is detected

---

### Post by praseodym on 2015-08-19
You can mark it SOLVED using thread tools in the top bar

---

