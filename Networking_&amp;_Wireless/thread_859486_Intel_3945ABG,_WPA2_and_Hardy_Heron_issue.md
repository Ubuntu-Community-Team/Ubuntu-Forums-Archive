---
title: "Intel 3945ABG, WPA2 and Hardy Heron issue"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by Sk1nnyMan on 2008-07-14
Hey

This issue is as old as hardy, but I am getting lost in all the launchpad, forum and blog posts about the issue, so I do not really know how to fix it.

The Wireless network I am trying to connect to has ESSID broadcasting enabled, MAC address filtering enabled (with the laptop in question being allowed), is WPA2 secured and has a DHCP server; the wireless controller is a "Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)" according to lspci.

I am having trouble connecting to the wireless network, what happens is I select to connect to my network in network-manager, the animation in the task bar spins around until network manager asks me for the WPA key despite me having it in keyring already, if I enter my WPA2 key and click enter I get an error icon on the network manager icon in the task bar. However my syslog will keep showing messages from the kernel saying it is still trying to connect to the network, it seems to go through a cycle of activating the device, authenticating, associating and then disassociating for "reason=3" about a second later for no apparent reason, during this time I do not have a connection.
Eventually (10 minutes this time, can take longer) something clicks and it associates and authenticates without disconnecting itself, however I don't have an IP address and have to call dhclient manually to get one.
After I call dhclient I can access the network, anything with any GNOME integration does not seem to believe I am actually connected, for instance Firefox 3 defaults to Offline mode and I have to manually call update manager to get updates (or apt-get).

I have tried using wicd over Network-Manager but got similar results.

Attached should be an extract from my syslog (had to zip it to get under the file limit) with everything non-network related and my ESSID edited out, it is taken from when network manager first starts up until me manually calling dhclient and getting an IP.

This issue has been really irritating for me, not knowing if it will take 10 minutes, 15 minutes or 5 minutes to get online once I switch my laptop on annoys me so any help will be much appreciated.

Thanks 

Sk1nnyman

---

### Post by Sk1nnyMan on 2008-07-15
Edited my description of the problem so it was more accurate.

---

### Post by wyth on 2008-07-30
No idea if this will help, but I found your thread looking for an answer to a similar problem.  

But I did find one workaround.  Seems the wireless isn't *actually* starting when you (or I, at least) boot up.  

I have a switch at the front of my laptop to turn the wireless on and off.  I noticed that the light wasn't turning on when I booted up, even though it was switched on.  Then I would have the same issues you're experiencing -- it'd see a network, try to connect, fail, fail again, etc.

So on boot, I tried switching that switch off and then back on.  Instant connection once again.  

I'm not sure what the issue is here, but the latest kernel updates seem to be skulking behind this and some other issues.  

[B]EDIT
[/B] Just found this thread, and the /etc/modprobe.d trick at the end did it for me.

Create file in /etc/modprobe.d called iwl3945.  In it, have the following:
[FONT=monospace]
[/FONT]```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
```**Second Edit**
The above fix worked once, but not the second time. The first time I was plugged in, the second on battery.  I don't know if that made a difference.

However going back to the 2.6.24-19 kernel did the trick.

---

