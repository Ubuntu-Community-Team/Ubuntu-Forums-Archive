---
title: "University Wireless Access"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by silent_ on 2007-10-04
Hello, I've been trying to connect to my university wireless network, but am unable to do so. I can set the essid to the proper name, try to get dhcp, but I can't access the login screen. The system (through windows) works as follows: Connect to network -> select airuc and connect -> gain local connection -> open browser, which automatically loads a login screen when connection to the internet is attempted -> login -> gain internet access.

I'm thinking I'm missing something important. I'm not sure whether the network is infrastructure or ad-hoc.

Any help is appreciated

(edit): Here are the advanced network properties as they appear in windows:

[[IMG]http://img518.imageshack.us/img518/7732/37508149ud4.th.jpg[/IMG]](http://img518.imageshack.us/my.php?image=37508149ud4.jpg)

---

### Post by tgalati4 on 2007-10-04
Most likely infrastructure.

From a terminal, post the output of:

>ifconfig
>iwconfig


Your connection command will be something like:

>sudo iwconfig wlan0 essid "Your School's Network Name or Lame Fight Song" key open key 23:45:34:23:34 

>iwconfig  (to confirm that you are connected)

---

