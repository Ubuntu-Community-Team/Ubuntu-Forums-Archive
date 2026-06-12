---
title: "A script run as SUID for sshfs - what am I doing wrong?"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by bernied on 2007-03-31
Can someone explain why the SUID bit is not behaving the way I expect it to here?

I have a script (sshmount) for connecting directories on a networked storage device (slug2) on my home network (myhome.homeip.net - this is a dynamic DNS name) to a server on a rented virtual machine (vserver). I have set the SUID bit on the script:
```
bernie@vserver:/usr/local/bin$ ls -alh ssh*
-rw**s**r-xr-x 1     **vserver** staff     345     Mar 31 11:55      sshmount
bernie@vserver:/usr/local/bin$ **cat sshmount**
#!/bin/bash
echo 'Mounting ssh filesystems...'
sshfs -o ro,allow_other vserver@myhome.homeip.net:/share/Music /mnt/slug2/Music/
sshfs -o umask=0,allow_other vserver@myhome.homeip.net:/share/vserver /mnt/slug2/vserver/
mount | grep sshfs
```So the script tries to mount the two directories using sshfs, then lists any sshfs mounts.

I'm expecting that because the SUID bit is set, the script will be run as user vserver, for which public/private key authentication is set up between vserver and slug2, without any passphrase on the key. But, different authentication seems to be used depending on who runs the script:
```
**vserver**@vserver:/home/bernie$ sshmount                          # running as user vserver
Mounting ssh filesystems...
sshfs#vserver@myhome.homeip.net:/share/Music on /mnt/slug2/Music type fuse (ro,nosuid,nodev,allow_other,max_read=65536,user=vserver)
sshfs#vserver@myhome.homeip.net:/share/vserver on /mnt/slug2/vserver type fuse (rw,nosuid,nodev,allow_other,max_read=65536,user=vserver)

# all goes well, the directories are mounted

**bernie**@vserver:~$ sshmount                         # running as user bernie
Mounting ssh filesystems...
Enter passphrase for key '/home/bernie/.ssh/id_rsa':
fusermount: user has no write access to mountpoint /mnt/slug2/Music
Enter passphrase for key '/home/bernie/.ssh/id_rsa':
fusermount: user has no write access to mountpoint /mnt/slug2/vserver
```
So this time the script seems to be running as user bernie (not enough permissions on those mountpoints) and sshfs seems to be authenticating using bernie's key, because the key for bernie needs a passphrase. I set it up like this because vserver has very limited permissions on both vserver and slug2, so I don't mind it not having a passphrase, but bernie is quite privileged, and I'm not happy giving bernie a key without a passphrase because I don't fully trust the security on this rented server. In fact I'd rather user bernie could not get from vserver to slug2 at all.

Does anyone know where I am going wrong? Is the script running as user vserver or not? Is there perhaps an environment variable that needs to be set?

---

### Post by bernied on 2007-04-01
Solved!

Apparently [linux does not support suid on scripts](http://www.linuxquestions.org/questions/showthread.php?p=2681990#post2681990). I don't know this for sure but it would explain the behaviour. 

So, instead I used sudo, like this:
```
bernie@vserver:/usr/local/bin$ ls -alh ssh*
-rwxr-x--- 1 root staff 425 Apr  1 19:01 sshmount

bernie@vserver:/usr/local/bin$ cat sshmount
#!/bin/bash
# sshmount - simple script to mount ssh shares.
echo 'Mounting ssh filesystems...'
sudo -u vserver sshfs -o ro,allow_other vserver@myhome.homeip.net:/share/Music /mnt/slug2/Music/
sudo -u vserver sshfs -o umask=0,allow_other vserver@myhome.homeip.net:/share/vserver /mnt/slug2/vserver/
mount | grep sshfs

bernie@vserver:/usr/local/bin$ sudo cat /etc/sudoers
Password:
--- snipped ---
# This one so that sshfs can be used as user vserver by anyone
ALL     ALL=(vserver) NOPASSWD: /usr/bin/sshfs

bernie@vserver:/usr/local/bin$ sshmount
Mounting ssh filesystems...
sshfs#vserver@murieston.homeip.net:/share/Music on /mnt/slug2/Music type fuse (ro,nosuid,nodev,allow_other,max_read=65536,user=vserver)
sshfs#vserver@murieston.homeip.net:/share/vserver on /mnt/slug2/vserver type fuse (rw,nosuid,nodev,allow_other,max_read=65536,user=vserver)

```
So, now any user that can execute the script (in group staff) can mount the directories as user vserver.

---

