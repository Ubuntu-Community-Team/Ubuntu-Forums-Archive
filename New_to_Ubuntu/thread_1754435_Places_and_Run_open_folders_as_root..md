---
title: "Places and Run open folders as root."
date: 2011-05-10
forum: New to Ubuntu
---

### Post by BrandonC19 on 2011-05-10
I'm posting this in absolute beginner's talk because it's probably an easy fix and I'm just not thinking straight, as work has me worn down a bit :). About a week or so ago I wiped my hdd and reinstalled Maverick. Everything went well for awhile until the other day when selecting any entry from "Places" or any directory from the "Run" dialog box suddenly appears to open the folder as root. All goes well if I append "Nautilus" before the directory in run (ex. "nautilus ~/Pictures") but simply typing "Pictures" (or any path, for that matter) prompts the admin password. I hate to have to ask for assistance as I've always been able to solve my own problems, but I've tried everything I could possibly think of, even chown'd my /Home folder as myself, but to no avail. Even dear old Google has failed me. So I come before you o' humble Ubuntu community and humbly ask for any assistance you can throw my way. I'm a very experienced sysadmin so don't worry about having to dumb anything down.

---

### Post by yetiman64 on 2011-05-10
> **BrandonC19 said:**
> I'm posting this in absolute beginner's talk because it's probably an easy fix and I'm just not thinking straight, as work has me worn down a bit :). About a week or so ago I wiped my hdd and reinstalled Maverick. Everything went well for awhile until the other day when selecting any entry from "Places" or any directory from the "Run" dialog box suddenly appears to open the folder as root. All goes well if I append "Nautilus" before the directory in run (ex. "nautilus ~/Pictures") but simply typing "Pictures" (or any path, for that matter) prompts the admin password. I hate to have to ask for assistance as I've always been able to solve my own problems, but I've tried everything I could possibly think of, even chown'd my /Home folder as myself, but to no avail. Even dear old Google has failed me. So I come before you o' humble Ubuntu community and humbly ask for any assistance you can throw my way. I'm a very experienced sysadmin so don't worry about having to dumb anything down.

Try this to fix it, create a folder on your desktop with the right click menu, right click the folder and select "Open with other application", select "Open Folder" from the list, ensure the tickbox to remember the selection is ticked, click "Open". Nautilus folders (which includes the places menu and such) should now be re-associated with the correct application.

If you try opening a folder with any other application or use a custom command to do so, ensure the tickbox is de-ticked. This has been a pretty common problem here of recent.

Regards, yetiman64

---

### Post by BrandonC19 on 2011-05-10
Ah Yetiman, thanks for the reply, but it didnt work, as soon as I clicked the "Open folder" option the tickbox just disappeared, and after selecting the option it still didn't work. I do appreciate your taking the time to help though.

EDIT: Never mind that, I tried again, and there appears to not be a check box at all. I did try selecting my home folder and setting the custom open command to "nautilus" but still nothing.

---

### Post by philinux on 2011-05-10
> **BrandonC19 said:**
> I'm posting this in absolute beginner's talk because it's probably an easy fix and I'm just not thinking straight, as work has me worn down a bit :). About a week or so ago I wiped my hdd and reinstalled Maverick. Everything went well for awhile until the other day when selecting any entry from "Places" or any directory from the "Run" dialog box suddenly appears to open the folder as root. All goes well if I append "Nautilus" before the directory in run (ex. "nautilus ~/Pictures") but simply typing "Pictures" (or any path, for that matter) prompts the admin password. I hate to have to ask for assistance as I've always been able to solve my own problems, but I've tried everything I could possibly think of, even chown'd my /Home folder as myself, but to no avail. Even dear old Google has failed me. So I come before you o' humble Ubuntu community and humbly ask for any assistance you can throw my way. I'm a very experienced sysadmin so don't worry about having to dumb anything down.

Open a terminal. Use this code and post back the result.

```
ls -la
```

---

### Post by BrandonC19 on 2011-05-10
Hi Phil, here you go. ```
brandon@brandon-laptop:~$ ls -la
total 717844
drwxr-xr-x 53 brandon brandon      4096 2011-05-10 07:17 .
drwxr-xr-x  3 root    root         4096 2011-04-29 04:13 ..
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 04:57 .adobe
-rw-------  1 brandon brandon      1522 2011-05-10 07:17 .bash_history
-rw-r--r--  1 brandon brandon       220 2011-04-29 04:13 .bash_logout
-rw-r--r--  1 brandon brandon      3353 2011-04-29 04:13 .bashrc
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 05:36 .bogofilter
drwxr-xr-x 15 brandon brandon      4096 2011-05-10 07:16 .cache
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 07:43 .compiz
drwxr-xr-x 28 brandon brandon      4096 2011-05-10 07:16 .config
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 04:17 .dbus
drwxr-xr-x  2 brandon brandon      4096 2011-05-10 07:17 Desktop
-rw-r--r--  1 brandon brandon        92 2011-05-10 06:59 .dmrc
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:17 Documents
drwxr-xr-x  2 brandon brandon      4096 2011-05-10 02:11 Downloads
drwx------  3 brandon brandon      4096 2011-05-10 07:00 .dropbox
drwxr-xr-x 12 brandon brandon      4096 2011-05-10 07:00 Dropbox
drwxr-xr-x  5 brandon brandon      4096 2011-05-03 19:34 .dropbox-dist
drwxr-xr-x  2 brandon brandon      4096 2011-05-10 07:00 .dropbox-dist-new
drwxr-xr-x  4 brandon brandon      4096 2011-04-29 07:10 .emerald
-rw-------  1 brandon brandon        16 2011-04-29 04:17 .esd_auth
drwxr-xr-x  8 brandon brandon      4096 2011-05-10 00:01 .evolution
-rw-r--r--  1 brandon brandon       179 2011-04-29 04:13 examples.desktop
-rw-r--r--  1 brandon brandon    314775 2011-05-07 23:43 Firefox_wallpaper.png
drwxr-xr-x  5 brandon brandon      4096 2011-05-06 14:25 .fluxbox
drwxr-xr-x  2 brandon brandon      4096 2011-05-06 14:00 .fontconfig
drwxr-xr-x  5 brandon brandon      4096 2011-05-10 06:59 .gconf
drwxr-xr-x  2 brandon brandon      4096 2011-05-10 07:17 .gconfd
drwxr-xr-x  4 brandon brandon      4096 2011-04-29 07:06 .gegl-0.0
drwxr-xr-x 22 brandon brandon      4096 2011-05-09 01:43 .gimp-2.6
-rw-r-----  1 brandon brandon         0 2011-05-10 07:17 .gksu.lock
drwxr-xr-x  9 brandon brandon      4096 2011-05-09 02:28 .gnome2
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:18 .gnome2_private
drwxr-xr-x  2 brandon brandon      4096 2011-05-09 00:47 .gnomenu
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 05:50 .gnupg
drwxr-xr-x  4 brandon brandon      4096 2011-05-06 11:04 .googleearth
drwxr-xr-x  2 brandon brandon      4096 2011-05-05 02:53 .gstreamer-0.10
-rw-r--r--  1 brandon brandon       192 2011-05-10 06:59 .gtk-bookmarks
dr-x------  2 brandon brandon         0 2011-05-10 06:59 .gvfs
-rw-------  1 brandon brandon     10500 2011-05-10 06:59 .ICEauthority
drwxr-xr-x  4 brandon brandon      4096 2011-05-10 02:00 .icons
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 04:17 .local
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 04:57 .macromedia
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 04:48 .mission-control
drwxr-xr-x  4 brandon brandon      4096 2011-04-29 04:36 .mozilla
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:17 Music
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:17 .nautilus
-rw-r--r--  1 brandon brandon      7362 2011-05-03 02:50 Omegle conversation log_mario.html
drwxr-xr-x  4 brandon brandon      4096 2011-05-02 23:24 Pictures
drwxr-xr-x  3 brandon brandon      4096 2011-04-29 05:34 .pki
-rw-r--r--  1 brandon brandon   7104190 2011-05-03 02:53 Portal_wcs.swf
-rw-r--r--  1 brandon brandon       675 2011-04-29 04:13 .profile
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:17 Public
drwx------  2 brandon brandon      4096 2011-05-10 06:59 .pulse
-rw-------  1 brandon brandon       256 2011-04-29 04:17 .pulse-cookie
drwxr-xr-x  6 brandon brandon      4096 2011-05-09 02:28 .purple
drw-------  2 brandon brandon      4096 2011-04-29 05:43 .recently-used.xbel
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 05:50 .ssh
-rw-r--r--  1 brandon brandon         0 2011-04-29 04:19 .sudo_as_admin_successful
drwxr-xr-x  3 brandon brandon      4096 2011-05-07 23:57 .teamviewer
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:17 Templates
drwxr-xr-x  4 brandon brandon      4096 2011-05-10 02:00 .themes
drwxr-xr-x  5 brandon brandon      4096 2011-05-04 22:07 .thumbnails
-rw-r--r--  1 brandon brandon 726827008 2011-05-06 01:36 ubuntu-10.10-desktop-i386.iso
drwxrwxr-x  2 brandon brandon      4096 2011-04-29 05:15 Ubuntu One
drwx------  2 brandon brandon      4096 2011-05-09 01:23 Ubuntu Token Button
drwxr-xr-x  2 brandon brandon      4096 2011-04-29 04:17 Videos
drwxr-xr-x  2 brandon brandon      4096 2011-05-10 02:11 .VirtualBox
drwxr-xr-x  4 brandon brandon      4096 2011-05-06 01:30 VirtualBox VMs
-rw-------  1 brandon brandon     98642 2011-05-10 07:17 .xsession-errors
-rw-------  1 brandon brandon    436036 2011-05-10 03:29 .xsession-errors.old

```

---

### Post by philinux on 2011-05-10
Well that all looks normal.:neutral:

/me thinks again

---

### Post by BrandonC19 on 2011-05-10
Yea, it's just the weirdest thing. Never seen anything like it.

---

### Post by yetiman64 on 2011-05-10
One more idea to test all the associations for directory opening is the code,
```
cat /usr/share/applications/defaults.list /usr/share/applications/mimeinfo.cache ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeinfo.cache | grep directory
``` This checks any reference to directories in the 4 files listed and displays the output in the terminal, you can paste the output here for checking if it is not obvious where the problem is.

An example to compare with from my machine is,

> inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
inode/directory=nautilus-folder-handler.desktop
x-directory/gnome-default-handler=nautilus-folder-handler.desktop
Edit: If any vary from the above output you can individually "cat" each file while piping its output to grep with " | grep directory" to see where the problem is. The use of grep is to filter the output to instances of "directory" only, otherwise the output will be immense.

---

### Post by BrandonC19 on 2011-05-10
Here we are
```
brandon@brandon-laptop:~$ cat /usr/share/applications/defaults.list /usr/share/applications/mimeinfo.cache ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeinfo.cache | grep directory
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;pcmanfm.desktop;
inode/directory=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;pcmanfm.desktop;
text/directory=evolution.desktop
x-directory/gnome-default-handler=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;
inode/directory=userapp-[COLOR=Red]**gksudo**[/COLOR]-SVQFUV.desktop;nautilus-folder-handler.desktop;pcmanfm.desktop;Thunar-folder-handler.desktop;Thunar.desktop;

```
I see something having to do with gksudo there. Hmm......

---

### Post by yetiman64 on 2011-05-10
> **BrandonC19 said:**
> Here we are
```
brandon@brandon-laptop:~$ cat /usr/share/applications/defaults.list /usr/share/applications/mimeinfo.cache ~/.local/share/applications/mimeapps.list ~/.local/share/applications/mimeinfo.cache | grep directory
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;pcmanfm.desktop;
inode/directory=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;pcmanfm.desktop;
text/directory=evolution.desktop
x-directory/gnome-default-handler=nautilus-folder-handler.desktop;Thunar-folder-handler.desktop;
inode/directory=userapp-[COLOR=Red]**gksudo**[/COLOR]-SVQFUV.desktop;nautilus-folder-handler.desktop;pcmanfm.desktop;Thunar-folder-handler.desktop;Thunar.desktop;

```I see something having to do with gksudo there. Hmm......

That's what I was expecting to see, and its a user app so it will be in your home directory,

Use the code,
```
rm ~/.local/share/applications/userapp-gksudo-SVQFUV.desktop
``` That should fix the problem. Removing userapps is safe to do.  **Edit**: You may need to logout and back in for it to take affect.

---

### Post by BrandonC19 on 2011-05-10
Ahhh. Thank you all. Your help has been greatly appreciated, and I shall now mark this thread as solved. :)

---

