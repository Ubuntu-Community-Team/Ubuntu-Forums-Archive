---
title: "DNS problem"
date: 2006-09-19
forum: Networking &amp; Wireless
---

### Post by lfys on 2006-09-19
I connect my Ubuntu 6.06 laptop to my network via a USR5410 PCMCIA card.

After booting up
[LIST]
[*]I CAN connect to my modem-router (the machine hes received an IP address)
[*]I CANNOT connect to webpages using their names
[*]I CAN connect to webpages using their IP addresses
[/LIST]

When I remove the WIFI card and put it back in (or do rmmod/modprobe) everything works as normal.
Does anyone have a clue how I can solve this problem?

---

### Post by tbonius on 2006-09-19
I find it strange that a lot of people have this issue.  Youre being allocated an IP from a DHCP server?  What IP addresses should the DHCP server be handing out for your DNS servers?  Are you getting those DNS servers assigned?  Check /etc/resolv.conf

T

---

### Post by Iowan on 2006-09-19
[http://www.ubuntuforums.org/showthread.php?t=252967]("http://www.ubuntuforums.org/showthread.php?t=252967")
Check this thread 
[http://http://www.ubuntuforums.org/showthread.php?p=1520033#post1520033]("http://http://www.ubuntuforums.org/showthread.php?p=1520033#post1520033")
Here's another one.
There are others, too.  Some have fixed the problem by editing the ** domain-name-servers** out of the **/etc/dhcp3/dhclient.conf** file.  The thread gives this and other information.  For more examples, SEARCH for **dhclient.conf** or **dhclient-enter-hooks**.


Good Luck!

---

### Post by lfys on 2006-09-20
/etc/resolv.conf sais

[INDENT][INDENT][I]domain domain.com
nameserver 192.168.1.1[/I][/INDENT][/INDENT]

Does that mean that my laptop wants my router (192.168.1.1) to translate the names into ip addresses?
And does that mean my computer tries to be part of a domain that probably isn't even there?

---

### Post by Iowan on 2006-09-20
Yes, sounds like your laptop wants the router to do DNS - which is OK **_IF_** the router can/will (mine does). Otherwise, some tweaking may be in order.

The router may be responsible for the domain assignment, too.

---

### Post by bastiegast on 2006-09-20
My router did the same and made my internet versy slow/not working I edited /etc/dhcp3/dhclient.conf and added the DNS servers provided by my ISP, for me it fixed all my internet issues:D

---

### Post by lfys on 2006-09-20
And what exactly do I have to add to /etc/dhcp3/dhclient.conf in order to point the machine to the right DNSs ?

****************************

In the mean time I managed to add 2 nameservers to /etc/resolv.conf
I restarted my machine and ... lo and behold ... it made connection to the internet right away! Hope this was not a coincidence and things stay like this. :D

---

### Post by Iowan on 2006-09-20
Hope all stays well, otherwise...
Check those threads - the prepend instruction lets you add the DNS servers.

---

### Post by lfys on 2006-09-21
Oh dear!
I was cheering too soon.
I'd better read the suggested literature ...

---

### Post by bastiegast on 2006-09-23
> **lfys said:**
> And what exactly do I have to add to /etc/dhcp3/dhclient.conf in order to point the machine to the right DNSs ?

****************************

In the mean time I managed to add 2 nameservers to /etc/resolv.conf
I restarted my machine and ... lo and behold ... it made connection to the internet right away! Hope this was not a coincidence and things stay like this. :D

look for this line: ```
supersede domain-name-servers;
``` if its commented (theres a # in front of it) uncomment it(remove the #) then add the dns servers, seperated by commas like this: ```
supersede doman-name-servers xxx.xxx.xxx.xxx, xxx.xxx.xxx.xxx;
```
and replace xx.xxx.xxx.xxx with your dns servers. (or dns server, if its just one)

---

### Post by lfys on 2006-09-25
I just had my fourth start WITHOUT DNS-problems.
Another coincidence or is the problem REALLY solved? :D

*************************

Hey! No! AGAIN the same problem ...

---

