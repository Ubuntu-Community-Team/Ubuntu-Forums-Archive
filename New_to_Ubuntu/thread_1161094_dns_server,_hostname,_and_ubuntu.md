---
title: "dns server, hostname, and ubuntu"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by devaparvata on 2009-05-16
I installed XAMPP on my ubuntu-server machine. And it works flawlessly. I took a static IP from my ISP and I set up port forwarding on my modem. Now, people can connect my website, hosted at home via the IP address of 88.XXX.XXX.XXX.

I want to register a hostname let's say XXXXX.COM. I will pay some money and I plan to start that people can access my website not just only entering the IP address also by entering XXXXX.COM to their browser's navigation bar.

What should I do next? Should I install a DNS server e.g. bind9? Or should I register the hostname first? I do not know what exactly to do. Please help.

---

### Post by wanchai on 2009-05-16
Registering the host name is independent of whether you are using it or for what you are using it. However, when selecting the registrar you should make sure that you pick one that gives you full control over all records associated with the domain, for example via a web site. Since you have a static IP address, you would then change the A record of your xxxx.com domain to point to that IP address. Then you may want to create an alias, a C record, [www.xxxx.com](www.xxxx.com) that points to xxxx.com.

If you don't have a static IP, you can use one of the free dynamic DNS providers. But that's another story...

DNS servers like bind9 are needed only for the machines in your network to find out what, for example, the IP of ubuntu.com is. In order for people to find the IP address of your domain, you won't need a DNS server on your site, the registrar's DNS should take care of that.

---

### Post by devaparvata on 2009-05-22
Hello again.

I register a hostname let's say hostname.com
I told the registrar that as nameserver register ns.hostname.com

Now, should I install bind?
 


> **wanchai said:**
> Registering the host name is independent of whether you are using it or for what you are using it. However, when selecting the registrar you should make sure that you pick one that gives you full control over all records associated with the domain, for example via a web site. Since you have a static IP address, you would then change the A record of your xxxx.com domain to point to that IP address. Then you may want to create an alias, a C record, [www.xxxx.com](www.xxxx.com) that points to xxxx.com.

If you don't have a static IP, you can use one of the free dynamic DNS providers. But that's another story...

DNS servers like bind9 are needed only for the machines in your network to find out what, for example, the IP of ubuntu.com is. In order for people to find the IP address of your domain, you won't need a DNS server on your site, the registrar's DNS should take care of that.

---

### Post by wanchai on 2009-05-22
Yes. Bind is a Domain Name Server and if you want to be your own DNS you'd have to use something like bind. Unfortunately, I do not know how to configure it so that it has authority over your domain. Maybe someone else can help you with that.

But let's go back one step: Why would you want your own name server in the first place? In the original post you mentioned something about a server at your home. If a single server at your home is all you want, then running your own DNS is overkill. If you have only one server and one IP, then ns.hostname.com and [www.hostname.com](www.hostname.com) etc will all be the same machine.

I don't know which registrar you are or will be using, but the the ones I'm using provide DNS at no extra charge and relying on their name servers is one less hassle for me.

---

### Post by superprash2003 on 2009-05-23
you could register with no-ip it would do all that for you..

---

### Post by wanchai on 2009-05-23
he has a fixed IP, so he wouldn't need no-ip or dyndns

---

