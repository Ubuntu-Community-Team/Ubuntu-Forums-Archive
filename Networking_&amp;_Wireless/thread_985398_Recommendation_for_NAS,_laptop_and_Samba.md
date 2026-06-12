---
title: "Recommendation for NAS, laptop and Samba"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Cereus on 2008-11-17
I would like some advice for a setup I would like to try with my NAS and laptop.

Ultimately I would like to have the NAS mounted automatically when my laptop is connected to my home network, but not when I'm out and about.

currently I run eeeBuntu (on an eeePC 900) and can mount and unmount the NAS with samba from the command line and sudo.

Right now I have problems when I am shutting down the computer when I haven't manually unmounted and it complains about not being able to unmount(? must check error this evening) - either the NAS is on standby and doesn't accept the auto-unmount command or since the NAS isn't in fstab, as the computer is turned off it doesn't have permissions to unmmount.  Irrregardless, I think this problem can be solved as I work with fstab (unless anyone has some great insight).

I'm pretty certain I could add the NAS to fstab following this [excellent guide]("http://ubuntuforums.org/showthread.php?t=283131").

My question is will the laptop have big troubles if the NAS is listed in fstab but isn't always attached? I can just plug away and try it but I thought I'd try and learn a bit more.

---

