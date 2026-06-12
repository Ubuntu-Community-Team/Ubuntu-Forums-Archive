---
title: "Wireless works, wired doesn't?"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by pearldrums on 2010-09-06
Almost everyone has spent time troubleshooting wireless networks, but for some reason I can only get wireless working on 10.04. My wired will not connect. I have no idea where to start. I know the connection is good because I can use the same PC in windows using only the wired connection. What can I do?

---

### Post by ulfj on 2010-09-06
Did you look in the network manager and see if it is recognised there? I ran into this when I first installed 10.04 and it wasn't there I added the connection in the network manager and had to restart and viola it worked. I don't understand why this worked it just did. Hope this gives you a starting point.

---

### Post by pearldrums on 2010-09-07
It is there. I fooled around for a while and decided to specify an IP, it started working for the night. Now for some reason it says its connected but wont send any information on Ubuntu or Windows, wireless is still working. I'm going to upgrade the router's firmware because it will not let me access the admin page. Something wonky is happening.

---

### Post by kenn123 on 2010-09-18
Same problem with me...  wireless works but wired doesn't, on Dell Inspiron 1525.  I tried to get it to work a bit in the past with no success, but it is bugging me again so I may give it another go.  It had worked fine in 9.04, but stopped after the 10.04 upgrade.

---

### Post by gandaran on 2010-09-18
do you have dhcp server enabled in the router?

---

### Post by kenn123 on 2010-09-18
Yes... wireless/wired router uses dhcp.  I made some progress... using only wired (eth0) I can connect to Internet IP addresses, but DNS doesn't seem to work.  Works ok on wireless (eth1).  I'll keep poking around with it as I have time, but any help would be appreciated.

---

### Post by gandaran on 2010-09-18
> **kenn123 said:**
> Yes... wireless/wired router uses dhcp.  I made some progress... using only wired (eth0) I can connect to Internet IP addresses, but DNS doesn't seem to work.  Works ok on wireless (eth1).  I'll keep poking around with it as I have time, but any help would be appreciated.
if it is a DNS problem then try opendns 208.67.222.222, 208.67.220.220 use the network manger wired IPv4 configuration tab to set it up.

---

### Post by kenn123 on 2010-09-18
Adding the opendns servers to my network connections > wired > ipv4 settings tab didn't work.  I changed the "method" to "Automatic (DHCP) addresses only", and tried one and then both servers as the "DNS Servers".  When I'm connected with just wired, I can get stuff to resolve with the host command if I specify the server: host <domain> 208.67.222.222.  Using my ISP's servers works too.  But with the regular host <domain> command it doesn't work.  My ISPs DNS servers are in resolv.conf.

One interesting thing:  When I left-click on my NetworkManager Applet, it shows at the top "Wired Network", "device not managed".  Could there be something that is overriding the network manager settings for eth0?

---

### Post by kenn123 on 2010-09-18
Also, in my network manager connections, wired tab, the "Wired connection 1" shows "Last Used" as never.

---

### Post by kenn123 on 2010-10-14
I found a solution for my problem (no host resolve with eth0 wired but eth1 wireless works fine).  It was post #17 in this thread: [http://ubuntuforums.org/showthread.php?p=9319878](http://ubuntuforums.org/showthread.php?p=9319878)

Kenn

---

