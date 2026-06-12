---
title: "Constant Disconnecting"
date: 2010-07-21
forum: New to Ubuntu
---

### Post by iCurtiee on 2010-07-21
Okay, I've got a problem with my connection, which I do believe is a problem to do with Ubuntu, due to the fact that my mum's laptop (which runs 7) doesn't disconnect from the internet.

The problem has started since a power cut about a week or so ago. I can just be happily browsing and then the internet will disconnect, which doesn't want to connect without me restarting/putting my laptop to sleep, which can get tiresome when I am doing it every five minutes.

I run Ubuntu 10.04 Lucid Lynx, on an Acer Aspire 5315. I do not dual boot, this laptop is completely Linux/Ubuntu.

My ISP is Talk Talk (I know...) and I have a Broadcom wireless card for which I have the drivers installed.

Many thanks in advance.

---

### Post by gvoima on 2010-07-21
I suggest that you try connecting a cable to the router, that way if it works, we can somewhat limit the fault to your wifi.
And start from there to try solving it. If there was a power failure, there is a slight possibility that it is broken.

---

### Post by iCurtiee on 2010-07-21
Okay, I'm all hooked up with wires, and I've browsed a bit, opened lots of pages at once, no problem with it at all, which makes me pretty damn certain it is something to do with the WiFi.

---

### Post by iCurtiee on 2010-07-21
Apologies for the double post, but haven't had a reply.

I've been browsing for about 15 minutes now and not had one disconnect :O

---

### Post by iCurtiee on 2010-07-21
Again, apologies for (what is now) a triple post. 

Does anyone have an idea what could be causing it to disconnect so much when connected wirelessly?

---

### Post by dca on 2010-07-21
If problem doesn't exist in Win7, two culprits are either the drivers used:  if it's Broadcom, then perhaps native b43, bxx, bwhatever module is incorrect, or if you're using ndiswrapper w/ Windows Broadcom driver may be issue...  Second, could be network-manager may be the problem as well...  You can try using WICD instead and see if the problem persists...

---

### Post by iCurtiee on 2010-07-21
I'll give WICD a try and report back shortly.

Thanks :]

---

### Post by iCurtiee on 2010-07-21
I've tried WICD, and it's running alongside network-manager, not doing much, really. 

I have tried to connect with it, but every time, it just told me 'bad password', despite the security key (and type) being correct. 

Anyone else got any ideas? ):

---

### Post by gvoima on 2010-07-22
Well the router could also be the culprit if you had a power failure and you are certain that it started after that. Is it possible for you to test it with another router with the same encryption?

---

