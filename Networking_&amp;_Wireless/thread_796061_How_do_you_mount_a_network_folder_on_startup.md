---
title: "How do you mount a network folder on startup?"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by cj1976 on 2008-05-16
Hi all,

I'm running Ubuntu 7.10 as a guest OS in VirtualBox. I am using Vista as a host. I have managed to set up the network connections so I can access my Windows shared folder in Ubuntu, but I have to manually connect every time I run the OS. Is it possible to mount the folder so I can access it straight away?
I want to use Amarok for my music and F-Spot, but it won't let me access Network folders.

---

### Post by .nedberg on 2008-05-16
Use /etc/fstab

add a line for the share, have a look at this [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

This is the interesting part:
```
cifs still uses a credentials file to avoid the need to enter a password. If you do not use a credentials file, you will mount a samba share with sudo and enter your username and password in a terminal.

Quote://Server/share /mnt/samba cifs users,auto,credentials=/path/credentials_file,noexec 0 0 

Server = Name (if in /etc/hosts) or IP Address of samba server.
share = Name of shared directory (folder).
/mnt/samba = your desired mount point.
/path/credentials_file = full path to your credentials file. A credentials file should be owned by root (permissions 400) and contain two lines :

username = samba_user
password = samba_user_password 

samba_user = samba user (on server).
samba_user_password = samba user password (on server).
noexec for security (it can be bypassed ...).

smbfs : depreciated, but similar.

Quote://win_box/shared_folder /mnt/samba smbfs rw,credentials=/home/user_name/winbox-credentials.txt 0 0
```

the option 'auto' makes it mount at boot (at least it works for me)

---

### Post by billcondie on 2008-06-12
Running 8.0b with VirtualBox 1.62 and XP Pro.

I've set Desktop as shared folder,but can't seem to mount it.

I tried your tip but get this:
[B]
root@bill-laptop:/home/bill# /etc/fstab
bash: /etc/fstab: Permission denied
[/B]

---

### Post by .nedberg on 2008-06-12
You need to edit that file as root

```
sudo nano /etc/fstab
```

then type your password

---

### Post by Cybie257 on 2008-06-13
I think the last reply missed that you were in root already, therefore the sudo will not help, but what will is that you need to type the following:

"nano /etc/fstab"  (you forgot the nano)

What you had typed was actually trying to execute the file, which is not an executable (by default at least)

Hope this helps :)

-Cybie

PS--> BE SURE to backup the fstab file before editing it. IE: cp fstab fstab.bak

> **billcondie said:**
> Running 8.0b with VirtualBox 1.62 and XP Pro.

I've set Desktop as shared folder,but can't seem to mount it.

I tried your tip but get this:
[B]
root@bill-laptop:/home/bill# /etc/fstab
bash: /etc/fstab: Permission denied
[/B]

---

