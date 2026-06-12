---
title: "Hardy Upgrade and NFS somewhat broken"
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by dagar on 2008-06-18
I did a gutsy to hardy upgrade yesterday and most everything went well except NFS.  I have an IBM iSeries that is setup as an NFS server.  There are certain folders that have the read/write permissions on them.  It was working fine in gutsy where on my Ubuntu box I made a NFS group with GID of 9000 that corresponded to a group setup on the NFS server with the same GID.  I upgrade to Hardy and I can still connect to all the non secure folders, but not to the secured folders.  
How can I debug what is being passed to the server for my GID?  How has the nfs client implementation changed in Hardy?
Any ideas?
Thanks
Derek

---

### Post by dagar on 2008-06-19
After doing some digging on NFS, I found that there is a 16 group limit prior to NFSv4.  I removed myself from some groups that I would not need like floppy and tape.  Now all is good.

---

