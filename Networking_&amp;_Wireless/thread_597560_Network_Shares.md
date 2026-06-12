---
title: "Network Shares"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by Churnd on 2007-10-30
Forgive me if this has been asked before.  I did search!  :)

At work I have a few Ubuntu x86 and x64 Linux machines that we use for data processing.  I need to find a GUI tool that will allow users to mount a network drive without requiring root or sudo access.

I've tried smb4k, which seems to work ok, but I was hoping to find something for Gnome.  Plus, I've noticed that smb4k will actually inherit permissions and ownership from the server.  Example:  we have a Xserve and a Windows server.  smb4k mounts the Windows shares with 777 permissions, whereas it will mount the Xserve shares the default permissions on the server itself along with the server's UID's/GID's which doesn't do me any good because the UID's/GID's on the server are different than on the workstations.  I've actually tried to duplicate them and that works, but I'd rather avoid having to do that if possible.

Let me know if I'm not explaining myself clearly... I have a habit of doing that.  I'd really like to figure this out, because users keep wanting to go back to Windows simply because it's so easy to "Map a network drive".

Thanks,

---

