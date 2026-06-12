---
title: "ubuntu server and btsync"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by gljones on 2014-02-09
I have proudly set up ubuntu server and everything works fine. I use samba to share files, I have the main file called public and below are my settings.
[Llyr's files]
comment = Llyr files
path = /files/public
browseable =yes
read only = no

I have btsync installed on the server and it works, it syncs my documents from dropbox and my songs from the laptos in files under public.
But when it comes to editing, deleting and creating filed in the sync files under public i get the following error "permission denied".
I have full access on btsync rather than read only, I have samba accounts.
What could be the reason, this permission problem only happens through btsync, does btsync change the permissions?
is my settings above sufficient?

---

### Post by gljones on 2014-05-30
Hello my self, since no one else answered I'll answer my self. You need to change the owner ship of the synced files using the  following command, chown user:user /location.
Its nice to know you have a forum so ready to help you.

---

### Post by mcvries on 2014-09-10
you could also try to set the umask to 000 in de advanced configure (sudo dpkg-reconfigure btsync) This will set al files coming through btsync read write for everybody. (I know miight impose risks, but i think OP will be able to determine if this is important for his setup)

---

