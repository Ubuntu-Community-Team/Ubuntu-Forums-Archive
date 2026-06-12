---
title: "Can't get my LAN DNS working in Ubuntu..."
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2006-09-02
Hello all!
I have a very wicked problem in Ubuntu. I can't ping computers that are inside of my LAN. I can ping them using their IP numbers but when I try to ping them (a PC called 'server' that does exist in the network for instance) using their names I get this:```
ping: unknown host server

```I've got a D-Link router that is a DHCP server (yes, I've got DHCP) and I can never even guess what IP given PC has at the moment. I tried to do the trick using the static IPs but the problem still exists, I can't operate with PCs using their names inside of my LAN. Everything works fine with the internet, so I can ping google for instance. Yet, I have to add that everything works fine under Windows.

Any suggestions? And sory if this problem was covered here already, I couldn't find it.

---

### Post by Uluen on 2006-09-02
DHCP doesn't do this, you need local DNS.
Do you have a server up 24/7 that you can use? Check out dnsmasq in the repos, it's a easy to configure DNS and DHCP server.
You could use static IPs on all computers and update your hosts files as well, more hassle though.

---

### Post by PryGuy on 2006-09-02
I know that we are talking about DNS not DHCP here. The thing is that everything works perfectly in Windows. And my DHCP server is not a PC actually but a [small plastic box]("http://www.dlink.com/products/?sec=1&pid=6"). Who's the DNS server in my network? The only thing that makes me feel strange is that it works perfectly under Windows so why can't it work here in Ubuntu. Is there anybody in the forum that would have the same problems? And I just can't use static IPs, sorry...

---

### Post by sebastfr on 2006-09-02
what does your "/etc/resolv.conf" say? you should have something like:

search localdomain
nameserver [ip-of-dns-server]

Seb

---

### Post by PryGuy on 2006-09-02
```
search 192.168.0.1
nameserver 192.168.0.1
```Who *should be* my DNS server in this case?

---

### Post by sebastfr on 2006-09-02
baaahh sorry, I misread your first post...

I thought dns wasn't working for internet (eg. pinging google.com)... if the problem is inside your network it's because you need to add static dns lookups to your /etc/hosts file. This is what mine looks like:

> 

192.168.1.11    sebserver
192.168.1.1     gw gateway
127.0.0.1       localhost
192.168.1.3     blanket
192.168.1.5     macserver



so here you basically map an ip address to one/several names. I think it works on Windows straight away as Windows tries to resolve the name using netbios/smb (whatever the name is)

There are other solutions than declaring manually the ip/name mappings, but this solution should be fine for a small lan.

Seb

---

### Post by PryGuy on 2006-09-02
The problem is how do I guess the IP if it's not necessary the same? Yet I've got two Windows notebooks that are used in different Wi-Fi networks and configured with the DHCP protocol so I can't and don't feel like disabling the DHCP protocol. Do you want to say that it's not possible to use DHCP to the full under Linux?

---

### Post by xyrer on 2008-02-27
You can use winbind, just make a quick search in the forums, it worked for me

---

### Post by Dmskz on 2008-04-10
I have exactly the same problem. Been banging my head on it too. What is this winbind? I googled it, but it looks quite involved. 

To recap, my router assigns IPs to the computers on my internal home network via DHCP. I never know which IP each computer will get (depends on what order they are switched on each day etc). I don't want to assign static IPs. 

The network is a mix of Linux, XP and Vista. Each computer has a hostname, including the Ubuntu box of course. The windows machines can identify each other and the Ubuntu box via the hostnames (e.g. for ping <hostname> type request). The ubuntu box can only successfully ping itself via its hostname but not any of the other machines. It can ping any machine via its internal IP address though, so no deep-rooted network problems. Just a name-resolution issue.

Is there an easy-to-follow tutorial out there that can help linux-challenged simpletons like myself and the original poster to resolve this issue? Thanks.

---

### Post by Eiríkr on 2008-04-10
It is possible to leave all your computers' network settings on DHCP, but to also configure the DHCP server (your router) to offer up fixed IP addresses for client machines based on their MAC addresses.  I've attached a screenshot of my own router's settings for reference; this is on a D-Link WBR-2310.

Cheers,

Eiríkr

---

### Post by xyrer on 2008-04-10
just install winbind by "sudo aptitude install winbind" and then modify the nsswitch so it resolves by winbind

---

