---
title: "Using static IP"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by firecat53 on 2005-09-05
I think I'm missing something when I'm trying to get a static IP. I have the router enabled for static ip of 192.168.0.101. My /etc/network/interfaces entry is:

iface ath0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1
auto ath0

When I connect using wpa_supplicant/madiwif I can ping the local network, but I can't see the internet. Am I missing a step to configure the static IP?

Thanks, Scott

---

### Post by lol on 2005-09-05
[QUOTE=][/QUOTE]
 stupid question but... did you setup your DNS servers?

---

### Post by pokapeski on 2005-09-05
[QUOTE=firecat53]I think I'm missing something when I'm trying to get a static IP. I have the router enabled for static ip of 192.168.0.101. My /etc/network/interfaces entry is:

iface ath0 inet static
address 192.168.0.101
netmask 255.255.255.0
gateway 192.168.0.1
auto ath0

When I connect using wpa_supplicant/madiwif I can ping the local network, but I can't see the internet. Am I missing a step to configure the static IP?

Thanks, Scott[/QUOTE]

Can you ping your router? a name on the Internet? an IP on the internet?

---

### Post by s_p_a_r_k_y on 2005-09-05
I'm going to bet its the DNS servers which he can't reach bc they probably aren't set in /etc/resolve.conf

---

### Post by firecat53 on 2005-09-05
Yep...that was it, thanks!!  Is there a program that modifies resolv.conf? I had the connection working before at one point, but then it just stopped, and I'm not sure what I did to change anything. I've connected to a variety of networks, both wired and wireless.

---

### Post by s_p_a_r_k_y on 2005-09-05
um well dhcp provides DNS servers in the lease so if you ever connected to a dhcp then it will have wiped out anything you statically entered. Keep a known "good" file in your /root folder and just copy that over resolv.conf if it gets wiped out

---

