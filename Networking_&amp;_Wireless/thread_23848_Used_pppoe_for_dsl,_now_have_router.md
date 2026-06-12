---
title: "Used pppoe for dsl, now have router"
date: 2005-04-04
forum: Networking &amp; Wireless
---

### Post by cburg on 2005-04-04
Hi Folks - I recently installed HH 5.04 as a dual boot w/ XP on a compaq desktop.  I am new to Linux although I used to be able to get around DOS a little using command lines. Thanks to your active community and some lucky searching, I managed to get pppoe working in Linux and could connect to my verizon dsl account.  I'm pretty sure I used 'sudo pppoeconf' in terminal.  

We are getting a laptop soon and I bought a router.  I wired the desktop to the router and modem and XP works thru it, but HH wouldn't.  After some searching, I found I could use 'sudo dhclient' to connect, but it seems I have to run it each time I boot into HH.  Also, it hangs trying to exit Linux.  I suspect it is still loading pppoe at startup and maybe there is a conflict.  I tried 'sudo pppoe -i' and 'apt-get--purge remove pppoeconf' but I get errors.  

Suggestions?  Please give complete commands as I don't really know how to do anything and find myself slipping into trying DOS commands.

Thanks - Dale

---

### Post by arctic on 2005-04-04
first of all: try to set up a lan connection with the networking tool in your top panel (system section). once you have set up your network-card, check if your system works. if not, please post the output of the following command:

ifconfig eth0

---

### Post by cburg on 2005-04-04
Thanks - that seems to have worked.  Although the startup screen said loading ppp, Firefox connected and loaded the startup page as I hoped - Dale

---

