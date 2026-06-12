---
title: "AUTOFS not mounting NFS mount"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by SilkBC on 2007-12-11
Hi There,

I am running Kubuntu Gutsy on my desktop.  I have a ClarkConnect box as my mail and file server, and it is setup to export the /home directory via NFS.  I am also using the CC box as a central authentication server using NIS.

I have "autofs" installed on my desktop machine.  When I log in to my desktop machine as a "NIS" user, I get authenticated no problem but the /home directory from my CC box does not mount, and so I do not have a "home" directory.

Here is my /etc/autofs.master file:

--- START ---
/mnt   /etc/autofs.d/auto.home --timeout 600
--- END ---

and here is my /etc/autofs.d/auto.home file:

--- START ---
*       -fstype=nfs,soft,intr,rsize=8192,wsize=8192,nosuid,tcp sbs01:/home:&
--- END ---

I have also tried replacing "sbs01" above (which is my CC box) with the server's IP address but no joy.  I have also confirmed that I can mount the /home directory via NFS manually on the command line as well as from /etc/fstab.  Oh, and yes, I have confirmed that the "automounter" service is indeed running.

Is there anything else I should be looking for?  Something I am missing?

Please let me know if you require any further information in the meantime.

Thanks! :-)

-SilkBC

---

