---
title: "Simple, easy file sharing?"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by Nixie Pixel on 2008-11-28
I've been struggling and struggling with trying to get a very basic share working properly through Samba.  It isn't working.

What I want is the Linux equivalent of the very easy Windows share:  Right-click on a folder/directory, choose file sharing, and enable it for all users.  Bam, done!  I can now access that share across the network (assuming my network is set up correctly).

Does this not exist in Linux/Ubuntu?  I am running Intrepid, and I just want to open up a folder for any user on my home network to view, edit, modify files in it or in its subdirectories, without messing with permissions and groups and users and so on...just open it up to all.  Am I missing something simple somewhere that would enable me to do this without any hassles?

Thanks!

~Nix

---

### Post by andrew.mckevitt on 2008-11-28
I'm using hardy and it's a matter of just right click and selecting sharing options, have they changed that in intrepid?
Although I did have to open nautilus as 'root' for it to work properly.

```
gksu nautilus
```

Once your on the sharing options, it's just a matter of ticking the boxes.

---

### Post by Nixie Pixel on 2008-11-28
I did tick the boxes.  I can connect to the share, but I can't create/move/edit files, only read them.

---

### Post by superprash2003 on 2008-11-28
ensure that you uncheck " Read only " and restart samba after that sudo /etc/init.d/samba restart

---

### Post by Nixie Pixel on 2008-11-28
I had done that, and restarted the whole server since, still no change...

---

### Post by superprash2003 on 2008-11-29
in that case its got to do with permissions.. right click on the folder and click on properties and what do you see under permissions?? a screenshot would help

---

### Post by Nixie Pixel on 2008-12-01
Ok, I decided to try it from the beginning, to avoid any problems I might have caused along the way.

I simply right-clicked on the directory I wanted to share, chose to share it and gave it a share name, and chose to allow others to write in the shared folders, and the following error message appeared:

"'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. Invalid parameter."

Perhaps this has something to do with why my network share couldn't be seen?  I looked up this error message and it seems to have something to do with setting passwords for new users?  But I don't want or need to do that, I just want the network share accessable by every person on the network, without user authentication.

Thanks!

~Nix

---

### Post by Iowan on 2008-12-01
It's possible the **security = share** option might be what you're looking for, but you may still need to enable a default user.

---

