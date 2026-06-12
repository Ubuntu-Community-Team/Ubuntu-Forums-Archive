---
title: "How do you  get command prompt at a network share?"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by cwmoser on 2009-02-06
How do you get a command prompt - I guess the proper terminology in Linux is Terminal - on a Network Share.

I can mount a Windows share using the GUI, but when I want to drop down to the command prompt, I can't seem to CD to the mounted folders.

In Windows, I would do something like this:

NET  USE  Y:  \\SERVERM\docs
Y:
cd book


Carl

---

### Post by GMachine_24 on 2009-02-06
I am a little confused - have you installed Samba and configured it to work with your Windows boxes? This part especially I don't understand:

```


I can mount a Windows share using the GUI, but when I want to drop down to the command prompt, I can't seem to CD to the mounted folders.


```

When you say you can mount a Windows share using the GUI, what GUI are you referring to?

Are you asking if you can use a terminal window on your Ubuntu box to get access to your networked Windows computers/shares? Or are you asking if you can open a terminal window on your Windows machine from your Ubuntu box?

--gm

---

### Post by Seq on 2009-02-06
If you're using gnome (Ubuntu, as opposed to kubuntu, etc) then you will be using gvfs.

If you open a terminal and go to ~/.gvfs, it will have the filesystems you've mounted with nautilus, gnome's file manager.

---

### Post by Seq on 2009-02-06
I should add that your windows example is rather similar to using the 'mount' command (from memory):

```
mount -t cifs \\SERVERM\docs /some/directory
```

Those files would be accessible in /some/directory.

If you used the GUI, which mounted through gvfs, note that it is not persistent, and is only available for your user.

---

### Post by 505 on 2009-02-06
I think if you access a network share using the GUI, you cannot easily get a terminal to that. You can check that by opening the network folder and looking in the lower left dropdown. If is starts with "/" (e.g. "/media"), then that is the path you can go to.
Otherwise you must mount it yourself using the terminal, using the "mount" command. You then have to give an (empty) folder to mount to. After that you can access that folder using the terminal.

---

### Post by lykwydchykyn on 2009-02-06
You want to use the smbmount command, because you'll likely have permissions trouble using "mount" as a normal user.  The command looks like this:
```

smbmount //server/share localfolder -o username=username

```
The username bit is optional if guest access is enabled on the share.  Basically, since we don't use drive letters you're just "mapping" the share to any folder on the system.

The other option is to use smbclient, which is like using FTP only with Windows shares.  You log in, use get/put to download/upload just like FTP.

---

### Post by Seq on 2009-02-06
> **505 said:**
> I think if you access a network share using the GUI, you cannot easily get a terminal to that.

One of the design features of gvfs is that filesystems mounted through it (smb/cifs, ssh/sftp, etc) are accessible within the filesystem for the user who is accessing it. These mounts get placed in ~/.gvfs

This is to allow applications that are not gvfs-aware (anything that is not a gnome app, and still a few that are) access files that have been mounted via a gvfs application. This was one of the benefits over the older gnome-vfs and is a relatively recent feature.

---

