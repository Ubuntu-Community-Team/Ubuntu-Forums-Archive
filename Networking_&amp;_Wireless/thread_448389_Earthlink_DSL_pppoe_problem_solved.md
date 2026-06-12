---
title: "Earthlink DSL pppoe problem solved"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by stereo3D on 2007-05-19
:)  :) 

I had an odd experience with connecting Earthlink DSL pppoe. I was able to connect easily when I first tried the new Ubuntu 7.04. Then I decided to install Ubuntu Studio over the existing Ubuntu. I couldn't get internet connection back. I re-installed at least a dozen times and tried every possible combination of both network set up and the pppoeconf options. 

The solution was to create a /etc/resolv.conf file containing the Earthlink provided DNS nameserver IP addresses. For some reason there wasn't a resolv.conf file. I suppose it is because most PPPoE DSL systems work through DHCP resolution, but not Earthlink DSL. Either the pppoeconf utility was not creating the resolv.conf file or it was being removed by some other script. 

If you are a n00b using Earthlink DSL then during installation you might have noticed the installer could not set up DHCP. 

If you and can't connect try this: 

open a terminal session and type 
 [FONT="Courier New"]  sudo gedit /etc/resolv.conf [/FONT] 

In the file you only need to enter two lines, the two IP addresses supplied by Earthlink for DSN. If you don't know what they are you can check a working connection in Windows on your DSL modem (if you have a working Windows internet connection) or contact Earthlink.  

enter these two lines into the editor: 

nameserver  xxxx.xxxx.xxxx.xxxx 
nameserver  xxxx.xxxx.xxxx.xxxx 

where the x's are the IP addresses for the primary and secondary DNS. 
Save the file and start or restart pppoe.

Good luck and happy Ubuntu 8)

---

