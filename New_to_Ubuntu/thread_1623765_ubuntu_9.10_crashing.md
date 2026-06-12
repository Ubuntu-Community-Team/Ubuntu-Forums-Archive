---
title: "ubuntu 9.10 crashing"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by vik.gelin on 2010-11-17
i have been using ubuntu 9.10 karmic koala since past one and half year.Day before yesterday it was working fine ,but when i started it again in evening it was not able to log in my account.i have lots of very important data on mu hard disk and i cannot afford to loose it at any cost,its so valuable for me.its a kind request to all the volunteers if they can help me rectify this problem as soon as possible.i am able to log use the computer by booting from the ubuntu cd.plz hel me.
it displayed the following messages::
..........................................................
  Gave up waiting for the root device.common problem
- Boot Args(cat/proc/cmdline)
   - check rootdelay =(did the system wait long enough?)
   - check root =(did the system wait for the right [FONT="Arial"][/FONT]device?)
-Missing Modules(cat/proc/modules;ls/dev)
Alert! /dev/disk/by-uuid/9db4e8dd=f2be-4384-966e-b7e1141ea6cd does not exist. Dropping ta a shell!
Busy Box v1.13.3(ubuntu1:1.13.3-1ubuntu7)built-in shell(ash)enter help for a list of built in commands

(initramfs)_

---

### Post by BugBuster on 2010-11-17
Please run this command and post the output here:

```
#sudo blkid
```
This command will list the UUID's for the various partitions on your hard drive.

Then run this command and post the output as well;
```
 $cat /etc/fstab 
```

You can run the first command  from the live cd as well, but for the second one you have to use the path for your installed fstab instead of the one found on the livecd.

---

### Post by vik.gelin on 2010-11-17
ok i will do so now ..thank u for helping

---

### Post by vik.gelin on 2010-11-17
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo blkid
/dev/sda5: UUID="cd221729-077c-4618-b74c-5e70adde9f36" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="7032-AF04" TYPE="vfat" 
ubuntu@ubuntu:~$  $cat /etc/fstab
bash: /etc/fstab: Permission denied
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$

---

### Post by Verbeck on 2010-11-17
@[BugBuster]("http://ubuntuforums.org/member.php?u=639564")
shouldn't the commands be run without the # and $

edit :nvm

---

### Post by vik.gelin on 2010-11-17
what did i do wrong..i have done as u said..i am not very much acquainted with all the commands .plz tell me directly

---

### Post by BugBuster on 2010-11-17
> **Verbeck said:**
> @[BugBuster]("http://ubuntuforums.org/member.php?u=639564")
shouldn't the commands be run without the # and $

Yes, you are right..but I was just trying to denote the prompt!!

@vik.gelin

Did you make any changes to the partition scheme on your hard disk? Or remove a hard drive? Asking this because as you can see your karmic installation is looking for a partition that is not listed in the output of blkid.

---

### Post by vik.gelin on 2010-11-17
no i never did so ..but one or two times it got shut down in am improper way due to power cut off..but last time i loged in it perfectly .but dont know why at all this is happening ,,i never made any changes to the partitions and didnt either removed the hard disk.

---

### Post by BugBuster on 2010-11-17
> **vik.gelin said:**
> no i never did so ..but one or two times it got shut down in am improper way due to power cut off..but last time i loged in it perfectly .but dont know why at all this is happening ,,i never made any changes to the partitions and didnt either removed the hard disk.

Ok..could you please post the output of this command as well?

```
sudo fdisk -l
```

---

### Post by Verbeck on 2010-11-17
you're running the command from a live cd?
in that case, you need to mount the ubuntu partition and post the contents of /etc/fstab from that drive

example:
```

cat /media/partitionname/etc/fstab

```or just browse to /etc on that partition and open fstab with gedit

---

### Post by vik.gelin on 2010-11-17
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15a99644

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4696    37720588+  83  Linux
/dev/sda2            4697        4870     1397655    5  Extended
/dev/sda5            4697        4870     1397623+  82  Linux swap / Solaris

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders
Units = cylinders of 6600 * 512 = 3379200 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1188     3918832    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by vik.gelin on 2010-11-17
plz tell me how to mount tht ubuntu partition in this situation.

---

### Post by vik.gelin on 2010-11-17
not able to mount it .....its just saying 
ubuntu@ubuntu:~$ cat /media/partitionname/etc/fstab
cat: /media/partitionname/etc/fstab: No such file or directory

---

### Post by Verbeck on 2010-11-17
> **vik.gelin said:**
> plz tell me how to mount tht ubuntu partition in this situation.

normally, it would be under the places menu.
but blkid didn't show that drive. are you sure the wires are connected firmly?
also does the the BIOS detect it?

---

### Post by vik.gelin on 2010-11-17
i think the wires are correctly in place as i didnt  opened my cpu since past one month.

---

### Post by vik.gelin on 2010-11-17
i have checked in bios tht the hard disk is there and showing tht following 
IDE secondary master [SAMSUNG SP0411N]
when i entered this it showed the following thngs
IDE HDD  Auto Detection
IDE SECONDARY Master  [auto]
access mode   [auto]
capacity 40062 mb
cylinder  19177
 head  16
precomp 0
leading zone  19176
sector  255

---

### Post by Verbeck on 2010-11-17
well.. could you run this once again from a terminal to make sure its not detected?
```
sudo blkid -c /dev/null
```

---

### Post by vik.gelin on 2010-11-17
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="cd221729-077c-4618-b74c-5e70adde9f36" TYPE="swap" 
ubuntu@ubuntu:~$

---

### Post by Verbeck on 2010-11-17
it might be the lack of sleep, i turned out to be pretty stupid and missed the first post on this page >_<
```

sudo mkdir ~/Desktop/filesystem
sudo mount /dev/sda1 ~/Desktop/filesystem
```
the folder on the desktop named 'filesystem' should have the drive mounted

---

### Post by vik.gelin on 2010-11-17
sudo mkdir ~/Desktop/filesystem
mkdir: cannot create directory `/home/ubuntu/Desktop/filesystem': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 ~/Desktop/filesystem
mount: you must specify the filesystem type

---

### Post by vik.gelin on 2010-11-17
this command has worked .....it has mounted the file system ....but i cannot see my data on the my home directory..it is showing tht it is blank/.....why is it showing so...and tell me how should i proceed further so tht i can loging into my system normally

---

### Post by vik.gelin on 2010-11-17
ubuntu@ubuntu:~$ sudo mount /dev/sda1 ~/Desktop/filesystem -t ext4
ubuntu@ubuntu:~$ sudo mount /dev/sda1 ~/Desktop/filesystem -t ext4 -o force
mount: /dev/sda1 already mounted or /home/ubuntu/Desktop/filesystem busy
mount: according to mtab, /dev/sda1 is already mounted on /home/ubuntu/Desktop/filesystem
ubuntu@ubuntu:~$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ ~/Desktop
bash: /home/ubuntu/Desktop: is a directory
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ ls
examples.desktop  filesystem  ubiquity-gtkui.desktop
ubuntu@ubuntu:~/Desktop$ cd
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ ls
examples.desktop  filesystem  ubiquity-gtkui.desktop
ubuntu@ubuntu:~/Desktop$ 
ubuntu@ubuntu:~/Desktop$ cd ~/Desktop/filesystem
ubuntu@ubuntu:~/Desktop/filesystem$ ls
bin   cdrom  distro  home        initrd.img.old  lost+found  mnt  proc  sbin     srv  tmp  var      vmlinuz.old
boot  dev    etc     initrd.img  lib             media       opt  root  selinux  sys  usr  vmlinuz
ubuntu@ubuntu:~/Desktop/filesystem$ cd ~/Desktop/filesystem/home
ubuntu@ubuntu:~/Desktop/filesystem/home$ ls
deepak  vikram
ubuntu@ubuntu:~/Desktop/filesystem/home$ cd ~/Desktop/filesystem/home/vikram
bash: cd: /home/ubuntu/Desktop/filesystem/home/vikram: Permission denied
ubuntu@ubuntu:~/Desktop/filesystem/home$ ls
deepak  vikram
ubuntu@ubuntu:~/Desktop/filesystem/home$ cd ~/Desktop/filesystem/home/vikram/
bash: cd: /home/ubuntu/Desktop/filesystem/home/vikram/: Permission denied

---

### Post by Verbeck on 2010-11-17
root should be able to access the data.
for a graphical method, in a terminal, run
gksudo nautilus /home/ubuntu/Desktop/filesystem/home/vikram/
and you'll have root permission

as for the original error, this is just a guess and might not work.
restart your pc and press right shift to bring up the grub menu. then  press 'e'. replace both the uuid=dsada-sfasd-safasdf with /dev/sda1 and press  ctrl+x

---

### Post by vik.gelin on 2010-11-17
heeee heay dear friend it has opened the home folder and i can see most of the files ....but there are many directories with the name starting from .skype .emesene,.purple etc which i cannot see .i have some important data in those particular directories,,,,,,so what should i do now .....as u have told me ''restart your pc and press *right shift* to bring up the grub menu. then press 'e'. replace both the uuid=dsada-sfasd-safasdf with /dev/sda1 and press ctrl+x''
 so i have to press  shift when i restart it and then press`e` then ...next thng i didnt get.........
i am pasting the output also as follows

ubuntu@ubuntu:~$ gksudo nautilus /home/ubuntu/Desktop/filesystem/home/vikram/
(nautilus:3877): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3877): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3877): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3877): WARNING **: No marshaller for signature of signal 'ShareCreateError'

** (process:3895): WARNING **: Couldn't change nice value of process.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(2449): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

totem-video-thumbnailer couldn't open file 'file:///home/ubuntu/Desktop/filesystem/home/vikram/vlc-record-2010-10-19-11h56m01s-youtube.YouTube_-_Lady_Gaga_-_Bad_Romance.flv-.mp4'
Reason: The playback of this movie requires a MPEG-4 AAC decoder plugin which is not installed..

** (process:3901): WARNING **: Couldn't change nice value of process.
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(2449): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

totem-video-thumbnailer couldn't open file 'file:///home/ubuntu/Desktop/filesystem/home/vikram/vlc-record-2010-10-09-19h44m49s-youtube.YouTube_-_Linkin_Park_-_High_Voltage.flv-.mp4'
Reason: The playback of this movie requires a MPEG-4 AAC decoder plugin which is not installed..

** (process:3920): WARNING **: Couldn't change nice value of process.
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(2449): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

totem-video-thumbnailer couldn't open file 'file:///home/ubuntu/Desktop/filesystem/home/vikram/Music/krsna%20maha%20culture/abhay%20charan/Abhay%20Charan%20-%20005.wmv'
Reason: The playback of this movie requires a Advanced Streaming Format (ASF) demuxer plugin which is not installed..

** (process:3925): WARNING **: Couldn't change nice value of process.
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(2449): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

totem-video-thumbnailer couldn't open file 'file:///home/ubuntu/Desktop/filesystem/home/vikram/Music/krsna%20maha%20culture/abhay%20charan/Abhay%20Charan%20-%20006.wmv'
Reason: The playback of this movie requires a Advanced Streaming Format (ASF) demuxer plugin which is not installed..

** (process:3930): WARNING **: Couldn't change nice value of process.
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(2449): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

totem-video-thumbnailer couldn't open file 'file:///home/ubuntu/Desktop/filesystem/home/vikram/Music/krsna%20maha%20culture/abhay%20charan/Abhay%20Charan%20-%20007.wmv'
Reason: The playback of this movie requires a Advanced Streaming Format (ASF) demuxer plugin which is not installed..

** (process:3947): WARNING **: Couldn't change nice value of process.
** Message: Error: Your GStreamer installation is missing a plug-in.
gstdecodebin2.c(2449): gst_decode_bin_expose (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20:
no suitable plugins found

totem-video-thumbnailer couldn't open file 'file:///home/ubuntu/Desktop/filesystem/home/vikram/Videos/malgudi%20days/malgudidays.Malgudi_Days_Watch_Online_Videos_Malgudi_Days_-_Episode_1.flv'
Reason: The playback of this movie requires a Sorenson Spark Video decoder plugin which is not installed..

--- Hash table keys for warning below:
--> user #1000
--> inode/directory
--> 1000
--> l2049

(nautilus:3877): Eel-WARNING **: "unique eel_ref_str" hash table still has 4 elements at quit time (keys above)

(nautilus:3877): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 13 elements at quit time
ubuntu@ubuntu:~$ 



........................................now the home directory did opened ,but when i closed tht and tried to again open by clicking the mounted filesystem on the destktop ..it is showing nothng again...tell me what is the problem..................

sir u have helped me a lot ,i am really very very thankful..plz tell me little bit so tht it will be solved..thank u

---

### Post by Verbeck on 2010-11-17
its just a guess, it might not work

after restarting the pc, press 'right shift' to bring up the grub menu
should look like this
[http://www.davestechsupport.com/blog/images/grub.png](http://www.davestechsupport.com/blog/images/grub.png)

then press 'e' while the ubutnu entry is highlighted
[http://www.codeweblog.com/upload/g/r/grub2-essentials-amendment-change_1.png](http://www.codeweblog.com/upload/g/r/grub2-essentials-amendment-change_1.png)

edit only the 'root=uuid=some-numbers ro quite splash' to
root=/dev/sda1 ro quite splash

---

### Post by vik.gelin on 2010-11-17
yes u r right..when i restart my ubuntu there do appears a screen as shown in 
[http://www.davestechsupport.com/blog/images/grub.png](http://www.davestechsupport.com/blog/images/grub.png)
  but there are many other options too like 
ubuntu kernel x.y.z. version 3
ubuntu kernel x.y.z. version 3 (recovery mode)
ubuntu kernel x.y.z. version  2
ubuntu kernel x.y.z. version 2(recpvery mode)

but when i click the latest grub one which at the top 
then a blank screen appears
it shows nothing
but when i press any key it enters the very frst screen as i mentioned earlier with somethng like :::


Gave up waiting for the root device.common problem
- Boot Args(cat/proc/cmdline)
   - check rootdelay =(did the system wait long enough?)
   - check root =(did the system wait for the right device?)
-Missing Modules(cat/proc/modules;ls/dev)
Alert! /dev/disk/by-uuid/9db4e8dd=f2be-4384-966e-b7e1141ea6cd does not exist. Dropping ta a shell!
Busy Box v1.13.3(ubuntu1:1.13.3-1ubuntu7)built-in shell(ash)enter help for a list of built in commands

(initramfs)_

---

### Post by vik.gelin on 2010-11-19
> **vik.gelin said:**
> yes u r right..when i restart my ubuntu there do appears a screen as shown in 
[http://www.davestechsupport.com/blog/images/grub.png](http://www.davestechsupport.com/blog/images/grub.png)
  but there are many other options too like 
ubuntu kernel x.y.z. version 3
ubuntu kernel x.y.z. version 3 (recovery mode)
ubuntu kernel x.y.z. version  2
ubuntu kernel x.y.z. version 2(recpvery mode)

but when i click the latest grub one which at the top 
then a blank screen appears
it shows nothing
but when i press any key it enters the very frst screen as i mentioned earlier with somethng like :::


Gave up waiting for the root device.common problem
- Boot Args(cat/proc/cmdline)
   - check rootdelay =(did the system wait long enough?)
   - check root =(did the system wait for the right device?)
-Missing Modules(cat/proc/modules;ls/dev)
Alert! /dev/disk/by-uuid/9db4e8dd=f2be-4384-966e-b7e1141ea6cd does not exist. Dropping ta a shell!
Busy Box v1.13.3(ubuntu1:1.13.3-1ubuntu7)built-in shell(ash)enter help for a list of built in commands

(initramfs)_
[QUOTE=Verbeck]well.. i stumped at how it got fixed...

the error you're getting means the system cant write to the file: its an  authentication file used by programs. to fix it, after logging in, run  the following commands in a terminal.

```

sudo chown vikram:vikram /home/vikram/.ICEauthority

``````

sudo chmod 600 /home/vikram/.ICEauthority
```then log out and login[/QUOTE]


...................................................................................................................................

\\ i ran both the commands as u mentioned adove but still it is showing  the same message that ""cannot update .ICEauthority file '' and it is  showing two more problems if u can help me sole them too please..they  are
 1.-->my sound device is not showing up ,,i cannot increase or  decrease the volume of my system,,i am able to hear the files playing in  vlc and can increase and decrease it by the vlc volume control ....but i  cannot see the ubuntu volume control in control menu or in the  preference menu when i click on 'sound' option it fail to  open it. how  to bring my sound device working .......when later i was talking on  skype ,i was able to hear the other person speaking but my microphone  was not responding ...other person was not at all able to hear me,,i  tried a lot to bring sound control ,,but failed ....sir please help me..  
 2.--> my skype call recorder is also not working:cry: ,,may be it is also related to the above mentioned sound device problem....plz help:smile:

---

