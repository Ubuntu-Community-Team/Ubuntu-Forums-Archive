---
title: "root partition is full"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by shootdorisday on 2009-03-19
using 12 gigs of 12 gigs.

this is what i'm told.


carl@carl-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              12G   12G     0 100% /
df: `/var/run': No such file or directory
df: `/var/lock': No such file or directory
udev                  506M   60K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda8              24G   17G  6.3G  73% /home
/dev/sdb1             150G   18G  132G  12% /media/New Volume
overflow              1.0M   52K  972K   6% /tmp
gvfs-fuse-daemon       12G   12G     0 100% /home/carl/.gvfs
/dev/sda1              37G  177M   35G   1% /media/disk
/dev/sda5              99M   12M   82M  13% /media/_boot


i know i could increase the size of the partition with gparted, but there are obviously some big files in there that shouldn't be.

i had a hunch it was something to do with var, so i deleted the var backup folder, but no change.

i would be thrilled if someone could help because i've been reading threads all day and nothing has helped.

i am fairly new to ubuntu, so please go easy.


here is a screenshot from gparted.

[IMG]http://teakdoor.com/Gallery/albums/userpics/10104/Screenshot-1~8.png[/IMG]

i presume sda6 is where root is living.

---

### Post by albandy on 2009-03-19
Type this in terminal and paste the results here

sudo du -m -s /*

---

### Post by shootdorisday on 2009-03-19
thanks.

this is what i get.

6	/bin
56	/boot
0	/cdrom
1	/dev
13	/etc
du: cannot access `/home/carl/.gvfs': Permission denied
16702	/home
1	/initrd
0	/initrd.img
0	/initrd.img.old
401	/lib
1	/lost+found
16871	/media
1	/mnt
20	/opt
du: cannot access `/proc/7182/task/7182/fd/3': No such file or directory
du: cannot access `/proc/7182/task/7182/fdinfo/3': No such file or directory
du: cannot access `/proc/7182/fd/3': No such file or directory
du: cannot access `/proc/7182/fdinfo/3': No such file or directory
0	/proc
8359	/root
7	/sbin
1	/srv
0	/sys
1	/tmp
2323	/usr
0	/vmlinuz
0	/vmlinuz.old

---

### Post by albandy on 2009-03-19
as you can see you have 8GB in /root , search inside /root

/root folder requires root permision so you can browse it by typing
sudo nautilus /root

---

### Post by vanadium on 2009-03-19
the problem might be in your /root. Itis more than 8 gigabyte. For reference, I have 98 Megabyte. To have a more detailed look at your /root, you can use the following command, which will sort the biggest files first.

sudo du /root | sort -nr

You can display the "top 20" with the command

sudo du /root | sort -nr | head -20

---

### Post by anaconda on 2009-03-19
12GB is too small root partition!

(almost) all programs that you install to your system will be installed to the root partition.. eg. /bin  /usr/bin etc..

Just cant help wondering why some ubuntu install quides still recommend far to small root psrtitions..

PS. in this case you seem to have too much stuff in /root  
Maybe you have deleted stuff using Nautilus in root mode (sudo nautilus) And the files are still stored in root users trash..

---

### Post by shootdorisday on 2009-03-19
thanks for the prompt replies.

here is the top part of what i get after running the command sudo du /root | sort -nr


16	/root/.local/share/Trash/files/var/lib/dpkg/triggers
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/First/var
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/6/var
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/5/var
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/4/var
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/3/var
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/2/var
16	/root/.local/share/Trash/files/var/cache/system-tools-backends/backup/1/var
16	/root/.gconf/apps/gedit-2/preferences
12	/root/.local/share/Trash/files/var/spool/openoffice
12	/root/.local/share/Trash/files/var/log/fsck
12	/root/.local/share/Trash/files/var/lib/update-notifier/user.d
12	/root/.local/share/Trash/files/var/lib/ufw
12	/root/.local/share/Trash/files/var/lib/thunderbird
12	/root/.local/share/Trash/files/var/lib/samba/printers
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/ui/webui/templates/ajax/static/themes/white/mime_icons
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/ui/webui/templates/ajax/static/themes/classic/mime_icons
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/ui/webui/templates/ajax/static/css
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/i18n/zh_TW
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/i18n/zh_HK
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/i18n/zh_CN
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/i18n/vi
12	/root/.local/share/Trash/files/var/lib/python-support/python2.5/deluge/i18n/uk






what can i do to free up some space?

---

### Post by shootdorisday on 2009-03-19
> **anaconda said:**
> 12GB is too small root partition!


PS. in this case you seem to have too much stuff in /root  
Maybe you have deleted stuff using Nautilus in root mode (sudo nautilus) And the files are still stored in root users trash..


i think that's the problem, but try as i might, i can't navigate to root trash.
permission / access denied etc.

---

### Post by philinux on 2009-03-19
Delete the files in roots Trash.

Use

gksu nautilus

12gig is fine for /. My systems been up for a while with loads of apps installed and I'm only using 3.8 gig out of 12.
You must be doing something odd to fill up roots trash.

---

### Post by vanadium on 2009-03-19
[quote=anaconda]12GB is too small root partition![/quote]
4 GB is plenty.

That you have such a trash under /root indicates that you are having either a root account or running a lot of commands using sudo.

Actually, having a root account is not recoommended, but if you want it and use it often, then you should move it out of your / partition to another partition. This can be as simple as replacing the directory /root with a symbolic link pointing to the real location on another partition.

---

### Post by shootdorisday on 2009-03-19
> **philinux said:**
> Delete the files in roots Trash.

Use

gksu nautilus

12gig is fine for /. My systems been up for a while with loads of apps installed and I'm only using 3.8 gig out of 12.
You must be doing something odd to fill up roots trash.

thanks but even then i can't access root trash.

just getting the message.... 

[B][I]Folder contents couldn't be displayed

Sorry, couldn't display all the contents of "trash": Operation not supported
[/I][/B]

---

### Post by gandaran on 2009-03-19
> **anaconda said:**
> 12GB is too small root partition!

(almost) all programs that you install to your system will be installed to the root partition.. eg. /bin  /usr/bin etc..

Just cant help wondering why some ubuntu install quides still recommend far to small root psrtitions..

PS. in this case you seem to have too much stuff in /root  
Maybe you have deleted stuff using Nautilus in root mode (sudo nautilus) And the files are still stored in root users trash..
12 GB is too small? I have a 5GB root partition and still have 1GB free space, now if you want to install every application in synaptic then yes it's too small!

---

### Post by albandy on 2009-03-19
well, if you don't want to restore the files in root's trash you can do the folowing:

sudo rm -rf /root/.local/share/Trash/*

---

### Post by gandaran on 2009-03-19
shootdorisday

run these two commands, they will clean the root system of cache and release some disk space
sudo apt-get autoclean
sudo apt-get clean

---

### Post by shootdorisday on 2009-03-19
^
did sudo rm -rf /root/.local/share/Trash/*

but got.

[B][I]can't mkdir /var/run/sudo: No such file or directory
[/I][/B]

---

### Post by shootdorisday on 2009-03-19
> **gandaran said:**
> shootdorisday

run these two commands, they will clean the root system of cache and release some disk space
sudo apt-get autoclean
sudo apt-get clean

i ran them already, cleared a tiny amount of space though.

still full to the brim.
:(

---

### Post by philinux on 2009-03-19
Open a terminal and issue the command 

```
gksu nautilus

```
now navigate to roots Trash folder and delete the contents.

---

### Post by gandaran on 2009-03-19
> **shootdorisday said:**
> ^
did sudo rm -rf /root/.local/share/Trash/*

but got.

[B][I]can't mkdir /var/run/sudo: No such file or directory
[/I][/B]
trash is locate in /home/'user'/.local/share/Trash, check it out if the files are there.

---

### Post by albandy on 2009-03-19
> **gandaran said:**
> trash is locate in /home/'user'/.local/share/Trash, check it out if the files are there.

He has the /root trash folder full of data.

---

### Post by drs305 on 2009-03-19
There is a link to a guide to finding and deleting trash, including root's, in my signature line. If you still don't have your problem solved yet it may help you out.

---

### Post by vanadium on 2009-03-19
IF all else fails, try to do it from a recovery prompt or from a live CD session.

---

### Post by mikechant on 2009-03-20
> i had a hunch it was something to do with var, so i deleted the var backup folder, but no change.

What exactly do you mean by 'the var backup folder'? Some of the later errors (like "can't mkdir /var/run/sudo: No such file or directory") seem to imply you actually deleted /var, in which case you might be looking at a reinstall (unless anyone knows how to reliably recover from this).

Aside from the /var issue though, I'd second the suggestion of deleting the root trash from the LiveCD. Various things may not work properly when running from a system with the '/' filesystem full.

Something else is that various posts have said "12Gb should be plenty for your '/' filesystem" which is true - but only if /home is seperate. As your /home is part of /, 12Gb could easily be too small - looks like /home is using 8Gb, only leaving 4Gb for / which is not really enough for comfort.

---

