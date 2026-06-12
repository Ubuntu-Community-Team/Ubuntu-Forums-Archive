---
title: "Kernel panic with activation of wireless card"
date: 2005-03-25
forum: Networking &amp; Wireless
---

### Post by marknewlyn on 2005-03-25
Hi

I am using a Dell Inspiron 1100 with a TrueMobile 1300 card (Broadcom in disguise). I have to use ndiswrapper (1.0-rc2-1) to use the wireless card. 

Things were working relatively well until yesterday - I have had 5.04 installed for a few weeks and have just been doing package updates. Yesterday when I booted with
my wireless card in (an update was done prior to this) I got a kernel panic. 

I have 2.6.10-2 as my kernel and the last part of the kernel panic screen dump say:

> Code:   Bad EIP value.

<0> Kernel Panic   - not syncing: Fatal exception in interrupt.

I removed the wireless card and then could boot. Its erratic but sometimes I can get the wireless card to activate if I boot - login and then plug it in but I haven't nailed down the exact sequence yet.

Have anyone else experienced anything like this? I know the ndiswrapper and wireless
card driver haven't changed through an update in ages so it must be something else.

Help!

Mark

---

### Post by satkins on 2006-06-02
I know the original problem was on an older version of Ubuntu but I thought I would post this anyway.

I've run into this problem using the latest Dapper release.  My wireless card uses the rtl8180 chipset and I've got it configured using the ndiswrapper instead of the kernel version.  The kernel version doesn't seem to work at all for me.

I was using Gentoo untill yesterday when I thought I would try out ubuntu.

Stephen

---

