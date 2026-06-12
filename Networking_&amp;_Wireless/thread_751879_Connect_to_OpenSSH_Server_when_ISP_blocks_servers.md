---
title: "Connect to OpenSSH Server when ISP blocks servers"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by jbpro on 2008-04-11
My ISP blocks the running of all servers.  I haven't tried obscure ports, but I don't think it would work.  The port is forwarded properly in my router.

I would like to connect to this server from outside my own network via SSH.  

Is it possible  to have the server connect to another box outside of my network and control it through that box acting as a relay ?

The server is running Ubuntu Server 7.10 with OpenSSH.

---

### Post by Mithrilhall on 2008-04-11
This is free and they have a linux client. [color=blue]([Hamachi]("https://secure.logmein.com/products/hamachi/vpn.asp?lang=en"))[/color]

LogMeIn Hamachi is a VPN service that easily sets up in 10 minutes, and enables secure remote access to your business network, anywhere there's an Internet connection.

It works with your existing firewall, and requires no additional configuration. Hamachi is the first networking application to deliver an unprecedented level of direct peer-to-peer connectivity. It is simple, secure, and cost-effective.



I've used it before and it's works pretty good. Especially when you want to bypass the whole port forwarding bit.

---

### Post by mrsteveman1 on 2008-04-11
Usually ISPs only block the privileged ports, those below 1024, high ports are almost never blocked.

In particular they block 80 to stop web servers, 135-139 because windows leaves those open and they are highly insecure, and some others.

22 isn't always blocked tho because its just SSH and isn't used to provide services to others.

I sometimes just use port 2222 for ssh, either by forwarding 2222 to 22 in the router or just setting openssh to use 2222 itself.

There are ways to do a reverse connect, like with netcat, get the box to call out to another box and then forward ssh over it etc.

---

