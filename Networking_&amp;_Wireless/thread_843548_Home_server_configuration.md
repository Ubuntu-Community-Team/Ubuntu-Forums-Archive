---
title: "Home server configuration"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by Jay I. on 2008-06-28
Hi! i've got two pc'c both running ubuntu. Both are connected to adsl modem that works as a switch. I also have an apache running on one of the machines and want to make it accessible from the outer world while keeping the second machine completely invisible from the outside. Also i want to enable file sharing between the machines. I know that there are tons of different tutorials on this subject but i'm such a noob in server administration))) I expect very few users - by now only one so i dont think i need to install a server-oriented os. It will be nicely if you give me some links to some simple tutorials or articles. Actually i got stuck at setting up NAT via my modem's web interface so related articles will be of great interest for me.

---

### Post by pytheas22 on 2008-06-28
I don't know of any tutorials off the top of my head that would help you, but I think it will only take a couple of steps to get the configuration you want.

First, log into your switch's configuration utility.  There should be an option somewhere where you can tell the switch to always assign the same IP address to a certain computer (you have to specify the computer's MAC address to identify it).  Tell it to do this for the machine that you want to be visible from the outside.

Then look for an option to configure port forwarding.  Tell your switch to open port 80 (the http port, which Apache uses) and to forward all traffic on port 80 to the local static IP address that you just configured.  If you need to open other services (e.g. ssh, vnc) on that computer to the Internet, repeat the process for the appropriate port numbers.

Now you're all set; you'll be able to reach the Ubuntu machine hosting the Apache server from anywhere on the Internet, while your other computer will remain invisible.

As for file sharing, that's really easy.  Open up the folder containing the files you want to share, right-click, select Properties and click on the Share tab.

---

### Post by Jay I. on 2008-06-28
I found how to redirect requests to IP but didnt find how to always assign the same IP to a certain MAC. I'm gonna upgrade firmware so maybe new user iterface will be more friendly to me. At least i know what i need and where to search for an answer. Thank you very much.

---

### Post by pytheas22 on 2008-06-28
It's possible that your switch doesn't have an option to always assign the same local IP to the same computer, but you should at least be able to tell it to always forward certain kinds of traffic to a certain computer...e.g. there should at least be an option to say, "all traffic on port 80 should go to the machine with MAC address XX:XX:XX...."

---

### Post by Jay I. on 2008-06-29
Yeah i found this option. But i still doesnt work((. i asked some guys form the company that produces the modem. Hope they will show me the right way.

---

### Post by pytheas22 on 2008-06-29
You may also want to contact your ISP to make sure it's not blocking the traffic.  Some providers block certain ports to make it hard to run a web server from a normal residential connection, among other things.  Or it could be your switch at fault--I had a router once where port forwarding would sometimes work and sometimes not, and it came down just to the hardware (or maybe the firmware on the hardware) being bad.  I assume that this is rare, however.

---

