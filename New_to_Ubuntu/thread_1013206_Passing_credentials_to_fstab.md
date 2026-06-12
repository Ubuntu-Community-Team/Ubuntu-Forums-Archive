---
title: "Passing credentials to fstab"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by JordyD on 2008-12-16
I want to mount a remote Linux file system. I'm using fstab and know how it's formatted, and normally I would have something like this in fstab:

[FONT=monospace]//my.ip/fileshare  /mnt/fileshare  cifs  user=<username>,pass=<password>,auto,rw  0  0[/FONT]

Now this works dandy, but it makes my username/password a little sensitive.

So I was wondering if anybody could tell me how to get my credentials from another file. Maybe with an option like 'credentials=<filename>'?

Thanks,
Jordy

---

### Post by bodhi.zazen on 2008-12-16
Exactly like that.

credentials=/path/to/filename

use the full path, use any name you wish

Make the file ro by root

In the file put two lines:

username = sambauser[FONT=monospace]
[/FONT]password = sambapass

---

### Post by JordyD on 2008-12-16
> **bodhi.zazen said:**
> Exactly like that.

credentials=/path/to/filename

use the full path, use any name you wish

Make the file ro by root

In the file put two lines:

username = sambauser[FONT=monospace]
[/FONT]password = sambapass

That's what I have:

[FONT=monospace]//my.ip/fileshare  /mnt/fileshare  cifs  rw,credentials=/home/jordy/.cred  0  0[/FONT]

I already checked to see if the mountpoint exists, I know it's the right server, and .cred is in the right format...

Would it have something to do with the filesystem I'm using?

**EDIT:**

The file /home/user/credential was created and is ro by root.
The file contains:

[FONT=monospace]username=user123
password=password[/FONT]

dmesg says:
[FONT=monospace][ 8212.226153]  CIFS VFS: No username specified
[ 8212.226176]  CIFS VFS: cifs_mount failed w/return code = -22[/FONT]

If I take out the credentials option and put in the username,password options this all works fine.

---

### Post by bodhi.zazen on 2008-12-16
I assume you have a typo somewhere.

The only one I can see is

FSTAB : //my.ip/fileshare  /mnt/fileshare  cifs  rw,credentials=/home/jordy/**.cred**  0  0

And later you say 

The file **/home/user/credential** was created and is ro by root.
The file contains:

[FONT=monospace]username=user123
password=password[/FONT]

So ... 

/home/jordy/.cred is not the same as /home/user/credential

---

