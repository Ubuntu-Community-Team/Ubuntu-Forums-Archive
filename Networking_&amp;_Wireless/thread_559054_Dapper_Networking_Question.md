---
title: "Dapper Networking Question"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by SuperMike on 2007-09-24
I'm trying to write a web-based admin system for an Ubuntu Server (Dapper version). I want to know what files should I edit in order to configure the network card? My scripts will control this programmatically.

Some things I need to do with it:

* Change it's speed depending on the environment: 10, 100, 1000, auto
* Turn on or off autonegotiation
* Edit the DNS client settings
* Change from DHCP Client to Static IP.
* Change from Static IP to DHCP Client.
* Set the default gateway
* Autodetect the default gateway
* Reload the network config after it has been edited, and without rebooting

Anyone have an idea what files to edit or commands to run?

---

### Post by noob12 on 2007-09-24
Well, look at **man interfaces** which covers the **/etc/network/interfaces** file and most of what you are talking about.

For control of ethernet speed, duplex, autonegotiation, etc., you can usually use invocations of **ethtool -s** (**man ethtool**) within **pre-up** lines in this file.

---

### Post by SuperMike on 2007-09-24
> **noob12 said:**
> Well, look at ...

Hey, thanks! :)

---

### Post by tgalati4 on 2007-09-24
I would spend some time eyeballing the Gnome Network tool (System-->Admin-->networking).  It takes most your list and makes a really long ifconfig statement.

For details:

>man ifconfig 


If you are looking for remote management tools, there are several out there already:

[www.centrify.com/trial](www.centrify.com/trial)

[http://www.groundworkopensource.com/](http://www.groundworkopensource.com/)

Suse Enterprise Server Edition 10

and I'm sure IBM has some tools as well.

Perhaps you can pattern your efforts after what is already available.

---

