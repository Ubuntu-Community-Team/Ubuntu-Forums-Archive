---
title: "dyndns address resolved to local ip"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by strowik on 2007-08-21
Hello!

I set up address at dyndns.com and got it working. Unfortunately after trying to set up reverse dns, the dyndns domain is resolved to local ip address 192.168.1.64 by network query tools and others cannot access my server using the domain name. I uninstalled bind9 and deleted the files i created during the setup. I followed this guide: [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)

One thing i notices is that i cannot change the content of resolv.conf. Well, i can, but it resets after every reboot.

resolv.conf:
```

search lan
nameserver 192.168.1.254

```

What to do?

---

### Post by rickyjones on 2007-08-21
Do you have a DHCP server running that is overriding what you want?

---

### Post by strowik on 2007-08-21
No, i haven't installed DHCP server.

---

### Post by rickyjones on 2007-08-21
If the /etc/resolv.conf keeps changing after you edit it then you must be using the DHCP client on your computer to get an IP from a DHCP server. That is what I meant. Is the DHCP server that gives you an address giving you the wrong information?

-Richard

---

### Post by strowik on 2007-08-21
Okay, i edited /etc/network/interfaces and now the resolv.conf content doesn't change after reboot. Nevertheless, this doesn't solve the problem. Domain is still resolved to local ip by NQTs.

---

