---
title: "No printing, no loopback, looooong logon"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by yves on 2006-11-11
This might be usefull to somebody else...
I've learned the "hard way" that there is a right way to move /var on a new partition and a wrong way !!

When I installed 6.06 the first time, everything went into the same disk partition under /.

I ran out of space, so I moved /home. Ran out of space again, so I decided to move /var on it's own too !.

What I did :
[LIST=1]
[*]boot livecd
[*]mounted my disk to access my /
[*]lunch gparted to create a new partition for /var
[*]copied my "old" /var to my new partition !! don't do this ](*,) 
[*]erased my "old" /var
[/LIST]

And then my problems started !! 

It took many minutes to logon in graphical mode !  Printer was not working at all !  After looking aroung I found out that my loopback device (ifconfig lo) was not UP !!  So for a while, before logging on in graphical mode, I logged on in a terminal (CRTL-ATL-F1) and typed > sudo ifconfig lo up and after that > sudo cupsd to enable the printing.

The other symptom I found out was that the > varrun tmpfs was also missing from the result of df -h while varlock was there !! 

I did not grab the whole thing, but I found out that  you really need only two directories under /var to start with : lock and run !  Just make sure you create them with the right permission.

Everything went smooth afterward !  Loopback was coming up at boot time and so cupsd !

---

