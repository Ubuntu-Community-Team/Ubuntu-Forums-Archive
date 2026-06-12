---
title: "problem sharing connection (ubuntu wifi and wired win xp)"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by jdimas on 2007-06-12
Hi, I'm trying to share a connection between my ubuntu and windows xp boxes.
the ubuntu box is connected via wifi to a linksys wrt54g router. I'm trying to access the internet from my windows xp, which is connected to the ubuntu box through ethernet.
I tried this post _ ["Howto Share internet connection"]("http://ubuntuforums.org/showthread.php?t=91370")_ but it didn't work for me (actually, it made my connection stop working).

can someone help me please?
thx

---

### Post by turinglabs on 2007-06-12
You don't specify how your boxes are connected, so here are some suggestions:

- Both the XP box and Ubuntu box need to be on the same logical network. The XP box should have a default gateway of the Ubuntu box's wired interface IP. So if the Ubuntu box has a wired  IP of 192.168.10.1, the XP box can be 192.168.10.2 with a default gateway of 192.168.10.1 (I'm assuming a /24 or 255.255.255.0 netmask for both). If the XP box only has one network interface, you don't really need to specify the default gateway, but it's good to be consistent.

- You'll need a crossover cable from your XP box to your Ubuntu box, or a straight-through cable with both boxes connected to the same hub or switch.

- Configure the wired network first, and get the two boxes communicating before you try to configure anything else (both boxes should be able to ping one another).

- Once the two boxes are communicating, you can (on the Ubuntu box) turn on IP forwarding, and enable IP masquerade, as per the article you referenced. At this point, the XP box should be able to get out to the internet. Note that the iptables line should reference the wireless interface, and you should specify the source, like 'iptables -t nat -A POSTROUTING -s 192.168.10.2 -o wlan0 -j MASQUERADE'.  If you don't specify the source, you'll end up NAT'ing local connections from the Ubuntu box itself, probably not what you intend.

- You only need dnsmasq if you want to use the Ubuntu box as a fowarding DNS or simple DHCP server. Your XP box can use any DNS server if it can get out to the internet. You may have to configure dnsmasq, esp. if you are using it as a DHCP server. I would leave it out to start.

- You only need ipmasq if you want a way to make this permanent. I haven't used it, but from the package description it appears to handle the masquerade (nat) and firewall automatically. I would do this manually, then install ipmasq if you get it working.

---

