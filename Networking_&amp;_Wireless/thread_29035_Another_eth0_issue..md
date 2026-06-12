---
title: "Another eth0 issue."
date: 2005-04-22
forum: Networking &amp; Wireless
---

### Post by draldo on 2005-04-22
Hey all, 

   I am a relative newbie to linux although I had Suse for awhile and thought I would give Kubuntu a try. I am having a similar problem to the guy in this post

[http://www.ubuntuforums.org/showthread.php?t=28242&highlight=enable+eth0](http://www.ubuntuforums.org/showthread.php?t=28242&highlight=enable+eth0)

Being that I changed ISP and am now running on a fiber optic line. All was well when I first plugged in the cable, network was up and running. Rebooted into windows for a game, came back to ubuntu and could not configure network.

Having googled and browsed the forum here I found I am not the only one with this problem. I am assuming that my ISP with the broadband that I have is a LAN connection, but when I am in windows and checking for networking it shows dhcp. Having used ipconfig in windows, I tried to add that to my interfaces file as a static connection and still no go. No network, no nothing. Went into control center and did pretty much what the other guy did and saw to my amazement that eth0 did not want to enable. Click on enable, it enabled for a second and jumped back to disable.

Here is my interfaces file if anyone knows and would be kind enough to help me out with this little niggle.

Thank.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
 script grep
 map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp

PS I have no clue what to add to broadcast, network, netmask either...


Problem solved...for those that have similar problems, I changed the interfaces setup from dchp to static. Found a site which explained how to work out my broadcast ip and set everything up with gateway, netmask, broadcast and ip addy. Upon boot, network configured in a flash    :smile:

---

### Post by alastair on 2005-04-22
Well ... time to look at the log files then.

On boot - check for your ethernet device being found i.e. references to ethernet/eth, and any ethernet modules getting loaded.

Anything the GUI can do, we can do, and check from the command line. So :

Output of :

a) ifconfig eth0
b) route -n

and, if you are using DHCP - 

Open s hell and :

sudo tail -f /var/log/syslog

To see kernel messages as they occur. Then try :

sudo ifdown eth0
sudo ifup eth0

Assuming you have a DHCP server available.

---

### Post by alastair on 2005-04-22
Oh .. OK. Now I see you have fixed it!

---

### Post by maddox on 2005-04-22
btw, wich site is it? might be usefull :) thx

---

