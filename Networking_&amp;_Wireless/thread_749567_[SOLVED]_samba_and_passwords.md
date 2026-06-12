---
title: "[SOLVED] samba and passwords"
date: 2008-04-08
forum: Networking &amp; Wireless
---

### Post by StOoZ on 2008-04-08
Well I finally installed and configured samba.
my host is Ubuntu and the guest (the other computer in the network,which receives the shared folder) is windows 2000 advanced server.
my question is , is it possible to DISABLE the password retyping for entering the shared folder for the first time for each time I restart my computer? (windows)

whenever I restart my computer , and then try to open the shared folder , it required a password, only for once, until I restart again, its annoying

---

### Post by koenn on 2008-04-08
You"d have to set the ntfs security AND the share permissions in WIndows so that anyone ("Everyone") is allowed to read/write that share. 
Not recommended because it allows access without authentication, but that seems to be what you want anyway.

-------
edit : I got it backwards i think, you're share is on ubuntu, with samba ?
there's probably a setting in smb.cng, like security=???, that does the same, but i don't remember it.

---

### Post by Eiríkr on 2008-04-08
Yes, StOoz, your post is a bit confusing.  If you're on Windows, trying to access a share located on Ubuntu, and you're worried about the password dialog, the easiest way around this is to map a network drive to the share, and check the "Reconnect at logon" box.  Then you only have to enter the password once when you map the drive, and then the drive (i.e. share) should be mounted automagically within Windows thereafter.  

Cheers,

Eiríkr

---

### Post by StOoZ on 2008-04-08
the network drive did the job... thanks alot.

and thank you all!!! :guitar:

---

