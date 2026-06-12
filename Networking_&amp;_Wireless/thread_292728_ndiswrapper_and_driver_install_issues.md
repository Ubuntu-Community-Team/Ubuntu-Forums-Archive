---
title: "ndiswrapper and driver install issues"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by thistlebrae on 2006-11-04
Hi all,

ThinkPad T30 with Edgy running beautifully and LAN adapter zooming.

Attempting to install NetGear WG111 USB wireless adapter and running into driver load issues.  NDISWRAPPER installed and seemingly running correctly.  When I execute the $ sudo ndisgtk command to install the driver I get the following message in the terminal window:

[INDENT]tmiller@tmiller-thinkpad:~$ sudo ndisgtk
Password:

(ndisgtk:4700): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
modprobe config already contains alias directive[/INDENT]

Despite that the driver load window does appear and I select the appropriate driver .inf file.  When I click install...nothing happens in the installer program and the driver does not load.  When I look in the terminal window I see the following message:


[INDENT]FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
[/INDENT]

Any suggestions, hints, guidance would be most appreciated!

Thanks...

---

