---
title: "How do I find shared directories on my network?"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by litlfrog on 2009-03-19
I've got xubuntu installed on one computer on the network and have no idea how to find directories that have been shared on other computers on the network. I've installed samba and fusesmb and have gone through steps to allow Thunar to browse network shares. But how do I find those shares on the network now?

---

### Post by MrWES on 2009-03-19
> **litlfrog said:**
> I've got xubuntu installed on one computer on the network and have no idea how to find directories that have been shared on other computers on the network. I've installed samba and fusesmb and have gone through steps to allow Thunar to browse network shares. But how do I find those shares on the network now?

Open nautilus (ubuntu file manager) and goto File | Connect To Server. Choose Windows Share from the drop down list and enter the IP of the computer you are trying to connect to. You can bookmark it and it will always be available in the Nautilus bookmark.

Bill

---

### Post by kidux on 2009-03-19
> **MrWES said:**
> Open nautilus (ubuntu file manager) and goto File | Connect To Server. Choose Windows Share from the drop down list and enter the IP of the computer you are trying to connect to. You can bookmark it and it will always be available in the Nautilus bookmark.

Bill
Nautilus is Gnome, Thunar is XFCE.

---

### Post by OffAxis on 2009-03-19
From the main thread on the subject here:
[http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba](http://ubuntuforums.org/showthread.php?t=304131&highlight=xfce+samba)


> Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

9) Logout and log back in (So the user privilege and fusesmb autostart will take affect)

---

### Post by MrWES on 2009-03-19
> **kidux said:**
> Nautilus is Gnome, Thunar is XFCE.


Duh -- that particular part slipped by me :)

---

### Post by doas777 on 2009-03-19
from the CLI you could use```
smbclient -L \\<server>
```

---

### Post by litlfrog on 2009-03-19
OK, I restarted the computer, but nothing is in the mountpoint directory I created. I should point out, the shared folder I'm looking for right now is NOT a Windows folder, it's on a different Ubuntu machine on the same network. Is there not a way to just, you know . . . browse the network? That seems really bizarre.

---

### Post by cariboo on 2009-03-19
Have you got the folder on the Ubuntu computer setup for sharing?

Jim

---

### Post by litlfrog on 2009-03-21
Yes, the folder is setup for sharing. Other computers on the network are seeing it fine.

---

### Post by litlfrog on 2009-03-22
When I try to run the command given above, I get

> globalnet@globalnet-desktop2:~$ smbclient -L \\192.168.1.35
Enter globalnet's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.2.3]
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
tree connect failed: SUCCESS - 0
globalnet@globalnet-desktop2:~$ 


---

### Post by gn2 on 2009-03-22
Have a look at the link in my sig, Network Browsing with Thunar, all is explained.

Another simpler way is to install and use Dolphin.

---

