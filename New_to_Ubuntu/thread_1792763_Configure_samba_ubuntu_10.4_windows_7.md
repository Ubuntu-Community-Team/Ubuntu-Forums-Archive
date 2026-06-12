---
title: "Configure samba ubuntu 10.4 windows 7"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by Floepsa on 2011-06-28
Hello,

I have created an server from an old pc we have at home. I tried to install samba on it using this tutorial: [http://www.youtube.com/watch?v=deb2jRm3c7g](http://www.youtube.com/watch?v=deb2jRm3c7g). I left everything exactly the same but when i try to find it on windows 7 using map network drive, i enter: //192.168.0.100/my_share but it cannot find it. Does someone lknow what the problem is?

Thank you very much, Floepsa.

---

### Post by texaco on 2011-06-28
If your windows machine can't find your share folder, it could be a connectivity trouble.

Can you ping from the client to the samba server?

just try:
```
ping 192.168.0.100
```

It's working, then you could try gain access from your samba server.

check man page for smbclient.

Then try from client, in run dialog type \\192.168.0.100 and you must see a list of shares resources.

P.D.: Beautiful... videotutorial.

---

### Post by Morbius1 on 2011-06-28
First, can your server see it's own share? This command will list all the shares on your network:
```
smbtree
```
You are probably going to have to install smbclient since servers don't normally have it installed by default.

Second, How is your server interpreting your smb.conf file? The following command will tell us that:
```
testparm -s
```

---

### Post by Floepsa on 2011-06-28
> **Morbius1 said:**
> First, can your server see it's own share? This command will list all the shares on your network:
```
smbtree
```You are probably going to have to install smbclient since servers don't normally have it installed by default.

Second, How is your server interpreting your smb.conf file? The following command will tell us that:
```
testparm -s
```

**I get then:**

WORKGROUP
    \\RUUD-DESKTOP           ruud-desktop server (Samba, Ubuntu)
        \\RUUD-DESKTOP\IPC$               IPC Service (ruud-desktop server (Samba, Ubuntu))
        \\RUUD-DESKTOP\print$             Printer Drivers
        \\RUUD-DESKTOP\Myshare            Myshare

[B]And the testparm -s:
[/B]
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[Myshare]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[Myshare]
    comment = Myshare
    path = /myshare
    read only = No
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers



I hope u know the problem now


EDIT: And another question, i want to hibernate the server while in lockscreen but i cant do that..

---

### Post by Morbius1 on 2011-06-28
You are typing in "my_share" in Windows but the share name is "Myshare" 

That would be my first guess.

---

### Post by Floepsa on 2011-06-28
> **Morbius1 said:**
> You are typing in "my_share" in Windows but the share name is "Myshare" 

That would be my first guess.


Thank You! :D that totally worked, now i have 1 more question because i have an external hardrive connected to the computer. How can i share that?

---

### Post by Morbius1 on 2011-06-28
That can get tricky.

How is the external drive formatted? NTFS, ext3, ...?

How is it mounted? fstab? Do you boot into the server and then turn on the drive?

Do you log into the server as a regular user?

---

### Post by Floepsa on 2011-06-28
> **Morbius1 said:**
> That can get tricky.

How is the external drive formatted? NTFS, ext3, ...?

How is it mounted? fstab? Do you boot into the server and then turn on the drive?

Do you log into the server as a regular user?

I dont know, i think it is NTFS. It is an 320 gb WD passport. 

Its connected with USB and i didnt do nothing more to it. The location is /etc/media/

---

### Post by Morbius1 on 2011-06-28
Here's the problem with an external NTFS usb drive. In a normal network where everyone is sharing something with someone else and someone wants to share an external drive you would simply create a share that looks like this:
> [Extshare]
path = /media/whatever
read only = No
    guest ok = Yes
force user = myusernameIt looks just like your other share except it has a "force user" line added.

An external usb ntfs formatted drive will automatically boot when turned on to have the login user as owner and with access permissions only to him ( in this case "myusername" ). The remote user is a guest and is not "myusername" so access is denied. The force user makes the remote user appear to be you for that share and everything works.

[COLOR=Blue]**But**[/COLOR],  you would have to login to the server with a real user name ( myusername ) and turn on the usb drive for this to work.

The alternative is to have the usb device auto mount to allow guest access by adding a line in fstab but then you would have to make sure that the usb device is turned on before the server boots.

---

### Post by Floepsa on 2011-06-28
> **Morbius1 said:**
> Here's the problem with an external NTFS usb drive. In a normal network where everyone is sharing something with someone else and someone wants to share an external drive you would simply create a share that looks like this:
It looks just like your other share except it has a "force user" line added.

An external usb ntfs formatted drive will automatically boot when turned on to have the login user as owner and with access permissions only to him ( in this case "myusername" ). The remote user is a guest and is not "myusername" so access is denied. The force user makes the remote user appear to be you for that share and everything works.

[COLOR=Blue]**But**[/COLOR],  you would have to login to the server with a real user name ( myusername ) and turn on the usb drive for this to work.

The alternative is to have the usb device auto mount to allow guest access by adding a line in fstab but then you would have to make sure that the usb device is turned on before the server boots.


I have added the line force user = ruud to the share, but if i want to connect i can sign in but then i get another text box to again sign in. Then another and then another and then i get the pop-up: The mapped network drive could noet be created because the following error has occurred: The specified server cannot perform the requested operation.

---

### Post by Morbius1 on 2011-06-28
You created a guest share with "force user" so no one should have to log in. Post the output of "terparm -s" again please.

While you at it post the output of this as well:
```
mount
```

---

### Post by Floepsa on 2011-06-29
> **Morbius1 said:**
> You created a guest share with "force user" so no one should have to log in. Post the output of "terparm -s" again please.

While you at it post the output of this as well:
```
mount
```

I think you mean testparm?

This is the output:

```
[global]
    server string = %h server (Samba, Ubuntu)
    security = SHARE
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[Myshare]
    comment = Myshare
    path = /myshare
    read only = No
    guest ok = Yes

[Ruud]
    comment = Ruud
    path = /media/Ruud
    force user = ruud
    read only = No
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

```

The [Ruud] is the share of the USB harddisk.

And with mount i get:
```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ruud/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ruud)
/dev/sda1 on /media/C29058B79058B39F type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1 on /media/Ruud type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

---

### Post by Morbius1 on 2011-06-29
That all looks good to me.

What's the permissions on the target folder:
```
ls -al /media/Ruud
```

BTW, Does running the following command produce any output:
```
net usershare info --long
```

---

### Post by Floepsa on 2011-06-29
> **Morbius1 said:**
> That all looks good to me.

What's the permissions on the target folder:
```
ls -al /media/Ruud
```BTW, Does running the following command produce any output:
```
net usershare info --long
```

```

total 32
drwx------ 1 ruud ruud  4096 2011-06-23 21:31 .
drwxr-xr-x 4 root root  4096 2011-06-28 22:25 ..
drwx------ 1 ruud ruud  4096 2011-06-28 19:07 Downloads
drwx------ 1 ruud ruud 12288 2011-05-22 16:19 Films
drwx------ 1 ruud ruud     0 2011-06-08 16:58 Laptop
drwx------ 1 ruud ruud     0 2011-06-08 20:17 $RECYCLE.BIN
drwx------ 1 ruud ruud     0 2011-06-08 16:58 RECYCLER
drwx------ 1 ruud ruud  4096 2011-04-20 16:58 Series
drwx------ 1 ruud ruud  4096 2011-06-08 20:17 System Volume Information
drwx------ 1 ruud ruud     0 2011-06-23 21:31 .Trash-1000

```

When i type in: net usershare info --long, nothing happens. I only get a next command line

---

### Post by Morbius1 on 2011-06-29
All of that is textbook correct. I have no idea why the Client keeps getting prompted for a credentials.

The only set of circumstances that would cause a Windows client to prompt for a username and password for a guest share is:

* You have the same user name on both Windows and Linux
* [COLOR=Blue]And[/COLOR] you created a samba password for the Linux user
* [COLOR=Blue]And[/COLOR] that samba password does not match the Windows user's password.

Even if you did all that it would be happening to the Myshare share as well as the Ruud share.

---

### Post by Floepsa on 2011-06-29
Maybe i'm entering the map network drive wrong, what must it be exactly?

---

### Post by Morbius1 on 2011-06-29
The same way you did it before:
\\192.168.0.100\Ruud

BTW, after you edited smb.conf you did restart samba right?
```
sudo service smbd restart
```

---

### Post by Floepsa on 2011-06-29
It finally works, i entered //192.168.0.100/media/Ruud instead of //192.168.0.100/Ruud. 

Thank you for your help!

---

### Post by Morbius1 on 2011-06-29
> **Floepsa said:**
> It finally works, i entered //192.168.0.100/media/Ruud instead of //192.168.0.100/Ruud. 
That cannot be. Sorry, let me rephrase that. I have no doubt that it works for you but that cannot be.

When you "map a network drive" from windows the syntax is:
```
\\server\share
```It even tells you that in the dialog box - see attachement.

Forgetting that in your post the slashes are in the wrong direction what you did was:
```
\\server\path-to-shared-folder
```The only way that would have worked is if you shared /media itself which smb.conf does not show.

So if somebody can explain to me why this works I would appreciate it.

---

### Post by Floepsa on 2011-07-06
Sorry, my english is not very good. What i meant in my last post was that \\192.168.0.100\Ruud worked instead of what i entered before that.

But next to that, the samba share works very slow for me. I get around 800 kb/s. The computer is quite old, with only 800 mhz but i think that i could reach a speed limit around 5 mb/s. If i want to watch a video it pauses all the time to buffer. Does anyone how i can fix that?

---

