---
title: "Connecting using Samba"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by Blazeix on 2006-12-03
Hi, I'm trying to connect to windows share using samba. In windows to connect all I have to do is type the location into the address bar of explorer (like \\example.address.net\folderName) and it automatically connects to it. Right now I don't have to enter in a password. 

I have been trying to do this under Linux, and I haven't made it very far. I have installed samba on linux. From what I've read, I need to use either the smbclient or the smbmount command. I've tried simply typing in 'smbclient \\example.address.net\folderName.' I've also tried pinging it and connecting directly to the ip, but nothing seems to work. Can anyone help? Thanks.

---

### Post by mssever on 2006-12-03
> **Blazeix said:**
> Hi, I'm trying to connect to windows share using samba. In windows to connect all I have to do is type the location into the address bar of explorer (like \\example.address.net\folderName) and it automatically connects to it. Right now I don't have to enter in a password. 

I have been trying to do this under Linux, and I haven't made it very far. I have installed samba on linux. From what I've read, I need to use either the smbclient or the smbmount command. I've tried simply typing in 'smbclient \\example.address.net\folderName.' I've also tried pinging it and connecting directly to the ip, but nothing seems to work. Can anyone help? Thanks.
Am I correct in understand that you're only trying to connect to shared services, and not host them on the machine in question? If so, you should be able to open Nautilus and hit Ctrl+L, then type in smb://. You can then browse to what you want. I don't know the exact path format that Nautilus uses, but you can see the results of browsing.

---

### Post by Blazeix on 2006-12-04
Right, I just want to connect to them. I'm using Xubuntu, so I don't have nautilus. I tried to connect to it in Thunar (xubuntu Nautilus equivalent) but it didn't work. Can I do it via the command line? Thanks for your help.

---

### Post by mssever on 2006-12-04
> **Blazeix said:**
> Right, I just want to connect to them. I'm using Xubuntu, so I don't have nautilus. I tried to connect to it in Thunar (xubuntu Nautilus equivalent) but it didn't work. Can I do it via the command line? Thanks for your help.

You can use smbclient to access samba shares like ftp (man smbclient for info). If you want to mount the partition, set the type in /etc/fstab to smbfs. See man smbmount for a list of the options.

---

### Post by grumpymole on 2006-12-04
Blazeix,

Or you can [try this]("http://ubuntuforums.org/showthread.php?t=304131"), which allows you to browse SMB shares from within thunar.  It works well for I need to do.

An alternative is to install [pyNeighborhood]("http://pyneighborhood.sourceforge.net"), which also allows you to browse and mount CIFS network shares.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

### Post by Blazeix on 2006-12-05
Thanks for your help, My networking knowlege is not very strong. I tried using pyNeighborhood. I can see some shares, but I can't see the share I'm trying to access. The share is on the same subnet that I'm on, but it isn't on the same 'subsubnet.' (i.e. I have IP a.b.c.d, and I'm trying to access a.b.x.y. I can see the a.b.c.w shares but not the a.b.x.y shares) 

First I'd like to connect via command line, and then I'll experiment around with GUIs. I'm typing the following:

```

smbclient -N //xyz.name.net/folder/folder2
Domain=[xyz] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

I changed the share name because it isn't currently password protected. I googled 'NT_STATUS_BAD_NETWORK_NAME' and it seems that it can't resolve the name of the share. I'm wondering if I have a incorrect setting somewhere. Does anybody have any ideas? Thanks for your help and patience!

Edit: I finally got connected via command line! For some reason, connecting to //xyz.name.net/folder/folder2 doesn't work, while connecting to //xyz.name.net/folder/ and then cd-ing into folder2 does. Thanks for the help!

---

