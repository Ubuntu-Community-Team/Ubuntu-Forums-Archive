---
title: "Mounting via smbfs unreliable, but &quot;Connect to server&quot; works??"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by registering on 2007-12-05
I cannot get a NAS share to mount reliably via smbfs mounting (it often disconnects at random times), however when I "Connect to Server" via "Places", it seems to work fine. My setup in fstab is below. The reason I can't use "Connect to Server" is Firefox and other apps can't see the icon on my desktop to save files to, however mounting to /media/NAS shows-up and is visible to all 3rd party apps. Any ideas how to mount via smbfs reliably, or how to make the "Connect to Server" icon visible to other apps? TIA!

> 

from fstab:

//192.168.0.101/share  /media/NAS      smbfs   credentials=/root/.smbcredentials,file_mode=0777,dir_mode=0777  0 0

$ ls -l /root/.smbcredentials 
-rwx------ 1 root root 32 2007-12-05 21:31 /root/.smbcredentials

$ sudo cat /root/.smbcredentials 
username=correctusername
password=correctpassword



---

