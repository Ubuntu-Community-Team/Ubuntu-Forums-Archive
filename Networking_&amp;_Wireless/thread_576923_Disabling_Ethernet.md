---
title: "Disabling Ethernet"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by ersuforum on 2007-10-15
My Ubuntu system is currently at a location where there is no network connection other than a modem.  While the modem is not connected, some CAD software we are using is experiening intermittent temporary lockups/slowdown.  At another location, when I was connected to an ethernet network, this problem did not occur.    I tried disabling eth0 using sudo ifconfig eth0 down.  The interface went down long enough to determine that the software did not lock up while the interface was down.  However, the eth0 interface came back up on its own.  

What would be the proper way to shut down eth0 for a modem only application so that it would stay disabled even when the modem connection is not active.  Can I simply comment out the eth0 lines in /etc/network/interfaces:
auto eth0
iface eth0 inet dhcp

to prevent eth0 restarts and then do  sudo ifdown eth0 to dynamically turn eth0 off.

Or, do I need to do someting with the network manager?

I tried to search the forum for a similar problem but was unsuccessful so I hope I'm not  repeating a simple question.  Thanks for your help.

ed

---

### Post by 5-HT on 2007-10-15
> **ersuforum said:**
> 

What would be the proper way to shut down eth0 for a modem only application so that it would stay disabled even when the modem connection is not active.  Can I simply comment out the eth0 lines in /etc/network/interfaces:
auto eth0
iface eth0 inet dhcp 

That would normally do the trick if not for network manager 

> **ersuforum said:**
> 
Or, do I need to do someting with the network manager? 
Network manager doesn't rely on /etc/network/interfaces to do its magic.
From your original post it looks like you have no real use for network manager at the moment and the easiest solution would be to simply either uninstall network manager or prevent it from running (removing nm-applet from your session should get the job done).

cheers,

---

### Post by ersuforum on 2007-10-15
Thank you for the response.  I know there are other things running that look for the network such as the code that alerts the user about software updates.  Does disabling the network manager take care of enough so that the machine will run well or do I need to really think about all of the network related apps and disable them also.

I don't want to uninstall the network manager since this computer will at some point be connected to a network.  Thus, disabling it would be the best solution.  I will remove it from the panel and see what happens.   

If disabling ethernet and the network manager does fix my program temporary freeze problem as suspected, I would be currious to understand which code is intermittently hogging the processor when the netork is not connected.  However, I'm not enough of a linux buff to know how to trace such a thing.  I would think that it shouldn't do this.

---

