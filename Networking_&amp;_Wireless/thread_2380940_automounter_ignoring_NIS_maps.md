---
title: "automounter ignoring NIS maps"
date: 2017-12-24
forum: Networking &amp; Wireless
---

### Post by bautsche on 2017-12-24
I'm in the process of moving my infrastructure to ubuntu. Currently working on getting a container to work.
This container is running 17.10 on top of a server running 17.04.
I have NIS and NFS configured and I can log in to the container with NIS-defined accounts.
However, the automounter is ignoring the NIS automounter maps.
The underlying server does not have this issue and I have been trying to work out the difference by comparing the configurations, but I can't find what might be wrong in the container.
If I add the maps to auto.master and create local map files, automounter does what it's supposed to but I want it to read the maps from NIS.
Any great ideas what to do?
(should there not be a switch in /etc/nsswitch.conf for the automounter? There isn't one on either the container or the host, but I would have thought there should be? I tried adding it to no avail, too.)

Any pointers greatly appreciated.
Thanks.
Eric

---

### Post by TheFu on 2017-12-28
A few things.
a) 17.04 support ends in a few weeks.  I wouldn't do anything troubleshooting where that OS is involved at this point.  IMHO, servers should only run LTS releases without extremely specific reasons.  6 months of support just isn't sufficient for a server, IMHO.
b) NIS isn't secure.  The problems have been well-known for 2+ decades.  We pulled NIS infra from our networks in the late 1990s.

As for getting things go work with NFS, you need to ensure all the ports and services are running everywhere it is needed. rcp, portmapper are often forgotten.  Don't forget to check firewalls and tcp-wrapper configs too.

Do you have this working using normal systems/VMs?  Containers need each necessary port to be forwarded inside, correct?

For more specific help, please post real config files for each part.

---

