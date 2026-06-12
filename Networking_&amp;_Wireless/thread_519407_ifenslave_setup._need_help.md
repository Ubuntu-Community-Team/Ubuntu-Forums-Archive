---
title: "ifenslave setup. need help"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by saadakhtar on 2007-08-07
i am trying to setup a 3 WAN network bond for my WIFI network at a apartment complex.
i have 3 ADSL lines that i can bond together to throttle bandwidth along with fail over. 
i am planning to use [**_this post _**]("http://ubuntuforums.org/showthread.php?p=549356#post549356")to setup the bond but i have a very simple question. Out of (eth0-3) i am bonding eth 1-3 and keeping eth0 for lan. the bond will be named bond0.
to make the bond work it is imperative to remove all other network interface entries from the /etc/network/interfaces file except for the loopback interface and the bond itself.
Now how would i have a lan interface for my access if i cannot specify it in my /etc/network/interfaces.

i would appreciate some help.

---

### Post by saadakhtar on 2007-08-07
any help.
how would i setup a lan interface for my clients behind this ubuntu box.
i know this is a silly question but its just not making any sense for me as it is.

---

