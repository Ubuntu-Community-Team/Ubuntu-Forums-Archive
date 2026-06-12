---
title: "Two connections at one moment"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by mente on 2007-12-24
I have two connections - one is internet, and another one is network. What I need is that all packages going to 10.0.0.0 will go through 10.0.7.254 gateway and all another ones is through 192.168.1.123. The problem is that all these connections go from one cable and through one netcard.
I'm newbie to Linux, but here's how I solve this problem in Windows:
manually setup network for 10.0.7.254;
add routing "route add 10.0.0.0 10.0.7.254 -p";
manually setup network for 192.168.1.123;
add ip in ip fields.

I tried to reproduce the same in Linux, but after switching networks route tables are cleaned up.

---

### Post by mente on 2007-12-25
Can anyone help?

---

### Post by zekica on 2007-12-25
Ubuntu currently doesn't have GUI for setting up multiple connections on one device, you will have to do that manually.

Setup your internet connection from GUI and then:

I don't know any better way to do this so here is:
in Terminal (Applications -> Accessories -> Terminal) type:
**sudo chmod a+x /etc/rc.local**
it will ask you for your password.
**gksudo gedit /etc/rc.local**

and insert above line that says:
exit 0

**/sbin/ifconfig eth0:local** <your_10.x_ip> **netmask** <your_netmask>
/sbin/route add -net 10.0.0.0 netmask 255.0.0.0 gw 10.0.7.254[/b]

Close gedit window and type following in terminal:
**sudo /etc/rc.local**

You should be connected to both networks.

---

### Post by mente on 2007-12-25
I knew, that there's no GUI, I thought I could do it via /etc/network/interfaces.

I'll try it soon. Thanks

---

### Post by mente on 2007-12-25
Really many thanks. The problem was resolved

---

