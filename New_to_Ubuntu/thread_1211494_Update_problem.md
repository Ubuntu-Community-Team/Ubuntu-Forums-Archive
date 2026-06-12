---
title: "Update problem"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Autumnie88 on 2009-07-12
the update installer told me that I needed to run dpkg --configure -a. I did that, and it gave me this

[b]dpkg: error processing update-notifier (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.
Errors were encountered while processing:
update-notifier

Any ideas on how to fix this so I can install the updates?

---

### Post by philinux on 2009-07-12
sudo dpkg --configure -a

---

### Post by Autumnie88 on 2009-07-12
I ran that and that is when it gave me all the other stuff.

---

### Post by Michael.Godawski on 2009-07-12
What happens after
```

sudo apt-get install -f
```

---

### Post by Autumnie88 on 2009-07-12
After I run that I get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dhcdbd libisc32
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 57.9kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main update-notifier 0.70.9netbook1 [57.9kB]
Fetched 57.9kB in 1s (31.2kB/s)         
(Reading database ... 99081 files and directories currently installed.)
Preparing to replace update-notifier 0.70.9netbook1 (using .../update-notifier_0.70.9netbook1_lpia.deb) ...
Unpacking replacement update-notifier ...
Setting up update-notifier (0.70.9netbook1) ...

---

### Post by Michael.Godawski on 2009-07-12
Sounds good.

Can you update now?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Autumnie88 on 2009-07-12
It was able to update, but now it says that all of the disk space in the root partition is being used.  My browser looks all screwed up now too.

---

### Post by earthpigg on 2009-07-12
> **Autumnie88 said:**
> It was able to update, but now it says that all of the disk space in the root partition is being used.  My browser looks all screwed up now too.

show output of this, please:

```
df -h
```

---

### Post by nynoah on 2009-07-12
I personally have grown to LOVE Ubuntu tweak.......... I know I am going catch a lot of flack that statement.  But ubuntu tweak has a feature that lets you clean up old packages and configure files that are clogging up your system.  This esp helps when space is limited and you have a sep home partition.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Ubuntu needs a GUI like they have for doing just this.

---

### Post by Autumnie88 on 2009-07-13
This is the output:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  3.4G     0 100% /
varrun                247M  108K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   36K  247M   1% /dev
devshm                247M   48K  247M   1% /dev/shm
lrm                   247M  1.9M  245M   1% /lib/modules/2.6.24-24-lpia/volatile
overflow              1.0M   52K  972K   6% /tmp
gvfs-fuse-daemon      3.4G  3.4G     0 100% /home/autumn/.gvfs


For my browser, it will not let me use the back, forward, stop, or home buttons.

---

### Post by earthpigg on 2009-07-14
```
Filesystem Size Used Avail _**Use%**_ Mounted on
/dev/sda2 3.4G 3.4G 0 _**100%**_ /
```

according to that, you are out of space on that thumb drive (or hard drive, or netbook ssd, whichever the case may be).

here a few things you could try, and in the order i would suggest trying them in:

(i suggest emptying the trash and running 'df -h' between each step so you can see how much each step freed up.)

1) clear out the local software backups that are automatically stored whenever you download any update:

```
sudo apt-get autoclean
sudo apt-get clean
```
and system -> administration -> computer janitor. <-- make sure you dont remove something you actually use. you will recognise something there that you use, if you use it.... 3rd party software (google earth, opera, skype) often shows up there.

2) remove music, videos, etc, that you have stored. a 3.4gb drive really isn't sufficient to be used to store that stuff. i suggest either an external hard drive or perhaps an external thumb drive.

3) go to applications -> accessories -> disk usage analyser -> scan filesystem. ignore that fancy graph thing on the right. click around on the left, see what is taking up space!

---

