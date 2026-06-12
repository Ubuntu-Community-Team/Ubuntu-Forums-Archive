---
title: "wired network is disconnected you are offline"
date: 2015-02-22
forum: Networking &amp; Wireless
---

### Post by hemendra on 2015-02-22
Hello 
I have installed Ubuntu just now along with windows 7. The cable for getting net is connected with this and still it is showing that you are not connected or you are offline. When I am trying to connect it with a WiFi network then also no network is showing there. It is showing device notready for wireless and for wired it is showing you are offline. What to do now

---

### Post by tripp98 on 2015-02-23
What hardware are you working with?

---

### Post by hemendra on 2015-02-24
Hp Compaq Cq40 Core 2 duo 32 bit

---

### Post by Andra on 2015-02-25
is it DHCP?
If so, then it may be a problem with the DHCP server, which does not give a new lease because it is still valid for the other system. That is, Win has a valid lease and then Ubuntu cannot get a valid lease. Then you must get rid off the lease you don't need.

---

### Post by hemendra on 2015-02-25
yeah Thats DHCP 
Now what i can do for it

---

### Post by Andra on 2015-02-25
in Win:
ipconfig/release & net stop dhcp
maybe you should do it more than once until you really get rid off the address (and Internet connection :)). Then go to Ubuntu and see whether there is connection or not.
Try it and then you see whether this is the case of dhcp lease time.

---

### Post by hemendra on 2015-02-25
I have installed the 10.0.4 Ubuntu and this is inside the windows ( dual port) when I'm working on windows the net is working properly but when I switch my os to Ubuntu by restarting its not working here i am using wired net

---

### Post by Andra on 2015-02-25
well, and why can't you try what I described in my previous post?

---

### Post by hemendra on 2015-02-26
its output is

No Operation can be performed on Bluethooth network connection while it has its media disconnected
no operation can be performed on wireless network connection while it has its media disconnected

---

### Post by Andra on 2015-02-26
what's happening now - this computer cannot access Internet at all? Did you try to launch Ubuntu? Reset the router/modem?
what's the output of "ipconfig /all" ?

---

### Post by tripp98 on 2015-03-03
can you wire your laptop to your router.  this should get you online.  if it does follow the next steps

open system settings
Software & updates
additional drivers tab. - there may be something listed there that is not enabled. enable the proprietary driver
once enabled unplug the wired connection.
you should see wireless networks.

---

