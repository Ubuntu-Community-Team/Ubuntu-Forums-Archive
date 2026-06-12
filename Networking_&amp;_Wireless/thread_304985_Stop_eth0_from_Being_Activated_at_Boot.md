---
title: "Stop eth0 from Being Activated at Boot"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by Ingla on 2006-11-22
Hello.

Due to a switch in the order of network cards, for reasons to complicated to go into, Ubuntu bootup is hindered by not being connected (via router).

The working connection is eth1. However, the system activates both gateway devices (eth0 and eth1) at boot, making eth0 the default. Changing the default to eth1 once I'm in, gets me connected (I also deactivate eth0). However this configuration disappears on reboot and we're back to scratch.

I need to solve this, if possible, by either:

1. making the system save my configuration (keep eth1 as the default at bootup), or

2. stopping the  automatic activation of eth0 at boot (which hopefully would make eth1 the default "by default"??)

3. using any other solution anyone may know of.

Does anyone know how to do (AND UNDO) 1 or 2?

Any help will be greatly appreciated.

---

### Post by OffHand on 2006-11-22
Can you disable it in the bios?

---

### Post by mssever on 2006-11-22
Edit /etc/network/interfaces and comment out the auto eth0 line. Add the correct line for your netcard.

---

### Post by Ingla on 2006-11-23
Here is the content of /etc/Network/Interfaces:

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
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

iface eth0 inet static
address 10.0.0.139
netmask 255.0.0.0
gateway 10.0.0.138



iface eth1 inet static
address 10.0.0.139
netmask 255.0.0.0
gateway 10.0.0.138


auto eth1

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

I can't claim to understand these things well, but I can't see what is causing eth0 to activate on boot. 

Can anyone see what might stop it?

---

### Post by FrodoB on 2006-11-23
You need to edit the /etc/iftab file and tie the card that is now eth1's MAC identifier to the name eth0:

$ sudo gedit /etc/iftab

Inside this file you will see that your older card's MAC is tied to eth0. You can just tie the new card's MAC identifier to eth0 and remove any references to other cards, or tie the older card to eth1. This will swap them. 

If you do not want both card to come up you can then modify the interfaces file and remove the:

auto eth1

or whichever one you do not want to be automatic.

---

### Post by Ingla on 2006-11-23
Thanks.

The file reads:

-----------------------------------------------------------------------------
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:0e:2e:6a:10:35
eth1 mac 00:11:09:02:e5:38
-----------------------------------------------------------------------------
Do you mean I should make it:

eth1 mac 00:0e:2e:6a:10:35
eth0 mac 00:11:09:02:e5:38       or does it need to be:

eth0 mac 00:11:09:02:e5:38
eth1 mac 00:0e:2e:6a:10:35

That is, is there a required order to this?

---

### Post by FrodoB on 2006-11-23
I don't know the detail to that level. I would try:

eth0 mac 00:11:09:02:e5:38
eth1 mac 00:0e:2e:6a:10:35

and reboot and see if it works.

---

### Post by mssever on 2006-11-23
Instead of rebooting, you can restart networking: ```
sudo /etc/init.d/networking restart
```

---

### Post by FrodoB on 2006-11-23
Agreed, but I did not know off hand it that would get the interfaces reassigned to different names. Rebooting will for sure.

Good point though for many situations.

---

