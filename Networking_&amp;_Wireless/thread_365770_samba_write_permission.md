---
title: "samba write permission"
date: 2007-02-20
forum: Networking &amp; Wireless
---

### Post by gaillard on 2007-02-20
Hey everyone,

I don't quite understand, I am just using samba to be able to write to an ubuntu drive through windows that I am running in vmware but even though the permissions I believe are correct and the writable tag is set to yes in the smb.conf it still says access denied only when I try to create a file or something in windows. I have the masks in the smb.conf set to 0700

---

### Post by gradedcheese on 2007-02-20
just checking: if/when you made changes to smb.conf, did you restart samba?

sudo /etc/init.d/samba restart

---

### Post by gaillard on 2007-02-20
yes I did

Are these the only places permissions are?

---

### Post by gradedcheese on 2007-02-20
Yeah, that should be it.  However the owner/group for the share on the Linux file system is also important (but usually set correctly).  Check who owns the share directory in question, versus who accesses it.  Post your share config for that share if you don't mind.  That's toward the end of smb.conf and looks like:

[share_name_here]
option=value
option2=value
...etc

---

### Post by gaillard on 2007-02-20
Ok I just figured it out but I am understanding.  The samba user "gaillard" is the same as my ubuntu login.  So why do I HAVE to have the permissions for the share folder set to read write for "Others" and not just owner??

Because thats the only one that works is others...  ? Thanks!

Oh my section looks like 

[Music]
path = /media/Music
read only = no
guest ok = no
create mask = 0700
directory mask = 0700
valid users = gaillard
force user = nobody
force group = nogroup
available = yes
writable = yes
browsable = no
disable netbios = yes

---

### Post by gaillard on 2007-02-20
Actually for some reason when I try to edit the files in foobar2000 in windows it tells me access denied. hm.

---

