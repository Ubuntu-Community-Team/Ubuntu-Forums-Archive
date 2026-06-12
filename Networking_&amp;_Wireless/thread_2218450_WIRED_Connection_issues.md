---
title: "WIRED Connection issues"
date: 2014-04-20
forum: Networking &amp; Wireless
---

### Post by izzydojo on 2014-04-20
i have ubuntu server 12.04 lts installed on a blade server i am currently making a Counter Strike server for a class project using it problem is im trying to get  wget [http://.](http://.).... but it wont connect so i used  ip link  and im getting 3 results back  lo  eth0  and eth1   both the eth say state down i cant figure out how to gain internet access anyone can help me i would be greatly appericate it  


thanks  mike

---

### Post by izzydojo on 2014-04-20
when i try to ping google.com it says  ping: unknown host google.com  when i try to restart network (sudo service networking restart) error says   stop: Unknown instance: netowkring stop/waiting  im completely stumped now

---

### Post by steeldriver on 2014-04-20
What are the contents of your /etc/network/interfaces file?

---

### Post by Danger_Monkey on 2014-04-21
It sounds like your NIC isn't configured or there is no routing to the Internet.  In addition to pasting the contents of the interfaces file that Steeldriver suggested, please incluse the output of the following:

```


ifconfig
netstat -nr


```

That will show where traffic is being routed for the default gateway, and what your NIC really thinks it is doing.

-DM

---

### Post by izzydojo on 2014-04-23
ya it was missing auto eth0  and stuff so i did that and it started to work correctly  Now only issue im having is the Linux dependecy tree files i need for my servers purpose seem to no longer exist anywhere i look -.- quite annoying

---

