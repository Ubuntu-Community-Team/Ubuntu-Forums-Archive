---
title: "Samba Will Not Print"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by nighthawk98tj on 2007-12-04
Hi there,

I am having an issue with samba on my ubuntu box (actually, mythbuntu...) where I am trying to print from an Ubuntu box to that box running samba.  I am using samba for the printer sharing as I am going to be printing from Windows boxes, too, and would prefer to use Samba with everything.

I am able to see and add the printer on the Ubuntu client box, but when I print to it, nothing happens and it just sits in the print queue on the client.  I have scoured the web and have been unable to find a good answer to this issue.  Does anyone have a suggestion on getting this going?

Here is my smb.conf file:

```
[global]
workgroup = WORKGROUP
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share
printcap name = cups
load printers = yes
printing = cups
printer admin = root, tim, @administrators

[recordings]
comment = TV Recordings
path = /var/lib/mythtv/recordings
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[videos]
comment = Videos
path = /var/lib/mythtv/videos
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv
[music]
comment = Music
path = /var/lib/mythtv/music
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[pictures]
comment = Pictures
path = /var/lib/mythtv/pictures
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[printers]
comment = All Printers
path = /var/spool/samba
printable = yes
read only = true
use client driver = yes
```

Any suggestions are much appreciated!

Thanks,

Tim

---

### Post by nighthawk98tj on 2007-12-04
OK- I fixed this problem by adding a user to samba, which I forgot to do.

Now the problem I have is that when I print something, it prints half of the page correct and the rest is all garbled and smashed into about an inch worth of vertical space... any idea why I would be getting this corrupted output?

Thanks!

Tim

---

### Post by nighthawk98tj on 2007-12-04
Nevemrind... problem solved!  The paper size was wrong by default.

Thanks!

Tim

---

### Post by DasCrushinator on 2007-12-09
> **nighthawk98tj said:**
> Nevemrind... problem solved!  The paper size was wrong by default.

Thanks!

Tim

Could you elaborate?  What release/version of Ubuntu are you using?  How did you add the user?

Thanks!

---

