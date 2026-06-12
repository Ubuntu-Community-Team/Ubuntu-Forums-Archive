---
title: "rename WORKGROUP"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by rated727 on 2008-07-19
I learned something about network naming conventions by working in an environ where naming actually made sense. (examples below)

Older test computers, manufactured by Hewlett-Packard were named for SW Pacific islands - eg. Bali, Tahiti, Palau, etc.

The next generation manufactured by Lucent Technologies (spun-off from HP) and Sun Sparc systems were named for Aleutian islands - eg. Unimak, Seguam, etc.

The ONLY engineer's test/development computer was Alcatraz.

(do you detect a theme?)

--

Currently my Windows installations are named for cartoon characters (Elmer, Bugs, Daffy,) in the (peer) workgroup WERNER
Linux installations are named for cartoon characters (Homer, Bart, Marge) in the (peer) workgroup WORKGROUP (default for Samba/NFS setup)  I want to rename WORKGROUP to SIMPSONS.

NOTE: there are NO servers, only a dedicated firewall computer.

I have viewed smb.conf and found where workgroup=WORKGROUP I assume that I edit this line to rename, but do I need to edit a config file for NFS?  If so, what name and location?

Also, when I view Network (within Ubuntu File Browser) I see the active (turned on) Linux installations and Windows Network.  Open Windows Network and find WARNER and WORKGROUP.  Open WORKGROUP and find the Linux installations (again).  Why this redundency in display of Linux installs?

---

### Post by Ayuthia on 2008-07-19
> **rated727 said:**
> 
I have viewed smb.conf and found where workgroup=WORKGROUP I assume that I edit this line to rename, but do I need to edit a config file for NFS?  If so, what name and location?You should only have to rename WORKGROUP and then restart samba (sudo /etc/init.d/samba restart) and it should change the name for you.  You should not have to do anything for NFS.  It is based on the ip address (host name) instead of a workgroup name.

> Also, when I view Network (within Ubuntu File Browser) I see the active (turned on) Linux installations and Windows Network.  Open Windows Network and find WARNER and WORKGROUP.  Open WORKGROUP and find the Linux installations (again).  Why this redundency in display of Linux installs?This is a guess, but it looks like you are first seeing your NFS mounts in the network then you also have it set up through Samba so you are seeing them again.  I could be completely wrong on this though.

---

