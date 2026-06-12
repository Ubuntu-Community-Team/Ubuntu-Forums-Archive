---
title: "HOW-TO ssh over the internet"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by lazertek on 2008-07-15
setting up ssh over a LAN is pretty straight forward but when it comes to setting it up to be accessible over the internet it has a little more steps to it...

I have a router through which all my computers connect wirelessly/wired.... Now lets say I want to setup a computer in this network to be accessible by over the internet using ssh...

How would I do this... Remember that the computer is connected through a router that gives it it's ip address through DHCP....  A complete guide on how-to this will help me out along with a whole bunch of folks who have a hard time with ssh-ing over the internet...

---

### Post by starfleetcaptainrob on 2008-07-15
Agreed.  Anyone know where one could find this info?

---

### Post by lazertek on 2008-07-16
Wow this is wierd! Someone just replied to this post twice and now they just dissapeard..

---

### Post by dmizer on 2008-07-16
1) secure ssh >

- change the default port (ex. 11111): [http://ubuntuforums.org/showpost.php?p=1010166&postcount=5](http://ubuntuforums.org/showpost.php?p=1010166&postcount=5)
- use encrypted key authentication: [http://ubuntuforums.org/showthread.php?t=30709](http://ubuntuforums.org/showthread.php?t=30709)

2) forward the new ssh port to your server >
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

3) set up a dynamic domain account >
[https://help.ubuntu.com/community/DynamicDNS?](https://help.ubuntu.com/community/DynamicDNS?)

4) ssh to your computer with the following command >
```
ssh usernam@your.dynamic-domain-here.com -p 11111
```

---

### Post by lazertek on 2008-07-16
there goes a better explanation... I'll post up agian once I try it out... Just a little overloaded for now... Wi

---

