---
title: "Username/Root Name"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by DannyP87 on 2009-03-07
Hi everyone,

When I fist installed Ubunut I stupidly installed it as da**nnn**y and not danny.

I know it's only a minor thing yet still I find it annoying! :(

Can I change it at all without having to create a new user? I can change the name of the computer so that the name at the top right is Danny but my home folder and so on is still dannny.

I've read somewere that if I create a new user then I won't the have same permissions as the original user and I'll have to log on which I don't want to, just want it to start up. 

Ta

Danny

---

### Post by albandy on 2009-03-07
yes, but it's a bit complicated:

first create new user with sudo permisions.
log in with that user, and edit this files changing dannny to danny:

/etc/passwd
/etc/shadow
/etc/group

---

### Post by Nepherte on 2009-03-07
Yes you can. This will change your username:
```
sudo usermod -l newusername originalusername
```
I suggest you backup your home directory. The manual page says you will probably have to rename your home directory to reflect the new login name.

---

### Post by DannyP87 on 2009-03-07
I think I have a problem.

I went into terminal and used the add user line. BUt it says only root user may add users.

I'm the only person on this computer so in theory should I not be root user?

---

### Post by unutbu on 2009-03-07
When asked for a password, just type in your user password.

Also, this command will move your home directory for you:
```
sudo usermod --login danny --home /home/danny -m dannny
```

You should also run
```
sudo groupmod --new-name danny dannny
```
so your group name is appropriately changed as well.

---

### Post by albandy on 2009-03-07
> **Nepherte said:**
> Yes you can. This will change your username:
```
sudo usermod -l newusername originalusername
```
I suggest you backup your home directory. The manual page says you will probably have to rename your home directory to reflect the new login name.

Wow this is a great command, Thanks a lot.

---

### Post by iamkrazee on 2009-03-07
It´s a way of protecting your system from potentially harmful scripts. You will be prompted for a password. But since root comes disabled in ubuntu, you just type in your own password.

---

### Post by nakedfanatic on 2009-03-07
> **DannyP87 said:**
> I think I have a problem.

I went into terminal and used the add user line. BUt it says only root user may add users.

I'm the only person on this computer so in theory should I not be root user?

To diminish the likelihood of you inadvertently damaging your system, Ubuntu doesn't have a 'root' account by default.

Instead, to run a command as root, precede it with 'sudo'

---

### Post by DannyP87 on 2009-03-07
I've learned how to log into terminal as root with the ```
su -l
``` command.

Now I've managed to set up a new user and everything but it's not changed anything other than another folder in the same place as the original dannny folder. I've ended up deleting the new user and the new folder is still there and I can't delete as it says > The folder ".compiz" cannot be handled because you do not have permissions to read it. 

I'm stuck again!

Nooooo.

---

### Post by taurus on 2009-03-07
What is the login name of the new user's directory that you want to remove?

```
sudo rm -rf /home/new_user_login_name
```

---

### Post by DannyP87 on 2009-03-07
Sorry to be a pain to everyone. I have now managed to delete the folder using ```
gksudo nautilus
```

So basically, I am back to square one. 

I'll start again.

1. In the location /home my folder is called da**nnn**y.
2. In terminal my user is danny@Da**nnn**y-Desktop:~$ 
3. The main group which I'm in is da**nnn**y.

All these three things I want it to change to Danny or danny if not possible.

Is it a case of deleting everything and greating a new group and user?

---

### Post by taurus on 2009-03-07
What are the outputs of these commands from a terminal?

```
id
ls -la /home
tail /etc/passwd
tail /etc/group
sudo tail /etc/shadow
```

---

### Post by DannyP87 on 2009-03-07
As requested:

```
danny@Dannny-Desktop:~$ id
uid=1000(danny) gid=1000(dannny) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(dannny)

danny@Dannny-Desktop:~$ ls -la /home
total 12
drwxr-xr-x  3 root  root   4096 2009-03-07 16:22 .
drwxr-xr-x 20 root  root   4096 2009-03-02 20:42 ..
drwxr-xr-x 43 danny dannny 4096 2009-03-07 16:25 dannny

danny@Dannny-Desktop:~$ tail /etc/passwd
hplip:x:103:7:HPLIP system user,,,:/var/run/hplip:/bin/false
avahi-autoipd:x:104:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
gdm:x:105:113:Gnome Display Manager:/var/lib/gdm:/bin/false
pulse:x:106:115:PulseAudio daemon,,,:/var/run/pulse:/bin/false
saned:x:107:118::/home/saned:/bin/false
messagebus:x:108:119::/var/run/dbus:/bin/false
polkituser:x:109:120:PolicyKit,,,:/var/run/PolicyKit:/bin/false
avahi:x:110:121:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
haldaemon:x:111:122:Hardware abstraction layer,,,:/var/run/hald:/bin/false
danny:x:1000:1000:Danny Parker,,,,:/home/dannny:/bin/bash

danny@Dannny-Desktop:~$ tail /etc/group
pulse-access:x:116:
pulse-rt:x:117:
saned:x:118:
messagebus:x:119:
polkituser:x:120:
avahi:x:121:
haldaemon:x:122:
admin:x:123:danny
dannny:x:1000:
sambashare:x:124:danny

danny@Dannny-Desktop:~$ sudo tail /etc/shadow
[sudo] password for danny: 
hplip:*:14181:0:99999:7:::
avahi-autoipd:*:14181:0:99999:7:::
gdm:*:14181:0:99999:7:::
pulse:*:14181:0:99999:7:::
saned:*:14181:0:99999:7:::
messagebus:*:14181:0:99999:7:::
polkituser:*:14181:0:99999:7:::
avahi:*:14181:0:99999:7:::
haldaemon:*:14181:0:99999:7:::
danny:$1$EvOE9uAp$1PzCNQ6V.fwuF2OnGh5Ka/:14310:0:99999:7:::
danny@Dannny-Desktop:~$ 

```


Thanks taurus

---

### Post by taurus on 2009-03-07
So your username is danny and you belong to group dannny.

First, edit /etc/passwd

```
gksudo gedit /etc/passwd
```
and change your $HOME from /home/dannny to /home/danny.

Then, edit /etc/group

```
gksudo gedit /etc/group
```
and change group dannny to danny, 1000.

Now, change your $HOME from /home/dannny to /home/danny.

```
sudo mv /home/dannny /home/danny
sudo chgrp -R danny /home/danny
ls -la /home/danny
```

Reboot.

---

### Post by DannyP87 on 2009-03-07
Think I may have a problem, a major one.

I did all the commands as you said and changed the details in gedit which were dannny to danny.

I followed with the other commands and when it got to sudo ```
chgrp -R danny /home/danny
```
it said permission denied, tried logging in into root status in terminal and again was denied.

Now I try and open any program it comes up with 

> **[SIZE="4"]Could not launch application[/SIZE]**
Failed to change to directory '/home/dannny' (No such file or directory)

PS Can't even open terminal. Using Opera as that was still open as I altered the settings.

---

### Post by DannyP87 on 2009-03-07
Restarted and seems to be working now :?

Opera settings changed, lost my desktop background and Music, Pictures etc got removed from places menu ha.

At least its working though!

Anyone knows how to get Music, Pictures, Documents back onto the places menu I'd be grateful to know.

Thanks. Especially taurus ;)

---

### Post by taurus on 2009-03-07
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
df -h
ls -la ~
```

---

### Post by DannyP87 on 2009-03-07
As requested:

```
danny@Dannny-Desktop:~$ sudo fdisk -l
[sudo] password for danny: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26164   210162298+   7  HPFS/NTFS
/dev/sda2           26165       38913   102406342+   f  W95 Ext'd (LBA)
/dev/sda5           26165       37697    92638791   83  Linux
/dev/sda6           37698       38913     9767488+  82  Linux swap / Solaris

danny@Dannny-Desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3d6cab89-432b-4214-857b-5ef81f28fc2b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=97ae9f6d-3b18-4d65-8c80-c4ba8f4a490a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

danny@Dannny-Desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              87G  3.1G   80G   4% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  752K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1             201G   95G  107G  48% /media/disk

danny@Dannny-Desktop:~$ ls -la ~
total 252
drwxr-xr-x 44 danny danny  4096 2009-03-07 19:51 .
drwxr-xr-x  3 root  root   4096 2009-03-07 19:06 ..
drwx------  3 danny danny  4096 2008-12-12 09:16 .adobe
-rw-------  1 danny danny  1030 2009-03-07 16:22 .bash_history
-rw-r--r--  1 danny danny   220 2008-12-11 18:32 .bash_logout
-rw-r--r--  1 danny danny  3115 2008-12-11 18:32 .bashrc
drwx------  2 danny danny  4096 2009-03-03 19:38 .bogofilter
drwxr-xr-x  5 danny danny  4096 2009-03-02 21:03 .cache
drwx------  3 danny danny  4096 2008-12-11 18:50 .compiz
drwxr-xr-x  9 danny danny  4096 2009-03-05 19:18 .config
drwx------  3 danny danny  4096 2008-12-11 18:37 .dbus
drwxr-xr-x  2 danny danny  4096 2009-03-01 23:17 Desktop
-rw-------  1 danny danny    28 2009-03-07 19:51 .dmrc
drwxr-xr-x  2 danny danny  4096 2009-03-01 22:50 Documents
-rw-------  1 danny danny    16 2008-12-11 18:37 .esd_auth
drwxr-xr-x  8 danny danny  4096 2009-03-07 19:54 .evolution
lrwxrwxrwx  1 danny danny    26 2008-12-11 18:32 Examples -> /usr/share/example-content
drwxr-xr-x  2 danny danny  4096 2008-12-12 09:16 .fontconfig
drwx------  2 danny danny  4096 2008-12-12 13:54 .fr-t4a49D
drwx------  5 danny danny  4096 2009-03-07 19:51 .gconf
drwx------  2 danny danny  4096 2009-03-07 20:17 .gconfd
-rw-r-----  1 danny danny     0 2009-03-07 19:49 .gksu.lock
drwx------ 17 danny danny  4096 2009-03-07 19:50 .gnome2
drwx------  2 danny danny  4096 2008-12-11 18:38 .gnome2_private
drwx------  2 danny danny  4096 2009-03-03 19:31 .gnupg
drwxr-xr-x  2 danny danny  4096 2009-03-02 21:02 .gstreamer-0.10
-rw-r--r--  1 danny danny   112 2009-03-07 16:02 .gtk-bookmarks
dr-x------  2 danny danny     0 2009-03-07 19:51 .gvfs
-rw-------  1 danny danny  7000 2009-03-07 19:51 .ICEauthority
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:41 .icons
drwx------  3 danny danny  4096 2008-12-11 18:38 .local
drwx------  3 danny danny  4096 2008-12-12 09:16 .macromedia
drwx------  4 danny danny  4096 2008-12-11 18:39 .mozilla
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:37 Music
drwxr-xr-x  3 danny danny  4096 2009-03-07 19:50 .nautilus
drwx------  3 danny danny  4096 2009-03-07 17:40 .openoffice.org2
drwx------ 12 danny danny  4096 2009-03-07 20:01 .opera
drwxr-xr-x  4 danny danny  4096 2009-03-07 15:34 .orca
drwxr-xr-x  3 danny danny  4096 2009-03-04 21:46 Pictures
-rw-r--r--  1 danny danny   675 2008-12-11 18:32 .profile
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:37 Public
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:38 .pulse
-rw-------  1 danny danny   256 2008-12-11 18:37 .pulse-cookie
drwx------  6 danny danny  4096 2009-03-01 23:15 .purple
drwxr-xr-x  2 danny danny  4096 2008-12-12 09:08 .qt
-rw-------  1 danny danny  4829 2009-03-07 19:38 .recently-used.xbel
-rw-r--r--  1 danny danny     0 2008-12-12 09:05 .sudo_as_admin_successful
drwxr-xr-x  4 danny danny  4096 2009-03-01 22:51 .sudoku
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:37 Templates
drwxr-xr-x  7 danny danny  4096 2009-03-02 20:37 .themes
drwxr-xr-x  2 danny danny  4096 2009-02-27 17:42 Themes
drwx------  5 danny danny  4096 2009-03-03 18:15 .thumbnails
drwxr-xr-x  4 danny danny  4096 2009-03-07 15:33 .tomboy
-rw-r--r--  1 danny danny  4843 2009-03-07 15:38 .tomboy.log
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:45 .update-manager-core
drwx------  2 danny danny  4096 2008-12-11 18:38 .update-notifier
drwxr-xr-x  2 danny danny  4096 2008-12-11 18:37 Videos
drwxr-xr-x  2 danny danny  4096 2009-03-07 15:38 .wapi
-rw-------  1 danny danny   252 2009-03-07 19:51 .Xauthority
-rw-r--r--  1 danny danny   129 2009-03-03 18:13 .xscreensaver-getimage.cache
-rw-r--r--  1 danny danny 13871 2009-03-07 20:17 .xsession-errors

danny@Dannny-Desktop:~$ 

```

Thanks ;)

---

### Post by taurus on 2009-03-07
Probably look in ~/.gnome2, ~/.gconf, & ~/.gnome2_private to make sure danny is still owned those directories/subdirectories and files.

---

### Post by t0p on 2009-03-07
> **DannyP87 said:**
> 
Anyone knows how to get Music, Pictures, Documents back onto the places menu I'd be grateful to know.


If you navigate to those directories (Music, Pictures, Documents) using the gui file manager, and then bookmark them (using the *Bookmarks* tab), those directories will appear in *Places*.

I think!

---

