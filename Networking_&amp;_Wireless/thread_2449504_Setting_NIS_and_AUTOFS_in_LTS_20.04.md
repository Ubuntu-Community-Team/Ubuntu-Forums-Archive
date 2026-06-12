---
title: "Setting NIS and AUTOFS in LTS 20.04"
date: 2020-08-28
forum: Networking &amp; Wireless
---

### Post by giovanni24 on 2020-08-28
Dear All,
I am inside my company network and I need to set the NIS domain, the domain search and the autofs services. Up to few months ago I was using OpneSuse and with Yast all these settings were really straightforward. Right now I switched tu ubuntu LTS 20.04 and I am not able to set these service. Anyone could help me how to change the proper files and how to set everything?
Thanks
GB

---

### Post by TheFu on 2020-08-28
NIS and autofs aren't distro specific. They work the same across all, to my knowledge.

If you have a Solaris system, there is NIS+, which is secure. Every OS has free NIS+ clients. Oracle (and Sun before them) retained the NIS+ server code. I'd definitely deploy NIS+ provided the company plans to retain at least 1 or 2 small Solaris servers.

NIS hasn't been secure ... ever ... but we used it inside a company until 1999. Does company security matter? After that, the switch to LDAP directory services was required.  Most Unix/Linux-centric networks would use **FreeIPA** for current deployments rather than NIS.  

Due to local situation, we used LDAP directly for centralized user management and didn't use maps for netgroups, hosts, etc.  I really need to setup a FreeIPA server here. RHEL/CentOS are the primary targets for the server and porting to Debian/Ubuntu too years for the server. Not sure if I'd run the server on any debian-based system.  Would love to hear from people who have.
Google found this: [https://www.server-world.info/en/note?os=Ubuntu_18.04&p=freeipa&f=1](https://www.server-world.info/en/note?os=Ubuntu_18.04&p=freeipa&f=1)  I've not used it and don't know the author or that website at all.

Autofs works fine in 20.04.  I didn't see any differences between 20.04 and prior implementations.  If you post your auto.master and auto.nfs files, I'll happily look them over.  I don't have any 20.04 NFS servers, but connections to 16.04 NFS servers "just work" from 20.04 clients. Can't imagine there would be any specific problems just due to the OS release.

However, 20.04 does push snap packages. Snaps have mandatory constraints that don't work with NFS in many configurations.  That is absolutely critical to understand, test for issues, and have mitigations.  The main issue is that last time I checked, NFS of any sort wasn't supported by snaps and HOME directories were limited to /home/ <--- the snap team HARD CODED THAT VALUE!!!
If you don't use snaps, no problems.  Flatpaks do allow local control for the constraints, which could be a work-around.  Servers don't always need snaps, so your setup may never have any issues.

---

