---
title: "Accessing file shares using samba"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by tanveer on 2008-03-17
Dear all,

I recently joined an ubuntu pc with our AD domain and its work fine. Now I need to have some shares from file servers which I can share from GUI using 
Places->Connect to server... ; then select "Windows Share" as Service type and server IP/name and connect. The share then appears at my desktop. But where is the physical existence of that? Because I want to do some aliasing with the files in that share with local files.
FYI, I found the shares are mentioned the %gconf.xml file in the below location under directories named as 1,2,....

/home/domain-name/username/.gconf/desktop/gnome/connected_servers/1/%gconf.xml

Any help.

---

