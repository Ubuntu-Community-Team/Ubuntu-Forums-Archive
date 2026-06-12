---
title: "Can I block the internet access for a single user?"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by Vinze on 2006-10-09
Hey, I was wondering if and how it is possible to block internet access for a single user. 

I'm on a wireless connection (wlan0) on Xubuntu edgy.

---

### Post by TheWizzard on 2006-10-09
never tried this, but it looks like this is possible with iptables.
see:
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH)

---

### Post by Vinze on 2006-10-10
> **TheWizzard said:**
> never tried this, but it looks like this is possible with iptables.
see:
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH](http://iptables-tutorial.frozentux.net/iptables-tutorial.html#OWNERMATCH)

But that's **a lot**of reading, I was thinking it would be easier if I were to disallow this user to run a certain program required to access the internet...

---

### Post by TheWizzard on 2006-10-11
> **Vinze said:**
> But that's **a lot**of reading, I was thinking it would be easier if I were to disallow this user to run a certain program required to access the internet...

i think this is the way to go if you want to trully block a user from using the internet. maybe you should explain why you want to block a user. 
if it is just parental control you can check:
[http://kb.mozillazine.org/Parental_controls](http://kb.mozillazine.org/Parental_controls)
[http://jpatrick.wordpress.com/2006/04/02/linux-parental-control/](http://jpatrick.wordpress.com/2006/04/02/linux-parental-control/)

---

### Post by Vinze on 2006-10-11
> **TheWizzard said:**
> i think this is the way to go if you want to trully block a user from using the internet. maybe you should explain why you want to block a user. 
if it is just parental control you can check:
[http://kb.mozillazine.org/Parental_controls](http://kb.mozillazine.org/Parental_controls)
[http://jpatrick.wordpress.com/2006/04/02/linux-parental-control/](http://jpatrick.wordpress.com/2006/04/02/linux-parental-control/)

Dansguardian looks great, thanks a lot!

---

### Post by Vinze on 2006-10-11
I now have my doubts, as I learnt that squid, which I'd need, is actually a proxy server, so I'd have to edit a lot of settings for every other user again...

---

### Post by dannyboy79 on 2006-10-11
if you are in control of the router and this user is on another computer with a certain ip, you can use the router to disallow that ip "out" to the internet! That's what I did so that they couldn't steal all my bandwidth. My torrents started going really slow one day and I had no idea that my roommate even knew what a torrent was. I read the log of my router and sure enough he was using torrents and sucking all my bandwirth, so now I restrict i-net access at certain times using the schedule function of my Netgear router. It's actually really funny, i warned him though that there'd be consequences if her kept sucking all my bandwidth! i am eventually gonna show him how to throttle the bandwidth he uses so that we can both bit torrent but i'll let him suffer for a week and see how much he freaks out! HA HA

---

### Post by Vinze on 2006-10-11
> **dannyboy79 said:**
> if you are in control of the router and this user is on another computer with a certain ip, you can use the router to disallow that ip "out" to the internet! That's what I did so that they couldn't steal all my bandwidth. My torrents started going really slow one day and I had no idea that my roommate even knew what a torrent was. I read the log of my router and sure enough he was using torrents and sucking all my bandwirth, so now I restrict i-net access at certain times using the schedule function of my Netgear router. It's actually really funny, i warned him though that there'd be consequences if her kept sucking all my bandwidth! i am eventually gonna show him how to throttle the bandwidth he uses so that we can both bit torrent but i'll let him suffer for a week and see how much he freaks out! HA HA

Hehe, unfortunately I'm not in control of the router... ](*,)

---

