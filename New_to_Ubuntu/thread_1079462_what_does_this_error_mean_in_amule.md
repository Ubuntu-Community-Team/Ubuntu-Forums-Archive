---
title: "what does this error mean in amule???"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by manuvaidya on 2009-02-24
when i try to connect to amule, this error message occurs.... i have only few servers.... in that i can only able to connect to usenext... which gives this error.... 


2009-02-24 22:57:48: WARNING: You have received Low-ID!
2009-02-24 22:57:48: 	Most likely this is because you're behind a firewall or router.
2009-02-24 22:57:48: 	For more information, please refer to [http://wiki.amule.org](http://wiki.amule.org)


is there anyway i can make this software function properly without any problem??? or can anyone tell me any other alternative software in ubuntu for amule???? i searched the whole internet desperately.... but no answer...

pls help me....

---

### Post by taurus on 2009-02-24
It means that you are probably either behind a firewall or your router is blocking your ports.

Is your computer connected to a router?

---

### Post by binbash on 2009-02-24
Be sure you open your ports

---

### Post by Michael.Godawski on 2009-02-24
hi,

you can install firestarter
and open the needed ports, which by default should be 4662,4665 (TCP) and 4672 (UDP).

Perhaps you have to forward the ports to your router too.

---

### Post by Festor on 2009-05-27
See this [http://www.amule.org/amule/index.php?topic=16836.0](http://www.amule.org/amule/index.php?topic=16836.0)

And this: [https://bugs.launchpad.net/ubuntu/+source/app-install-data-ubuntu/+bug/368580](https://bugs.launchpad.net/ubuntu/+source/app-install-data-ubuntu/+bug/368580)

---

### Post by youngmix on 2010-07-07
It means that, for some reason, your port is being blocked or is being redirected while attempting connections. The reasons can range from your firewall blocking it, to your router redirecting or blocking it, to your ISP blocking it (apparently it happens), to the server you're trying to connect to being down (rare). 

In amule, go to the Preferences.
When in Preferences, click on the "Connection" tab. It will be under the "General" tab.
You should now see, "Standard client TCP Port:" and "Extended client UDP Port" on the top-right side of the Preferences window.
Change your Standard and Extended Ports to another number; for example, 5030 for your Standard Port and 5040 for your Extended Port.

It should work. The wiki page for amule explains how this works and how to change, but not why you should. Let us know if it works.

---

