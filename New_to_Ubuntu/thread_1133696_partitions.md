---
title: "partitions"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-04-23
I set up an out dated version of Ubuntu (7.04) on my machine and need to change it but before I do, I want to make sure I have the whole partitioning thing down pat - I want to do it manually this time. I used 'guided' for the outdated one, and it said it would make 5 partitions but when I look in 'My Computer' I just see 'hda1' and 'file system'. Does that mean it simply made 2 partitions or am I just unable to see them all?
 
mystmaiden

---

### Post by tom56 on 2009-04-23
Not quite sure what you mean. Guided is usually fine, just make sure it won't wipe out what you want to keep. If you want to do it manually, make sure you have a swap partion around 1.5x your memory size, and an ext3 / partition.

EDIT: Added a screenshot of how mine looks.
/dev/sda1 is my Windows Vista partition
/dev/sda5 is my /
/dev/sda6 is my swap
The numbering is a little funny because there was a Windows 7 partition but I deleted it to get some space back.

---

### Post by mystmaiden on 2009-04-23
Thanks for the screen shot. What I mean is when I open the 'My Computer' file, all I see is the hard drive and 'file system' so that I'm not actually seeing the separate drives? So if I want to save something to a drive, how would I do that?

---

### Post by anjilslaire on 2009-04-23
save it it your Home folder, which is also located in /home/mystmaiden/

When you look at it through "My Computer" it all appears as one, even if its really separate partitions.

---

### Post by drs305 on 2009-04-23
> **mystmaiden said:**
> Thanks for the screen shot. What I mean is when I open the 'My Computer' file, all I see is the hard drive and 'file system' so that I'm not actually seeing the separate drives? So if I want to save something to a drive, how would I do that?

Mounting can be a pretty complex topic. I'll use the command line, others can give you advice with gui apps. Let's start with the basics.

If you don't mind the command line, you can run the following command to see what drives/partitions are currently mounted on your machine. Open a terminal with Applications, Accessories, Terminal and then run the following. **NOTE ADDED: Dileeshvar offers an easier to read command in the next post, "df -h"**   ;-)
```

mount

```

You will get an output something like this:
> 
me@mycomputer:~$ mount
**/dev/sda10 on /** type ext4 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
**/dev/sda2 on /media/data** type ext3 (rw,nosuid,nodev,relatime,commit=60)
**/dev/sda3 on /media/av** type ext3 (rw,noexec,nosuid,nodev,relatime,commit=60)
**/dev/sdb1 on /media/backup** type ext3 (rw,noexec,nosuid,nodev,relatime,commit=60)
none on /proc/bus/usb type usbfs (rw,devgid=123,devmode=664)


The partitions in bold are my partitions and where they are mounted. For instance, sda3 in is mounted on /media/av. So if I save something to /media/av, I will be saving it on the sda3 partition. If you look in Nautilus or your file browser, you should be able to find the mount point (example: /media/av in my case) by clicking on File System, then Media, which should display "av" in the right panel.

To see a list of your partitions, run this command:
```

sudo fdisk -l   # Note this is a lowercase L, not a 1.

```

Another way to look at your partition structure is via *gparted*, ubuntu's partition editor. You can open it via System, Administration, Partition Editor; or in terminal with "*gksudo gparted*".

If your partitions are NOT mounted, then we would have to determine why not and how to achieve it.

---

### Post by Dileeshvar on 2009-04-23
> **mystmaiden said:**
> I set up an out dated version of Ubuntu (7.04) on my machine and need to change it but before I do, I want to make sure I have the whole partitioning thing down pat - I want to do it manually this time. I used 'guided' for the outdated one, and it said it would make 5 partitions but when I look in 'My Computer' I just see 'hda1' and 'file system'. Does that mean it simply made 2 partitions or am I just unable to see them all?
 
mystmaiden


Hello,

if your doubt was about manual partitioning then 
these are the things u may need to partition

/
/boot
/etc
swap space
/var
/home 

This is how I manually partitioned my Ubuntu8.04 and regarding your question on seeing the partitons by checking in to /etc/fstab or
df -h will do :)

---

### Post by mystmaiden on 2009-04-23
Thanks all, these are all informative. I also need to ask/explain part of my concern here. One thing I needed with Windows  was a separate partition to store all the extra stuff I use for my art work. I've tried extra folders in My Docs and My Pictures, but in the end - it just gets to crazy and winds up being a real pain. Not sure what file system I'd use for it either. Mostly its things like extra brushes for gimp, pngs, jpgs, pz3's when I need them I just move them over to the main drive and tuck them away again when I'm finished. 
 
hmm.. hoping that's making sense. 
mystmaiden

---

### Post by sgosnell on 2009-04-23
Well, you could use a separate partition, but I don't see the point.  A separate folder in your home would do just as well as a separate partition, wouldn't it?  You can easily create as many subfolders as you like.  I'm afraid I don't understand your concern, perhaps you could explain it better.

---

### Post by mystmaiden on 2009-04-23
One of the reasons I had stuff on a separate drives was for scanning purposes, otherwise there was so much stuff scans took forever. I could scan the whole computer when needed but also do quicker scans as well. Maybe with Ubuntu the constant spyware/virus scanning will not be as much an issue. Otherwise, sub folders will probably work as well.

---

### Post by sgosnell on 2009-04-24
With Linux you can toss the scanner.  It's not at all necessary.  I don't run a firewall, nor any anti-virus, antimalware, or any other such app.  Windows viruses only run under Windows, and the software necessary to protect it slows those computers waaaayyyyy down.  There are no extant Linux viruses.

btw, you do know that you can exclude directories from the scan even on Windows, don't you?

---

### Post by mystmaiden on 2009-04-25
I do tend to download stuff, lots of free artsy stuff to play with out there, so malware and viruses have always been a concern. I try to stick with reliable sites, but you never know. I'm glad to hear the virus problem is a thing of the past.

I don't have windows anymore.

---

### Post by presence1960 on 2009-04-25
> **mystmaiden said:**
> I do tend to download stuff, lots of free artsy stuff to play with out there, so malware and viruses have always been a concern. I try to stick with reliable sites, but you never know. I'm glad to hear the virus problem is a thing of the past.

I don't have windows anymore.

for a great overview of security in Ubuntu read this : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by sgosnell on 2009-04-26
As long as you're careful about not clicking on OK and entering your password just because a popup asks for it, Linux should be relatively secure.  You have to enter your password to allow any changes to any system files, so it's somewhat difficult to write malware that can actually damage a Linux system.  Not impossible, of course, but difficult, as long as the user uses common sense.  It's much easier to exploit user carelessness than to write code that can bypass the system security.

---

### Post by mystmaiden on 2009-04-26
Thanks, that's good to know.

---

### Post by Miljet on 2009-04-26
If you want just to find out how many partitions are currently on your hard drive, open a terminal and type:

```
sudo fdisk -l 
```

That's a small L, not a one.

---

### Post by mystmaiden on 2009-04-26
thanks, Miljet!

---

### Post by PukingPenguin on 2009-04-26
> **Ellen2 said:**
> How about a cross platform virus for linux. A new area of concern identified in 2007 is that of cross platform viruses, driven by the popularity of cross-platform applications. This was brought to the forefront of malware awareness by the distribution of an openoffice virus called *Bad Bunny*.

Did you get infected? 
Do you know anyone who did? 
Does ANYONE know anyone who did?



I didn't think so.

Guarding against every theoretical threat is exhausting.

It's amazing how simple computing becomes without Windows.

---

