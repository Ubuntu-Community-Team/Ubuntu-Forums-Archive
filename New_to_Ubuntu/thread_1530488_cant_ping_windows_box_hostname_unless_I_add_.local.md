---
title: "cant ping windows box hostname unless I add .local"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by g3k0 on 2010-07-13
How can I ping a windows box without needing to put .local on the end of the hostname?

Thanks

---

### Post by jtarin on 2010-07-13
What command are you using to "ping"?

---

### Post by g3k0 on 2010-07-14
ping somehost.local

---

### Post by Excedio on 2010-07-14
should just be a simple
 
```
ping localipaddress
```
 
The local IP should look something like 192.168.x.x or 10.0.x.x

---

### Post by g3k0 on 2010-07-14
well I can ping the ip address.  I want to be able to ping the hostname.  I don't always have the ip address and I want it.  The problem that has brought this forth is that I am running apache on my system and it is set to connect to a mysql database on our network.  It works fine in windows, however in Ubuntu it dies on the host name and I am required to stick the ip address in my code because it cant resolve correctly.

That is the root of my problem.  I would however, like to be able to ping a hostname without having to put .local on the end of it.

---

### Post by Excedio on 2010-07-14
Are you trying to ping form inside the same netowrk or outside. I guess that's what is confusing me.

---

### Post by g3k0 on 2010-07-14
I am inside the network

---

### Post by _Mark_ on 2010-07-14
Add the IP to the /etc/hosts file, should work

> 192.0.0.0 hostname

---

### Post by jtarin on 2010-07-14
Add the address to the /etc/hosts file for name resolution. Such as ```
10.x.x.x hostname 
```

---

### Post by _Mark_ on 2010-07-14
> **jtarin said:**
> Add the address to the /etc/hosts file for name resolution. Such as ```
10.x.x.x hostname 
```

There's a delayed echo in this thread :p

---

### Post by g3k0 on 2010-07-14
Is there a way it can pick it up automatically rather than manually inserting it into the hosts file?

---

### Post by jtarin on 2010-07-14
That would be comparable to me guessing your name when we haven't been introduced.What's the problem editing the hosts file?

---

### Post by bodhi.zazen on 2010-07-14
> **g3k0 said:**
> Is there a way it can pick it up automatically rather than manually inserting it into the hosts file?

Yes, you need to run a dns server for your lan.

dnsmasq is simple to install and configure. dnsmasq uses your hosts file, but will service multiple clients.

otherwise, no you need to edit your hosts file.

---

### Post by jtarin on 2010-07-14
> **bodhi.zazen said:**
> Yes, you need to run a dns server for your lan.

dnsmasq is simple to install and configure. dnsmasq uses your hosts file, but will service multiple clients.

otherwise, no you need to edit your hosts file.

An excellent idea but possible overkill on a home network and the **_host file will still need to be edited._**  > Dnsmasq will serve names from the /etc/hosts file on the firewall machine: **_If the names of local machines are there,_** then they can all be addressed without having to maintain /etc/hosts on each machine.

---

### Post by g3k0 on 2010-07-14
Why can you ping a hostname from a windows box on a normal network, but with ubuntu you need a dns server?

Edit--
I missed your message earlier regarding the problem with editing the hosts file. Yes I could live with it that way, I am just trying to learn why it has to be done that way.  If I can ping hostname.local why isn't there someway for it to do that automatically?

---

### Post by tgm4883 on 2010-07-14
You don't need a DNS server, as proved by you being able to ping hostname.local

I had this same thing happen when I changed to openwrt on my main router. Your computer will ask the router for an IP address for the hostname.

---

### Post by g3k0 on 2010-07-14
> **tgm4883 said:**
> You don't need a DNS server, as proved by you being able to ping hostname.local

I had this same thing happen when I changed to openwrt on my main router. Your computer will ask the router for an IP address for the hostname.

So how do I get it to work the way I want it to?

---

### Post by bodhi.zazen on 2010-07-14
> **jtarin said:**
>  **_host file will still need to be edited._**

On one machine and not every client. It depends on how large a lan you have. If you are talking a single edit on a single machine, sure edit the hosts file.

If you are talking maintaining a hosts file on multiple clients I would go dnsmasq.

If your router performs DNS services, configure the router. If not use

1. hosts file (good for a single clinet).

2. dnsmasq - again very easy to install and configure.

3. Settle for having to add .local

---

### Post by jtarin on 2010-07-14
> **g3k0 said:**
> Why can you ping a hostname from a windows box on a normal network, but with ubuntu you need a dns server?

Edit--
I missed your message earlier regarding the problem with editing the hosts file. Yes I could live with it that way, I am just trying to learn why it has to be done that way.  If I can ping hostname.local why isn't there someway for it to do that automatically?It will do it automatically once you set up your hosts file. Windows does this also for you transparently when you set up network shares. Take a look at you local copy of windows hosts file and see if your other computers address is listed. Linux allows you to do this with your complete knowledge of what is going on.

---

### Post by g3k0 on 2010-07-19
I was able to get it to work automatically after reading a blog on the subject.  What I had to do was add 'wins' to a line in /etc/nsswitch.conf 
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```
install winbind
install samba

Thanks for the help everyone.

---

### Post by tgm4883 on 2010-07-19
> **g3k0 said:**
> I was able to get it to work automatically after reading a blog on the subject.  What I had to do was add 'wins' to a line in /etc/nsswitch.conf 
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
```
install winbind
install samba

Thanks for the help everyone.

Ah that makes sense. We would have needed more information about your network to figure that out. Thats what I have to do at work.

---

### Post by jtarin on 2010-07-19
> **_Mark_ said:**
> There's a delayed echo in this thread :p
I would love to hear a simultaneous one.:p

---

