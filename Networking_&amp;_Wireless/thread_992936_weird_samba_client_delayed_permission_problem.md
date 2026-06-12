---
title: "weird samba client delayed permission problem"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by antych on 2008-11-25
I have 2 similar fedora instances runing in OpenVZ where I'm kinda forced to use samba on them. So I map one of directories on my Ubuntu (running latest 8.10) and weird things happen. One works fine, but the other one gives me random permission errors when directories are created. I noticed that the directory is first created a different user (509, group is empty) and then the owner changes to the right one. I noticed that by dragging an empty directory onto mapped drive, the view quickly refreshes and sometime shows me 509 instead of actual user. I can replicate it this way:
$mkdir zzz && touch zzz/xxx
touch: cannot touch `zzz/xxx': Permission denied

$mkdir zzz && sleep 1 && touch zzz/xxx
<-- this works fine, because the owner changed in the meantime.

This happens only on one of the boxes, one runs smbd 3.0.22-1.fc5 and it's fine, the other one causing problems runs smbd 3.0.28-0.fc7. They are configured the same way, I even copied the config across to make sure. Also it works fine if use it drive in nautilus without mounting it ie. I can copy anything to it using smb://location, but if copy it into mounted directory it fails.

Any help greatly appreciated. Thanks.

---

