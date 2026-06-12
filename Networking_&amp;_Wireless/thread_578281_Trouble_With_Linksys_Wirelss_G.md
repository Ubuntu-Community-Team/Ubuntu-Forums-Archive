---
title: "Trouble With Linksys Wirelss G"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by saturninus on 2007-10-17
I've been trying Ubuntu out on a Live-DVD.  So far everything seems okay except for the Internet connection.

I use the Linksys Wireless G wireless network device.  It's a USB wireless network card.

Ubuntu can detect the different networks around my neighborhood.  As a matter of fact, it detects more than Windows Vista does.  However, when it comes time to connect to my home network it doesn't happen. Nor with any other network.  It just sits there looking like it's trying to connect forever yet nothing happens.

What can I do to fix this issue?

---

### Post by chewearn on 2007-10-17
What I found out is, the current network-manager in Feisty need to see a DHCP server in the network, else it refuse to connect to it.

Some people suggest to use wicd, though I have no experience there.

---

### Post by saturninus on 2007-10-17
How would I go about making the change?

---

### Post by webbie180 on 2007-10-22
Have the same problem too after upgrading to Gusty.  It was working well under Fiesty, now also dont know wat to do, just waiting for help.

---

### Post by njh on 2007-10-22
I had trouble with upgrade to gutsy where browsers (firefox, galeon, lynx, curl) were not doing anything seemingly at random.  It turned out that my wireless router was giving two addresses for DNS lookups (/etc/resolv.conf).  The first was the router, which was (and I still haven't worked this one out) returning 1.0.0.0 to everything.  Commenting it out in /etc/resolv.conf resolved the problem.

The error looked like this:
```
root@niffler:~# curl -vvv [http://ubuntu.com](http://ubuntu.com)
* About to connect() to ubuntu.com port 80 (#0)
*   Trying 1.0.0.0... 
```
^C

So try commenting out one of the nameserver lines in /etc/resolv.conf and test with something like ```
curl -vv ubuntu.com
``` and see if you make progress.

---

### Post by webbie180 on 2007-10-22
Tried using manual configuration in network manager with the same inputs I used in Fiesty but still cannont work.
Tried network monitor in panel too, but my network device is not there.
Under Gusty 7.10, is there other way to connect to network?

---

### Post by kevdog on 2007-10-22
Try connecting manually from the command line, the instructions are linked to in my signatures.

---

### Post by webbie180 on 2007-10-23
What I observed from connection information under network manager is empty
IP address, boradcast, subnet.....secondary DNS.  How to overcome this?  Can I manually input my wired connections into this to make my wireless workeed?

---

### Post by AlexMono94 on 2007-10-23
Your problem is that Feisty uses a different driver than Gusty. Feisty uses RT2570 for your card where as Gusty uses RT2500usb. Follow my tutorial here: [http://ubuntuforums.org/showthread.php?t=588045](http://ubuntuforums.org/showthread.php?t=588045) and see if it works for you.

---

### Post by njh on 2007-11-04
> **njh said:**
> I had trouble with upgrade to gutsy where browsers (firefox, galeon, lynx, curl) were not doing anything seemingly at random.  It turned out that my wireless router was giving two addresses for DNS lookups (/etc/resolv.conf).  The first was the router, which was (and I still haven't worked this one out) returning 1.0.0.0 to everything.  Commenting it out in /etc/resolv.conf resolved the problem.

The error looked like this:
```
root@niffler:~# curl -vvv [http://ubuntu.com](http://ubuntu.com)
* About to connect() to ubuntu.com port 80 (#0)
*   Trying 1.0.0.0... 
```
^C

So try commenting out one of the nameserver lines in /etc/resolv.conf and test with something like ```
curl -vv ubuntu.com
``` and see if you make progress.

The driver change seems a more likely explanation, but in the case that someone else goes down my path, here is a better analysis:
[https://bugs.launchpad.net/ubuntu/+bug/81057](https://bugs.launchpad.net/ubuntu/+bug/81057)

---

