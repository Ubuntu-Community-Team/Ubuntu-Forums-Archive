---
title: "Cannot restart networking service"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by barnabas022 on 2014-04-19
I have just upgraded my Ubuntu server from 13.10 to 14.04, and am trying to configure networking, but whenever I try to restart it with sudo service networking restart, it says
```
stop: Job failed while stopping
start: Job already running: networking
```
/etc/init.d/networking restart seems to not do anything, and my changes in /etc/network/interfaces are not updated.
Any ideas on why this is happening and how to fix it?

---

### Post by truck87brp on 2014-04-19
I think Networking is Hosed in 14...Thought I had a hardware problem untill I tried 12.04 Lubuntu and everything is fine. 

In 14.04 I opened firefox and had to do a reset on the fresh install and it backup to a folder on first use to the desktop. Suprise! WTF It still would NOT connect with wired.

---

### Post by The Codfather on 2014-05-02
> **barnabas022 said:**
> I have just upgraded my Ubuntu server from 13.10 to 14.04, and am trying to configure networking, but whenever I try to restart it with sudo service networking restart, it says
```
stop: Job failed while stopping
start: Job already running: networking
```
/etc/init.d/networking restart seems to not do anything, and my changes in /etc/network/interfaces are not updated.
Any ideas on why this is happening and how to fix it?

I get the same messages as this on a new install.
I even downloaded another iso, just in case there was a disk problem, but still the same.
I get round this with a system reboot, but it is still annoying.

---

### Post by Yang_Lu on 2014-05-27
I got this message too. Anyone who can help?

---

### Post by Manas B on 2014-06-26
I am experiencing the same issue. I have not found a solution yet.

---

### Post by WinEunuchs2Unix on 2014-08-02
This has been reported as a bug: [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1301015](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1301015) and is now called an undocumented feature.

Under 14.04 it appears the preferred methodology is ifdown <interface> followed by ifup <interface>.  I will try it myself the next time the network gets "choppy".

---

### Post by DaveQB on 2014-11-25
But the ifdown command will disconnect you and now you have just lost connection with the your server. 

Is there a working solution for this??

---

### Post by ikki_72 on 2014-11-27
I've been having this since 13.10. What a piece of...

---

### Post by hellmitre on 2015-01-04
> **DaveQB said:**
> But the ifdown command will disconnect you and now you have just lost connection with the your server. 

Is there a working solution for this??


I hate it; there should be a command for restarting networking services, and silent failure is NOT AN ACCEPTABLE BEHAVIOR.

BUT! You can chain the commands to bring down the interface, and bring it back up, so that whether or not you're there to see it, the interface comes back up.

```
ifdown eth0 && ifup eth0
```

---

