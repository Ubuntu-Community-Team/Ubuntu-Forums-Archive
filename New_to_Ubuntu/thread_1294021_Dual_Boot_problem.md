---
title: "Dual Boot problem"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by Fidelio on 2009-10-17
Probably a Windows thing, but every time I boot into windows, or almost every time, I cant connect to the Internet. I always have to go into tools, diagnose connection problems (or whatever it's called) and leave it for a minute to fix it. Then it's fine. Why would that happen?
I connect with an ethernet connection to a Voyager router.
Puzzled, I am.
Thanks

---

### Post by mbeichorn on 2009-10-17
I am uncertain as to what may be the case, way Windows are you running. I have encountered similar networking problems after sleeping in Win7RC. But regardless this is independent of the dual boot, unless there is some strange configuration in your LAN.

---

### Post by houbysoft.xf.cz on 2009-10-17
More detail would help, I would maybe record what it says in linux about the network when you connect (ifconfig) and then when you reboot, check the details about the connection before fixing, see if there is something badly configured (different than in Ubuntu), and then see what changed (if anything did) after you use the windoze repair thingy.

As was said before though, there is a very, very marginal probability that this is caused by dual-boot.

EDIT: whoops, your connection is wired not wireless, ifconfig then.

---

### Post by yeats on 2009-10-17
It's possible your router is confused by seeing a two OS's using the same MAC address to connect.  I've had issues with this regarding certain hot spots' security settings.

---

### Post by falconindy on 2009-10-17
> **chrissharp123 said:**
> It's possible your router is confused by seeing a two OS's using the same MAC address to connect.  I've had issues with this regarding certain hot spots' security settings.
More likely related to DHCP than the operating system. Speaking from a network level, devices don't care what OS you're using. To that effect, it might help to set static IPs.

---

