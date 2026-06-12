---
title: "PPTP VPN from command Line?"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by ashish2512 on 2008-02-17
Hi all

I have installed pptp for network manager and it works great. But, now I need to use vpn in a script so that I can connect to the vpn server, sync some files, and disconnect when the job is done.

Is there a way to connect/disconnect vpn using command Line? 

I have tried using the following command.
nm-ppp-auth-dialog -s 'org.freedesktop.ppp_starter' -n <Name of VPN connection>
The dialog box for username and password comes up but it just freezes after that.

Any help will be appreciated.

---

### Post by ashish2512 on 2008-02-17
After executing VPN from panel, I saw nm-ppp-auth-dia in the processes. Is there a way to figure out exactly what command is being run?

---

### Post by ashish2512 on 2008-02-17
anyone?

---

### Post by achianese on 2008-02-19
Sorry I don't know how, but I would like to do this too.

---

### Post by The Cog on 2008-02-19
I set my work access up using this guide, using the configuration by hand method (about halfway down). My command to connect is simply 
**pon <name>**
wherne <name> is the name of the file in /etc/ppp/peers.


[http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)

---

