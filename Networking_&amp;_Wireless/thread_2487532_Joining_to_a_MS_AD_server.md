---
title: "Joining to a MS AD server"
date: 2023-06-07
forum: Networking &amp; Wireless
---

### Post by bjr23 on 2023-06-07
Really been struggling with this I've watched a LOT of tutorials with some very in depth instructions. Hope I'm finally in the right forum for some advice.

---

### Post by TheFu on 2023-06-08
I've never used AD with linux, but wanted to post so you knew that people saw it.  

MS-AD merges things that are separate in Unix-like systems, but have been available over 30 yrs.  I understood that with Ubuntu Desktop 20.04, integration with MS-AD was added during installation.


Anyway, I searched for "AD ubuntu" and found these posts from Canonical:
[LIST]
[*][https://ubuntu.com/blog/new-active-directory-integration-features-in-ubuntu-22-04-part-1](https://ubuntu.com/blog/new-active-directory-integration-features-in-ubuntu-22-04-part-1)
[*][https://ubuntu.com/blog/new-active-directory-integration-features-in-ubuntu-22-04-part-2-group-policy-objects](https://ubuntu.com/blog/new-active-directory-integration-features-in-ubuntu-22-04-part-2-group-policy-objects)
[*][https://ubuntu.com/server/docs/service-sssd-ad](https://ubuntu.com/server/docs/service-sssd-ad)
[/LIST]

Hopefully, you've already seen those.

<rant>
[B]I find it a bit frustrating that Canonical is trying to support MS-AD instead of having their own LDAP integration across Ubuntu (and other Linuxen) trivially possible first.  
[/B]Every new install of Ubuntu should ask where the LDAP server is, guess multiple OUs (try the normal setup first), and let every installation LAN with 2 or more Ubuntu computers connect to an LDAP server for centralized user/group/home directory management. 

Managing 2 - 50,000 Linux systems isn't really that hard, beyond just the sheer number of systems that might have physical hardware issues.  From an OS/Config standpoint, tools for keeping settings the same across an enterprise have existed longer than I've been using Unix systems.
In the old days, we used local scripts that were kicked off remotely over ssh or rsh (deprecated).  These days, there are a few devops tools (ansible/salt/rexify) that make it pretty easy. If you prefer pain, there's Chef or Puppet - ok, perhaps those last tools have fixed their pain points. Nothing is perfect, even the best options have some complexities.
</rant>

---

