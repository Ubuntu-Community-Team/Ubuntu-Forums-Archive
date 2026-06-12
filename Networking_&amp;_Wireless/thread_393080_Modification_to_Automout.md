---
title: "Modification to Automout"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by SarahKH on 2007-03-25
I'm banging my head against a brick wall at the moment (more a brainfart than anything).  I have in the fstab's of the laptops and desktops a line that looks like this:

\\darkstar\media /media/darkstat  smbfs 0 0 

Well not quite that but you get the idea.  Basically, I want to change the automount system so that it's semi-conditional.

So instead of Read fstab > check for nfs/smbfs -> mount  I'd like  Read fstab -> check for nfs/smbfs -> ping server (thus checking for avaliability) -> mount. 

The reason being is that the laptops are often roaming around on other networks and need to mount different file systems; using the "smb://" system in Nautilus isn't quite good enough as I've discovered several programs I use don't really like this.  

Anyone got a quick code snippet I can inject in to the /etc/networks automounter?

---

### Post by Mr. C. on 2007-03-25
Review this thread: 

[http://www.ubuntuforums.org/showthread.php?t=333139&highlight=mrc+mount+script](http://www.ubuntuforums.org/showthread.php?t=333139&highlight=mrc+mount+script)

MrC

---

