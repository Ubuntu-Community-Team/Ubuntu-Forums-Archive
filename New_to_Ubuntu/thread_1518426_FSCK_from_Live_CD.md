---
title: "FSCK from Live CD"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by jfbooth on 2010-06-26
Xubuntu 10.04 Lucid Lynx installed on hard drive.  Only OS on the entire drive (no dual boot).

Objective:  Run FSCK on hard drive.

Booted Live CD and selected Run without installing.  Am presently at desktop.

Problems:  Cannot understand instructions for fsck.  Need to know clear instructions.  I am confused about device names etc:

hda0, ext*, partitions, swap partitions etc etc.  Not sure how to run FSCK to check the HD.  Don't know how to tell if HD is presently mounted or not.

Please, if possible, command for command instructions.

Thank you in advance.

---

### Post by WinterRain on 2010-06-26
From terminal on live cd, do:
```
sudo su
```
then
```
fdisk -l
```
to find out the path to the drive you want to check. It should be something like /dev/sda1 or something. Then from the terminal on the live cd, do 

```
fsck /dev/sda1
```

---

### Post by da burger on 2010-06-26
I believe the preferred way to get interactive root is ```
sudo -i
``` Also why are you recommending a root shell for two commands. If the OP forgets they have root privileges after the command they could do enormous damage. Just preface the command to run as root with sudo.

---

### Post by WinterRain on 2010-06-26
> **da burger said:**
> I believe the preferred way to get interactive root is ```
sudo -i
``` Also why are you recommending a root shell for two commands. If the OP forgets they have root privileges after the command they could do enormous damage. Just preface the command to run as root with sudo.

I keep forgetting that the ubuntu way of doing things frowns upon old school ways of doing things. But anyway, after the fsck is done, I'm sure the user would reboot and be done with it. No big deal.

If he doesn't know how to do an fsck, how would he know enough to do any damage? If it was gui, I could understand your concern, but for a noob to know enough to start deleting files randomly via terminal, doesn't make sense.

---

### Post by da burger on 2010-06-26
Just good habits. If your getting it right from the start your less likely to mess it up later on. Also the OP might not know much about the terminal but they may know enough to do some damage. rm is not that advanced.

---

### Post by anewguy on 2010-06-26
Glad to see you're getting somewhere with this.  You picked a great title for the thread!

If you need help understanding any of what they want you to do, just let us know and we can try to come up with some very simple instructions.

Dave ;)

---

### Post by jfbooth on 2010-06-26
First, thank EVERYONE for helping.  I want to thank winterain for being willing to help at all.  I want to thank da burger for thinking in MY best interest.
Ubuntu's attitude toward root privilage security is a great idea.  I am sure it has saved many people from disaster.  I do believe it is PRIMARILY an UBUNTU "thing", and easily overlooked by other distro gurus, such as winterain.
I am a noob, and I really appreciate all the help .. and I respect Ubuntu's policy .. but appreciate ANY and all help.

anewguy:  I want ahead and burnt a live CD in order to get the fsck thing done (thanks to winterain and da burger).  Still curious about a bootable 'rescue floppy' though .. so will watch 'our' other threads for the conclusion to that.  I opened this thread 'on my own' to get fsck done.

thank you .. all three of you.

---

### Post by jfbooth on 2010-06-26
I am ASSUMING mounting/unmounting that HD is NOT AN ISSUE .. just 'do it' .. right, Winterain??  Otherwise, you would have mentioned it. That's what I'm goin on .. so here goes.  thanks again.

---

### Post by jfbooth on 2010-06-26
I knew something would go wrong.  Here is fdisk -l:

root@ubuntu:/home/ubuntu/Desktop# fdisk -l

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00044265

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1209     9706083+  83  Linux
/dev/sda2            1209        1216       61405    5  Extended
/dev/sda5            1209        1216       61373+  82  Linux swap / Solaris

and I read it as .. HD is /dev/hda   and that is what I should check.  Here is what I got:

root@ubuntu:/home/ubuntu/Desktop# fsck /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
root@ubuntu:/home/ubuntu/Desktop#

I don't think /dev/sda is right .. must be something else .. like:

/dev/sda1     so:

root@ubuntu:/home/ubuntu/Desktop# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: clean, 147384/614400 files, 901017/2426520 blocks
root@ubuntu:/home/ubuntu/Desktop#

WOW, that was FAST!!  1/3 second!!  Did I do it?  Am I good?  Am I done?

thanks, all.

---

### Post by anewguy on 2010-06-26
I'm glad you went this route.  I think I mentioned it in my post in the other thread, but we never pursued it, so I'm really glad you're getting the help you need!

Best of luck and welcome to Ubuntu!

Dave ;)

---

### Post by jfbooth on 2010-06-26
> **anewguy said:**
> I'm glad you went this route.  I think I mentioned it in my post in the other thread, but we never pursued it, so I'm really glad you're getting the help you need!

You certainly did mention it but as you might recall, I could not find my Live CD and thought it would be a simple thing to do it from a bootable floppy .. never realizing it is impossible (evidently).  So, I 'bit the bullet' and burned a new Live CD.

I still have a question .. what started this whole thing is I have had at least one illegal shutdown (electricians hit my main breaker on the back of the house).  Being noob, it seemed urgent to me to run fsck  which started this whole 'thing'.

So, .. I think I have run it ... good and proper, .. except .. all I checked was sda1.  Aren't there other parts of the HD that might be 'in trouble'?  Like:

/dev/sda2 1209 1216 61405 5 Extended
/dev/sda5 1209 1216 61373+ 82 Linux swap / Solaris

Should I go back and fsck sda2 and sda5 ????

I can 'guess' what sda5 is .. like Windows Swap File except on its own partition .. but I have no idea what sda2 is.  Wait a minute, they both occupy the same .. uh .. cylinders(?) 1209 - 1216.  Should I run fsck on sda2 and sda5 or one/not the other (which one?), or not at all?

I promise, .. this will be the last question.

---

### Post by k3lt01 on 2010-06-26
sda is your hdd. sda1 is the first partition on the hdd, sda2 and sda5 are the second and third partition on the hdd. To fsck the entire hdd just run fsck /dev/sda

---

### Post by jfbooth on 2010-06-26
> **k3lt01 said:**
> sda is your hdd. sda1 is the first partition on the hdd, sda2 and sda5 are the second and third partition on the hdd. To fsck the entire hdd just run fsck /dev/sda

It so happened, fsck /dev/sda is the first thing I tried with the following response:

root@ubuntu:/home/ubuntu/Desktop# fsck /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
root@ubuntu:/home/ubuntu/Desktop#

which I interpret to mean an error.  Did I misinterpret?

---

### Post by k3lt01 on 2010-06-26
That just means you will have to unmount it before you fsck it. In your live cd environment go into Places and it will show your disk, in the left hand panel it will have an eject icon next to it, click on that icon and it should unmount. Once you have done that you should be able to fsck /dev/sda

Also don't go into /home to do this because that is why it is mounting. You are actually locating it with your command and then telling it to do something it cannot do because you have mounted it.

Just have root@ubuntu fsck /dev/sda

---

### Post by libssd on 2010-06-26
The drive is mounted; you need to unmount it before running fsck: *umount /dev/sd*

To get information about how commands work, at the command line type man "command" ; e.g. *man fsck*. Documentation for every Linux command is accessible this way.

---

### Post by Miljet on 2010-06-26
> sda1 is the first partition on the hdd, sda2 and sda5 are the second and third partition on the hdd

Actually sda2 is an extended partition which acts as a container for one or more logical partitions. Sda5 is a logical partition that is located inside sda2. That is why they show to occupy the same sectors.

Your swap partition (sda5) is probably what is mounting at bootup of the live CD. Typing "swapoff" in the terminal should unmount the swap partition.

---

### Post by k3lt01 on 2010-06-26
> **libssd said:**
> To get information about how commands work, at the command line type man "command" ; e.g. *man fsck*. Documentation for every Linux command is accessible this way.Check out the [official page]("http://manpages.ubuntu.com/") and you install it as part of your search function in FireFox as well

---

### Post by jfbooth on 2010-06-26
>  go into Places and it will show your disk, in the left hand panel it will have an eject icon next to it, click on that icon and it should unmount. Once you have done that you should be able to fsck /dev/sda 

No .. it doesn't.  Places in XUBUNTU does not show any devices except Floppy Drive and CD ROM Drive.

So, I went to terminal.  **Holy Mother**, .. looks like things are good and screwed now:

ubuntu@ubuntu:/$ sudo su
root@ubuntu:/# umount /dev/sda
umount: /dev/sda: not mounted
root@ubuntu:/# fsck /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/# 

What now??

---

### Post by k3lt01 on 2010-06-26
That is probably because sda contains your SWAP partition so it has baulked on that as it isn't a ext type file system. Soooo, you will have to fsck /dev/sda1 on its own. After you have done that try doing fsck /dev/sda2 and then fsck /dev/sda5. One of them will baulk because of the SWAP.

---

### Post by jfbooth on 2010-06-26
> **k3lt01 said:**
> That is probably because sda contains your SWAP partition so it has baulked on that as it isn't a ext type file system. Soooo, you will have to fsck /dev/sda1 on its own. After you have done that try doing fsck /dev/sda2 and then fsck /dev/sda5. One of them will baulk because of the SWAP.

Thank you for you input.  No arguement here .. but I would like some clarification if I could ... I ran fsck /dev/sda with sda unmounted (the last time) and got the superblock errors.  Is that logical?

From what you are saying, I will get an error on one of the partitions no matter what?  Seems to defeat the purpose of fsck, doesn't it?  How do I know the one that errors is not corrupted?

I am going to do what you said and post the results .. hang on:


root@ubuntu:/# umount /dev/sda
umount: /dev/sda: not mounted
root@ubuntu:/# fsck /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
root@ubuntu:/# fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: clean, 147383/614400 files, 900715/2426520 blocks (check in 5 mounts)
root@ubuntu:/# fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
root@ubuntu:/# fsck /dev/sda5
fsck from util-linux-ng 2.17.2
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5

There you go .. unmounted sda and ran fsck on every "device' with errors.  Am I to CONCLUDE my filesystem on my hard drive is OK????????  I find that hard to believe .. but I am no 'Nix head .. am right at idiot level.  I need (at this point) to KNOW this fs is OK or not.

thank you again, .. and I look forward to your answer.

---

### Post by anewguy on 2010-06-26
I *think* you have to add -t ext4 in the fsck line.  I say this since you booted from CD there is no fstab entry for your hard disk, so it defaults to ext2.  By default I think 10.04 installs as ext4.  This may be why you are getting the errors and they refer to ext2.

I believe if you are still having problems with the device busy that it's probably the swap.  It is my understanding that the LiveCD will use a swap partition if it sees one.

So, I think I would try this:

sudo swapoff

sudo fsck -t ext4 /dev/sda


Dave ;)

---

### Post by jfbooth on 2010-06-26
> **anewguy said:**
> I *think* you have to add -t ext4 in the fsck line.  I say this since you booted from CD there is no fstab entry for your hard disk, so it defaults to ext2.  By default I think 10.04 installs as ext4.  This may be why you are getting the errors and they refer to ext2.

I believe if you are still having problems with the device busy that it's probably the swap.  It is my understanding that the LiveCD will use a swap partition if it sees one.

So, I think I would try this:

sudo swapoff

sudo fsck -t ext4 /dev/sda


Dave ;)

I see.  Well, speculation worries me .. at this point, I am not sure whether my file system is ok or not.  From what I can tell, there is no 'risk' in your suggestion .. so I will do that and post the results.  Hang on.  To my knowledge sda is unmounted .. that is the last thing I told it to 'be'.:

root@ubuntu:/# swapoff -a
root@ubuntu:/# fsck -t ext4 /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

root@ubuntu:/#

I conclude something is still wrong.

---

### Post by k3lt01 on 2010-06-26
I have to admit your partitions seem odd to me so some of what I am suggesting is guessing what is going on and trying to work through it. I agree with Dave (anewguy) and think fsck might be confused with the ext4 formatting but having said that I also would have thought fsck off a LiveCD would know about ext4 and be able to cope with it.

---

### Post by k3lt01 on 2010-06-26
> **jfbooth said:**
> I conclude something is still wrong.I agree.

---

### Post by CharlesA on 2010-06-26
I think you are just trying to check the drive, not the individual partitions.

EDIT: Judging from what you'd already said in the thread, /dev/sda1 is clean. If you want to force a fsck, you can boot into the OS and run something like this:

```
sudo touch /forcefsck
```

Then reboot and it'll force a fsck to run before the machine boots up.

If you want to just do it from the livecd, run this command:

```
sudo fsck -FC /dev/sda1
```

---

### Post by k3lt01 on 2010-06-26
> **CharlesA said:**
> Try doing this from a livecd:

```
sudo fsck /dev/sda1
```

I think you are just trying to check the drive, not the individual partitions.We have already done this.

---

### Post by CharlesA on 2010-06-26
Try to force a fsck check per my previous post and see what happens. You should be fine.

---

### Post by k3lt01 on 2010-06-26
@jfbooth, what has actually prompted this? I mean why do you need to fsck anyway? You may have already mentioned this but I haven't seen it and just looking through your threads I still haven't seen anything to say why.

---

### Post by CharlesA on 2010-06-26
There was a power outage from what I read. Linux file systems are a bit more robust than Windows file systems, at least in my experience.

---

### Post by anewguy on 2010-06-26
I recommended the -t ext4 on the fsck because if you read the man page you'll see that it mentions that when there is no fstab entry for the disk (which there shouldn't be when it's a LiveCD) it will default to ext2.  You may want to check that yourselves in case I am misinterpreting anything.  I noticed on the last attempt it still got the invalid ext2 error - another indication that I think it is defaulting to the incorrect file system type.  

For jfbooth:

Did you install xubuntu 10.04 from scratch or did you do an "upgrade" from a previous release?

Dave ;)

---

### Post by k3lt01 on 2010-06-26
I meant what prompted wanting to fsck in the first place. Did the machine just stop booting? Or did something else happen? Or are we just trying a new learning experience? I'm just a little lost atm as to the purpose of this exercise.

---

### Post by jfbooth on 2010-06-26
> **CharlesA said:**
> I think you are just trying to check the drive, not the individual partitions.

EDIT: Judging from what you'd already said in the thread, /dev/sda1 is clean. If you want to force a fsck, you can boot into the OS and run something like this:

```
sudo touch /forcefsck
```

Then reboot and it'll force a fsck to run before the machine boots up.

If you want to just do it from the livecd, run this command:

```
sudo fsck -FC /dev/sda1
```

OK .. so I shut down from the live CD session and restarted from hard drive.  Opened terminal .. did not unmount anything.  I entered:

sudo touch /forcefsck

and hit return.  did not get challenged for a password .. but I expected to.  Just went to the next terminal prompt.

Did a restart .. machine went down, came back up but it took a long time coming up.  No errors.  I guess it was fsck'ing something.  And here I am.

Maybe there is nothing wrong with the freekin file system.  I really can't tell ... from anything.  fsck from live cd sure indicated something is wrong .. but .. well, just don't know.

Yes, .. this machine has had a couple of illegal restarts/shudowns due to come electricians who are doing work on my house hitting the main switch to the house .. and I THOUGHT it would be a good idea to 'chkdsk' my hard drive ... which turns out to be fsck from live CD.  I had no idea it was this complicated or 'mystic'.  I still don't know if anything is wrong with it.  I 'GUESS' everything is fine.

I have one valid question at this time .. unlike chkdsk which finds and fixes errors .. does fsck only find errors?  I get the feeling that is all it does .. just lets you know if something is wrong ,,, doesn't actually fix anyting on its own.  This is an academic question.

IN ANY CASE .. no one had to help me .. and I REALLY appreciate everyone's energy and valuable time.  I don't consider the matter closed .. and maybe someone will have some kind of conclusive input or further instructions.  Again, .. thank you all .. sincerely.

---

### Post by k3lt01 on 2010-06-27
fsck will fix errors if it finds them and you allow it to. After a certain number of reboots, about 25 I think, the system will do it naturally and tell you if it finds anything. It will say press F if you want to fix the errors and a couple of other options.

---

### Post by jfbooth on 2010-06-27
>  Did you install xubuntu 10.04 from scratch or did you do an "upgrade" from a previous release? 

I upgraded from the previous version .. think that makes a difference???

>  fsck will fix errors if it finds them and you allow it to. After a certain number of reboots, about 25 I think, the system will do it naturally and tell you if it finds anything. It will say press F if you want to fix the errors and a couple of other options. 

Well thats encouraging .. just have to reboot 20(?) more times and it will 'take care of itself'.  thank you for that.  It is encouraging ... seriously.  thank you.

---

### Post by anewguy on 2010-06-27
What previous version did you upgrade from?  It's possible that the default file system was ext3 at that time (9.10??).  If so, that would indicate you would need to change the manual fsck to -t ext3.

I'd say your file system is fine - Ubuntu is a little better that way.  The only thing I haven't done yet that I do in Windows is turn off write caching.  That way I don't have some buffer not get written to disk.

Dave ;)

---

### Post by Shazaam on 2010-06-27
jfbooth...
Going back to what caused your problem in the first place, I strongly urge you to purchase a UPS (battery backup system). They can be found at many retailers and are indipensable. Good ones can be bought for a reasonable price (roughly $100 US) and can be easily configured using linux or Windows.
I learned the hard way by having a power outage trash a new pc.

---

### Post by jfbooth on 2010-06-27
> **anewguy said:**
> What previous version did you upgrade from?  It's possible that the default file system was ext3 at that time (9.10??).  If so, that would indicate you would need to change the manual fsck to -t ext3. 

Yes .. upgraded from 9.10 Xubuntu.  I apologize, but could you give me 'line for line' commands?  What directory to be in to avoid a mount, unmount what  sda?, .. there has been so much input, I am not sure anymore.  Could you maybe start with:

Boot Live CD.
Run Terminal


>  I'd say your file system is fine - Ubuntu is a little better that way.  The only thing I haven't done yet that I do in Windows is turn off write caching.  That way I don't have some buffer not get written to disk.

Dave ;)

Probably is fine .. I just think an fsck on the drive (sda), or each and every partition, one at a time, should not produce error messages and warnings.  As for write caching .. good idea, but at the moment, I just want to stay involved with fsck and getting a 'good' run on it.

>  I strongly urge you to purchase a UPS (battery backup system). 

Very good advice, Shaz.  I will do that.  This box is intended to be 'up' 24/7.

---

### Post by Miljet on 2010-06-29
I could be wrong but this is how I see it. The only reason that you are throwing errors is that you insist on running fsck on the entire disk which includes the swap partition. It is exceedingly difficult to check the file system on a swap partition, since it has NO FILE SYSTEM.

If fsck finds no errors on sda1, then you have no problem.

---

### Post by jfbooth on 2010-06-29
Miljet, I would say that is an excellent notion.  Maybe that is the answer .. would be nice to know for sure.  Thank you.

---

### Post by jfbooth on 2010-08-19
I FINALLY found a 'proper' way to run fsck on demand. No need for Live CD .. simply stop all programs and open terminal:

sudo shutdown -r -F now

Credit goes to "Bryann":

[https://lists.ubuntu.com/archives/kubuntu-users/2006-August/008395.html](https://lists.ubuntu.com/archives/kubuntu-users/2006-August/008395.html)

Thank you, everyone for your efforts to assist.

---

