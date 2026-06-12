---
title: "Evil Nameserver Issue"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by Kyle W. Cartmell on 2007-02-23
I can connect to my network just fine. I use DHCP. After I connect, /etc/resolv.conf looks like this...

kcartmell@kcartmell-hp:/etc$ cat /etc/resolv.conf
search cyclonecommerce.com
nameserver 10.1.0.101
nameserver 10.1.0.102
kcartmell@kcartmell-hp:/etc$ 

Anywhere from 30 to 120 minutes later, it is modified to look like this...

kcartmell@kcartmell-hp:/etc$ cat /etc/resolv.conf
search cyclonecommerce.com
nameserver 10.50.2.1
nameserver 4.1.1.1
nameserver 4.2.2.2
kcartmell@kcartmell-hp:/etc$ 

I'm trying to determine what is making this change. Can anyone suggest a /good/ way to troubleshoot this issue?

Thanks in advance for any assistance!
- Kyle

---

### Post by sdide on 2007-02-23
Hey,

Sounds strange.

can you do 

# cat /etc/dhcp3/dhclient.conf | grep -v ^#

and post output.

---

### Post by Kyle W. Cartmell on 2007-02-25
send host-name "kcartmell-hp";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers,
        netbios-name-servers, netbios-scope;

---

### Post by sadjack on 2007-02-25
I've had the same problem. I was directed to this thread

[http://www.ubuntuforums.org/showthread.php?t=181697](http://www.ubuntuforums.org/showthread.php?t=181697)

However the easiest fix for me (6 hosts) was to give each a fixted IP address and turn off DHCP.

---

### Post by Kyle W. Cartmell on 2007-02-25
I'd considered that option, but I would prefer to use DHCP and network-manager.

I'm willing to expend a great deal of time hunting a solution, I just need a push in the right direction. ;)

EDIT: Oh wait, that's a great thread!! *reading*

ANOTHER EDIT: I'm not convinced that the thread reference nor the one referenced from there is this issue. Then again, neither thread is terribly precise in defining the "network problems" they're working with. At this point, I'm pondering methods of observing what processes are making changes to resolv.conf.

---

### Post by sadjack on 2007-02-25
Its strange that this problem seems peculiar to Ubuntu. I've looked around and posed the question to my local LUG but people using different distros do not seem to have the problem.

Saying that it only happens on my desktop which acts as a print server. My laptop does not get messed about in the same way. Both have Ubuntu 6.10 and very much have the same software installed.

---

### Post by Kyle W. Cartmell on 2007-02-25
*sigh*

Sounds like I get to go hunting. I'll bring back the results of my troubleshooting, useful or not. We've got to figure this one out!

---

