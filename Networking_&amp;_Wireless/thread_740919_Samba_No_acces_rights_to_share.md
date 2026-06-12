---
title: "Samba: No acces rights to share"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Reeva on 2008-03-31
Hello,

My samba shares are running very well, but now I got a little problem when I try to add a new share to my existing list.

I have a 500gig disk, that I mount on startup. This is ok, I see the disk on /mnt/backupdisk.
I did this using the fstab file:

```

/dev/sda1       /mnt/backupdisk vfat  iocharset=utf8,umask=000  0    0

```

Now I want to make a dir on that disk, and make it accessable to all the samba users.

mkdir -p /mnt/backupdisk/backups
chown -R root:users  /mnt/backupdisk/backups/

But this gives an error :
 chown: changing ownership of `/mnt/backupdisk/backups/': Operation not permitted

How can I solve this?

After that, I do:
chmod -R ug+rwx,o+rx-w /mnt/backupdisk/backups/

So the disk is mounted now. Next step is editing the samba share : sudo gedit /etc/samba/smb.conf

And that's my file:
```

[homes]
   comment = Home directory
   browseable = no
   valid users = %S   
   writable = yes
   create mask = 0700
   directory mask = 0700
   

[gedeelde_server]
path = /home/shares/gedeelde_server
comment = Gedeelde server alle gebruikers
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0660
directory mask = 2770

[backup_server]
path = /mnt/backupdisk/backups
comment = Backup server alle gebruikers
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0660
directory mask = 2770

```

The Home & gedeelde_server are working well, but the mounted drive not.

How could this be?

Thanks :)

---

### Post by superprash2003 on 2008-03-31
did you use sudo for the chown command?

---

### Post by Eiríkr on 2008-03-31
Yes, ditto on superprash2003's question.  Your chown command should look like this:
```
**sudo** chown -R root:users /mnt/backupdisk/backups/
```

Cheers,

Eiríkr

---

### Post by Reeva on 2008-04-01
Yes I did it like sudo, as I am in a sudo session ( sudo su )

thank you

---

### Post by superprash2003 on 2008-04-01
why dont you just do it via the GUI.. right click on the folder you created in nautilus and click on share folder.. and set it to check or uncheck "read only" option..

---

### Post by Eiríkr on 2008-04-01
@superprash2003 --

I don't know about Reeva's case, but very often the GUI doesn't provide the flexibility and finely grained possibilities required for proper configuration.  

@Reeva --

About the chown troubles, did you trying chown-ing immediately after creating an empty directory?  Is it possible some other process was somehow interfering, perhaps by accessing that directory?  One other thought, too -- though this is a bit weird, have you tried chown-ing when you leave the final / slash off, like so:
```
sudo chown -R root:users /mnt/backupdisk/backups
```

Your smb.conf file looks fine, so I strongly suspect that whatever access problem's you're having are related to your chown troubles.  

Cheers,

Eiríkr

---

