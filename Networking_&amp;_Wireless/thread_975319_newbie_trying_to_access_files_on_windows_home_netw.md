---
title: "newbie trying to access files on windows home network"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by KnavishClout on 2008-11-08
Hello all.  I have used Ubuntu before and I love everything about it EXCEPT that when your new it can be difficult to learn how to accomplish a given task.

In this case, I have four computers in my home connected to a router (2 Vista, 1 WXP, and now 1 Ubuntu 8.10)  When this computer had Vista on it, I could very easily access the shared files on the other PC's in the home.  Now that it has Ubuntu, I go to "Places>Network" and I can see the other computers but when I double click on them, I don't see any of the files or directories.  

I have seen other threads that offer what is probably a great solution, but I don't understand any of them because none of them were written for linux newbies.  I prefer to use GUI whenever possible, but if you do give me code, please be as specific as possible.  Assume I'm a complete moron, because (when it comes to linux) I really am.

Thanks!

---

### Post by Steve1961 on 2008-11-08
> **KnavishClout said:**
> Hello all.  I have used Ubuntu before and I love everything about it EXCEPT that when your new it can be difficult to learn how to accomplish a given task.

In this case, I have four computers in my home connected to a router (2 Vista, 1 WXP, and now 1 Ubuntu 8.10)  When this computer had Vista on it, I could very easily access the shared files on the other PC's in the home.  Now that it has Ubuntu, I go to "Places>Network" and I can see the other computers but when I double click on them, I don't see any of the files or directories.  

I have seen other threads that offer what is probably a great solution, but I don't understand any of them because none of them were written for linux newbies.  I prefer to use GUI whenever possible, but if you do give me code, please be as specific as possible.  Assume I'm a complete moron, because (when it comes to linux) I really am.

Thanks!

That used to happen to me a lot, and it turned out to be something to do with netbios resolution problems.  Anyway, the easy fix for me was to simply add the computers I wanted to access to my /etc/hosts file.  This, of course, is only possible if the computers have been allocated static ip addresses (although that's easy enough to do in windows).

To add the computers to /etc/hosts just type

sudo gedit /etc/hosts

and then add each computer as in the example below (the last three entries):

127.0.0.1	localhost
127.0.1.1	steve-1000h

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.132 computer1
192.168.0.205 computer2
192.168.0.138 computer3

Change the ip and hosts names to suit.  Then in a terminal type findsmb to check that the hostnames resolve.

---

### Post by KnavishClout on 2008-11-08
Thanks Steve!  That worked perfectly.  I just went and gave all the windows computers static IP's and then added them like you said, and now all is well.

---

### Post by Steve1961 on 2008-11-08
Glad it worked for you :D

---

