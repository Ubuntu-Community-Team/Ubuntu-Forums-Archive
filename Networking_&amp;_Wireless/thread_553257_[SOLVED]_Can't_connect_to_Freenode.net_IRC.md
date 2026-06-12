---
title: "[SOLVED] Can't connect to Freenode.net IRC"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-09-17
I have never been able to connect to freenode.net's IRC, but I don't know where the problem is. How do I troubleshoot?

Note: I don't really know what I'm doing, but here's a successful scan of dal.net (an IRC server I *can* use:
```
$ nmap swiftco.wa.us.dal.net -p 6667 -P0

Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-17 15:38 EDT
Interesting ports on 208.99.193.130:
PORT     STATE SERVICE
6667/tcp open  irc

Nmap finished: 1 IP address (1 host up) scanned in 0.152 seconds


```

And here's a failed scan of freenode.net:
```
$ nmap chat.freenode.net -p 6667 -P0

Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-17 15:38 EDT
Warning: Hostname chat.freenode.net resolves to 10 IPs. Using 64.161.255.20.
Interesting ports on 64.161.255.20:
PORT     STATE  SERVICE
6667/tcp closed irc

Nmap finished: 1 IP address (1 host up) scanned in 0.730 seconds
```

Does this tell me anything as to the source of the problem?

If this isn't a good way to troubleshoot, please tell me how to do so...

Thanks,
Jamie

---

### Post by noob12 on 2007-09-17
```

host chat.freenode.net

```

will give you a list of IPs you can try individually.  Closed port bad.  Open port good. :-)

---

### Post by gautada on 2007-09-17
Maybe you ISP is blocking IRC?

---

### Post by Jamie Jackson on 2007-09-17
> **noob12 said:**
> ```

host chat.freenode.net

```

will give you a list of IPs you can try individually.  Closed port bad.  Open port good. :-)

Thanks, "host" is a new one to me. I tried a few of those, and the result is the same each time.

However, I'm wondering what a networking guru would do to pinpoint the problem. I often have the question of whether there's a firewall (corporate, I've got no rights to it) problem or if the server is simply refusing (or has a closed connection).

I just tried an online port scanner:
```
Scanning ports on 82.96.64.4 (kornbluth.freenode.net)
82.96.64.4 is responding on port 6667 (ircd).
```

Does this, in combination with the freenode nmap (above) tell me definitively that my firewall is to blame?

I'd like to be able to do this kind of diagnosis in the future, when this type of issue comes up again.

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-09-17
> **gautada said:**
> Maybe you ISP is blocking IRC?

Blocking freenode in particular? I don't know, but it seems unlikely considering I can IRC through dal.net (as noted in the original post).

---

### Post by noob12 on 2007-09-17
Looks like something between your current location and that site because nmap from my home server shows 6667 open on 82.96.64.4.

---

### Post by kevdog on 2007-09-17
I use xchat as the irc client -- just thought I would throw this into the ring, although it sounds like you want to make a command line connection, which I cant help you with

---

### Post by Jamie Jackson on 2007-09-18
> **kevdog said:**
> I use xchat as the irc client -- just thought I would throw this into the ring, although it sounds like you want to make a command line connection, which I cant help you with

Thanks for the suggestion. I was using the command line to rule out any client config problems, but I'm pretty committed to Pidgin, because it handles (mostly) all protocols in one client. (MS LCS support is [coming soon]("http://developer.pidgin.im/ticket/48") too, so hopefully, coworkers won't be annoyed that I'm offline in MS Communicator all the time.)

---

### Post by Jamie Jackson on 2007-09-18
I'm pretty sure my corporate firewall has freenode blacklisted, as I can connect to dal.net from there, but not freenode. 

I can connect to both from home.

Marking as solved...

---

