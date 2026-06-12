---
title: "Ubuntu 14.04 Wireless Connection Stopped Working"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by pac-g on 2016-05-16
[SOLVED] I was reading Yahoo news on Firefox when it appeared to get overloaded and froze the entire system, I'm assuming from so many advertisements.  I had to press the power button on the laptop to turn off the computer.  I turned the computer back on, logged back into Ubuntu, and there was no wireless connection whatsoever.  Nothing AT ALL, as in zippo, zilcho and squato.  :(  No connectivity, no sign of life at all, no icon above. Nothing.  The Ubuntu system itself still works great.  This was NOT the result of an upgrade or an update.

The computer is an Acer Aspire 7741Z-4643 laptop.  Operating system is Ubuntu 14.04, dual-boot with Windows 10 upgrade.

Wireless Info Script result [is here]("http://paste.ubuntu.com/16453557/")

From searching on UbuntuForums I've tried this:

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

That didn't work.

Tried this:

sudo apt-get install --reinstall linux-generic
sudo apt-get install

Then rebooted, but that didn't work either.  I've also tried various information commands, and it does detect wlan0.  Thanks beforehand.

Oh, I forgot to mention I finally tried logging into Windows 10 to see if the wireless connection works at all.  It WORKED great in Windows.

[Update] It appears it might be an update issue after all.  I forgot about an update notice to which I didn't pay much attention.  I ran Software Updater again hoping it might have saved the update information.  Sure enough I had updates for things like network-manager, which is currently not working.  Now I need to learn how to manually download and install the packages that need to be updated.  Here is everything listed by Software Updater:

Central cgroup manager daemon(client library)
Changes for libcgmanager0 versions:
Installed version: 0.24-0ubuntu7.5
Available version: 0.39-2ubuntu2~ubuntu14.04.1

GObject introspection data for NetworkManager
Changes for gir1.2-networkmanager-1.0 versions:
Installed version: 0.9.8.8-0ubuntu7.2
Available version: 0.9.8.8-0ubuntu7.3

Library for dealing with netlink sockets
Changes for libnl-3-200 versions:
Installed version: 3.2.21-1ubuntu1
Available version: 3.2.21-1ubuntu1.1

Library for dealing with netlink sockets-generic netlink
Changes for libnl-genl-3-200 versions:
Installed version: 3.2.21-1ubuntu1
Available version: 3.2.21-1ubuntu1.1

Library for dealing with netlink sockets-route interface
Changes for libnl-route-3-200 versions:
Installed version: 3.2.21-1ubuntu1
Available version: 3.2.21-1ubuntu1.1

Network management framework (daemon and userspace tools)
Changes for network-manager versions:
Installed version: 0.9.8.8-0ubuntu7.2
Available version: 0.9.8.8-0ubuntu7.3

Network management framework (GLib shared library)
Changes for libnm-glib4 versions:
Installed version: 0.9.8.8-0ubuntu7.2
Available version: 0.9.8.8-0ubuntu7.3

Network management framework (GLib VPN shared library)
Changes for libnm-glib-vpn1 versions:
Installed version: 0.9.8.8-0ubuntu7.2
Available version: 0.9.8.8-0ubuntu7.3

Network management framework (shared library)
Changes for libnm-util2 versions:
Installed version: 0.9.8.8-0ubuntu7.2
Available version: 0.9.8.8-0ubuntu7.3

Unity Tweak Tool
Changes for unity-tweak-tool versions:
Installed version: 0.0.6ubuntu1
Available version: 0.0.6ubuntu2~ubuntu14.04.1

XSL stylesheets for the yelp help browser
Changes for yelp-xsl versions:
Installed version: 3.10.1-1
Available version: 3.12.0-1~ubuntu14.04.1

Central cgroup manager daemon(client library)
Changes for libcgmanager0:i386 versions:
Installed version: 0.24-0ubuntu7.5
Available version: 0.39-2ubuntu2~ubuntu14.04.1

SUCCESS!!!  I Googled and searched for the exact packages I needed.  Put them all in one folder, transferring them to my main laptop.  In the terminal, navigate to the folder with the *.deb files and enter
sudo dpkg -i *.deb

---

