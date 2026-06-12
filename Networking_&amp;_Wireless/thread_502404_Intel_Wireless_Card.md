---
title: "Intel Wireless Card"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by jrs0390 on 2007-07-16
I just installed Ubuntu Fiesty Fawn on my IBM Thinkpad T30

I went into my Windows Partition and found that I have what seems to be two wireless cards:
Intel(R) PRO/100 VE Network Connection 
and
High Rate Wireless LAN Mini-PCI Adapter with Modem

I was wondering if there was a driver available or some other way for me to get my wireless working. Any help would be GREAT. Thanks!

By the way, I have checked the wireless card drivers list, and these were not on the list.

---

### Post by frio80 on 2007-08-29
I am having the exact same problem as this gentlemen.  

I went to the Ubuntu Wiki and it told me to run a:

sudo pccardcrl ident

- Once I ran this, I was not able to see my Wireless Intel card.

I then ran,

gksudo gedit /etc/pcmcia/config.opts

Which says: 
socket 0: No product info available
socket 1: No product info available

I am 99% sure my wireless card didn't break when I made the switch from XP to Ubuntu.  Why can't Ubuntu recognize this card???  THanks.


- Duh.  Answer is right here! [Answer]("http://ubuntuforums.org/showthread.php?p=2499761#post2499761")

---

