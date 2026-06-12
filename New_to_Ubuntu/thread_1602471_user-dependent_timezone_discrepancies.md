---
title: "user-dependent timezone discrepancies"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by jamzen on 2010-10-21
The 'date' command prints UTC time, unless I'm logged in as root, when it
prints EDT time as is proper for my location in Boston.

See the two screenshots appended.  One of them is running as 'root', the other as use 'lfs'.

This is happening on a VBox machine running 10.04 server, and just started
this morning.  Driving me nuts.

The host machine is running 10.04 desktop, and behaves properly.

I've attempted
[INDENT]debconf-show tzdata[/INDENT], and
[INDENT]dpkg-reconfigure tzdata[/INDENT]
as was recommended here and there in the google listings

I've rummaged through all of the bash setup scripts I could find, in /etc and in the user 'lfs' home directory.  I can't find anything that would account for the discrepancy.

I've compared the executing environments for 'lfs' and 'root' and don't see anything either.

Anybody got any suggestions?

P.S. Not a noob: been using ubuntu since 5.04, other distros since 1995.  But this is my first attempt to post on the forums, and this is the first forum available.

---

