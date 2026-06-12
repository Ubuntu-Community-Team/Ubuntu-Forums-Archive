---
title: "Wireless doesn't work after ver.8 upgrade"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by milsurpninja on 2008-10-23
Hi all, brand new user here.  I started my little linux experiment to learn more about computers, and I've learned a ton already and haven't even scratched the surface!  

I've been looking through the threads and stickies here and have learned quite a bit, but I still can't solve my problem.

After much kicking and screaming I managed to get my wireless internet working on my 7.10 install.  Since I've upgraded to 8.04 it doesn't work anymore.  It doesn't 'see' any of the wireless networks in the area like it did before.  The PC does recognize the card still.  

I apologize for my ignorance.  I've been learning as much as I can but I'm getting overwhelmed and really need my hand held on this one.  :)

Thanks!

---

### Post by Ayuthia on 2008-10-24
Welcome to the community!  Can you help us out by letting us know what wireless card you are using?  If you are not for sure, can you go into the Terminal and post the results of:
```
lspci -nn
```It will list out the PCI cards that is in your system.

Thanks!

---

### Post by milsurpninja on 2008-10-24
> 02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller

ls is the generic list command right?

What does the -nn do?

Thanks!

---

### Post by barrel_master on 2008-10-24
> **milsurpninja said:**
> ls is the generic list command right?

What does the -nn do?

Thanks!

I think it prints some of the information as numbers.

[http://www.oreillynet.com/linux/cmd/cmd.csp?path=l/lspci](http://www.oreillynet.com/linux/cmd/cmd.csp?path=l/lspci)

---

### Post by milsurpninja on 2008-10-24
I uninstalled and reinstalled the driver, it works now.  :oops:

---

