---
title: "Problems with connect to server"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by canine9 on 2010-02-16
Hey, I'm having an issue with Connect to server. Every time i connect to a remote file(samba) share it opens up then closes suddenly and then clears my desktop icons so that the desktop is left blank but the background image is still visible. I'm using Ubuntu 9.04 Jaunty. Why is this happening and is there a way to fix it?

---

### Post by Peter09 on 2010-02-16
It sounds like nautilus is crashing. As a test open a terminal and then do your normal connect activity. After the crash type into the terminal
> nautilus
and see if your normal desktop returns.
 
Nautilus has been known to crash when trying to deal with unknown or corrupt files. Check the taget directory for anything strange.

---

### Post by aeiah on 2010-02-16
once you launch nautilus from the terminal, if it crashes again you may be able to gleam useful information that outputs into the terminal. you could paste it here or use it for google searches

---

### Post by canine9 on 2010-02-17
I tried doing that and this is what i got from stderr:
> 
** (nautilus:28745): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:28745): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:28745): WARNING **: Got GFileInfo with NULL name in smb://kenene@192.168.5.5/storage4/, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:28745): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault


And i don't think there's something wrong with my share configurations since trying to login with sftp precipitates the same situtation:
> 
** (nautilus:29163): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:29163): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:29163): WARNING **: Got GFileInfo with NULL name in sftp://kenene@192.168.5.5/S4/students, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:29163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:29163): GLib-GIO-CRITICAL **: g_file_info_get_name: assertion `G_IS_FILE_INFO (info)' failed

** (nautilus:29163): WARNING **: Got GFileInfo with NULL name in sftp://kenene@192.168.5.5/, ignoring. This shouldn't happen unless the gvfs backend is broken.


(nautilus:29163): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault


---

### Post by superprash2003 on 2010-02-17
it mostly a nautilus bug , alternatively you could do this [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by kavoura on 2010-02-26
From what I read elsewhere, the problem seems to be with libglib upgrading to 2.22 from 2.20, which causes the bug in Nautilus.

To revert to 2.20 I found this helpful

sudo aptitude install libglib2.0-0=2.20.1-0ubuntu2.1

---

