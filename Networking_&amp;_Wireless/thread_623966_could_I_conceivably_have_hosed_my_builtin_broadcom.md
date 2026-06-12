---
title: "could I conceivably have hosed my builtin broadcom wireless?"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by edheil on 2007-11-26
As of the past few days, maybe a week, I haven't been able to see any access points with the broadcom wifi in my Gateway mx3215 (running up-to-date Gutsy).  (It was working fine in all ways before, using the native bcm43xx driver.)

This is true both when I'm booted into Gutsy *and when I'm booted into Windows*.

In both cases the OS doesn't report any problems at all with the card, it just acts as if there were no access points nearby when there definitely are.  Trying to join one explicitly by sepcifying the name fails too.

Because the problem persists in Windows, I'm assuming it's a hardware problem.  It didn't happen after any fooling around with firmware or anything like that, just one day it stopped working.

I just wanted to ask -- is it *conceivable* that anything done in Ubuntu could have hosed the card in such a way that it wouldn't work when booted into Windows?  Or am I correct in taking that as a sign that we're dealing with failed/broken hardware here?

Thanks!

---

### Post by Loukisgr on 2007-11-26
First of all try a static ip and customize the default gateway(put the wireless router's ip). If you own a wireless router disable the dhcp server from it and keep the static ip. Hope it works!!!

---

