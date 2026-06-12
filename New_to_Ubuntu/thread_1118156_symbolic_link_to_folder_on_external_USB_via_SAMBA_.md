---
title: "symbolic link to folder on external USB via SAMBA share"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by benfindlay on 2009-04-06
Ok, apologies if this has already been answered; I did a quick search and could not find anything quite like my situation.

I have several external USB drive connected to my ubuntu server which were previously shared across the network using SAMBA. Rather than share each and every folder/drive connected, I would like to create a single folder on my desktop to share and use symbolic links to create 'short-cuts' in this one folder to the folders spread across several drives. The problem I have is that the symbolic links work across the network to a Windows machine, but Mac OS won't follow them properly. Anyone have any ideas on what I am doing wrong?

Thanks

Ben

---

### Post by benfindlay on 2009-04-07
Following some googling I found a page on this forum that didn't come up using the forum's own search. So for anyone else who has this problem, look [here]("http://ubuntuforums.org/showthread.php?t=1077823").

Adding uni extensions = no to the smb.conf on the server seems to fix it!

---

