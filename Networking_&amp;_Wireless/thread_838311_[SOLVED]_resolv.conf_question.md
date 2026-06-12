---
title: "[SOLVED] resolv.conf question"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by editrix on 2008-06-23
[COLOR="Red"]Ack! I've got the wrong prefix! It should be[/COLOR] [COLOR="DarkOrange"][all variants] [/COLOR][COLOR="Red"]and I can't change it.[/COLOR]

Could someone please tell me what /etc/resolv.conf is supposed to look like?

I began a thread in Absolute Beginners [http://ubuntuforums.org/showthread.php?t=837309](http://ubuntuforums.org/showthread.php?t=837309) because I can't connect to localhost but so far, no joy. I think I'm getting close to an answer, however. I have no entry for myself in /etc/resolv.conf and I think I should. But I don't know what it's supposed to look like. The examples I've found on the web don't make much sense to me.

Right now, what I have is:
> domain ncf.ca 		#kppp temp entry
nameserver 134.117.137.1
nameserver 134.117.1.27
nameserver 134.117.137.1	#kppp temp entry
nameserver 134.117.1.27	#kppp temp entry


The IP numbers are for ncf.ca, my ISP.

---

### Post by plewisfdx on 2008-06-23
Here's my output.
```
search lan
nameserver 192.168.1.1

```

But I think your problem may involve /etc/hosts

What does that file look like on your machine?

I think it should look like this:

127.0.0.1 localhost
127.0.1.1 hostname

I'm not sure if the second line is .1.1 since my network is .1.1, but I think the first line is important for your issue.

---

### Post by superprash2003 on 2008-06-23
the resolv.conf file is normally filled by your router in the case of DHCP..

---

### Post by editrix on 2008-06-23
> **superprash2003 said:**
> the resolv.conf file is normally filled by your router in the case of DHCP..

Except I don't have a router. I'm on dialup. I have an ethernet card, which is currently disabled. I'm wondering if it somehow messed up resolv.conf.

---

### Post by editrix on 2008-06-23
> **plewisfdx said:**
> Here's my output.
```
search lan
nameserver 192.168.1.1

```

I've found many examples with that "search" line, but as you can see, I don't have one. And "lan" means you're somehow networked, right? I'm not.

> But I think your problem may involve /etc/hosts ...

I think it should look like this:

127.0.0.1 localhost
127.0.1.1 hostname


That's what mine looks like. :(

---

### Post by editrix on 2008-06-24
Problem solved in that it wasn't resolv.conf, it was /etc/hosts.

The 1st line of which *should* read: 
127.0.0.1 localhost.localdomain localhost computername

So that's all fixed, but Firefox crashed. Sigh!

---

