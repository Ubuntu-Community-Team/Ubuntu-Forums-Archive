---
title: "VSFTPD, Ntfs-3g and folder/user permissions"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by aoenate on 2009-03-28
Hey guys,

I'm trying to setup a small ftp server for at home (planning on it being a glorified network hdd with print and web serving in the future)

The plan is to have two different types of ftp users, one "administrator" and a two "users".
Nate - Server Administrator: Read/Write/Rename/Delete
users: Download/Upload(includes making new folders)
My idea here is to keep somebody from accidentally deleting everything or messing up the file structure.

Running Ubuntu server 8.10, vsftpd (both updated) There are two hdds installed, one 80gig(ext3) for os and a 500g(ntfs, ntfs-3g) dedicated to the ftp server. 500g drive is set to mount on boot to /mnt/ntfs. I've created a new group called ftp-user and made a few test users, setting their home folder to /mnt/ntfs/.

Where i'm getting stuck is at the user permissions. I was planning on making "user" read only at first then adding the upload feature once i got that working (maybe create a /mnt/ntfs/download and /mnt/ntfs/upload directory with different permissions and i can manually move upload to download)

```

nate@linuxserver:/mnt/ntfs$ sudo chown Nate:ftp-users /mnt/ntfs
nate@linuxserver:/mnt/ntfs$ sudo chmod 644 /mnt/ntfs/*
nate@linuxserver:/mnt/ntfs$ ls -l
total 4
drwxrwxrwx 1 root root 4096 2009-03-28 11:14 ftp
```

I'm confused why the root root is still there. I was attemping to change ownership of the directory and all subdirectories. Are their issues with ntfs-3g and permissions? As of now my "users" have full read/write/delete access via FTP. If this looks normal or i'm going about this all the wrong way i'm open to trying other things.

For the sake of time please let me know if you have any questions, this post could get very long if i try to display all the configurations. I'll try to find any other info you need, just ask.

Sorry if i ran on a bit, I'm still trying to learn linux.

Thanks - Nate

---

### Post by SunnyRabbiera on 2009-03-28
Ubuntu by default disables the root account, sudo is used in its place.

---

### Post by aoenate on 2009-03-28
After running "ls -l" and seeing root root is normal? I wanted to change the folder ftps ownership to Nate(a system user, in the group ftp-user).

---

### Post by tripolitan on 2009-03-28
You are getting stuck on user permissions because you are using the wrong file system. Use NTFS if you are setting up a Windows server, ext3 is for linux servers.

Based on your requirements:
-One shared HD
-no anonymous ftp
-Nate is Admin (read write)
-Users read/write (PROBLEM, this pretty much means that users have the same permissions as Nate!) This is unsafe and redundant.

If you want people to not mess other people's files or accidentally delete them, they must have their OWN ftp directory from within their own local user account on the linux server.

If you are new to setting up FTP servers, here are certain things you might want to consider:
-Nate should NOT login to an FTP server as root.
-Restrict local users to their home directories.

listen=yes
anonymous_enable=no
local_enable=yes
write_enable=yes
xferlog_enable=yes
connect_from_port_20=yes
chroot_local_users=yes
leave the rest of options at their default setting

If this is a local server (not accessible from outside your local network)
You could enable anonymous logins and have the files owned by a user other than root, this way, no anonymous user can accidentally delete other's uploads and users don't have to have an account on the linux server. In this case:
anonymous_enable=yes
local_enable=no
chown_uploads=yes
chown_username=EnterExistingLocal_NON-ROOT_Username

Finally, Nate should login to the server using ssh (shell), from there Nate can start mc or some other file manager and perform file management from there. If Nate is logging-in, using ssh on a linux machine (vs. using cygwin from Windows), Nate can also do some file management by starting a graphical file manager, like Konqueror or gnome-commander. These file managers have to be installed on the server and Nate would have to login using [ssh [email]nate@nnn.nnn.nnn.nnn[/email] -X] (the -X is to enable X forwarding to the client side)

---

### Post by aoenate on 2009-03-28
Thanks for the help tripolitan - the drive is NTFS because it in a windows box as a secondary hd. I was hoping to avoid reformatting but it seems to be causing some problems. I'll begin backing up all the data and reformatting into ext3 and double check the server config.

---

### Post by hyper_ch on 2009-03-28
unix permissions don't work on ntfs - so chmodding the ntfs folder will achieve nothing.

who needs to access that ftp server? I think you might fare better with just a ssh server and scp

---

### Post by aoenate on 2009-03-28
My ideas were to have password protected file sharing, giving access to a few people on the local network but not everybody (apartment building all on same LAN, access to the friends but not just anybody). The entire network is behind a router and shouldn't be accessible from the outside world so security isn't a priority for me at this time.

The files, all 260gigs are still being backed up to a external hdd as we speak. I successfully got the functions of the FTP server running out of a temporary folder on the main hdd.
Thanks once again for the help.

---

### Post by hyper_ch on 2009-03-28
In that case I'd rather use mysecureshell to restrict your friends as systemusers and use scp for the filetransfer.

---

