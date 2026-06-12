---
title: "Unable to mount Internal Hard Drive."
date: 2009-07-11
forum: New to Ubuntu
---

### Post by jdegan on 2009-07-11
I am new to Ubuntu, a month ago my Windows updated and when I turned my laptop back on, it was no longer able to access my Hard Drive. Operating system not found.
I have a 16GB SSD SATA.
The BIOS sees it, but it now has 0MB??
I'm not great at computers, but am willing to learn.
I have installed Ubuntu onto an external hard drive, in the hope I can access the other hard drive and retrieve my photos before I send it back to be repaired. I have a Dell mini.

Ubuntu is unable to mount the hard drive. It sees it in the 'Computer' window.

I have been searching the threads and there are a lot of similar problems, but they mainly seem to deal with secondary hard drives with a running Windows on it or multiple partitions. I tried running a program to locate the partitions, but it said there wasn't any!

I'm slowly learning the commands and terminals, but I would appreciate if you assume I know nothing.

After reading some threads I know how to access the root user and I also tried to use fdisk and I tried mounting it, but it didn't work:

jdegan@jdegan-laptop:~$ mkdir -p /mount/sda
mkdir: cannot create directory `/mount': Permission denied
jdegan@jdegan-laptop:~$ su - root
Password: 
root@jdegan-laptop:~# mkdir -p /mount/sda
root@jdegan-laptop:~# fdisk sda

Unable to open sda
root@jdegan-laptop:~# fdisk /dev/sda

Unable to read /dev/sda

I'd be grateful for any help,
my main objective is to recover my photos, I'm not worried about getting Windows working again, I'm liking Ubuntu so far.
Jdegan.

---

### Post by jerome1232 on 2009-07-11
If the bios sees it as 0 MB I fear you have one damaged hard drive. Probably one Physically damaged hard drive. 

I've had a hard drive do the same thing after my power supply blew sparks and started smoking. If the bios doesn't see the drive right the OS won't either, so I don't have much to suggest other than double checking cables/power connections in the laptop to that drive.

---

### Post by cjv8888 on 2009-07-11
> **jdegan said:**
> I am new to Ubuntu, a month ago my Windows updated and when I turned my laptop back on, it was no longer able to access my Hard Drive. Operating system not found.
I have a 16GB SSD SATA.
The BIOS sees it, but it now has 0MB??
I'm not great at computers, but am willing to learn.
I have installed Ubuntu onto an external hard drive, in the hope I can access the other hard drive and retrieve my photos before I send it back to be repaired. I have a Dell mini.

Ubuntu is unable to mount the hard drive. It sees it in the 'Computer' window.

I have been searching the threads and there are a lot of similar problems, but they mainly seem to deal with secondary hard drives with a running Windows on it or multiple partitions. I tried running a program to locate the partitions, but it said there wasn't any!

I'm slowly learning the commands and terminals, but I would appreciate if you assume I know nothing.

After reading some threads I know how to access the root user and I also tried to use fdisk and I tried mounting it, but it didn't work:

jdegan@jdegan-laptop:~$ mkdir -p /mount/sda
mkdir: cannot create directory `/mount': Permission denied
jdegan@jdegan-laptop:~$ su - root
Password: 
root@jdegan-laptop:~# mkdir -p /mount/sda
root@jdegan-laptop:~# fdisk sda

Unable to open sda
root@jdegan-laptop:~# fdisk /dev/sda

Unable to read /dev/sda

I'd be grateful for any help,
my main objective is to recover my photos, I'm not worried about getting Windows working again, I'm liking Ubuntu so far.
Jdegan.
If this is the case, you can boot with the Ubuntu live CD, mount the Windows partition, then just copy the photos across to your external harddrive.

---

### Post by theozzlives on 2009-07-11
Check to see if the drive spins-up when you turn the power on. You can hear it if you listen, if you hear clicking or grinding it's probably a lost cause. BACK UP your data! I learned the hard way after Michaelangelo virus got me in 1992.

---

### Post by whole.grains on 2009-07-11
> **theozzlives said:**
> Check to see if the drive spins-up when you turn the power on. You can hear it if you listen, if you hear clicking or grinding it's probably a lost cause. BACK UP your data! I learned the hard way after Michaelangelo virus got me in 1992.


OP said it's a solid-state drive.

---

### Post by jdegan on 2009-07-12
Thanks for the response guys,

@jerome1232-When you had your problem, was there any marks on the hard drive. I don't know much about Solid State Drives, will there be any visible damage? Or visible damage on the cables?

It looks like I'll have to forget about my photos and just start from scratch. I usually back up everything every month, but it had been an important week before the crash and I would have preferred to hang on to them.

Thanks for the help.

---

### Post by LewRockwell on 2009-07-12
> **whole.grains said:**
> OP said it's a solid-state drive.

lol

.

---

### Post by LewRockwell on 2009-07-12
> **jdegan said:**
> Thanks for the response guys,

@jerome1232-When you had your problem, was there any marks on the hard drive. I don't know much about Solid State Drives, will there be any visible damage? Or visible damage on the cables?

It looks like I'll have to forget about my photos and just start from scratch. I usually back up everything every month, but it had been an important week before the crash and I would have preferred to hang on to them.

Thanks for the help.

don't give up so easily

get a copy of the latest Puppy Linux and try to mount your SSD drive with it

just because ubuntu doesn't do something...doesn't mean it can't be done!

never give up, never surrender!

there are other things you can try but give puppy a try and report back to us please!

.

---

### Post by whole.grains on 2009-07-12
You could open the case and make sure the power and sata connectors are completely connected and not damaged, if you don't mind getting your hands dirty. Also, is it still under warranty? You might be able to send it back.

---

### Post by zerhacke on 2009-07-12
Yeah, your SSD is fried.  Hope you're under warranty still...

I hear it so often about the SSD drives these days that I sure wouldn't use one if I could get away with it.

---

### Post by jerome1232 on 2009-07-12
> **jdegan said:**
> Thanks for the response guys,

@jerome1232-When you had your problem, was there any marks on the hard drive. I don't know much about Solid State Drives, will there be any visible damage? Or visible damage on the cables?


No there won't be physical marks (unless it's like dripping melted transitors or something lol) and mine were mechanical so I knew one was dead for sure because it would repeatedly click and nothing else.

My guess is something fried in the ssd or (hopefully) a cable is partially lose, I'm going to repeat that if the bios see's the drive as 0 mb no amount of OS switching will help you since they go off what the bios says. 

Contacting the manufacturer of your ssd sounds like a good route to go to get it replaced to me.

---

