---
title: "Script vpn + netword manager"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by yalala on 2008-09-09
Hi,

I'm fairly new to linux and just decided to get rid of windows for good. I was wondering if someone might be able to help me out with a script concerning my internet connection.

I am using my university's wifi in my tiny student room, and i'm having issues. I am then using VPNc to log in, using that command :

# gksudo "xterm -e vpnc-connect --no-detach upmf.conf"

The command works real nice, but the connection is really crappy and keeps disconnecting, forcing me to disable the wireless in network manager, the enable it, wait for the laptop to get the connection, then launch the vpnc command again... Kind of annoying when you have to do it every 5 mins !

There comes my idea : would it be possible to build some kind of script that would work that way :

If 
     Connection down
Then
     Disable wifi, enable wifi, wait for connection
     Launch vpnc using the command line

Please tell me if anything can be done, it is way out of my league !

Thanks in advance guys

PS1 : sorry if the english feels kinda weird, i'm French :)
PS2 : to admin, not sure it is the right section, sorry if its not !

---

### Post by Sef on 2008-09-09
Moved to networking and wireless.

---

### Post by yalala on 2008-09-11
Anyone ??

---

