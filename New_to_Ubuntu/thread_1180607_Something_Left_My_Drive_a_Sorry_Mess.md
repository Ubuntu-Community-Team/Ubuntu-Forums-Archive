---
title: "Something Left My Drive a Sorry Mess"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Sarrel on 2009-06-07
I suspect it may have disasterously overheated, mostly due to the fact that right before this happened I ceased to have fingerprints anymore, and it's not incredibly surprising, seeing as it is an old computer. It's an IBM A31p and I don't even remember how old it actually is, though I'd have to guess around 3-4 years.

I figured that since I already had all of the important info stored elsewhere, I might as well just reinstall xubuntu, and get on with things, but for some reason, there are no partitions to install it on, and it won't give me the option to just use the entire disk. It will let boot from the disk, which is how I'm typing this, but I'd actually like to save things, so it presents a problem. (I haven't a big enough flash drive apparently)

It also starts the startup procedures, but never manages to finish them, something about not having a startup prcedure in the first place. and as I have very limited knowledge of these processes in general, I figured it wasn't worth a few months tryng to salvage, even with all of the help from Ubuntu's wonderfully supportive community.

So I'm mostly wondering if I can't just wipe the entire drive and completely reinstall my operating system, or if that would do me no good whatsoever. I'd also like to be informed of my other options, so please inform me if there's something that's a better idea, or if there's nothing I can do and this computer has finally met it's end. Thank You.

---

### Post by Sef on 2009-06-07
Depends.  If it is just your hard drive that is bad, then maybe the machine is usuable.  However, it seems to have another problem since you said it overheated.  (Bad Fan or Bad power supply most likely.)   I would figure out why it overheated before putting any money into it.

---

### Post by Lampi on 2009-06-07
you should examine the health of your system and your hard disk with some helper tools. Try booting from a different media (good choice is ubuntu live cd)

I assume your disk is unmounted and has been given the name "/dev/sda" - now:

*) have a look at your disks filesystem integrity - run a dry-run filecheck  (sudo fsck -VMN /dev/sda), this will only check for errors, not repairing any.
*) Since you are mentioning heat problems have a look at sensor values (type "sudo sensors" in terminal and check for ALARMS plus unusually high values.)
*) You might want to check disk temperatures (type sudo hddtemp /dev/sda in terminal)
*) you might want to check your disks health data aka S.M.A.R.T. data (type "smartctl -H /dev/sda" for basic SMART pass test. If it passes with okay type "smartctl -a /dev/sda | more" for extended smart logs and have a look at the prefail attributes)

I hope some of these tests will show you possible reasons for what is wrong with your system.

---

### Post by wpshooter on 2009-06-07
Tell us how much memory your computer has and we can give you better advice as how to proceed.

---

### Post by Sarrel on 2009-06-07
It doesn't use a battery anymore due to the fact that when it had the battery, things were worse. Now it doesn't use either battery, and I'm left to using it like a somewhat more portable desktop, if that gives any clue as to what's wrong with it. And the fan can get pretty noisy, I've gotten used to falling asleep to it... -.-

And I'm also under the suspicion that it ended up using ubuntu in the first place due to a similar incident, which is what gives me hope that it can be repaired. I'm alot less skillful than the one who first repaired it though.

For those system checks, you'll have to translate for me, as again, I really am a beginner here.

For the first one, sudo fsck -VMN /dev/sda, I got this:
fsck 1.41.4 (27-Jan-2009)
[/sbin/fsck.vfat (1) -- /dev/sda] fsck.vfat /dev/sda

For the second and third, I got command not found messages.(I understand that one at least.)

and for the last one, I had to install smartctl, it gave me an OK, and then I got this message from the second command:
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sda failed: No such file or directory

I'm not entirely sure what some of those mean, though I have a general idea of what they were checking for. I'm not very fluent in computer-speak yet.

I'm not entirely sure how to check how much memory I have... sorry if this is a really stupid question, but how do I check again?

---

### Post by Lampi on 2009-06-07
as you've already figured out on your own ubuntu always tells you what application to install if it is missing on your system - so just type what it tells you to do (sudo apt-get install <name of the missing program>)

- make sure these applications are installed
- make sure to use sudo
- and make sure your hard disk is /dev/sda - might be /dev/hda, it depends on the type of drive you are using, and how this drive is connected on your mainboard. if you don't know how to figure this out "cat /proc/partitions" might tell you so.

---

### Post by Sarrel on 2009-06-07
I installed the ones it told me to, and also, I'm booting from my live cd, so after a while It just goes ahead and tells me there's not enough room.

---

