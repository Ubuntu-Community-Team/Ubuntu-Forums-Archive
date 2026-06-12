---
title: "Easy Home File Sharing with FTP and Zerconf on Ubuntu GNOME 14.04 amd64"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by lambdafox on 2014-06-23
I am trying to set up Easy Home File Sharing with FTP & Zeroconf with [this wiki]("https://help.ubuntu.com/community/EasyHomeFileSharingWithFTPAndZeroconf").

When I install avahi, there is no package called service-discovery-applet available.  When I do an ubuntu package search I see that this package is only available for lucid.  The dependencies suggest that it relies on GNOME 2, but Ubuntu GNOME 14.04 has GNOME 3.

I have been able to set up everything else according to the wiki.  I did set up announcements by creating an ftp.services file.

My desktop is called , randyb-desktop and I see it and the ftp service when I run Avahi Browser on my desktop.

I have a windows xp virtual machine running on this system.  I have Bonjour for Windows installed.  I also installed NetDrive.  When I try to connect net drive to [ftp://randyb-desktop.local:21](ftp://randyb-desktop.local:21) it fails.

I installed Bonjour Browser for windows and when I run it in the VM nothing appears in the list.  I can see my laptop which runs Vista in my network places, and I can also see the XP VM on the laptop.  Neither the laptop nor the desktop, however, show the ubuntu machine there either.

I manually opened port 5353 on the XP VM's firwall and that does not fix the problem.

Please help.

---

### Post by lambdafox on 2014-06-25
When I set up the bridge, I had inadvertently deleted the loopback interface from the /etc/network/interfaces file

Putting that back in and restarting, fixed the problem.

I started getting errors and found that I also needed to set 

    AVAHI_DAEMON_DETECT_LOCAL=0

in

/etc/default/avahi-daemon

Now my tablet running Windows Vista shows everything as expected in Bonjour Browser, and I can connect NetDrive to the ftp server on my desktop.

My XP VM still is not able to do the same.    Turning off the firewall on the desktop and VM does not solve the problem. 

I found the following in [this article]("http://jpamills.wordpress.com/2013/04/08/linux-life-syncing-iphone-with-itunes-on-a-virtual-machine/") from August 2013.

> ... Bonjour cannot bridge from the virtual machine over virtIO, ... Finally, i  found [mdns-repeater ]("https://bitbucket.org/geekman/mdns-repeater")a  small program that does exactly what I want: it runs on my Linux  machine, and forwards Bonjour packets from the virtual network between  the host and virtual machine...

---

