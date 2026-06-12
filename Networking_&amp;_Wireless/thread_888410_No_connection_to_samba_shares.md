---
title: "No connection to samba shares"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Malfet on 2008-08-13
Once again I'm facing the same problem.
Just after fresh Ubuntu 8.04 install many people using password protected samba shares were unable to connect to a server. It was working fine as smb://serveradress/sharename, but not as smb://serveradress Finally it was recognized as bug in Nautilus does not ask for a password when connects to a server, while it does when connect to a folder on a server. And here [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072")there is a fix of gvfsd-smb-browse regarding this issue.
Yesterday I had updated system and faced the same problem. Already four mounth after official release the severe bug is not fixed and previous fixed version of gvfsd-smb-browse doesn't work either!
Finally, what to do with it??? I can perfectly connect to any folder, like smb://192.168.0.1/Software, but I can not remember names of all folders on the server and it is all about the smallest problem: gvfs does not ask for the authentification when it connects to the server!
Please, FIX IT!

---

### Post by quill3033 on 2008-08-24
is this a huge security hole whereby someone could be accessing your computer? if so, how do I turn off the process. I just noticed i had gvfsd-smb-browse on and I don't remember ever allowing samba to be up and running. Please forgive me if I'm way off base here. I have very limited understanding of this. But there seem to be a few fishy upload and download figures lately that I'm sure I'm not responsible for and made me wonder if there is a security issue. I have Firestarter on but on very permissive settings.

---

