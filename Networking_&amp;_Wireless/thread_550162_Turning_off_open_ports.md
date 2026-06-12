---
title: "Turning off open ports"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by Chris Johnson on 2007-09-13
Newbie question: I'm about to move to University halls, which have a draconian policy on running services of any kind. I'd therefore like to turn off as many open ports as I can, but I'm not sure which to turn off and how.

```
[B]
chris@indeed:~$ sudo nmap -sS -O 127.0.0.1 | grep open[/B]
22/tcp   open  ssh
53/tcp   open  domain
111/tcp  open  rpcbind
631/tcp  open  ipp
865/tcp  open  unknown
2049/tcp open  nfs[B]
chris@indeed:~$ sudo netstat -nap | grep tcp | grep LISTEN[/B]
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     5655/hpiod          
tcp        0      0 0.0.0.0:865             0.0.0.0:*               LISTEN     5774/rpc.mountd     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:57637           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     4846/portmap        
tcp        0      0 0.0.0.0:34320           0.0.0.0:*               LISTEN     5890/rpc.statd      
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN     5590/dnsmasq        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     5629/cupsd          
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     5658/python         
tcp6       0      0 :::53                   :::*                    LISTEN     5590/dnsmasq        
tcp6       0      0 :::22                   :::*                    LISTEN     5836/sshd    

```

ssh/sshd - I need to be able to SSH into other machines without being open to it myself: not sure how to do this.

domain/dnsmasq - I know that this is internet sharing but I'm sure how to turn it off.

cupsd/ipp - I know that this is to do with print servers. I have a printer connected to my computer by USB, but don't need access to any network printers. Is this port necessarily open for printing to local printers?

While I have an idea of what the others do, I don't know which which are parts of Linux that I should probably keep, and which are other programs that I can disable. Could someone advise what should probably be shut down and how? Thanks.

---

### Post by kidders on 2007-09-14
Hi there,

The first thing worth noting about what you've posted is that a port scan of 127.0.0.1 won't tell you anything at all about what non-local users can access on your computer. Try scanning a remotely accessible network interface. If you're running a firewall, you may prefer to do it from another PC, unless you *know* it makes no difference.

> **Chris Johnson said:**
> I need to be able to SSH into other machines without being open to it myself: not sure how to do this.Don't run an SSH server ... or at least don't bind one to a remotely accessible interface. The idea that you'd need an SSH server to access *remote* SSH servers is a bit like suggesting that you can't browse the web without installing Apache.

> **Chris Johnson said:**
> domain/dnsmasq - I know that this is internet sharing but I'm sure how to turn it off.These are DNS and masquerading services.

> **Chris Johnson said:**
> cupsd/ipp - I know that this is to do with print servers. I have a printer connected to my computer by USB, but don't need access to any network printers. Is this port necessarily open for printing to local printers?In most cases you need to leave your print services running (and their ports open to local traffic) in order to print. You'll probably prefer to deny remote access to your printers though. Again however, these services are completely unnecessary when using printers on other computers.

> **Chris Johnson said:**
> Could someone advise what should probably be shut down and how?If I were in your position, I wouldn't have configured *anything* to be remotely accessible in the first place, unless I specifically wanted it for something. You should check that nothing you don't want entire networks (or perhaps even the world) to see is externally visible ... but that's just proper practice for any situation.

In general terms, none of the services you've listed as being locally visible (with the possible exception of SSH) should _ever_ be externally visible, if your computer is directly connected to an untrusted LAN (eg at a University) or the internet.

Once you're sure your computer is properly configured, you might want to consider running a firewall, just to protect yourself against inadvertently enabling remote access to something you shouldn't, and accidentally breaking the rules. There are occasions where firewalling yourself can be quite useful, for instance...
[LIST]
[*]You use your computer in more than one location, and want to make different services remotely accessible depending on where you are. Manually reconfiguring things all the time would get tedious very quickly!
[*]Very occasionally, applications come along that are either "on" or "off" ... ie they either bind to every network interface, or none at all. In cases like that, you *need* a firewall to prevent remote users seeing a service you want to be able to access locally.[/LIST]Anyhow, a combination of these two approaches should sort you out.

[LIST=1]
[*]Start by checking what services are remotely accessible.
[*]If you spot one you know you realllly don't want, you can always uninstall it.
[*]Other times, stopping an unwanted application (eg a web server) might be preferable.
[*]Once you're satisfied with how your computer looks to the outside world, give yourself the added protection of a firewall.[/LIST]
I hope that helps.

---

