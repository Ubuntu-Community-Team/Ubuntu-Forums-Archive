---
title: "NetworkManager without DHCP?"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by Sargonmetal on 2006-09-06
Hi,

I use NetworkManager 0.6.2 to manage my wireless connections. The thing is that when I want to access to a non DHCP server, I can't since it can't assign a correct IP address. 

I've tried to do it manually with the **inet** command, but when I reconnect to the non DHCP server, that IP that I assigned with the **inet** goes away and the wrong IP address reappears.

Any ideas? I'm sure it's quite easy to solve, but I'm a newbie on this...
Thanks in advice!

Sargon

---

### Post by wieman01 on 2006-09-06
NetworkManager does not work with Static IPs... That's one of the restrictions next to lack of support for hidden ESSIDs, etc.

You need to configure your network manually if you need Static IPs.

---

### Post by Sargonmetal on 2006-09-06
Ouf... I wished I wouldn't hear that... Is that means that I'll have to turn off NetworkManager and change my interfaces configuration file? 

Well, thanks for the info :)

---

### Post by wieman01 on 2006-09-06
I am afraid so... NetworkManager won't help you in your case.

Two useful threads:

[http://www.ubuntuforums.org/showthread.php?t=225290&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=225290&highlight=wpa2+rsn")
[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

---

### Post by Sargonmetal on 2006-09-07
That's really useful for me. Thanks!

---

