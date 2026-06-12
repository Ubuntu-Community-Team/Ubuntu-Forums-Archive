---
title: "Cannot delete files of Synology Shared Folder (shared thru NFS), pls. help!"
date: 2017-08-08
forum: Networking &amp; Wireless
---

### Post by hhtmp88 on 2017-08-08
Dear all,


* Assumes
# Client PC: ZorinOS12.1 (Zorin-OS-12.1-Core-64.iso, [http://ZorinOS.com](http://ZorinOS.com)), based on Ubuntu16.04 Core, and GNOME Desktop with Nautilus File Manager3.18.5
# NAS Server: Synology Diskstation DS716+II, with DSM 6.1.3-15152 Update 1 and network name "hNAS3"




I have successfully auto-mounted Synology shared folders to my Client PC running ZorinOS12.1 thru "NFS" according to this URL: 
[https://www.ryananddebi.com/2013/01/15/linuxmint-or-ubuntu-how-to-automount-synology-shares](https://www.ryananddebi.com/2013/01/15/linuxmint-or-ubuntu-how-to-automount-synology-shares)




However, it's weired that using ZorinOS's default file manager "Nautilus":
(1) for files under the shared folders, e.g. "folder1", "folder2", & "folder3", I can create or paste new files, change file names, but CANNOT delete any one of them ;
(2) but for the home directory of the Synology user "user1", it's normal




and:
(3) In terminal mode, I CAN delete files in shared folders, e.g. folder1, using the "rm" command, whether or not I am a root user or NOT; but failed to do so in GUI Nautilus File Manager. 


(4) Using Nautilus File Manager, I CAN delete file of home folder of a synology user, e.g. user1, normally.


(5) If I mount synology shared folder thru Nautilus File Manager (it seems that it use "gvfs" to do the mounting), e.g folder1,
-> I CAN delete files under synology shared folder using Nautilus File Explorer
-> However, many other applications, such as Firefox, Google Chrome, NotepadQQ, XnViewMP, CANNOT see the mounted folder directly, and can only see it by browsing into the folder "/run/user/1001/gvfs/smb-share:server=hnas3.local,share=folder1"
-> Although other applications can see this shared folder, but they, e.g. XnViewMP, CANNOT save file into it.




So any suggestions to solve my problem: "Cannot delete files" of shared folder (mounted thru NFS) using Nautilus File Manager?




Thanks for any kinds of help!

---

