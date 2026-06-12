---
title: "DHCP not getting new IP when switching networks"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by parameter on 2007-01-30
Hi everyone. I'm new to Ubuntu, trying to make the switch of my desktop from Windows to Linux.  I'm having a issue with DHCP that I'm not sure how to fix.

I have two network cables at my desk.  One is on one network and the other is on another network.  When I disconnect the ethernet cable for one network and plug in the other, the DHCP client is not getting and updating my IP address with that of the new network.

When I've done this in the past with Windows, I would be alerted as soon as the network cable is unplugged.  When I plugged in the new network cable the OS would send a DHCP request and get the IP address for the new network.

When I do this in Ubuntu, I still have the IP address of the old network.  I opened a shell and did "watch ifconfig" and let it run for about eight or nine minutes. The IP address never updated.  It seems that the only way to get it to try to get a new address is to open a shell and run "sudo ifdown eth0 && sudo ifup eth0" every time I switch networks.  Not very convenient.

Is there a way to fix this to send a DHCP request when a cable is connected?

---

### Post by dbott67 on 2007-01-30
EDIT: Oops, I re-read your post.  I see now that you want the command to be issued upon the cable re-connecting (I missed that last part the first time).  At any rate, the command below is another method.


[COLOR="Silver"]
This should do the trick:

```
sudo dhclient
```

-Dave[/COLOR]

---

### Post by parameter on 2007-01-30
Thanks, but that just does the same thing in fewer characters.  I know that programs can detect when the network is disconnected.  The "network monitor" program in the toolbar at the top tells me when I have removed the network cable.  If I can just get it, or something else, to run dhclient when I reconnect the network cable I'll be all set.

I've made a workaround for the time being where I run dhclient from root's crontab every 30 seconds, but that's very inelegant.

---

### Post by komputes on 2008-02-27
Is there a DHCP-related bug in launchpad for nm-applet. I also find that on some specific networks, I need to run dhclient to get an IP address. Once I do that, nmapplet (sometimes) reports the IP address as 0.0.0.0

@parameter: I've had this problem for a while, please message me if you find a soluyion to run dhclient when a cable is connected.

---

