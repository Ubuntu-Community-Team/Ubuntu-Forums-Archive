---
title: "Wireless problems...?"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by CA5UALTY on 2007-12-06
I realize they're various topics about wireless topics and whatnot, but I can't solve this problem... Now, I'm new to this stuff, and not too sure what to do; that's why I'm here...

The Problem: I was on the internet, and all of a sudden...stopped working. I went to google just to see if I did lose connection, and I couldn't get to it. So, I lose my connection, and I saw the wireless networks, and I tried to connect to mine, but it wouldn't connect. Now, I have my desktop computer working through the wireless router, and that works fine, so obviously, my laptop is the problem. After trying to connect to my network numerous times, I didn't see the little icon thing anymore... So, I went to Restricted Drivers Manager and disabled and re-enabled the Broadcom 43xx thing. Whenever I try to complete that task, this message pops up saying something about trying to locate it (CONFUSED!!). It says 'download from link or internet, something like that, and I checked that, but it was invalid. Now, I see the icon again, but I don't see my network, or anyone else's, for that matter... So, I'm very confused here, and in desperate need of help, because I suck at this stuff. Anyway, when I directly connect the wire to my laptop, it works fine. 

Does anyone (please, God) have any idea how to fix this?! 

Sorry for the essay to read.

Thank you...

---

### Post by danielmncastro on 2007-12-06
Try to remove and reload the module:

1) If you use NDISWRAPPER:
```
# rmmod ndiswrapper
# modprobe ndiswrapper
```

2) If you use an native driver. Use the same commands but with the module name. 

It use to work when I lost my connection.

- Daniel

---

### Post by CA5UALTY on 2007-12-06
I don't exactly understand what you told me to do, but I ran the commands in the terminal, and this was the result... "ERROR: MODULE -blah blah- does not exist in /proc/modules" and "FATAL: Error inserting -blah blah blah blah blah- :Operation not permitted." So, this didn't correct the problem, but maybe I did it wrong. Anyway to say that in simpler terms? Or do you, or anyone, have another idea?

---

### Post by rustybronco on 2007-12-06
> **CA5UALTY said:**
> Iso obviously, my laptop is the problem. After trying to connect to my network numerous times, I didn't see the little icon thing anymore... So, I went to Restricted Drivers Manager and disabled and re-enabled the Broadcom 43xx thing. Whenever I try to complete that task, this message pops up saying something about trying to locate it (CONFUSED!!). It says 'download from link or internet, something like that, and I checked that, but it was invalid. Now, I see the icon again, but I don't see my network, or anyone else's, for that matter... So, I'm very confused here, and in desperate need of help, because I suck at this stuff. I don't think anyone that tries to fix something and can't get it to work su*ks, it means they haven't found a way yet. >  Anyway, when I directly connect the wire to my laptop, it works fine. did you try to enable the restricted drivers while cabled to the internet? if not try it. I think this may be why you are getting the "invalid" error. 

> [Does anyone (please, God) have any idea how to fix this?! He does, we on the other hand are human, so it may take a while.

> Sorry for the essay to read. essay? not even close...

---

### Post by rustybronco on 2007-12-06
> **danielmncastro said:**
> Try to remove and reload the module:

1) If you use NDISWRAPPER:
```
# rmmod ndiswrapper
# modprobe ndiswrapper
```

2) If you use an native driver. Use the same commands but with the module name. 

> **CA5UALTY said:**
> I don't exactly understand what you told me to do, but I ran the commands in the terminal, and this was the result... "ERROR: MODULE -blah blah- does not exist in /proc/modules" and "FATAL: Error inserting -blah blah blah blah blah- :Operation not permitted." So, this didn't correct the problem, but maybe I did it wrong. Anyway to say that in simpler terms? Or do you, or anyone, have another idea? rm= remove, mod=module, modprobe=add module into kernel,  ndiswrapper= well you get that one, broadcom module=bcm43xx or something like that...

---

### Post by CA5UALTY on 2007-12-06
> I don't think anyone that tries to fix something and can't get it to work su*ks, it means they haven't found a way yet. 

That's true, thank you.

> did you try to enable the restricted drivers while cabled to the internet? if not try it. I think this may be why you are getting the "invalid" error.


Yeah, I just tried that now, and it didn't work; I'm still getting the same thing.


> He does, we on the other hand are human, so it may take a while.


Ha ha, I only wish he registered on Ubuntu Forums. 


> essay? not even close...

Yeah, I noticed that after I posted it. When I was typing it in the tiny box, it appeared long, but when I looked at it, without previewing it before I posted, it was barely even a paragraph. =P

---

### Post by CA5UALTY on 2007-12-06
> **rustybronco said:**
> rm= remove, mod=module, modprobe=add module into kernel,  ndiswrapper= well you get that one, broadcom module=bcm43xx or something like that...

Ah, thank you. I had no idea what that meant, whatsoever... Even so, I tried what you guys said, and still nothing. If you got anymore, keep 'em coming! I appreciate the helping, too!

---

### Post by rustybronco on 2007-12-06
> **CA5UALTY said:**
> I realize they're various topics about wireless topics and whatnot, but I can't solve this problem... Now, I'm new to this stuff, and not too sure what to do; that's why I'm here...

The Problem: I was on the internet, and all of a sudden...stopped working. I went to google just to see if I did lose connection, and I couldn't get to it. So, I lose my connection, and I saw the wireless networks, and I tried to connect to mine, but it wouldn't connect. Now, I have my desktop computer working through the wireless router, and that works fine, so obviously, my laptop is the problem. After trying to connect to my network numerous times, I didn't see the little icon thing anymore... 
(please, God) have [you] any idea how to fix this?! 
Thank you... take a look at my signature, in it is a trouble shooting guide written by Kevdog, in this guide you will find a section on how to connect from the command line.
help your self learn, and ask questions.
what kind of wireless n.i.c (network interface card) do you have? internal, pcmcia (cardbus), usb ect...

---

