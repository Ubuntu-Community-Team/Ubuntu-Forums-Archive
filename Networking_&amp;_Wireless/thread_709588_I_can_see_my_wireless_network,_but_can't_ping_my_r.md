---
title: "I can see my wireless network, but can't ping my router?"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by sKuarecircle on 2008-02-27
Hi all , I have scoured the net and these forums looking for an answer but..none.

Sio I have just fininshed installing Ubuntu and have set up my wireless. I use a wireless router in th elounge and a USB wireless adapter on my computer. Ubuntu picks up the wireless network and even connects to it fine....but I am unable to ping the router?

I am at wits end and don't know where to go from here

---

### Post by jan quark on 2008-02-27
do you have access to the internet?
are you perhaps behind a proxy or a filrewall?

---

### Post by sKuarecircle on 2008-02-28
No not at all, internet access I mean. And no firewall, also no encryption on the router, it just simply wont let me ping it, I have a dual boot system and from windows everything works fine, but on Ubuntu I don't have access? I have a feeling I am missing on small litlle thing which is causing the whole bugger up.

---

### Post by superprash2003 on 2008-02-28
go to system->administration->network->look for your wireless ethernet card and click on properties.. change it from roaming to DHCP.. and try.. if that doesnt work.. go to the terminal type ifconfig and post results here!!

---

### Post by sKuarecircle on 2008-02-28
Ok, its all been sorted, could someone tell me how to mark this thread as solved.

Firstky thank you so much guys for you rquick responses, it is amazing to be part of such a helpful community and makes the change from Windows to Ubuntu so so much easier and fun. Coll enough emotional drivel.

The problem was this:

I had an adsl router connected to a lynksis router through which I was connection to the internet via windows. In Ubuntu it would not work though even though it picked up the wireless network.

To remedy this all I did was take away one router, don't need two in any case. Ubuntu without a whimper or a snigger promptly picked up the network and the router without any input from me, which means that this would have worked straight away from installation. let me tell you I am well impressed.

So basically it was my own foolhardiness that caused the problem and not Ubuntu at all.

If someone else reads this thread an dwould like more specif explanations on as to how I fixed it please post and I will help you out.

---

