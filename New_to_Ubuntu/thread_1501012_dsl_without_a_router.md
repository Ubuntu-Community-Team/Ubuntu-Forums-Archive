---
title: "dsl without a router"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by senorian on 2010-06-03
(ubuntu 10.04. )
Having lost my router I attempted to connect (directly to the dsl modem) to the internet and failed.
I have a book
Ubuntu Linux Desktop by Ric Shreves 
pub.visual.
He has 4 pages indexed as either "network connections" or "network tools" (pp.110-115)
However it does not seem to help me, possibly as I do not understand how to use the network tools he names.
Is there a tutorial, or a book, that explains in detail the steps to connect directly to the dsl modem?
tia

---

### Post by Autodave on 2010-06-03
> **senorian said:**
> (ubuntu 10.04. )
Having lost my router I attempted to connect (directly to the dsl modem) to the internet and failed.
I have a book
Ubuntu Linux Desktop by Ric Shreves 
pub.visual.
He has 4 pages indexed as either "network connections" or "network tools" (pp.110-115)
However it does not seem to help me, possibly as I do not understand how to use the network tools he names.
Is there a tutorial, or a book, that explains in detail the steps to connect directly to the dsl modem?
tia

There would be no difference to either connecting to a router or just connecting directly to the DSL modem.  Just attach your ethernet cable from the modem to your computer.  You will probably see a notification in the top right corner saying that you are connected.  If not, then go to System > Preferneces > Network connections.  Click on the WIRED taB and see if it lists it there.  If not, click on ADD and it should appear.  Just confirm the add then.

---

### Post by arsenic23 on 2010-06-03
Well depending on your dsl modem you may not need to do anything.

Assuming your router was handling your PPPoe connection all you have to do is log into your modem and set it to do it.  If it's already set this way it should just work when you plug it in, if not just lookup configuring your particular modem.  Your DSL company can more then likely help you out if you ask, but you may just end up confusing whoever is running their support.

---

### Post by lkraemer on 2010-06-04
System > Preferences > Network connections. Click on the WIRED Tab and see if Roaming is checked. If not, set the connection for Roaming.....

lk

---

### Post by senorian on 2010-06-05
Thanks for the advice
I just bought a new cisco WRT 120 N router ($60 can)
lkraemer
I could not find "roaming"

arsenic23
"...but you may just end up confusing whoever is running their support." 
The first guy that answered gave up when I said that I was using Linux!
Thanks to all

---

