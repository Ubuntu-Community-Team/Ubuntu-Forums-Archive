---
title: "Okay, folks.  Got a network question this time."
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Everynameistaken on 2010-03-08
I'm trying to connect to a local Windows network.  When I go to Network -> Windows Network, I can SEE the workgroup I'm trying to join.  A few times, I've even been able to see the individual computers in the workgroup.  But eventually, I always get the error "Unable to mount location.  Failed to retrieve share list from server."

Windows networking is so godawful that I'm sure Linux can't be any harder, but I'm kinda stuck.  If I can see the network and even the computers on, what could the problem be?

---

### Post by kanikilu on 2010-03-08
The last page of [this thread](http://ubuntuforums.org/showthread.php?t=1082148) has some suggestions that seem to work for others with the same problem...

---

### Post by Everynameistaken on 2010-03-08
*smbclient -L WASP* [I]from the ROMULUS computer.

if it asks you for a password, don't enter anything, just hit enter, this is anonymous samba login. if that returns nothing than you have no shares defined for anonymous access. if when it does ask for a password, and you enter the password for that machine, it should show you a list of shares if any are available. good luck

[/I]Wow, that command totally worked.  Uh, just for future reference though, what exactly did I just do that fixed it?

---

