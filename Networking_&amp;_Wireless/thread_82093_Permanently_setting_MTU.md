---
title: "Permanently setting MTU"
date: 2005-10-25
forum: Networking &amp; Wireless
---

### Post by veloct on 2005-10-25
My MTU is set to 1492.  I can do > sudo ifconfig eth0 mtu 1500 and it will make the change.  How can I make this permanent?

Also, I would like to tweak my internet performance.  Any suggestions?

Thanks.

---

### Post by mgor on 2005-10-26
check /etc/network/interfaces.
options that go in there are found in
```
man 5 interfaces
```

---

### Post by veloct on 2005-10-26
Thank you, that did the trick.

---

### Post by jnoreiko on 2005-12-17
veloct, could you post the changes you made to that file please?

---

### Post by veloct on 2005-12-17
I won't post the whole thing but only the part that was changed. I ended up setting a static ip since I have a router between my DSL modem and my PC but it works just fine if you just use dhcp also. I opened my favorite editor as sudo ('sudo kedit /etc/network/interfaces') and added the mtu line.

[B]# The primary network interface
iface eth0 inet static
     address 192.168.2.7
     netmask 255.255.255.0
     gateway 192.168.2.1
     mtu 1500[/B]

Then saved the change I made. Back in the terminal window I entered the following commands:

*sudo ifdown eth0* - this brings the network down, you can verify by issuing 'ifconfig' without the quotation marks.

*sudo ifup eth0* - pretty straight forward, I brought the network back up

*ifconfig* - it should show the new mtu value plus all the other information related to eth0

HTH

BTW, the lines after the iface command have a couple spaces in front of them.  Makes it easier to see.

---

### Post by Lambert on 2005-12-17
[quote=veloct]

Also, I would like to tweak my internet performance.  Any suggestions?

Thanks.[/quote] 
Are you using a broad band connection? If so see this thread for some tweaks.

[http://www.ubuntuforums.org/showthread.php?t=104371]("http://www.ubuntuforums.org/showthread.php?t=104371")

Also look into disabling ipv6 in firefox and system wide. Some of claimed improvements with this. there's a small section in the WTG that's linked in my signature on how to do this.

---

### Post by jnoreiko on 2005-12-21
[QUOTE=veloct]it works just fine if you just use dhcp also[/QUOTE]

I'm not sure it does.
The manual page for that file seems to sugget the mtu line can only go on after an interface listed with the static method.

I've tried this:
```

iface eth0 inet dhcp
        mtu 1400
```

and it doesn't work.

---

### Post by jnoreiko on 2006-01-12
Update: found a fix on another thread here. This is apparently a known bug.

---

### Post by eXisor on 2006-08-03
I know this is an old thread, but it took me ages to find the simple answer for DHCP, ie. requiring no boot script. It was originally posted by mlonker, but is buried in a thread

[http://glasnost.beeznest.org/articles/290](http://glasnost.beeznest.org/articles/290)

---

### Post by jefferz on 2008-04-08
link is broken...
DHCP and manual MTU setting is needed for my Hauwei E220 on GSM (1500 is to high works good on 576)
Can someone post this info
Thanks

---

