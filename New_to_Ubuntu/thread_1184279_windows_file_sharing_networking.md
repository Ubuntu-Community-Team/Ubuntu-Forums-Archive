---
title: "windows file sharing networking"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by wenhui100 on 2009-06-11
Hi people,
          how do i share and view windows xp files shared by windows xp users? i have tried all the smb.config files. Can anyone give or post their smb.config that just work ... no security ... share basic file sharing ...

thanks ..

---

### Post by nandemonai on 2009-06-11
View XP shares from Ubuntu you mean? Places -> Network

If you're looking for a more permanent solution perhaps mounting them manually would be the way to go.

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)

---

### Post by swerdna on 2009-06-11
[global]
workgroup = NAME_OF_WORKGROUP
netbios name = name_of_this_workstation
name resolve order = bcast host lmhosts wins
server string = ""
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
load printers = yes
use client driver = yes
map to guest = Bad User
local master = yes
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

[printers]
comment = All Printers
path = /var/spool/samba
printable = Yes
create mask = 0700
browseable = No
guest ok = Yes

[print$]
path = /var/lib/samba/printers
browseable = yes
read only = yes
guest ok = no

[UbuShare]
path = /home/anthony/UbuShare
read only = no
guest ok = yes
force user = anthony

The [global] stanza is all you need to view and share windows stuff.

The next two allow you to share your attached printers from Ubuntu


The last allows the user anthony to share the directory UbuShare to windows guests

---

### Post by superprash2003 on 2009-06-11
you dont need the samba server installed if you only want to view shares.. if you are having trouble viewing windows shares , you could try this [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by powel212 on 2009-06-11
I had some trouble with this when I first started with Linux.

In Ubuntu the easy way to share files is to right click a folder in your home directory, selct share, hit aply. Your system will then tell you that Sharing services is not installed and ask you if you want to install it now. Accept install now. Wait. When it's done log out and back in again an then right click the same folder and enable sharing with read and write permissions and you are done.

Hope that helps.

Powel

---

### Post by wenhui100 on 2009-06-11
Hi linux experts,
                Thanks for all ur brilliant advices ... i didn't there are more than one way to access the windows share folders using ubuntu.. I will try all of them and post feedbacks 

thanks people

---

### Post by wenhui100 on 2009-06-12
Hi people all your solutions works great ... they all worked ... Thanks you so much ...

---

