---
title: "Two wireless networks with same name"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by pickture on 2008-09-18
There are two wireless networks with the same name, "linksys" one secured, one unsecured. I want to connect to the unsecured network, but Ubuntu can only show one of the networks at a time. Rebooting sometimes helps temporarily. If I reboot 10 times, the unsecured network will show up maybe once. It does this on both my laptop and my desktop. If I boot into Windows, I can use both networks just fine.

I don't know if this is a known or unknown issue. I've tried searching and found no solution. I'm using hardy heron on both machines. Any help is appreciated.

---

### Post by tacticalbread on 2008-09-18
couldn't you manually connect to the network?

---

### Post by lswb on 2008-09-18
Are you using Network Manager? I haven't found a way to get it to display different wifi networks with the same essid or specify which to use. This is one of several NM flaws I am hoping will be addressed in an upgrade. 

You can use the command line tools to specify the correct net with the hardware address of the desired access point, read the man pages for exact details but the syntax is something like:

sudo iwconfig eth1 mode managed essid "networkname" ap 00:11:22:33:44:55

where the string of numbers distinguishes one access point from the other. The  command 

sudo iwlist scanning 

will show the different wifi nets in range and there essids and other info, then use for the iwconfig command.

To make it easier, you can install another wireless net manager that will display all networks including duplicate essid. wicd is a popular choice but it will uninstall NetworkManager. The "rutilt" program is a simple wifi manager available from the ubuntu repositories and it will install without bothering NetworkManager. wifi-radar is another but I can't recall if it forces uninstall of NM or not.

---

