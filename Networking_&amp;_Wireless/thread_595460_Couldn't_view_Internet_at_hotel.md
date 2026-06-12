---
title: "Couldn't view Internet at hotel"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by itsacoaster on 2007-10-28
Hello everyone.  I have searched and I could not find a solution, so I'm posting this.

I was inconvenienced by Ubuntu last night, as I could connect to the hotel's network, but I could not access any websites or do anything like that, either wirelessly or via a wired connection.

I'm using Ubuntu Gutsy.

Here's what I know.  (I'm not at the hotel now--I'm hoping that someone knows offhand what was going on.)

-The router gave me an IP address.
-DNS IPs were listed.  (connected via DHCP)
-Could ping router
-Could not ping any external IPs (I tried Ubuntu.com's IP)

Is there anything else you would need to know to help me?

I appreciate any help you can give.

---

### Post by kevdog on 2007-10-28
Sometimes hotels and other public places you have to click a terms of aggreement in the browser to connect. I know in chili hotspot you could set this up.  Did the hotel help mention this at all.

---

### Post by itsacoaster on 2007-10-28
Nope, it was supposed to connect right away.  And I didn't get one of these screens.

---

### Post by kevdog on 2007-10-28
Did you check route -n to see if the universal gateway parameter was correct?

---

### Post by itsacoaster on 2007-10-28
Unfortunately I didn't.  
(I would have tried it if I had an Internet connection to look for connection guides.)

What would I look for, if I used it?

---

### Post by adamos on 2007-10-28
I carried my laptop in one of the hotels that i went recently and they advertised wireless internet connection. they didnt mention that i had to pay 10 bucks to connect :) i dont think so that it was free internet connection! if you couldnt ping outside ips then this is what happened, you should pay :p

my .02

adam

---

### Post by kevdog on 2007-10-28
Here is my route statement:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0

Notice the last line UG is the universal gateway.  Its set to my route (as are most home networks).  You need to make sure that the UG is set #1, and that the address is correct.  WIth multiple routers it might not always be the router you are connected to.

---

### Post by itsacoaster on 2007-10-28
> **adamos said:**
> I carried my laptop in one of the hotels that i went recently and they advertised wireless internet connection. they didnt mention that i had to pay 10 bucks to connect :) i dont think so that it was free internet connection! if you couldnt ping outside ips then this is what happened, you should pay :p

my .02

adam

Heh, I wish it were that simple.  I assure you it was free. ^_^

> **kevdog said:**
> Here is my route statement:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 ath0

Notice the last line UG is the universal gateway.  Its set to my route (as are most home networks).  You need to make sure that the UG is set #1, and that the address is correct.  WIth multiple routers it might not always be the router you are connected to.

All right, that makes sense.  Thank you so much for your  help!

---

