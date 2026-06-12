---
title: "ping: sendmsg: Operation not permitted"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Jimmey on 2007-11-18
I am trying to connect my two computers using a switch. They're both connected to the same wireless router but I would like to use their wired NICS to connect them directly. 

I tried this in Windows, and when I plugged them both into the switch and rebooted, windows had given the wired interfaces the following IP addresses:

192.168.0.1
192.168.0.2

Where the wireless interface addresses are 

192.168.1.XXX

So the connection to the switch is showing up on the switch's lights, and I have been able to ping to and from each computer on the wired addresses in Windows, when I try the same in Ubuntu 7.10, I get

> ping: sendmsg: Operation not permitted

How can I resolve this?

Thanks.

I enabled internet connection sharing on each of the wired network interfaces on each machine using firestarter. then it worked.

---

### Post by Jimmey on 2007-11-18
I've just done another test in Windows. The ip addresses for each other network interface cards are identical over the two platforms, and it works in Windows. 

How can I get it to work in Ubuntu?

Thanks?

---

### Post by Blutack on 2007-11-18
sudo ping?
Sounds like either a permissions or a firewall thing.  Most likely permissions.

---

### Post by Sabeeh on 2008-04-29
> **Blutack said:**
> sudo ping?
Sounds like either a permissions or a firewall thing.  Most likely permissions.
No it doesn't helps with **sudo**...can please someone give a solution?

---

