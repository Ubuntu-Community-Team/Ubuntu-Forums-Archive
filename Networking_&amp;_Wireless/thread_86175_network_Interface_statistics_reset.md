---
title: "network Interface statistics reset?"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by webwalker on 2005-11-04
'm a Solaris geek moving to Linux. In most of the traditional big iron Unix systems, I can run netstat -z to zero out the interface statistics to help diagnose a dicey connection, cable, port, .etc. I've found that, so far, the only way to clear the interface in Ubuntu Linux is to reboot the machine. No user is going to let me drop-kick their machine repeatedly to test it when they're trying to work.

Is there another way in Linux to reset the interface counters?

RMW

---

### Post by cwaldbieser on 2005-11-04
[QUOTE=webwalker]'m a Solaris geek moving to Linux. In most of the traditional big iron Unix systems, I can run netstat -z to zero out the interface statistics to help diagnose a dicey connection, cable, port, .etc. I've found that, so far, the only way to clear the interface in Ubuntu Linux is to reboot the machine. No user is going to let me drop-kick their machine repeatedly to test it when they're trying to work.

Is there another way in Linux to reset the interface counters?

RMW[/QUOTE]
Not sure exactly what statistics you are talking about, but if you mean IP accounting counters, you can reset them with iptables.

---

### Post by greenway on 2005-11-04
I am also not quite sure what you mean. If you are looking for a way to resest your NIC, use "ifdown" and "ifup". If you are looking for a way to diagnose any problems on your network, you might want to use "ifconfig" to get a status on carrier errors and collisions. For a more detailed error report, I always use "ethtool -S".

---

### Post by webwalker on 2005-11-07
Well, If I have a production system that someone is using and I am trying not to disturb them while a diagnose an intermittent or degraded connectivity problem, I look to netstat -i for my statistic...ya know...packets drop, TxRx errors.. you know the drill.

But the person on the system is also smart enough to look there too. So while I'm diagnosing this thing, after I make a change (jiggle,wiggle,replace) I need to zero the TxRx error counters so that I can see whether I'm still throwing errors.

Not a smart aleck character would just say, "What? You can't ADD?" And they would be right. For fixing the immediate problem its not that big of a deal. Where it becomes a big deal is next week, when my customer looks at their box again or feels some "percieved performance problem" and pulls up the interface stats. And sees TxRx error numbers. And calls me or one of my fellows to fix a problem that got fixed a week ago. 

So is there a way in Linux, like Solaris to clear the TxRx error interface statistics you get from netstat -i to let you start fresh and not generate additional calls unecessarily?

---

