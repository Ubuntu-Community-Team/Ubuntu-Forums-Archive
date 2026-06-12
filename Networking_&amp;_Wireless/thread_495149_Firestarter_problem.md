---
title: "Firestarter problem"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by Bofur on 2007-07-07
I'm having trouble getting firestarter to run at startup. I added it to sessions and I changed the sudoers.tmp adding the line root ALL= NOPASSWD: /usr/sbin/firestarter but it still won't work. Any help would be appreciated.

---

### Post by kevdog on 2007-07-07
Forget Firestarter, go with Guard Dog, setup your iptables and then forget about it!

---

### Post by scxtt on 2007-07-07
firestarter will alter/set up your iptables rules AT BOOT - the gui does NOT have to be running in the taskbar for you to have a firewall ...

to be sure, reboot - then run **sudo iptables -L** and you'll see the rules ...

and i hope you used **visudo** instead of editing a file directly ...

---

### Post by edm1 on 2007-07-08
if you're trying to get the gui to begin at start up i cant help you but if the 'policies' aren't being loaded into iptables at start up have a look [here]("http://ubuntuforums.org/showthread.php?t=468630"). It may be a bug with networkmanager rather then firestarter.

---

