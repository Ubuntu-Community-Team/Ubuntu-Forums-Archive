---
title: "NAS Mount to UBUNTU - Read Only"
date: 2024-09-27
forum: Networking &amp; Wireless
---

### Post by srutx47 on 2024-09-27
So I got the mount to work, but it is the RedHat syntax and there is no rights in the syntax... so I know that has something to do with it.  

the problem is I cannot mount without SUDO or at root, and even at those levels I cannot change the mod or the owner or group.  I have checked the NAS and the credentials I used to mount are full admin.  Now I was able to change these settings in the past, yet that was a different mount syntax... but regardless.  There is still something wrong with this newest version of UBUNTU since I NEVER had this issue in the past... just after that upgrade and patches... Now I am up that creek without one of those paddles... So let's just throw out everything we know about Linux and flip a coin to see how to fix this... OR Ubuntu can relook at their upgrade and fix the quirks that are obviously there.

I just saying...

---

### Post by TheFu on 2024-09-28
What is "RedHat syntax"?  Never heard that term in 30 yrs of dealing with NAS devices.
Also, which protocol is your client and server using to connect to the NAS.  

What is the file system on the NAS?  NTFS doesn't support chmod/chgrp/chown commands, regardless of the file sharing protocol used.

NFS with ext4 (or other native Linux file system) will support chown, chmod, chgrp commands.  However, chown is a root command and root access from the client isn't allowed by default.  The owner needs to be changed directly on the NAS server - or you could allow any remote root id to have full control, but that's a huge, huge, huge, security issue with NFS. Best not to do it, but there is an option in the NFS "exports" file to allow it.

---

### Post by Morbius1 on 2024-09-28
>  So I got the mount to work, but it is the RedHat syntax and there is no rights in the syntax... so I know that has something to do with it. 

Always interested in how others do this sort of thing so I looked at the Red Hat documentation and found this:
> 9.2.2. Manually Mounting an SMB Share
To manually mount an SMB share, use the mount utility with the -t cifs parameter:

[QUOTE]mount -t cifs -o username=user_name //server_name/share_name /mnt/
Password for user_name@//server_name/share_name:  ********[/QUOTE]

Yep, that ain't gonna work. Well, ... it will work but unless you are root you only have read access to the mounted share.

You are going to have to at least take possession of the mount:
> mount -t cifs -o username=user_name**[COLOR="#B22222"],uid=srutx47[/COLOR]** //server_name/share_name /mnt/

I would also choose a subdirectory ot /mnt instead of /mnt itself but that's just me.

---

### Post by srutx47 on 2024-09-29
As i mentioned in my last post (a separate one) The NAS I have (Buffalo Drive) does not support NFS.  I understand your passion but NFS is not something every device supports, and I am a fan of NFS.  Also RedHat Syntax means it works for my RedHat install.  Also, in the past on this very laptop before the 20.04 update, I was able to chmod chgrp and chown for this very share.  So, again either I am missing some syntax or some variable in no mount statement, OR the update and patches screwed up far more items that I first found.

The command I entered that mounted the drive:  ```
sudo mount -t cifs -o user=username,vers=1.0 //192.168.1.195/wilshare /mnt/NetShare
```

Mount should not have changed with the update, but I cannot seems to get this mount to function as it once did.  I need the RW function so I will continue to research unless someone may have the solution.

---

### Post by srutx47 on 2024-09-29
I will check into this and try it out.  Thanks!

---

### Post by srutx47 on 2024-09-29
I need to add a line in FSTAB from the error:

```
mount.cifs: permission denied: no match for /mnt/NetShare found in /etc/fstab
```

I will look into the proper syntax for that. I will post the results.

---

### Post by srutx47 on 2024-09-29
Well I added the FSTAB entry - now I get permission denied.  lovely!

```
[179415.677576] r8169 0000:01:00.0:    [ 0] RxErr                  (First)[179416.536078] CIFS: Attempting to mount //192.168.1.195/wilshare
[179416.542071] CIFS: VFS: cifs_mount failed w/return code = -22
[179418.220505] pcieport 0000:00:1c.0: AER: Multiple Correctable error message received from 0000:01:00.0



```

---

### Post by srutx47 on 2024-09-29
fix the error but the mount is still read only.

---

### Post by Morbius1 on 2024-09-30
Install nmap:
```
sudo apt install nmap
```
Then run this command to find out what "dialects" of smb the NAS is running and post the results:
```
nmap -Pn --script smb-protocols 192.168.1.195
```

---

### Post by him610 on 2024-09-30
Does your Buffalo NAS happen to have DD-WRT NXT preinstalled?

---

### Post by srutx47 on 2024-10-01
Not sure.. but it used to work perfectly before the upgrade and updates.

---

### Post by srutx47 on 2024-10-05
From what I have read so far, the [COLOR=#000000]DD-WRT NXT with buffalo technologies is on their wireless routers... I have yet to find anything about their storage NAS devices.[/COLOR]

---

### Post by srutx47 on 2024-10-05
According to Buffalo... DD-WRT NXT is not for their drives but wireless routers...

---

