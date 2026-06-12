---
title: "avahi vs mdns vs winbind"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by sefs on 2007-04-29
What exactly is avahi/mdns.  has this replaced the need for winbind?

They are not playing nicely together ... if both are running at the same time then samba shares are inaccessible.  If one or the other is running then everhthing is ok. 

Could a person in the know elaborate?

Thanks.

---

### Post by paparucino on 2007-04-30
> **sefs said:**
> What exactly is avahi/mdns.  has this replaced the need for winbind?
They are not playing nicely together ... if both are running at the same time then samba shares are inaccessible.  If one or the other is running then everhthing is ok. 
Could a person in the know elaborate?

```

Avahi is a system which facilitates service discovery on a local network. This means that you can plug your laptop or computer into a network and instantly be able to view other people who you can chat with, find printers to print to or find files being shared.

```
[http://avahi.org/](http://avahi.org/)

```

mDNS (Multicast DNS) Using IP multicast with DNS to provide the capabilities of a DNS server for service discovery in a small network that does not have a DNS server. 

```
[http://www.answers.com/topic/multicast-dns](http://www.answers.com/topic/multicast-dns)

```

winbind is a component of the Samba suite of programs that solves the unified logon problem. Winbind uses a UNIX implementation of Microsoft RPC calls, Pluggable Authentication Modules (PAMs), and the name service switch (NSS) to allow Windows NT domain users to appear and operate as UNIX users on a UNIX machine. 

```
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/winbind.html)



UAResolved

---

### Post by sefs on 2007-05-01
So do I need them both, or can i have avahi take care of what winbind is doing. and get rid of winbind. or vice versa

---

### Post by paparucino on 2007-05-01
> **sefs said:**
> So do I need them both, or can i have avahi take care of what winbind is doing. and get rid of winbind. or vice versa
Avahi should take care of everything

---

### Post by sefs on 2007-05-01
I just realise it sorta does.  interesting.  I can ping the netbios name of the linux machine from windows machines and can access the samba shares from the windows machines but going from linux to windows i can only access the shares on windows, but i cannot ping the windows machines by name.  Is there some sort of setting flag i have to set for that? to ping the windows machines by name?

> **paparucino said:**
> Avahi should take care of everything

---

### Post by eduardoriviera on 2007-05-02
You have to install mdns on the windows boxes too.  You can download bonjour for windows from Apple.  That should do the trick.

---

### Post by sefs on 2007-05-03
Just one other question, with all the mdns installed on all the machines .. This wont swamp the network with multicast traffic will it?

---

### Post by sefs on 2007-05-03
Huston we have lift off :D

Now able to ping in all directions using hostname.local.   But was only able to do this after adjusting the firewall to for mdsn traffic by following this guide....

[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

The only thing now is that the pings are really slow!   Me thinks it must be a slight case of ndiswrapper maybe ...  as seen in this faq ... [http://avahi.org/wiki/Avah4users#FAQ](http://avahi.org/wiki/Avah4users#FAQ)

But what in the world does this mean....
That you disabled all local firewalls (This includes disabling the Firestarter default FW), at least for UDP traffic from and to port 5353   ... does this mean to open port 5353 in the firewall?.

A nice read on mdns  [http://www.net.princeton.edu/filters/mdns.html](http://www.net.princeton.edu/filters/mdns.html)

---

### Post by eduardoriviera on 2007-05-03
I don't have any problems with slow ping times; however, I have never had any success with ndiswrapper.

---

