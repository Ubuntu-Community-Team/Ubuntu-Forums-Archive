---
title: "XP PC's cannot log onto my Ubuntu domain"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by NeonSamurai on 2008-04-03
I've built a mini network of which most of the PC's are XP, however I have three old laptops running 7.10. One '**C**' being the main DNS, another '**A**' being the file and print, FTP and secondary DNS and a third just acting as a terminal. 

All the XP PC's can see the two DNS machines and have had them added to their TCP/IP setting as primary and secondary DNS servers. The network '**A.org**' can also be seen by these machines and accessed. Files can be shared and print jobs sent with no problem.

However when I try to connect any of these XP machines to the **A.org** domain they flag up a message saying that they can't see the domain, but they can connect to it as a workgroup.

Any ideas why these XP machines only recognise my domain as a workgroup?

Many thanks


Mark

---

### Post by koenn on 2008-04-03
nothing in your post indicates you actually have a domain.
you need to set up a domain controller if you want a "domain". 
Before you do that, ask yourself if you really need / want it.

---

### Post by NeonSamurai on 2008-04-03
Hi Koenn,

In all honesty I don't need a Domain, however this is really a learning exercise for me. I've been using old PC's at work to make this network and brush up on my Linux/networking skills.

Basically I followed the instructions[ here on the ubuntu forums]("http://ubuntuforums.org/showthread.php?t=236093") to build a DNS server, but maybe I've misunderstood what it should be capable of doing. At the moment I'm trying to enable a domain login so that I can configure the users to get access to shared folders etc without having to map them all in individually.

So does this mean that I don't actually have an active domain?

Thanks


Mark

---

### Post by mozetti on 2008-04-03
DNS provides doman name resolution - basically, when you type 'www.ubuntuforums.org' in the browser, the DNS server finds out what the IP address is and then tells your browser so it can navigate to the page.

To have a domain, you need a domain controller. For Windows clients I think you'd need to set up Samba to be your Primary Domain Controller (PDC). In practice, you should always have a Backup Domain Controller (BDC) in case the PDC fails. However, Samba can only act as a PDC, not a BDC and you can't have more than one PDC.

Also, are the XP machines running the 'Home' or 'Pro' version of XP -- 'Home' doesn't have the networking tools for connecting to a domain, only a workgroup.

As far as having domain or not, it really depends on what you want to do and how many machines you'd need to configure. If it's just a matter of getting all the machines to access the Ubuntu shares then I'd opt for one of these two options:

1) Create the connections to the Ubuntu shares on one XP machine, copy the shortcuts from 'My Network Places' to a floppy or USB disk, then paste the shortcuts on each machine.

2) If the Ubuntu share names won't change, and you won't be adding new shares, write up an autoexec.bat script to create the 'My Network Places' shortcuts when booted (if they're not already present) and put it on each XP machine.

---

### Post by koenn on 2008-04-03
That thread is about DNS, and refers to domains such as bubble.com or ubuntuforums.org, i.e domain names as in DNS "Fully Qualified Domain Name", a naming scheme for network hosts.


What you're thinking of is a Windows NT-style domain, or a microsoft active directory domain, or, more general, an LDAP domain, for computer and user authentication and account management. Different thing entirely.
You can implement such domains on Linux with Samba and/or OpenLDAP and the likes.

Go have a look at the samba documentation - [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
or search google and/or the forums, the community  documentation ( [https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers) ) , ....  for anything about samba and domain.

---

### Post by NeonSamurai on 2008-04-03
Thanks guys. That's just what I needed to know. I was expecting my DNS to deliver the goods, but I'll go and modify the file and print. At the end of the day this is all a big learning experience, so if the PDC craps out then it's no biggie.

Thanks again.

---

