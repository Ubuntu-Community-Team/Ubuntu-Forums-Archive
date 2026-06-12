---
title: "Permissions probelm after connecting to a NAS server"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by casperfelix on 2007-12-04
Don't understand this: I mount my NAS server with this line in the fstab:

//192.168.1.10/blahblah /home/me/blahblah cifs credentials=/root/.blah,uid=1000,gid=1000 0 0

No problem. The mount exists and when I look at it's properties I'm the user. 

I then create a folder in the NAS server folder I have opened - again no problem. However when I look at the properties of the folder I have created it says root is the owner which means I then can't do anything inside that folder.

I have tried numerous different fstab options without going anywhere. I guess it must be a user problem. Help.

---

### Post by Wynyard on 2008-07-01
I have the same problem, it means programs that automatically create folders on the NAS (in my case F-spot) can't write to them.

I would love to know how to change this.

EDIT. I think everyone has moved on from this, but the solution is to add something like this to the fstab

//192.168.1.66/share  /media/share  cifs defaults,noperm,noacliocharset=utf8,auto,rw,credentials=
/root/.nas_credentials,dir_mode=0777,file_mode=0777  0    0

---

