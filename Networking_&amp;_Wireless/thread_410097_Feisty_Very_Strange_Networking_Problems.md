---
title: "Feisty: Very Strange Networking Problems"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by michelinux on 2007-04-15
Hi everybody.
When I use the Feisty Fawn Beta I can reach only a few website: for example I can easily reach all the Google website but **I cannot reach other popular sites (eg. Ubuntu) and my own Modem/Router web panel**. After a few seconds Firefox says there was a problem with the connections, while **the apt-get never gets time out**.
I tried the Feisty Fawn Beta with three different connection: 
[LIST]
[*]desktop with a wired connection (Realtek chip)
[*]laptop with a wireless connection (Intel chip)
[*]same laptop with a wired connection (Broadcom chip)
[/LIST]
The name resolution (DNS) works fine and also the ping works well, so maybe it is only a problem regarding TCP connections.
The two computers work fine with Edgy and Dapper in both live and installed environments, and they have all the same problem with Feisty. I also tried a daily build (Apr 14 2007) with no success.
I tried with both static IP Address and DHCP configuration. I can easily reach the other computers in my network, but I cannot reach my own router/modem.** I suspect there is some strange compatiblity issue between the Feisty networking and my Modem/Router**.
My Modem/Router is a Sagem F@st 3001, and never had any problem. It even works with that buggy OS called Windows.
I think it is a bug related with the new release of our favourite OS. 
[INDENT]**What do you think about that? **[/INDENT]
[INDENT]**Is there anything I can do to get more informations about this problem?**[/INDENT]
Thanks,
Michele

---

### Post by alexcollins on 2007-04-15
Wow, I was just about to post a new thread about this as I am having the exact same problem.

Only difference is I'm using a US Robotics 9003 router along with an Intel wired network card built into my DP965LT motherboard. Mine too works fine with Windows.

Thanks
Alex

---

### Post by michelinux on 2007-04-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/107195](https://bugs.launchpad.net/ubuntu/+bug/107195) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just posted a new bug in launchpad.

[INDENT][https://bugs.launchpad.net/ubuntu/+bug/107195]("https://bugs.launchpad.net/ubuntu/+bug/107195")[/INDENT]

Please go there and provide extra informations, if you can. Thanks

---

### Post by michelinux on 2007-04-17
Try this:

```
sudo su
echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
```

---

### Post by alexcollins on 2007-04-17
That fixed it for me, thanks.

---

