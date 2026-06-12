---
title: "Belkin Wireless G PCI"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by metalix on 2007-07-24
After I installed Ubuntu, the network manager detected by Belkin PCI card, and even the orange meter lights up. However, it still won't connect to the internet. 

As the orange bar is lit up, is this likely to be a ploblem with the network rather than the PCI card?

---

### Post by kevdog on 2007-07-24
Could be a driver related issue.  Did you install any drivers??

Let's see the driver currently installed for the card.  Type at command line and cut and paste output:
lshw -C network
lspci -nn

---

### Post by metalix on 2007-07-25
Thanks for replying.

It must have been an issue with my router because I'm logged onto the Internet now and replying using Ubuntu!

I think it's great that Ubuntu has such a good base of users who are ready to support people with their problems. Ubuntu is by far the best OS I've used.

Thankyou

---

