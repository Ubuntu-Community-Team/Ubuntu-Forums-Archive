---
title: "Adhoc XP problems."
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Dooley on 2008-11-26
Hey all,

I'm trying to set-up Synergy and am having problems creating an ad-hoc connection between ubuntu and windows xp, using a crossover cable. Here's the general config I have going.

Windows:
IP:192.168.1.5
Subnet Mask:255.255.255.0
Gateway:None

Linux:
IP:192.168.1.4
Subnet Mask:255.255.255.0
Broadcast:192.168.1.255(Not sure if this matters)

Anyway, for some reason pinging each of them doesn't seem to work. The cable is in properly, windows complains if it's unplugged at either end.

I'm not using any network managers so I'm no sure if that makes a difference.

Any help would be much appreciated!

---

### Post by Dooley on 2008-11-26
Can nobody help?
I'm just not sure what else could possibly be the problem. Or if the settings are wrong.

---

### Post by Dooley on 2008-11-26
Actually it worked fine now for some reason.

---

### Post by Dooley on 2008-11-27
Yeah, so actually it's decided not to work again after a reboot! The settings are exactly the same. Could anyone, at all tell me anything else might be an issue? I've tried different crossover cables etc but still no luck.

---

### Post by Dedoimedo on 2008-11-27
Are you using firewalls on these machines?
Dedoimedo

---

### Post by Dooley on 2008-11-27
Well I'm disabling the firewall(Comoodo) on Windows and I'm fairly certain there's no firewall on the linux box. I didn't kill anything on it when I got the connection working the first time.

---

### Post by Dooley on 2008-11-27
Okay, I uninstalled Comodo and rebooted, windows can now ping the linux box but not visa-versa. Would that means something is blocking the linux box?

---

### Post by Dedoimedo on 2008-11-27
You mean the other way around. If you can ping the linux box, this means it accepts icmp echo requests and replies to them. So the Windows machine is blocking ... check the Windows firewall settings and make sure icmp echo request is enabled for inbound.
Dedoimedo

---

### Post by Dooley on 2008-11-27
Ah there we go, cheers mate! Hopefully that should take care of the problem!

---

