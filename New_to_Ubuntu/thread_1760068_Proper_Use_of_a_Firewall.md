---
title: "Proper Use of a Firewall?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-16
Hi all,

For anyone looking to hack me, I have a firewall and know how to use it [img]http://i366.photobucket.com/albums/oo107/TienGK/th_4539_eusa_shifty.gif[/img]

For everyone else, I understand that firewalls prevents applications and attempts to connect into and out of a computer. So if I set a firewall to block port 22 in and out my computer, it'll block anyone trying to connect to my ssh server and block me trying to connect to a ssh server. This is as far as my knowledge extends.

So my question is, if I have nothing running/showing up from [shields up](https://www.grc.com/x/ne.dll?bh0bkyd2), what use would a firewall be for me? Do I *really* need one? Do I have one already installed by default?

Massive thanks for the mightily confused.

---

### Post by doas777 on 2011-05-16
no, you only really need a firewall if:
1) you wish to filter outgoing ports to prevent applications from connecting.
2) you have services that you wish to allow to some parties but not to others
3) you wish to protect your IP stack from malicious packet-based attacks (shoudl not be a concern on linux).

a external computer can only connect to a port that is open (eg: there is a program listening on that port,  and it is allowed by firewall). if you have no open ports, then no one can connect to you, firewall or no.

---

