---
title: "fstab problems with permissions"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by KevinM2k on 2011-02-15
Hi,

I have set up an apache2 server which reads the websites from an NTFS partition I formally used when in windows.

When I first tried it, it said I had no permission to access anything, I tried running chmod/chown and although no errors came back it simply didn't do anything.

I then added an entry in fstab:

/dev/sda5 /media/Storage/Websites ntfs rw,defaults,user,gid=1000,umast=0222 0 0

When I rebooted, the web server now works, but they are all set up as 777 permissions and are chowned - root:user1 (user1 being me)

Again I tried chmod/chown and again no errors but nothing has changed.

Am I doing something wrong?

Thanks in advance

Kevin

---

### Post by vanadium on 2011-02-15
ntfs does not support linux file permissions. Default owners and file permissions for the entire file system are set through mount options, as you did.

umast is not a valid option. You probably mean umask. This will explain why permissions are 777 rather than 555.

gid=1000 denotes the group of user 1000: probably that is indeed your account. Since you did not specify a uid, the default, root, is assumed.

It would be preferred to have your files on a file system that supports linux file permissions.

---

### Post by amsterdamharu on 2011-02-15
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)
under
Mount options for ntfs

gid=www-data

if you need access as well:
uid=myuser
Where myuser is your user name (it says id but the name works as well).

umask=0222 will set the correct permission, the irritating execute will still be there everytime you click a file but setting it to 111 or 0111 or anyting 111 will remove the execute from directories too and make them unreadable.

---

### Post by KevinM2k on 2011-02-15
> **vanadium said:**
> 

It would be preferred to have your files on a file system that supports linux file permissions.

I dont have my windows system anymore, so would be happy to give this a go, but don't want to lose anything on the drive, is it possible to change the file system without reformatting? Can gparted do this?

---

### Post by vanadium on 2011-02-15
> **KevinM2k said:**
> I dont have my windows system anymore, so would be happy to give this a go, but don't want to lose anything on the drive, is it possible to change the file system without reformatting? Can gparted do this?
It surprises me that you care for these data if you do not have a backup. So many risks and problems disappear if you have a good backup. It indeed would have been a breeze to reformat the partition and put the data back.

There is a second problem in using an ntfs file system on a system without MS Windows. It has become impossible to check the file system using the dedicated Windows tools, specifically designed for the ntfs format.

Anyway, in the mean time, you can solve the permission/owner issues adapting the options in /etc/fstab as amsterdamharu indicated.

---

### Post by KevinM2k on 2011-02-15
> **vanadium said:**
> It surprises me that you care for these data if you do not have a backup. So many risks and problems disappear if you have a good backup. It indeed would have been a breeze to reformat the partition and put the data back.

There is a second problem in using an ntfs file system on a system without MS Windows. It has become impossible to check the file system using the dedicated Windows tools, specifically designed for the ntfs format.

Anyway, in the mean time, you can solve the permission/owner issues adapting the options in /etc/fstab as amsterdamharu indicated.

If I lost everything on the drive, it wouldn't be the end of the world if you know what I mean, it would just be a hassle.

I have an external HDD around which I use for backup, so maybe its time to pull that out, clean the drive out change to ext4 (that is the best isn't it?) then put everything back on it.

In the meantime I have changed the umask (I did mean that) to 0022, so its the same as 755 as put the uid in as well so all is fine for now until I get around to a proper backup.

Thanks for the help.

---

### Post by vanadium on 2011-02-15
Do that! Then you will remove the risk, even if it is just a hassle.

---

