---
title: "eth0:avahi and no IP by DHCP"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by mbeccaria on 2008-05-23
I am using Ubuntu 8.04 being wired to my company network, on which we have to use DHCP.

From time to time, when I boot the PC I fail in connecting to the network.
If i run the ifconfig command, I see a weird network interface labelled as eth0:avahi and no IP address is given to standard eth0 IF

To overcome this, I have to run the following command

sudo dhclient eth0

Can anybody explain what's happening ?
Is there any problem with my DHCP client at boot time ?
Is there any drawback in removing AVAHI from the system ?

Thanks in advance for the replies-

---

### Post by superprash2003 on 2008-05-23
go to system->administration->network and go to eth0 properties and select DHCP instead of Roaming mode

---

### Post by larubbio on 2008-06-09
I'm running into the same issue, however running sudo dhclient eth0 does not fix my issue (only a reboot does) and my wired interface is set to dhcp, not roaming.  Is there another config I need to check?  Thanks.

Also I just want to add I do show an eth0 interface with an ipv6 address, but no ipv4.  eth0:avahi has an ipv4 address but no ipv6

Just adding a little more information.  When I am in this state, if I set up eth0 with a static ip like this:

IP: 192.168.1.107
Mask: 255.255.255.0
Gateway: 192.168.1.1

The ifconfig entry looks correct, but the machine is unable to ping anything.

---

### Post by crane on 2008-06-10
I'm having the same issues on my work PC. I have tried everything I can think of but no luck. I can get it to connect after about 6 to 10 restarts, but that is totally random.

---

### Post by Daneel24 on 2008-06-16
I had the same problem with my network disconnecting every now and then, and when switching between wlan and wired, I got the same eth0:avahi interface and no internet connection. I had to solve it by restarting, but superprash2003's solution seems to have fixed that.

[EDIT] Scratch that. The connection still dies, except now, my ifconfig output doesn't change. It looks perfectly normal with the usual local IP, but I still don't have a connection.

Running dhclient gives me "No DHCP offers" received. Still works when I restart the computer though.

---

### Post by bhamail on 2008-09-10
Apologies if this is not related, but after spending a few hours banging my head against the wall trying to get my wireless network working in Hardy Heron 8.04 - the solution was just too embarrassing not to share:

All the while, I had been right clicking on the network management icon on the system tray to show the "Enable ..." menus ( screenshot attached as screenshot-rightclick.gif )

After far too many years being conditioned to expect nothing from left clicking system tray icons, I finally tried left-clicking the same network tray icon ( screenshot-leftclick.gif). Shazam - it shows all the available wireless nets and lets me pick one to connect to and it all just worked!

I realize most are not a dumb as I, but just in case someone else might google the same "eth0:avahi" and "wlan0:avahi" and "wmaster:avahi" keywords, maybe my post will save them some time.

Dan

---

