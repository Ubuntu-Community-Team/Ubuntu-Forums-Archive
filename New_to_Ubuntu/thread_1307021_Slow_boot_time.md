---
title: "Slow boot time?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-10-30
I just upgraded to 9.10 from 9.04 recently and I've noticed the boot time lengthen quite a bit.

It takes about 30 seconds to get to the login screen after selecting Ubuntu. Of those 30 seconds, it takes about 5 seconds to get to the white ubuntu circle, then it stays on that logo for about 10 seconds, then it take about 15 seconds to get to the login screen.

To put things in perspective, Windows 7 pro gets to the login screen in 21 seconds.

Both are equally usable after logging in (I don't have to sit and wait for tray icons to load in Windows 7, I have firefox running in about 4 seconds).


Any ideas of why boot time slowed down for Ubuntu? (on top of that my sound stopped working, but that's not the point of this thread)

---

### Post by wmunguiam on 2009-10-31
Dear friends,

I've already upgraded my 9.04 to 9.10 and the only bad issue is the loooooong time to boot. 

With 9.04 the whole system used to take about 12 seconds (because I was using Ext4 insted ext3)

But now with this new version 9.10 I have to wait three times than usual.

I am looking for a solution ... 

best regards

---

### Post by humphreybc on 2009-10-31
Hi guys,

Yes there have been some problems with the new boot system in Karmic. As you may know, the boot process has been re-designed completely from the ground up, with grub2 instead of grub, a new splash screen (two in fact!), a new read a head program and startup app/session management.

Unfortunately it isn't as fine tuned as it should be, so, people have been reporting delays in boot time coming from Jaunty.

If you are using bootchart to record your time, remember that the new bootchart in karmic records from GRUB all the way to stable desktop, whereas Jaunty was only from GRUB to the login prompt, so bootchart will seem as though the time is taking 3x as long.

Could you guys install bootchart (suda aptitude install bootchart) and then restart your computer. You'll find the bootchart image in /var/log/bootchart.

If you could add this image to a zip file and attach it so we can have a look that'd be good. Make sure you add it to a zip file, otherwise it gets resized and we can't see it in detail :)

Thanks!

---

### Post by HiImTye on 2009-10-31
I also have this, it sits at the white logo for a bit (I assume while it tests hardware and such) before it gets to the new (amazing looking, I might add) boot screen. it takes longer right now to boot than it did on my older computer (was using a PIII Coppermine overclocked)

this doesn't really bother me that much as I spend so little of my computing time actually booting since Ubuntu runs well for 30+ days (the time it takes for a new kernel to come out or something else that requires that I reboot) but it is rather disheartening given all the youtube 'win7 vs karmic bootup race' videos. was expecting much faster bootup. but then this is release time so the real bugs come out now :P

will install that package and upload once my download finishes :D

---

### Post by humphreybc on 2009-10-31
Oh also, check this please. Open a terminal and type this:

```

sudo gedit /etc/fstab

```

Where there is an entry for your hard drives, there should be two digits at the end of each line. Both digits should, in most cases, be two **zeros.** The first digit deals with a dump backup feature, not important, but the second one we are interested in. If this is a 1, then on every boot Ubuntu will perform a disk check, which drastically slows down boot.

I think that on a fresh install, disk check is enabled by default on every boot.

So, your entry for any particular drive should look something like:

```

# Filesystem - / was on /dev/sda1 during installation
UUID=884c9e30-3565-455f-bc58-c935a6984621 /               	ext4   			errors=remount-ro 		0       0

```

---

### Post by underquark on 2009-10-31
Put it into perspective against Windows.  I switched on my older Win XP machine (Pentium dual-core), let it warm up and logged in then went next door and switched on my ubuntu machine.  Even leaving the 10-second pause before ubuntu boots (default on my dual-boot machine) and then logging in the ubuntu machine was up and ready and I was onto this forum 47 seconds before the Win XP machine was ready to do anything.  Both of them access my home network wirelessly and the Win XP machine doesn't have too many startup programs or bells and whistles (neither does the ubuntu machine, mind you).

---

### Post by HiImTye on 2009-10-31
> **humphreybc said:**
> Oh also, check this please. Open a terminal and type this:

```

sudo gedit /etc/fstab

```Where there is an entry for your hard drives, there should be two digits at the end of each line. Both digits should, in most cases, be two **zeros.** The first digit deals with a dump backup feature, not important, but the second one we are interested in. If this is a 1, then on every boot Ubuntu will perform a disk check, which drastically slows down boot.

wouldn't you know it, there was one entry with a 0, let's see if it speeds anything up :D

---

### Post by humphreybc on 2009-10-31
> **underquark said:**
> Put it into perspective against Windows.  I switched on my older Win XP machine (Pentium dual-core), let it warm up and logged in then went next door and switched on my ubuntu machine.  Even leaving the 10-second pause before ubuntu boots (default on my dual-boot machine) and then logging in the ubuntu machine was up and ready and I was onto this forum 47 seconds before the Win XP machine was ready to do anything.  Both of them access my home network wirelessly and the Win XP machine doesn't have too many startup programs or bells and whistles (neither does the ubuntu machine, mind you).

Is that running Jaunty like you say in your sig? Good to hear that Ubuntu is booting up fast for some. I think it's quite a varying topic, there are a lot of variables that can affect bootup. BIOS, GRUB, spreadahead/readahead, linux kernel, HDD speed, amount of RAM, type of CPU, encrypted directories or lots of hard drives to mount, auto login enabled or not etc etc etc

But I do admit that Karmic seems slower than Jaunty on my machine too. Not by much, but it's not a positive improvement such as the devs have been touting. Oh well, I see that the proposed updates from today had some new updates to xplash to fix a few problems. I'm sure they'll get onto it quick in the next week or two.

Anyway, i'm off to bed! Goodnight ya'll!

---

### Post by humphreybc on 2009-10-31
> **HiImTye said:**
> wouldn't you know it, there was one entry with a 0, let's see if it speeds anything up :D

You mean one entry with a 1? You want to be all 0's, no 1's at all :P

Oh, also I should mention make a backup of your fstab before editing stuff... how forgetful of me to remind you beforehand!

---

### Post by HiImTye on 2009-10-31
yeah a 1 :P all zeroes except for one for my main drive (the one with ubuntu)

how is ext4 btw (since your fstab entry says youre using it), I hear mixed things about it (mostly the bad is the possibility of data loss)

---

### Post by Lazy-buntu on 2009-10-31
I'm wondering if there's something wrong with the CPU speed?

I run ```
cat /proc/cpuinfo
``` and it says 800MHz per core. Shouldn't I be seeing 3.2GHz? (note I've got a tri-core, so it's not 4 x .8 = 3.2)

I'm reading your posts now so I'll post back in a minute.

---

### Post by Lazy-buntu on 2009-10-31
I've got the double zeros like you

> **humphreybc said:**
> Oh also, check this please. Open a terminal and type this:

```

sudo gedit /etc/fstab

```

Where there is an entry for your hard drives, there should be two digits at the end of each line. Both digits should, in most cases, be two **zeros.** The first digit deals with a dump backup feature, not important, but the second one we are interested in. If this is a 1, then on every boot Ubuntu will perform a disk check, which drastically slows down boot.

I think that on a fresh install, disk check is enabled by default on every boot.

So, your entry for any particular drive should look something like:

```

# Filesystem - / was on /dev/sda1 during installation
UUID=884c9e30-3565-455f-bc58-c935a6984621 /               	ext4   			errors=remount-ro 		0       0

```

---

### Post by netdevil on 2009-10-31
I've upgraded from 9.04 to 9.10 and boot time is pretty long infact one can go to sleep waiting for stable desktop to load. If one uses startup manager and removes splash screen then you realize that the system check for various unwanted devices is consuming time. Any fix for this. Ubuntu 9.10 has been pretty disappointing up to now.

---

### Post by Crandom on 2009-10-31
> **Lazy-buntu said:**
> I'm wondering if there's something wrong with the CPU speed?

I run ```
cat /proc/cpuinfo
``` and it says 800MHz per core. Shouldn't I be seeing 3.2GHz? (note I've got a tri-core, so it's not 4 x .8 = 3.2)

This sounds like powersaving, it is probably in "ondemand" mode where it reduces your CPU frquency when not much is happening. To be sure of this, right click on your top gnome-panel > Add to panel > Drag the "CPU Frequency Scaling Monitor" onto the gnome-panel. Click on the icon, and you should have a choice between ondemand, conservative, performance etc as well as a whole range of frequencies. If this isn't the case, then you may be right to be worried.

**EDIT:** For me, the 9.10 experience has been great. My boot time is now about 15 secs instead of 25 and my wireless has FINALLY begun to connect to my access point first time, and I managed to install off of an external usb hdd rather than using a cd (using grub2)!

---

### Post by motorcity909 on 2009-10-31
I upgraded this morning from 9.04 to 9.10.  I'm mostly happy but I too have noticed a slower boot time - 9.04 went from pressing the on-button to a loaded Firefox webpage in 65 seconds; the same in 9.10 is taking 1 min 45 sec.

This is the output from fstab:-

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=5e48d577-470d-458a-87a1-24a6ea9c7574 / ext3 relatime,errors=remount-ro 0 [SIZE=2][COLOR=Red]**1**[/COLOR][/SIZE]
# swap was on /dev/sda5 during installation
UUID=14e70801-261d-4e25-b8bd-b95575ba6509 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

Am I right in saying that if I change that **[COLOR=Red]red 1[/COLOR]** to a zero, it won't run the disk check everytime and thus should make my boot up quicker?

Cheers all.

---

### Post by 5nak3 on 2009-10-31
I never knew about the fstab feature. In any case I ran it out of curiosity and found the following:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sda1 during installation
UUID=bfe99f55-1193-42f9-9500-b32a1d720365 /               ext4    errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sda5 during installation
UUID=e1cc4ed6-ed7b-4800-92d8-01661e6cd2e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Now the above bit in red as you can guess is my Ubuntu Karmic partition. As the previous poster  (motorcity909) has asked, does changing the 1 to a 0 actually mean that the check will be bypassed?

In addition to this, I would also like to understand what the purpose of that initial check or "pass" as fstab calls it does. If it is something useful, I wouldn't mind keeping it.

It is a shame that I never check Jaunty's fstab to see what the setup was like.


----EDIT----

I just check the man page for fstab and found the following 

> The  sixth field, (fs_passno), is used by the fsck(8) program to deter&#8208;
       mine the order in which filesystem checks are done at reboot time.  The
       root  filesystem  should  be specified with a fs_passno of 1, and other
       filesystems should have a fs_passno of 2.  Filesystems within  a  drive
       will  be checked sequentially, but filesystems on different drives will
       be checked at the same time to utilize  parallelism  available  in  the
       hardware.   If  the sixth field is not present or zero, a value of zero
       is returned and fsck will assume that the filesystem does not  need  to
       be checked.

I'll admit while i understand the meaning of pass from the above, I don't understand whether or not this is useful for the end user. I would assume that my filesystem is ok, and therefore of no need to be checked since everything works. But I'm aware this may not actually be what the pass actually checks.

---

### Post by Lazy-buntu on 2009-10-31
The CPU frequency and scaling thing does show that it is saving power for whatever reason. Is there a way to keep it always on performance? Even if I set it to 3.2GHz manually, I do cat /proc/cpuinfo and still get 800MHz.

You think this one of the reasons for the slow boot?

---

### Post by Zoot7 on 2009-10-31
> **Lazy-buntu said:**
> The CPU frequency and scaling thing does show that it is saving power for whatever reason. Is there a way to keep it always on performance? Even if I set it to 3.2GHz manually, I do cat /proc/cpuinfo and still get 800MHz.
You think this one of the reasons for the slow boot? 

IMO it's unlikely. Hard Drive speed is normally the bottleneck upon booting.

---

### Post by Lazy-buntu on 2009-10-31
I'm wondering if my CPU was throttled when updating to Karmic, because I booted about 15-20 seconds faster on Jaunty.

> **Zoot7 said:**
> IMO it's unlikely. Hard Drive speed is normally the bottleneck upon booting.

---

### Post by moore.bryan on 2009-10-31
I'm very interested into an answer on this... my fstab's were always 0's, but if I set this in Karmic, will it *never* run a fsck check?

> **5nak3 said:**
> I never knew about the fstab feature. In any case I ran it out of curiosity and found the following:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sda1 during installation
UUID=bfe99f55-1193-42f9-9500-b32a1d720365 /               ext4    errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sda5 during installation
UUID=e1cc4ed6-ed7b-4800-92d8-01661e6cd2e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Now the above bit in red as you can guess is my Ubuntu Karmic partition. As the previous poster  (motorcity909) has asked, does changing the 1 to a 0 actually mean that the check will be bypassed?

In addition to this, I would also like to understand what the purpose of that initial check or "pass" as fstab calls it does. If it is something useful, I wouldn't mind keeping it.

It is a shame that I never check Jaunty's fstab to see what the setup was like.


----EDIT----

I just check the man page for fstab and found the following 



I'll admit while i understand the meaning of pass from the above, I don't understand whether or not this is useful for the end user. I would assume that my filesystem is ok, and therefore of no need to be checked since everything works. But I'm aware this may not actually be what the pass actually checks.

---

### Post by Zoot7 on 2009-10-31
> **Lazy-buntu said:**
> I'm wondering if my CPU was throttled when updating to Karmic, because I booted about 15-20 seconds faster on Jaunty.
I know it's not much of a fix but does turning off Cool n' Quiet in the BIOS have any effect on the boot time? Worth a shot...

---

### Post by occams_beard on 2009-10-31
Ditto on the slow karmic boot time. It seems to take twice as long to get to the desktop as it did in Jaunty.

Also it "flickers" more than Jaunty. Mine goes from grub, to console, to the white logo thing, back to console, then to the new boot screen, then finally to desktop.

All in all, it's quite a disappointment and looks cheesy.

---

### Post by Lazy-buntu on 2009-10-31
That, and grub didn't pick up the new kernel. I tried to fix it, but now I can't even boot into ubuntu now.

If anyone's interested in that problem see: [http://ubuntuforums.org/showthread.php?p=8208130](http://ubuntuforums.org/showthread.php?p=8208130)

> **occams_beard said:**
> Ditto on the slow karmic boot time. It seems to take twice as long to get to the desktop as it did in Jaunty.

Also it "flickers" more than Jaunty. Mine goes from grub, to console, to the white logo thing, back to console, then to the new boot screen, then finally to desktop.

All in all, it's quite a disappointment and looks cheesy.

---

### Post by eauque on 2009-11-01
Did an upgrade. The only slowdown I see so far is slower boot time. Am able to use Normal Visual Effects now. Prior to the upgrade, Firefox was REALLY choppy with Normal turned on and my 512MiB/1000Mhz machine was generally slow. Normal Effects is usable now.

Still, disappointed by the slower boot time. First couple boots presented me with a malformed Ubuntu screen. Seems OK now.

Give and take.....

---

### Post by Ni85 on 2009-11-02
I gave it a shot and changed fstab to 0, but didn't change my boot speed. Bootchart still says 1:29 (give or take 1-2 secs).
It's a lot slower than Jaunty, and it is also quite slow after login to get to a ready desktop.
I am attaching here the last bootchart with fstab with 0's (the file that ends in -4), while the" -3" file is the previous one (with 1 on fstab). Any clue on how to speed it up? Or is it just a matter of waiting for some update that will save us all?

---

### Post by moore.bryan on 2009-11-02
I read somewhere (figures I can't remember where; in fact, it might be in this thread!) the new Karmic boot times reflect from button-push to "usable" desktop, whereas Jaunty was just to the login screen. If that's true, it would make a whole lot more sense.

---

### Post by Ni85 on 2009-11-02
> **moore.bryan said:**
> I read somewhere (figures I can't remember where; in fact, it might be in this thread!) the new Karmic boot times reflect from button-push to "usable" desktop, whereas Jaunty was just to the login screen. If that's true, it would make a whole lot more sense.

yeah, but i never used bootchart before. i started using it now because before i could push the "on" button and would be up and running in 30secs all included, while with karmic i noted long booting times and i wanted to check it out through bootchart...

---

### Post by namelessone on 2009-11-02
My boot time has also dramatically increased. I always time it with a stopwatch. On Jaunty it was around 40ish seconds to boot. Now it takes over a minute.

> **moore.bryan said:**
> I'm very interested into an answer on this... my fstab's were always 0's, but if I set this in Karmic, will it *never* run a fsck check?

I am also curious about this. I know that in Jaunty it was always set to 1 and it did big scan every 20 hdd mounts. Does it really do a check every time? If I set it to zero will I risk losing data or something?

---

### Post by moore.bryan on 2009-11-02
A little bit of research and I found some, possible, answers to the long boot time. Karmic moves away from the well-established Ubuntu way of booting and reorders some things; it would seem at least *some* people are attributing the slowness to that change. In any way, Karmic seems to be going through some growing pains.

As far as the /etc/fstab settings, this has apparently been in changed in Karmic as well. We *want* the 1 in the sixth column because it allows fsck to run on a "regular" basis. It *would* seem setting it to zero causes it to *not *run, which--for me--is a **worse** solution than it running occasionally.

Something else which is still bugging me--literally, since there's many open Launchpad bugs about it--is the random networking failures.

---

### Post by JayD2 on 2009-11-02
[http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html](http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html)

That link describes a way which some people claim improves boot times. I personally haven't tried it because I'm not entirely sure what it does or how to undo it if something goes wrong. Anyone have more insight there?

---

### Post by oldjimsteele on 2009-11-02
After upgrading both an old HP laptop and an asus eee-pc to karmic boot times on both are approx 1.5 - 2X slower than they were with jaunty.  A white ubuntu logo to load a moving ubuntu splash to load login to revert to the splash for a while before loading a working desktop.  It seems like more of a regression if the point is to quickly boot a computer.  Other than that both regular 9.10 and UNR 9.10 are great.

---

### Post by jap1968 on 2009-11-03
I updated my three computers at home from 9.04 to 9.10, and I am suffering this problem on all the computers.

Boot times have almost dubbed on every computer. even having very different components.

I have tested all the pre-releases since alpha-4 on my netbook, and boot times were really fast until alpha-5. Starting from alpha-6 they changed several things in order to use upstart, and boot times increased notably. Since it was an alpha version I supposed that the final version will achieve even better times that with alpha-5, but obviously it is not the case.

You can find additional information on [Ubuntu 9.10 boot times]("http://ospatia.blogspot.com/2009/08/novedades-en-ubuntu-910.html") in a blog entry that I wrote a couple of months ago (in Spanish).

The boot delay is related to upstart. I consider that topics related to disk checks (fstab flags) and cpu speed are not related to this problem.

---

### Post by Praxicoide on 2009-11-03
There's a *slight* increase in boot time, but I went from a compiled to a generic kernel. To me it's no biggie in any case. I'll compile again when 2.6.32 comes out.

---

### Post by P4man on 2009-11-03
> **JayD2 said:**
> [http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html](http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html)

That link describes a way which some people claim improves boot times. I personally haven't tried it because I'm not entirely sure what it does or how to undo it if something goes wrong. Anyone have more insight there?

It shaved about 15s (!) from my karmic boot time with no ill side effects (second boot only gives full advantage). But its not entirely risk free I imagine, being prerelease. Use at your own risk as Im not too sure how to undo it either

---

### Post by bcoffield on 2009-11-04
I'm having the same exact issue that others have described.  Upgraded from 9.04 and now the boot time is significantly longer and goes through the same process as described above.

Seems really strange especially considering that improved boot time was one of the major things touted as improvements to be noticed by the average end user with 9.10.  9.04 boot times were already awesome.

So, is this boot time increase essentially a wait-n-see type of thing?  Is it something likely to be addressed through updates by the developers?

---

### Post by wobin77 on 2009-11-04
Same here... I did change the the checkdisk on boot. But no difference, so put it back to 1.

---

### Post by compaq615 on 2009-11-06
> **P4man said:**
> It shaved about 15s (!) from my karmic boot time with no ill side effects (second boot only gives full advantage). But its not entirely risk free I imagine, being prerelease. Use at your own risk as Im not too sure how to undo it either

I did not time it, but after performing this upgrade, my Koala is notably faster on second bootup than before. So far, also no side effects (so far)...living on the edge pays of;)

---

### Post by Pebble2009 on 2009-11-09
> **JayD2 said:**
> [http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html](http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html)

That link describes a way which some people claim improves boot times. I personally haven't tried it because I'm not entirely sure what it does or how to undo it if something goes wrong. Anyone have more insight there?


My boot time was 1 min 32 seconds, before i tried this out. Now im down to 49 seconds.

---

### Post by zarf on 2009-11-18
OK, when it comes to slow boots i believe i win :) with  3:21.

I did make the changes suggested by *humphreybc* in post#5 which did speed it up a touch - I was over 4 mins before.

anyway... I have installed Bootchart and attached a zipped copy of the image. If anyone would be so kind as to have a look and see what I cannot, thanks

Chich

and maybe related or not, but I have noticed that if I boot into XP and then reboot, the system hangs with a "no such disc" error. It will boot from the CD tho'.

---

### Post by svkndv on 2009-11-18
> **JayD2 said:**
> [http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html](http://www.omgubuntu.co.uk/2009/10/get-dramatically-faster-boot-times-in.html)

That link describes a way which some people claim improves boot times. I personally haven't tried it because I'm not entirely sure what it does or how to undo it if something goes wrong. Anyone have more insight there?

I feel replacing kernel with new version will make drivers incompatible. This happens if we have a device driver(in my case wireless adapter driver) compiled against specific kernel version

---

### Post by P4man on 2009-11-18
Its not a new kernel. It basically seems to replace (s)readahead with an in improved ureadahead. Been using it for a month now, with no problems with updates or drivers. Of course YMMV but I havent heard of anyone having problems with this.

from the man page:

> NAME
       ureadahead - Read files in advance during boot

SYNOPSIS
       ureadahead [OPTIONS]...  [PACK]

DESCRIPTION
       ureadahead  (über-readahead)  is  used  during  boot  to  read files in
       advance of when they are needed such that they are already in the  page
       cache, improving boot performance.

       When started without any arguments, it checks for the existance and age
       of the default pack file /var/lib/ureadahead/pack, and if  not  present
       or  older  than a month, will discard it and retrace the boot sequence.
       The pack will then contain information about the  files  opened  during
       boot, and the blocks that were in memory at the completion of the boot.

       If  the file exists and is newer than a month old, or an alternate PACK
       path is given on the command-line, the files listed  in  the  pack  are
       opened  and  the blocks read into the page cache using the readahead(2)
       system call.


---

