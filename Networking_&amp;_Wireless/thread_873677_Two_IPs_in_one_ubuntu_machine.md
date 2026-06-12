---
title: "Two IPs in one ubuntu machine?"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by Abu_Dayya on 2008-07-29
I installed gutsy on a desktop at work that has two network cards. The cards are connected to different networks. Can I assign an IP to each one and access both networks at the same time? for example can I open two Terminal and telnet from each terminal to a machine on the two networks at the same time, without having to disable one card if I want to connect through the other one? hope that make sense.

Thanks

---

### Post by Abu_Dayya on 2008-07-29
May I also add that I installed the desktop version of Ubuntu

---

### Post by Archmage on 2008-07-29
Yes, you can assigne for each nethwork-care on IP. But of course you must tell the OS what network should be used with what IP.

---

### Post by Abu_Dayya on 2008-07-29
I'm sorry, I'm a little bit lost

So I can just plug two cables, assign an IP to each one, and be able to acces both networks at the same time?

or do I have to disable one network card in order to access the other?

---

### Post by ilrudie on 2008-07-29
You will have to set up different routes in order to accomplish this.  Essentially you have to tell ubuntu that machines with a certain ip address (or range) need to be accessed via a certain interface.  use man route to find out more about doing this.  Also netstat -rn tells you your current routing configuration.  be aware that route add does not make the routes permanent.  You will lose them when you reboot so make sure to add them to an rc script or the interfaces script if you want them to be permanent.

---

### Post by Abu_Dayya on 2008-07-29
I know how to manipulate the routing table (I'm a unix administrator, so it should be the same). But other than that, is there any other settings or configurations I should do?

Thanks in advance

---

### Post by ilrudie on 2008-07-29
I haven't done this but if you know how to do it in unix it should work pretty much the same way.  Just bring up the interfaces on the different networks and route them up correctly.

---

### Post by Abu_Dayya on 2008-07-29
Excellent.

Now I have another question:
what is the path of the rc script that starts network daemons and settings in ubuntu?

---

### Post by ilrudie on 2008-07-29
> **Abu_Dayya said:**
> Excellent.

Now I have another question:
what is the path of the rc script that starts network daemons and settings in ubuntu?

/etc/network/interfaces is a good place to add static routes.  It is also where the interfaces are configured.  For routes  put them in the stanza for the interface they belong to and prefix the route add command with up eg: up <command>

read man interfaces for more info on this.

---

