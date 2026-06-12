---
title: "Reset / remove Samba share permissions?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by aquascrotum on 2010-01-12
I have 2 drives shared via samba - I want to remove the share.

Nautilus doesnt show the folders as being shared for some reason, so I cant simply go into Nautilus "Sharing Options" and untick the shared box.  I know the files are still beng shared though as I can view them in my network places and on a windows machine in my network.

Any ideas?  Cheers

---

### Post by Morbius1 on 2010-01-12
If you have a share named "documents" you can open a Terminal and type:

**net usershare delete documents**

[COLOR=Blue]EDIT: That deletes the share not the documents folder. Probably should have said that somewhere 
[/COLOR] 
The other way is to go back in nautilus, share it again, and then unshare it. I know that doesn't make any sense but there's a bug in nautilus where it forgets to add a "share" icon to the share folder after a reboot or logoff.

---

### Post by Gone fishing on 2010-01-12
Edit the samba conf

alt F2 then type gksu gedit /etc/samba/smb.conf

and remove the share. Probably best to make a backup of the original smb.conf first just in case.

---

### Post by Morbius1 on 2010-01-12
> so I cant simply go into Nautilus "Sharing Options" and untick the shared box.

I believe the OP is using nautilus-share not Classic samba so the shares are not defined in smb.conf .

---

### Post by mikewhatever on 2010-01-12
Have you tried to log outand then login? Alternatively, have to tried reloading samba?

---

### Post by Morbius1 on 2010-01-12
There is another possibility. You have shares defined using both methods - Classic and Nautilus. In which case you would need to use both my and Gone fishing's answers. 

You should probably do Gone Fishing's first, then mine.

---

### Post by aquascrotum on 2010-01-12
Thanks for all the replies.  I've no idea there were 2 methods to share and have no idea which I've used - apparently it was a fluke I had shares at all.

I tried 

> The other way is to go back in nautilus, share it again, and then unshare it.

with apparent success.  Cheers!

---

