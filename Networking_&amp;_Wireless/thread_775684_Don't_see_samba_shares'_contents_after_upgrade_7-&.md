---
title: "Don't see samba shares' contents after upgrade 7-&gt;8`"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by mwillems on 2008-04-30
I upgraded a vanilla Samba deksktop from 7.10 to 8.04.

Now I can still see samba machines, but when i look at them they contain no folders or files. Help!  :)

Any ideas?

---

### Post by markofealing on 2008-04-30
Same here!

I can see the Ubuntu shares from Windows and can access then but from Ubuntu I can only see the PCs. When I open the PC to display the shares I get a blank window as if no shares are defined.

All was working well before the upgrade, the only think I can think  of which might have caused problem was choosing tokeep my existing smb.conf file. Had I known that this would bugger up my system then I would have replaced it.

The more I'm using 8.04 the less happy I'm with this release. Yes it's faster, but I would rather have functionality over speed anyday! 

Did you retain your smb.conf file or replace it with the new version on upgrade?

---

### Post by markofealing on 2008-04-30
Okay, just had a thought try this from terminal:

smbclient -L 'computer_name'

where computer_name is the name of the computer you are trying to connect to e.g. athlokxp. Do you get a list of available shares?

I do get a list of share names

---

