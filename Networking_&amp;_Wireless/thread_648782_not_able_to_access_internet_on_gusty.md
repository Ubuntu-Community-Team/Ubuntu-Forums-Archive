---
title: "not able to access internet on gusty"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by drthomasmathew on 2007-12-24
hi,
using netgear wg311v3 wireless with ndiswrapper fully configured. Static ip alloted, routing ok, able to ping to google,ipv6 disabled,interfaces/network file is copied from feisty, which is working fine. but after URL is entered in firefox and thats it, the progress bar shows"waiting for google.co.in..." does not go further.please help me on this issue.thanks.

---

### Post by koala114 on 2007-12-24
In Windows is that OK?
Make sure you DNS is your router ip address

---

### Post by drthomasmathew on 2007-12-24
i am able to access internet with almost identical setttings on fiesty, which is intalled on another partition. dns is ok i am using static ip hence i have added name servers in /etc/resolv.conf.

---

### Post by koala114 on 2007-12-24
check to see  your output of ifconfig -a

---

### Post by cjhermann on 2007-12-24
Hi.
I just installed Gutsy on my parent's computer from the Live CD.
I was experiencing the same problem:
- IP address was acquired just fine
- I could ping & mtr google & other websites
- I could not access the web with firefox, it would say "Connecting to <website>...

I downloaded about 200MB worth of updates, and hey presto - just like brand new.

Hope this helps.

---

### Post by drthomasmathew on 2007-12-27
how do you update 7.10 without internet connection? the synaptic manager nor 'apt-get upgrade/update' does not work.i  have been trying otherwise, one funny thing is that in lynx when google is being loaded it goes up to the stage where one cookie is accepted and then while accepting the next cookie it just hangs. the ping to gooogle also resolves the ip address and transmits but no packets are recieved , i dont know whether this is normal or not. i tried DHCP and it gets an ip alloted, gateway is also ok.

---

