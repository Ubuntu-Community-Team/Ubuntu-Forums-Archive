---
title: "What is Ubuntu so ...clumsy... when it comes to samba shares ?"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by Andre-D on 2008-06-19
I use Nautilus to access samba shares this simple way:

smb://server/share

however, I get errors if I try to:
-burn files from a share to a CD/DVD, (using nautilus)
-burn files from such share when using Brasero burner (error)
-extract multipart RAR volumes using file-roller (does not find next file)
-Movie player does not play subtitle-file if playing movie from SMB
-VLC refuses to play file on samba share..

and the list goes on....

WHY ?
Isn't there a way to make software work properly with samba shares ?

---

### Post by molotov00 on 2008-06-19
```

sudo mount -t smbfs //host/dir /mnt/dir

```

Once you mount the samba share, Nautilus and all other programmes see it as a regular folder. If you're on a wired network then you can add this command to your startup scripts. Or just create a bash script and run that to mount all your shares when you double click it.

The above example would make smb://host/dir accessible as /mnt/dir.

Reason: not all programmes know how to respond to smb://. It's not really a Ubuntu issue but they could do something to get programmes to correctly recognize the smb:// protocol. Also, sometimes you need to enter passwords and usernames to gain access to shares. The mount command takes these in stride and it becomes completely transparent. This is unlike windows in that sometimes you have to re-enter usernames and passwords from within a programme that wants to play a network share.

Hope that helps.

---

### Post by superprash2003 on 2008-06-19
also you might need to allow WRITE Permission in that folder..

---

### Post by Andre-D on 2008-06-22
Thank you.
- I thought I *did* mount in using nautilus, after all, after using smb://...  - right clinking it in nautilus offers "unmount" - so I assumed it was "mounted"

I made /mnt/movies

then:
```

andre@andre-laptop:~$ sudo mount -t smbfs //odin/movies /mnt/movies
mount: wrong fs type, bad option, bad superblock on //odin/movies,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I do already have write rights - both to share and filesystem, (NTFS) - what kind of trouble /why do I risk trouble if I try to mount a real-only share/folder-rights?

Thanks.

---

### Post by Andre-D on 2008-06-22
Ok I searched, and found that I needed smbfs package
after installing it , I got:

```
andre@andre-laptop:~$ sudo mount -t smbfs //odin/movies /mnt/movies
mount error: could not find target server. TCP name odin/movies not found
No ip address specified and hostname not found

```

.. then, after some time, I found that it - for some reason, could not resolve the netbios name.

so I tried to enter IP:

```
andre@andre-laptop:~$ sudo mount -t smbfs //192.168.1.110/movies /mnt/movies
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

now how freakish hard is this "simple" task in Linux ? - damn :)
- I just bought a VMWare workstation license for Linux - but my new OS still does not like me :)

---

### Post by dmizer on 2008-06-23
samba is a closed protocol that windows uses for file sharing.  it only works in linux because it's been backwards engineered.

please see the second link in my sig for more information on how to mount windows shares with cifs.

---

### Post by Andre-D on 2008-06-25
Thanks.
installing "winbind" messes Nautilus up.
when browsing smb:// , sometimes everything i listed ok, sometimes some files/folders are missing, and other times, an empty list is displayed.

removing winbind solves the problem.

BTW: isn't there a more simple way to mount shares properly ? - like a GUI?
I also don't like to make a plain text password file (.smbcredentials)
.. I must look for whole disk encryption in linux ..

---

### Post by dmizer on 2008-06-25
if you mount the share either with either option in the howto, you do not need to browse the share with smb:// in nautilus.  open nautilus, browse to /mnt/movies and you will be able to view the shares.

with chmod 700, the .smbcredentials file is only readable by the root user.  obviously encryption would be a more secure option, but this is about as safe as you get without it.

full disk encryption is an option on the alternate cd during install

---

### Post by Andre-D on 2008-06-25
I am aware of the possibility of browsing /media/(share) in stead of SMB
however, I am attemting Ubuntu for professional use in my job.
I still need a fast'n'easy way to view any share using smb://
(we have >100 servers and >2500 users  - I cannot mount all shares I need)

It IS acceptable to mount only these I need to do special file operations on, but I must still be able to use basic functionality using SMB://  - because it's fast

is "windbind messing up smb:// in Nautilus" a known bug ?

Thanks.
I still hope to find Ubuntu easy and usable for my job.

---

### Post by dmizer on 2008-06-27
> **Andre-D said:**
> I am aware of the possibility of browsing /media/(share) in stead of SMB
however, I am attemting Ubuntu for professional use in my job.
I still need a fast'n'easy way to view any share using smb://
(we have >100 servers and >2500 users  - I cannot mount all shares I need)
this is a genuine problem for which i do not have a reasonable answer.  there are gui samba browsers available, so you may want to take a look in that direction.  but nautilus isn't really going to be helpful.

> **Andre-D said:**
> It IS acceptable to mount only these I need to do special file operations on, but I must still be able to use basic functionality using SMB://  - because it's fast

is "windbind messing up smb:// in Nautilus" a known bug ?

Thanks.
I still hope to find Ubuntu easy and usable for my job.
as far as i know, yes there is a bug open on this.  for some reason cifs, winbind, and nautilus cannot work in harmony with one another.  this has been a problem for as long as i've been using ubuntu.

as a temporary work around, you could stop the winbind daemon when you need to browse via nautilus:
```
sudo /etc/init.d/winbind stop
```
then when you're done:
```
sudo /etc/init.d/winbind start
```

ugly to be sure, but better than nothing.  i do know that the developers are working hard to try to fix nautilus and samba interoperability, so your problem may actually be solved in the relative near future.

---

