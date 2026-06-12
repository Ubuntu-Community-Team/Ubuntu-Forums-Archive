---
title: "samba ntfs"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by cong06 on 2007-11-15
quick question: does Gutsy gibbon have ntfs available or not?

I assumed it did, but apparently samba can't read my ntfs partitions...

I'm getting this error: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/106532/comments/1](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/106532/comments/1)

---

### Post by delphiguy on 2007-11-15
i believe gutsy does come with ntfs-3g.

---

### Post by disturbed1 on 2007-11-15
We have 2 older PCs in the house with Win2000 and XP installations formated as NTFS. 

Browsing using
```
smb://192.168.1.106/C$
```in Nautilus works fine. Sad a password isn't even needed to browse/change the system files in Windows 2000.

Also in 4 of our Linux machines we have this line in the fstab

```
//192.168.1.30/D    /media/Julie.D    cifs    username=:),password=;),uid=1000    0    0
```which gives us read/write access to the NTFS drive across all Linux machines.

Check to make sure file sharing is set correctly on Windows machine. If you plan on mounting the drive, use the update to date CIFS rather than the depreciated and buggy samba protocols. CIFS works better as **mounting** the network share. Samba is just fine for occasional browsing/copying. CIFS is highly recommended for permanent logical mounting of network shares. Has a reduced file locking nature, and greater throughput. With SAMBA we could only achieve 4-5MBS transfer speeds, with the occasional hang here and there. CIFS nets us 8.9-9.2MBS with no file locks noticed as of yet across 3 years of CIFS usage.

---

### Post by cong06 on 2007-11-15
ok, I was pretty vague, my problem is that I have a ntfs hard drive, that I can do read/writes to.

However, when I try to share it with samba, I get that error. It's only when I right click on the folder and "Share folder" that I even encounter this problem.

---

### Post by cong06 on 2007-11-15
Just to test it, I set up a share that was completly off my ext3 drive.

It had absolutely no problems...
Shame the "bug"/problem wasn't more obviously related to ntfs, then I might have saved myself around 5 hours...

---

### Post by disturbed1 on 2007-11-15
> **cong06 said:**
> ok, I was pretty vague, my problem is that I have a ntfs hard drive, that I can do read/writes to.

However, when I try to share it with samba, I get that error. It's only when I right click on the folder and "Share folder" that I even encounter this problem.

That makes sense now :lolflag:

I am completely unaware if that is possible at all. Interesting to know though. If you find out any information, it'd nice to post in this thread. I'm sure you're not the only one wanting to share files off your NTFS drive mounted in Linux. When they search for answers, this thread will pop up.

---

### Post by cong06 on 2007-11-15
well, I [figured it out.](http://ubuntuforums.org/showpost.php?p=3602771&postcount=2)

```

# /dev/sdb1
UUID=260C19000C18CD25 /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1

```

the /etc/fstab file apparently wasn't working with samba...

when I switched this to:
```

# /dev/sdb1
UUID=260C19000C18CD25 /media/sdb1     ntfs    defaults,umask=00[COLOR="Red"]0[/COLOR],gid=46 0       1

```

then the mounted drive (ntfs) could be read by samba, etc. (after I setting /etc/samba.smb.conf correctly of course)

It's less secure, but pretty much just as secure as it was for me when I used windows...So I'm content. (as long as only LAN connections get to it, I'll be fine)

---

