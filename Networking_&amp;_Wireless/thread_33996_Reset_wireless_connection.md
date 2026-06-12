---
title: "Reset wireless connection?"
date: 2005-05-13
forum: Networking &amp; Wireless
---

### Post by doans on 2005-05-13
I have just reinstalled Hoary with the hope of getting my wireless internet connection to be stable.  The wireless internet connection works, but only for a short time and then basically locks Ubuntu up.  It basically makes my system completely unusable with having to restart constantly.

I am using a Netgear router (in b and g mode) and Netgear WG111 (version 1? I think) USB wireless adapter (using 128bit WEP encryption, no DHCP) with the use of NDISWRAPPER-Utils 0.12+1.0rc2-1 .  Everything works fine for an hour or so and then I lose internet connectivity.  Shortly after I lose the internet connection the computer eventually just locks up.  Appears that everything is dependent on the connection.

I am wondering if there is a way to reset/restart/reprogram the wireless adapter so I don't have to restart Ubuntu just to get the internet working again?  I have tried removing the adapter from the USB port and plugging back in, but that just locks the computer up faster!  There has to be a way to reset, or clear this thing out, and then start the wireless connection over again.

Also, would upgrading to the latest version of Ndiswrapper-utils from breezy help?  And, would finding a different version of the windows driver help?

Any help would be much appreciated.

---

### Post by poofyhairguy on 2005-05-13
[http://ubuntuforums.org/showthread.php?p=170076#post170076](http://ubuntuforums.org/showthread.php?p=170076#post170076)

I'm currently asking for a backport of the new ndiswrapper on your behalf. I think that upgrading ndiswrapper will fix the problem. If you can't wait, you can install the new ndiswrapper from the source.

---

### Post by doans on 2005-05-13
[QUOTE=poofyhairguy][http://ubuntuforums.org/showthread.php?p=170076#post170076](http://ubuntuforums.org/showthread.php?p=170076#post170076)

I'm currently asking for a backport of the new ndiswrapper on your behalf. I think that upgrading ndiswrapper will fix the problem. If you can't wait, you can install the new ndiswrapper from the source.[/QUOTE]
 I will try to install the new ndiswrapper-utils from source.  I am ready to try anything to get this connection more stable.  Thanks for the reply.

---

### Post by doans on 2005-05-13
[QUOTE=poofyhairguy][http://ubuntuforums.org/showthread.php?p=170076#post170076](http://ubuntuforums.org/showthread.php?p=170076#post170076)

I'm currently asking for a backport of the new ndiswrapper on your behalf. I think that upgrading ndiswrapper will fix the problem. If you can't wait, you can install the new ndiswrapper from the source.[/QUOTE]
 Okay, I am confused now. Install ndiswrapper from source?  I am not finding ndiswrapper-utils source?  Are ndiswrapper and ndiswrapper-utils the same?  Maybe this is a dumb question, but I am not sure what I am supposed to install.

---

