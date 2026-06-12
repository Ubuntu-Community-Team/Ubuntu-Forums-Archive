---
title: "Home Network access between ubuntu"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by jonroc on 2008-04-10
Hi to all! 

Thanks in advance for reading

I have been working with ubuntu for some time now (1 year) to do everything i need with a computer. I have this weird network problem i have no clue how to solve it. 

I have a Desktop running ubuntu and a laptop with ubuntu aswell.
My laptop is a Fujitsu Siemens Esprimo Mobile with poor suport to ubuntu, so i have ndiswrapper to have internet. The internet works fine over Wifi, however i cant access my desktop. 

If i ping my desktop i get "host unreachable" the same when i try to ping my laptop from my desktop.

the 2 computers are connected to a router (desktop wired and laptop wireless) with static ip's.
From my laptop i can ping the router but not the computer (same with desktop).

i have tried some things concerning my network configuration, using dhcp, putting down ipv6, changing /etc/net All bad. 
What i dont understand is why neider computer can ping, so i dont know which one has the problem (or both). 

Is it a problem in my router configuration? 

I really have no idea how to solve this...

thanks a lot for any idea! :)

cheers
jonroc

---

### Post by notwen on 2008-04-10
Are you pinging the internal ips of each specific machine?  Are you wanting the machines to see one another for additional reasons other than pinging?

---

### Post by jonroc on 2008-04-11
Hi! 

thanks a lot for answering.

I was able to solve the problem! : )

I reseted my router to factory defaults and disabled DHCP. I removed firestarter and it worked! 


Any way thanks :)

cheers
jonroc

---

### Post by njparton on 2008-04-11
You should leave DHCP on in your router, it was more likely a firestarter/iptables issue that was causing your problem.
 
If you're behind a secure router then search for how to flush iptables to reset it to it's default configuration and you should then be able to turn on DHCP in your router.
 
If you don't, new network devices may not be able to get an IP address.

---

### Post by mikmark on 2008-04-11
Are you wanting the machines to see one another for additional reasons other than pinging?

---

### Post by jmstern on 2008-04-11
After only 1/2 cup of coffee- the first thing which comes to mind is 

what are the IP addresses / Subnet masks?   Are the two devices on the same subnet?

eg: if you're using IPs of 

machine 1 192.168.0.2 / 255.255.255.0 
machine 2 192.168.2.2 /255.255.255.0  they will give the results you describe

I found that although convenient - DHCP is more trouble than its worth on small networks.  if there are only a few devices - better to hard code them.  Makes easier troubleshooting.

---

