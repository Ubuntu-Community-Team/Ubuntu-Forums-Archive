---
title: "Static IP Addresses"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by jbullard on 2007-06-20
I have searched the forums and know this question has been asked at least 1000 times but for the life of me could not find an answer.  My current problem is that when I add my static ip's and restart the network I still can't ping/resolve hostnames.  Any help would be appreciated on this matter as I have been working on it for 2 days now and nothing.

IP's
74.95.54.17 - 20

Gateway
74.95.54.22

Netmask
255.255.255.248

The only thing I can't figure out is the network and broadcast as Ubuntu automatically adds 74.95.54.16 and 74.95.54.23 which are not part of my address range.

TIA,
Jason

---

### Post by dreadlord_chris on 2007-06-20
> **jbullard said:**
> I have searched the forums and know this question has been asked at least 1000 times but for the life of me could not find an answer.  My current problem is that when I add my static ip's and restart the network I still can't ping/resolve hostnames.  Any help would be appreciated on this matter as I have been working on it for 2 days now and nothing.

IP's
74.95.54.17 - 20

Gateway
74.95.54.22

Netmask
255.255.255.248

The only thing I can't figure out is the network and broadcast as Ubuntu automatically adds 74.95.54.16 and 74.95.54.23 which are not part of my address range.

TIA,
Jason

You need to add a couple DNS IPs to you mix:
```

sudo nano /etc/resolve.conf

```
add the following 2 lines to the **top**
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```
Those are the [OpenDNS]("http://www.opendns.com/") servers - I've found them to be much faster then my ISPs DNServers.
Save the file & restart your network. You shouldn't have any problems resolving domain names now.

---

### Post by PilotJLR on 2007-06-20
> **jbullard said:**
> 
IP's
74.95.54.17 - 20

Gateway
74.95.54.22

Netmask
255.255.255.248

The only thing I can't figure out is the network and broadcast as Ubuntu automatically adds 74.95.54.16 and 74.95.54.23 which are not part of my address range.


Ubuntu is actually correct...

Your subnet (which you don't specifically assign to anything) is defined as 74.95.54.16 /29
Your broadcast is also 74.95.54.23

This is derived from your address range + mask.

The post above, while helpful (cause openDNS is really good), is not relevant to this addressing question.

---

### Post by dreadlord_chris on 2007-06-20
> **PilotJLR said:**
> Ubuntu is actually correct...

Your subnet (which you don't specifically assign to anything) is defined as 74.95.54.16 /29
Your broadcast is also 74.95.54.23

This is derived from your address range + mask.

The post above, while helpful (cause openDNS is really good), is not relevant to this addressing question.

actually, the OP said:
[quote=jbullard ]
My current problem is that when I add my static ip's and restart the network I still can't ping/resolve hostnames.
[/quote]

Which would be because in setting up the static address he didn't enter any DNS info.
My post solves that problem.

---

### Post by PilotJLR on 2007-06-20
Oops, my mistake! He did say that was the problem.  :-)

---

### Post by jbullard on 2007-06-20
dreadlord_chris,

Thanks for that.  I searched for hours on what the problem was thinking it was something wrong with my network cause the nameservers put in my Ubuntu were not what they were suppose to be.  Hopefully I won't have any problems on reboot.


Jason

---

