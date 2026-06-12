---
title: "problem with internet connection"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by seltix on 2007-09-24
hello!

I have ubuntu 7,04 and I am with a problem with the Internet&#8230;
ubuntu is a server, and is connected to one switch, and has one another PC with windows xp pro connected to this switch.
When the Internet falls and comes back, obviously the IP is modified, and because of this I do not have Internet in ubuntu.
At the beginning I thought that ubuntu did not recognize the IP change, however it recognizes the new IP because the PC with windows continues with Internet!
the only thing that obtained to make ties now to decide the problem is to restart ubuntu, and thus I come back to also have Internet in ubuntu.

what can I do?

already I tried to restart networking with the command &#8220;/etc/init.d/networking restart&#8221; but he continues equal.

---

### Post by gautada on 2007-09-24
Are you using DHCP?  Obviously network settings are changing with each internet connection changing state.  Typically your internal network should not change with an internet connection state change.  To get this you probably need a router not a switch.

---

### Post by seltix on 2007-09-24
yes eth1 are thcp....

the problem is not switch is ubuntu… the modem is connected to ubuntu for the door eth1, and ubuntu is connected to switch for the door eth0, the PC with windows xp is connected to this switch. the problem cannot come of switch because the Internet enters directamente in ubuntu.

---

### Post by gautada on 2007-09-25
OK so you need to setup Ubuntu as a router?  I am not sure why you think a new IP address on eth0 (connection to Internet) is an issue. But you should look at this [thread]("http://ubuntuforums.org/showthread.php?t=25813").

---

### Post by seltix on 2007-09-25
no. the problem is that when ah one cut in the Internet, exactly after coming back I continues without Internet in ubuntu! I know that the Internet came back because I have Internet in windows… the linking of the two computers is this:

[IMG]http://img480.imageshack.us/img480/3013/untitled1it1.jpg[/IMG]

---

