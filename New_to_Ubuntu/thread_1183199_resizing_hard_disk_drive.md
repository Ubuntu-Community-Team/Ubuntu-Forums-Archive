---
title: "resizing hard disk drive"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by hunvilr on 2009-06-09
Hi,
I am dual booting b/w linux and windows. since new to linux, i was trying to download a large linux video tutorial file and now when i have completed downloading almost 93% it says running out of space. when i access windows i can see there is about 35GB free space . so how do i go about resizing? pls can anyone help me? using windows vista and linux ubuntu 8.10.

---

### Post by bodhi.zazen on 2009-06-09
You could download the file to your windows partition as a temporary fix.

To resize your partitions I suggest gparted, from a live CD :

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by murray92 on 2009-06-09
Hi, out of interest, what is this video and where can i find it? Im also quite new and keen to learn as much as possible. A link would be great, thanks :)

---

### Post by hunvilr on 2009-06-10
[[COLOR=#980101]**thanks bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") for the file. i went thru it . actually i have the gparted package installed already..trying to proceed further from there. I don't want to loose any data..in the gparted window, under partition menu resize option is disabled

---

### Post by hunvilr on 2009-06-10
there are plenty of videos available..u might need to search for torents to download it.. check for (cbt nuggets linux series, , train signal, linux all in one) may be a very old one but for me as a beginner i think its enuf

---

### Post by hunvilr on 2009-06-10
In the gparted window , under the partition option the resize option is disabled. Any idea how to proceed further?

---

### Post by Elfy on 2009-06-10
If you are using the livecd (ubuntu that is) you will have swpa being used - right click the swap partition and swapoff.

If you're trying to do so without being in either the livecd of ubuntu or gparted - you need to be, you can't work on the partitions while they are mounted.

---

### Post by bodhi.zazen on 2009-06-10
> **hunvilr said:**
> [[COLOR=#980101]**thanks bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") for the file. i went thru it . actually i have the gparted package installed already..trying to proceed further from there. I don't want to loose any data..in the gparted window, under partition menu resize option is disabled

You can not resize a partition if it is already mounted, thus the advice to boot a live CD.

Once you boot a live CD the most common problem is that the swap partition is mounted, as suggested by forestpixie.

You can unmount partitions within gparted or from the command line:


```
sudo swapoff -a
```

---

### Post by hunvilr on 2009-06-11
thanks a lot to both of u..i'll try it n let u'll know

---

### Post by hunvilr on 2009-06-13
this may sound silly...actually i did not create any partition in windows before installation of ubuntu. i realised now, thats the reason I see only one drive. probably i may have to create separate drives in windows n then install ubuntu in the separate drive. is that how u r supposed to do?
okk let me put my question this way i have a single drive, my filesystems for both linux n ubuntu are same ntfs. then why should linux say that there is no space. i am not able to get the concept.

---

### Post by Elfy on 2009-06-13
Did you install with wubi?

That is installed inside windows - not as a seperate thing on it's own real partition - it uses a virtual partition.

Edit - if that is the case then your vista partition should be available to you - [https://wiki.ubuntu.com/WubiGuide#How do I access the Windows drives?](https://wiki.ubuntu.com/WubiGuide#How do I access the Windows drives?)

The whole wubi guide is here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by hunvilr on 2009-06-13
yes i installed Wubi. I went thru this
**How can I access the Wubi files from Windows? **

But it speaks for filesystems that can be mounted for ext2. 
When I check the windows partition it says it uses NTFS filesystem. Nowhere I came across the word ext2. But inspite of that I went ahead and installed ext2ifs. I use a Sony VIAO laptop and when I installed ext2ifs program, i could actually see the recovery disk which used to be always hidden.
Apart from that nothing. Moreover in the ubuntu/disks folder the files are in some unreadable format. they are not the files that I actually downloaded

---

### Post by Elfy on 2009-06-13
Look in /host - they should be there.

If that doesn't help then I'm not sure tbh - only ever looked at wubi once.

As far as I know you shouldn't need ext2ifs - that is for reading linux files in windows. Ubuntu should read ntfs out of the box now.

---

### Post by hunvilr on 2009-06-13
yeah i looked thru all the files. yeah i agree with u that ext2ifs is not reqd. 
no idea how to get to the files. thanks for all the support.i'll keep trying. may be one day i'll figure out!!!

---

### Post by Elfy on 2009-06-13
I see now reread the post your trying to do it the other way, read linux video in windows - sorry. I've been going at this the other way. 

I would look into resizing your partition - there is a link on the wubi guide - not as easy as it is with a normal install.

I had mixed responses with extifs when I used windows - not always working for me, certainly I never tried to access wubi from vista. 

Possibly that is the problem. 

When you do trry and access the files from vista what error do you get - it helps us to actually have the errors.

---

### Post by Elfy on 2009-06-13
Thinking about it I would do as bodhi sadi in post #2 and download it to vista - you should be able to access it from ubuntu then.

---

### Post by hunvilr on 2009-06-13
i was downloading the file using linux itself. when i was thru say 93% i got this msg saying that I am running out of space n cannot download further. well i deleted files of about 2GB and allocated space for download. that is secondary. doesn't solve my problem in future.
i have a few questions
1)when u install wubi in vista does vista allocate some fixed amount of disk space to linux?
i) If yes how much? and how do I increase it?
ii)If not y can't I just keep downloading as much hard disk space is available to me.

If I boot through windows n check the disk management it has one drive n has about 35 Gb of free disk space. so me getting the message that i am runnign out of space in linux does not make sense to me. 

have u come across ubuntu providing any detailed documentation? do let me know if u have any idea.

well now temporarily i have connected an external hard disk and using it.

---

### Post by Elfy on 2009-06-13
> 1)when u install wubi in vista does vista allocate some fixed amount of disk space to linux?Yes 
> 
i) If yes how much?However much you told it to.
> 
 and how do I increase it?[https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?](https://wiki.ubuntu.com/WubiGuide#How do I resize the virtual disks?)

> If I boot through windows n check the disk management it has one drive n has about 35 GbPlease run ubuntu, open a terminal, paste this command in and give us the output.

```
df -h
```

---

### Post by hunvilr on 2009-06-14
lcsonyuser@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G   11G  1.4G  90% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  120K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1005M   1% /dev
tmpfs                1008M  468K 1008M   1% /dev/shm
/dev/sda2             143G  100G   43G  70% /host
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             112G   63G   50G  56% /media/NET_STORAGE

---

### Post by Elfy on 2009-06-14
> **hunvilr said:**
> lcsonyuser@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                      13G   11G  1.4G  90% /
/dev/sda2             143G  100G   43G  70% /host
/dev/sdb1             112G   63G   50G  56% /media/NET_STORAGE

These 3 pertain to the room you have available as storage space - the last is an external.

The first line , / , is the linux install - you can see you have used 90% of the available space there. The second, /host , is the windows drive - you have 43Gb available there - you can access this from within your linux install.

To get there without having to find it run nautilus like this

```
nautilus /host
```

If you want more room for your linux then you have to either remove existing files or resize the drive.

---

### Post by hunvilr on 2009-06-14
This is just awesome!! I can access my windows files so easily!!! unbelievable!!!

Couple of questions more. Just to confirm

a) /host/ubuntu/disks/root.disk
                      13G   11G  1.4G  90% /

I presume the 13GB allocated here is space from hard disk drive and not a virtual disk or anything.

b) In case I want to increase the 13GB I have two options , either resize it or create a virtual disk.

i) I understood how to create virtual disk. say I want to create 10GB i can add these commands.

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F extra.disk

ii) But in case I have to resize it I have to use gparted and do it. Is that correct?

Y is that any of the options aren't highlighted for me. I cannot see any option enabled under gparted.

Is there any limitation?

---

### Post by Elfy on 2009-06-14
To be honest I'm not sure - I never used wubi so never had a need to muck about with it's virtual disk, sorry.

---

### Post by bodhi.zazen on 2009-06-14
I do not have an answer either, but to be honest, if you have decided to keep Ubuntu it would make your life easier if you were to uninstall wubi and perform a standard installation.

You can not resize your partitions while the partition is mounted , thus a live CD is advised for the Ubuntu root partition and since ubuntu is running in a virtual drive within windows (wubi) I doubt gparted will manage the loop mount required for wubi.

---

