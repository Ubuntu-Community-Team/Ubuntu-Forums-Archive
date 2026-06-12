---
title: "Connect to Server and absolute path"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by skirkpatrick on 2007-03-08
When I use Places->Connect to Server, what's the actual path for the resulting directory?  It may show up on the desktop but it's not in ~/Desktop.  Programs like XMMS or even if I wanted to access the share from a terminal, can't find the directory.  So how can I access it from non-Gnome compliant programs?

---

### Post by Mr. C. on 2007-03-08
> **skirkpatrick said:**
> When I use Places->Connect to Server, what's the actual path for the resulting directory?  It may show up on the desktop but it's not in ~/Desktop.  Programs like XMMS or even if I wanted to access the share from a terminal, can't find the directory.  So how can I access it from non-Gnome compliant programs?

I believe its just a virtual folder - its a set of properties, that when opened/browsed rusn the appropriate browse utility.

You created the folder, so you should know where it points.

MrC

---

### Post by skirkpatrick on 2007-03-08
Actually, Connect to Server creates the folder but I have no idea how to get to it other than clicking it on the desktop.

The reason I'm asking is because my Samba mounts in fstab that were working in Edgy do not work in Feisty.

---

### Post by Mr. C. on 2007-03-08
As I said, I believe it is a VIRTUAL folder.  Think of it like a shell script with an icon, that when you double-click it, it runs the shell script.  Its more complicated than that, but that's the idea.

If your SMB mounts are not working, you need to check to be sure that Samba is configured correctly and that you can mount an SMB share manually.  One you can do it manually via command line, add them to your fstab.

MrC

---

### Post by skirkpatrick on 2007-03-08
Yeah, I was afraid they were virtual.  As far as mounting the shares, they were working in fstab under Edgy and changing from smbfs to cifs makes them work in Feisty.

---

