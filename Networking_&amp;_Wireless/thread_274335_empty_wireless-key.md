---
title: "empty wireless-key?"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by EReckase on 2006-10-09
I have an HP Pavilion dv8000 with the Broadcom 4318 chipset, using ndiswrapper to connect to wireless networks.  When at home, I have a secured access point, so I use a 'wireless-key' entry in my /etc/network/interfaces file.  I regularly meet my co-workers at free wireless locations, like Panera Bread stores, which do NOT have a wireless key.  If I bring my connection down with 'sudo ifdown eth1', edit my /etc/network/interfaces file to have the correct wireless-essid and NO wireless-key line, and then 'sudo ifup eth1', my machine will not connect unless I reboot.  If I go from a non-password-protected access point to a protected one, I don't have this problem.  Of course, rebooting is something no card-carrying-Linux-user should have to do in order to get anything to work, so I'm curious why this happens.  I figure the old essid is cached somehow since I can't figure out how to specify a 'blank' essid when connecting to open access points - if I have a blank essid line in my interfaces file, then I get an syntax error.

Ideas?

---

### Post by wieman01 on 2006-10-09
I don't really have this problem, only if I have Firestarter (my firewall) enabled. Once I disable it/shut it down for a minute reconnecting works just fine. You don't have Firestarter by chance?

---

### Post by EReckase on 2006-10-09
Nope.  No firewall on this machine.

---

### Post by wieman01 on 2006-10-09
I see... I think I actually DO have the same problem, although I am using WPA(2) rather than WEP as you do. Before I reconnect (encrypted->unencrypted) I need to kill a process:
> sudo killall wpa_supplicant
I suspect WEP will also iniate a process that's running in the background and keep you from restarting the network successfully.

Have you tried using the GUI/Gnome applet rather than command line? That should take care of the issue I have mentioned...

---

### Post by EReckase on 2006-10-10
I've tried using the applet, but I switch between networks so much that my /etc/network/interfaces file rapidly filled with a lot of junk that made it hard to understand what was going on.  I also seem to remember having this problem with the applet as well, which is why I went to editing the interfaces file directly in the first place.

I looked for a process with 'wep' or 'eth1' or something like that in the process name/call, but came up with nothing.  Anyone know what process I need to kill to accomplish this?

---

