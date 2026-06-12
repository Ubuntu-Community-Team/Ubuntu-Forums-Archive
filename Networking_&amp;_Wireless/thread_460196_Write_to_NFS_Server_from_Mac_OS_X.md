---
title: "Write to NFS Server from Mac OS X"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by maeks84 on 2007-05-31
My */etc/exports*
```
/var/lib/mythtv/        192.168.1.50(hard,rw,sync,no_root_squash,insecure)
```

I can mount the NFS server in the Finder by connecting to *nfs://192.168.1.52/var/lib/mythtv*.  I see all the files and can copy from the server to the mac, but I cannot write to the server from the Finder.  However, if go into the terminal on the mac, I can copy a file to the server with ```
sudo cp /Users/eks/Desktop/asdf.rtf /Volumes/192.168.1.52
```.  Any ideas on how I can copy to the server from the Finder?

A guess is the UID's and GID's need to be changed.  If this is so, how can I find out what I need to change them to?

Thank-you

---

### Post by maeks84 on 2007-06-02
[COLOR="Red"]Bump[/COLOR]

---

### Post by transparent9 on 2007-06-05
Yes, I think you do need to change the UID/GIDs.  I got it to work just by changing the UID, so I don't know if changing the GID is needed.

Here are a couple links that describe how to do it:

[http://www.atmos.washington.edu/~salathe/osx_unix/change_uid.html](http://www.atmos.washington.edu/~salathe/osx_unix/change_uid.html)

[http://www.eecs.umich.edu/dco/help/NFSMac.htm](http://www.eecs.umich.edu/dco/help/NFSMac.htm)

Like I said, I got it to work just by changing the UID in Ubuntu to match my Mac's UID.  

Does anyone know if not changing the GID might lead to problems?

---

### Post by maeks84 on 2007-06-24
Well, I finally got back to this and changed my uid on my mac to match the uid of a user on the Ubuntu computer.  Doing this, however, only allowed me to write to the home folder on Ubuntu.  I suppose I could change my UID on the mac to 0, but I'm afraid this might cause some problems.  I can copy files via the terminal as root, but not via the Finder.  So, with more research I found out how to map UID's and found out that it no longer worked that way.  So I guess I'll have to try a different method of network, unless someone knows how to map the UID's to 0...  It's just frustrating because it is so close to working well, but just not there.

---

