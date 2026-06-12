---
title: "changing the driver/module for eth1"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by andka on 2005-08-24
Hi,

Summary:
I'm trying to figure out how to *permanently* change the driver/module for eth1 (to de4x5).  Using rmmod and modprobe I can change it temporarily, but at the next reboot it changes back again. I have tried to add "alias eth1 de4x5" in the /etc/modules.conf but it does not help.

long version:
I want to use the module 'de4x5' which seems to work better on my NIC than the module 'tulip' which is loaded by default. If I do a 'rmmod tulip'  and a 'modprobe de4x5' everything works much better. But this change does not stick when I do a reboot.

In the Ethernet HOWTO there is a section called "2.1 How do I tell Linux what driver to use?". The provided answer does not work, unfortunatelly. In short, it says that I should add the line "alias eth1 de4x5" to /etc/modules.conf  (actually, I think I should add it to /etc/modutils/aliases and then run 'update-modules'. I tried that and it gives the same result).

I also tried to add de4x5 to the /etc/modules file to make it load early and perhaps avoid loading the tulip driver. Did not work. Both drivers were loaded!

My current assumption is  that the association between eth1 and the module is done in some other way in Warty (Debian?) than an alias in the modules.conf file. But I am unable to find this. I have greped for "tulip" in /etc and elsewhere without any luck.

Does anyone have an idea of what I should do?

A different question. How can I see if eth1 works in 10 or 100 mbps mode?

---

### Post by nad on 2005-08-24
You have the right idea with addition of your prefered driver to the /etc/modules file. In addition, add the tulip driver to the file /etc/hotplug/blacklist to keep it from loading.

Diagnostics for most open source network drivers are here: [http://www.scyld.com/ethercard_diag.html](http://www.scyld.com/ethercard_diag.html)

---

### Post by andka on 2005-08-25
Great! Thanks! This should do it.

Does anyone know how to figure out wether a ethernet network interface works in 100 mbps or 10mbps? Where is that visible?  I have been fidling witht the ifconfig and ip commands and the device manager GUI, without much luck.

/Andreas

---

### Post by nad on 2005-08-25
"Diagnostics for most open source network drivers are here: [http://www.scyld.com/ethercard_diag.html](http://www.scyld.com/ethercard_diag.html) "

This is _the_ site for open source network drivers. There are several small utilities listed. Pick the one for your adapter and mii-diag.c , compile them for your system (this operation will take about one second and requires only the gcc compiler) and issue the command ./mii-diag or the one for your specific controller. These will show you all of your settings.

---

### Post by andka on 2005-08-27
Ah! yes the diagnositcs program  worked fine!

Thansk for all the help sofar!

However, I have now finally got around to try your proposal and it did not work perfectly for me. Here is what happend.

The short version:
de4x5 did not seem to be able to initiate my NIC, but if I first loaded and then removed 'tulip', the de4x5 module works fine (and better than the tulip module). Is this at all fixable? Or should I just get a better network card?

The longer version:
I added 'de4x5' on a new line in /etc/modules
I added 'tulip' on a new line in /etc/hotplug/blacklist

When I rebooted, eth1 did not work at all, but 'de4x5' was loaded (I checked with 'lsmod').

If I did a '[FONT=Courier New]ifup eth1[/FONT]' it produced the following message:

eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.

I now first did an 'rmmod de4x5' and a 'modprobe tulip', and the eth1 was possible to start (ifup eth1). But also, if I removed the tulip driver again (rmmod tulip) and reloaded the de4x5 module (modprobe de4x5) it also worked. Strange!

I guess the de4x5 is not doing the right thing initially, and does not initialize the card, or something else, in a correct way. 

Is this a lost case, or does anyone think this is fixable?

/Andreas

---

### Post by nad on 2005-08-29
You may wish to contact Mr Becker (his email addy is in dmesg).

Please include the output of dmesg , lspci , lspci -nvv and any other pertinent log files and error messages.

Be certain to first read through all of his docs relating to the drivers you have chosen to use, and have tried the configuration setting utilities.

---

