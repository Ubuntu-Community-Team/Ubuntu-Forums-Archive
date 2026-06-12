---
title: "Problem with Default Gateway setting reverting on restart"
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by jordanne on 2016-11-06
Hi

I recently have set up a computer and I am having an issue with Ubuntu Mate reverting the default gateway setting after I have changed it in terminal.

Essentially I have it connected to two networks..

192.168.1.1 - is to a non-internet connected router which acts as a DHCP server for several IPCCTV cameras and also for the computer. It is connected to the on-board Ethernet on the computer.
192.168.0.1 - is to the router which is the (internet connected) home network (also DHCP). Its connected by a USB Ethernet adaptor to the computer.

Ubuntu Mate is choosing the first network as the default gateway when I need it to be the second network for internet access.
I use the command 'sudo route del default gw 192.168.1.1' and then 'sudo route add default gw 192.168.0.1' and it works and is fine until I need to restart.

How can I fix this?

-Jordanne

---

### Post by Hadaka on 2016-11-06
Hi, give this a try..
from terminal..
Open your editor with.. or use your favorite editor 
```
gksudo gedit /etc/rc.local
```
insert your 2 lines of code..
*Note the "&&" insures the first command completed before issuing the next command.
```
sudo route del default gw 192.168.1.1 && sudo route add default 192.168.0.1
exit 0
```
don't forget the "exit 0"
save and close gedit.
then.click your wifi icon..and then choose edit connections.
uncheck the "Connect Automatically" Ipv4 setting for 192.168.1.1 and verify it says...Automatic DHCP 
save and close the 192.168.1.1 connection edit.
again..click your wifi icon..and then choose edit connections.
verify "Connect Automatically" Ipv4 setting for 192.168.0.1  IS checked. and then change from "Automatic DHCP"
To ->   "Automatic DHCP address only" and then enter 192.168.0.1 on the DNS field.
save and close the connection edit.
Boot and test.

*After thought..if you do not use Ipv6 set both connections to IGNORE while you are in there.

---

### Post by jordanne on 2016-11-06
Entered what you said into [COLOR=#000000][FONT=&quot]/etc/rc.local on nano.. saved, checked all the connection settings. Rebooted and it's online![/FONT][/COLOR]

I've been searching the web all afternoon for a solution.

Thank you very much for your help :D:D

---

### Post by Hadaka on 2016-11-06
Great !...glad that worked for you.
Thank You for marking your thread Solved.

---

