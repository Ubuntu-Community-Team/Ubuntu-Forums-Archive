---
title: "Openvpn DNS leak almost resolved......almost"
date: 2015-12-30
forum: Networking &amp; Wireless
---

### Post by dave205 on 2015-12-30
(Ubuntu 15.10)
So if I follow the instructions here ([http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html](http://www.ubuntubuzz.com/2015/09/how-to-fix-openvpn-dns-leak-in-linux.html)) then it actually fixes the issue BUT you must run openvpn from the cli and manually type in the username/password every time. I am using Private Internet Access (PIA) and they have preconfigured ovpn files that you can use to launch the vpn form the cli. ([http://www.privateinternetaccess.com/openvpn/openvpn.zip](http://www.privateinternetaccess.com/openvpn/openvpn.zip))  Or....you can use those as templates to import into the network manager. (next step)


I would like to use the network connection manager to launch the vpn connection as there is an option to have the vpn auto launch when the wireless is activated. Problem is, if I import the ovpn files from the zip above, then Ubuntu creates a new configuration file within /etc/NetworkManager/system-connections.  This is what I assume the network manager is using to launch the vpn.  I have tried appending the fix into these created files but that doesn't seem to work. I get leaks detected.

I have tried adding the extra security lines as described on ubuntubuzz above into the opvn file before importing into the network manager AND also adding those lines to the network manager created config file (after import) and neither one seems to work. The only sure fire way to stop the leak is to not use the network manager at all and just run cli. 

Any ideas?

---

### Post by Seanan on 2016-01-04
I would think that you could make a executable that dumps wireless connectivity info and runs your vpn if it finds something in the dump and then use cron to run it every 30 seconds or something. Sorry if this doesn't help.

---

### Post by weatherman2 on 2016-01-04
I use Cuttlefish to connect to my VPN automatically when I connect to certain wireless networks.  Cuttlefish is a Gui-based event manager; based on certain triggers, it can execute various commands.  OpenVPN via Network Manager does work fine for me in Ubuntu 12.04, though.  I'm pretty sure you could put the password in a file on on the command line if issuing the openvpn via a command line, although that technically puts your password in the clear and makes it not very secure.

---

### Post by dave205 on 2016-01-04
> **weatherman2 said:**
> I use Cuttlefish to connect to my VPN automatically when I connect to certain wireless networks.  Cuttlefish is a Gui-based event manager; based on certain triggers, it can execute various commands.  OpenVPN via Network Manager does work fine for me in Ubuntu 12.04, though.  I'm pretty sure you could put the password in a file on on the command line if issuing the openvpn via a command line, although that technically puts your password in the clear and makes it not very secure.

interesting!  so you can check for DNS leak and it only shows the DNS from your VPN provider?  If so, sounds like they broke something. I know in 15.x and have heard that in 14.x, the DNS leaks.


I'll have to look into cuttlefish and report back what I find. thanks for the tips!

---

### Post by dave205 on 2016-01-04
> **weatherman2 said:**
> I use Cuttlefish to connect to my VPN automatically when I connect to certain wireless networks.  Cuttlefish is a Gui-based event manager; based on certain triggers, it can execute various commands.  OpenVPN via Network Manager does work fine for me in Ubuntu 12.04, though.  I'm pretty sure you could put the password in a file on on the command line if issuing the openvpn via a command line, although that technically puts your password in the clear and makes it not very secure.

Weatherman, I looked up cuttlefish and the only thing I can find is in the UB software center and it says it is a "icon previewer for artists & devleopers".  A quick google search for cuttlefish event manager didnt turn up any results either.  Do you have any links or pointers to it?

---

### Post by weatherman2 on 2016-01-05
> **dave205 said:**
> Weatherman, I looked up cuttlefish and the only thing I can find is in the UB software center and it says it is a "icon previewer for artists & devleopers".  A quick google search for cuttlefish event manager didnt turn up any results either.  Do you have any links or pointers to it?

Well, I found this:

[http://ubuntuhandbook.org/index.php/2014/03/install-cuttlefish-in-ubuntu-14-04-or-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2014/03/install-cuttlefish-in-ubuntu-14-04-or-ubuntu-13-10/)

but unfortunately, it seems that Cuttlefish has been abandoned.  I was able to build it in 14.04 using the link above, but I could not build it at all in 15.10.

---

### Post by dave205 on 2016-01-05
> **weatherman2 said:**
> Well, I found this:

[http://ubuntuhandbook.org/index.php/2014/03/install-cuttlefish-in-ubuntu-14-04-or-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2014/03/install-cuttlefish-in-ubuntu-14-04-or-ubuntu-13-10/)

but unfortunately, it seems that Cuttlefish has been abandoned.  I was able to build it in 14.04 using the link above, but I could not build it at all in 15.10.

well darn.  I did get another site as a resource to read though. So that's good.

---

### Post by davehenson on 2016-01-14
Dave205, looks like this is a known issue already. Being tracked in Ubuntu's bugtracker. [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1211110](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1211110)

---

