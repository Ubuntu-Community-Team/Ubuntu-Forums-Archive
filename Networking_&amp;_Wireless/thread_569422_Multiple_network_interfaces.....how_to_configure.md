---
title: "Multiple network interfaces.....how to configure?"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by UbuntUser4389 on 2007-10-07
I am running Ubuntu 7.04 and I have a wireless network card and an on-board ethernet port. I am currently using my wireless to connect to the internet (wireless dsl modem). What I would like to do is connect a router to the ethernet port and be able to boot thin clients using LTSP. 

Is this possible? I am currently working on connecting to the router. I have it attached to the ethernet port but when i put in 192.168.0.1 into the browser, nothing comes up. So I am not sure what I need to do to configure the ethernet. 

I hope this is possible, I like to think that anything is possible with Linux!

Thanks for all your help!

---

### Post by chrisxp on 2007-10-08
i gave it a quick try with my ubuntu laptop with onboard wireless/ethernet and it didnt work..

im connected via wireless, plugged in the cable and did a "sudo dhclient eth0" and received no dhcpoffers, presumubly because the router already knows im connected via wireless and why should i want another connection via cable

i shouldnt think it would be possible, but it may be (im only a ubuntu newbie :P)

*bump*

---

### Post by DarkAgdistis on 2007-10-08
Hello,

I don't know if it helps but in those 2 threads, discussions about having multiple network interfaces have been covered.

[http://ubuntuforums.org/showthread.php?t=539777&highlight=multiple+network](http://ubuntuforums.org/showthread.php?t=539777&highlight=multiple+network)

[http://ubuntuforums.org/showthread.php?t=539777&highlight=multiple+network](http://ubuntuforums.org/showthread.php?t=539777&highlight=multiple+network)

Now, following the above questions, I would have an additional question :

I'm having a cable and a wireless connection to the net. I would like to use the wireless connection for browsing with Firefox and the cable one for Edonkey.

How can I tell each application to use a specific network interface ? :confused:

Thanks in advance !

Cheers
V.
*BUMP*

---

