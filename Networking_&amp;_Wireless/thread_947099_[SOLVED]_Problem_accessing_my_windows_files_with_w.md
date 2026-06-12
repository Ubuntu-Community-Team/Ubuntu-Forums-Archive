---
title: "[SOLVED] Problem accessing my windows files with winshare"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by rockophonic on 2008-10-14
I'm new to ubuntu. I am trying to file share between my ubuntu laptop and windows xp desktop.  I was successful over the weekend filesharing with a macbook, after scratching my head and digging thru the permissions nuances.  However, I'm having a little more difficulty getting to access my windows desktop from my ubuntu laptop.  Let me give the scenerio as clear as I can:

1.) I can see and fully access my ubuntu laptop on my windows machine.
2.) Both my ubuntu and windows machine are in workgroup
3.) My windows machine icon has begun to appear on my ubuntu machine under network servers, but when i try to access it, it fails to open the folder contents and says, "**The folder contents could not be displayed.**
[COLOR="Red"]Sorry, couldn't display all the contents of "Windows shares on workgroup": DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[/COLOR]

Help would be greatly appreciated

---

### Post by superprash2003 on 2008-10-14
always better to use advanced file sharing instead of simple file sharing in windows.To access windows shared folders you could try accessing by typing smb://x.x.x.x where x.x.x.x is the ip of the windows machine
for reference : [http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html](http://prash-babu.blogspot.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by rockophonic on 2008-10-15
Thank you for the help.  It seems to be working fine now.

---

