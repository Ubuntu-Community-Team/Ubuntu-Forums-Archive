---
title: "XChat not connecting to Ubuntu chat"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by nlsthzn on 2010-10-13
Greetings,

Running Ubuntu 10.04 and installed XChat from USC (XChat 2.8.6) and I have been unable to connect to Ubuntu chat...

It tries to connect to [I]Looking up irc.ubuntu.com
* Connecting to chat.freenode.net (140.211.166.3) port 8001...[/I] however I get the error message *Connection failed. Error: Network is unreachable* (This is from the network list when I start up XChat)

I read somewhere on ubuntu.com that the IRC channel for Ubuntu is chat.ubuntu.com and not irc.ubuntu.com but I am not sure how to change this (and even if I should)...

Yes, I gave been using the Internet since around 1996 and I think in all that time I used IRC twice :(

*edit: I am able to connect to other chats...*

Neil

---

### Post by nlsthzn on 2010-10-20
[S]Hmmm... I guess about a week is enough time to wait before I BUMP this question :(

BTW, I can connect to the debian chat server (which doesn't use freenode) and connects through port 6667... X-Chat wants to connect via port 8001 when I try to connect to freenode...

How can I verify which ports are open? (Not blocked by my ISP)[/S]

Wow... got it to work... removed the /8001 from the server name and it connected via 6667... lol, I am such a noob sometimes

---

### Post by Elfy on 2010-10-20
A week is long enough ;)

Try irc.freenode.net

[https://help.ubuntu.com/community/XChatHowto#Configuration](https://help.ubuntu.com/community/XChatHowto#Configuration)

You can change the port if needed 

irc.freenode.net/6667 I would assume

---

