---
title: "Why still receiving bytes?"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by D1Knight on 2009-11-08
[COLOR=Purple]**OK, in system monitor I am showing that I am receiving bytes. :confused:Why? :-?I am not downloading anything and I don't use P2P.**[/COLOR] **[COLOR=Purple];)Thanks for any help.P.[/COLOR]**:D

---

### Post by lavinog on 2009-11-08
do you have any other network devices?
There are numerous things that can go on in the background such as dns queries, updates, scanning for network shares, synchronizing clocks...etc

I wouldn't worry about bytes so much...kilobytes would be more significant, but still could be a background process.

iptraf can show you more details.

---

### Post by D1Knight on 2009-11-08
> **lavinog said:**
> do you have any other network devices?
There are numerous things that can go on in the background such as dns queries, updates, scanning for network shares, synchronizing clocks...etc

I wouldn't worry about bytes so much...kilobytes would be more significant, but still could be a background process.

iptraf can show you more details.

[COLOR=Purple]**Lavinog, no I do not have any other network devices attached**[/COLOR]**[COLOR=Purple]. Nothing updating.  Thanks for your response.:D[/COLOR]**

[COLOR=Purple]**Background process? Something calling home?**[/COLOR]

---

### Post by akudewan on 2009-11-08
Usually its just some harmless process, like a weather applet or clock trying to update. I've noticed that peers try to connect to me even though I have quit a p2p or bittorrent program. These connections are just rejected by the OS.

Here are some ways you can find out whats going on:
1) run: [FONT="Courier New"]sudo lsof -Pni[/FONT] to see what programs are listening on which ports. Its likely that some of these may be sending/receiving data. (Edit: this will show local processes as well)

2) You can install a program called nethogs (sudo apt-get install nethogs). This program shows you the programs using your bandwidth in real-time.

3) several other programs like iptraf, wireshark, netstat can show details of whats going on. You can explore these if you're interested.

---

### Post by pootan on 2009-11-08
If its only small bumps of bytes in Network History then it is most likely loopback to your router.

---

### Post by D1Knight on 2009-11-08
> **akudewan said:**
> Usually its just some harmless process, like a weather applet or clock trying to update. I've noticed that peers try to connect to me even though I have quit a p2p or bittorrent program. These connections are just rejected by the OS.

Here are some ways you can find out whats going on:
1) run: [FONT=Courier New]sudo lsof -Pni[/FONT] to see what programs are listening on which ports. Its likely that some of these may be sending/receiving data. (Edit: this will show local processes as well)

2) You can install a program called nethogs (sudo apt-get install nethogs). This program shows you the programs using your bandwidth in real-time.

3) several other programs like iptraf, wireshark, netstat can show details of whats going on. You can explore these if you're interested.

Akudewan, wow thanks. :DThis looks like some good useful information, worth checking into.  I very much appreciate you and your response. P.

---

### Post by D1Knight on 2009-11-08
> **pootan said:**
> If its only small bumps of bytes in Network History then it is most likely loopback to your router.

Pootan, yeah I am receiving about 57/bytes every other second. A loopback to router, interesting. :-k I thank you kindly for your response.:D

---

### Post by The Cog on 2009-11-08
There is a constant background noise of packets on the internet. What you are seeing isn't a great amount and is probably just a combination of mis-addressed packets and bots scanning for vulnerable hosts. As long as you are not running any services that accept incoming connections then thsi burble is nothing to worry about.

---

### Post by Somme on 2009-11-08
0 bytes would mean that you are disconnected - as long as you are connected, you send/receive something ( yes, even if there are no running applets or whatsoever ).

---

### Post by D1Knight on 2009-11-08
> **The Cog said:**
> There is a constant background noise of packets on the internet. What you are seeing isn't a great amount and is probably just a combination of mis-addressed packets and bots scanning for vulnerable hosts. As long as you are not running any services that accept incoming connections then thsi burble is nothing to worry about.

The Cog, thank you for your response.:) That does help to shed some light on my question.

---

### Post by D1Knight on 2009-11-08
> **Somme said:**
> 0 bytes would mean that you are disconnected - as long as you are connected, you send/receive something ( yes, even if there are no running applets or whatsoever ).

Thank you. Good to know.:)

---

