---
title: "internet connection dies after 20 seconds"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by dynam on 2006-12-11
Hello, I am new to Ubuntu and Linux, almost a complete newbie. I tried to search the forum and came across some relevant networking problems but I just can't solve mine:

Yesterday I successfully installed Ubuntu 6.10 on a PC which can now dual-boot between Ubuntu and Windows. The computer is plugged straight to my ADSL modem.

On Ubuntu, after configuring my internet connection using the sudo pppoeconf command, I started Firefox and happily got connected to the internet. But after like 20 seconds, the connection would die. I don't know what went wrong but the syslog seems to suggest something unusual:

> DHCPACK from 192.168.2.1 bound to 192.168.1.1 -- renewal in 18 seconds

It seems to be a networking configuration problem so I tried to manually assign two DNS addresses in system --> networking --> DNS but it doesn't really help.

Since I am only available to connect to the internet using Windows, I am sorry that I can't provide other information at the moment -- but I would be more than happy to boot to Ubuntu and try to find and copy whatever information you'd need and post it over here. Thanks very much for your help.

---

### Post by Iowan on 2006-12-11
Looks like the lease time is quite short... 
You might check **/etc/dhcp3/dhclient.conf** to see if there's a line similar to:
```
#send dhcp-lease-time 3600;
```
but without the # and a smaller number.  If the Windows box works, it would seem doubtful that the DHCP server is faulty.  Having no experience w/ pppoe, I dunno if there's a value to limit connection time.

---

### Post by dynam on 2006-12-11
Thanks for your reply, Iowan, but this doesn't seem to solve my problem.

> #send dhcp-lease-time 3600;

This line is in my /etc/dhcp3/dhclient.conf file but I guess this file is a sample configuration file only...

In another relevant config file /etc/ppp/peers/dsl-provider, I don't see any value deciding the lease time. Thanks for your help anyway.

---

### Post by dynam on 2006-12-12
I found that the DNS nameservers I provided in System > Admin > Networking are changed automatically to a useless default address 192.168.1.1 very soon after I made my amendment.

As the problem has been reported and discussed in the forum for a while, I think it has to do with dhclient over-writing the /etc/resolv.conf file as I did manually edit the file but the nameserver setting was forced back to the default address.

So, I tried the option 2 of this [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=307758") and edited the PREPEND line of /etc/dhcp3/dhclient.conf and and placed my isp's DNS nameservers there. But this option doesn't work. Any thought? Thanks.

---

### Post by Iowan on 2006-12-13
You might *uncomment* that lease-time line to see if it helps.  Whilst there, you might remove the **domain-name-servers** entry from the **request** line.  (Although the PREPEND line *should *make your ISP's DNS servers appear first.)

---

