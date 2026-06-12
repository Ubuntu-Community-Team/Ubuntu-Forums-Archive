---
title: "Unable to reconnect the mobile broadband, if signal drops for more than 3 hours"
date: 2018-07-18
forum: Networking &amp; Wireless
---

### Post by naveen.bathula on 2018-07-18
Hi,

I am working on Ubuntu 16.04 with Telit module for mobile  broadband. I am facing the problem in reconnecting the mobile broadband  once it lost the connection more than 3 hours. 

I was able to use  the mobile broadband until there is signal drop.If signal drop occurs  for a long period(more than 3 hours, it is varying at times), mobile  broadband is unable to re-establish the connection.As I have selected  auto connect option in the Mobile broadband connection GUI, it is  reconnecting if signal drop is less than 2-3 hours

When I checked  the system logs, I found that Network manager is trying to reconnect  for some time, if it is not succeed in reconnecting it is signaling  modem manager to kill the pppd daemon and switch to simple connect  rather than using pppd. Apart from it is removing some other modules. I have attached the syslog's while booting and terminating the mobile  broadband connection.

I tried with restarting network manager, modem manager and pppd daemon from systemctl but nothing worked, Can any one suggest the solution to fix my  problem.

[ATTACH]280440[/ATTACH]

Regards,
Naveen.

---

