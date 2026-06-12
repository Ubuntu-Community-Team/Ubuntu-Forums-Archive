---
title: "How do I troubleshoot wireless networking?"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by OneSeventeen on 2007-01-16
I have a laptop with wireless that worked great until I upgraded to Edgy.

I have started various threads when I thought the issues were caused by DHCP, and by DNS settings, and things like that.

Because I obviously don't know how to diagnose the problem, I was wondering if someone could help me learn how to narrow down and diagnose the issue.

Steps I have taken:
I can *usually* just run the following script anywhere from once to 25 times and get on the internet for 20 minutes or so before it "breaks" again:```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "allyourbase"
sudo iwconfig eth1 key "mywepkey"
sudo dhclient
```
As of now, I have full signal strength, but when I try to configure wireless using "Network Settings" it does not natively find any wifi access points.  (I am about 5 feet from a wireless G router, and there are usually about 10 wifi networks around me.)

dhclient keeps giving me something like 192.168.136.254, which is not even in my subnet (192.168.1.1)

I am typing this from my windows desktop that has a wifi PCI card connected to the same router working just fine.

I have the same problem on other (unsecured) networks.

I have been trying for about 25 minutes now and still can't get online.

I cannot ping static IP addresses inside or outside of my network.

after using Ubuntu for a few years, selling Linux on CD and using it as my primary desktop OS at work for about 6 months, I'm getting ready to pull out the XP install CD because I don't know how to properly diagnose this issue.

I would appreciate any tips (including which manuals to read and which google search strings to use) that might help me troubleshoot this issue.

[size=1]despite my ability to usually get it to work by the 20th try, I've done it well over 50 times and still can't connect this time, even though I was connected earlier this evening.  Looks like I'll have to use a USB drive to transfer files over so I can upload this week's episode of my podcast... very frustrating, so any help is very much appreciated![/size]

**EDIT:** could any of this have to do with the vmnet8 and vmnet1 virtual networking devices that appear on my machine since I have vmware server installed?
**EDIT2:** ping google results in finding the IP address, then ttl=235 and time=6929 ms... ouch!  still can't connect to my FTP site though.

---

