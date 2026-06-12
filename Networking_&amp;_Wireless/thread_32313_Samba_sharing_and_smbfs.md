---
title: "Samba sharing and smbfs"
date: 2005-05-07
forum: Networking &amp; Wireless
---

### Post by DarkGreen16 on 2005-05-07
I am trying to setup seamless networking with windows computers using the guide on ubuntuguide.org. I have 1 question and 1 problem...

Why do I need smbfs and not just samba?

and my problem

Ok whenever I share a folder using right click > share folder it does not immediately show up in the windows network browser. In fact, the only way I can see it is if i do a \\hostname in which case it will show up in the network browser in the future. However, the other problem I notice is the hostname option nor the domain option has any effect. I changed the domain from mshome to bleh yet it still shows mshome...and i changed the hostname to %h yet it still shows up in windows as

%h ubuntu or whatever the h e double hockey sticks the default is....

anyone know how to fix this and what smbfs is for?

thx in advance...

---

### Post by bonifacio on 2005-05-07
smbfs is used if you want to mount a remote SMB share, not necessarily share yours with others.  With Samba you can define share on your host machine and access other remote machine at the same time.

---

### Post by DarkGreen16 on 2005-05-07
thx any idea how to fix my other problems?

---

