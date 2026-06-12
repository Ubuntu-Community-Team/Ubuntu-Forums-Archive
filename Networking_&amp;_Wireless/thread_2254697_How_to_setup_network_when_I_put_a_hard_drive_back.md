---
title: "How to setup network when I put a hard drive back"
date: 2014-11-29
forum: Networking &amp; Wireless
---

### Post by ruwan2 on 2014-11-29
Hi,
I have two PCs A and B. I used to have hard drive hdA and hdB with A. For diagnose PC B, I had moved hdB at PC B and it can connect to internet. Now, I put hdB back to PC A. There is no internet connection at PC A. I think that the home router connection does not change. On Network window, there is only the Ethernet address shown under "Wired" label. What procedures can restore my ubuntu 12.04 LTS internet connection? 


Thanks,

---

### Post by ruwan2 on 2014-11-29
Hi,
After I run the following commands, the internet works on this PC.

[COLOR=#0000ff]sudo service network-manager stop
[sudo] password for robert: 
network-manager stop/waiting
robert@Aspire-M5100:~$ sudo ifconfig eth0 down
robert@Aspire-M5100:~$ sudo ifconfig eth0 up
robert@Aspire-M5100:~$ sudo dhclient eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd

robert@Aspire-M5100:~$ sudo service smbd reload
robert@Aspire-M5100:~$ sudo service network-manager start
[/COLOR]



But I find that Network configuration is still the same:
It shows: [COLOR=#0000cd]Wired
Unmanaged-1000 Mb/s
Hardware address: XX:00:1C:25:57:6B[/COLOR]


The above network configuration is still not as the usual which has IP address etc,  even now I can browse website after those commands.


When I restart the PC, it lost internet connection again. The problem is that how to keep it until next boot? Thanks,

---

### Post by grahammechanical on 2014-11-29
Even if the two machines had exactly the same hardware, the network adapters would have had different hardware addresses (MAC address). It is my guess that in putting the hard drive into another machine and then connecting it to the internet you created a network connection in Network Manager for the network adapter in PCB and that connection still exists in the Network Manager configuration file. So, there is a conflict. This is a complete guess. Did I tell you that?

Try deleting the wired connection using Edit connections. Shut down and restart with the ethernet cable connected and see what happens.

[http://en.wikipedia.org/wiki/MAC_address](http://en.wikipedia.org/wiki/MAC_address)

Regards.

---

### Post by ruwan2 on 2014-11-29
Thank you. What you said is correct, but there is nothing that I can delete now. 

BTW, I see that under the right up corner, pull down menu: both "Wired Network" and "device not managed" are grey out. I don't know how to make network manager to initialize the configuration again.

---

