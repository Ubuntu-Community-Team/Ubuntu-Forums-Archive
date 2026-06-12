---
title: "how to create domain in ubuntu server 12.04"
date: 2014-03-04
forum: Networking &amp; Wireless
---

### Post by Ankit_sarawgi on 2014-03-04
I have ubuntu server 12.04 .. i am new in ubuntu ..
in my server running a web services , at client side user accsess the link through IP in browser like **192.168.1.250/national_cis** but i want user replace the ip from domain like **[http://bansal_hospital/national_cis](http://bansal_hospital/national_cis)** kindly suggest me step by step process ...
how to change IP access to domain access.

---

### Post by xeonix on 2014-03-04
For internal network with same subnet, you can simply change "**hostname**"
You can view your hostname with the command "hostname"
Change the hostname in the following files, and reboot.
```

/etc/hostname
/etc/hosts

```

For external IP's or different subnets or VLAN's you need look int DNS (Domain Name Servers)

---

### Post by Hadaka on 2014-03-04
Here is a link to a tutorial that shows step by step
EXACTLY what you are wanting to do. Have fun !
[http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/](http://chrisjean.com/2009/02/19/ssh-tutorial-for-ubuntu-linux/)

---

