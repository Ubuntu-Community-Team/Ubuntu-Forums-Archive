---
title: "[SOLVED] Strange Samba permissions on vfat volume"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by Tomas123 on 2008-06-16
I know, perhaps it is not related with Ubuntu Server 8.04, but rather with Samba itself, but I thought perhaps someone has similar experience...

I have a couple of shares on Samba on a vfat (fat32) volume. As everybody knows Linux permissions does not work on vfat, except on mount folder where vfat partition is mounted. I though that is really not a minus, but a plus if you want to create share for 10-15 users, because then it's not necessary to mess with all those permissions. 

So, recently I have noticed, that I cannot delete some of the files on that share, even if the share is mounted with fstab option:

/dev/sdb1  /mnt/320gb/disk_c        vfat    utf8,noatime,umask=007,gid=1003 0       0

I have tried umask=000, but that didn't help either...


Interesting part is that I could delete most of the files, but not those couple.

I compared permissions of the "normal" files and those "bad" ones from the Windos XP box. Normal files had All permissions available in comparison with bad files that had only Read-Execute and Read permissions available. On server permissions looked like this:

Normal file:
-rwxrwxrwx 1 root server1  6158201 1999-05-05 21:36 Alex Gopher - Super Disco.mp3

Bad file:
-r-xr-xr-x 1 root server1 2568192 2001-10-04 16:52 Bjork - All Is Full Of Love.mp3

I realized that some of the "bad" files where copied to vfat partition from CD drive (when this HDD was still on a windows PC). So the logical thinking would suggest, that those files have Read Only mark (which is usually given to all files that are copied from CD). Knowing this I tried to play with smb.conf options:

        delete readonly = Yes
        map readonly = No / Yes

I didn't get any results. I tried to change other map options but with no results either. Permissions were not intact. My Only idea is that somehow Samba is interpreting Read-Only flag and that affects the file permissions.

I would really appreciate any comments or ideas. Here are the settings of my share:

[320GB_C_full]
        path = /mnt/320gb/disk_c/
        available = Yes
        browseable = Yes
        read only = No
        follow symlinks = No
        hide dot files = Yes
        delete readonly = Yes
        case sensitive = No
        preserve case = Yes
        map archive = Yes
        map system = No
        map hidden = No
        map readonly = No
        guest ok = No
        oplocks = No
        level2 oplocks = No

---

### Post by Tomas123 on 2008-06-16
One helpful sysadmin from samba mailing list pointed me to the right direction: this problem is not related with samba, but rather with file system. I found similar thread here:

[http://ubuntuforums.org/archive/index.php/t-336667.html](http://ubuntuforums.org/archive/index.php/t-336667.html)

Because in the title described problem doesn't exist, I mark this thread as SOLVED.

The solution for this problem you will find here:

[http://stason.org/TULARC/pc/cd-recordable/3-57-How-do-I-clear-the-read-only-flag-under-Windows.html](http://stason.org/TULARC/pc/cd-recordable/3-57-How-do-I-clear-the-read-only-flag-under-Windows.html)

---

