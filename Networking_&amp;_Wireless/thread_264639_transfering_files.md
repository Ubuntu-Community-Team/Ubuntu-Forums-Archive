---
title: "transfering files"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by Alev on 2006-09-24
please excuse my total and utter lack of knowledge in the area of connecting two computers together.
Pretty much what I want to do is to be able to transfer files between my ubuntu pc, a windows pc, and an ibook with mac os x.  It'd be great if there were and easy way to do this.  perhaps someone can point me in the right direction.
I thought that making an ftp server might be a good way.  As I hinted above, I don't know exactly how one may work, but I imagine I can turn the ubuntu machine into one while still using it for anything else.  I would only need it running when I want to transfer files.  From reading a bit it seems all I need is a program to do this.  Is one that would be easy to use (remember, I don't need many features) that anyone can recomend?  A GUI would be great too.
If there is another method that seems better than this, I'm all ears.

---

### Post by Rule on 2006-09-25
well if your pcs are connected to a router or hub you can use WinSCP in windows to transfer files from your windows pc to ubuntu or ubuntu to windows. as for the mac I dunno I know OSX has ssh but I don't know if WinSCP will connect to it also but you can try.

[www.winscp.net](www.winscp.net)

:mrgreen:

---

### Post by Iowan on 2006-09-25
Samba seems to be the tool of choice when working between Unix and Windows (dunno about Mac either). Samba looks like a network drive to Windows (could even be mapped as a drive letter), so My Computer would be the GUI.

---

### Post by Alev on 2006-09-25
i'll check out samba.  so the ftp thing seems a bad idea?  not just the two that graciously replied but anyone else also.

---

