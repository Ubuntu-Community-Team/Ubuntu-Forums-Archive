---
title: "pyNeighborhood: &quot;Scanning host XXX... failed&quot;"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by Hatta0 on 2008-09-06
I am trying to mount a samba share through pyNeighborhood.  I right click on "groups" and select "Scan" it tells me "failed to scan groups.
I right click on groups and select "scan using msbrowse" and it finds my workgroups and the computers in them.

Now, one of my computers, a Ubuntu machine is in workgroup WORKGROUP.  I cannot scan this workgroup, I cannot scan the computer I can not see the shares inside.  pyNeighborhood tells me "Scanning host XXX... failed"

Another one of my computers, a debian machine is in workgroup FACS.  I can scan this machine and see its shares just fine. I can connect to them no problem.

I don't know what the deal is here, the Ubuntu machine has been configured with the GUI tools, and guest access is enabled.  So I should be able to connect just fine.  In fact, I can connect to the Ubuntu machine from the debian machine with smb4k, so the share is set up just fine.

So there's something wrong with pyNeighborhood on this computer.  How do I get more information to figure this out?

---

### Post by gregphil on 2008-09-08
Not sure you can fix it.  There are long standing bugs in ubuntu (like 224351 & 207072).  Basically some part of ubuntu fails to fetch the available shares list correctly (but can connect if given the full share name to connect too).

This may be related to the availibility of an enabled guest (anonymous) account on the remote machine.  If the anonymous account exists and allows an initial anonymous connection, it might be that the local application (gnome?) does not feel it needs to use a username/password authorization for any future connections to that machine (which my be a false assumption).

You could look into what sharing protocols each remote machine is supporting, and check on the guest/anonymous acount status.

Good Luck.

---

