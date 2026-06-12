---
title: "Assigning domain name to localhost"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by thepopasmurf on 2008-09-29
I set up the MoinMoin desktop wiki for my computer and it's address is *localhost:8080* . This is fine for me but I want to put in on a friends computer and I don't think they'll remember it, is there a way to assign a domain name to this local address which the user can just type into their address bar eg. MyWiki ?

---

### Post by jerome1232 on 2008-09-29
Ubuntu automatically assigns the computers hostname and 'localhost' as loopback names.

To assign names the easiest way is to edit the hosts file, on Ubuntu it's located at /etc/hosts on windows vista and xp it's located at c:\windows\system32\drivers\etc\hosts and can be edited with a text editor just like on linux
an example of mine (localhost and lifebane refer to my own machine) the ipv6 stuff you don't have to worry about. Any address between 127.0.0.1 and 127.255.255.254 refers to your own machine.

```
127.0.0.1 localhost
127.0.1.1 lifebane

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by cariboo on 2008-09-29
Go to:

[http://www.no-ip.com/](http://www.no-ip.com/)

Select no-ip free and setup an account, then forward port 8080 on your router from the computer with the web site on it. You can select a domain name while you are setting up your free account.

Jim

---

### Post by jerome1232 on 2008-09-29
If you are actually hosting this service on your computer then you can completely ignore what I posted, I was thinking your were installing the program on your friends computer.

---

### Post by thepopasmurf on 2008-09-29
> If you are actually hosting this service on your computer then you can completely ignore what I posted, I was thinking your were installing the program on your friends computer.

No I'm not hosting it on my computer. It's all standalone on each computer. It just needs to run through the browser though

---

### Post by jerome1232 on 2008-09-29
Then in that case editing the hosts file will do the trick :)
add an entry like
127.0.1.2 mywiki

---

### Post by thepopasmurf on 2008-10-01
It didn't work, my file looks like this
```

127.0.0.1 localhost swiki
127.0.1.1 andrew-laptop
127.0.0.1:8080 mywiki

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

the address for the wiki (as I put into the browser) is 127.0.0.1:8080

---

### Post by jerome1232 on 2008-10-01
make it


127.0.1.2:8080 mywiki

remember any address between 127.0.0.0 - 127.255.255.255 refers to your machine (try entering the example ip i gave you it'll work) and I don't think you can define the same ip twice I could be wrong though.


and make sure you dns cache is flushed (I don't remember what the command is but a restart will get it done)

---

### Post by Iowan on 2008-10-01
> **jerome1232 said:**
> I don't think you can define the same ip twice I could be wrong though. You *might* be able to use multiple aliases for the same address (dunno for sure), but I doubt you can alias a specific port.  **man hosts** would have more details.

---

