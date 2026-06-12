---
title: "eth0 has completely disappeared"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by StealthCP on 2007-08-07
[[COLOR="Red"]This[/COLOR]](http://ubuntuforums.org/showthread.php?t=283656) thread shows almost the exact same problem.  I have checked for help elsewhere on the forums, the net, and also got two very knowledgeable Linux tech-heads to have a bash about, no joy.

Simply, */etc/network/interfaces* is correct, *lspci* lists the device, *dmesg | grep eth0* shows the lan adapter, but *ifconfig* has it missing.  Below is a gif showing all of this, as it is a server, with no net connection, I must access it via live video stream input, so copy/paste is also impossible, only screenshots.

[[IMG]http://img376.imageshack.us/img376/6830/serverey0.th.gif[/IMG]](http://img376.imageshack.us/img376/6830/serverey0.gif)

The server uses two IPs (as can be seen in the image) and runs Ubuntu 6.06.1 LTS.  iptables as firewall, if there is any more information you need to help me resolve the problem just yell.  Remote access can be offered to those that convince me that they know what they are doing, and exactly what the problem is.  I'd also like to point out that I'm a fairly confident amateur with Linux serversm though only have experience with Debian based servers to date.  I've been brief as I'm just back from the pub, and tired :)  Sorry if I haven't given enough information.

I'll be back at around 1100 UTC.

---

### Post by noob12 on 2007-08-07
I've never seen an animated gif that long.

Do
```

ifconfig -a

lshw -C network

```
say anything interesting?

What is in **cat /etc/iftab** ?

---

### Post by noob12 on 2007-08-07
Note: ifconfig only shows interfaces that are UP.  You need the -a to see the down ones.

---

### Post by StealthCP on 2007-08-08
Interesting yes, because an interface eth1 appears on this list.  I do remember before now, that the device was always called eth1, but the /etc/networking/interfaces shows that it is configured for eth0.  This strikes me as odd, because network has always worked before with this configuration.  I have e-mailed my host's support with this problem, to see if it may be a loose cable connection.  Apart from that, nothing has been changed since the last time it worked.

> # cat /etc/iftab
eth0 mac 00:16:76:9c:79:88 arp 1

---

### Post by noob12 on 2007-08-08
Try manually invoking
[B]
sudo /sbin/ifup eth0
[/B]
(or eth1 whichever is actually showing up).  Hard to drive blind.

---

