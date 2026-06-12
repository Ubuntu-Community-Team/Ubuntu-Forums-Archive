---
title: "NetworkManager bug?"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by EpicNoob on 2011-05-03
Few hours ago my computer glitched out and I had to force-reboot. Now my NetworkManager:
a) doesn't show up ([ifupdown] managed=false)
b) shows up ([ifupdown] managed=true), but Auto eth0 is named ifupdown (eth0) instead and it doesn't connect to the network)
Right now I'm using a LiveCD version and I wouldn't like to reinstall Ubuntu. Is there any way to fix that?

---

### Post by EpicNoob on 2011-05-04
Bump&some progress
Managed to update to 11.04. Now, if [ifupdown] managed=false I can't see any wired connections in NM menu (using VPN), but still can see them in connections editor (where you add them). And if [ifupdown] managed=true, I see all of them, but no programs can use it (FF, qutIM, Opera - ABSOLUTELY no connection, just times out), but I still can use ping and traceroute. Help?

---

### Post by EpicNoob on 2011-05-05
Bump

---

### Post by EpicNoob on 2011-05-07
God damn bump
Will I ever get help :(?

---

### Post by grahammechanical on 2011-05-07
Can we start from the beginning? Do you see a Network Manager icon? With a wired connection it should be two arrows going in opposite directions. What do you see when you click the icon? Do you see any wired network connections with information about the ethernet controllers? Is there a tick mark against the line Enable Networking? With a wireless connection you need a tick mark against the line Enable Wireless.

Wired connections should make easy connection to the modem/router. 

I suggest (it is only a suggestion. I do not give it as an answer) that you delete the wired connections that you have put in Network manager. Then shutdown and reboot. Allow network manager to find its own wired connections (that is what it is there for). Which should be Auto eth0 and Auto eth 1 (if you have two ethernet adapters).

Try powering off the router and powering it back on. By clicking on Enable Networking you switch the network adapters off and on. Doing that sometimes stimulates a probe for a connection.

Regards.

---

### Post by EpicNoob on 2011-05-10
> **grahammechanical said:**
> Do you see a Network Manager icon? With a wired connection it should be two arrows going in opposite directions.
Yep
> **grahammechanical said:**
> What do you see when you click the  icon? Do you see any wired network connections with information about  the ethernet controllers?
If I set managed=true in [ifconfig] of file /etc/NetwrokManager/NetwrokManager.conf., I see One aouto-made connection and one connection made by 01ifupdown script. If I set managed-false, I don't see a single wired connection.
> **grahammechanical said:**
> Is there a tick mark against the line Enable  Networking? With a wireless connection you need a tick mark against the  line Enable Wireless.
Yes, and using wired connection.
> **grahammechanical said:**
> 
I suggest (it is only a suggestion. I do not give it as an answer) that  you delete the wired connections that you have put in Network manager.  Then shutdown and reboot. Allow network manager to find its own wired  connections (that is what it is there for). Which should be Auto eth0  and Auto eth 1 (if you have two ethernet adapters).

Try powering off the router and powering it back on. By clicking on  Enable Networking you switch the network adapters off and on. Doing that  sometimes stimulates a probe for a connection.

Ok, I'll try it, will post about it in ~10 minutes.

---

### Post by EpicNoob on 2011-05-14
Didn't work. Still using LiveCd. Bump.

---

### Post by candtalan on 2011-05-14
> **EpicNoob said:**
> Didn't work. Still using LiveCd. Bump.

sorry to see you still have problems.
I am not a networking person. At this stage though, with an unknown glitch problem presumably causing grief, it might be worth considering to confirm that your hardware is all ok including ram and certainly hard drive (eg disc utility etc etc)
good luck

---

