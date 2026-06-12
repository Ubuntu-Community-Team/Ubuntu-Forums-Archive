---
title: "File doesn't exist"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by visisound on 2009-04-12
I have recently installed Ubuntu 8.10 and now have the video drivers working so I can use 2 screens. However, when I try to save the configuration I get an error message telling me it couldn't access the xorg.conf.backup file. This file doesn't exist.

When I tried to create it, it seems I don't have sufficient permissions to do so and when I try to switch to superuser using su I don't have the correct password. Is there a default su password with the installation?

How can I create this file or chmod other files which is apparently beyond my privileges right now?

visiound

---

### Post by cariboo on 2009-04-12
WHen editing configuration files, you have to edit and save then as root. To do this press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

This will allow you to edit and save the config file.

I would suggest using the save-as function to backup the file before editing.

Jim

---

### Post by visisound on 2009-04-12
Thanks for your reply,Jim.

I'm   not actually trying to edit the file. I'm using the NVIDIA X Server Settings tool in the System/Administration menu. When I try to save the config I get the dialogue box which says:

" Unable to create new X config backup file '/etc/X11/xorg.conf.backup' "

I'm assuming this is a permissions problem on the directory but as I can't log in as superuser I can't change the permissions. It seems I don't have the superuser password but I don't know what it might be. When I installed Ubuntu it never asked for a superuser password, only for my user password.

Is there a default password that Ubuntu is installed with?

---

### Post by nandemonai on 2009-04-12
> **visisound said:**
> Thanks for your reply,Jim.

I'm   not actually trying to edit the file. I'm using the NVIDIA X Server Settings tool in the System/Administration menu. When I try to save the config I get the dialogue box which says:

" Unable to create new X config backup file '/etc/X11/xorg.conf.backup' "

I'm assuming this is a permissions problem on the directory but as I can't log in as superuser I can't change the permissions. It seems I don't have the superuser password but I don't know what it might be. When I installed Ubuntu it never asked for a superuser password, only for my user password.

Is there a default password that Ubuntu is installed with?

Run the nvidia-settings app with gksudo from treminal.

```
$ gksudo nvidia-settings
```

---

### Post by theozzlives on 2009-04-12
Helpful hint: Ubuntu uses sudo instead of su.

---

