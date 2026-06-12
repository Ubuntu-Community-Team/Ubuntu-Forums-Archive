---
title: "Internet connection problem"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by diceydemon on 2006-11-06
Alright, i've read through a lot of other threads in vain and decided to just ask for help instead of lurking.

I installed ubuntu 6.0.6 last night, and when running off the Live CD the internet was running. Now without the cd, i can't connect to the internet through ff, or using email, or even using apt-get update. 

I have an active network connection : eth1 and it's status is receiving, with a 100% signal strength.

I have diabled the ipv6 through ff, and /etc/modprobe.d/aliases.

And i have also found a DNS address for networking.

I am using a static IP adress, as when using this i can ping my network IP adress and get a response.

If you need any more info just ask.

EDIT: I just thought of some more stuff that might help, i have tried  sudo pppoeconf, and got an error, access concentrator did not respond.

---

### Post by stream303 on 2006-11-10
> **diceydemon said:**
> 
And i have also found a DNS address for networking.

I am using a static IP adress, as when using this i can ping my network IP adress and get a response.


Is this DNS address in /etc/resolv.conf one of your isp's or one from your router?  Since you are running static, perhaps just rewriting /etc/resolv.conf with your isp's nameserver at the top might help -- if this is truly the problem...

---

