---
title: "Removing a user from admin group to restrict sudo"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by fishbutt2 on 2011-05-23
I was going to ask this but ended up figuring it out

I could not remove my second user account from the admin group with the GUI.  They could still use update, install, apps etc.  The sudo command still worked even though the user appeared to be removed from the group in the interface.

First I changed the primary group

su root
usermod -g <group> <user>

I just used the users group

[http://ubuntuforums.org/showthread.php?t=90511](http://ubuntuforums.org/showthread.php?t=90511)

deluser <user> <group>

now it works fine, not sure if I changed anything else but it should be all set.  If it is messed up I will type in

adduser <user> <group>

---

