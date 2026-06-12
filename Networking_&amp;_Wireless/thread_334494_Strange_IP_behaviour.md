---
title: "Strange IP behaviour"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by JKoder on 2007-01-09
Hello
I have a questions. sometimes i use WindowsXP and UBUNTU ( but now ONLY ubuntu 6.10)
Can anyone tell me why in windows i have an IP number like: 86.xxx.xx.xx and in Ubuntu i have : 89.xxx.xxx.xxx, i need to mention that my IP is assigned via DHCP.
If i switch back to Win i will have the first IP, if i am using ubuntu i will have the second IP.
I can manualy set the first IP but i whant to find out why this is happening.

It does not happened before.
Thank you , for anyone cant talk to me about this !

---

### Post by aliyanage on 2007-01-09
well, I mean as long as you get out to the internet and have a connection I wouldn't really question myself to much about it, but did you already try out this command and see what happens?

```
sudo dhclient
```

and after just double check the ip address by doing:

```
ifconfig
```

aliyanage

---

