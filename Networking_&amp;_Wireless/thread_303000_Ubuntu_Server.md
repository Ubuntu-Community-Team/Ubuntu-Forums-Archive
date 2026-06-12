---
title: "Ubuntu Server"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by jimmymac on 2006-11-19
Hi guys,

I'm just about to setup a file/download server and am just looking for a few pointers.

It will be accessed from both windows and linux clients.

I want to create network shares (presumably NFS?)  that are read only to all users and read/write to a few.

I also want to people to get onto to it using a remote desktop of some description (i.e. only the people that have the root password) to configure updates etc.
Obviously some of that can be done via telnet but it would be easier to have a gui interface.

I think that's all I need to do....

All help appreciated!

TIA

Cheers,

Jimmy

---

### Post by Jussi Kukkonen on 2006-11-19
For a windows+unix network, you should probably use samba instead of NFS.

The administrative access is probably best done with SSH. Do not use telnet, that is a security nightmare. SSH allows normal command line access, but you can also start graphical apps if you need to (assuming the client machine runs an X server). Remote desktop is of course also possible, but SSH should really be enough for admin access.


EDIT: by the way, you might want to read about sudo if you don't know about it already (Ubuntu does not have a root password by default).

wiki.ubuntu.com has info and installation instructions on sudo, NFS, samba and SSH. Take a look there.

---

### Post by jimmymac on 2006-11-19
Thanks for that, the NFS wiki looks fairly straight forward.

Didn't see anything on Samba though?

Does ubuntu have a server installation option (i.e. don't install what isn't needed) or is it easier to do a manual install?

Cheers,

Jimmy

---

### Post by Jussi Kukkonen on 2006-11-19
Yes, there's a server install option (doesn't install X by default for example), remember to download the correct CD.

Samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jimmymac on 2006-11-20
Excellent,

Just a quick dumb question...

Can I still start graphical applications if I don't install X?

Cheers,

James

---

