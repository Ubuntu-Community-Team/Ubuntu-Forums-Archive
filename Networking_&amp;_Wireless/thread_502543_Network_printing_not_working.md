---
title: "Network printing not working"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by jackn on 2007-07-16
OK, followed [this clear and concise how-to]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") in the Ubuntu Wiki in order to get network printing working.

Everything looks good. Both my server marchine and my client machine show icons with the printer 'ready'.

```
lpstat -d -p 
```

on the client machine gives out this:

```
~$ lpstat -p -d
printer DeskJet-5740 is idle.  enabled since Tue 17 Jul 2007 01:14:41 AM CEST
        Connecting to 192.168.0.1 on port 631...
system default destination: DeskJet-5740

```

Using Feisty Fawn. Printer is HP Deskjet 5740 and works just fine on server machine (a desktop). 

What I cannot do is print to it from my client machine (a laptop).

One more point: [Another post]("http://http://ubuntuforums.org/showthread.php?t=288860") says that some HP printers won't work with the CUPS IPP protocol, and require the jetDirect HP protocol. 
I don't know whether this could be relevant to the above model number. In addition, I wan't able to follow the instructions in that post.

Thanks for your help.

Jackn

---

