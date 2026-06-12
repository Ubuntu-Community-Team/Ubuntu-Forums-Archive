---
title: "Cant ping to the PC on LAN...help"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by visio159 on 2007-05-24
I have 2 PC:

1st PC
            runnung ubuntu 7.04
            having 2 ethernet cards 
            one card(ip addr:192.168.1.159, subnet: 255.255.255.0, gateway: 192.168.1.1, DNS: 61.1.96.69) connected to router(192.168.1.1)
            other card(ip addr:192.168.1.22, subnet:255.255.255.0, other fields are left blank) is connected to a computer running winxp professional(firewall turned off) and that computer is having ip addr: 192.168.1.23, subnet:255.255.255.0.


I have set up Samba and guidedog but i am not able to ping the other computer (ip addr: 192.168.1.23)


Please help me, i hav been trying to find the solution for past 6 hours.

---

### Post by visio159 on 2007-05-24
???anybody

---

### Post by lloyd_b on 2007-05-24
First off, you don't say where you are pinging from.  I'm assuming that you're pinging from the Ubuntu box.

What's probably going on is that your routing is trying to send the packet via the first network card.  This is an issue that occurs when you have two NICs (Network Interface Cards, aka Ethernet cards) on the same network (in your case, 192.168.1.x).
 
The "quick and dirty fix" (Assumes that your *second* NIC is on interface "eth1").  In a terminal window:
```
sudo route add -host 192.168.1.23 eth1
```
This will tell your computer that for that particular host, send the packets via "eth1" rather than the default (which is probably "eth0").

The "real" fix - move the XP machine to a different address (such as 192.168.2.23), and then configure the 2nd NIC with an address on that network (such as 192.168.2.22).  Then the standard routes that are created by the system will take care of correctly routing to that machine (Note: this assumes that the 192.168.2.x isn't used for something else, but if so, then grab another "unroutable" network range, such as "192.168.200.x" or "10.1.0.x").

Lloyd B.

---

### Post by visio159 on 2007-05-24
**@lloyd_b**

Man u saved me,  hey even sharing is working now:p
Thanx for the rescue. I own you:popcorn:

Just what is left is internet sharing, i hope u can guide me on this also.
I am using **guidedog**

and changed the address of eth1 to 192.168.2.22 and on other computer 192.168.2.23 as u said.

[[IMG]http://img02.picoodle.com/img/img02/8/5/24/t_ScreenshotAm_e681dd2.png[/IMG]](http://www.picoodle.com/view.php?srv=img02&img=/8/5/24/f_ScreenshotAm_e681dd2.png)
[[IMG]http://img03.picoodle.com/img/img03/8/5/24/t_ScreenshotAm_f2def34.png[/IMG]](http://www.picoodle.com/view.php?srv=img03&img=/8/5/24/f_ScreenshotAm_f2def34.png)

So now is this config correct and only i have to do is to set the proxy settings in internet explorer in other PC to 192.168.2.22 at port 5000 ?

---

