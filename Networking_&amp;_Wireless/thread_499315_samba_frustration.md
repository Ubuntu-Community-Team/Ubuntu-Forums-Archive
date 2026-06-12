---
title: "samba frustration"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by serfcx on 2007-07-12
Have looked through several threads but cant find solution to this problem

I have 2 machines running Ubuntu and 3 others on the network running Windows.
Machine number 1 running Ubuntu can access all the other shared folders on the network via samba
If I go to places/network servers/windows network/workgroup/ i have a list of all the machines on the network as expected.
If I select machine 1 on this network I see the shared folder Music" which has been set up to be the shared folder on that machine, but when I click on it I get the message that this "folder cannot be found - perhaps it has been deleted"

This is obviously not the case as I can get to it using nautilus.

How can I get samba to recognise this shared folder ?

My samba.conf looks OK

[Music]
path = /home/bill/Music
available = yes
browsable = yes
public = yes
writable = yes

Any ideas as this is really bugging me

---

