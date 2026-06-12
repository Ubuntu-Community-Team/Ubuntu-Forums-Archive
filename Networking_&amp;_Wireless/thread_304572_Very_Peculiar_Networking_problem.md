---
title: "Very Peculiar Networking problem"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by alimovz on 2006-11-22
Ok here is my problem. I just installed Ubuntu. I have a DSL modem that runs a DHCP server and gives out addresses fine. I boot into the new box. It's ip address is properly set according to the ifconfig command. I can ping google.com, ping goes perfect. 
But if I run Firefox and type google.com in the address bar, the browser will look it up ok but will not actually connect to it. On the status bar it will say connecting to google.com and it will stay like that until it times out. 
Now if I enter google's IP in the browser it work perfect. If it is a DNS issue, that why does the ping google.com work without a problem? 
Any suggestions?

---

### Post by dmizer on 2006-11-22
it's not a dns issue.  this is an ipv6 issue.  in firefox, browse to: about:config
and search for ipv6.  double click it to turn it off.

edit:
almost forgot ... restart firefox to enable the setting change.

---

### Post by alimovz on 2006-11-22
Well... it worked. Thank you. Let me just point out that the problem took me most of the evening to figure out and really doesn't make any sense to me.

---

### Post by dmizer on 2006-11-22
as for why ... it's a bug in firefox that apparently has reappeared (there was no problem with the 1.5 release of firefox).

a quick search on this forum would have gotten you the results you needed as there are many threads with this problem.  there's even a wiki page dedicated to it: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

my search with: "firefox webpages ping" turned up at least 3 threads that have the answer, and several others that mention ipv6.

my intent here is to merely illustrate that just because you couldn't find the answer ... does not mean that your answer didn't exist.  furthermore, i'd like to point out that once you posted, i responded to your request within 60 seconds.

for more information on ipv6: [http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)

---

### Post by stream303 on 2006-11-23
If you run into any lingering dns issues in the future, you might want to check this out, but glad to see that you've fixed the immediate problem!

[http://www.ubuntuforums.org/showthread.php?t=305275](http://www.ubuntuforums.org/showthread.php?t=305275)

---

