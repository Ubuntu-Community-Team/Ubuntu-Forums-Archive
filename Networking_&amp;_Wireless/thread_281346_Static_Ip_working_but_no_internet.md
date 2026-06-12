---
title: "Static Ip working but no internet"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by yakkob on 2006-10-20
I am running dapper, just installed a few days ago.  I got my broadcom wireless card up and running great.

I have a wireless card hooked up to a wireless router that runs our home network.  And that is hooked up to a cable modem.

The problem is now I am trying to set up a static IP address and I am having no luck with it at all...  
I've been trying everything messing around with the

 /etc/network/interfaces

sudo ifdown wlan0 
sudo ifup wlan0 
each time i make a change. sometimes it connects to the router sometimes it doesn't... but never will it let me connect to the internet.

I am not sure if I am getting the right settings everytime I do it.  I have no trouble with the internet in dhcp mode but I need to run static.

 I believe I have the right name servers listed in the hosts.conf file. (I might have the file name wrong)
I have spent the whole day trying to figure this out.

Is this a common error? I have tried so many things listed on the internet... But I am frustrated and I thought I would make this post to see if I can find help.

Please help.

Also why is it that trying to set up the static ip in the GUI not work?

---

### Post by hanzomon4 on 2006-10-20
I don't have wireless but I had a similar problem...
> **hanzomon4 said:**
> I fixed it.. here's how

First the only setting I had to reset after a reboot was the DNS. The config file where the DNS settings are stored is in /etc/resolv.conf. 
For some reasons getting my settings to stick using the Network configuration tool would not work, so I tried editing /etc/resolv.conf by hand.
That did not work because Ubuntu uses a dynamic DNS configuration. This will overwrite the etc/resolv.conf file at boot-up.
The solution is to add your settings to /etc/resolvconf/resolv.conf.d/base like this.
```
 sudo gedit /etc/resolvconf/resolv.conf.d/base
```
```
nameserver   192.X.X.X
```
Replace the "192.X.X.X" with your DNS number.

Okay my work here is done.

---

