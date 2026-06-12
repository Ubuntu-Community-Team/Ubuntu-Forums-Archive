---
title: "add/remove programs gives bizarre network related error"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by kdfox on 2007-10-23
using gutsy.  first attempt at *any* linux use, so be gentle.  installed 7.10.  when i go to add/remove prog.  it says

> The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 

when i click refresh it looks for the packages to update, but each one fails with the following error message, or some variation thereof (which includes the ip address of my router, for some odd reason):

> [http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to 192.168.0.1:8080 (192.168.0.1), connection timed out

help!

---

### Post by SunnyRabbiera on 2007-10-23
you might want to try in a terminal apt-get update.

---

### Post by kdfox on 2007-10-23
how do i do that?

---

### Post by kdfox on 2007-10-23
figured out the apt-get part.  it outputs the following error:
> E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

