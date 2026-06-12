---
title: "Help needed with /etc/dhcp3/dhclient.conf"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by Axanon on 2009-04-22
I am running a small web server on a headless ubuntu (hardy) box and my router is not seeing the hostname of the computer. I did some reading about this and found that people with similar problems can edit their **/etc/dhcp3/dhclient.conf** file. The problem is there are no examples shown. My dhclient.conf file looks like this:

```
request subnet-mask, broadcast-address, time-offset, routers, domain-name,    domain-name-servers, host-name, ntp-servers;
```

Since everything is on one line like this I'm a little confused as to what I need to do? Do I change 'host-name' to the real host-name? Can somebody please give an example.

---

### Post by cariboo on 2009-04-22
What does your /etc/hosts file look like, could you paste the contents in your next post?

Jim

---

### Post by Iowan on 2009-04-22
First - is your server getting address via DHCP?  If so, you may eventually want to make that a static (MAC-address based) lease. The dhclient.conf file has a line:```
send host-name "<hostname>";

```
You can embed your hostname in that line.

---

