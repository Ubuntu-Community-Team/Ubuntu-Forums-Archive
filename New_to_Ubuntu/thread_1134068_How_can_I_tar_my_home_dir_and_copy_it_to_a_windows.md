---
title: "How can I tar my home dir and copy it to a windows box?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by mvalviar on 2009-04-23
I'll be installing jaunty later. I'll want to back-up my entire home folder and copy it to a windows box over a network. My home folder isn't that big. I wanted to tar it since windows can't handle dot files. I want to use tar /home/username <destination> where destination is a folder named "Shared Documents" under the windows box. I don't know how to write <destination> in the CLI.

---

### Post by starcannon on 2009-04-23
R+click your home folder, choose "create archive" from the contextual menu.

After looking at the tar man page, to command line it would be something like:
```
tar -cvvf foo.tar foo/
```tar contents of folder foo in foo.tar

```
man tar
```GL and have fun.

---

### Post by stchman on 2009-04-23
> **mvalviar said:**
> I'll be installing jaunty later. I'll want to back-up my entire home folder and copy it to a windows box over a network. My home folder isn't that big. I wanted to tar it since windows can't handle dot files. I want to use tar /home/username <destination> where destination is a folder named "Shared Documents" under the windows box. I don't know how to write <destination> in the CLI.

Right mouse click on /home/<your name> and select Create archive.  You will need to go up one folder.

Select .tar.gz and let it go.

---

### Post by kanikilu on 2009-04-23
> I don't know how to write <destination> in the CLI.

Assuming you have a windows machine ("winbox") with a shared folder ("share"), you need to mount it first.

```
sudo mkdir /media/winbox
sudo mount.cifs //winbox/share /media/winbox -o user=windowsUsername,pass=windowsPassword,rw
```

You might have to play around with the mount options, check out the man page for mount.cifs.

Once it's mounted, just use /media/winbox as the destination in your tar command.

---

### Post by mvalviar on 2009-04-23
Sorry if that was ambiguous. Tarring from the context menu creates a tar file in the same folder. I wanted to run the command such that the tarfile is written to the shared folder on the windows network. Running your example will create foo.tar in the current working directory.

---

### Post by starcannon on 2009-04-23
> **mvalviar said:**
> Sorry if that was ambiguous. Tarring from the context menu creates a tar file in the same folder. I wanted to run the command such that the tarfile is written to the shared folder on the windows network. Running your example will create foo.tar in the current working directory.

Ah, np, it would look more like this then:
```

tar -cvvf /location/of/windows/directory/foo.tar foo/

```

---

### Post by mvalviar on 2009-04-23
Yes, thats what I'm looking for. Under nautilus the address bar shows ```
smb://milan/SharedDocs/
```. I can't use this path in the terminal. What should I use then? Is it under /mnt? /dev? I really have no idea.

Thank you for your patience.

---

### Post by mvalviar on 2009-04-23
> **kanikilu said:**
> Assuming you have a windows machine ("winbox") with a shared folder ("share"), you need to mount it first.

```
sudo mkdir /media/winbox
sudo mount.cifs //winbox/share /media/winbox -o user=windowsUsername,pass=windowsPassword,rw
```

You might have to play around with the mount options, check out the man page for mount.cifs.

Once it's mounted, just use /media/winbox as the destination in your tar command.

Eureka! Thanks I haven't read this earlier.

---

### Post by starcannon on 2009-04-23
****Heres a nice guide to mounting Windows Shares to a folder using samba (smb).
[http://www.geekology.co.za/blog/2009/04/ubuntu-linux-quick-tip-mount-samba-windows-file-share-to-folder/](http://www.geekology.co.za/blog/2009/04/ubuntu-linux-quick-tip-mount-samba-windows-file-share-to-folder/)


Ah, okies I see now; the Windows directory you want to save to is not on another partition of the machine with the /home/your_username directory that needs tar'd(sic).

I'll do a bit of digging around, though I think the easiest would be to tar it with R+click and then just use nautilus to move the foo.tar file over to the windows networked computer.

Anyway, I'm curious how it would be done to tar smb://some/windows/computer/folder/foo.tar foo/ so I'll keep looking into it and report back anything I find.

GL

---

### Post by kanikilu on 2009-04-23
Type **mount** at the command line to find it. I think it will probably be under ~/.gvfs/...

---

### Post by stchman on 2009-04-24
> **mvalviar said:**
> I'll be installing jaunty later. I'll want to back-up my entire home folder and copy it to a windows box over a network. My home folder isn't that big. I wanted to tar it since windows can't handle dot files. I want to use tar /home/username <destination> where destination is a folder named "Shared Documents" under the windows box. I don't know how to write <destination> in the CLI.

When someone uses a parameter in CLI apps and uses the <xxxx> nomenclature the <> means it is a required parameter.  Do not actually type <destination>.  Type something like ~/backup in place of destination.

---

