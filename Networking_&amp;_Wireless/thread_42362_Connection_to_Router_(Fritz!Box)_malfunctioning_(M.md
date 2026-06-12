---
title: "Connection to Router (Fritz!Box) malfunctioning (MTU prob?)"
date: 2005-06-17
forum: Networking &amp; Wireless
---

### Post by fhennies on 2005-06-17
My Ubuntu machine works fine in most ethernet networks, but i can't connect to my (new) router at home:

From the Router (Fritz!Box ata), most times i don't get a DHCP lease, when using static IP and ping the router i have >50% packet loss. DNS only works for local network.

The router works fine with other machines (Desktop with Win XP / old Notebook with Ubuntu) 


Hardware

Notebook Compaq Evo N410C with Ethernet Pro 100 (eepro100)

Using e100 instead of eepro100, i get a DHCP lease, and have less packet loss, but still can't connect with http.

I had a mtu-prob once in connection with the Cisco VPN-client ([http://ubuntuforums.org/showthread.php?p=179886#post179886)](http://ubuntuforums.org/showthread.php?p=179886#post179886)), thats why i use the eepro100.

Recently i had a problem when connecting to a switch over a minihub, i couldn't get a connection, directly it worked.

Any suggestions?

---

### Post by Joeb on 2005-06-17
Are you sure you don't just have a bad cable?  Maybe a crossover cable instead of a regular one?  If that's not the case, what happens if you plug the Ubuntu box into one of the ports that works for other computers and vice versa?  Does the Ubuntu box then work and the other one doesn't?  If so, then you have a bad port.

It could be the driver/nic, however, I'd check the cable type first.

---

### Post by fhennies on 2005-06-17
Good idea, but i have checked this before. Same port/cable works with other machine.

Rather seems to be a driver issue...

---

### Post by Joeb on 2005-06-17
If you run an ifconfig on it, what do you get?  If you get a "Try again" message, that means you most likely have an interrupt problem.

---

### Post by Joeb on 2005-06-17
I just re-read your original post.  If I understand correctly, your laptop works on most ethernet networks, just not yours at home with your new router.  If that's the case, I would propose that the nic and driver are fine and there might be some setting on the router.

Is the eepro100 built in or is it a pcmcia card?  I thought the evo had 802.11b or something like that.  Does your router support wireless and maybe there is a conflict with the computer trying to use two connections?

Does the laptop dual boot?  If so, does it work under Windows?

While it is possible that it is an mtu problem, I would think it wouldn't work with other routers, either.

---

### Post by Joeb on 2005-06-17
googling around a little bit, I found this link
[https://lists.netfilter.org/pipermail/netfilter/2005-April/060007.html](https://lists.netfilter.org/pipermail/netfilter/2005-April/060007.html)

I don't know if it applies or not, but it appears there might be a problem with the driver, kernel 2.6.11 and running a firewall

I know this sounds like clutching at straws, but the eepro drivers are supposed to work very well (which doesn't help you, I know).

---

### Post by fhennies on 2005-06-18
@Joeb: Thank you for your ideas:

1) ifconfig works fine and shows what it should

2) eepro100 is built-in, my notebook has no wireless

3) I checked all possible router settings, but there is not much to configure

4) I don't have a win on my machine, but tried with a different nic (PC-card realtek 8390) that works fine.

5) I use standard ubuntu, no firewall, but anyway thanks for the suggestion.

In the moment the workaround with the PC-Card works, probably with the next kernel the problem will solve, thank you once more for your effort!

---

### Post by fhennies on 2005-06-20
Update:

I disabled IPv6, now it works...

---

