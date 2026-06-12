---
title: "can,t upgrade from cdrom or mount it at all"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by brianbeswick on 2011-06-19
Hey , I'm definitly a noob! I was trying to get some packages from my natty cdrom that weren"t installed in my recent installation. I've tried synaptic package manager , software center, or when I #apt-cdrom add# it says that the mount failed, its not listed in /etc/fstab or /etc/mtab, but the cdrom mounts fine when I insert it. can some one help me. I hoe I posted this right? Thanx.:???:

---

### Post by jtarin on 2011-06-19
Try the command ```
eject -n
``` in the terminal and post the results.

---

### Post by brianbeswick on 2011-06-19
ok let me boot back into ubuntu.

---

### Post by brianbeswick on 2011-06-19
ok I'm back heres the results <brian@ubuntu:~$ eject -n
eject: device is `/dev/sr0'
brian@ubuntu:~$ >
Oh and by the way, how do you post with the box around the code. I'm sorry if I've been posting wrong. I noticed that all the post have it, and I don't want to be a complete idiot.

---

### Post by jtarin on 2011-06-19
In the "advanced" reply box you will see in the menu "#" (pound sign)for code insertion. 
Back to the problem.....Using Nautilus file manager go to your /media directory and see if you have any directory relevant to your CD drive and post back.

---

### Post by brianbeswick on 2011-06-19
I don't have Nautilus installed, but in my media file it shows two files cdrom(empty) and Ubuntu 11.04 i386, so I know its mounted.Oh and thanx for the ```
code insertion info
```:p

---

### Post by jtarin on 2011-06-20
> **brianbeswick said:**
> I don't have Nautilus installed, but in my media file it shows two files cdrom(empty) and Ubuntu 11.04 i386, so I know its mounted.Oh and thanx for the ```
code insertion info
```:pOK...lets try to edit /etc/fstab.
In the terminal ```
gksu gedit /etc/fstab
```this will open fstab as root.
Now lets make a backup. While open in Gedit save to a location where you can find it or back to the /etc directory....save as "fstab.orig" (without quotes). 
Now lets edit the open file for your CD to mount at boot time.
At the bottom of your fstab file copy and paste this line.
```
/dev/scr0  /media/cdrom  udf,iso9660  user,noauto,exec,utf8  0  0
```Now save as /etc/fstab. Then reboot and see if we got it right. :P

---

### Post by brianbeswick on 2011-06-20
Ok sorry It took so long to resond. Had to sleep, have to work today. I'm not sure if I did some thing wrong but my /fstab is blank. I```
 gksu gedit /fstab 
```and gedit opened to [ATTACH]195567[/ATTACH]
not sure what hapend. thanx again for your patients. Now I'm kinda worried to shut off my computer cause thats what happend last time I couldn't boot. its probably nothing though. Actualy I think I could boot but it took a really long time.  p.s I hope I posted my screen shot right.

---

### Post by westie457 on 2011-06-20
> **brianbeswick said:**
> Ok sorry It took so long to resond. Had to sleep, have to work today. I'm not sure if I did some thing wrong but my /fstab is blank. I```
 gksu gedit /fstab 
```and gedit opened to [ATTACH]195567[/ATTACH]
not sure what hapend. thanx again for your patients. Now I'm kinda worried to shut off my computer cause thats what happend last time I couldn't boot. its probably nothing though. Actualy I think I could boot but it took a really long time.  p.s I hope I posted my screen shot right.

Hi You missed a bit out of the code that 'jtarin' provided. Suggest you try again

Copy and Paste is usually the best thing to do; Becuase normally my typing is rubbish and I miss bits as well. Just noticed that there is extra letters in here but I am not going to correct them.

When doing Copy and Paste use one line at a time. One line no matter how long is one command. Three lines is three commands.

---

### Post by jtarin on 2011-06-20
He's right....look at my previous post.

---

### Post by brianbeswick on 2011-06-20
Yep! Your both right. In my haste I forget to type the entire file name. Sorry, I knew I would do something foolish, but I guess I can blame it on being tired. Ha! I was also going over the thread, and noticed that my P isn't working. ...........Ha! 
                                                                                                                                            Insert joke here ^
I'll try again.

---

### Post by brianbeswick on 2011-06-20
Ok, so here goes
   first
```
gksu gedit /etc/fstaband then 
```   and then
```
/dev/scr0  /media/cdrom  udf,iso9660  user,noauto,exec,utf8  0  0
```and then reboot[ATTACH]195632[/ATTACH]
Am I missing something. Hmmm? Again thanx for the help.

---

### Post by jtarin on 2011-06-20
Enter this command in the terminal and post back```
sudo blkid
```
Did you make the directory before you edited /etc/fstab?
> Remember that the mount point must already exist, otherwise the entry will not mount on the filesystem. To create a new mount point, use _**root privileges**_ to create the mount point.

---

### Post by brianbeswick on 2011-06-20
No I don't think so. Not sure though. Here is the results though.
[ATTACH]195636[/ATTACH]

---

### Post by jtarin on 2011-06-21
OK...it seems the /etc/fstab is not working so edit the line for CD(as root) to look like this```
/dev/scr0/media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```then remove(as root) the folder you created in /media .....reboot and try.

---

