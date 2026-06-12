---
title: "cannot connect to internet"
date: 2008-03-15
forum: Networking &amp; Wireless
---

### Post by vipinjo on 2008-03-15
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=651682](http://ubuntuforums.org/showthread.php?t=651682) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi i am vipin joseph and new to ubuntu.
now i can't able to access internet. i can ping to server 192.168.1.1
if i takes a web page using firefox it says server not found. I can't able to ping google.com. My system is connected through peer to peer connection.  in firefox network settings i am using "Direct connection to the internet".

Please help.

settings for interface eth0
Configuration        : Static IP address
IP address            : 192.168.1.2
Subnet mask         : 255.255.255.0
Gateway address : 192.168.1.1

---

### Post by ugm6hr on 2008-03-15
Try surfing here: [http://64.233.183.147/](http://64.233.183.147/)

If that works, then it is an ipv6 issue.

This is your solution:
[http://ubuntuforums.org/showthread.php?p=2631546#post2631546](http://ubuntuforums.org/showthread.php?p=2631546#post2631546)

---

### Post by prshah on 2008-03-15
> **vipinjo said:**
> 

settings for interface eth0
Configuration        : Static IP address
IP address            : 192.168.1.2
Subnet mask         : 255.255.255.0
Gateway address : 192.168.1.1

Considering that you have set a static IP address, maybe your DNS settings are off? post the output of ```
cat /etc/resolv.conf
``` it should contain something like > 
nameserver 192.168.1.1


If it doesn't run the command ```
 sudo gedit /etc/dhcp3/dhclient.conf
``` and find the line that looks like >  #prepend domain-name-servers 127.0.0.1;  and change it to read > prepend domain-name-servers 192.168.1.1; (Note that the "#" at the beginning of the line has been deleted.

Also: ```
sudo echo nameserver 192.168.1.1 > /etc/resolv.conf
``` (Just realized that a static IP setup will not use dhclient.conf)

Then:```
sudo /etc/init.d/networking restart 
``` 

Try that and let us know if it works!

---

