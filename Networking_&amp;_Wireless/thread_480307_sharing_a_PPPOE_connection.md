---
title: "sharing a PPPOE connection"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by shachtal on 2007-06-21
the situation is so

i have the main desktop computer, running dual boot (feisty and xp)  that connects using PPPOE to the internet

the connection is just fine.

i have another computer running vista and ubuntu

the two of them are connected together in a network using the second ehternet card i have on the main computer

when the main computer runs win XP i have no problem. everything works smooth including the internet connection on both computers
its just a simple matter of rightclicking the pppoe dialer and clicking the "share connection" box

when the main computer runs ubuntu however, i have no idea how to "share" the internet connection with the second computer.
i looked and looked and didn't find even one guide that shows how this could be done.
this is very frustrating for me. because it seems as if in windows its the most simple thing, and on ubuntu on the other hand its near imposible.

i'll be glad to find an answer to this

thanks a bunch
tal

---

### Post by shachtal on 2007-06-24
come on people.....

you mean to tell me that no one ever got stumbled in this same problem?

many people use adsl pppoe connections, you mean to tell me, non of them ever tried to share it with ubuntu?

---

### Post by koutsonik on 2007-06-24
Have you tried sudo -s pppoeconf and after that  pon dsl-provider

---

### Post by boteeka on 2007-08-19
Does the internet connection actually work on the Ubuntu machine?

I'm asking because I am in a similar situation, and I managed to set up the internet connection through pppoe, but I can't share it.

I would be interested in the sharing part too.

---

### Post by isharra on 2007-09-23
Setting up a connection and sharing it are very different matters. There is not (currently) a single gui that combines the two functions.
[pppoeconf]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#modems") is currently recommended as the means of configuring a pppoe connection.

You share the connection by configuring firewall rules which allow the traffic. You can do this manually or use a tool to set it up for you. 
[ Firestarter]("https://help.ubuntu.com/7.04/internet/C/networking.html#networking-firestarter") from the Universe repository is such a tool and handles the case of one adapter for internet access and a different adapter for all internal access very well. (It does not handle multiple internal adapters though.)

---

