---
title: "Dell Wireless Compatibility?"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by ebbishop on 2010-01-07
Hello-
I'm finally fed up with windows and am getting ready to make the switch to ubuntu on a new machine. I'm looking at Dell laptops mostly and am wondering if there is any good information out there about the (new?) Dell 1397 802.11g half-mini wireless card and if it is or isn't functional with Ubuntu.

I've been doing a bunch of reading, but I'm very much a newbie- beginner talk please!

Thanks!

---

### Post by bkratz on 2010-01-07
> **ebbishop said:**
> Hello-
I'm finally fed up with windows and am getting ready to make the switch to ubuntu on a new machine. I'm looking at Dell laptops mostly and am wondering if there is any good information out there about the (new?) Dell 1397 802.11g half-mini wireless card and if it is or isn't functional with Ubuntu.

I've been doing a bunch of reading, but I'm very much a newbie- beginner talk please!

Thanks!

I think I read somewhere that the Dell wireless cards were just renamed Broadcom cards, but not sure.

Could you go to the terminal and enter
(Applications>>Accessories>>Terminal)

lspci -nn     (that is LSPCI in lowercase)

and copy/paste the output here?

---

### Post by ibbill on 2010-01-07
Just installed the broadcom sat driver on a dell inspiron 1520 from system> administration > hardware drivers and I am happy to say I finally have wireless internet

---

### Post by ebbishop on 2010-01-07
> **bkratz said:**
> 
Could you go to the terminal and enter
(Applications>>Accessories>>Terminal)

lspci -nn     (that is LSPCI in lowercase)

and copy/paste the output here?

I don't actually have a Dell laptop yet. I'm shopping around and hoping to find one with compatible hardware.
The specs on the Dell website are what I listed above- nothing about Broadcom, though it's Broadcom that seems to be coming up in the forums most often.

Thanks!

---

