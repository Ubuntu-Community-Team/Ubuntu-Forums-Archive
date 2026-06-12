---
title: "Turn Ubuntu into Wifi Router/Access Point?"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by jago25_98 on 2008-11-14
I think I know how to do it by hand, but I'm looking for a guide that can help me avoid missing any steps.

What I know so far:

iwconfig --master or something like that
iptables PREROUTING / masquerade
DNS server, DHCP server

^ may which to separate the above with colinux into a separate distribution

---

### Post by nixscripter on 2008-11-14
You've got the parts right, I think, although you don't need DNS if you can masquerade, since DNS requests will be forwarded.

Here are articles for each:

The wireless access point (should work similarly, though this is on Debian): [http://www.linux.com/articles/55617](http://www.linux.com/articles/55617)

The DHCP server: [http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

IP masquerading: [http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)

Hope this helps.

---

### Post by jago25_98 on 2008-11-15
Thanks.

There is help to do this, but sadly it seems to be in the form of a new distro. I'll get typing.

---

### Post by nixscripter on 2008-11-15
What do you mean? I think Ubuntu should be able to do it. Is there something specific you're having trouble with?

---

### Post by jago25_98 on 2008-11-17
I just mean, it's ok, but wouldn't it be good if there was an application to automate the process?

---

### Post by nixscripter on 2008-11-17
Sure it would. That's why I used to love Macs in days past, they had a lot of built-in configurability.

Unfortunately, the drawback of the open source software ecosystem is that it's not very organized. I would imagine people set it up once by hand, and either write a script to manage it from then on, or just don't mess with it. Either way, the result is that it's not easier for anyone else the next time. Someone needs a lot of spare time and the desire to do it over and over again (like some sort of networking contractor) -- as well as the desire to give it away under the GPL for Street Cred.

In short, this is item number #10,332,912 at the bottom of that long list actually kept on SourceForge somewhere: "if you have 100 hours of spare time, write this for me!"

---

