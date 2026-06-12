---
title: "Lost internet connection"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by Mariane on 2009-10-09
I have internet connection through a wire, the very same wire I am using to write this post on a laptop. So I know there is no problem such as a firewall or anything. If the problem was not in the desktop machine itself but beyond I couldn't post this. 

On the desktop machine the internet connection does not work. I have dual boot win xp and ubuntu and neither has internet connection now. I have not done anything in particular, it was working when I left it and not working when I came back. 

To test with a ping I did: 

```

ping www.lri.fr

```

On both machines.

The laptop answers: 

```

PING futurwww.lri.fr (129.175.15.11) 56(84) bytes of data.
64 bytes from futurwww.lri.fr (129.175.15.11): icmp_seq=1 ttl=45 time=61.2 ms
(...)
4 packets transmitted, 4 received, 0% packet loss, time 3004ms

```

The desktop machine answers: 

```

PING futurwww.lri.fr (129.175.15.11) 56(84) bytes of data.
From 192.168.200.1 icmp_seq=1 Destination Host Unreachable
(...)
4 packets transmitted, 0 received, +4 erros, 100% packet loss, time 15013ms

```

Through the same wire. (I plug it into the machine I'm using)

At first I though there was some hardware problem with the desktop machine. But then I noticed that though it says "Destination Host Unreachable" it still manages to find the ip of  the pinged site. This is not true for all sites. 

```

ping www.ubuntu.com

```

The desktop machine answers: 

```

ping: unknown host www.ubuntu.com

```

Mariane

---

### Post by LewRockwell on 2009-10-09
try connecting your wires the way you want them then reboot your networking devices(usually just the router is sufficient)

you could learn more about routing, dhcp, and leases via various articles, guides, and tutorials located across the interwebs

.

---

### Post by halitech on 2009-10-09
you say it doesnt work in windows either? just want to clarify because if it doesn't work in windows then its not an Ubuntu issue but a hardware issue. If you are using the same cable with the laptop as you are with the desktop then that eliminates the cable and everything outward.

---

### Post by Mariane on 2009-10-11
Thanks, that's what I feared... 

As far as I can tell I lost my internet connection at the same time both under ubuntu and under windows xp on this dual-boot machine. I don't think I did anything wrong, it just happened. 

When I connect the laptop on the same internet connection (same wire) it works fine. 

So, what can I do now? Are there any commands I could type which would give me some clue as to what is wrong? 

My hardware experience is limited to opening a desktop box, looking inside at all the wires and stuff, removing some dust and closing the box. 

Please help. 

Mariane

---

### Post by LewRockwell on 2009-10-11
> **Mariane said:**
> As far as I can tell I lost my internet connection at the same time both under ubuntu and under windows xp on this dual-boot machine. I don't think I did anything wrong, it just happened. 

When I connect the laptop on the same internet connection (same wire) it works fine.

Having it quit for both Ubuntu and XP at the same time may indicate a hardware failure, given that your laptop connectivity still exists

What happened when you reset your router?

.

---

### Post by halitech on 2009-10-12
in Windows, check the control panel and see if your NIC is still showing there and also in Ubuntu, open a terminal and run ```
lspci
```and see if it is still seeing your NIC as well.

---

### Post by Iowan on 2009-10-12
Maybe I missed it somewhere - can you ping the router from the desktop (or vice-versa)?

---

### Post by Mariane on 2009-10-13
Thank you everyone. 

I have discovered that my hardware is OK, my mac address 
has been banned by some machine here. So I have to change 
it. 

So far I tried:
```

sudo ifconfig en0 ether 10:02:03:04:05:06

```

But it doesn't work, I copied this from the web and there 
is a mistake in it. 

I also tried to modify the "/etc/network/interfaces" file 
according to the instructions here:
[http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/change-your-network-card-mac-address-on-ubuntu/) 

And it doesn't work either. 

Mariane

---

### Post by halitech on 2009-10-13
the only "machine" that can "ban" an IP address is the router and it wouldn't do it randomly. Do you have access to log into the router? If you do, check and make sure the MAC address of the NIC hasn't been set to denied access.

---

### Post by Mariane on 2009-10-13
I don't have access to the router and I don't know how to force my way in, either. It didn't ban my mac address randomly, it banned it because a movie company complained I was seeding "district 9". 

So I'm thinking, if I can't get it unbanned maybe I could just change it? Or mask it in some way because the mac addresses are hard-wired, I've been told. 

When I ping from the desktop I go no further than 192.168.200.1

My normal traceroute is: 
1	Trouble.local	192.168.200.82	0.228ms
1	gw.local	192.168.200.1	0.809ms
2	130.208.247.193	130.208.247.193	0.952ms
3	ofanleiti-ge2.rhnet.is	130.208.18.25	3.033ms
4	bustadavegur-ge8.rhnet.is	130.208.17.22	1.355ms
5	stakkahlid-ge8.rhnet.is	130.208.17.26	1.400ms
6	hringbraut-ge8.rhnet.is	130.208.17.30	1.508ms
7	taeknigardur01-ge1.rhnet.is	130.208.17.34	1.550ms
8	ndn-gw.rhnet.is	130.208.16.8	1.300ms
9	rhnet-gw.nordu.net	193.10.68.149	1.569ms
10	dk-uni.nordu.net	193.10.68.133	31.552ms
etc. 

Except the destop is 192.168.200.86 and not 192.168.200.82. 

Mariane

---

### Post by rogerp1 on 2009-10-13
Your MAC address is tied to your network card

You would have to replace the network card.

What kind of network are you on? ISP, school/college?

---

### Post by Iowan on 2009-10-13
[Here]("http://www.debianadmin.com/change-your-network-card-mac-media-access-control-address.html") is one option... though you should probably work on resolving the real problem.

---

### Post by Mariane on 2009-10-14
Thank you Iowan. Now the problem I have is that I can't apt-get anything. I'll try saving MAC Changer on a usb key and transfer it to the desktop machine. 

Hum. 

Oh well, I'll try anyway. 

As for "resolving the real problem" this includes changing the way society work, I am working on it but I don't expect results anytime soon. 

Mariane

---

