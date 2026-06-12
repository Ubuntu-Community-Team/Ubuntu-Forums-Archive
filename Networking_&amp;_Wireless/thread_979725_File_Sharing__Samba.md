---
title: "File Sharing / Samba"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by midnitemonty on 2008-11-12
Hello:)  I have been noticing if I say I right click a folder in gnome, and click file sharing.. sharing shows up fine.  If I now go into /etc/samba/smb.conf, there have been no lines added for the file share.  By doing it in the gnome enviroment put sharing somewhere else?  is it not using the standard samba?  If I go ahead and do it manually through Samba, it shows up fine.  I'm trying to kill the shares I made through gnome by right clicking and enableing them, but have no idea where the config is going.  any thoughts?

---

### Post by Iowan on 2008-11-12
Yes, apparently they now go to /var/... (/var/lib/samba/usershares?) I know path was referenced in another thread - I'll try to find it and post back.

---

### Post by kLAcK on 2008-12-04
bump

---

### Post by Iowan on 2008-12-05
[Here]("http://ubuntuforums.org/showthread.php?t=996146") is one link - but not the one I remember...
[Another]("http://ubuntuforums.org/showthread.php?t=833127") link.  Both mention [I]/var/lib/samba/usershares
[/I].

---

