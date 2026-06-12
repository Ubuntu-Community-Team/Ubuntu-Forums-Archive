---
title: "Samba Permission issues - Local or Samba?"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by plonka2000 on 2008-09-17
Hi all,
I'm having some issues with my SMB shares that I have created for the raid volume on my newly built server.
The array has been created and works fine, however, the shares are inaccessible from my Windows client.

I have run **ls -al** from various locations as I suspect its a local permission AND samba issue rather than simply samba.
From my experience managing Windows shares, I am always prudent to make sure that my local permissions reflect what I need to do via sharing. However, its a little more complicated using Linux, so I would really like some help.

FYI: My RAID5 is mounted from **_/dev/md0_** as **_/raid_**.
Here are my ls -al outputs from various locations:

From /
```
root@soundwave:/# ls -al
total 84
drwxr-xr-x 22 root root  4096 2008-09-16 18:09 .
drwxr-xr-x 22 root root  4096 2008-09-16 18:09 ..
drwxr-xr-x  2 root root  4096 2008-09-15 05:33 bin
drwxr-xr-x  3 root root  4096 2008-09-15 17:12 boot
lrwxrwxrwx  1 root root    11 2008-09-15 04:26 cdrom -> media/cdrom
drwxr-xr-x 12 root root 14140 2008-09-16 18:31 dev
drwxr-xr-x 67 root root  4096 2008-09-17 00:05 etc
drwxr-xr-x  3 root root  4096 2008-09-15 05:01 home
drwxr-xr-x  2 root root  4096 2008-09-15 04:28 initrd
lrwxrwxrwx  1 root root    32 2008-09-15 13:11 initrd.img -> boot/initrd.img-2.6.24-19-server
lrwxrwxrwx  1 root root    32 2008-09-15 04:35 initrd.img.old -> boot/initrd.img-2.6.24-16-server
drwxr-xr-x 12 root root  4096 2008-09-16 00:33 lib
lrwxrwxrwx  1 root root     4 2008-09-15 04:27 lib64 -> /lib
drwx------  2 root root 16384 2008-09-15 04:26 lost+found
drwxr-xr-x  3 root root  4096 2008-09-15 04:26 media
drwxr-xr-x  2 root root  4096 2008-04-15 06:53 mnt
drwxr-xr-x  2 root root  4096 2008-09-15 04:28 opt
dr-xr-xr-x 80 root root     0 2008-09-16 18:31 proc
drwxr-xr-x  3 root root    19 2008-09-17 00:14 raid
drwxr-xr-x  2 root root  4096 2008-09-16 22:07 root
drwxr-xr-x  2 root root  4096 2008-09-16 00:33 sbin
drwxr-xr-x  2 root root  4096 2008-09-15 04:28 srv
drwxr-xr-x 12 root root     0 2008-09-16 18:31 sys
drwxrwxrwt  3 root root  4096 2008-09-16 22:07 [COLOR="Lime"]tmp[/COLOR]
drwxr-xr-x 10 root root  4096 2008-09-15 04:28 usr
drwxr-xr-x 14 root root  4096 2008-09-16 22:07 var
lrwxrwxrwx  1 root root    29 2008-09-15 13:11 vmlinuz -> boot/vmlinuz-2.6.24-19-server
lrwxrwxrwx  1 root root    29 2008-09-15 04:35 vmlinuz.old -> boot/vmlinuz-2.6.24-16-server
```

From /raid
```
root@soundwave:/raid# ls -al
total 8
drwxr-xr-x  4 root root   31 2008-09-17 10:02 .
drwxr-xr-x 22 root root 4096 2008-09-16 18:09 ..
drwxr-xr-x  2 root root    6 2008-09-17 10:02 media
drwxrwxrwx  2 root root 4096 2008-09-17 00:26 [COLOR="Lime"]public[/COLOR]
```

FYI: I'm using Webmin to try and simplify my SMB management, but it doesnt seem right still. Here is the tail end of my /etc/samba/smb.conf
```
[public]
comment = Public Folder
writeable = yes
public = yes
invalid users = 
path = /raid/public


[homes]

[media]
read list = nobody
public = yes
path = /raid/media
write list = kareem
```

If anyone can help, please do, or by all means ask for any other info which I can provide.

Thanks.

---

### Post by plonka2000 on 2008-09-17
Bumper.

Can anyone help?
This is driving me crazy... I browse to the machine (from windows) and cannot access my shares (Tells me to check permissions but I think its more of a general error for not being able to access a share).

I think my problem does lie in permissions though, either local disk or SMB.

---

### Post by plonka2000 on 2008-09-17
Bump

---

### Post by plonka2000 on 2008-09-17
Can anyone help with this?

I think I'm soon to lose my sanity over something which I'm sure is quite simple.

---

### Post by robgolding63 on 2008-09-17
Sorry I took so long - here's some info about my setup to help you diagnose the issue:

**ls -al** in the /mnt directory - where all my extra stuff is mounted:
```

rob@vhost:/mnt$ ls -al
total 32
drwxrwxrwx  1 root root 4096 2008-09-17 00:30 Backup
drwxrwxrwx  3 root root 8192 2008-09-06 13:57 Data
drwxrwxrwt  8 root root   77 2008-08-31 19:41 VMs

```
Backup is the mountpoint for my external USB drive. All permissions within are 777. I know this isn't ideal, but for finding your issue it may be prudent to try it, then try changing it back to be more restrictive once it's working.

Relevant smb.conf section:
```

[Backup]
comment = Backup Drive
browseable = yes
writeable = yes
path = /mnt/Backup
valid users = rob backup
guest ok = no

```
Try a config similar to that, and see where it gets you.

Good luck!

Rob

---

### Post by plonka2000 on 2008-09-17
Hey Rob,
I applied the same settingsbut to no avail.

My /dev/md0 is mounted as /raid in my system

I have run **chmod 777** on /raid and all folders inside my volume after mounting but still i cant seem to get my share to access from windows.
I'm using these settings as your advice:

[backup]
comment = Backup Drive
browseable = yes
writeable = yes
path = /raid/media
valid users = kareem backup
guest ok = no

I've managed to create 1 share that works and is accessible to all, but its not helpful considering its writable by anyone.
The settings for that are:

[public]
writable = yes
writeable = yes
invalid users = 
path = /raid/public
comment = Public Folder
public = yes
available = yes

Still testing, its been like a day of getting this SMB to work now... :(

Here is my permissions dump:
```
root@soundwave:/raid# ls -al
total 8
drwxrwxrwx  4 root root   31 2008-09-17 10:02 .
drwxr-xr-x 23 root root 4096 2008-09-17 22:30 ..
drwxrwxrwx  7 root root   68 2008-09-17 23:15 media
drwxrwxrwx  3 root root 4096 2008-09-17 22:36 public
```

Thanks for your help.

---

### Post by plonka2000 on 2008-09-17
Here is a further dump from inside the /raid/media dir:

```
root@soundwave:/raid/media# ls -al
total 0
drwxrwxrwx 7 root root 68 2008-09-17 23:15 .
drwxrwxrwx 4 root root 31 2008-09-17 10:02 ..
drwxrwxrwx 2 root root  6 2008-09-17 21:33 movies
drwxrwxrwx 2 root root  6 2008-09-17 21:33 music
drwxrwxrwx 2 root root  6 2008-09-17 23:14 new1
drwxrwxrwx 2 root root  6 2008-09-17 23:15 new2
drwxrwxrwx 2 root root  6 2008-09-17 21:34 pictures
```

The really annoying thing is, I constantly get the error (attached) about permissions!

---

### Post by gregphil on 2008-09-17
Did you remember to set the password for kareem in samba?

smbpasswd -a kareem
password
password

---

### Post by plonka2000 on 2008-09-18
> **gregphil said:**
> Did you remember to set the password for kareem in samba?

smbpasswd -a kareem
password
password

That appears to have fixed it! :)
Thanks mate!

Now I'm a little confised about this, mostly because I'm using webmin, and according to the webmin docs, it should have worked fine for setting up my smb passwords.

So the correct syntax is as stated? I'll keep that one in mind.

I'm considering writing my own howto on how to setup ubuntu(on usb)+smb+webmin+mdadm+vmware as I've been piecing together tips from all over the place to be sure I'm doing this correctly.

Thanks!

---

