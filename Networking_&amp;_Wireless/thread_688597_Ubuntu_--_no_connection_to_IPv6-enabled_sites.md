---
title: "Ubuntu -- no connection to IPv6-enabled sites"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by exabyte on 2008-02-05
Hello. I've never used Ubuntu myself, but half of my friends do.
Recently, I've made some of my personal web sites IPv6 enabled. At that moment, some of my friends using Ubuntu claim they cannot access them anymore. It goes that way - I add an AAAA record and their access to my site dies, I remove it, voila, they have access again. So I disabled AAAA records for all my sites and will never enable them again. 

So I start this topic, to
1. See if someone knows what causes the problem (my guess goes that Ubuntu has IPv6 enabled and with no IPv6 connectivity it tries to use IPv6 to connect to those sites and fails)
2. Know for some workaround I can enable on my side... (my guess is that there is none)
3. Someone who has any knowledge about the matter (I don't) will do something to get this fixed. It is very unfortunate that OS like Ubuntu would impede IPv6 adoption like this.

---

### Post by Hightide on 2008-02-05
Hi exabyte

dont know if this helps but I came across this [thread]("http://ubuntuforums.org/showthread.php?t=581055&page=3") discussion on IPv6.

have a look

regards

:)

---

### Post by MJN on 2008-03-08
> **exabyte said:**
>  3. Someone who has any knowledge about the matter (I don't) will do something to get this fixed. It is very unfortunate that OS like Ubuntu would impede IPv6 adoption like this.

Arriving late to the party I know, but in case you're still interested in pursuing this I thought you might wish to know that my site (using Apache on Dapper) is now serving pages with IPv6 so there's nothing 'broken' about Ubuntu per se.

Describe what steps you've taken, and provide the URL so we can test against it.

Mathew

---

