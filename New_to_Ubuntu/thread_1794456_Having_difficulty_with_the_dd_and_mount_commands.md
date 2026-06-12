---
title: "Having difficulty with the dd and mount commands"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-07-01
Hi,

My situation is I'm trying to use a desktop computer with no o/s installed to plug in these ide hard drives and image the drive to get the data off of them. I thought I could run Ubuntu 10.04 LTS live and use the command line to execute the dd command; and store the image on my external usb drive. The usb drive is not automounted like usually and when I look in "/media" it is empty. I'm not for sure but I think in order to do this I need to mount the drive.

I've looked at the man page several times and an online article that gives examples of the command. And I've tried several things. When I use the -t option I'm not sure what I'm supposed to put in there. I've tried "fat" "fat16" "usb" and "Lacie" (Lacie is the name of the usb drive. I've also tried without the -t option like so:

```

mount /dev/sdb1 /media

```

And like so:

```

mount /dev/sdb /media

```

And like so:

```

mount /dev/hdb /media

```

And for all those three I'm told:

```

mount: special device /dev/<whatever I had put here> does not exist

```

I also wonder if the hard drive I'm trying to image is mounted and if I will need to umount it before I'll be able to use dd.

Can anyone help?
---------------------

Edit:

I did do all these things while logged in as the (superuser?)(root?)

```

sudo -s

```

---

### Post by sam_delta on 2011-07-01
whats the output of ```
sudo fdisk -l
```
(note its the leter 'L' not a number 1)
sam

---

### Post by ClientAlive on 2011-07-01
> **sam_delta said:**
> whats the output of ```
sudo fdisk -l
```
(note its the leter 'L' not a number 1)
sam


Requested info in attachment.

Seems like I see both drives being mounted. The one that says it's hpfs/ntfs is the local disk and the one that says it's 250.1 GB is the usb.

Is that right?

---

### Post by ClientAlive on 2011-07-01
But I'm running that same, Ubuntu 10.04 LTS on my laptop here and that usb never mounts to /dev/sdb1. It mounts to /media. I use the command line with it on this machine all the time. This doesn't make sense now

---

### Post by sam_delta on 2011-07-01
the drives listed by "sudo fdisk -l" are the drives being detected by your computer and NOT necessarily mounted.

It looks like the 80 gig ntfs drive is being listed as /dev/sda, so to mount it, try this:
```
sudo mount /dev/sda1 /media
```
then if the mount was succesfull, to see the files inside the drive type
```
ls /media
```
or to open a file manager type
```
nautilus /media
```

let me know how it goes!!
sam


EDIT 
just for more info
/dev/sda defines the whole drive.
/dev/sda1 defines the first partition of the drive /dev/sda
/dev/sda2 defines the second partition of the drive /dev/sda and so on
with mount, you have to give the partition you want to mount, not the drive, so you would use '/dev/sda1'


sam

---

### Post by ClientAlive on 2011-07-01
> **sam_delta said:**
> the drives listed by "sudo fdisk -l" are the drives being detected by your computer and NOT necessarily mounted.

It looks like the 80 gig ntfs drive is being listed as /dev/sda, so to mount it, try this:
```
sudo mount /dev/sda1 /media
```
then if the mount was succesfull, to see the files inside the drive type
```
ls /media
```
or to open a file manager type
```
nautilus /media
```

let me know how it goes!!
sam


EDIT 
just for more info
/dev/sda defines the whole drive.
/dev/sda1 defines the first partition of the drive /dev/sda
/dev/sda2 defines the second partition of the drive /dev/sda and so on
with mount, you have to give the partition you want to mount, not the drive, so you would use '/dev/sda1'


sam


I hafta get to bed for tonight (it's past 3am here). Will do in the morn though. I think the result I need in the end is to have the 80 gig drive (this is the one I need to copy from) be umounted (not mounted) and the 250 gig drive (the usb I need to copy to) be mounted. Will look at it again tomorrow though.

Isn't it that the drive you're trying to image with dd can not be mounted for it to work?

Thanks for your help.

---

### Post by sam_delta on 2011-07-01
ahh i see, i think i misunderstood what you wanted to do.

to use dd you don't have to have the input drive mounted but only the output.
your dd comand would be something like the this:

mount the destination hard drive (i understand that this one would be the 250 gig hdd (sdb1)
```
sudo mount /dev/sdb1 /media
```
once mounted the destination hdd, make the image of the source drive into the mounted destination drive.
```
sudo dd if=/dev/sda1 of=/media/file.img
```
unmount the destination hard drive with
```
sudo umount /media
```

note that dd will make a exact copy bit by bit of the partition sda1 into the file file.img (it will take a considerable amount of time to finish).

if what you want to do is just retrieve some files from the partitions, you might consider just mounting both partitions and copy the files you need into the other partition.

let me know how it goes!! gnite!
sam

---

### Post by ClientAlive on 2011-07-01
> **sam_delta said:**
> ahh i see, i think i misunderstood what you wanted to do.

to use dd you don't have to have the input drive mounted but only the output.
your dd comand would be something like the this:

mount the destination hard drive (i understand that this one would be the 250 gig hdd (sdb1)
```
sudo mount /dev/sdb1 /media
```
once mounted the destination hdd, make the image of the source drive into the mounted destination drive.
```
sudo dd if=/dev/sda1 of=/media/file.img
```
unmount the destination hard drive with
```
sudo umount /media
```

note that dd will make a exact copy bit by bit of the partition sda1 into the file file.img (it will take a considerable amount of time to finish).

if what you want to do is just retrieve some files from the partitions, you might consider just mounting both partitions and copy the files you need into the other partition.

let me know how it goes!! gnite!
sam


Yes, time is, of course, a consideration. The sitch is it's a data recovery project. In exchange for a few old computers I'm to recover this guys data from all the drives in them. There are like 3 drives and the largest is that 80 GB one. The others are 20 GB; and, the third, has no size recorded on the label. It's prob relatively small though since it's old enough to not put that info on the label.

In consideration, not just of my time to do it but also his convenience to access the data later, I didn't want to just hand him a raw image with a ton of free space in it. The best way I know of (thanks to another member of this forum) was to image the drive and then use file-roller to rip the data out. I can see that this 2 process method would take considerably longer than if I had a way to just rip the data to begin with and do it in one pass. There are constrains on the tools I can or am willing to use though (see third item in list at the bottom).

My other concern, and a big one, is not to do anything invasive on those drives as part of the recovery process. The thought crossed my mind to use Parted Magic to create a partition in the unused space that is just slightly over the size of the data, move the data to it, then image that partition. Again though - invasiveness and the possibility of changes to the drive causing data loss.

To summarize some of the key factors:

~ The source drives are all ide so they can all easily be plugged into the mobo of that desktop
~ The 80 GB source drive is NTFS file system (and I anticipate the others will be too)
~ Because this desktop's real purpose in life is not for this, one data recovery job, but is to become a cloud server - because of that I am pretty unwilling to install Windows on it. Only if I absolutely had to and there were no-other-way. I don't really want to install anything on it that is not related to what I want to do with it later. It would just be a huge time/ effort pit for me to do that. Therefore, I'm trying to use only tools that can be run live and thus be able to do this data recovery w/o anything installed.

For now, I think I'll take a shot at the: image the drive (utilizing the info you gave me above) then use file roller on the image. If I find a better, less time consuming way I'll switch to it then (even if 'then' means the next time I do a project like this). Since I have this laptop here at least I can do other stuff while I wait for the dtop to process the job.

---

### Post by nothingspecial on 2011-07-01
Whatever you do, look at the dd command before you execute it, then look at it again, and one one final time. And make sure you know exactly what it is going to do to what.

Once you press 'enter' it will do it, no questions.

It's not nicknamed disk/data destroyer for nothing.

---

### Post by ClientAlive on 2011-07-01
Oddly enough, when I booted up and plugged in that external it did auto mount this time. Don't know what the difference is but whatever - it was mounted. So then . . .

What I ran was:

Fist -

```

umount /dev/sda

```

No gripes from the terminal so I figured it was all good

Then -

```

dd if=/dev/sda of=/media/Lacie/<NameOfFolder>/<NameOfFile.img> conv=notrunc,noerror bs=512

```


* But here's the thing. There's one thing I don't like about that dd script I ran. It doesn't give you any output on what's going on. The man page doesn't show a " -v" option for verbose and I didn't see anything equivalent for dd in there. Maybe I just missed it. While I would like to add something to that script that gives me some output, I don't want to have any user interaction required. I don't need to be sitting there pressing Y and then enter a million times. Lol.

Any thoughts on what I can add to get some std output?

Thanks

---

### Post by ClientAlive on 2011-07-01
> **nothingspecial said:**
> Whatever you do, look at the dd command before you execute it, then look at it again, and one one final time. And make sure you know exactly what it is going to do to what.

Once you press 'enter' it will do it, no questions.

It's not nicknamed disk/data destroyer for nothing.


I hear ya' Solid advice there. Thanks.

---

### Post by sam_delta on 2011-07-01
check out posts 7 and 8 from this thread: [http://ubuntuforums.org/showthread.php?t=884093](http://ubuntuforums.org/showthread.php?t=884093)

sam

---

### Post by ClientAlive on 2011-07-01
> **sam_delta said:**
> check out posts 7 and 8 from this thread: [http://ubuntuforums.org/showthread.php?t=884093](http://ubuntuforums.org/showthread.php?t=884093)

sam


I thought the kill command stopped processes indefinitely though (until you start it again manually anyhow). dd must be different so that it restarts itself then?

---

### Post by sam_delta on 2011-07-01
the program kill just sends diferent signals to a process, it is mostly used to send the default signal "-2" (SIG INT) or "-9" (SIG KILL) to end processes but it can be used to send other signals as well.

check out "man kill" for more info.

sam

---

### Post by ClientAlive on 2011-07-01
> **sam_delta said:**
> the program kill just sends diferent signals to a process, it is mostly used to send the default signal "-2" (SIG INT) or "-9" (SIG KILL) to end processes but it can be used to send other signals as well.

check out "man kill" for more info.

sam

Oh, I see what he's doing I think. It looks like he's interposing, something that makes give standard output, by putting it in the middle of the command and piping. Interesting. I don't know what pv is and I tried "man pv" but there's no entry for it. I'm assuming it's related to kill. Lemme try "man kill" and see what I get.
----------------------

Edit:

I'm reading the man page for kill. It says the INT option (or -2) action is "exit". So then exit must not mean the same thing as stopping the program or closing it entirely. Sorry I'm seeing gui images flash through my mind when I try to write this. I'm a bit of a newb to the cli still.

Thanks

---

### Post by sam_delta on 2011-07-01
with kill, you can send numerous types of signals, (kill is most used (and defaults) to send signal 2 SIGINT) which is used to close a program. You can see the full list of signals you can send in the manual page.

Each program will react differently to each of the signals it receives depending on how the program was written. (there are default reactions for each signal tho).

dd is coded in a way that if it receives signal USR1 it will print its current progress into stdout. 

Now, you can send USR1 signal to dd using kill. Kill's syntax is as follows
```
sudo kill -SIGNAL PID
``` just replace SIGNAL with the signal you want to send, and PID with the pid you want to send the signal to. If no signal is specified, it defaults to send signal 2 (SIG INT) which terminates the program.

For example if you want to send USR1 signal to dd, you will type the following command (supposing that dd PID is 1234)
```
sudo kill -USR1 1234
```
dd would react to that signal by returning its curring progress.

EDIT,
if you have dd running in a terminal, you can send the signal from another terminal, so DD doesnt stop its execution.

let me know if you still have questions.

sam

---

### Post by ClientAlive on 2011-07-01
> **sam_delta said:**
> with kill, you can send numerous types of signals, (kill is most used (and defaults) to send signal 2 SIGINT) which is used to close a program. You can see the full list of signals you can send in the manual page.

Each program will react differently to each of the signals it receives depending on how the program was written. (there are default reactions for each signal tho).

dd is coded in a way that if it receives signal USR1 it will print its current progress into stdout. 

Now, you can send USR1 signal to dd using kill. Kill's syntax is as follows
```
sudo kill -SIGNAL PID
``` just replace SIGNAL with the signal you want to send, and PID with the pid you want to send the signal to. If no signal is specified, it defaults to send signal 2 (SIG INT) which terminates the program.

For example if you want to send USR1 signal to dd, you will type the following command (supposing that dd PID is 1234)
```
sudo kill -USR1 1234
```
dd would react to that signal by returning its curring progress.

EDIT,
if you have dd running in a terminal, you can send the signal from another terminal, so DD doesnt stop its execution.

let me know if you still have questions.

sam


Wow Sam! Talk about a golden nugget of information there! Thank you. That's the kind of thing a guy can do a hell of a lot with. Not just this one, specific thing.

Way cool!

---

### Post by sam_delta on 2011-07-01
:) no problem. Im glad its being useful. Have fun and feel free to ask if you have more questions! 

sam

---

