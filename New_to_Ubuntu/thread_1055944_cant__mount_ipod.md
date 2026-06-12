---
title: "cant  mount ipod"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-31
hi all,
i set up amarok so i could use my ipod 30Gig colour  and it would mount.  when i configured it on amarok again recently (clean reinstall in 64bit 8.10) i think i made an error somewhere.  now when i plug in my pod  get the following
> Cannot mount volume'
unable to mount the volume 'NIGEL'S IPOD'
(details)mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

what then pops up is 
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 amarok doesnt seem to offer a way of correcting or reconfiguring and frankly i am at a loss asto what to do next.  i have searched the forum and cant find any other threads that quite fit this case.
can anybody help please?
thanks in advance
cheers
nigel

---

### Post by mc4man on 2009-01-31
Try running  in the terminal ```
gconf-editor
```
Scroll down to system and see if there are any individual listings under drives and or volumes.
If so highlight each one and look at what shows up in right side box for mount_point.

If there is one for the ipod it will be obvious, anything other than NIGEL'S IPOD would need to be edited out. (r. click edit to edit or unset to remove

---

### Post by capnthommo on 2009-01-31
hi mc4man
cheers, spot-on - that has sorted it, i can now mount and unmount.
thanks a lot for that
nigel

---

### Post by Jynxx on 2009-01-31
Another great program you may want to try is gtkpod. I use it with my iPod and it works great. It allows me to add music/movies to my ipod and extract them as well. Its simple to setup and is a powerful little program.

---

### Post by capnthommo on 2009-01-31
hi jynxx
yes i just installed that and will check it out, now i have solved the original problem.
cheers
nigel

---

### Post by Jynxx on 2009-01-31
Good to hear, have fun with it!

---

### Post by tarek89 on 2011-04-04
am having the same problem and i dont know how to solve it!! 
i dont understand what exactly to do with gconf-editor
can you explain more!
thank you

---

