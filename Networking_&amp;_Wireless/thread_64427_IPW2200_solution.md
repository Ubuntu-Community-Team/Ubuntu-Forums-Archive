---
title: "IPW2200 solution"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by tbasten on 2005-09-11
Hi, I dont know if this will work with everyones wireless card but this is what seems to work with my laptop and a few of my mates laptops.

From a clean install of ubuntu ipw2200 is working fine. All you really have to do is set your card into Ad-Hoc mode. Simply type this command in

```
iwconfig eth0 mode ad-hoc
``` 

replace eth0 with your card location, (e.g ra0, eth1 etc)

Then if you got wep keys you need to put in goto Network setup then properties of your wireless adaptor. Your will see WEP Key, put it in there.

Regards

dYnA

---

### Post by mlomker on 2005-09-11
Ad-hoc allows PC's to connect to one another directly, whereas managed mode is used when connecting to an access point (wireless router).

---

### Post by tbasten on 2005-09-11
I understand the difference between Ad-Hoc and Managed. I was just try to show people what to do to get a simple setup up and running. If you have a wireless access point you can use ad-hoc on more then 1 computer connecting to the access. At home i have 4 computers in ad-hoc mode and it works fine.

Cheers

dYnA

---

