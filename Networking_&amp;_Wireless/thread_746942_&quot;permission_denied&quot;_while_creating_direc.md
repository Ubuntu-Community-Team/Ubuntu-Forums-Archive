---
title: "&quot;permission denied&quot; while creating directory on cifs mount."
date: 2008-04-06
forum: Networking &amp; Wireless
---

### Post by zoarre on 2008-04-06
i'm able to mount the samba folder with the following command (and other variations):
```

sudo mount -t cifs //computer/backups /mnt/backups -o user=x,pass=x
```

when i try to create a directory on the mounted fs, i get the following error:

```
mkdir: cannot create directory `/mnt/backups/blah': Permission denied
```

i've tried noperm and file_mode=0777,dir_mode=0777 without any success. any ideas about what i'm doing wrong?

thanks in advance.

---

### Post by Eiríkr on 2008-04-06
When mount is run with sudo for a cifs-type filesystem, root winds up being the ultimate owner and group of the share mountpoint, and thus you'd need to sudo to create any directory or file.  To change this, add the "uid=" and "gid=" mount options.  See [font=courier]man mount.cifs[/font] for more details.  I your case, the mount line should probably look a bit like this:
```
sudo mount -t cifs //computer/backups /mnt/backups -user=x,pass=x,uid=USERNAME,gid=GROUPNAME
```
Replace the caps as appropriate.  

HTH,

Eiríkr

---

### Post by zoarre on 2008-04-07
thanks for replying.

unforutnately, this doesn't appear to be the issue. the permissions do change according to ls -l but i'm still unable to make a directory (or any changes to the share, i assume). i did try sudoing to see if i could create a directory as root and the same thing happens.

the server is on a debian etch box, if that helps.

any other ideas? i've been reading through the man page for mount.cifs and haven't found anything helpful. i've tried options file_mode, dir_mode, noperm, and rw, without success.

again, thanks in advance for any advice.

---

### Post by Eiríkr on 2008-04-07
The question then becomes, does the username you're connecting as have write permission on the server's filesystem for the shared directory?  In other words, if you run **ls -l** on the server, would it show the shared directory as being writable for your username?

Cheers,

Eiríkr

---

### Post by zoarre on 2008-04-07
ah, that's the problem then. it's working now.

thanks!

---

### Post by Eiríkr on 2008-04-08
Cheers!  Glad it's working.  :D  If that does it for you in this thread then, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

