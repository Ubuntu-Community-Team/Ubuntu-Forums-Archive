---
title: "Automount network drives with pam so long as network is up"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by xingmu on 2008-01-01
I have already set up my network drives to be mounted when I login into Gnome using the pam_mount plugin.  This has worked great when I am using either wired network or manual configuration of my wireless.  But under roaming mode my network drives don't mount.  I am pretty sure this is because the network connection is not up until after I login, and so the mount command fails because there is no connection to the network drive.

But I want to ask if there is any way to delay pam_mount until after the network is up?  I got a feeling this is asking too much from pam, but I would like a second opinion.

And if I really can't do this through pam, than are there any recommendations about alternatives?

Thanks!

---

### Post by xingmu on 2008-01-13
Well, it looks like I am going to answer my own question:

It seems that there is no elegant way to mount network drives with pam when the network is not already connected at boot up.  The best way that I can find is to add the following line to the /etc/fstab file:

```
//servername/folder /mountpoint cifs defaults,credentials=/etc/smb-credentials 0 0
```

You also need to make a file called /etc/smb-credentials with the follow info (note there are NO spaces around the = sign):

```

username=yourname
password=yourpass
domain=yourdomain

```

You should change the permissions so that only root can read it:

```
sudo chmod 640 /etc/smb-credentials
```

When you boot up again (or just disconnect and reconnect the network), the network drives will be automatically mounted.  This is because there is a script ( /etc/network/if-up.d/mountnfs ) which will automatically mount nfs/smb/cifs entries in the /etc/fstab.  

Perhaps this can help someone else!

---

### Post by oror on 2008-03-05
Is there any way to do this without the use of a password file on the system? Can't I just use the login credentials for that user to automount the directories upon login, without leaving a file with potentially dangerous passwords in it?

---

### Post by xingmu on 2008-03-05
Well, yes and no.  The libpam-mount allows you to mount a network drive using the login credentials.  The problem is that it will attempt to the mount the drive right after login.  If the network is not yet up (as was my case), then the mount will fail.

So the alternative is to make a credentials file.  Even though it may not be the most secure option, note that chmod'ing the file makes it so only the adminstrative users can read the file.  It cannot be viewed by ordinary users.  So it's not *that* insecure.

---

### Post by oror on 2008-03-06
I'll give libpam-mount a try. It seems like you can't even use hashed passwords in the credentials file. chmod'ing it to something more secure is good, but I'm still hesitant to put any important login credentials (i.e., AD domain admins) in plain text anywhere on the system, restrictive permissions or not.

---

