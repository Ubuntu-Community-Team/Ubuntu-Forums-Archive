---
title: "How to change file permissions"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by webwiller on 2009-09-24
Hi all!
By mistake I changed permissions about all files (mostly video's) on my movie-staion and now they're own by root and I'm not able to move them or cancel as I like obvoisly.
Which is a fast 'n easy way to re-change permission for the entire directory? Best way is probably through Terminal...but I dont know the right commands.
Pls...help me out! ;)
Ty :D

---

### Post by credobyte on 2009-09-24
```
sudo chmod -R 755 /path/subfolder
sudo chown -R user:group /path/subfolder

```

---

### Post by webwiller on 2009-09-24
I'm not sure about the second line. Let's say my username is webwiller. What should I type exactly?
> sudo chown -R webwiller:group /path/subfolder

Where /path/subfolder I understand to put correct path and subfolder.

---

### Post by credobyte on 2009-09-24
user:group usually are equal .. If your main username is geek ( no offense ), group will be the same ( user:user ).

```
sudo chown -R webwiller:webwiller /path/subfolder
```

---

### Post by webwiller on 2009-09-24
> **credobyte said:**
> user:group usually are equal .. If your main username is geek ( no offense ), group will be the same ( user:user ).

```
sudo chown -R webwiller:webwiller /path/subfolder
```

They all changed to root now :(

???



(not offended:))

---

### Post by credobyte on 2009-09-24
> **webwiller said:**
> They all changed to root now :(

???



(not offended:))

What ? :-s

```
cd /path/subfolder
ls -l
cd ..
ls -l
```

Execute the following commands ( copy / paste ) and let us know the output of both ls's.

---

### Post by webwiller on 2009-09-24
> webwiller@webwiller-laptop:~$ cd /media/disk/chri
webwiller@webwiller-laptop:/media/disk/chri$ ls -l
totale 56
drwxrwxrwx 1 root root  4096 2009-09-15 23:16 back-up
drwxrwxrwx 1 root root  8192 2009-06-30 14:51 back-up-02giu09-crisdn
drwxrwxrwx 1 root root  4096 2009-03-19 10:12 documenti
drwxrwxrwx 1 root root  4096 2009-06-06 00:05 dr.house
drwxrwxrwx 1 root root     0 2009-03-19 10:13 lettere, mail...scritti xsonali
drwxrwxrwx 1 root root  4096 2009-03-01 15:22 music
drwxrwxrwx 1 root root     0 2009-03-19 10:14 old jobs
drwxrwxrwx 1 root root  4096 2009-03-01 13:55 pictures
drwxrwxrwx 1 root root  4096 2009-06-02 14:16 system volume information
drwxrwxrwx 1 root root 20480 2009-09-24 21:31 video
drwxrwxrwx 1 root root  4096 2009-06-02 14:16 xxx

and......

> webwiller@webwiller-laptop:/media/disk$ cd ..
Webwiller@webwiller-laptop:/media$ ls -l
totale 20
lrwxrwxrwx 1 root      root    6 2009-09-21 17:26 cdrom -> cdrom0
drwxr-xr-x 2 root      root 4096 2009-09-21 17:26 cdrom0
drwxrwxrwx 1 root      root 8192 2009-09-24 22:02 disk
drwx------ 5 webwiller root 8192 1970-01-01 01:00 max_ shuffl

---

### Post by credobyte on 2009-09-24
Try:
```
sudo chown -R webwiller:webwiller /media/disk/chri
```

---

### Post by webwiller on 2009-09-24
> webwiller@webwiller-laptop:~$ sudo chown -R webwiller:webwiller /media/disk/chrichown: cambiamento del proprietario di "/media/disk/chri/VIDEO/TOSEE/Fo&#58782;ta Pasc (2009) CD1.avi": Nessun file o directory
chown: cambiamento del proprietario di "/media/disk/chri/VIDEO/TOSEE/NEWS 2009/Punisher Zona Di Guerra 2008.avi": Errore di I/O
webwiller@webwiller-laptop:~$ cd /media/disk/chri
webwiller@webwiller-laptop:/media/disk/chri$ ls -l
totale 56
drwxrwxrwx 1 root root  4096 2009-09-15 23:16 BACK-UP
drwxrwxrwx 1 root root  8192 2009-06-30 14:51 BACK-UP-02GIU09-CRISDN
drwxrwxrwx 1 root root  4096 2009-03-19 10:12 Documenti
drwxrwxrwx 1 root root  4096 2009-06-06 00:05 DR.HOUSE
drwxrwxrwx 1 root root     0 2009-03-19 10:13 Lettere, mail...scritti xsonali
drwxrwxrwx 1 root root  4096 2009-03-01 15:22 Music
drwxrwxrwx 1 root root     0 2009-03-19 10:14 OLD JOBS
drwxrwxrwx 1 root root  4096 2009-03-01 13:55 PICTURES
drwxrwxrwx 1 root root  4096 2009-06-02 14:16 System Volume Information
drwxrwxrwx 1 root root 20480 2009-09-24 21:31 VIDEO
drwxrwxrwx 1 root root  4096 2009-06-02 14:16 XXX



Do they keep belonging to root...dont they? How comes...
Should come out webwiller webwiller, isnt it??!!

---

### Post by webwiller on 2009-09-24
I'm confused...now I tried to delete two video's both owned by root, I checked file properties...and I could delete one but I got "I/O mistake deleting file: operation not permitted" for the other one...why's that?

---

### Post by sandyd on 2009-09-24
perhaps without the collon
```

sudo chown -R webwiller /media/disk/chri

```

---

### Post by webwiller on 2009-09-24
Nope! Still every single directory and file owned by root! 

... :'''-)

:confused:

---

### Post by jrothwell97 on 2009-09-24
Are these files stored on an external disk, and if so, is it formatted with FAT?

---

### Post by webwiller on 2009-09-24
> **jrothwell97 said:**
> Are these files stored on an external disk, and if so, is it formatted with FAT?

The answers are:

- YES
- YES

They're on an external movie-station that I share with both Win&Linux

---

### Post by bodhi.zazen on 2009-09-24
Ownership and permissions on FAT and NTFS files are set at the time of mounting the partition and you can not change them with chown or chmod.

You have to unmount the partition and re-mount it.

```
mount -t vfat /dev/sdb1 /media/disk/chri -o uid=1000,gid=1000,dmask=000,fmask=111
```

Normally these things are set automatically so long as there is no entery in /etc/fstab for the device. If you wish to over rode the defaults use mount or edit /etc/fstab;

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

You may be able to set it with a gui tool of some kind, I am not sure. Take a look at ntfs-config (it handles both FAT and ntfs partitions).

---

