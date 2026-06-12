---
title: "ESSID not showing up when creating ad-hoc network"
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by david-c-moffatt on 2014-06-25
I need some help fixing an ad-hoc network.

If I create an ad-hoc network with my PC or Mac then connect to it with Ubuntu boxes everything works as documented.   I can even run the DHCP server on one of my Ubuntu boxes and the others will get their IPs from it.
However If I don't have an existing ad-hoc network and I first bring up my Linux boxes I can't find the ESSID from the mac or PC or other linux boxes.  I have tried several different methods of configuration:

1) Using the network manager applet.
2) Using a script (iwconfig, ifconfig) which is attached as setup.txt 
3) Using /etc/network/interfaces which is attached as interfaces.txt

Always the same result.  Everything seems to work but I can not connect.    

Here are my questions:

1) What log files should I be looking in?   Where can I see error messages?
2) Are there any kernel configuration that I should turn on?   I am using stock 64bit 14.04 and I do install updates.
3) Has anyone done an only ubuntu ad-hoc network with 14.04?   What kind of NIC did you use? 
4) Does anyone have any advice on how to track this through the kernel?   I tried grep-ing for ESSID or essid in the driver code but did not find much other than a field in a structure. 

Thank for any help you can give.
David Moffatt.

PS a bunch of ubuntu web pages asked you to run a little set of diagnostic commands and post the results when asking wifi questions.   Also attached is the result of that.   It is called output.txt.gz

---

