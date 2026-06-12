---
title: "Dell Wireless Network Card"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by oh_no_not_her_again on 2008-01-06
My son decided in his wisdom to install Ubuntu onto my Dell Inspirion 2200 laptop but he couldn't get my wireless network to work on it...I know I have to try and download a load of stuff to get my internet connection to work now..He has gone back to Bristol and left me scratching my head......

I have both operating systems on my laptop now and am determined to master Ubuntu.

If I try to get the network card to work with Ubuntu system will it still work with Windows XP?:confused:

---

### Post by Bachstelze on 2008-01-06
Moved to Networking & Wireless.

All right, first, we need to know what kind of wireless adapter there is on your notebook. When you're in Ubuntu, open a terminal (Applications > Accessories > terminal), and type

```
lspci | grep Network
```

It should output some lines of text,which we need in order to identify your adapter. If you're in Windows right now, the Device Manager should also be able to tell which one you have.

Of course, whatever you do to get your wireless working in Ubuntu will not affect it's operation in Windows :)

---

### Post by oh_no_not_her_again on 2008-01-06
> **HymnToLife said:**
> Moved to Networking & Wireless.

All right, first, we need to know what kind of wireless adapter there is on your notebook. When you're in Ubuntu, open a terminal (Applications > Accessories > terminal), and type

```
lspci | grep Network
```

It should output some lines of text,which we need in order to identify your adapter. If you're in Windows right now, the Device Manager should also be able to tell which one you have.

Of course, whatever you do to get your wireless working in Ubuntu will not affect it's operation in Windows :)

A 1370 WLAN Mini PCI Card

---

### Post by Bachstelze on 2008-01-06
Okay, this card has a Broadcom chipset, which can be a bit of trouble. Can you get your notebook wired for installation of the drivers, or is wireless the only option you have ?

---

### Post by oh_no_not_her_again on 2008-01-06
> **HymnToLife said:**
> Okay, this card has a Broadcom chipset, which can be a bit of trouble. Can you get your notebook wired for installation of the drivers, or is wireless the only option you have ?

Oh heck......what do you mean?  :confused:

---

### Post by Bachstelze on 2008-01-06
I mean, can you get your notebook connected with an Ethernet cable while you install the drivers, or can you get it online ony with the wireless ?

---

### Post by oh_no_not_her_again on 2008-01-06
> **HymnToLife said:**
> I mean, can you get your notebook connected with an Ethernet cable while you install the drivers, or can you get it online ony with the wireless ?

Oh I see.  I have a modem that is unreachable (behind the lounge sofa) 

Can I not do it when the laptop is wireless?  

My son rushed off to get his train saying "You can sort it yourself mum!" 

Ha! Ha!:cry::cry:

---

