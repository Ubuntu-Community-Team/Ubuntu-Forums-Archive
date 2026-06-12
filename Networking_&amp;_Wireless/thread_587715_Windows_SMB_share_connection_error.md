---
title: "Windows SMB share connection error"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by jamiltonio on 2007-10-23
I tried following the mounting suggestions in this thread: [http://ubuntuforums.org/showthread.php?t=280473&highlight=windows+sharing](http://ubuntuforums.org/showthread.php?t=280473&highlight=windows+sharing)

However, I end up with this error.  Others have gotten it as well.  When I click through Nautilus to get to the shares, it asks for an authentication...username, password, domain.  When I try to just go to the IP address in Nautilus, I get the same error.  Are my settings off?  It was working for a while, and all of the sudden stopped.

hamilton@hamilton-laptop:~$ smbclient -L 192.168.2.3 -U%
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.2.3.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.2.3 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[MSHOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        SLURK                SLURK

        Workgroup            Master
        ---------            -------
        MSHOME               SLURK

---

### Post by Blackcomb on 2007-10-23
a question for username, domain & pwd doesn't seem like an error. 

What are you trying to do?
Access shared folders from a Windows box
or also
Share directories from your ubuntu machine over a windows network (you'll need the samba package)

---

### Post by jamiltonio on 2007-10-23
i am trying to access windows box from ubuntu.  i've tried entering every username/password combination i have for my windows machine, including null user, guest, but it still doesn't work.

---

### Post by Yfrwlf on 2007-10-30
> **jamiltonio said:**
> i am trying to access windows box from ubuntu.  i've tried entering every username/password combination i have for my windows machine, including null user, guest, but it still doesn't work.

One thing you could do is turn on simple file sharing in Windows to allow anyone to access your shares there.

---

