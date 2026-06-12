---
title: "configuring a proxy"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by muddymind on 2007-08-01
Hi!

To configure my proxy I went to System->'Preferences'->Network proxy and I filled the address, port, username and password... But when I try to use apt it gives me an error saying ta ISA server requires authentication... 

I saw a workaround which was editing apt.conf in /etc and write this:
```
Acquire
{
http::proxy "http://username:password@proxy:port/"
}
```
But I can't use this cuz any user could see the contents of the file and would create a security issue... Is there any other way of doing it?

---

### Post by chewearn on 2007-08-01
You can add the proxy into Synaptic:
Menu > Settings > Preferences > Network tab

---

### Post by muddymind on 2007-08-01
well... that simply didn't work...

I put the proxy address in the ubuntu proxy network and it isn't affecting anything... even gaim doesn't work... 

The only thing that I managed to enable was firefox that have it's own proxy manager... 

I've tried the method that I discribed in the 1st post but that didn't work either... It always give me an error saying that it couldn't authenticate to ISA server...

I'm going nuts with this... my superior doesn't stop arguing negative stuff about linux and this isn't helping... :(

PLZ HELP!!!

---

### Post by muddymind on 2007-08-01
BTW.. I need to set a global proxy and not application specific cuz I need to manage internet permisions for different users...

[]

---

### Post by chewearn on 2007-08-01
I'm sorry to say, this has gone beyond my limited knowledge in this area. Unfortunately, I'm not familiar with ISA server, or setting up for multiple users.  Hope someone else in the forum has an idea what to do next.

---

### Post by muddymind on 2007-08-01
> **AstalaVista said:**
> I'm sorry to say, this has gone beyond my limited knowledge in this area. Unfortunately, I'm not familiar with ISA server, or setting up for multiple users.  Hope someone else in the forum has an idea what to do next.

thank you anyway :)

I'll continue my struggle to dominate it  ](*,)

---

### Post by muddymind on 2007-08-01
Now I have another problem... I installed ntlmaps and now I have access to the internet with firefox without set a proxy but apt continues to not work ](*,)

To make things worse if I set the ip manually and then make ifconfig, it says that eth0 doesn't have an ip... WTF!?!?!? is this really a linux for human beings?!?!? [-(

---

