---
title: "Help for connection sharing..."
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by trastullo on 2006-11-06
Hi guys,
at first sorry for my english...I'm italian ubuntu user.
I've asked this question on ubuntu's italian forum, but nothing, any answer.
I've a problem, specifically i would share my adsl connection to my second pc with winxp installed.
My first pc (Ubuntu) have 2 ethernet device,
eth0 (connected with cross-over cable to pc winxp) and
eth1 (connected to modem ethernet adsl).

My configuration on eth1 is:
Ip: 192.168.1.2
sub:255.255.255.0
Gateway: 192.168.1.1 (modem's ip)

I tried to set on eth0:
Ip: 192.168.1.3
sub: 255.255.255.0
gateway: 192.168.1.1 (modem's ip)

And on pc (winxp)
Ip: 192.168.1.4
Sub: 255.255.255.0
Gateway: 192.168.1.1

but I isn't able to browse the web.
I use ppp0 to enable/disable connection on ubuntu.
How can I do? I hope to be clear :-k

---

### Post by kidders on 2006-11-06
Hi there,

Your first problem is that two network cards = two networks (unless of course you're willing to bridge them, which would be pointless).

You have to do a little work to get Ubuntu to act as a router for your XP box, but thankfully, there are plenty of HOWTOs around :-)

Just for the sake of argument, consider the ISP's side of your LAN to be 192.168.1.0/24, and the more "local" side of it 192.168.2.0/24. The first thing I would do is install iptables on my Ubuntu box, and configure NAT/etc. so packets could be routed successfully between the two.

Although not strictly necessary, I would then install DNS, DHCP and a web proxy, to make the day-to-day operation of both machines easier (and a little faster). This configuration would also allow you to remove the crossover cable at some point in the future, and replace it with a hub, to allow more PCs to get access to the web.

---

### Post by trastullo on 2006-11-06
Thanks,
I'll try that you have suggest me and I'll comunicate the results...

---

### Post by trastullo on 2006-11-14
Sorry guys but i'll become mad....Is it really difficilt share my dsl connection from ubuntu to win xp? How to? I'd visited on [http://www.iptables.org/](http://www.iptables.org/) but.....how to? sorry....

---

### Post by kidders on 2006-11-14
Hi there,

It's not really a very hard thing to do, but the networking concepts are complex enough. The first thing to do is make sure you understand all the issues involved ... after that, it's quite easy. Technically, all you need to do is set your Linux box up to masquerade for your Windoze box and enable packet forwarding (which is often switched off by default for security).

You might find it useful to learn about some additional services though, like DNS, DHCP, or proxying, so whatever is sharing your Ubuntu box's internet connection is a bit happier.

---

### Post by scrooge_74 on 2006-11-15
> **trastullo said:**
> Thanks,
I'll try that you have suggest me and I'll comunicate the results...

Go to your network configuration and tell your PC eth0 to get its ip from your ADSL most probably aby DHCP

tell the second card eth1 probably?

to use static ip like 192.168.1.1

then tell second computer to have and ip like 192.168.1.2, same subnet, gateway address to be 192.168.1.1

Then tell your firewall (firestarte?) to set eth0 for internet and eth1 for  internal LAN I don't remember if you have to tell the firewall to allow packets from 192.168.1.2.

---

### Post by trastullo on 2006-11-20
Ok....thanks for all....but if i want to set all in dhcp....? probably is most simple?

---

### Post by scrooge_74 on 2006-11-20
It doesn't work that way, your first ethernet card is for connecting to the internet and it gets its IP from your provider.  Your second card is for your own LAN, so you are the provider.  I have not been succesfull at having my own DHCP server to give address to my own machines so I have to give static IPs instead.

If you ask, I could only give DHCP service to my machines only when I had my first card unhook from my provider.

Remember that your second cards acts as a internet and LAN provider to your  own network and your machine is the bridge between your internal LAN and the outside world.  The same thing do routers provided by internet providers.  They get their own IPs from another machine and then it gives IPs to yours.

---

