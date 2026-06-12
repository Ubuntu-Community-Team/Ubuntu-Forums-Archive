---
title: "IP Static or Dynamic?"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Kafubie on 2010-01-15
**_Hello Ubuntu forums members_!**
This is my first time on the forums, and I have a "noob" question to ask. :popcorn:

I've been trying to get my Broadcom 4312 wifi driver to work on my Hp netbook for some time now.  I used ndiswrapper.

I recently changed my IP to static to change my performance on the internet on my PS3.

**[COLOR="Red"]Does this screw anything up?[/COLOR]**
I'm not really sure if this can do anything to make my wifi unable to use.

---

### Post by marshmallow1304 on 2010-01-15
What did you change to static?  Laptop? PS3? Router?

---

### Post by Kafubie on 2010-01-15
> **marshmallow1304 said:**
> What did you change to static?  Laptop? PS3? Router?

I changed it in my router.

---

### Post by pricetech on 2010-01-15
A static IP on your computer won't make any difference in performance.

Is there something else you want to accomplish ??

---

### Post by marshmallow1304 on 2010-01-15
> **Kafubie said:**
> I changed it in my router.

So now your external IP is Static?  That should not cause any problems, as the router will take care of giving Ubuntu an IP.

---

### Post by pricetech on 2010-01-15
> **Kafubie said:**
> I changed it in my router.

Does your ISP allow you a static IP ??  If not, you'll probably lose your Internet connection very soon, though not permanently, just until you change back to DHCP.

---

### Post by Kafubie on 2010-01-15
> **pricetech said:**
> A static IP on your computer won't make any difference in performance.

Is there something else you want to accomplish ??

I'm not sure what you said was sarcastic. ;)
I tried to get my wifi to work using the ndiswrapper guide, I installed the windows drivers.  No workie...:confused:
I don't know if you know about ndiswrapper.
Well, I tried.

---

### Post by Kafubie on 2010-01-15
> **pricetech said:**
> Does your ISP allow you a static IP ??  If not, you'll probably lose your Internet connection very soon, though not permanently, just until you change back to DHCP.

I don't really know what you meant.  I had a static IP for awhile now.  There is some rare occasions I lose access to the interwebz on everything except the computer it is hooked up to.

---

### Post by pricetech on 2010-01-15
> **Kafubie said:**
> I'm not sure what you said was sarcastic. ;)
I tried to get my wifi to work using the ndiswrapper guide, I installed the windows drivers.  No workie...:confused:
I don't know if you know about ndiswrapper.
Well, I tried.

No I'm not being sarcastic.  A static IP won't make any difference in performance for your computer.

Sadly, no I can't help you with ndiswrapper.  I've never had a NIC that didn't just plain work in whatever flavor of Linux I was running, so I've never had to use it.

---

### Post by pricetech on 2010-01-15
> **Kafubie said:**
> I don't really know what you meant.  I had a static IP for awhile now.  There is some rare occasions I lose access to the interwebz on everything except the computer it is hooked up to.

What I'm asking is, are you supposed to have a static IP ??  Does your ISP assign you a static IP ??

Your IP doesn't necessarily have to change frequently just because it's dynamic.  My cable Internet provider doesn't assign me an IP, but my IP remains the same for long periods of time, several months in fact.

If your ISP doesn't assign you a static IP, change it back to dynamic (DHCP).  Otherwise you lose your connection when the IP you picked gets assigned to someone else.  It just comes back after they have rebooted, released / renewed, whatever to get a different IP.

---

### Post by DivisionMatrix on 2010-01-15
I'm a little confused here, did you mean to set your external ip to static, or are you trying to set up port forwarding to speed up your ps3?

---

### Post by audiomick on 2010-01-15
I have the feeling that different posters are talking about different IPs.

There is the one that the Internet sees that is mostly dynamic, typically on a 24hr lease, and often renewed to the same IP every time. This should be left at whatever the Internet provider says to set it to.

Then there are the ones that the router and the computer(s) and whatever else is is in the local network have to communicate with each other. These can be static or assigned via DHCP from the router.

One way of achieving a static IP in the local network is to reserve an IP in the router for a particular device using the MAC address of that device. This is the method I use at home, and it works very well. Unfortunately, not all routers can do it.

I think that this is what the OP is talking about, but I am not sure.

---

### Post by Belizeian on 2010-01-16
Okay I'm really confused now, you said you changed the IP on your routher and from time to time you lose conection on all our machines but the one directly connected.  So can you please expalin your external interface?  From you post it seems it's

cloud > pc > router > rest of your machines

If that's the case then I "assume" that you eitehr have a USB connection to your machine and use your ethernet port on that machine to connect your routher.

Or you have that one machine setup as a DMZ machine wait that doesn't make since either.


What exactly do you have and how is it connected.

---

