---
title: "Turning a Folder into an FTP"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by jdelasalas on 2007-06-27
How can I share one folder full of stuff?  I just want to use this folder so we can all collaborate on a project.

---

### Post by Laurel Raven on 2007-06-27
Sounds to me like you aren't really looking for FTP so much as just a shared folder.  In Ubuntu/GNOME, it is controlled under System->Shared Folders (not sure off the top of my head if that is in Applications or the main system tab...I think the latter, but I'm running a KDE session right now, but it should be easy to find).

There, you just give it your password, the first field will be to define the path, the second one is where you decide if you want it shared through Samba (use if Windows machines will want to access it) or NFS (usually a UNIX/Linux only share).  The next thing you will define will be the name of the share, and will be accessed on the local network as \\[MACHINE_NAME]\[SHARE_NAME].  Uncheck "Read Only" if you want someone else to be able to place files on the share.

If you are running Ubuntu/KDE (Kubuntu), then from the K-Menu, select System Settings and then open Sharing.  You will have to access the Administrator Functions to create or edit shares.  From here, you can select Simple or Advanced sharing.  Simple will probably be fine.  From here, you click Add, then you select what folder you want shared.  Then you will be able to select if you want it to share through Samba, NFS, or both, and the share name for Samba.

I hope that helps!

---

### Post by p_quarles on 2007-06-27
Of course, that won't work if the poster is trying to share a folder over the internet. If that's the case, make sure you use a secure ftp server (there are several available in the repositories), and make sure the security settings have all default passwords and anonymous access turned off. 

You might also install Webmin on the machine you want to run it from; that will give you some helpful server administration tools if you don't have a lot of experience with this. 

You'll also need to configure any routers and/or gateways you're using to allow this kind of traffic.

---

