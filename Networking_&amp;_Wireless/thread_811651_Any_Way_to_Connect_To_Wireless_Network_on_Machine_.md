---
title: "Any Way to Connect To Wireless Network on Machine Boot?"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by baudelaire on 2008-05-29
I've looked for this answer, but can't find exactly how to do it.  I can connect to my network easily once in Gnome, but of course I must login first.  I would like to have my laptop connect without anyone having to log into the machine.  My wireless network uses WPA-AES encryption.  If you need anymore information please let me know.  I appreciate the help!

---

### Post by tigerplug on 2008-05-29
May I ask why you want to do this?

If the reason you ask is for domain authentication then I guess you would have to performa cached logon.

---

### Post by baudelaire on 2008-05-29
I would like to be able to use the machine remotely via ssh when I am away from it.  If I reboot that machine and I'm not physically in front of the machine or at my home I cannot log in.  Also, I would like to experiment with ldap and network logins, meaning that I would have to first be connected to the network (preferably without a hard, wired connection to the network)  It's very much a convenience thing

---

### Post by tigerplug on 2008-05-29
You dont need to be connected to the network for Directory type logons .... I assume that Ubuntu can perform a "cached logon".

Hmm, I'm not sure to be honest but there should be no reason to reboot with SSH unless its something like a kernel upgrade or similar.

---

### Post by baudelaire on 2008-05-29
Maybe I should specify that this is a home network -- I want it to connect to my network automatically

---

### Post by baudelaire on 2008-06-05
Anyone else have any ideas?

---

### Post by lswb on 2008-06-05
It can be done with some of the command line tools for sure but I don't think NetworkManager will be compatible; Check out ifplugd, waproamd, and IIRC, wifi-radar has a start-up otion that worked well on dapper. 

I believe you will have to edit your /etc/network/interfaces file, there are man pages and web sites to look up more info.

---

### Post by Quantumstate on 2008-06-05
Try in /etc/rc.local:
```
/sbin/ifdown wlan0
/bin/sleep 1
/sbin/ifup wlan0
/usr/bin/tail /var/log/messages
```

---

### Post by baudelaire on 2008-06-05
> **lswb said:**
> It can be done with some of the command line tools for sure but I don't think NetworkManager will be compatible; Check out ifplugd, waproamd, and IIRC, wifi-radar has a start-up otion that worked well on dapper. 

I believe you will have to edit your /etc/network/interfaces file, there are man pages and web sites to look up more info.

Thanks lswb, wifi-radar worked perfectly.  It was exactly what I needed and it plays well with the default network manager.

---

