---
title: "Why won't firestarter..."
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by william_hunter on 2007-07-06
I have set up rules in firestarter, to allow ports to be open for a game server, web server, and VNC. It does not seem that these rules are being followed by the firewall at all, because I have to actually manually disable firestarter each time I reboot the machine. Any insights?

---

### Post by dreadlord_chris on 2007-07-06
> **william_hunter said:**
> I have set up rules in firestarter, to allow ports to be open for a game server, web server, and VNC. It does not seem that these rules are being followed by the firewall at all, because I have to actually manually disable firestarter each time I reboot the machine. Any insights?

Ya, get rid of firestarter. Alot of people have been having issues with firetstarter's firewall rules completely dissapearing after reboots.

I recently switched from firestarter to Guarddog for firewall configuration. It's a little more tricky to set up, but in the end far more flexible then firestarter.

---

### Post by william_hunter on 2007-07-06
It just doesnt seem to stay persistent for whatever reason. I did tinker with the startup programs and it seemed to start up on system reboot, though, and it seems more stable now. I dunno.

---

### Post by dreadlord_chris on 2007-07-07
> **william_hunter said:**
> It just doesnt seem to stay persistent for whatever reason. I did tinker with the startup programs and it seemed to start up on system reboot, though, and it seems more stable now. I dunno.

after you reboot, from a command line enter:
```

sudo iptables -L

```

if it spits out a bunch of stuff - then firestarter is working....

---

### Post by edm1 on 2007-07-08
look [here.]("http://ubuntuforums.org/showthread.php?t=468630") i think it may be a problem with network manager rather then firestarter.

---

