---
title: "Sharing Folders"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by parmstrong on 2007-10-22
I just installed Ubuntu for the first time last week, 7.10.  I am trying to find the best Linux OS so I can DUMP Windows.  Everything looks great so far except I am having trouble with network sharing...I want to connect to my Windows PC via router to transfer some stuff.  When I go to System>Admin>Shared Folders in 7.10 I get "Sharing Services are not installed, you need to install..."  "Install Unix networks..." and "Install Windows Networks (SMB)"... are both checked, I click Install Services to proceed, it thinks for a few seconds, then comes right back to the same message.   I can't get past this point.  I am new to Linux/Ubuntu so I'm sure it's something stupid I am forgetting.  Can anyone offer advice?  Thanks!

---

### Post by froy02 on 2007-10-22
Open synapics package manager and checked if if the following are installed:
samba
samba-common

If they are installed they should have a green block before their names.

I hope that helps you.
Note: Synaptics package manager is the graphical installer of drivers, plugins, libraries, and software for Ubuntu.

---

### Post by Robert507 on 2007-10-22
I had the exact same problem. What I did to solve it:
Go to applications-->add and remove
search for 'samba'
install that
I am also a new user and can't really tell how this action is different from the other suggestions for this problem but it worked for me (the other suggestions didn't). Good luck

---

