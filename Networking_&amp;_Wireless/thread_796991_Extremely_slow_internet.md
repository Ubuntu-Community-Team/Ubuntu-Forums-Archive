---
title: "Extremely slow internet"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Pinocchio on 2008-05-16
Hi. I'm a new user of ubuntu. I have a hp pavilion dv2000 laptop with AMD 64-Bit processor. I installed the AMD 64-Bit version of ubuntu using wubi.

I can't use the wired network for a long time because my sister needs it too. I don't even have a chance to configure the wireless thingy.

For some unknown reasons, the wired network become extremely slow. It works completely fine yesterday when i first installed ubuntu but the next day when I boot into ubuntu, it's terribly slow.

I checked the statistic of the network and surprisingly I only received 16kb for like 30 seconds. It takes a year for google to load up. But my wireless network works ok on vista.

There are some possible causes of this problem but I'm not so sure:
-I'm dualbooting with vista and ubuntu 8.04. May be there's some conflicts with the wireless I'm using on vista I guess?

-I used wubi to install ubuntu as I wanna play around with it first before I seriously drop windows vista. Some problems here and there? I don't know.

Any help would be appreciated. Or some commands that I can try to get some more data will be really helpful. I really love ubuntu and I don't want to give up just for these stupid things. I don't care if something messed up because I can uninstall it and install it again using wubi. So Please help!

Thanks in advance.

---

### Post by vyruss on 2008-05-16
> **Pinocchio said:**
> I can't use the wired network for a long time because my sister needs it too. I don't even have a chance to configure the wireless thingy.

For some unknown reasons, the wired network become extremely slow. It works completely fine yesterday when i first installed ubuntu but the next day when I boot into ubuntu, it's terribly slow.

I checked the statistic of the network and surprisingly I only received 16kb for like 30 seconds. It takes a year for google to load up. But my wireless network works ok on vista.

I'd say that using **NetworkManager** (the small "two screens" icon on your top right hand side) to configure your wireless is a breeze, at most two clicks and a password. Certainly easier than configuring wireless through windows. Is your wireless adapter working? Maybe you need some drivers for it, try **System -> Administration -> Hardware drivers**.

You are not giving us any info about your network's setup. Also it would help to right click on NetworkManager, choose **Connection Information** and tell us what it says there. 

At the very least you could try writing down your network's configuration in windows and copying it by hand into Ubuntu's, by clicking on NetworkManager and choosing **Manual Configuration**.

> There are some possible causes of this problem but I'm not so sure:
-I'm dualbooting with vista and ubuntu 8.04. May be there's some conflicts with the wireless I'm using on vista I guess?

There is no way that ubuntu can "conflict" with vista. You either boot one or the other, the two installations' configurations do not interact.

---

