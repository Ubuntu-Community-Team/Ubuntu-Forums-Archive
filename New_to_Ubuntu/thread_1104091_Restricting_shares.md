---
title: "Restricting shares"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by GepettoBR on 2009-03-23
This seems like it should be a simple task, but apparently I'm an idiot and can't figure it out :)

My home network is comprised of four computers, two of which run Ubuntu (one of these dual-booting with Windows XP), one running XP and one running Vista. They are all connected through a wireless router, port forwarding is configured etc etc

I want to set up a shared folder on one of the Ubuntu machines for a partition I have mounted as /data. But here's the catch:

1) I want one user to have full read/write access to /data and all subdirectories.

2)I want every other user to have read-only access without needing to log in (is that called a public share? I have no idea), but not to all subdirectories of /data. Setting up separate shares for each subdir won't do, because there are files in the partition's root folder that I want shared as well. Specifically, there is ONE subdirectory that I only want the password-protected account to access remotely, and the rest can be open.

Also, what is the best way to configure such things?

I think this issue should be DE-agnostic, so I prefixed the thread All Variants, but for the sake of completeness, I'm running GNOME Intrepid Ibex 64-bit edition.

Thanks in advance for all replies.

Cheers,
Paulo

---

### Post by Bachstelze on 2009-03-23
You can do that easily using FTP. I think it should be easy to do using SAMBA too, but I don't have much experience with it.

---

### Post by GepettoBR on 2009-03-23
Well, then I really need help. How do I set up a LAN-only FTP server, and how do I configure permissions for it?

---

### Post by Bachstelze on 2009-03-23
There are a lots of ftpds to choose from, my favourite is vsftpd

```
sudo apt-get install vsftpd
```

You don't need to worry about making it "LAN-only". As long as you don't forward port 21 on your router, the server won't be accessible from the outside world. Then there's a few things you need to change in the configuration file, so open it in your favourite editor, for example:

```
gksudo gedit /etc/vsftpd.conf
```

Here's what you should need to change (those are the options you need, so add them if they're not in the file, or modify them if they have a different value):

```

anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
no_anon_password=YES
anon_root=/data

```

Next you must configure the permissions. You want one user to have full read/write access to /data and everything below it, so you give that user ownership of all that part of the filesystem:

```
sudo chown -R user /data
```

Then we give full read-write permisisons to that user and full read-only permissions to everyone else:

```
sudo chmod -R 755 /data
```

Finally, we set some secret directory (and everything below it) to be readable only by the owner:

```
sudo chmod -R 700 /data/secretdir
```

Finally, restart vsftpd:

```
sudo /etc/init.d/vsftpd restart
```

and you should be good to go.

---

### Post by GepettoBR on 2009-03-23
Thank you very much, HymnToLife.

This is simpler than I expected, too.

I suppose then that the location will be accessible through [ftp://my-internal-ip/data](ftp://my-internal-ip/data)?

---

### Post by Bachstelze on 2009-03-23
> **GepettoBR said:**
> 
I suppose then that the location will be accessible through [ftp://my-internal-ip/data](ftp://my-internal-ip/data)?

Close. ;)

For anonymous access: [ftp://ip](ftp://ip)
For "admin" access (i.e. with login): [ftp://login@ip/data](ftp://login@ip/data)

In Vista and KDE, you can put a shortcut to it in the "My Computer"-thingie (I don't know about XP or Gnome).

---

### Post by GepettoBR on 2009-03-23
Thanks again, I'll try this when I get back home.

---

