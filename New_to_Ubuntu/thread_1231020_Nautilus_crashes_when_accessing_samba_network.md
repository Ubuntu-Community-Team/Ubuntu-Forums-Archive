---
title: "Nautilus crashes when accessing samba network"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by monkeylytics on 2009-08-04
Nautilus crashes on me whenever I try to access my samba network through a bookmark. Even if I go to the Ubuntu master menu and go to Places -> Network, it'll crash all of my Nautilus windows. The desktop icons disappear.

For instance, if I start up Nautilus through the command line and then click on an SMB bookmark, this is what happens

foo@foo-desktop:~$ nautilus -q && nautilus --no-desktop
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:5584): WARNING **: Unable to add monitor: Not supported

*[Nautilus window loads up fine despite the errors and warning. However, as soon as I click on a SMB bookmark, I get the following errors.]*


(nautilus:5584): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:5584): WARNING **: Got GFileInfo with NULL name in smb://192.168.1.2/foo/, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:5584): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

My Windows machine can access the Samba server fine (up to date Debian Etch). I'm not sure when my Ubuntu desktop started flaking out like this. It did seem to occur shortly after I went into the Karmic branch to apt-get install a screen-capture app, shutter, and its accompanying packages on my Jaunty setup. But this could just be coincidence though.

Any suggestions on how to resolve this? Doing a full re-install of Jaunty would be a bummer (especially if I still had the same problems...)

---

### Post by Hador on 2009-08-14
I've got the same issue, seems to be a bug in gvfs and it should be fixed in gvfs-1.2.3.
[Look here for more informations.]("http://www.nabble.com/-Bug-50895--nautilus,-NEW:-nautlius-hangs-on-computer---and-network---td23526096.html")
Let's hope it gets in the repositories fast...

---

