---
title: "Problem with network / ip-adress just gone"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by quaoar on 2006-12-31
Hi

Been fiddling with and trying to learn using Ubuntu 6.10 server (only console, no desktop). 
Installed a LAMP-server. Set up network and sshd. Everything has been working for a week now. Then last night while I was doing some work in MySQL, I lost connection to my server. (server is at office, I was working from home). I couldn't get any response from the server's ip-adress. 
Today I walked(!!!) to the office. Thinking the server has had a major crash. But no. Everything worked fine on the server, except that I couldn't ping the gateway or any other adress for that sake. Was just told that network was unreachable. 
Doing a ifconfig, returned the expected information, except for one thing. For eth0 there was no line like this:
"inet6 addr: xxx.xxx.xxx.xxx  Bcast: xxx.xxx.xxx.xxx  Mask: xxx.xxx.xxx.xxx"

Running "sudo ifup eth0" said eth0 was already configured. "cat /etc/network/interfaces" show the correct information. Not sure what to do, I just rebooted the server. After reboot the network is back and ifconfig listed up eth0 and lo, and also the previous missing line for eth0:
"inet6 addr: xxx.xxx.xxx.xxx  Bcast: xxx.xxx.xxx.xxx  Mask: xxx.xxx.xxx.xxx"

But why did the network/network information disappear in the first place and the network stop working? :confused: 
Couldn't find anything suspicious in /var/log/messages either. A bit clueless about where to look for further information.
The server is connected directly to the internet, via a gigabit switch where several other servers are connected. None of them had failed.

This is a serious problem for me, because I was hoping to put the server(s) to work soon. Got another mirror server which I'll use the same install on, when everthing is working on the first one. 

Server is a Dell PowerEdge SC1430 with Dual Quad Core Intel Cpus, 8GB memory, and using a hardware raid. Network cable connected to the integrated GBit nic.

---

