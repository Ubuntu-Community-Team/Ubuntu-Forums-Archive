---
title: "Intel 3945 Wireless problem"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by derickcyril on 2008-03-28
Hello,

I have Intel 3945ABG in my laptop, running ubuntu 8.04 beta. It shows wireless networks in Network manager, but the green light of wifi is not enabled. I have a Dell 6400.

Thanks in advance.

Derick.

---

### Post by heyho on 2008-03-29
I have the same wireless chipset in my fujitsu laptop - it works right out of the box in Gutsy.

Are you 100% sure that you have the wireless card switched on?

---

### Post by thirdspace on 2008-03-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/204979](https://bugs.launchpad.net/ubuntu/+bug/204979) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I booted the 8.04 beta livecd and noticed that the wireless network worked but the wireless status light stayed off. I found a bug report on launchpad about it:
[https://bugs.launchpad.net/ubuntu/+bug/204979](https://bugs.launchpad.net/ubuntu/+bug/204979)

> **derickcyril said:**
> Hello,

I have Intel 3945ABG in my laptop, running ubuntu 8.04 beta. It shows wireless networks in Network manager, but the green light of wifi is not enabled. I have a Dell 6400.

Thanks in advance.

Derick.

---

### Post by chili555 on 2008-03-29
Are you all using the module iwl3945? Check with *lsmod | grep 3945.* This is a well known "feature" of iwl3945: [https://bugs.launchpad.net/linux/+bug/176090](https://bugs.launchpad.net/linux/+bug/176090)

---

### Post by derickcyril on 2008-03-29
Hello,

I figured out the problem. The wifi light is not turning green, but the card is actually working :-)

So it must be a problem with the driver.

---

