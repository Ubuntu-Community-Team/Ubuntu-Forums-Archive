---
title: "644  permission problem than major mistake by me"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-02-06
i was getting the 644 error-users doesnt own home directory and was trying to fix then really messed up. my home folder is on a separate partition and now i cant access it. i have tried failsafe terminal etc and now on live 8.10 cd. my home folder used to be 1000 but somehow i have changed it to owner 755 and i have only 
list /create delete and no access to 
how i can i correct.
note when i reboot off live cd can access my daughter which has a file of 1001 but not mine of 1000. hopefully easy way to fix. speedy reply would be nice but i know you are all busy/cheesemaker

---

### Post by rburkartjo on 2009-02-06
note have not deleted anything just cant access/cheesemaker

---

### Post by taurus on 2009-02-06
Boot from the LiveCD and mount the partition where your /home is located.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Then, you can change the UID for your $HOME from 755 (that looks like you were trying to change permissions but somehow using the wrong command!) back to 1000.

p.s.  Which partition is your /home from the output above?

---

### Post by rburkartjo on 2009-02-06
taurus home is on /dev/sda4 ext3/cheesemaker

---

### Post by taurus on 2009-02-06
From the LiveCD, run

```
sudo mkdir /media/home
sudo mount -t ext3 /dev/sda4 /media/home
sudo chown -R 1000:1000 /media/home/cheesemaker
sudo chmod 755 /media/home/cheesemaker
sudo chmod 644 /media/home/cheesemaker/.dmrc
ls -la /media/home
```
I assume _cheesemaker_ is your login name!

---

### Post by rburkartjo on 2009-02-06
taurus and how do it do that/cheesemaker

---

### Post by taurus on 2009-02-06
> **rburkartjo said:**
> taurus and how do it do that/cheesemaker

Not sure what you mean here?  How do you run those commands?  You can do that from the LiveCD.  Once the LiveCD finished booting, open a terminal, Applications -> Accessories -> Terminal, and type in one line at a time.

---

### Post by rburkartjo on 2009-02-06
taurus didnt worked tried three time look at this output my home is under ray just use cheesemaker cause i am one. if i could change my permission to be the same as the first kat(my daughter) i think i would be good to go but how do i do this
4 drwxr-xr-x 34 1001 1001  4096 2009-02-06 20:17 kat
16 drwx------  2 root root 16384 2009-01-31 00:21 lost+found
 4 drw-r--r-- 54  644 1000  4096 2009-02-06 18:45 ray
tks/cheesemaker

---

### Post by taurus on 2009-02-06
Assuming you still mount /dev/sda4 to /media/home from the LiveCD, try

```
sudo chown -R 1000 /media/home/ray
sudo chmod 755 /media/home/ray
sudo chmod 644 /media/home/ray/.dmrc
ls -la /media/home
```
Post the output of the last command here.

---

### Post by rburkartjo on 2009-02-06
taurus,must be one of those days that worked kind of. all is restored however i have no sound under my desktop okay with my daughters desktop and i have no internet connection under either any idea how to fix. i have the connection with the live cd which i am using now. i really appreciate all the help and if you or someone could help me with this i will shutup for the day./cheesemaker

---

### Post by rburkartjo on 2009-02-06
if this helps at all when i tried to do a sytem backup i got this error message when tried to do so in the terminal sudo:must be setuid root/cheesemaker

---

### Post by rburkartjo on 2009-02-06
and of course i couldnt install the backup/cheesemaker

---

### Post by taurus on 2009-02-06
Do you belong to group admin?

```
id
```

---

### Post by rburkartjo on 2009-02-06
taurus how do i check while in the live cd/cheesemaker

---

### Post by rburkartjo on 2009-02-06
okay i got this far under ray properties it shows owner is 1000 folder options create and delete files   group 1000 folder access access files
others folder access access files and note on bottom you are not the owner so you cant change these permissions.

---

### Post by rburkartjo on 2009-02-06
note this link

[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)

maybe the above is relevant/cheesemaker

---

### Post by rburkartjo on 2009-02-06
there must be away to fix tks for all who have read this so far. got to get some sleep will check back in the am/cheesemaker

---

### Post by taurus on 2009-02-06
Post the output of this command from a terminal.

```
ls -la /home/ray
```

---

### Post by rburkartjo on 2009-02-06
note maybe because i am in the live cd but got this and i know it is wrong
ubuntu@ubuntu:~$ ls -la /home/ray
ls: cannot access /home/ray: No such file or directory
ubuntu@ubuntu:~$ 
it is there i can access it when i mount my  home partition/cheesemaker

---

### Post by taurus on 2009-02-06
If you are running off the LiveCD and you have mounted /dev/sda4 to /media/home, then the command now should be

```
sudo ls -la /media/home/ray
```

---

### Post by theozzlives on 2009-02-06
The problem you had happened to me when I tried to share my /home/ozzie folder and gave write permissions (apparently not allowed). Did you do that?

---

### Post by rburkartjo on 2009-02-06
taurus i get this 


ubuntu@ubuntu:~$ sudo ls -la /media/home/ray
ls: cannot access /media/home/ray: No such file or directory
ubuntu@ubuntu:~$ sudo ls -la /media/home/ray
ls: cannot access /media/home/ray: No such file or directory
ubuntu@ubuntu:~$ 



that is wrong my home is on dev/dsa4 ext3 i can mount the volume and look at it?/cheesemaker

---

### Post by taurus on 2009-02-06
Then where did you mount /dev/sda4?

```
df -h
```

---

### Post by rburkartjo on 2009-02-06
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  104K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.9M  1.7G   1% /dev
tmpfs                 1.7G  124K  1.7G   1% /dev/shm
rootfs                1.7G   58M  1.7G   4% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.7G   28K  1.7G   1% /tmp
/dev/sda4              27G  1.2G   25G   5% /media/disk
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-02-06
```
sudo ls -la /media/disk/home/ray
```

---

### Post by rburkartjo on 2009-02-06
ubuntu@ubuntu:~$ sudo ls -la /media/disk/home/ray
ls: cannot access /media/disk/home/ray: No such file or directory
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-02-06
```
ls -la /media/disk
```

---

### Post by rburkartjo on 2009-02-06
ubuntu@ubuntu:~$ ls -la /media/disk
total 28
drwxr-xr-x  5 root root  4096 2009-01-31 00:57 .
drwxr-xr-x  3 root root   100 2009-02-07 03:52 ..
drwxr-xr-x 34 1001 1001  4096 2009-02-07 02:48 kat
drwx------  2 root root 16384 2009-01-31 00:21 lost+found
drwxr-xr-x 61 1000 1000  4096 2009-02-07 02:49 ray
ubuntu@ubuntu:~$ 

if i set the root to the same permissions as kat and ray would this maybe fix and how would i do it just a thought/cheesemaker

---

### Post by taurus on 2009-02-06
```
ls -la /media/disk/ray
```

I have no idea what you meant by "set the root to the same permissions as kat and ray".

---

### Post by rburkartjo on 2009-02-06
ubuntu@ubuntu:~$ ls -la /media/disk/ray
total 15828
drwxr-xr-x 61 1000 1000     4096 2009-02-07 02:49 .
drwxr-xr-x  5 root root     4096 2009-01-31 00:57 ..
-rw-r--r--  1 1000 1000   309384 2009-01-21 07:11 1208_splash.xpm
drwx------  3 1000 1000     4096 2009-01-19 01:18 .adobe
drwx------  8 1000 1000     4096 2009-01-21 09:42 .amsn
drwx------  2 1000 1000     4096 2009-01-21 09:40 amsn_received
-rw-------  1 1000 1000     1296 2009-02-06 22:38 .bash_history
-rw-r--r--  1 1000 1000      220 2009-01-18 23:26 .bash_logout
-rw-r--r--  1 1000 1000     3115 2009-01-18 23:26 .bashrc
drwxr-xr-x  5 1000 1000     4096 2009-01-21 16:53 .cache
drwx------  3 1000 1000     4096 2009-01-20 09:54 .checkgmail
drwxrwxrwx 22 1000 1000     4096 2009-01-19 21:15 clamav-0.94.2
drwxr-xr-x  5 1000 1000     4096 2009-01-19 21:29 .clamtk
drwx------  3 1000 1000     4096 2009-01-21 16:37 .compiz
drwxr-xr-x 14 1000 1000     4096 2009-02-07 02:35 .config
drwx------  3 1000 1000     4096 2009-01-18 23:30 .dbus
drwxr-xr-x  4 1000 1000     4096 2009-01-21 17:21 Desktop
-rw-------  1 1000 1000       28 2009-02-07 02:35 .dmrc
drwxr-xr-x  2 1000 1000     4096 2009-01-31 00:33 Documents
-rw-------  1 1000 1000       16 2009-01-18 23:30 .esd_auth
drwxr-xr-x  3 1000 1000     4096 2009-01-21 09:49 .evolution
drwxr-xr-x  6 1000 1000     4096 2009-01-21 10:13 .exaile
lrwxrwxrwx  1 1000 1000       26 2009-02-06 22:31 Examples -> /usr/share/example-content
drwxr-xr-x  2 1000 1000     4096 2009-01-21 16:06 .fontconfig
drwx------  4 1000 1000     4096 2009-02-07 02:35 .gconf
drwx------  2 1000 1000     4096 2009-02-07 02:49 .gconfd
-rw-r-----  1 1000 1000        0 2009-01-20 23:01 .gksu.lock
drwxr-xr-x  3 1000 1000     4096 2009-01-19 00:53 .gnome
drwx------ 13 1000 1000     4096 2009-01-21 18:11 .gnome2
drwx------  2 1000 1000     4096 2009-01-18 23:30 .gnome2_private
drwx------  2 1000 1000     4096 2009-01-18 23:30 .gnupg
-rw-r--r--  1 1000 1000      331 2009-02-06 14:26 .gshutdown
drwxr-xr-x  2 1000 1000     4096 2009-01-19 00:48 .gstreamer-0.10
-rw-r--r--  1 1000 1000      100 2009-02-07 02:36 .gtk-bookmarks
dr-x------  2 1000 1000     4096 2009-01-21 16:44 .gvfs
drwxr-xr-x  2 1000 1000     4096 2009-01-31 12:11 .helix
drwxr-xr-x  2 1000 1000     4096 2009-01-21 17:10 .hubackup-data
-rw-------  1 1000 1000     5110 2009-02-07 02:35 .ICEauthority
drwxr-xr-x  4 1000 1000     4096 2009-01-19 01:22 .icons
drwx------  3 1000 1000     4096 2009-01-21 16:15 .kde
lrwxrwxrwx  1 1000 1000       25 2009-02-06 22:31 Link to Documents -> /media/disk/ray/Documents
drwx------  3 1000 1000     4096 2009-01-18 23:30 .local
drwx------  3 1000 1000     4096 2009-01-19 01:18 .macromedia
-rw-r--r--  1 1000 1000     3146 2009-01-31 12:11 .mailcap
drwxr-xr-x  3 1000 1000     4096 2009-01-31 12:01 .mcop
-rw-------  1 1000 1000       31 2009-01-31 12:01 .mcoprc
drwxr-xr-x  5 1000 1000     4096 2009-02-04 00:19 .miro
drwx------  5 1000 1000     4096 2009-01-19 01:05 .mozilla
drwxr-xr-x  2 1000 1000     4096 2009-01-18 23:30 Music
drwxr-xr-x  3 1000 1000     4096 2009-01-21 16:41 .nautilus
drwxr-xr-x  2 1000 1000     4096 2009-02-06 11:03 .neverball
-rw-------  1 1000 1000      200 2009-01-20 09:52 .notifier.conf
drwxr-xr-x  3 1000 1000     4096 2009-02-01 06:56 .openoffice.org
drwx------  3 1000 1000     4096 2009-01-21 16:45 .openoffice.org2
drwxr-xr-x  3 1000 1000     4096 2009-01-21 09:45 Pictures
-rw-r--r--  1 1000 1000      675 2009-01-18 23:26 .profile
drwxr-xr-x  2 1000 1000     4096 2009-01-18 23:30 Public
drwxr-xr-x  2 1000 1000     4096 2009-02-07 02:49 .pulse
-rw-------  1 1000 1000      256 2009-01-18 23:30 .pulse-cookie
drwx------  4 1000 1000     4096 2009-01-21 15:58 .purple
drwx------  6 1000 1000     4096 2009-01-19 01:24 .pysol
drwx------  3 1000 1000     4096 2009-01-20 02:11 .qalculate
drwxr-xr-x  2 1000 1000     4096 2009-01-31 12:01 .qt
-rw-------  1 1000 1000     1239 2009-02-06 22:31 .recently-used
-rw-------  1 1000 1000    20112 2009-02-07 02:44 .recently-used.xbel
drwx------  3 1000 1000     4096 2009-01-21 10:20 .Skype
-rw-r--r--  1 1000 1000 15504764 2009-01-21 10:00 skype-debian_2.0.0.72-1_i386.deb
drwx------  5 1000 1000     4096 2009-01-20 20:13 .songbird2
-rw-r--r--  1 1000 1000        0 2009-01-18 23:36 .sudo_as_admin_successful
drwxr-xr-x  2 1000 1000     4096 2009-01-18 23:30 Templates
drwxr-xr-x 19 1000 1000     4096 2009-01-19 01:22 .themes
drwx------  4 1000 1000     4096 2009-01-18 23:31 .thumbnails
drwx------  2 1000 1000     4096 2009-02-07 02:44 .tsclient
drwxr-xr-x  2 1000 1000     4096 2009-01-18 23:36 .update-manager-core
drwx------  2 1000 1000     4096 2009-01-18 23:30 .update-notifier
drwxr-xr-x  3 1000 1000     4096 2009-01-21 09:45 Videos
drwxr-xr-x  2 1000 1000     4096 2009-01-21 16:22 .wallpapoz
drwxr-xr-x  4 1000 1000     4096 2007-05-31 06:05 wallpapoz-0.4
drwxr-xr-x  2 1000 1000     4096 2009-02-07 02:36 .wapi
drwxr-xr-x  4 1000 1000     4096 2009-01-21 18:08 .wine
drwxr-xr-x  2 1000 1000     4096 2009-02-03 23:43 WolfQuest
-rw-------  1 1000 1000       56 2009-02-07 02:49 .Xauthority
drwxr-xr-x  2 1000 1000     4096 2009-02-02 00:04 .xine
-rw-r--r--  1 1000 1000    27963 2009-02-07 02:44 .xsession-errors
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-02-06
Everything looks fine to me so you still can't log in with your username, ray, and password?

---

### Post by rburkartjo on 2009-02-06
i can log on as user password etc all fine again i cant access volume on ray or internet and on kat i have sound but no internet i though cant use sudo i noted sudo:must be setuid root error on one of the previous pages and a link but couldnt figure it out if i could get this to work i could access my systembackup and reinstall but without this fix i cant do that/cheesemaker

---

### Post by taurus on 2009-02-06
That is why I asked you a question back in post #13 to see which groups you belong to.  Boot Ubuntu from your harddrive and post the output of that command to see if you still belong to group admin.  If you are not, then sudo won't work.

```
id
```

---

### Post by rburkartjo on 2009-02-06
okay will do i didnt understand that before back in a few/cheesemaker

---

### Post by rburkartjo on 2009-02-06
ray@localhost:~$ id 
uid=1000(ray) gid=1000(ray) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(ray),1002(root) 
ray@localhost:~$

---

### Post by taurus on 2009-02-06
> **rburkartjo said:**
> ray@localhost:~$ id 
uid=1000(ray) gid=1000(ray) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(ray),**[COLOR="Blue"][COLOR="Red"]1002(root)[/COLOR][/COLOR]** 
ray@localhost:~$

Why is there a root with GID of 1002 on your machine?  There is already root account (UID/GID of 0) so I am not sure exactly what you were trying to do to create a root GID of 1002?

What are the outputs of these two commands?

```
cat /etc/passwd
cat /etc/group
```

---

### Post by rburkartjo on 2009-02-06
should i get out of the live cd to get that output/ray

---

### Post by taurus on 2009-02-06
Maybe creating a new root group with 1002 (I still don't understand why you would do that) causes all those trouble on your machine.  

Run those two commands when you boot from the harddrive, not the LiveCD.

---

### Post by rburkartjo on 2009-02-06
okay back in a few /cheesemaker

---

### Post by rburkartjo on 2009-02-07
taurus, i probably really messed things up when trying to solve the 644 error problem had to use the gnome fail safe terminal and must of goofed up.
here is what you reguested
it is in more than i post
ray@localhost:~$ cat /etc/passwd 
root:x:0:1002:root:/root:/bin/bash 
daemon:x:1:1:daemon:/usr/sbin:/bin/sh 
bin:x:2:2:bin:/bin:/bin/sh 
sys:x:3:3:sys:/dev:/bin/sh

---

### Post by taurus on 2009-02-07
> **rburkartjo said:**
> taurus, i probably really messed things up when trying to solve the 644 error problem had to use the gnome fail safe terminal and must of goofed up.
here is what you reguested
it is in more than i post
ray@localhost:~$ cat /etc/passwd 
root:x:0:**[COLOR="DarkRed"]1002[/COLOR]**:root:/root:/bin/bash 
daemon:x:1:1:daemon:/usr/sbin:/bin/sh 
bin:x:2:2:bin:/bin:/bin/sh 
sys:x:3:3:sys:/dev:/bin/sh

You are missing a bunch of entries in /etc/passwd if that is all you've got on your machine!  

You need to boot into recovery mode from GRUB menu and edit /etc/passwd

```
nano -Bw /etc/passwd
```
and replace the 1002 for root (first line) back to 0.  Save it and exit with <Ctrl>x and Y for the question.  Then, you need to examine /etc/group to make sure there is no group 1002 that belongs to root.  In other words, the first line in /etc/group should look like this.

```
root:x:0:
```

---

### Post by rburkartjo on 2009-02-07
taurus ,tks i had to you the info you wanted too long to post and i couldnt get those stupid smiley faces out ot it. will try what you said/ray

---

### Post by rburkartjo on 2009-02-07
2/7/09 4:35pm
taurus back online/cheesemaker

---

