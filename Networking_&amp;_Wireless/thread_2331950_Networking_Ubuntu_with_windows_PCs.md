---
title: "Networking Ubuntu with windows PCs"
date: 2016-07-27
forum: Networking &amp; Wireless
---

### Post by dornu on 2016-07-27
Hello guys,

I have a simple requirement to network 3 devices.

One of the device is running Ubuntu 15.04, and has 2 Ethernet interfaces [eth0 and eth1].
The other two PCs are running Windows 8 and each has 1 Ethernet interface.

The network setup is as follows:

[ATTACH=CONFIG]270387[/ATTACH]

The IP address assignment is as follows:

Ubuntu device (B)
eth0: 192.168.0.1
eth1: 192.168.0.2

Windows PC (A)
192.168.0.3 

Windows PC (C)
192.168.0.4

After the above setup, the desired result is to enable A, B, and C to ping each other, however, I'm getting below result:
[LIST]
[*]Only A and B can ping each other
[*]B and C cannot ping each other
[*]A and C cannot ping each other
[/LIST]

Please how can I achieve the desired result? Is there any routing configuration that needs to be set on the Ubuntu system?

---

### Post by mastablasta on 2016-07-27
B needs to be a router (or at least have some router service running). might be easier to add a cheap network switch in between these PC's

[https://en.wikipedia.org/wiki/Network_switch](https://en.wikipedia.org/wiki/Network_switch)

Difference between Router and Network Switch

[http://www.cisco.com/cisco/web/solutions/small_business/resource_center/articles/connect_employees_and_offices/what_is_a_network_switch/index.html?referring_site=smartnavRD](http://www.cisco.com/cisco/web/solutions/small_business/resource_center/articles/connect_employees_and_offices/what_is_a_network_switch/index.html?referring_site=smartnavRD)

---

### Post by SeijiSensei on 2016-07-27
Edit the file /etc/sysctl.conf and remove the hash mark from the line
```
net.ipv4.ip_forward=1
```
then reboot the Ubuntu machine.  By default Ubuntu hosts cannot forward packets from one interface to another for security reasons.

That should fix problems between A and C.  I don't know why B cannot ping C though.  What about in the other direction?  Open a Windows command prompt (Start > type cmd in box, then Enter).  You can use "ping 10.10.10.10" from there.  Does C have Windows Firewall enabled?  I don' t know if that blocks pings or not, but until you get things going, I'd turn off any firewalls except on interfaces with public IP addresses.

You need to edit this file with "sudo" since it is owned by the root user.  Use the command
```
sudo nano /etc/sysctl.conf
```
to edit it with the "nano" editor.

---

### Post by gordintoronto on 2016-07-27
And BTW, 15.04 is at end of life, so it's time to upgrade.

---

### Post by dornu on 2016-07-28
> **SeijiSensei said:**
> Edit the file /etc/sysctl.conf and remove the hash mark from the line
```
net.ipv4.ip_forward=1
```
then reboot the Ubuntu machine.  By default Ubuntu hosts cannot forward packets from one interface to another for security reasons.

That should fix problems between A and C.  I don't know why B cannot ping C though.  What about in the other direction?  Open a Windows command prompt (Start > type cmd in box, then Enter).  You can use "ping 10.10.10.10" from there.  Does C have Windows Firewall enabled?  I don' t know if that blocks pings or not, but until you get things going, I'd turn off any firewalls except on interfaces with public IP addresses.

You need to edit this file with "sudo" since it is owned by the root user.  Use the command
```
sudo nano /etc/sysctl.conf
```
to edit it with the "nano" editor.


I was able to open the **/etc/sysctl.conf **file with **sudo vi**, after uncommenting the **net.ipv4.ip_forward=1** line, I cannot save - the error message says the **file is read-only**.

However, I used below command to set it:

```
sudo sysctl net.ipv4.ip_forward=1
```

It still didn't change the outcome.

---

### Post by dornu on 2016-07-28
> **mastablasta said:**
> B needs to be a router (or at least have some router service running). might be easier to add a cheap network switch in between these PC's

[https://en.wikipedia.org/wiki/Network_switch](https://en.wikipedia.org/wiki/Network_switch)

Difference between Router and Network Switch

[http://www.cisco.com/cisco/web/solutions/small_business/resource_center/articles/connect_employees_and_offices/what_is_a_network_switch/index.html?referring_site=smartnavRD](http://www.cisco.com/cisco/web/solutions/small_business/resource_center/articles/connect_employees_and_offices/what_is_a_network_switch/index.html?referring_site=smartnavRD)


In my given scenario, we do not need additional hardware. So can I configure the Ubuntu system as a network switch/router? If yes, what are the steps?

---

### Post by howefield on 2016-07-28
Moved to the "*Networking & Wireless*" forum.

---

### Post by dornu on 2016-07-30
Thanks everyone for your help. I really appreciate it.

---

