---
title: "[SOLVED] Same user on home network"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by conphara on 2008-07-02
Hey,

I have this situation at home. I relocated my hard drives so that I could have a clean install of Hardy on one of the big disks.

A potential problem, as I see it, is creating a home network, probably using Samba, and having to accounts/users with the same login name. I have the same account on my desktop and my laptop creating the network but with different names for the machines.

Will there be a problem, as with Windows where it'll complain about two identical accounts (login names) on the same network?

_Desktop_ 
Login name: example
Computername: ubuntu-desktop
OS: Hardy

_Laptop_ 
Login name: example
Computername: ubuntu-laptop
OS: Hardy

Network name: home-network

---

### Post by netztier on 2008-07-02
> **conphara said:**
> 

Will there be a problem, as with Windows where it'll complain about two identical accounts (login names) on the same network?


I've never heard of Windows complaining about identical *user* names on different machines. It actually is a good thing to have, since if Username/PW are the same on all machines, you don't get prompted for a password when accessing a share on another machine: Windows tries with the logged-on user credentials before prompting for username & password.

Having non-unique *host* or computer names is another thing, that's when you'll run into trouble.

> **conphara said:**
> 
_Desktop_ 
Login name: example
Computername: ubuntu-desktop
OS: Hardy

_Laptop_ 
Login name: example
Computername: ubuntu-laptop
OS: Hardy

Network name: home-network

That will work perfectly. I am doing the very same thing on my Ubuntu home network - that has even more hosts than just two.

If you really want to go a step further in the ways of Unix/Linux, make sure that **UID** and **GID** for each user are identical on all machines. When creating a user via GUI, go to **System -> Administration -> Users&Groups**, then look in the **Advanced** tab of the **Add User** dialog; here, you'll find the **User ID** field. It normally is 1001 for the user that's been created during setup. 

Make sure this numbers matches across all your systems for the same username. In large networks with dozens or hundreds of machines, there's NIS, LDAP or even ActiveDirectory servers that'll take care of this, so each user can log on to every machine, always with the same username, UID and GID. Access to NFS shares for instance is based on UIDs and GIDs, not username/password (like with Samba).


regards

Marc

---

### Post by conphara on 2008-07-02
Thank you so much! :)

---

