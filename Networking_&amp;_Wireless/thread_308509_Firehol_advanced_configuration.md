---
title: "Firehol advanced configuration"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by hewhocutsdown on 2006-11-28
Hello

I have installed the parental controls onto Edgy Eft via this script & tutorial:
[http://christer.homeip.net/index.php/2006/11/24/parental-controls-with-dansguardian-tinyproxy-firehol-ubuntu-6061-610/](http://christer.homeip.net/index.php/2006/11/24/parental-controls-with-dansguardian-tinyproxy-firehol-ubuntu-6061-610/)

The controls are working brilliantly; I´ve configured the proxy and the various controls.

Here now lies the problem. I need to do some advanced firewall operations, and I have never used firehol before. Reading the threads on here, and online tutorials haven´t helped much.

The closest I´ve found has been [http://firehol.sourceforge.net/tutorial.html?](http://firehol.sourceforge.net/tutorial.html?), however all the helpme command gives are:

$ sudo /etc/init.d/firehol helpme
Password:
Usage: /etc/init.d/firehol {start|stop|restart|force-reload} [<args>]

Here are my goals:
for the eth+ interfaces (sit+ could probably get the same):
From outside my network, going in I need to access:
SSH (port a), VNC (port b-d), VMWare Server (port e), FTP (port f), HTTP (f)
From inside my network, reaching out I need:
HTTP, FTP, Bittorrent, SSH, etc etc; pretty extensive.
vmnet should be wide open.

Now, I´ve figured out my network devices (lo, eth0, eth1, sit0, vmnet8, vmnet1) and came up with this general skeleton of a conf file as a beginning

interface eth+ home
	server dns	accept
	server ftp	accept
	server dhcp	accept
	server http	accept
	server ssh	accept

	client ssh	accept

interface sit+ wireless
	client all	accept

interface vmnet+ vmware
	client all	accept
	server all	accept

Is this even remotely on the right track? If so, how do I add things like the port range I have set up for bittorrent?

---

