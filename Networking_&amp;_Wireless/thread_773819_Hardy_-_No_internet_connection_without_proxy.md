---
title: "Hardy - No internet connection without proxy???"
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by LordKael on 2008-04-29
Hi. Let me just explain my situation, because this is truely driving me insane :P

I have a Toshiba Qosmio laptop that I was using with Windows Vista up until last week, when I upgraded to the new LTS version of ubuntu. I've used ubuntu before, but I'm still no expert. :)

I use my laptop for both home and work. At home I have a small network with a few servers and a linux box as a router/firewall. At work I have two options: use DHCP and a proxy, or use a dedicated IP that was assigned to me (I'm special :P).
Using windows, I only had to switch to my manual IP when I arrived at work, since no proxy was needed in either locations, this way. After I installed ubuntu, the situation turned: I managed to set the manual IP, but I could not connect to the internet. Using the proxy (with still the manual IP) I managed to fix this situation (weird).

So yesterday I arrived home, deactivated the proxy (in system > preferences, switched to the 'connect directly to the internet' option) and set the network to recieve DHCP from my router. Network works fine, as I can ping and rdesktop my servers. The servers have internet access, but my laptop doesn't&#451;

So I went to my router's web admin (IPCOP) and configured a web proxy... firefox magically started to work... HELP? :s

Oh, just to clarify... Firefox is using the 'system setting' for proxy and I only configured the proxy in system>preferences.

Also, just to mess it up a bit, My virtual machine running windows XP (so I can actually do my work @ .NET :P) is using a bridged connection to my eth0 and can connect to the internet just fine.

*shoots himself*

---

### Post by jtrindle on 2008-04-29
When you configure your proxy, are you using a numeric IP or an address you have defined in your hosts table?

If that's true, the browser could find the proxy without DNS.  Then any name resolution which is done via the proxy finds DNS just fine because the *proxy machine* has DNS defined.  If you try to connect direct you can't look up a website name and so can't find its numeric IP.  This makes some kind of sense if you access your other local machines with host-defined names or numeric IPs.

From your laptop, can you ping a numeric IP such as 204.17.220.5?

---

### Post by LordKael on 2008-04-29
> **jtrindle said:**
> When you configure your proxy, are you using a numeric IP or an address you have defined in your hosts table?

If that's true, the browser could find the proxy without DNS.  Then any name resolution which is done via the proxy finds DNS just fine because the *proxy machine* has DNS defined.  If you try to connect direct you can't look up a website name and so can't find its numeric IP.  This makes some kind of sense if you access your other local machines with host-defined names or numeric IPs.

From your laptop, can you ping a numeric IP such as 204.17.220.5?

I used a numeric IP in my proxy setup (192.168.0.3:8080), and no, I can't ping a numeric IP, just like I can't ping a hostname :(.
I can ping local network ip addresses just fine...

---

### Post by LordKael on 2008-05-05
*up*

Anyone?

Does anyone use the proxy feature in ubuntu 8.04? Is it working fine, or am I not the only one?

Btw, anyone using proxy with maybe Kubuntu? I'll be happy to try KDE out, if it solves my problem :P

I'm using only WinXP at the moment, and it's making me depressed. :(

---

