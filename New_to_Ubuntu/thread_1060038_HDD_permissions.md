---
title: "HDD permissions"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by webmiester on 2009-02-04
Hi guys,

I just finished reformatting an external hard drive for my computer.

My problem is that I can't put anything on it because it says that the permission to make changes on the drive is owned by root.


How do I set these permissions and how do I change this?

Thank you so much

---

### Post by taurus on 2009-02-04
What filesystem did you format your external harddrive to and where do you mount it, mount point?

```
sudo fdisk -l
df -h
id
```

---

### Post by webmiester on 2009-02-09
[QUOTE=taurus;6675613]What filesystem did you format your external harddrive to and where do you mount it, mount point?

```
sudo fdisk -l
df -h
id
```[/QUOTE

webmiester@mobile-one-linux:~$ sudo fdisk -l
[sudo] password for webmiester: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf602f602

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6437    51705171    7  HPFS/NTFS
/dev/sda2            6438        9729    26442990    5  Extended
/dev/sda5            6438        9587    25302343+  83  Linux
/dev/sda6            9588        9729     1140583+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f780f78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6374    51199123+   7  HPFS/NTFS
/dev/sdb2            6375        9729    26949037+  83  Linux
webmiester@mobile-one-linux:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              24G   19G  3.9G  84% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  228K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  497M   1% /dev
tmpfs                 500M   12K  500M   1% /dev/shm
lrm                   500M  2.0M  498M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb2              26G  173M   24G   1% /media/Linux External 1
/dev/sdb1              49G   16G   34G  33% /media/Windows External 1
webmiester@mobile-one-linux:~$ id
uid=1000(webmiester) gid=1000(webmiester) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(webmiester)

Hi, the partition in question is sdb2 which I labelled as "Linux External 1".  It was formatted using ext3

---

### Post by taurus on 2009-02-09
You can change the ownership of /media/"Linux External 1" from root to your login name, webmiester, so you can write to it anytime you want.

```
sudo chown -R webmiester:webmiester /media/"Linux External 1"
ls -la /media
```

---

### Post by webmiester on 2009-02-09
> **taurus said:**
> You can change the ownership of /media/"Linux External 1" from root to your login name, webmiester, so you can write to it anytime you want.

```
sudo chown -R webmiester:webmiester /media/"Linux External 1"
ls -la /media
```

WOW, it worked!  Thank you so much!  Say, will I have to do this everytime I plug the HD in, or will it do it automatically from now on?

---

### Post by taurus on 2009-02-09
If you're using the same mount point (that you have created), you don't have to change the ownership every time.

---

### Post by webmiester on 2009-02-09
Thank you so much :)

---

### Post by mcloser on 2009-02-14
Taurus, thank you from me also.

you must know that for every person that you answer a question for - there are dozens that will read it and find the solution they need.

I know that you seem to answer the same basic question many times, but then maybe a few of us grateful souls will also become people to answer all the types of questions that come up.

thanks from a happy Ubuntu-ite

ps i hope the little guy makes it !  ( i always wondered where the 'run' key went ??? )

---

### Post by HavocXphere on 2009-02-14
> **mcloser said:**
> there are dozens that will read it and find the solution they need.

I know that you seem to answer the same basic question many times, but then maybe a few of us grateful souls will also become people to answer all the types of questions that come up.
+1

Ubuntuforums + Google indexing spiders ftw.:guitar:

---

