---
title: "how do i know on which partition a folder is in linux?"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by ustulation on 2011-02-16
for instance in windows if i see c: and d: drives and if i click to go into d: then i'm certain that i'v entered a different partition than i would have if i had clicked c: ... but in ubuntu, i see / and a whole lot of folders in it...on some else's system how can i know which one (say /home, /tmp etc) is in the same partition as / and which one is in different without using other software tools like gparted.. being new it's appearing counter-intutive to me

---

### Post by jwcalla on 2011-02-16
```
df /home
```

or just "df" without any arguments can give you a hint for each partition

It's kind of designed to be completely transparent from a filesystem perspective. The user could go to /htpc and it could be a directory that's actually stored on a harddrive in the living room, and the user wouldn't even know any different from typical operation.

---

### Post by Paqman on 2011-02-16
Well, you won't be able to see that info in the file manager, no. But you can see it in places like System Monitor. I guess the people who designed the file manager don't really think it's important to expose that information to you.

---

### Post by ustulation on 2011-02-16
thank u jwcalla & Paqman... but /dev is also a folder...df /dev didnt give anything... does df work on every folder?

---

### Post by sanderd17 on 2011-02-16
/dev contains hardware parts, so it's not on your HDD.

The linux phylosofy is "everything is a file", so even hardware components are files. you can read info about it by reading the file, or write settings to it by writing to the file. This way, applications can simlpy implement those things.

---

### Post by jwcalla on 2011-02-16
> **ustulation said:**
> thank u jwcalla & Paqman... but /dev is also a folder...df /dev didnt give anything... does df work on every folder?

df works on every folder (and file) but the files in /dev (devices) and /proc (processes) are special.  special like all of us.

i don't think they're stored on a filesystem -- probably stored in memory some place

---

### Post by Paqman on 2011-02-16
> **ustulation said:**
> but /dev is also a folder...

That's a *nix thing: "everything is a file". You'll find that actual hardware and devices show up as files in the filesystem. So a partition might show up as /dev/sda1 (which is the actual hardware) and also as / (which is its mount point in the filesystem. You wouldn't ever put data into /dev, you put it into where the drive is mounted.

---

### Post by jwcalla on 2011-02-16
> **sanderd17 said:**
> /dev contains hardware parts, so it's not on your HDD.

The linux phylosofy is "everything is a file", so even hardware components are files. you can read info about it by reading the file, or write settings to it by writing to the file. This way, applications can simlpy implement those things.

Isn't it exciting?

For example if I type "tty" I learn that my console is operating on device /dev/pts/1.  So I can write a file to that device "cat /etc/X11/xorg.conf > /dev/pts/1" and voila -- it prints out on my console.

And that's how we can rip blu-ray disks straight from /dev/sr0.
(oops... did I say that out loud?)

---

### Post by asmoore82 on 2011-02-16
+1 for System Monitor
"System -> Administration -> System Monitor -> File Systems Tab"

-or-
```
mount
```
with no arguments

-or-
```
df
```
with no arguments

---

### Post by ustulation on 2011-02-16
thanks to all...
@jwcalla "For example if I type "tty" I learn that my console is operating on device /dev/pts/1. So I can write a file to that device "cat /etc/X11/xorg.conf > /dev/pts/1" and voila -- it prints out on my console."


v. interesting....i tried that...so it means that if df /home returns /dev/sdc8 and i add information to /dev/sdc8 file (in an appropriate manner) it would immediately reflect on the mounted interface, ie., the visual i get in the file manager?..

---

### Post by grahammechanical on 2011-02-16
I have four partitions on my hard disc. I know where I am going when I select each one.

When I go to the Places menu I select Home folder. The Nautilus file manager opens and the folders and the files in the folders are on my /home partition - my largest partition. I look at the panel on the left side. I see three hard disc icons. File system is the 20GB partition that my standard Ubuntu is installed in. The  10GB File System is where I have installed Ubuntu Studio to test it out. The 9.6GB Files System is where I have installed Mandriva and where I am thinking of installing Edubuntu after the next release to test it out. I can access the folders and files on each of these.

So, what is your problem. This is easier to work with than in Windows. On a simple system for someone who just wants to use the computer without knowing about drive C: this or drive D: that, it is great.

Regards.

---

### Post by jwcalla on 2011-02-16
> **ustulation said:**
> thanks to all...
v. interesting....i tried that...so it means that if df /home returns /dev/sdc8 and i add information to /dev/sdc8 file (in an appropriate manner) it would immediately reflect on the mounted interface, ie., the visual i get in the file manager?..

That sounds very naughty.  I'm not sure if that would work or not, since there is some filesystem abstraction going on when the disk is mounted (filesystem type, flags, etc.) that indicates where on the partition files are to be stored, the file name, file attributes... there's a file table also that has to be maintained, etc.  You could write something there, but it'd be pretty raw and go right onto the disk, and likely overwrite who knows what.  So yes, never do that.  :)  Fortunately you don't have permission to do it either.  ;)

---

### Post by ustulation on 2011-02-16
@jwcalla  ok..great..thanks mate

@grahammechanical:: yes, right u r!! but my problem was not so much with the filesystems displayed on the left in the file manager.. they give an impression that they belong to a different partition...i wanted to know abt the ones not listed there...like /home (and may be /etc, /tmp and others which i'v not configured on different partitions so i dont really know)... df seems to be a nice start...

---

### Post by ustulation on 2011-02-16
and oh !!...on googling i found this, if its interesting to anybody::
[http://www.ibm.com/developerworks/linux/library/l-linux-filesystem/](http://www.ibm.com/developerworks/linux/library/l-linux-filesystem/)

will spend sometime to get used to it :)

---

### Post by JKyleOKC on 2011-02-16
You could only do that if you were logged in as the super user, or had "root power" for the duration of the command -- and it would probably overwrite some critical structure and make your system unusable, and unrecoverable. I wouldn't recommend trying it. However the command "dd if=/dev/sr0 of=$HOME/MyCD.iso" would create an exact copy of the CD in your drive (if, like mine, the drive was known as sr0) in the file "MyCD.iso" within your home directory. You could then feed that CD image to the burner software to create a copy, or mount it as a separate partition to get data from it without having the CD in its drive at all.

---

### Post by ustulation on 2011-02-16
@JKyleOKC.. yes..thnks..m getting the hang of it now

---

### Post by jwcalla on 2011-02-16
As you can see the unix variants expose a lot more of the inner workings to the end user.  This means you can hang yourself, but you can also learn a ton if you're interested in how things work.  It's okay to experiment a bit, just know the risks and keep a backup on hand... ;)

---

