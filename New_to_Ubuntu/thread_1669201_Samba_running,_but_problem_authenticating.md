---
title: "Samba running, but problem authenticating"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by ripeart on 2011-01-17
So, I set up samba using the instructions as thus:

smb.conf settings I changed/added:[INDENT]security = share

[SHARE]
 comments = sharename
 path = /validatedpath/toshare
 read only = no
 writeable = yes
 browseable = yes
 guest ok = yes
[/INDENT]then issue the command **sudo restart smbd**

When connecting via SMB from OS X, (smb://ip.add.of.server) it pulls up the authentication dialog box and I enter the credentials however it tells me wrong username or password. I am positive that I am entering the credentials correctly. What am I missing?
Thank you!

---

### Post by cap10Ibraim on 2011-01-17
did your try the Guest user mode ?

---

### Post by ripeart on 2011-01-17
OK the issue was I had not set the samba password so I ran:

smbpasswd user

and I was able to authenticate, now however the error is that there was an error connecting to the server... 

please see image:

[http://img.waffleimages.com/37a8d85310804858fe9b577016ff80d08905b264/Screen%20shot%202011-01-17%20at%2012.41.24%20PM.png](http://img.waffleimages.com/37a8d85310804858fe9b577016ff80d08905b264/Screen%20shot%202011-01-17%20at%2012.41.24%20PM.png)

Thoughts?

---

### Post by Morbius1 on 2011-01-17
You created a share that allows guest access so the client should not be asking for any password. I'm a little rusty with share level security since no one living remembers how it works but I think you'll need to post your entire smb.conf:
```
testparm -s
```And just in case you're also using nautilus-share you should probably post the output of this as well:
```
net usershare info --long
```

---

### Post by cap10Ibraim on 2011-01-17
why you don't right click the folder and choose sharing options , 
it's smb too and you can  configure authentications

---

### Post by ripeart on 2011-01-17
Yes I tried to also share it through the GUI by right clicking the folder and configuring sharing options. Also, I configured the File Sharing system preference. Here's the output of testparm -s:

```
#
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[USHARE]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    workgroup = DOWNINGNET
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[USHARE]
    comment = USHARE
    path = /media/Vaio_Internal/UShare
    read only = No
    create mask = 0660
    directory mask = 0770
    guest ok = Yes


```And this is the output of the netshare command:

```

user@VAIO:/etc/samba$ net usershare info --long
info_fn: file /var/lib/samba/usershares/ushare is not a well formed usershare file.
info_fn: Error was Path is not a directory.

```Whats that error about?

---

### Post by Morbius1 on 2011-01-17
> [Torrents]
    comment = UShare
    path = /media/Vaio_Internal/UShare
    read only = No
    create mask = 0660
    directory mask = 0770
    guest ok = Yes
/media/Vaio_Internal/UShare an internal NTFS or FAT32 partition by any chance?

If it is this could be a Linux permissions problem and not a Samba problem. There's an easy fix if it is - just add the following line to the share definition:
```
force user = your-ubuntu-login-user-name
```Then restart samba:
```
sudo service smbd restart
```And if you also shared it through Nautilus that share will have to go. The share definitions between the two samba methods will now not be in sync and will conflict with one another. Just go back into Nautilus and undo the sharing process.
[B][COLOR=Blue]
EDIT:[/COLOR][/B] Didn't see your last edit. No need to unshare anything in Nautilus - your share didn't take.

---

### Post by ripeart on 2011-01-17
/media/Vaio_Internal/UShare an internal EXT3 formatted partition.

I added the force user line to the share definition even though the partition is not NTFS or FATx. No dice. Thanks for your help so far.

---

### Post by Morbius1 on 2011-01-17
Please post the output of this command:
```
ls -dl /media/Vaio_Internal/UShare
```

---

### Post by ripeart on 2011-01-17
> **Morbius1 said:**
> Please post the output of this command:
```
ls -dl /media/Vaio_Internal/UShare
```

OK, very odd, when I first ran that command I got 'No such file or directory'. I went to the GUI, Places, Computer, then the disk, saw it appear on the desktop and ran the command again:
[INDENT]drwxrwxrwx 5 user user 4096 2011-01-15 18:56 /media/Vaio_Internal/Ushare
[/INDENT]After that the share **is** mounting over SMB. I suppose the issue was the partition was not mounted to begin with. So there is something I have to do so that the partition automatically mounts on startup then? I'll Google that. Thank you for your help!

---

### Post by Morbius1 on 2011-01-17
We try to be a full service shop here so you could follow this as an example:

Unmount the partition you just mounted

Then run the following command:
```
sudo blkid -c /dev/null
```You'll get something like this:
> /dev/sdb3: LABEL="vmlin" UUID="e92eaf02-ff61-4db0-9397-35f1aadb98e8" TYPE="ext3"Then create a permanent mount point:
```
sudo mkdir /media/Data
```Then you would add a line to /etc/fstab that looks something like this:
```
/dev/sdb3 /media/Data ext3 defaults 0 2
```Save fstab and run the following command to test the new line and mount the new partition:
```
sudo mount -a
```You might have to redo permissions on the mount point:
```
sudo chmod 0777 /media/Data
```

---

### Post by ripeart on 2011-01-17
Just to tie up any loose ends for others who search this [I used this thread]("http://ubuntuforums.org/showthread.php?t=852842")  and added the following to the end of my /etc/fstab file.

/dev/sdb1 /media/Vaio_Internal ext4 defaults 0 0

EDIT: Just saw your post, thank you. I changed the last digit in the above line to a 2 and changed perms as per your instructions. Thank you! =)

---

### Post by ripeart on 2011-01-17
If making Ubuntu appealing to the masses is one of the aims of the developers, then editing an fstab file with config info from other commands cannot be the standard. The OS should work to do this automagically. Your average Windows/OSX user is going to be stumped with what I just did to get my share working.

Most people aren't going to be pulling and installing internal drives so I think its safe that the OS can automatically add an entry that would cause the drive to mount at startup.

Just a thought.

---

### Post by Morbius1 on 2011-01-17
> Most people aren't going to be pulling and installing internal drives so  I think its safe that the OS can automatically add an entry that would  cause the drive to mount at startup.Not to nit pick but you had an opportunity during the install process to do just that. Don't recall the step of where exactly it is in the install process and I think you have to click on an Advanced or Configure button somewhere but the installer will ask you 3 questions:

What partition do you want me to install from the shown list. - /dev/sdb1
Where do you want me to install it - /media/Vaio_Internal
Do you want me to reformat it - hell no

Ba da bing - you have an entry in fstab.

You may not like the default options it chooses but that's another matter.

---

### Post by Kreacher on 2011-01-17
Automount local drive - PySDM [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Get at [http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

