---
title: "robocopy from Win7 -&gt; Ubuntu extremely slow"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by dbone on 2014-11-21
Using robocopy on my Win7 laptop with a mapped SMB drive running the latest version of Ubuntu Server. The file transfers are quick but the delta checking portion crawls along. Any ideas?

smb.conf
[storage]
path = /media/Data
available = yes
valid users = user
read only = no
browseable = yes
public = yes
writable = yes

Here is my robocopy command:
robocopy D:\ S:\ /MIR /W:1 /R:2

---

### Post by weatherman2 on 2014-11-21
Is the copy equally slow when you do it just by drag-and-drop instead of using robocopy?

How about if you try copying from another Ubuntu client to the SMB share?  (if you don't have another Ubuntu client, boot a live USB on the Windows 7 machine and use that as a temporary Ubuntu client.)

You might also try enabling SSH on the server and see if copy speed is about the same or faster when you use filezilla or winscp to do the file copy to the Ubuntu server.

---

### Post by dbone on 2014-11-21
Copying from explorer to the smb share is fast (11 mb/s on 10/100 nic). Same with deleting directly on the smb share, fast.

Checked perfmon on the Win7 laptop and the drive is almost idle even during the robocopy process. It just runs very slowly. Disabled the wireless adapter on the laptop and went eth to eth with same result.

Not sure what else to try and not even sure if a NAS device will be any better.

---

### Post by weatherman2 on 2014-11-22
The issue is probably with Robocopy if Windows explorer is fast.  You'll probably get better help from an MS forum.

I prefer rsync FYI - works in both Linux and Windows, though you do have to install it in Windows.

---

