---
title: "Internet problem"
date: 2005-08-27
forum: Networking &amp; Wireless
---

### Post by nischg on 2005-08-27
Hello:

I am having a problem with the internet connection in my box. The thing is I can only surf some web sites. As matter a fact only Google. I can search for stuff but I can’t access the results. I can’t access any other web site. When I try to apt-get something it stops in the middle of the download process. 
I’ am connected through a home server running XP SP2 with DHCP on.

Please consider that I’ m new to the whole Linux environment. 

Thanks in advance.

---

### Post by numberexhaust on 2005-08-27
Is this problem on a wireless connection or a hardwire?  It may be possible that you are connecting long enough to get to google.com and then the connection dies.  (It's a long shot, but maybe).

Try to sudo ifdown wlan0 and then sudo ifup wlan0 in a terminal.  If that doesn't work I'm not sure where to go.

---

### Post by nischg on 2005-08-27
[QUOTE=numberexhaust]Is this problem on a wireless connection or a hardwire?  It may be possible that you are connecting long enough to get to google.com and then the connection dies.  (It's a long shot, but maybe).

Try to sudo ifdown wlan0 and then sudo ifup wlan0 in a terminal.  If that doesn't work I'm not sure where to go.[/QUOTE]


thank you for your reply. Ive got my connection on hardwire. I dont think the problem is that i can connect to google (or any other site) for a while and then it dies since i can always come back to google and search regardless of the uptime.

any clues?

---

### Post by HarabanaR on 2005-08-28
I'm ina simular problem.

I just installed Ubuntu 5.04, and i have set the ip address to be static on eth0 and i haveg gone throught the values i set and it should be correct as I set up the network here.

I can ping from other machines, wireless laptops, win2003 server and my main computer (running winxp) but this my ubuntu box will not ping locally nor will local machine ping the ubuntu box. 

I have a ADSL router which is my DHCP server as well. But setting the eth0 to get an ip from the DHCP server will not work either. 

Is there anyone there that can help me ?

edit: I found out why i did not get any ping results. My NIC card was bad. I put in another one and it workd. Thanx any way :D

---

