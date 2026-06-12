---
title: "prob with sources.list"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by soorajviraat on 2011-06-01
when i open my source.list by the following code
 gksudo gedit /etc/apt/sources.list



i get the following error message but source.list opens in text editor .is there any probs?

(gedit:2604): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2604): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.U51QWV': No such file or directory

(gedit:2604): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by Pand5461 on 2011-06-01
They are not error messages but warnings. recently-used.xbel is the file where names of the last opened files are stored. It is used to show "Places > Recent Documents" list. Those warnings mean that this file for root user is not found. I think it won't cause any trouble.

---

