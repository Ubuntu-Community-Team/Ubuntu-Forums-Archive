---
title: "credentials file can't be that hard"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by theozzlives on 2009-05-23
this is whats in my fstab:
```
//192.168.1.3/e-books /home/ozzie/E-Books cifs users,auto,credentials=/home/ozzie/.creds,noexec 0 0
```

Here's my file:
```
username=ozzie
password=password
```

It don't work!!!

---

### Post by kellemes on 2009-05-23
Seems to be correct syntax..
What message are you getting at mount?

---

### Post by MrWES on 2009-05-23
> **theozzlives said:**
> this is whats in my fstab:
```
//192.168.1.3/e-books /home/ozzie/E-Books cifs users,auto,credentials=/home/ozzie/.creds,noexec 0 0
```

Here's my file:
```
username=ozzie
password=password
```

It don't work!!!

What are the perms of the .creds file? Mine are 600. Also you might want to add _netdev right after the .creds entry. It makes sure there is a network connection before attempting to mount.

Bill

---

### Post by theozzlives on 2009-05-24
> **kellemes said:**
> Seems to be correct syntax..
What message are you getting at mount?

It's in the fstab, it should mount at boot, I don't see a message.

---

### Post by theozzlives on 2009-05-24
> **MrWES said:**
> What are the perms of the .creds file? Mine are 600. Also you might want to add _netdev right after the .creds entry. It makes sure there is a network connection before attempting to mount.

Bill

It works when I use my username and password in the fstab itself.

---

### Post by MrWES on 2009-05-24
> **theozzlives said:**
> It's in the fstab, it should mount at boot, I don't see a message.

After boot up, from a terminal type
```
dmesg | tail
```

See if there are any errors messages about mounting the cifs share.

Bill

P.S. Please rearrange your fstab entry as follows, putting the creds entry up front:

```
//192.168.1.3/e-books /home/ozzie/E-Books cifs credentials=/home/ozzie/.creds,users,auto,noexec 0 0
```

---

### Post by kellemes on 2009-05-24
> **theozzlives said:**
> It's in the fstab, it should mount at boot, I don't see a message.

```
sudo mount -a
```
mounts all devices based on fstab, could be you get some info when it tries to mount your cifs-device.

---

### Post by theozzlives on 2009-05-24
[   20.432013] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.432019] pci 0000:00:02.0: setting latency timer to 64
[   20.432153] pci 0000:00:02.0: irq 2298 for MSI/MSI-X
[   20.432258] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   20.434507] [drm:i915_setparam] *ERROR* unknown parameter 4
[   22.382189] sky2 eth0: enabling interface
[   22.382429] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.432069] eth1: no IPv6 routers present
[   69.046309]  CIFS VFS: No username specified
[   69.046315]  CIFS VFS: cifs_mount failed w/return code = -22

---

### Post by theozzlives on 2009-05-24
ozzie@ozzie-laptop:~$ sudo mount -a
[sudo] password for ozzie: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.3/e-books,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by MrWES on 2009-05-25
> **theozzlives said:**
> ozzie@ozzie-laptop:~$ sudo mount -a
[sudo] password for ozzie: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.3/e-books,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Did you try moving your creds entry in the fstab like I posted?

~Bill

---

### Post by Paqman on 2009-05-25
> **MrWES said:**
> What are the perms of the .creds file? Mine are 600.

That would be the first place i'd look too. You need it to be readable by root. If the permissions in your home prevent this then it won't work. Personally i'd stick it in root's home not my own, but I don't suppose it matters if the permissions are ok.

Also, just to be sure: you've installed smbfs, yes?

---

### Post by kellemes on 2009-05-25
I have permissions set at 600 (-rw-------), placed in /etc
Works for me..

---

### Post by theozzlives on 2009-05-25
> **MrWES said:**
> Did you try moving your creds entry in the fstab like I posted?

~Bill

yes

---

### Post by theozzlives on 2009-05-25
> **kellemes said:**
> I have permissions set at 600 (-rw-------), placed in /etc
Works for me..

my permissions are 600, it's just in my home... I'll try moving it to roots home.

---

### Post by theozzlives on 2009-05-25
My line now looks like this:
```
//192.168.1.3/e-books /home/ozzie/E-Books cifs credentials=/root/.creds,users,auto,noexec 0 0
```

My .creds file has 600 permissions and is in /root

It still don't work, I'm tempted just to have my password in the fstab.

---

### Post by Paqman on 2009-05-25
Have you double-checked the file for spelling mistakes? I've spent ages trying to fault-find this exact problem and it turned out to just be a typo in the credentials file.

---

### Post by kellemes on 2009-05-25
This is mine..
```
//IP-OF-SERVER/docs /mnt/syn_docs cifs user,uid=500,rw,suid,credentials=/etc/cred.txt 0 0
```

As said, Credentials-file has permissions 600.

---

### Post by Baelus on 2009-05-25
Just to check. Is "mount.cifs" available as a command on the command line? i.e. smbfs has been installed?

---

### Post by theozzlives on 2009-05-25
> **Baelus said:**
> Just to check. Is "mount.cifs" available as a command on the command line? i.e. smbfs has been installed?

I thought smbfs was installed, but apparently that changed when I made the move to Jaunty. I have a new problem, I shut down and get that Server not found error (which I can live with) it then locks up. I push the power once and  it locks up at Apache MPM not installed, I have to hold the power down to kill the machine. Do I need to install smbfs on my server???

---

### Post by Paqman on 2009-05-26
Have a look at some of the fault-finding stuff on [this thread]("http://ubuntuforums.org/showthread.php?t=288534"). There's a lot of good stuff there, and it's always cleared the shutdown bug for me.

---

### Post by dmizer on 2009-05-26
Just for future reference, the credentials file needs a blank line at the end. If you use the CLI editor nano, this line is automatically created for you. VI does not create it, nor do any of the GUI text editors. GUI text editors also leave behind bits that make the file unreadable to fstab as well.

---

### Post by kellemes on 2009-05-26
> **dmizer said:**
> Just for future reference, the credentials file needs a blank line at the end. If you use the CLI editor nano, this line is automatically created for you. VI does not create it, nor do any of the GUI text editors. GUI text editors also leave behind bits that make the file unreadable to fstab as well.

Just checked mine, made with vi, no blank line at the end, still works fine.

---

### Post by dmizer on 2009-05-26
> **kellemes said:**
> Just checked mine, made with vi, no blank line at the end, still works fine.

Dunno, if it's not a problem now, it certainly used to be: [http://ubuntuforums.org/showpost.php?p=1769217&postcount=89](http://ubuntuforums.org/showpost.php?p=1769217&postcount=89)

---

### Post by Baelus on 2009-05-26
> **Paqman said:**
> Have a look at some of the fault-finding stuff on [this thread]("http://ubuntuforums.org/showthread.php?t=288534"). There's a lot of good stuff there, and it's always cleared the shutdown bug for me.

Under the "Troubleshooting" heading, the "CIFS VFS: Server not responding" section worked for me.

Although the "K15umountnfs.sh" link was named something like "S23umountnfs.sh". I renamed the two files and shutdown went smoothly.

---

### Post by theozzlives on 2009-05-27
Well I give up! I've tried everything I could think of. The problem seems to be with smbfs. Now I can either:

1. Live with the problem.
2. Go back to having my username and password in the fstab.
3. just use my server for web and backups. Copy everything back to my laptop.

---

### Post by dmizer on 2009-05-27
How about nuking the current version and remaking it with nano:
```
sudo rm /root/.creds
sudo nano /root/.creds
```
Type in your username and password in this format (don't copy/paste as I've seen problems with that occasionally):
username=ozzie
password=password

Save the file by hitting ctrl x, and type y to save the modified buffer.

Chmod the file:
```
sudo chmod 600 /etc/.creds
```
Try the mount again.
```
sudo mount /home/ozzie/E-Books
```
If it works, you will see no output, if not, you will see errors. Please post them.

---

### Post by theozzlives on 2009-05-27
> **dmizer said:**
> How about nuking the current version and remaking it with nano:
```
sudo rm /root/.creds
sudo nano /root/.creds
```
Type in your username and password in this format (don't copy/paste as I've seen problems with that occasionally):
username=ozzie
password=password

Save the file by hitting ctrl x, and type y to save the modified buffer.

Chmod the file:
```
sudo chmod 600 /etc/.creds
```
Try the mount again.
```
sudo mount /home/ozzie/E-Books
```
If it works, you will see no output, if not, you will see errors. Please post them.

The problem is no longer the .creds file, everything is pointing to smbfs. I always use my laptop anyhow and copying the files will speed up access times.

---

### Post by dmizer on 2009-05-27
Did you get errors when you tried to mount?

Try this mount line:
```
//192.168.1.3/e-books /home/ozzie/E-Books cifs credentials=/home/ozzie/.creds,noexec,file_mode=0777,dir_mode=0777 0 0
```

If that works, then we can try adding "users"

---

### Post by dmizer on 2009-05-27
> **theozzlives said:**
> ozzie@ozzie-laptop:~$ sudo mount -a
[sudo] password for ozzie: 
mount: wrong fs type, bad option, bad superblock on //192.168.1.3/e-books,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Oh man, I just saw this ...

Try this:
```
sudo aptitude install smbfs
```

---

