---
title: "OpenVPN - I can't understand"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Pegasus_from_UA on 2008-02-21
So I installed the OpenVPN server whith routed mode (i.e. tun device is used). It seems to me it works but....
I have 2 users at least. When they are connected I only  have  1 tun device on the server side. Don't I should have 2 tun-device on the srver side ?

Why I asked?
I have a billing system and it doesn't work correct.

Please help me !!!

---

### Post by SpaceTeddy on 2008-02-21
this is really a question about openVPN, but i'll answer anyways (just teasing).

the server always only uses ONE tun device. it will always have the first ip on the network specified in your openvpn config file. So it is quite normal to stick with one Device.

If you want to test if everything works, you should be able to ping the IP's of the clients from the server (as far as i know, it should be 6 and 10 at the end) and you should be able to ping the server from each client (as i said, that should be the 1 at the end)

anything else i can be of service with ?

---

### Post by Pegasus_from_UA on 2008-02-21
Thanks for the reply!
I see. Ping is Ok. All program are working . But a billing system don't count a traffic :(

---

### Post by SpaceTeddy on 2008-02-21
i don't know what billing system you are using, but openvpn gives you a status (either via mangement or in a status file) where it writes out the connection time, remote ip, local, bytes send and bytes received by each host.

also, if you are only interrested in data transfer, you can use it the tun device like ANY other network card. If you have ip persistant pool enabled in your openvpn config you can make sure that each openvpn user always get the same ip and can bill them by that... 

or did i misunderstand you ?

---

### Post by Pegasus_from_UA on 2008-02-21
> i don't know what billing system you are using, but openvpn gives you a status (either via mangement or in a status file) where it writes out the connection time, remote ip, local, bytes send and bytes received by each host.
yes ? I know.
> also, if you are only interrested in data transfer, you can use it the tun device like ANY other network card. If you have ip persistant pool enabled in your openvpn config you can make sure that each openvpn user always get the same ip and can bill them by that...
Yes , I made mac + ip thing by the sertificate name.

I use the Stargazer billing system. All the programs are working via openvpn, but I can't bill ther traffic.

---

### Post by SpaceTeddy on 2008-02-21
sorry, but my russian (if that is russian) is no existant, so i cannot help you with that billing system at all... i can find the download link on their page, but that is about it... 

sorry, that one you will have to figure on your own... 
althought it does look like a very interesting piece of software.

---

### Post by Pegasus_from_UA on 2008-02-21
Thanks anyway...
Look ... I just  don't understand why the billing are billing a connection via an ethernet card but don't bill a connection via openvpn card ? 0_o

---

### Post by SpaceTeddy on 2008-02-21
well, since i don't know the billing system, i can only guess. But i suspect that they scan for network devices a certain way, and since the tun device is a software network adapter, it might not show. some other programms had these problems in earlier versions aswell, that the tun devices would NOT show up in their list of network devices.

my guess is that you need to talk to the developers about that and wait for them, or you go about and change the source of stargazer yourself to fit your needs (if that is allowed)

---

### Post by Pegasus_from_UA on 2008-02-21
You see ... they want money . I have no money.My salary is too small :(

---

### Post by The Cog on 2008-02-21
Is your problem that the billing system doesn't see any traffic at all, or is it that you cannot separate the traffic usage of different OpenVPN clients? 

If your problem is that you cannot separate the client traffic because htey share a tun interface, you could parhaps consider running a different OpenVPN instance (listening on a different UDP port) for each client. That way, they will have a different tun interface each.

---

### Post by Pegasus_from_UA on 2008-02-21
> **The Cog said:**
> Is your problem that the billing system doesn't see any traffic at all, or is it that you cannot separate the traffic usage of different OpenVPN clients? 
No. If I only have 1 connection a billing can't bill. 
Look... The billing system should write iptables rules for each client and it do it. I can see it by the command 

```
iptables -L
```

So I guess the billing system see clients.

> If your problem is that you cannot separate the client traffic because htey share a tun interface, you could parhaps consider running a different OpenVPN instance (listening on a different UDP port) for each client. That way, they will have a different tun interface each.

Do you want say I need to create for each an openVPN client create separate an openvpn(#).conf file?

---

### Post by The Cog on 2008-02-22
If your problem was just that your billing system can't tell the clients apart, I would have suggested having multiple openvpn#.conf files and multiple tun# interfaces. 

But if the problem is that the billing system just doesn't see the tunnel interfaces at all (maybe it's only written to deal with eth# interfaces) then I don't know what you can do about that.

---

### Post by Pegasus_from_UA on 2008-02-22
> **The Cog said:**
> If your problem was just that your billing system can't tell the clients apart, I would have suggested having multiple openvpn#.conf files and multiple tun# interfaces. 

I tried to make  many  openvpn#.conf  but  it doesn't work  =(


> But if the problem is that the billing system just doesn't see the tunnel interfaces at all (maybe it's only written to deal with eth# interfaces) then I don't know what you can do about that.

The billing system sees client openvpn ip but it can't bill the traffic. I don't know why =(

Anyway thanks !

---

### Post by The Cog on 2008-02-23
They will each have to listen on a different port number (I think 1194 is the default). They will each need a different tunnel number and a different IP network too. e.g.

openvpn1.conf:
port 9001
dev tun1
server 10.8.1.0 255.255.255.0

openvpn2.conf:
port 9002
dev tun2
server 10.8.2.0 255.255.255.0

---

### Post by Pegasus_from_UA on 2008-02-24
> **The Cog said:**
> They will each have to listen on a different port number (I think 1194 is the default). They will each need a different tunnel number and a different IP network too. e.g.

openvpn1.conf:
port 9001
dev tun1
server 10.8.1.0 255.255.255.0

openvpn2.conf:
port 9002
dev tun2
server 10.8.2.0 255.255.255.0

The billing system don't bill even one client , so I guess there is problem in other thing...

---

