---
title: "Is it possible to have a static IP with a FailSafe DHCP"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by Kedster on 2009-12-13
Umm is there a way to have my laptop request a certain IP when it connects, but if unavailable just failsafe to DHCP and take what is there. I am asking because from what I understand is that if anyone has the IP I need my computer will not know what to do and fail? Also would this not be more beneficial for me if i am going occasionally bringing my computer to school and working on another network.But when I am at home i would like to have the same IP all the time(ohh and sometimes my ipod will take an IP) for torrents and remote desktop.

Please tell me if this is stupid or already available or if it even makes sense. Would it be worth doing?

---

### Post by lisati on 2009-12-13
What I usually do is have my router assign a set IP to each of my machines, and let them accept whatever they're given.

---

### Post by Dave67 on 2009-12-13
Stick with the DHCP once you setup a profile for a network it will auto connect to that network using DHCP and it will scan the network for other computer or laptops so there will be no conflict with another computers on that network meaning your system has an IP of 192.168.100.102 and and on the network at school a class mate laptop has the same IP as yours the DHCP server will change yours than no conflict. but when you go home the same thing happens again so you can still connect to the network, read the link below.

[http://kb.iu.edu/data/adov.html](http://kb.iu.edu/data/adov.html)

---

### Post by lisati on 2009-12-13
> **Dave67 said:**
> Stick with the DHCP once you setup a profile for a network it will auto connect to that network using DHCP and it will scan the network for other computer or laptops so there will be no conflict with another computers on that network meaning your system has an IP of 192.168.100.102 and and on the network at school a class mate laptop has the same IP as yours the DHCP server will change yours than no conflict. but when you go home the same thing happens again so you can still connect to the network, read the link below.

[http://kb.iu.edu/data/adov.html](http://kb.iu.edu/data/adov.html)

+1 Nice explanation in the link, which is why I prefer to let the router choose the IP addresses in my home network, rather than the computer.

---

### Post by Kedster on 2009-12-13
When I am at home i would like to have a static IP for remot desktop and torrents, so that I can have the ports opened. So if i stick with DHCP then how can I have these ports open all the time while at home

---

### Post by lisati on 2009-12-13
> **Kedster said:**
> When I am at home i would like to have a static IP for remot desktop and torrents, so that I can have the ports opened. So if i stick with DHCP then how can I have these ports open all the time while at home

I let my routers assign the IP addresses. Both my routers can be set to assign a specific IP address with a specific machine, and still have DHCP turned on. The details are different on each router. On my Netgear router's web interface, it's under the heading "LAN IP Setup".

---

### Post by Kedster on 2009-12-13
Would u know where I would find this setting for linksys routers

---

### Post by CoolDreamZ on 2009-12-13
Not sure if it is available on your linksys router. On my DLINK router the facility is called "DHCP Reservations" (under LAN setup) - you can reserve a specific IP address for your computer using the "Computer Name" (hostname) or MAC address of the network interface on your PC.

To get the MAC address type [FONT="Courier New"]ifconfig[/FONT] in a terminal and look for something like[FONT="Courier New"]HWaddr 00:1d:7d:c1:2a:ce[/FONT]. The MAC address in this case is [FONT="Courier New"]00:1d:7d:c1:2a:ce[/FONT] yours will be different as every network interface has a different number.

---

### Post by Kedster on 2009-12-13
so i supose im back where im started, does anyone have any ideas of what i should do?

---

### Post by CoolDreamZ on 2009-12-13
> **Kedster said:**
> Would u know where I would find this setting for linksys routers
Have you tried reading the user guide for your linksys router?

---

### Post by CoolDreamZ on 2009-12-13
If you find out that your router does not support DHCP reservations and you have the time, this post may help:

[http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

---

