---
title: "settings won't stick tired or plain stupid ?"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by r4ik on 2007-12-19
My networksettings will not survive a reboot.
This is what i did,

1. Open a terminal window and type the following.

    $ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0

Still on reboot it is back to 192.168.1.1

Where do i go wrong ?
Help would be appreciated 
TIA

---

### Post by r4ik on 2007-12-20
Bump

---

