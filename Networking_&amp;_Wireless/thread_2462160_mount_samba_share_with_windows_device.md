---
title: "mount samba share with windows device"
date: 2021-05-15
forum: Networking &amp; Wireless
---

### Post by loki6666 on 2021-05-15
[LEFT] sorry for my bad English[/LEFT] [LEFT] 
 [/LEFT] [LEFT] Hello everyone I installed Lubuntu, and I used and configured samba exactly as I had done with Ubuntu.[/LEFT] [LEFT] 
 [/LEFT] [LEFT] On the windows pc I shared the Desktop and an internal hard drive "D".[/LEFT] [LEFT] 
 [/LEFT] [LEFT] The desktop is mounted correctly, for the D disk it gives me the error:[/LEFT] [LEFT] 
 [/LEFT] [LEFT] mount error(13): Permission denied Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)[/LEFT] [LEFT] 
 [/LEFT] [LEFT] the lines added to the fstab file are:[/LEFT] [LEFT] 
 [/LEFT] [LEFT] //PC-xxxx-xxxx/Desktop /media/Desktop-win/ cifs vers=2.0,credentials=/home/xxxxx/.smbcredentials,iocharset=utf8,gid=1001,uid=1000,file_mode=0777,dir_mode=0777 0 0[/LEFT] [LEFT] 
 [/LEFT] [LEFT] //PC-xxxx-xxxx/D /media/HDdiscoD/ cifs vers=2.0,credentials=/home/xxxxx/.smbcredentials,iocharset=utf8,gid=1001,uid=1000,file_mode=0777,dir_mode=0777 0 0[/LEFT] [LEFT] 
 [/LEFT] [LEFT] Why does Desktop have no problems but the disk does? thanks[/LEFT]

---

