---
title: "Network access permissions."
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by jmail524 on 2008-11-28
I have a server running Ubuntu 8.10/Samba.  One of the server's partitions is setup to be shared over the network.  I have configured my desktop to connect to the server automatically during boot up.

My problem is that I can see the shared network drive but I can't write any files/folders to it.  I have tried using sudo chmod and sudo chown to change permissions but I get an error saying I don't have permission to change permissions of the network files/folders.

Any ideas. Your help is greatly appreciated.

Thanks.
Brian

---

### Post by cariboo on 2008-11-28
If you set the permissions of your share to be world readable by using the following command:

```
sudo chmod -R 777 /share
```

You should be able to access the share from anywhere on the network.

Jim

---

### Post by superprash2003 on 2008-11-28
maybe you havent told samba to allow writing.. have you added the shares manually to the smb.conf file?

---

### Post by jmail524 on 2008-11-28
Thanks for the replies.

**cariboo907:** "sudo chmod -R 777 /share" yields the response - "chmod: changing permissions of '/share': Permission denied"  (Yes I replaced the /share with the name of my shared path.)

**superprash2003:**  I checked the 'smb.conf' file and there is a line called 'writeable=yes'.  Also I tried changing it to 'writable=yes' since 'writeable' is incorrect English (although it is apparently accepted in computer terminology), but it made no difference.

If I create a folder in the shared drive on the server, I can change the permissions of that folder from my desktop.  However, I cannot create any folders from my desktop through the network and I cannot create any folders or files under the folder that I just changed permissions on.

The really weird thing is. I have two shared partitions which were setup identically and my other partition is not giving me any of these problems.

Thanks for the help.  I am willing to try any other suggestions you may have.

Brian

---

### Post by superprash2003 on 2008-11-29
after making changes, you need to restart samba, if it still doesnt work, posting your smb.conf may help

---

### Post by jmail524 on 2008-11-29
**superprash2003:**  After making changes to 'smb.conf', I used the command 'sudo /etc/init.d/samba restart' to restart samba. (I think that is how its done.)

Here is a copy of my 'smb.conf':
```
[global]
        workgroup = HOME
        server string = %h server (Samba, Ubuntu)
        log file = /var/log/samba/log.%m
        max log size = 1000
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
        dns proxy = no
        security = share
;       encrypt passwords = yes
;       guest ok = no
;       guest account = nobody

[recordings]
        path = /media/recordings
        writeable = yes
;       browseable = yes
        guest ok = yes
        comment = TV Recordings

[media]
        comment = Audio/Video Files
        path = /media/media
        writeable = yes
;       browseable = yes
        guest ok = yes

[archive]
        comment = Shared Network Archive
        path = /media/archive
        writeable = yes
;       browseable = yes
        guest ok = yes
```

All of the shared partition are XFS if that makes any difference.

Thanks.
Brian

---

### Post by jmail524 on 2008-11-30
A little more info.

If I create a folder under a normal users credentials on my server and then change the permissions of that folder, I can then create a file or folder through the network on my client computer.  However, I don't have the permission to alter/delete the file or folder I have created until I run 'chmod -R 777 folder/file'.

If I create folders or files under the network browser in Gnome (Places/Network/etc...), I can read and write without any permission issues.

Thanks.
Brian

---

