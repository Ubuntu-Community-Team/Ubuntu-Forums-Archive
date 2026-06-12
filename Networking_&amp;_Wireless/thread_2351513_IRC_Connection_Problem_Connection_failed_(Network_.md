---
title: "IRC Connection Problem: Connection failed (Network is unreachable)"
date: 2017-02-04
forum: Networking &amp; Wireless
---

### Post by sarpim on 2017-02-04
Hello,

I am unable to connect to any IRC servers. I have tried different ports, but that does not seem to be the issue. I have also checked in with my network provider, and they told me that they were not blocking it either. I am using HexChat, but a few other clients also did not work. I am currently running Ubuntu 16.04 LTS. I am new to the forums so I would be grateful if you could advise me for collecting further info/seeking help somewhere more appropriate if that is the case.

Thank you

---

### Post by howefield on 2017-02-04
Which IRC network are you trying to connect to ?

---

### Post by sarpim on 2017-02-04
Thanks for your reply! 

I am trying to connect to freenode, by directing my client to chat.freenode.net

---

### Post by sarpim on 2017-02-07
Just to add: my internet connection otherwise is fine. It's only IRC networks that I cannot connect to.

---

### Post by QIII on 2017-02-07
When you try to connect and it fails, what messages are returned by hexchat?

Please paste the exact text.

---

### Post by sarpim on 2017-02-09
Thanks for the reply. I am beginning to think that IRC may be blocked by my ISP (I am on a campus), but the support people tell me that they don't know of such a block. Here is what I get:
```
 Looking up chat.freenode.net
* Connecting to chat.freenode.net (64.86.243.181:6661)
* Connection failed (Network is unreachable)
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (195.154.200.232:6660)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (195.154.200.232:6697)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:8000)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (195.154.200.232:8001)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:6668)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up irc.freenode.net
* Connecting to chat.freenode.net (173.230.128.213:6667)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:6669)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:7000)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:6666)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:6665)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (91.217.189.42:6664)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (91.217.189.42:6663)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (91.217.189.42:6662)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (195.154.200.232:6661)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (94.125.182.252:6660)
* Connection failed (Network is unreachable)
 Cycling to next server in Ubuntu Servers (freenode)...
* Disconnected ()
* Looking up chat.freenode.net
* Connecting to chat.freenode.net (195.154.200.232:6697)
* Connection failed (Network is unreachable)
```

---

### Post by howefield on 2017-02-09
Please use code tags rather than quote tags when posting terminal output or similar.

Can you get to [https://webchat.freenode.net/](https://webchat.freenode.net/) and join a channel using a web browser ?

Or ping chat.freenode.net.. what's the response ?

```
ping -c 4 chat.freenode.net
```

---

