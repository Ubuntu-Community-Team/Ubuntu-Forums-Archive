---
title: "Connecting, Showing Good Connection Strength, but Internet Not Working"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by niiiick on 2007-02-06
Working with a Dell Latitude D620.

After fresh Edgy install, the wireless card was detected and appeared to be installed, but did not work.  I installed ndiswrapper, cut out the broadcom drivers from the windows version and installed it.

Now the wireless card works: it connects if i manually type in the ESSID and hex password.  It doesn't automatically detect the wireless networks available in System -> Admin -> Networking, but when i run iwconfig eth1 scanning from terminal, it shows the available networks.

So now I'm at the point where the Green connection percentage bar shows up in the icon tray thingy, but the internet won't actually work.  The firefox status bar stays on "Looking up google.com", but I can't even connect to the router's setup page through the router's ip address (ruling out DNS problems -- or at least THIS problem isn't a DNS one; it may be both).  I've tried disabling eth0 to no avail.  I've tried network manager, nothing.

Also, when I was at home the wireless worked fine with network manager.  Now i've gotten to school and I get the problem.  Note that windows connects and works properly.

So...
1) How can I get the available networks to show up under ESSID in the wireless network configuration
and 2) HOW CAN I GET THE INTERNET TO WORK?

---

### Post by niiiick on 2007-02-07
bump?

---

### Post by gradedcheese on 2007-02-07
I'm assuming you get a DHCP address?  You can do this at the shell and see if you get an IP address assigned:

sudo ifconfig eth1 down
sudo ifconfig eth1 up
sudo iwconfig eth1 essid type_your_essid_here
sudo dhclient eth1

The first two are just in case, then associate and ask for an IP address.  If you get one, then try using Firefox.  If you don't, then we need to find out why.

---

