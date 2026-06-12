---
title: "Help! Gigafast ee100-axp not working!"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by kdub432 on 2006-09-28
Hi,
I had an onboard ethernet chipset that didnt work... so i bought a gigafast ee100-axp. im pretty sure its a generic card.... but when i put it in the computer, it doesnt work. lspci shows two different ethernet chips, one for the unsupported onboard one,and the new one, which shouldd work..... I dont really know anything about installing linux drivers or hardware troubleshooting....
Any suggestions?

---

### Post by srf21c on 2006-11-13
Having the same issue with a gigafast 10/100 PCI adapter, probably the same model although not 100% sure, don't feel like hassling with cracking the case to find out just now.

At any rate, the card shows up under lspci as the following:

```
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

``` 

Anyone know if there's a module that can be manually loaded to enable the card?   Or perhaps there is something that needs to be done with /etc/network/interfaces?

---

