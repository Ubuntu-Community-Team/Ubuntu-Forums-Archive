---
title: "SSH/SFTP Nautilus end up stuck in home directory"
date: 2018-07-13
forum: Networking &amp; Wireless
---

### Post by aaronp on 2018-07-13
Hi guys,

I'm running Ubuntu 18.04 and experience an issue when I connect to a remote server using SSH via Nautilus (Other Locations, then ssh://server-name-or-ip).

When I first create the connection it opens up to the server's root (i.e. / ) which I can then use to navigate to any folder in the system.
If I close that Nautilus window and then re-open the mount point it created, it then opens inside the remote user's home directory with no way to go up any levels - so I'm jailed to the home directory or below.

I have tried this on many different remote servers that I connect to and the behaviour is the same across all of them, which leads me to believe it's an issue in my local SSH or Nautilus and not the config on the server.

Has anyone else experienced this and is there a fix or workaround?

Thanks
Aaron

---

### Post by Morbius1 on 2018-07-13
Consider this a bump because I don't have an explanation but ...
> When I first create the connection it opens up to the server's root  (i.e. / ) which I can then use to navigate to any folder in the system.
If I close that Nautilus window and then [COLOR=#0000cd]**re-open the mount point it  created**[/COLOR], it then opens inside the remote user's home directory with no  way to go up any levels - so I'm jailed to the home directory or below.
I can confirm that symptom [COLOR=#0000cd]**if by mount point you mean the mount link on the side panel of nautilus**[/COLOR].

But if I go to the actual mount point in Nautilus ( /run/user/1000/gvfs/sftp:host=server) it does list the entire entire contents of the server.

Not sure if this is a Nautilus issue or a gvfs / gio issue.

Until someone figures this out I would suggest going to /run/user/1000/gvfs and bookmarking that location - it will show up as gvfs on the side panel. Your ssh mount point will appear under it.

[COLOR=#0000cd]**EDIT**[/COLOR]: I just tried this in Xubuntu 18.04 which uses Thunar not Nautilus and it works as expected. If I connect then close and reopen Thunar then click on the shortcut it brings me back to the whole fileystem. Both of them are using the same gvfs / gio so it looks like a Nautilus thing to me.

---

### Post by #&amp;thj^% on 2018-07-13
> **Morbius1 said:**
> so it looks like a Nautilus thing to me.
+1>>>Same Here.

---

### Post by aaronp on 2018-07-13
Thanks guys! I'll raise a bug.

---

