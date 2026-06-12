---
title: "network disabled in lshw"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by mrwawa on 2008-05-22
Hi all,

I am running 6.10 and my wireless was working until I got DSL a few months ago.  Alas, since then I haven't been able to access the internet.  I am trying to run through some troubleshooting guides, but am stuck at stage one.  lshw says that "*-network DISABLED"  but can see that I have a card.  Eth0 is Ehternet interface and eth1 is the wireless.  Any help on how to "enable" the network would be appreciated  I have been reading Kevdogs post on how to manually configure without the network manager (because I can't find it now, was there before).  [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Hope this makes sense,

Wade

---

### Post by chili555 on 2008-05-22
May we please go ahead and see your:```
sudo lshw -C network
sudo cat /var/log/messages | grep eth1
```The last command will produce quite a bit of output, so just let us have the last 6-8 lines. Thanks.

---

### Post by mrwawa on 2008-05-23
Thanks for the reply.  I actually upgraded to 8.04 and everything works great.  I know this isn't the way that I should handle things like this, but I wanted to upgrade anyway.

Wade

---

### Post by mapes12 on 2008-05-23
Would you like to mark the thread as SOLVED then please?

---

### Post by scott_w on 2008-07-02
Hi,

I'm on 8.04 and am experiencing this disabled network 
problem. I'm trying to get the ubuntu machine online, so I'm posting from a different computer, forgive the approximations.

if I do ```
lshw -c network
``` I get the wireless card which I'm trying to use, ndiswrapper driver installed and found. It used to display ```
*-network:0 DISABLED
```, which I thought was the problem, but the DISABLED has now disappeared and still no connection.

The last line of ```
sudo cat /var/log/messages | grep eth1
``` produce this: ```
ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Any help is appreciated.

---

