---
title: "How to Make firewall start as service with Ubuntu?"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by sharif_aly on 2009-07-21
How to Make firewall start as service with Ubuntu?

---

### Post by wojox on 2009-07-21
Turn it on:

```
sudo ufw enable
```

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by 3rdalbum on 2009-07-21
Your firewall doesn't start as a service, it starts as part of the kernel. If you have turned it on with Firestarter or (preferably) UFW it will do its work on startup.

---

### Post by Rocket2DMn on 2009-07-21
IIRC, the firewall doesn't start out of the box because ports are closed by default.  If you start opening ports, that's when the firewall needs to be enabled.  Remember that ufw is just a front end to iptables.

---

### Post by sharif_aly on 2009-07-21
I was talking about firestarter .. anyway is there a better firewall ?

---

### Post by Rocket2DMn on 2009-07-21
Firestarter is also a front end to iptables, however I believe it is no longer maintained.  We now use ufw on the command line and gufw for a graphical interface.  ufw = Uncomplicated Firewall.
```
sudo apt-get install gufw
```
Then you can access it from System->Administration->Firewall configuration

---

### Post by sharif_aly on 2009-07-21
But **"Firewall Configuration"** is very poor tool, dose not have all features of **"Firestarter"**

---

### Post by XCan on 2009-07-22
UFW itself is kind of too dumb. It can only block incoming traffic. Now, people are going to tell you that there's no reason to block outgoing since they are initiated by your computer. But I still believe that is up to how much control the user wants, and making a tool that only works half the way and calling it user friendly is questionable.

---

### Post by The Cog on 2009-07-22
> **sharif_aly said:**
> But **"Firewall Configuration"** is very poor tool, dose not have all features of **"Firestarter"**
Ah, but Firestarter is a very poor tool, does not have all the features of iptables. And, I gather, is is no longer maintained.

Any choice of firewall-configuring GUI is a personal choice, a compromise between feature-set and convenience. UFW is very simple and suitable for most home users. I prefer guarddog with more features but more complicated. I generally just use an iptables shell script though - that way I really know what it's doing.

---

