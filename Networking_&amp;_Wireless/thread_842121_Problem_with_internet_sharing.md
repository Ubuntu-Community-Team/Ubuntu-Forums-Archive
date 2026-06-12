---
title: "Problem with internet sharing"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by n3mo.wolf on 2008-06-27
Firstly sorry about my bad english.

So, i've got problem with internet sharing. I've got 2 computers:
desktop - where internet come from my provider
laptop - internet come from desktop pc
i use desktop pc to route internet connection
i've connected them with normal UTP cable and i'm sure it is not broken.
So :
1) On the desktop all setting is normal and it works with vista at laptop
2) but when i install ubuntu at laptop - the internet is gone
So, here something strange
i open ipv6 sites, but when i ping (ex. google.com) i ping ipv4 server...
i can't update my packages list, but i can search in google...
when i click on some site nothing happen. I thing i have lost packages somewhere, 'cause when i'm with Vista at the Laptop - everything works alright. 

Regards,
Nedyalko Dyakov

---

### Post by dominiquec on 2008-06-27
Have you checked the IP address assigned to your laptop?  Is it manually assigned, in which case did you set up the IP address?  Or is it dynamic, in which case the desktop should be providing the IP address.

IP address is first thing I would check.  Very little else to go on from your description.

---

### Post by n3mo.wolf on 2008-06-27
> **dominiquec said:**
> Have you checked the IP address assigned to your laptop?  Is it manually assigned, in which case did you set up the IP address?  Or is it dynamic, in which case the desktop should be providing the IP address.

IP address is first thing I would check.  Very little else to go on from your description.

I checked it. 
___________________________

Desktop ip - 192.168.0.1
laptop ip - 192.168.0.2
laptop dns - 192.168.0.1
laptop gw 192.168.0.1
sub mask - 255.255.255.0
____________________________

---

### Post by dominiquec on 2008-06-27
Those settings look okay.

Can you ping to your desktop machine (192.168.0.1)?  If that's okay, try the following:

nslookup [www.yahoo.com](www.yahoo.com)  - this should return an IP address of yahoo.com; this will check if DNS resolution is okay

tracepath [www.yahoo.com](www.yahoo.com) - shows whether the packets are processed correctly

What routing software are you running on the desktop, by the way?

---

### Post by n3mo.wolf on 2008-06-27
> **dominiquec said:**
> Those settings look okay.

Can you ping to your desktop machine (192.168.0.1)?  If that's okay, try the following:

nslookup [www.yahoo.com](www.yahoo.com)  - this should return an IP address of yahoo.com; this will check if DNS resolution is okay

tracepath [www.yahoo.com](www.yahoo.com) - shows whether the packets are processed correctly

What routing software are you running on the desktop, by the way?

I can ping my desktop machine. I use NAT in iptables to share internet connection between computers. 

take a look at that : 

```
nafo@nafo-laptop:~$ nslookup yahoo.com
Server:		192.168.0.1
Address:	192.168.0.1#53

Non-authoritative answer:
Name:	yahoo.com
Address: 206.190.60.37
Name:	yahoo.com
Address: 68.180.206.184


nafo@nafo-laptop:~$ tracepath yahoo.com
 1:  unknown (192.168.0.2)                                  0.135ms pmtu 
1500
 1:  unknown (192.168.0.1)                                  0.250ms 
 1:  unknown (192.168.0.1)                                  0.222ms 
 2:  unknown.ddns-lan.pl.ekk.bg (89.215.69.1)               2.312ms 
 3:  default.intl.ekk.bg (217.9.225.162)                   12.934ms 
asymm  4 
 4:  unknown.interbgc.com (89.215.174.41)                  11.175ms 
asymm  5 
 5:  ge-1-1-2-fra.eu-exchange.net (80.81.192.156)          43.428ms 
asymm  6 
 6:  ge-1-3-0.pat1.dee.yahoo.com (80.81.192.115)           49.245ms 
asymm  7 
 7:  ge-0-2-0.pat2.dee.yahoo.com (66.196.65.131)           51.004ms 
 8:  so-3-0-0.pat2.dcp.yahoo.com (66.196.65.129)          142.508ms 
asymm 14 
 9:  so-1-0-0.pat2.da3.yahoo.com (216.115.101.155)        186.807ms 
asymm 14 
10:  so-0-0-0.pat2.sjc.yahoo.com (216.115.101.151)        215.159ms 
asymm 13 
11:  ae1-p171.msr2.sp1.yahoo.com (216.115.107.87)         268.380ms 
asymm 13 
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
```

Packets just stop come? I can't understand it!

---

### Post by dominiquec on 2008-06-27
Seems like your network is fine, then.  The output is expected of yahoo.com (I get that, too) and that's because of their content distribution network.

Maybe next try checking the packages.  You can do

sudo dpkg --configure -a 

(this will reconfigure any packages that have not been configured)

and 

sudo apt-get update

and 

sudo apt-get upgrade

(this will reload the package indexes and upgrade files)

---

### Post by n3mo.wolf on 2008-06-27
Nothing happens... same ****! I can't update packages list ... somethign is wrong... too wrong....

---

