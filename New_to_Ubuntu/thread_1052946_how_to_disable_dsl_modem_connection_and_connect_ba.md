---
title: "how to disable dsl modem connection and connect back using cable from router"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Nell on 2009-01-28
hi,
I have dsl modem using ibrust technology.

I couldn't connect to internet directly from modem when i first installed ubuntu. So, i hooked up the cable from modem to router then from router to my PC. Afterthat,I was able to connect to internet.

I wanted to connect from dsl modem directly without router since I'm the only one using it. So, that I downloaded and installed Ib_driver and configure pppoeconf from terminal. After that I'm able to connect to internet directly from the modem.

Now, I want to connect both my laptop and PC to internet, so i have to use router. But now i couldn't get internet connection via router anymore.

What should I do to be able to connect to internet using router like before I installed ib_driver and configure pppoeconf?

---

### Post by Nell on 2009-01-28
I've solved it accidentally:o, here's what i did:
-go to network manager (system>administration>network)
-unlock and enable "wired connection" >properties >change connection setting to DHCP > ok 
-click DNS tab > add router ip address in DNS server (the address can be obtain from typing "sudo ifconfig" in terminal. the address is the number beside "inet addr" under "eth0" ; this detail might help if you don't know know anything about configuring internet connection like me;))

thanks a lot to LeAstraler,jcmorris,coolbhavi,forestpixies who have tried to help me out in ##beginners-help  (sorry if i misspell your names here, I couldn't remember how to spell them by now) :KS

---

### Post by Elfy on 2009-01-28
I'll pass it on :)

Glad you're sorted out ok now.

---

### Post by LeAstrale on 2009-01-28
Thank you for the credits, lets hope that next time we will actually be able to solve your problem ;)

/LeAstrale

---

### Post by lazyart on 2009-01-28
I would add that leaving the router in place is a better way to go.  It's an extra layer of protection, and whenever someone visits they can connect without issue.

---

### Post by Nell on 2009-01-29
> **lazyart said:**
> I would add that leaving the router in place is a better way to go.  It's an extra layer of protection, and whenever someone visits they can connect without issue.

Yup..ok..I've learnt from my mistake now:)

---

