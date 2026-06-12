---
title: "Wireless, fixed IP and WinXp"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by stena on 2008-04-17
Hi,

It is a question for Ubuntu . I have a desktop running on WinXP. It has 1 Ethernet and 1 wireless card. The idea is to use WinXP as an Access Point for my laptop (dualboot WinXP and Ubuntu Gutsy) and also have Internet through it's Ethernet card. I also gave a static IP to both connections and bridged them. On my laptop running WinXp I also gave a static IP (same network, same subnet) to my wireless connection. Everything works fine. But, I do not want to use WinXP any more, I want to use Ubuntu.

However, when my wireless (Ubuntu) is in Roaming mode, it finds a network, it even connects to it but no internet. The IP I get from desktop WinXP machine is 169.254.23.121 or something (I know that IP comes from XP). If I try to give static IP to my wireless card, it doesn't connect at all (and I do not see that it tries at all). Wireless under Ubuntu, by the way, works perfectly in Roaming mode in all other cases (regular access points around).

So, how to setup static IP on my wireless card under Ubuntu and how to make it work? And, can this combination (with XP) even work under Ubuntu? If so, what do I have to do?

Thanks in advance.

stena

---

### Post by sKAApGIF on 2008-04-17
It might be that you don't have a default route configured.  A very simple way to think of a default route is "the route or way to the internet".  

Since your WinXP access point is the one with the internet you will want your default route to point to it.

You can see if you have a default route by typing: route

Check for an entry "default" and made sure "Gateway" is the ip of your winxp machine.

If you don't have a default route you can add one with:

route add default gw ip.of.your.ap

---

### Post by sKAApGIF on 2008-04-17
It might be that you don't have a default route configured.  A very simple way to think of a default route is "the route or way to the internet".  

Since your WinXP access point is the one with the internet you will want your default route to point to it.

You can see if you have a default route by typing: route

Check for an entry "default" and made sure "Gateway" is the ip of your winxp machine.

If you don't have a default route you can add one with:

route add default gw ip.of.your.ap

---

