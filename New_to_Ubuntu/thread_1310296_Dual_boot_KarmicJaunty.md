---
title: "Dual boot Karmic/Jaunty"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-11-01
I want to dual boot with Karmic and Jaunty...while using the same /home. I want to switch over to Karmic when I am totally happy with it. Then I will replace Jaunty with 10.04 etc etc.

There is a lot of info on dual booting with Windoze etc...but not much on Ubuntu/Ubuntu.

My present set up is as follows.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3b53557

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       30401   234428512+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris
/dev/sda6            1217        3648    19534977   83  Linux
/dev/sda7            3649        6080    19535008+  83  Linux
/dev/sda8            6081        8512    19535008+  83  Linux
/dev/sda9            8513       29164   165887158+  83  Linux


/sda2 is extended
/sda6 is /
/sda7 is /usr
/sda8 is /var
/sda9 is /home

How should I go about it while not erasing my whole disk (I have already done that once and it was not fun!)

---

### Post by ranch hand on 2009-11-01
If you have the free space, 5 to 10Gb, for a root (/) partition you should be fine.  Make sure you use a different user name for the two OS' so that your files do not get co-mingled in the /home partition.

---

### Post by dunbrokin on 2009-11-01
Thanks for that....much appreciated....but I think I need a little bit more hand holding...I thought I had it all together last time, and I managed to blank the whole disk!!

---

### Post by ranch hand on 2009-11-01
How about a screen shot of gparted (full screen) so we can actually see your setup?

---

### Post by timsdeepsky on 2009-11-01
I'm curious....Why use the same /home....

---

### Post by dunbrokin on 2009-11-01
See attached....I want to keep the same home as I want to us the Document folder as all my files are in there.

---

### Post by timsdeepsky on 2009-11-01
Thanks....
I learn something new everyday....I am going to follow this thread because i am curious about this....

---

### Post by jord_101 on 2009-11-01
Sorry this aint gonna be very helpful cause im a newb but ive got a fantastic friend who was able to tell me how to do this, to bad i dont remeber wat he told me to do or what that involved, all i know is i went in to the terminal thing and also used the disk manager to find the name of the partition, copied my files to the home partition at some point. Ill tell my friend bout this see if he will answer if someone else doesn't first. 

Anyway what i know is that ive got 2 hard drives the first has xp the second now has 9.10 and 9.04 My partion on the second hard drive is 300G ntfs storage, 20G 9.10, 2G swap space, 20G 9.04, 50G Home

50G home, is where my home folder is had some unexpected side affects for me probably cause ive got the same username, 

I have the same desktop back ground and themes in both 9.10 and 9.04 automatically. Another thing that happened was i now cant create folders in the system files without putting on my admin hat. 

Which i learnt is: sudo nautilus

**Anyway i am a complete newb... this all prob wasn't helpful but i guess one of the points i make is have 3 partitions. **I think.

---

### Post by MC707 on 2009-11-01
Sorry for pun but... dual boot Ubuntu with Ubuntu? Now I've seen everything. :lol:

---

### Post by timsdeepsky on 2009-11-01
I used to put 2 operating systems on the same hard drive....But i found it easier in the long run to separate on different drives....This worked for me because it seemed easier to maintain....Anyway,,,,good luck to you on this....I do not know much about sharing the /home folder between 2 systems....

---

### Post by ranch hand on 2009-11-01
> **MC707 said:**
> Sorry for pun but... dual boot Ubuntu with Ubuntu? Now I've seen everything. :lol:
I started to multi-boot when I started Linux/Ubuntu.

I dumped Win JerryLewis Pro for Hardy.  Then it was so much FUN that I broke it 5 time in a week.

My wife has this strange idea that the computer should work, she was not amused.

So I dual booted Hardy/Hardy.  One for use, the other for play (I mean learning).  I did nothing to the "main" Hardy without trying it first on the "play" install.

Didn't break the main ever again.

---

### Post by Orographic on 2009-11-01
I'm the same, I have a number of internal drives and just unplug and use a different drive when needed. Its cheap, easy and less given to problems.

You could always have a nice external HD or USB drive for your documents instead?

---

### Post by MC707 on 2009-11-01
> **ranch hand said:**
> 
So I dual booted Hardy/Hardy.  One for use, the other for play (I mean learning).  I did nothing to the "main" Hardy without trying it first on the "play" install.

Didn't break the main ever again.

I guess you have a good point. However, much more simple than that would be to use Virtualbox for that, don't you think? :P I think it is a little less messy than actually having a dual boot. If you want to have fun messing an OS up, just double click VB and way to go ;)

---

### Post by ranch hand on 2009-11-01
> **Orographic said:**
> I'm the same, I have a number of internal drives and just unplug and use a different drive when needed. Its cheap, easy and less given to problems.

You could always have a nice external HD or USB drive for your documents instead?
You guys are no FUN at all.  I have four 320Gb drives and multi boot on all of them.  I am a little short right now but I have 18 OS' on the box right now.  This will go up wnen testing for 10.04 starts here shortly.

---

### Post by MC707 on 2009-11-01
> **ranch hand said:**
> You guys are no FUN at all.  I have four 320Gb drives and multi boot on all of them.  I am a little short right now but I have 18 OS' on the box right now.  This will go up wnen testing for 10.04 starts here shortly.

18 OSs? Holy gawd. At least I'm happy you are one more tester for Ubuntu ^_^

---

### Post by ranch hand on 2009-11-01
> **MC707 said:**
> I guess you have a good point. However, much more simple than that would be to use Virtualbox for that, don't you think? :P I think it is a little less messy than actually having a dual boot. If you want to have fun messing an OS up, just double click VB and way to go ;)
I tried VB, doesn't blow my skirt up.  There is too much buffer between the "test" OS and the real hardware through the host hardware interface.  I also do not like having to mess with setting up file sharing.

VB does seem like a real slick deal, though, and it would be a great way to run Win JerryLewis Pro if you could think of a good reason to do so.

---

### Post by dunbrokin on 2009-11-01
This is a very interesting discussion.....but.....I am still no furher forward in achieving the goal.....anybody got any more suggestions?

---

### Post by ranch hand on 2009-11-01
I would shrink your swap by 5Gb and your sda9 by 5Gb and then put a partition there and install / on that.

---

### Post by dunbrokin on 2009-11-01
Will it then be able to access my /home partition and operate on the files in there?

---

### Post by ranch hand on 2009-11-02
When you install, and select the manual option in the partitioner, on your new sda10 click on "change" and select ext4 journaling, check the format box, and designate / as the mount point.

On your sda9 click on change, select ext4 jsurnaling, DO NOT check the format box, select /home as the mount point.

Make real sure that you use a different user name than you are using in Jaunty.  This should make sure that you have different configuration files in /home for Jaunty and Karmic.

---

### Post by dunbrokin on 2009-11-02
Great...thanks for that....I will give it a whirl...

---

### Post by David Geary on 2009-11-02
I agree with ranch hand.
Having two different user names is brilliant!
That way you have the same permissions on both folders when you log in as either!

jord_101 had already installed the two systems independantly, and so we simply made a new home partition and configured them both to use that home. We didn't use different usernames, so some of the settings conflicted with stuff that existed on one system but not on the other.

The process we used was technically involved but nevertheless simple. We wrote down the UUID of the home partition as found by clicking on the partition in the partition editor 'gparted' and then clicking partition->information and added an entry into /etc/fstab on both systems to mount that UUID on /home. We modelled this entry off the one for /. We migrated the existing home folders to the new home partition due to foreseeable issues arising from mounting a partition on a non-empty folder.

We did the migration and configuration from the Live CD and had to be root to do it.

Pressing 'alt-f2' and then typing 'gksu nautilus' and then clicking 'run' from the Live CD simply runs the file manager (nautilus) as root.

root is the ultimate administrator and exists on the vast majority of Unix and Unix-like systems such as Linux. This is different from the normal administrator account which normally runs just like a regular user account except for system administration tasks when it runs the selected process as root. It is dangerous to run programs that expect to run as normal users as root, but we did this to get the nice file manager and text editor interfaces without having to resort to the terminal.

I, personally, feel more comfortable in the terminal to do such tasks, however I was demonstrating how to do it more simply.

dunbrokin, In your case, you got the installers to do this.
Why do you separate /var and /usr from /? I'm just curious...

---

### Post by dunbrokin on 2009-11-02
I use /var /usr etc...coz I saw it recommended somewhere....no idea why really.

I just downloaded Karmic and ran it first as the live CD. It still has really bad problems linking me up to the internet. I think I will wait a few weeks and try again to see if the problem is fixed....back to Jaunty for now.

---

### Post by timsdeepsky on 2009-11-02
I boot Karmic for my main system,,and xp from another hard drive(only for my network gaming)....After getting around my grub2 issue,,i have to admit,,i have had zero problems....Karmic so far has been sweet for me....If it had big boobs i would marry it....Don't tell my wife or girlfriend....

---

### Post by ranch hand on 2009-11-02
We won't tell.

---

