---
title: "Start Networking after a reboot, before login?"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by dcajacob on 2008-09-04
Hi All,

I have a desktop in my basement, running Ubuntu, that I'd essentially like to run headless.  It has a wireless network card to connect to the network.  I can SSH and VNC both inside and outside the network, but if the desktop reboots or I have to shut it down, when it comes back up, it is no longer on the network!  Apparently, it doesn't connect until someone logs in, which requires me to go down there, etc., defeating the purpose of SSH.  I have looked around a lot and not found a solution to this, but if someone could point me in the right direction, I'd appreciate it!  I'd like for the computer to automatically connect to the network on reboot or startup and allow SSH connections.  That way, I can SSH, start a snew session and move on.  Thanks!

---

### Post by michelek on 2008-09-20
I have told to read 
man interfaces
which I did but it didn't helped me.

---

### Post by excbuntu on 2009-03-01
i'm also looking for this solution. the wireless connection does not connect unless someone is logged in.

---

### Post by x1101 on 2009-03-01
what you both need to do is put your wireless info into /etc/network/interfaces so that the section you add looks something like this. The fastest way to find out what your wireless interface is called is to login, then do an ifconfig or iwconfig. It will likely be either wlan0 or ath0 (I have one of each) add that to the (YOUR WIRELESS CARD HERE) parts, and the other information mentioned as well. Reboot, and try it out.

#adding this for auto wireless
allow-hotplug (YOUR WIRELESS CARD HERE)
auto (YOUR WIRELESS CARD HERE)
iface ath0 inet dhcp
        wireless-essid (YOUR SSID HERE)
        wireless-key (YOUR KEY HERE)

---

### Post by qbox on 2009-03-01
You can add commands in /etc/rc.local to execute on boot before login. So you can make connection and start servers before you are actually logged in.
read this
[https://www.mirbsd.org/htman/i386/man8/rc.htm](https://www.mirbsd.org/htman/i386/man8/rc.htm)
In rc.local you can put all commands you want to execute.

---

