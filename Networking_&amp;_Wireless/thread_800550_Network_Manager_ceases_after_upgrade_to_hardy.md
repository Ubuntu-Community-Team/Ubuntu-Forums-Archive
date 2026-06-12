---
title: "Network Manager ceases after upgrade to hardy"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by fishexe on 2008-05-19
Hi folks, I just upgraded to 8.04 and my Network Manager has simply stopped coming up in my gnome panel.  When I start it from the command line, either with the command "nm-applet" or with the command "nm-applet --sm-disable" (which is in my session startup programs) it gives me the following error:
** (nm-applet:20095): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.59" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

needless to say this error baffles me altogether.  I have no idea which configuration file has the offending security policy or even what the service "org.fre......" even is.  Also baffling is that the program (nm-applet) does not terminate at this point, but keeps trying what it's doing over and over, repeating the identical error message.:confused:

---

### Post by fishexe on 2008-05-20
I have tried the following things:

add <allow own="org.freedesktop.NetworkManagerInfo"/>
to the section marked <policy at_console="true">

in /etc/dbus-1/system.d/NetworkManager.conf
(recommended by [http://bbs.archlinux.org/viewtopic.php?id=30607](http://bbs.archlinux.org/viewtopic.php?id=30607))

this did not work...

added this:
        <allow own="org.freedesktop.NetworkManager"/>
        <allow send_destination="org.freedesktop.NetworkManager"/>
        <allow send_interface="org.freedesktop.NetworkManager"/>

between <policy context="default"> and </policy>
to /etc/dbus-1/system.d/NetworkManager.conf and /etc/dbus-1/system.d/nm-applet.conf
(per instructions in [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager))

both of which did not work, and

killall nm-applet
sudo nm-applet &
which DID work (it's how I'm connected right now) but I'm not comfortable running it as root any longer than I have to (for obvious reasons).

Any help would be much appreciated.

---

### Post by fishexe on 2008-05-20
I also tried:
sudo adduser $USER netdev
which some sites said was supposed to work, but got
The user `blah' is already a member of `netdev'.

So that's one more thing that didn't work.

---

