---
title: "no more internet"
date: 2005-06-16
forum: Networking &amp; Wireless
---

### Post by pumpkinpatch on 2005-06-16
My computer was doing wonderfully on the network until recently when it stopped working.  Everytime I try to activate the card it automatically deactivates.  I checked both the card and the cable but they work fine.  Whats wrong with Ubuntu?

---

### Post by hw-tph on 2005-06-17
[QUOTE=pumpkinpatch]My computer was doing wonderfully on the network until recently when it stopped working.  Everytime I try to activate the card it automatically deactivates.  I checked both the card and the cable but they work fine.  Whats wrong with Ubuntu?[/QUOTE]
 You might want to check the system log in /var/log/syslog and output from the **dmesg** command. Logfiles often provide essential information for troubleshooting.

Håkan

---

### Post by mila80 on 2005-06-20
[QUOTE=pumpkinpatch]My computer was doing wonderfully on the network until recently when it stopped working.  Everytime I try to activate the card it automatically deactivates.  I checked both the card and the cable but they work fine.  Whats wrong with Ubuntu?[/QUOTE]

Try with it...
edit your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth0

# The primary network interface
#iface eth0 inet dhcp

Marco

---

### Post by ubuntu_demon on 2005-06-25
[QUOTE=mila80]Try with it...
edit your /etc/network/interfaces by commenting out the lines:


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth0

# The primary network interface
#iface eth0 inet dhcp

Marco[/QUOTE]
 don't do this. It will only take your network/internet down as soon as /etc/network/interfaces  is loaded again (for example after a reboot). 

mila80 please don't give this advice anymore

---

