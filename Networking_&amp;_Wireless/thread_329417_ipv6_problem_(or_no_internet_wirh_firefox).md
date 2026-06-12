---
title: "ipv6 problem? (or no internet wirh firefox)"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by moishz on 2007-01-01
Hi all
I am new to Linux in general and ubuntu in particular. I have at home a network that includes a modem - eci bfocus 312 and a router of Motorola which is a bit faulty, the problem with my Motorola router is that his wan socket is not working therefor I configured my modem to act as a router and put him in to one of the LAN connections in the Motorola router. During installation ubuntu did a fine job in detecting my network but it gave me an error when it tried to get updates. After installation I got problems with the fire fox and the synaptic thingy , the synaptic didn’t want to get any updates and the fire fox was too slow in browsing until it timed out. 
Note: pings got in with no problems. 
So I did my searches through the forums and what I came to understand is that I might be experiencing   problems with ipv6 and I found some solutions of how to disable the ipv6. There were 3 ways to address the problem :idea: 
1. To change the alias files(this I did not want to do as I am new to Linux and I don’t want to muck around with system files which I don’t understand + I got the impression that when the system updates it self the files that are configured might be updated too ruining my work ):confused: 
2. To configure something in the fire fox to disable ipv6 in it- didn’t understand where to configure the fire fox and I think the problem is deeper and want to take care of it on a bigger scale.
3. To add a file by the name of bad_list to /etc/modprobe.d with the following text in it “alias net-pf-10 off”.
So I tried the third solution rebooted my system and... youck nothing gurnisht. :mad:
Please if anyone has a better sugestion as to the source of my problem I still don’t want to muck around with the alias files.
Thanks a bundle.

---

### Post by moishz on 2007-01-01
changed in firefox 
[http://ubuntuforums.org/showthread.php?t=329325&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=329325&highlight=ipv6)
so i can browse now but still problems with synaptic etc.:neutral:

---

### Post by handy on 2007-01-02
Have a look at the DNS section of this how-to?

[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

---

