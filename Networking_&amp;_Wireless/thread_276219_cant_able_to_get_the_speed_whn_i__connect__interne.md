---
title: "cant able to get the speed whn i  connect  internet to my pc but i can in other pc"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by sxydude on 2006-10-12
im usin windows xp as an operatin system....i got an internet connection with a speed of 256kbps..whn i connect this to my pc i cant able to get the max speed while downloadin...im gettin a max speed of 5kbps...but whn i connect the same to other pc im gettin a speed of 30kbps....

this is the problem im facing from the past 3days..so any one can help me out of this...plzz give me the suggestions how to cope up this problem..

---

### Post by bonzodog on 2006-10-12
let me get this straight; you have 2 PC's, sharing an internet connection, one with Xp and one with Ubuntu? am I right?
The one with Xp is fine for download and connection speed, but the Ubuntu one is slow?

If that is the case, then it sounds like an IPv6 clash. ONE of the things you can do is to disable IPv6 in Firefox, by typing:
```
about:config
``` 
in the address bar and type IP into the filter box. You will see it brings up a line with the words;
```
network.dns.disableIPV6
```

right click on that line, and click 'toggle' so it is set to 'true'.

look further down and you will see:
```
network.http.pipelining
```. 
again, right click on this line and toggle it to 'true'

the line below it has the words:
```
network.http.pipelining.maxrequests
```. Change the value of this line to something like 15.

That should speed up your Firefox browsing experience. Search these forums for a way to turn off IPv6 altogether.

---

### Post by sxydude on 2006-10-12
Thanks for giving the reply...

Both of my pcs r with xp only.....n the other thing is im not sharing the internet connection....im just unpluggin the wire and connecting it to the other system with same operating system...i think the problem is with my system networking configuration...

so any help from you on this...

---

### Post by Superdarion on 2007-01-25
You do realize this is ubuntuforums, right...? These are forums for ubuntu users with ubuntu issues.

Regardless, maybe the problem is the slow PC having a crappy old card or, more probably, the router's firewall (or any other firewall active) is blocking your signal. Check for windows firewall (There's an icon on the control panel) and then check for the router's firewall, if present.

You should try getting help in some other forum, one that is Windows-related. This isn't the right place to ask.

---

