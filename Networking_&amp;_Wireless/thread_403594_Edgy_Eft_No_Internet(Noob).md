---
title: "Edgy Eft No Internet(Noob:)"
date: 2007-04-07
forum: Networking &amp; Wireless
---

### Post by thesheqq on 2007-04-07
I just installed ubuntu on my desktop which is a Dell Dimension 8400.  I have not been able to get the internet running with the edgy eft release.  I have tried some things I saw in here, I am pretty sure I disable ipv6.  I tried changing from DHCP to static and matched subnet mask, default gateway, and DNS servers with what I know to be the right settings for my internet previously.  I am posting this on my laptop which is hard wired to the same connection using a network switch.  I am lost and really want to get going on setting up the rest of ubuntu what can/should I do.

---

### Post by Paul41 on 2007-04-07
See if this fixes it for you.

[http://ubuntuforums.org/showthread.php?t=186430](http://ubuntuforums.org/showthread.php?t=186430)

---

### Post by userthebuntu on 2007-04-07
When doing this on xubuntu 6.10 (which is edgy anyway right?) I received a message at startup to add my hostname to /etc/hosts
I put a line 192.168.1.36 (my IP) followed by a whitespace and my hostname (ie. my computername).
Didn't solve the problem of not being able to get online where I am indeed able to ping my router and access it via telnet.

---

### Post by thesheqq on 2007-04-07
paul41  I followed the link you posted and did the steps, still no connection, I also changed to openDNS settings.  But nothing still.  Should my broadcast address be the same as what my laptops DHCP server is on the same internet connection?  I am able to ping local host as well.

---

### Post by userthebuntu on 2007-04-07
Your DHCP would be your router right?
My broadcast address differs from the router's address: 192.168.1.255 is broadcast and 192.168.1.1 (surprise) is my router.

Do you know how to change the broadcast address in ifconfig?

---

### Post by thesheqq on 2007-04-07
well I am kinda learning on the fly, if you wanted to tell me how to do it it'd be great, thanks for the help everyone!

---

