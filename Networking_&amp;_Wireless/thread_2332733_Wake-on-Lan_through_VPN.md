---
title: "Wake-on-Lan through VPN"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by flucoe2 on 2016-08-03
Hi,

I was trying to set up ssh access to the desktop I have in my office and I did this by allowing for only ssh keys and disabling password access. What works? If I leave the desktop on before leaving, then I can use my office vpn to connect from anywhere with no issues. However, I can't turn the desktop on through the VPN. At the same time, when within my office network (say, using wifi), I can use wake-on-lan without any issues and then ssh into the desktop using my laptop. So, it seems as if the VPN is interfering with wake-on-lan (I'm using powerwake) but I'm not sure why or how. Any suggestions would be welcome. Thanks!

---

### Post by DuckHook on 2016-08-04
> **flucoe2 said:**
> &#8230;I can't turn the desktop on through the VPN.My first thought would be: "of course not". Why would you want your internal network to be exposed that way? The whole point of a firewall is (among other things) to stop outsiders from activating machines at will, so your firewall is doing its job preventing you or anyone else acting on the outside from waking anything on the inside.>  At the same time, when within my office network (say, using wifi), I can use wake-on-lan without any issues and then ssh into the desktop using my laptop.Your IT staff have decided that anyone within the network is trustworthy, so has allowed WoL within the internal network. I'm not sure that I would be so trusting, but that's just me. They have obviously decided otherwise, so you enjoy that functionality within the internal network.>  So, it seems as if the VPN is interfering with wake-on-lan (I'm using powerwake) but I'm not sure why or how. Any suggestions would be welcome. Thanks!The VPN is not "interfering" with WoL. VPN is a totally different technology and has nothing to do with WoL. It has no built-in WoL functionality. Your IT staff have decided that they will not allow external WoL access. This is a combination of your organization's security policy and a bunch of technical settings on whatever equipment that functions as your gateway and WoL server.

---

### Post by flucoe2 on 2016-08-05
Thanks DuckHook for the explanation.

---

