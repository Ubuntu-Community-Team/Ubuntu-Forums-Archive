---
title: "Deploying updates across network"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by skymedic on 2008-11-14
I have a small network running at home, which I use as much as a work platform for myself and the family as a tool to teach myself the ins and outs of computing, networking, etc. I have succeeded in tossing Windows out of the proverbial window, using it only as a gaming platform, and running Ubuntu8.04LTS as a working OS. So far, wonderful. I would like to set up the other machines on the network to also be dual boot systems, but would like to avoid unnescessary ADSL bandwidth consumption on a capped line. How can I set up my machine to download the (Ubuntu) updates from the net, but the other machines to look to my machine first and then only to the internet based repositories?

I have got a single port ADSL router connected to a gigabit switch through which the networked machines all connect. The ADSL router is also providing DHCP server function for the network.

---

### Post by nixscripter on 2008-11-14
The way I did it (or something similar for Gentoo) is to keep one machine up to date with automatic updates, and have it save all downloaded package files (it's an option in Synaptic preferenecs somewhere). Then, you can export the directory where it keeps them (**/var/cache/apt/archive**) to the other machines over NFS. This way, when they try to update, they'll think they already have downloaded all the packages, and not do it again.

The only drawback is that the machine exporting the directory probably has to be on all the time (i.e. like a server). It depends on whether you do the client side of the NFS automatically, manually, at boot, etc.

---

### Post by drenzu on 2008-11-14
I was doing this with 8.04 and all worked fine.

However, with 8.10, after every update I get an "error" message stating 
```
Not using locking for nfs mounted lock file /var/cache/apt/archives/lock
```
I think this message can be ignored, but it's rather annoying having to see it every time.

Does anyone know how to hide it?

---

### Post by skymedic on 2008-11-15
Thanks for prompt resonse and helping me in the right direction. I have downloaded and installed NSF server through the Synaptic Package Manager, but now I've no idea how to get the directory shared across the network, and getting the other machines to look to that directory first.

---

### Post by nixscripter on 2008-11-15
skymedic: there's a HOWTO for NFS here:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

drenzu: if you're mounting read-only (the wises idea for a shared cache), you can add **nolock** to your NFS mount options and it should go away.

---

