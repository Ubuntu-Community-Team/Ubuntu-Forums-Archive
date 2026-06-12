---
title: "How do I permanently mount a Windows share?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Unhyper on 2009-12-31
I realize this is an extremely common problem, and I've searched for an answer quite a bit, seeing as I'm sure it's out there. Just haven't had any luck working it out.

I have a home network of two PCs connected through a Belkin router. One PC is running Windows 7 (not in homegroup) and sharing a printer, and the other Ubuntu Karmic x64.

I have managed to connect and test print to the printer shared on the Win PC via Samba. My next step was to find a way to add a quick bookmark in my Places menu for the folders I have shared on Windows.
[FONT=monospace]
[/FONT]I found a [recent thread]("http://ubuntuforums.org/showthread.php?t=1369102") in which instructions were given to issue the following commands in Terminal:

sudo apt-get install smbfs
sudo mkdir /mnt/samba
sudo mount -t smbfs -o username=user,password=pass //networkaddress/share /mnt/samba

Having done that, I can use File Browser to select File System | mnt | samba, which takes me to /mnt/samba where the selected shared contents from Windows are available. So that at least tells me that I have the right credentials and am on the right track since I can access those files.

But I can't figure out how to make a permanent bookmark in the Places menu for quick access and an easy mount. I am assuming that if I were to reboot my machine now, that mounted location would no longer be accessible via /mnt/samba, until I went into Terminal and mounted it by hand again.

I found some instructions that suggested using the Places|Connect To Server option to connect to the share and bookmark it; but when I do that, I just get an error message telling me it's unable to connect. There is no Samba option in that dialog screen, anyway, so I just tried Windows Share, but it's not working.

---

### Post by SuperSonic4 on 2009-12-31
I would get samba to start on boot before fstab is read (no idea how to do it in ubuntu)

*edited out*

---

### Post by Seq on 2009-12-31
Add the following line to your /etc/fstab

```

//networkaddress/share /mnt/samba cifs _netdev,username=user,password=pass 0 0

```

A few notes:
[LIST]
[*]If it's just you, you could use the network browser instead of adding to fstab (I prefer this route on my laptop as my smb mount is not always available).
[*]You probably want to use cifs instead of smbfs. cifs is the newer protocol in samba.
[*]_netdev is a hint to the startup scripts to wait until after networking has come up to mount that share. I'm not sure what will happen if you depend on Network Manager with wireless (NM wired works fine. I use this for /home over nfs on my desktop).
[/LIST]

---

### Post by Seq on 2009-12-31
Also, fstab is publicly readable, so you may not want your password in there.

Create (as root) a file called /etc/samba/myserver.creds with the below information:
```
username=user
password=pass
workgroup=WORKGROUP

```

For security purposes, ensure the file is owned by root and the mode is 600 (rw by root).
```
chown root:root /etc/samba/myserver.creds
chmod 600 /etc/samba/myserver.creds
```
Then replace the username and password part in your fstab with
```
credentials=/etc/samba/myserver.creds
```

---

### Post by michaelsidenius on 2010-01-09
Hi 
I have the same problem. But I am seeking a solution where each user are logged into their own Samba drives when they log onto the Ubuntu box. Just like you can define individual drive mappings (to samba drives) in windows for each user.

The "bookmarks" in "places" works only halfway for me: the server samba drives are nicely mounted under ~/.gvfs/<bookmark name>, but I have to manually open the bookmarks after login, to have them activated/mounted. And many applications don't show ".<something>" files in their file selector (because they are hidden).

So what I want is a simple way of declaring permanent mounting (for each user) f.inst under ~/net (like ~/net/photos, or ~/net/private-net-folder) of the samba folders. 

Any ideas for doing this "right"?

Thanks,

Michael

---

### Post by Seq on 2010-01-09
> **michaelsidenius said:**
> Hi 
I have the same problem. But I am seeking a solution where each user are logged into their own Samba drives when they log onto the Ubuntu box. Just like you can define individual drive mappings (to samba drives) in windows for each user.

The "bookmarks" in "places" works only halfway for me: the server samba drives are nicely mounted under ~/.gvfs/<bookmark name>, but I have to manually open the bookmarks after login, to have them activated/mounted. And many applications don't show ".<something>" files in their file selector (because they are hidden).

So what I want is a simple way of declaring permanent mounting (for each user) f.inst under ~/net (like ~/net/photos, or ~/net/private-net-folder) of the samba folders. 

Any ideas for doing this "right"?

You should create a new thread as per-user mounting is substantially different than persistent global mounting, and you will have more luck with a more descriptive title.

Off the top of my head, I'd read up on pam-mount.

---

