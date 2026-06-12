---
title: "SMB client (Cx File Explorer) can't access shared folder"
date: 2021-01-31
forum: Networking &amp; Wireless
---

### Post by uacnt83982803 on 2021-01-31
I have a shared folder configured with some photos in it.  Trying to get my Android to be able to access the files, when I'm at home, via WiFi.

I configured UFW so that the Android can get to the PC's IP, that works fine.  It can connect (I'm logging in with a separate guest account I created).  

Cx File Explorer (on the Android) sees the shared folder, but can't access the contents (Access denied error).

If I sign into the PC with the guest account, it doesn't have rights to access the folder, so I'm pretty sure the problem stems from a permissions issue on the Ubuntu PC.  The sharing is set up as follows:

(inside the Properties on the shared folder under Local Network Share): Allow others to create and delete files is checked (on).
(on the Permissions tab): "Others" are set to Access Files.  Under "Change Permissions", Others are read-only for Files and Access Files for Folders.

What am I missing?  Thanks in advance!

---

### Post by TheFu on 2021-01-31
Many android apps use a free SMB1 library.  By default, samba disabled smb1 support because it is easier to crack than looking up and typing a password.  The version of android may matter too.

Might I suggest using some other method - perhaps ssh-based - instead?  Then you can use scp or rsync to push or pull files.

If this is a 1-time thing, you could run a tiny web server (python has a 1-line web server) just to share files quickly. There's a different line depending on python3 or v2.

I use nextcloud or a USB cable to connect Linux to my Android devices. I just have to plan ahead slightly, since nextcloud sync is sorta slow.  One of my devices runs Android v5 and it allows putting files almost anywhere on the device.  Another device has a newer Android version where google locked down things 1000x too much, so we can't put files where we want them and every app needs to be granted permission to access specific storage areas controlled by other apps.  What a pain.

---

### Post by uacnt83982803 on 2021-01-31
I'm on the most recent update of Android.  The app requires me to enter a username and password (which is where I'm using my guest account).

So I can connect ok, the problem is a sharing issue on the PC end.  I need to understand what I am doing wrong or missing.

Again if I log into the PC using that same guest account, I can't access the shared folder.  So I am pretty sure the problem lies there, not in the Android app. 

I am confident that if I can fix it so that when logged into the PC using that guest account, and access that shared folder, I should be ok with the app.  Thanks!!

---

### Post by Morbius1 on 2021-01-31
> (inside the Properties on the shared folder under Local Network Share): Allow others to create and delete files is checked (on).
(on the Permissions tab): "Others" are set to Access Files.  Under  "Change Permissions", Others are read-only for Files and Access Files  for Folders.
Please post the output of the following command so we can see how Samba views that share:
```
net usershare info --long
```
You might want to post the output of this one as well se we can see how Samba itself is set up:
```
testparm -s
```

---

### Post by uacnt83982803 on 2021-01-31
Ok, here we go:
net usershare info --long returns:
[Sandisk]
path=/media/me/Sandisk
comment=
usershare_acl=Everyone:F,
guest_ok=n

(guessing 'guest_ok=n' isn't good?)

2nd query:
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
WARNING: The 'netbios name' is too long (max. 15 chars).

Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by Morbius1 on 2021-01-31
> path=/media/me/Sandisk
The "me" there is the issue.

Linux sets up this mount point path in such a way that only "me" can get to whatever is beyond it. 

You can either access the share with "me" and the corresponding samba password for "me":
```
sudo smbpasswd -a me
```
Or if you already did that for your "guest" user you created and since you have a simple share you can force the guest user to appear as "me" by:

Editing /etc/samba/smb.conf, find the workgroup = WORKGROUP line, and add this under it:
```
force user = me
```

Then restart smbd:
```
sudo service smbd restart
```

[COLOR=#ff0000]**Note**[/COLOR]: I'm assuming the "me" refers to an actual local Ubuntu user name so use that name instead of me above.

---

### Post by zergling on 2021-01-31
I am still a novice in SAMBA since I just installed it couple days ago but I noticed that you are missing the following 

```
  
create mask = 0777
directory mask = 0777

```


Anyhow, below is what I did on my SAMBA Server and  Cx File Explorer App works great 

```

sudo mkdir /cloud
```

```

sudo chmod user_name:user_name /cloud -R
```

```

sudo smbpasswd -a user_name
```


In /etc/samba/smb.conf add the text below

```

[cloud]
  path = /cloud
  writeable = yes
  browseable = yes
  create mask = 0777
  directory mask = 0777
  public = no

```


Restart Samba daemon.

```
sudo systemctl restart smbd
```


Now, you should be able to access your Samba folder from Cx File Explorer

---

### Post by uacnt83982803 on 2021-01-31
Sounds like I set it up incorrectly to start with.  How should I set the share up, so that I and the guest account can access it, properly?  Thanks.

---

### Post by zergling on 2021-01-31
for setting the shared to be accessible by guest you need to add

```
guest ok = yes
```

---

### Post by Morbius1 on 2021-01-31
There is no way to do that on a samba usershare.

This is a legitimate samba usershare:
> [Sandisk]
path=/media/me/Sandisk
comment=
usershare_acl=Everyone:F,
guest_ok=n

It will require that you access the share as "me" unless you do what I posted above.

---

### Post by uacnt83982803 on 2021-01-31
I'll try that.

---

### Post by Morbius1 on 2021-01-31
In a terminal:
```
sudo -H gedit /etc/samba/smb.conf
```
I'm guessing here you are using Ubuntu since you didn't specify.

---

### Post by uacnt83982803 on 2021-01-31
Tried this, didn't work.  Even just logged into the PC itself (never mind an Android app) I can't access the files in the sandisk when logged in as the guest.
sudo chmod user_name:user_name /cloud -R [FONT=arial]didn't work at all, returns: invalid mode: guest:guest (guest being the username).

Done fooling with this for tonight, too tired.  I just wish this was easier.  I'm an old hand at TOPS-20 and RSX-11M+ but some of this Linux stuff is beyond me.  Maybe I'm getting too old, sigh.
[/FONT]

---

### Post by Morbius1 on 2021-01-31
You seem to ignoring my posts which is fine by me but:

> Even just logged into the PC itself (never mind an Android app) I can't  access the files in the sandisk when logged in as the guest.
Of course you can't. I already explained that:
>  [QUOTE]path=/media/me/Sandisk
The "me" there is the issue.

Linux sets up this mount point path in such a way that only "me" can get to whatever is beyond it. [/QUOTE]

DO you have a requirement that this "guest" user not only have access to the share over the network but also locally on the Ubuntu box itself?

If that is so change your mount point.

[COLOR=#ff0000]And chmod changes mode or permissions. chown changes owner and group.

Cheese and crackers folks. I'm outa here.[/COLOR]

---

### Post by uacnt83982803 on 2021-01-31
I'm sorry, I'm not deliberately ignoring your recommendations.  I'm just trying to follow one path at a time.  I'll switch paths now.  I don't need the 'guest' to have access locally, but I figured that was needed.  Maybe not?

To change the mount point, that's in Disks, under Mount Options?  There is a field for Mount Point, but nothing in there has the path as shown above with 'me' in it.  It's shown as 

/mnt/usb-SanDisk_Cruzer_Glide_4C530000240615101283-0:0

---

### Post by TheFu on 2021-01-31
BTW, **chmod** and **chown** don't work with NTFS or exFAT or FAT32 file systems.

---

