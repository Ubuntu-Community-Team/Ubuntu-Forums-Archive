---
title: "Internet connectivity fails"
date: 2010-04-15
forum: New to Ubuntu
---

### Post by KaleXD on 2010-04-15
So, I have an HP laptop with a wireless network and dlink router with WPA/WPA-2 Personal encryption. The computer is triple booted ubuntu 10.04 beta 2, windows vista, and windows 7, and both windows computers connect to the internet fine, and I've verified that the password is right.

Now onto the problem.
When I (try to) connect to the internet, I get all the way, and it attempts connecting for around 5 minutes, but then it just asks for the password again, and again... and again.

Other info:
It connected to the internet fine at the start, and it was doing good, but then randomly disconnected and this started happening.
Also, it has recently started ignoring my network, and all the other ones I normally see in the "available networks" menu. I've had to enter my SSID manually under "Connect to a hidden network".


I am out of ideas. I guess I'll resort to restarting my computer over and over again until it works... ](*,)

---

### Post by garvinrick4 on 2010-04-15
This is the program open a terminal and use these commands one at a time.

sudo apt-get remove network-manager-gnome

sudo apt-get clean

sudo apt-get install network-manager-gnome


This uninstalls package incase is bad, cleans cache of the packages in your cache, and go's out and fetches a new one.

Here is what the package does.

rick@rick-laptop:~$ aptitude show network-manager-gnome
Package: network-manager-gnome
State: installed
Automatically installed: no
Version: 0.8-0ubuntu3
Priority: optional
Section: net
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5,022k
Depends: libatk1.0-0 (>= 1.29.3), libc6 (>= 2.4), libcairo2 (>= 1.2.4),
         libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>=
         2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.27.0), libglade2-0
         (>= 1:2.6.1), libglib2.0-0 (>= 2.18.0), libgnome-bluetooth7 (>=
         2.27.8), libgnome-keyring0 (>= 2.20.3), libgtk2.0-0 (>= 2.16.0),
         libnm-glib2 (>= 0.8~rc2~git.20091229t135236.302e62d), libnm-util1 (>=
         0.8~a~git.20090930t162132.866d48b), libnotify1 (>= 0.4.5),
         libnotify1-gtk2.10, libpango1.0-0 (>= 1.14.0), libxml2 (>= 2.6.27),
         zlib1g (>= 1:1.1.4), gconf2 (>= 2.10.1-2), network-manager (>=
         0.8~rc2), gksu, mobile-broadband-provider-info (>= 20090622)
Recommends: notification-daemon
Description: network management framework (GNOME frontend)
 NetworkManager attempts to keep an active network connection available at all
 times. It is intended only for the desktop use-case, and is not intended for
 usage on servers. The point of NetworkManager is to make networking
 configuration and setup as painless and automatic as possible.  If using DHCP,
 NetworkManager is _intended_ to replace default routes, obtain IP addresses
 from a DHCP server, and change nameservers whenever it sees fit. 
 
 This package contains a systray applet for GNOME's notification area but it
 also works for other desktop environments which provide a systray like KDE or
 XFCE. It displays the available networks and allows to easily switch between
 them. For encrypted networks it will prompt the user for the key/passphrase and
 it can optionally store them in the gnome-keyring. 
 
 Homepage: [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

rick@rick-laptop:~$

---

### Post by KaleXD on 2010-04-16
woah.

well i fixed it by simply restarting.

thanks anyways! :D

---

