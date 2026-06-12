---
title: "Need permissions help"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by AndyInNYC on 2010-12-14
I have a 64 bit 10.10 server set up with Samba.  I installed mythTV on the same box and everyone is playing nicely.

The mythtv settings want to record to the boot disk; I'd like the recordings to live on the Samba-shared drive.  I'm having a permissions issue which I don't know how/have the technical skills to solve.

/media/RAID is mounted and shared in Samba.  The owner is 'server'.  My Samba config sets 'force user = server'

I'd like the mythTV recordings to live in /media/RAID/Media/TVShows.

ls -lh returns this for that subdirectory

drwxr-xr-x 2 server server 4.0K 2010-12-13 15:44 TVShows

When I point myth to that directory I get a permissions error.


So (short story long) - What change can I make to allow the mythTV program to write to that directory without messing up everything else on the file-serving side?

Thanks.

Andrew

---

### Post by prat22 on 2010-12-14
use sudo nautilus!;)

---

### Post by AndyInNYC on 2010-12-14
I'm still confused.

The folder is already shared via Samba; 'server' is the owner.
Perhaps if I can make a new group(?) of which server and mythtv/mythtvuser are members and allow that as owner? (I don't even know how groups work, so I'm reaching for straws here)

I'm sure you have an answer for me in your response - I'm just too dense to understand the actions I need to take.

Thanks for your response(s) so far.

Andrew

---

### Post by sohail_linux on 2010-12-14
check out with what permissions ur mythtv is running ? is it running with root permissions ? or any other specific user ? set write permissions to the samba shared directory for that user.
or run mythtv with root , and chown samba share directory for root.

---

### Post by Morbius1 on 2010-12-14
If you have "force user = server" then all remote users that are granted access by samba will look like "server" to linux. So as long as "server" actually owns the target folder you should be good to go.
 Can you post your smb.conf:
```
testparm -s
```

---

### Post by AndyInNYC on 2010-12-14
It looks like sudo chmod 777 -R /media/RAID/Media/TVShows worked.

I'm going to change it to 766 (which removes execute, right?) since I want read/write access for all but owner.

Prior to 777 the frontend wouldn't start and I'd get the permissions error in the backend.log file.  Now the frontend starts.

I hope it still starts with 766.

Thanks for the pointers.

Andrew

---

