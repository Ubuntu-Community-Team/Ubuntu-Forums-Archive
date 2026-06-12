---
title: "Can't Register Computername/Hostname on network"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by ltkenbo on 2008-02-11
Me and my friend are running an ubuntu machine connected to the residential network here at school. For some reason I can not figure out how to get the host name registered. You can reach the computer by IP but not by computername/hostname. I had to reinstall ubuntu and before I reinstalled it the hostname was working but another guy helped us do it and I'm not sure how he did it. And don't link me to either of these:
[http://ubuntuforums.org/showthread.php?t=156092](http://ubuntuforums.org/showthread.php?t=156092)
[http://ubuntuforums.org/showthread.php?t=122002](http://ubuntuforums.org/showthread.php?t=122002)

cause I already read them and tried some of that stuff and it doesn't work. I didn't do the hosts thing because that has to replicated one very computer which isn't practical because we're running a LAN webserver for people in the dorms. Anyways, any help would be greatly appreciated.

---

### Post by swerdna on 2008-02-11
Probably the netbios names aren't properly defined in the samba configuration file. So copy that to your desktop, open it in a text editor, copy it and paste it onto a forum reply. I'll tell  you what's missing then.

You can make the copy on your desktop with this command in a terminal:
**cp /etc/samba/smb.conf /home/yourname/Desktop/smb.txt**
in that command replace 'yourname' with your user name

Swerdna

---

### Post by ltkenbo on 2008-02-11
I don't have to copy it to my desktop I can just use vi and edit it right in /etc/samba/smb.conf. Anyways, I have edited that file already and changed some of the stuff but I'll post what the file looks like.

---

