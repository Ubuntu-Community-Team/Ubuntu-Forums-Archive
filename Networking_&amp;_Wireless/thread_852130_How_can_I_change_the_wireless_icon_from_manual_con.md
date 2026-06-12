---
title: "How can I change the wireless icon from manual configuration to automatic config?"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by cmpunk on 2008-07-07
I was playing around with my wireless connection icon on my toolbar, and i accidentally changed it to manual configuration and now instead of seeing how many bars I have, i only see the network icon. and also, when i want to search for a wireless connection on the go, instead of just left-clicking and showing me all the connections in range, i have to manually type it in.

How do I change it back to the automatic configuration?

btw, my internet still works.

---

### Post by tuxneo on 2008-07-07
Hi, 
if I well understood, the automatic config works well for you. Else, tell it :)
So, you just have to go to the manual config (system => administration => network), then choose your wireless interface and to turn on "enable roaming mode".
That's all ;)

ps : sorry, i'm french, i got a bad english

---

### Post by cmpunk on 2008-07-07
well, it went back to normal, but the internet wouldnt work anymore (even when I restarted the computer). i had to change it back to the manual config for it to work.

Is there a way to fix this problem?

---

### Post by tuxneo on 2008-07-07
Did the internet work before you play around (also, with a automatic config) ?

And did you reconfig the network with the auto config (i mean, select the network, enter the password, ...) ?

---

### Post by cmpunk on 2008-07-07
No, it stopped working. Here's how it happened:

My computer was on standby, so i opened it, but for some reason, it didnt tell me to put in my username and password, so i opened up firefox. But all of a sudden right when i click firefox, my computer reboot, and rebooted again, so i turned it off. then when i opened it back up, it started up, but the internet wasnt working, it was telling me that the internet was connected, but it wasnt working. so i played around with it for an hour or two and i guess i turned off roaming and it worked, but now i cant find other networks with manual configuration. so now i cant connect to other connections if i want to bring my laptop with me somewhere else.

Can you still help me fix this?

---

### Post by pez6_9 on 2008-07-07
You should just be able to change into roaming mode in the preferences of your wireless connection, then when you click on the network icon, you will get different ESSID's and have to enter a passphrase/net key. select the type of security you use, enter your password/key, click connect and that should be it

---

### Post by tuxneo on 2008-07-07
Yes, but the auto config seems to bug with the home (I presume ?) network...

So, if the auto config doesn't work at all when you're at home, you can use the manual and switch to the auto when you're moving, then you can see others networks. Then come back to manual when returning to home, to prevent laptop bug (is this sentence correct ? :s )

I don't have ideas to fix your bug , but i'll search ;)

---

### Post by damis648 on 2008-07-07
What is the model of your card?

---

### Post by cmpunk on 2008-07-07
> **damis648 said:**
> What is the model of your card?
how do i check?

---

### Post by tuxneo on 2008-07-07
> **cmpunk said:**
> how do i check?
With lshw (in a terminal) or with sysinfo (it's a program, you may need to install it first)

---

### Post by cmpunk on 2008-07-07
I'm pretty sure its one of these (I looked in sysinfo):

Network Controller:
Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
Subsystem: Intel Corporation Unknown device 1000

---

