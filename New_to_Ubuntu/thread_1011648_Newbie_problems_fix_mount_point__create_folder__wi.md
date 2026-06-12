---
title: "Newbie problems: fix mount point / create folder / windows sharing"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Fatah Ruark on 2008-12-15
I finally decided to learn Ubuntu (had a few attempts in the past).

Here are the problems I am having:

1. I accidentally changed the mount point of the second drive (sdb1) to \. How do I change it back so I can mount the drive?

2. I'd also like the 2 additional drives I have (sdb1;sdc1) to mount automatically when I start Ubuntu

3. I can't even create a new folder on those drives. How can I do that? I'm pretty sure my login has admin privileges.

4. Finally, I want to copy a large number of files from my XP machine to the new Ubuntu machine. At one point I could get to my XP shares via Places>Network>Windows Network>Home but I can't seem to now, and even when I could I could not copy any files. Any ideas on how to resolve that?

TIA.

---

### Post by HermanAB on 2008-12-15
You can change the mount points in /etc/fstab, then do "mount -a" to mount them.  Read 'man fstab' a few times, then edit the file and see for yourself, it is not hard to figure out.

Absolutely the easiest way to share files is with good old FTP.  FTP has been around for almost half a century and there is a good reason for that: It works.  Install Filezilla client and server on Windows, then use Nautilus to retrieve files from Windows using the address "ftp://windows.machine.ip.address".

[http://filezilla-project.org/](http://filezilla-project.org/)

Cheers,

Herman

---

### Post by pbpersson on 2008-12-15
Automatically mounting new drives:

I found this [great article]("http://www.psychocats.net/ubuntu/mountlinux") that walked me through it.

When I did this....I saved myself tons of trouble by NOT putting the folders in the root.  I created some folders in my home directory, for instance:
/home/phil/shared drives/drive1
/home/phil/shared drives/drive2

That way, I know once the drives are mounted I will have the needed permissions.

For accessing remote Windows shares, I use SMB4K and I think it is excellent!

I hope this helps

---

