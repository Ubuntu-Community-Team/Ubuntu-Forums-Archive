---
title: "CIFS mount perms changed on server"
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by jhetrick62 on 2008-02-17
I am having a problem that I can't seem to solve.  I have a FC5 file server that my family writes to and has for a couple of years. I run Samba on this file server.   I moved their main PC to Ubuntu Gutsy about 2 mos ago.

For user file shares that are mounted underneath each users home directory, I have no issues.  BUT, I also have a music share mounted for everybody under the /mnt/music directory on Gutsy.

I use the following auto-mount statement in fstab:
//192.168.0.48/music	/mnt/music			cifs	rw,users,auto,user=music,password=music1	0 0

( I know it could be more secure, but until it works, this will suffice)

The issue is that you can copy a file to the mount's root directory and the permission will be as expected as I have mask statements for both file and group in the samba definition file on the server.  But when you make a new folder inside of this, the permissions are set to 754 although I specify 774 in the server setup.  This causes the folders to not be group writeable and I need this with multiple users accessing to write to the same folders.

I don't have this problem with my FC6 client.  It works fine.  Permissoins on /mnt and /mnt/music are both 774 so that should not be the issue.

Any help would be appreciated.

Thanks,
Jeff

---

