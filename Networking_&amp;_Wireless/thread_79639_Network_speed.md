---
title: "Network speed"
date: 2005-10-20
forum: Networking &amp; Wireless
---

### Post by foxy123 on 2005-10-20
I've got desktop and laptop, connected in a wireless network. The desktop has a  Ethernet card and connected to a wireless AP which has 11 MB/s speed. The laptop has a PCMCI card which is also 11 MB/s (it's actuall 54g, but I do not know how to get it work a 54g with ndiswrapper). 

However if copying files from desktop to the laptop (ad vice versa) over network I've got only 300 kBytes/s. Why is it so slow?

---

### Post by kidcharles on 2005-11-18
I'm having the same problem. When I try to transfer files from my Ubuntu 5.04 machine to my 5.10 machine I get about 200-400 KB/s which are internet speeds, not LAN speeds.

---

### Post by lonetree on 2005-12-13
I fact this has been discussed for many many times, and many people give different answer but none of it that I have found actually solve.

I tested out with wireless and wired connection. To be frank, wired connection has a slightly improvement in speed but still it is slow. I compared this with MS machine, transferring same file from one machine to another. Wonder why too. Seems that either no one has notice this or maybe some has notice but just dun care. Or maybe most of the users are just using it as a pure desktop, not in a LAN enviroment.

:-)

Regards,

---

### Post by Schmic on 2006-02-19
I would like to revive this post as i have the same query?

Simple file transfers over wired lan use 300-400k max, over wireless 200-300k max (using samba) 700k using just nfs. Over wired i have tried setting up ftp server and ftp over wired and i get max 3500k which is better but still not near maximum.

Now to add to this i can get 500k over my adsl connection which is near maximum for my connection.

Why is this so, surely less than 1% lan utilisation is not the most efficient that ubuntu can maintain or it is not at all a network OS. Please can someone offer a solution to at least get it to rival windose in this manner[-o<

---

### Post by Milamber_Cubed on 2006-02-19
I installed apache on one of my ubuntu machines and was getting over 1MB/sec transfers over my wireless network (54Mb). Curiously, I can actually download (again over the wireless) files from the internet faster than this - which makes no sense. 

Also, the further away the machines are from the AP the worse the transfer speed gets - this happens to me when downloading from the internet too. You can see this youself if you try and wget a large file (ubuntu live cd, for example) - moving away from your AP will make the speed drop. This may have something to do with the poor performance people are seeing over wireless.

---

### Post by Schmic on 2006-02-19
Just tried removing ipv6 from my machine and it increased the transfer speed significantly, getting approx 15% utilisation which is alot better but still not quite what i am hoping for. I am transferring a file about 350mb as test which was taking 40 mins previously but now is down to about 5 mins.

search the forums if you want to try dissabling ipv6.

---

### Post by bscbrit on 2006-02-19
Here's the info on disabling IPv6:

[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?)

---

