---
title: "Hibernate/Suspend Not working"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by Windows Nerd on 2009-08-16
Thank you to AlexsAntidote for submitting a solution to my problem:

> **AlexsAntidote said:**
> I have been using Ubuntu since 7.04 on my Acer Notebook and for a long time could not get the suspend/hibernate to work. I tried everything... 

However, I found a fix (at least for my problem) inadvertently while trying to fix the freeze bug with 9.04 and now suspend and hibernate work flawlessly for me.

Here's what I did:

Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do ```
sudo apt-get update && sudo apt-get upgrade
``` (this is especially important if you have a Nvidia video card).

Download and install the latest Kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/") (if you have a 64 bit processor and installation, make sure you choose 64 bit, otherwise get the 386)

Restart and boot with the new kernel. Enjoy!

Thanks Alex! Here is a detailed guide that worked for me. If you have a 64 bit system, your instructions will be slightly different. In a short while I will update this post for those of you with a 64 bit system.

[U][B]Solution Information

[/B][/U]Note: If you see any spelling/grammar mistakes or readability issues in this post, please notfy me by post/PM. I want this thread to help others as much as possible!

[B]The Problem/Situation

[/B]When using Ubuntu 9.04 (Jaunty Jackelope), when you click suspend or hibernate, the screen goes black, but the computer still is running, as you can hear the fan, and the power light does not indicate that you have suspended the computer. When you try to "wake" the computer by pressing the power button, clicking/moving the mouse, or typing anything in the keyboard, it does not work. Nothing that you try to wake the computer works-the only remaining option is to force a hard reboot. This happens with _both_ suspend and hibernate options.

_My system specs:_

Gateway computer Model MT6709

The Computer came with Windows Vista 32-bit Home Premium Installed, which was used as the sole operating system for 2 years. 

Windows is currently dual booted alongside Ubuntu Jaunty Jackelope, each on their separate partition (Wubi was NOT used), and there is also a 4 Gb Swap partition

2.5 Gb of ram (Upgraded from the 1.5 Gb it came with)
150 Gb Solid-State Hard Drive
Processor: Genuine Intel(R) CPU T2080 @ 1.73GHz   1.73GHz
Graphics Card: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

[B]The Solution

[/B]Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat...ive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do      

```

sudo apt-get update && sudo apt-get upgrade 

```Then do:

     ```

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")

sudo dpkg -i linux-headers-2.6.30-*.deb linux-image-2.6.30-*.deb

```If anyone thinks I should add other information to this post, please notify me by post/PM. Also notify me if you want help or don't understand my instructions via PM

Hope this helps!

Scott

---

### Post by Cuco3 on 2009-08-16
> **Windows Nerd said:**
> Hi all,

I just installed Ubuntu alongside my windows in a dual-boot fashion. I am loving the new operating system so far, though with one issue: Hibernate and Suspend Features do not work properly. I click either one of them, and m yscreen goes black, with a blinking white underscore-like thing at the top left of my screen. I assume this is what happens when one goes into Hibernate or suspend. The only problem then is that I cannot "wake" My computer, meaning that no matter what, if I press keys, move my mouse, plug in an external device ect., it does not come back the display I was in before. I have to power it off by holding the power button and reboot and login and all that.

I am aware that many other people have this same issue, though I have not found any resolution, as it probably has to do with my hardware, which is unique to each computer.

On another not, when booting up, logging in, and changing my screen brightness, a blue and white checkered-ish patterned-box appears in the top left of my screen.

A solution is greatly appreciated, as I currently cannot put my computer in a low power state on Linux!   

ScottGet used to it, I haven't gotten my Suspend to work properly either and the solutions I've tried don't work. There appears to be no solution.

When I suspend my computer, then resume, the screen starts flickering. The only way to stop it from flickering is to restart (which defeats the point of suspending; might as well turn off the computer).

You're better off sticking with Windows or Mac.

---

### Post by Windows Nerd on 2009-08-16
> **Cuco3 said:**
>  
You're better off sticking with Windows or Mac.

I thought this was a* help* forum for *_Ubuntu_. *I asked for a solution if possible. I know others have the same issue.

If you have a possible solution or a website/wiki I could check out, let me know. 

Scott

---

### Post by mrbiggbrain on 2009-08-16
Are you useing Wubi? becuse suspend/hibernate dont work on Wubi at all.

---

### Post by ptrivino on 2009-08-16
> **Windows Nerd said:**
> Hi all,

I just installed Ubuntu alongside my windows in a dual-boot fashion. I am loving the new operating system so far, though with one issue: Hibernate and Suspend Features do not work properly. I click either one of them, and m yscreen goes black, with a blinking white underscore-like thing at the top left of my screen. I assume this is what happens when one goes into Hibernate or suspend. The only problem then is that I cannot "wake" My computer, meaning that no matter what, if I press keys, move my mouse, plug in an external device ect., it does not come back the display I was in before. I have to power it off by holding the power button and reboot and login and all that.

I am aware that many other people have this same issue, though I have not found any resolution, as it probably has to do with my hardware, which is unique to each computer.

On another not, when booting up, logging in, and changing my screen brightness, a blue and white checkered-ish patterned-box appears in the top left of my screen.

A solution is greatly appreciated, as I currently cannot put my computer in a low power state on Linux!   

Scott

So, I am kinda new to Ubuntu myself, but here's what I see:  in System|Preferences|Power Management, the settings in the "On AC Power" say 'Put computer to *sleep* when inactive for...' with a slider control.  So I don't know if that counts as Suspended or Hibernating (or Asleep, and frankly I've never known the difference between Hibernation and Suspension even in Windows [where they NEVER work]).  But mine DOES work, except that I have to use the power button to re-animate it (unsleep or unhibernate or WTF-ever), the usual keyboard or mouse move doesn't do it in Ubuntu AFAICT.

Hopes this helps.

Paul

---

### Post by Windows Nerd on 2009-08-16
No I am not using Wubi, I clarified that in my first post by saying that I *dual booted* Linux alongside Windows. But anyways, I was aware that Hibernate/Suspend did not work in Wubi as I tried it before I permanently installed it on a separate partition.

---

### Post by Windows Nerd on 2009-08-16
> **ptrivino said:**
> So, I am kinda new to Ubuntu myself, but here's what I see:  in System|Preferences|Power Management, the settings in the "On AC Power" say 'Put computer to *sleep* when inactive for...' with a slider control.  So I don't know if that counts as Suspended or Hibernating (or Asleep, and frankly I've never known the difference between Hibernation and Suspension even in Windows [where they NEVER work]).  But mine DOES work, except that I have to use the power button to re-animate it (unsleep or unhibernate or WTF-ever), the usual keyboard or mouse move doesn't do it in Ubuntu AFAICT.

Hopes this helps.

Paul


I don't know if there is a difference between sleep/suspend. I know hibernate is different because it saves system data or whatever to a thingy then essentially turns your computer off, and then reloads that data next time you turn it on.

If it makes a difference, Sleep/Hibernate features work perfectly for me on Windows.

---

### Post by ptrivino on 2009-08-16
> **Windows Nerd said:**
> I don't know if there is a difference between sleep/suspend. I know hibernate is different because it saves system data or whatever to a thingy then essentially turns your computer off, and then reloads that data next time you turn it on.

If it makes a difference, Sleep/Hibernate features work perfectly for me on Windows.

Cool, (and 'hibernate *never* works in Windows' is an exaggeration but I've never had much luck with it).

The hibernation I see in Ubuntu is what I would call an abbreviated boot, takes maybe 20 seconds, but I do get all my open apps/terminal sessions etc. right where they were.

Paul

---

### Post by Windows Nerd on 2009-08-16
Okay, back on topic; I still am asking for a possible solution...anyone?

---

### Post by jrox717 on 2009-08-17
If you've done your research you probably know about this, but is your swap partition being used? Check free or top in a terminal.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by anewguy on 2009-08-17
Opinions and results vary, but you should try setting your swap size to at least 2 times your physical memory plus some overhead.  I'm not exactly sure how things work now in Ubuntu, but long ago if you were to hibernate, the system copied all of physical memory plus a small amount of overhead to virtual memory.  That way when you restart things should be right where you left off.  If you haven't tried that, you may want to to see if it helps.  

Also, somewhere either in this forum or in a Yahoo search with Linux, I saw something about making your video restart at wake up.  You may want to search for that as well if you haven't already.

Wish I could try to help you more.

Dave :)

---

### Post by Windows Nerd on 2009-08-17
Hmm I remember making a Swap partition at all. This all makes sense then. I have 3 Gb of RAM on my computer, and if the Swap should be double the RAM...Thats quite a lot for Swap. I know that the recommended Swap size is anywhere between 1-3 Gb.

Thanks a lot, I shall make a Swap partitionmand see if my problem clears.

Scott

---

### Post by jrox717 on 2009-08-18
I usually hear that swap should be between 1 and 2 times the size of your RAM. I would guess that 3 gigs is good

---

### Post by Windows Nerd on 2009-08-18
Okay...so about a 4 Gb Swap size then....

Now, as far as making the swap partition.

I know what the partition settings should be: A logical partition formatted to Swap or Linux-Swap. The only thing is that you should be doing this while installing Ubuntu. I have already installed it, though with no swap.

Anyone want to tell me how to create a Swap partition in these circumstances? I am not afraid of the terminal or command-line, and I will use it if the method requires it.

Scott

---

### Post by jrox717 on 2009-08-18
[http://ubuntuforums.org/showthread.php?t=516961]("http://ubuntuforums.org/showthread.php?t=516961")

---

### Post by Windows Nerd on 2009-08-18
I have seen that thread before actually. It just recommends GParted, which I have never had good luck with. I shrink my Linux partition by 4 Gb for my swap file. and then set that free space to a Swap Partition. I click apply, and it does neither and gives me an error message saying something like (changes not applied/changes failed...)

Scott

---

### Post by Chronon on 2009-08-18
Is the partition you're trying to change unmounted?

I wish I had direct help for you.  I had Suspend to RAM working properly on my netbook until last week.  Then something changed and while it suspends and wakes properly, the backlight on my monitor will not turn on after waking up.  Logging out and back in fixes the problem.

---

### Post by milesnapue on 2009-08-18
Gparted should work just fine or you, though as stated in the above post you should only be making changes to unmounted partitions. Guessing you have an ubuntu liveCD seeing as you did a clean install. Boot from the disc and try gparted again. If all goes well with Making your swap you should search for a couple of commands for activating the swap. might have to use the terminal a small amout.

This thread has some good info on mounting swap once it is created [http://ubuntuforums.org/showthread.php?t=365530](http://ubuntuforums.org/showthread.php?t=365530)

---

### Post by AlexsAntidote on 2009-08-18
I have been using Ubuntu since 7.04 on my Acer Notebook and for a long time could not get the suspend/hibernate to work. I tried everything... 

However, I found a fix (at least for my problem) inadvertently while trying to fix the freeze bug with 9.04 and now suspend and hibernate work flawlessly for me.

Here's what I did:

Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do ```
sudo apt-get update && sudo apt-get upgrade
``` (this is especially important if you have a Nvidia video card).

Download and install the latest Kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/") (if you have a 64 bit processor and installation, make sure you choose 64 bit, otherwise get the 386)

Restart and boot with the new kernel. Enjoy!

---

### Post by jrox717 on 2009-08-18
Instead of a partition, try making a swap file instead.

[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?")

(sorry, I really like that FAQ page)

---

### Post by thomasyen on 2009-08-18
I have what could be the same problem: suspend not working in Ubuntu. I suspect that my BIOS is not [ACPI]("http://en.wikipedia.org/wiki/ACPI")-compliant (the whole system came with a CD containing Windows-only motherboard drivers). My computer is a dual-boot as well; Suspend works fine on Windows XP. Maybe that's an explanation? Or did I get it wrong?

---

### Post by Windows Nerd on 2009-08-18
Can you hibernate/suspend to a swap file?

---

### Post by Windows Nerd on 2009-08-18
> **AlexsAntidote said:**
> I have been using Ubuntu since 7.04 on my Acer Notebook and for a long time could not get the suspend/hibernate to work. I tried everything... 

However, I found a fix (at least for my problem) inadvertently while trying to fix the freeze bug with 9.04 and now suspend and hibernate work flawlessly for me.

Here's what I did:

Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do ```
sudo apt-get update && sudo apt-get upgrade
``` (this is especially important if you have a Nvidia video card).

Download and install the latest Kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/") (if you have a 64 bit processor and installation, make sure you choose 64 bit, otherwise get the 386)

Restart and boot with the new kernel. Enjoy!

If when I create a Swap partition and it does not work I will try this-thanx for the advice!

---

### Post by jrox717 on 2009-08-18
>  Can you hibernate/suspend to a swap file? 

[it seems like it's possible]("http://ubuntuforums.org/showthread.php?t=1042946") but it looks quite difficult. I guess you should try to make a partition first.

---

### Post by Windows Nerd on 2009-08-18
Ok I have a Swap partition made. Now to just enable it :). It turns out my problem was that I forgot to unmount the drive before I partitioned it in GPartEd. Silly me :)

---

### Post by Windows Nerd on 2009-08-18
> **milesnapue said:**
> Gparted should work just fine or you, though as stated in the above post you should only be making changes to unmounted partitions. Guessing you have an ubuntu liveCD seeing as you did a clean install. Boot from the disc and try gparted again. If all goes well with Making your swap you should search for a couple of commands for activating the swap. might have to use the terminal a small amout.

This thread has some good info on mounting swap once it is created [http://ubuntuforums.org/showthread.php?t=365530](http://ubuntuforums.org/showthread.php?t=365530)

So, looking through there, I decided to check if my system "knows" if I have a Swap partition. So I ran;

```

free
sudo fdisk -l
cat /ect/fstab

```Here are the results:
> 
scott@scott-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2052444     560140    1492304          0      36788     253428
-/+ buffers/cache:     269924    1782520
Swap:            0          0          0
scott@scott-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63cfb345

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1271    10209276    7  HPFS/NTFS
/dev/sda2   *        1272       13583    98896140    7  HPFS/NTFS
/dev/sda3           13584       18940    43030102+  83  Linux
/dev/sda4           18941       19457     4152802+  82  Linux swap / Solaris

scott@scott-laptop:~$ cat /ect/fstab
cat: /ect/fstab: No such file or directory
Sorry for readability issues from what came out of my terminal. All I did was copy and paste it and the forum does not keep that spacing and all that.

Looking with Nautalis, I can clearly see a fstab file. It reads as follows: 

> 
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8 /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0Any help for activating my swap partition? As you can plainly see, it is there and is correctly formatted as Swap.

Scott

PS: I also saw another suggestion:
> 
2.3 Some people also reported this to help: 
[LIST]
[*]1) cfdisk : erase the old swap partition and recreate a new one 
[*]2) reboot (mandatory) 
[*]3) mkswap /dev/hda8 
[*]4) swapon -a
[/LIST]

I tried going into cfdisk, though it told me this:
> 
FATAL ERROR: Cannot open disk drive
       Press any key to exit cfdisk

---

### Post by AlexsAntidote on 2009-08-18
> **Windows Nerd said:**
> Ok I have a Swap partition made. Now to just enable it :). It turns out my problem was that I forgot to unmount the drive before I partitioned it in GPartEd. Silly me :)

haha! Yeah that would do it. Don't feel bad, I've done that before myself. It's an easy oversight to make.

So did the swap partition help?

---

### Post by AlexsAntidote on 2009-08-19
> **Windows Nerd said:**
> So, looking through there, I decided to check if my system "knows" if I have a Swap partition. So I ran;

```

free
sudo fdisk -l
cat /ect/fstab

```Here are the results:
Sorry for readability issues from what came out of my terminal. All I did was copy and paste it and the forum does not keep that spacing and all that.

Looking with Nautalis, I can clearly see a fstab file. It reads as follows: 

Any help for activating my swap partition? As you can plainly see, it is there and is correctly formatted as Swap.

Scott

Try:
```
cat /etc/fstab
```
It looks like you spelled "etc" as "ect".

Also, use [_code_] instead of [_quote_] (without the _'s), that should keep the spacing.

---

### Post by Windows Nerd on 2009-08-19
> **AlexsAntidote said:**
> Try:
```
cat /etc/fstab
```It looks like you spelled "etc" as "ect".

Also, use [_code_] instead of [_quote_] (without the _'s), that should keep the spacing.
Oh...my thats a stupid mistake of me. Thanks

From Cat /ect/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8 /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Looks the same as if I looked at it with a graphical editor, or ran 

gksudo gedit /etc/fstab

Scott

I am signing off to go to bed now. If anyone can find a solution (I am fine with terminal/command line) for me and post it while I am a snoozin', much wukk be appreciated :)

---

### Post by AlexsAntidote on 2009-08-19
> **Windows Nerd said:**
> 
...
PS: I also saw another suggestion:

I tried going into cfdisk, though it told me this: 
...


Be careful with cfdisk if you use your that disk for other operating systems (I think I recall you mentioning you dual boot with windows?)... read the manual and you'll see why. (man cfdisk)

---

### Post by AlexsAntidote on 2009-08-19
> **Windows Nerd said:**
> Oh...my thats a stupid mistake of me. Thanks

From Cat /ect/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8 /               ext4    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

Looks the same as if I looked at it with a graphical editor, or ran 

gksudo gedit /etc/fstab

Scott

I am signing off to go to bed now. If anyone can find a solution (I am fine with terminal/command line) for me and post it while I am a snoozin', much wukk be appreciated :)

Yeah it looks like your swap partition is not being mounted at boot... 

Run the following to see if your swap partition exists (post output if you want/need help locating it):
```
sudo fdisk -l
```
Take note of the path, mine is /dev/sda6.

If your swap partition is listed in the output, you can find it's UUID by doing the following:
```
blkid
```
(post the output for that too if you want)

If you can find the UUID of your swap, you can add it to fstab:
```
gksudo gedit /etc/fstab
```
(but you knew that part)

add the following line(s):
```

# /dev/sda6
UUID={$yourSwapUUID} none            swap    sw              0       0

```
be sure to insert your swaps UUID above in place of {$yourSwapUUID} (I know, that is obvious right?!)

***Edit***
Also, I forgot to mention to use the following command to turn the swap on, and then reboot:
```
swapon -a
```
***/Edit***

If that doesn't work, read the following for more help: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by jrox717 on 2009-08-19
look at the man page for swapon.

you can find the UUID for the swap partition by
```
 ls -l /dev/disk/by-uuid 
```
then add it to your fstab file (I'll leave it to you to figure that out) and then
```
 swapon -a 
```

---

### Post by AlexsAntidote on 2009-08-19
> **jrox717 said:**
> look at the man page for swapon.

you can find the UUID for the swap partition by
```
 ls -l /dev/disk/by-uuid 
```
then add it to your fstab file (I'll leave it to you to figure that out) and then
```
 swapon -a 
```

Thanks jrox717, I forgot to add the swapon command... also, ls -l /dev/disk/by-uuid is good, but I think blkid is a little easier to read. But it's nice to see we're on the same page.

---

### Post by jrox717 on 2009-08-19
Wow, sorry AlexsAntidote, I must have totally missed your post!

---

### Post by AlexsAntidote on 2009-08-19
> **jrox717 said:**
> Wow, sorry AlexsAntidote, I must have totally missed your post!

:) Hey no worries, I'm glad you posted, I forgot to mention the swapon command and you reminded me. So it's all good.

Take care!

---

### Post by Windows Nerd on 2009-08-19
> **AlexsAntidote said:**
> Yeah it looks like your swap partition is not being mounted at boot... 

Run the following to see if your swap partition exists (post output if you want/need help locating it):
```
sudo fdisk -l
```Take note of the path, mine is /dev/sda6.

If your swap partition is listed in the output, you can find it's UUID by doing the following:
```
blkid
```(post the output for that too if you want)

If you can find the UUID of your swap, you can add it to fstab:
```
gksudo gedit /etc/fstab
```(but you knew that part)

add the following line(s):
```

# /dev/sda6
UUID={$yourSwapUUID} none            swap    sw              0       0

```be sure to insert your swaps UUID above in place of {$yourSwapUUID} (I know, that is obvious right?!)

***Edit***
Also, I forgot to mention to use the following command to turn the swap on, and then reboot:
```
swapon -a
```***/Edit***

If that doesn't work, read the following for more help: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Thanks. I'll do this when I get home. I have about 2 hours from the time I get home and when I go to bed. Sports camp leaves me exausted, and I am there for almost 10 hours a day, for the past 2 and a half weeks.

Scott

---

### Post by Windows Nerd on 2009-08-19
Okay, so here is what happened:
```

scott@scott-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63cfb345

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1271    10209276    7  HPFS/NTFS
/dev/sda2   *        1272       13583    98896140    7  HPFS/NTFS
/dev/sda3           13584       18940    43030102+  83  Linux
/dev/sda4           18941       19457     4152802+  82  Linux swap / Solaris
scott@scott-laptop:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="86126BF0126BE421" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="F0C2BA2BC2B9F5C6" TYPE="ntfs" 
/dev/sda3: UUID="c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8" TYPE="ext4" 
scott@scott-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 86126BF0126BE421 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 cac4572e-80fa-48ae-91bf-86a16d310507 -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 F0C2BA2BC2B9F5C6 -> ../../sda2
scott@scott-laptop:~$ 

```blkid could not see my Swap partition (/dev/sda4), though ls -l /dev/disk/by-uuid could, though the information it told me looks like it was encrypted or something...

Any ideas for finding out the UUID of my swap partition from what you see above, or any other way, so I can add it to my /ect/fstab file? 

Scott

---

### Post by Windows Nerd on 2009-08-19
In other news...I also cannot get any video when I watch youtube videos (I have not tried to view any videos on other sites yet). I think this has something to do with flash or whatnot, though I can hear the audio perfectly fine.

Scott

PS: I found a great quote and have added it to my signature. See below :)

---

### Post by AlexsAntidote on 2009-08-20
> **Windows Nerd said:**
> Okay, so here is what happened:
```

scott@scott-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63cfb345

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1271    10209276    7  HPFS/NTFS
/dev/sda2   *        1272       13583    98896140    7  HPFS/NTFS
/dev/sda3           13584       18940    43030102+  83  Linux
/dev/sda4           18941       19457     4152802+  82  Linux swap / Solaris
scott@scott-laptop:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="86126BF0126BE421" LABEL="Recovery" TYPE="ntfs" 
/dev/sda2: UUID="F0C2BA2BC2B9F5C6" TYPE="ntfs" 
/dev/sda3: UUID="c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8" TYPE="ext4" 
scott@scott-laptop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 86126BF0126BE421 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 c3c892fa-37f2-4dc0-8d7b-8d7e8a7258f8 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 cac4572e-80fa-48ae-91bf-86a16d310507 -> ../../sda4
lrwxrwxrwx 1 root root 10 2009-08-19 11:56 F0C2BA2BC2B9F5C6 -> ../../sda2
scott@scott-laptop:~$ 

```blkid could not see my Swap partition (/dev/sda4), though ls -l /dev/disk/by-uuid could, though the information it told me looks like it was encrypted or something...

Any ideas for finding out the UUID of my swap partition from what you see above, or any other way, so I can add it to my /ect/fstab file? 

Scott

Hey Scott,

Yeah that's really strange... It's interesting that blkid could not detect the UUID for the swap...

It looks like your swap's UUID is: 

You can try adding it to your /etc/fstab (gksudo gedit /etc/fstab), here is the line you want to add:

```

# Swap Partition /dev/sda4
UUID=cac4572e-80fa-48ae-91bf-86a16d310507 none            swap    sw              0       0

```

save, exit, then run

```
swapon -a
```

You may also want to restart your computer.

---

### Post by AlexsAntidote on 2009-08-20
> **Windows Nerd said:**
> In other news...I also cannot get any video when I watch youtube videos (I have not tried to view any videos on other sites yet). I think this has something to do with flash or whatnot, though I can hear the audio perfectly fine.

Scott

PS: I found a great quote and have added it to my signature. See below :)

Hm... My dad had a similar problem when he first installed Ubuntu... I helped him fix it over the phone while I was distracted with about 5 other things so I'm a little fuzzy on how exactly it went... I think it went something like this:

close your browser and open your terminal.
purge your flashplayer and plugin:
```

sudo apt-get purge flashplugin-nonfree mplayer mozilla-mplayer

```

reinstall your flashplayer and plugin
```

sudo apt-get install flashplugin-nonfree mplayer mozilla-mplayer

```

Also, if you don't already have it, install the codecs, medibuntu, and ubuntu-restricted-extras
```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install non-free-codecs ubuntu-restricted-extras

```

Let me know if that fixes it or not.

p.s. nice quote.

---

### Post by Windows Nerd on 2009-08-20
> **AlexsAntidote said:**
> Hm... My dad had a similar problem when he first installed Ubuntu... I helped him fix it over the phone while I was distracted with about 5 other things so I'm a little fuzzy on how exactly it went... I think it went something like this:

close your browser and open your terminal.
purge your flashplayer and plugin:
```

sudo apt-get purge flashplugin-nonfree mplayer mozilla-mplayer

```reinstall your flashplayer and plugin
```

sudo apt-get install flashplugin-nonfree mplayer mozilla-mplayer

```Also, if you don't already have it, install the codecs, medibuntu, and ubuntu-restricted-extras
```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

sudo apt-get install non-free-codecs ubuntu-restricted-extras

```Let me know if that fixes it or not.

p.s. nice quote.
I solved that with a simple google search. Hopefully this will get fixed in Karmic. 

Well, it looks like I have my UUID. Thanks everyone :).

---

### Post by Windows Nerd on 2009-08-20
By the way, for the code "Swapon -a" you have to run that as root:

```

scott@scott-laptop:~$ swapon -a
swapon: /dev/sda4: Operation not permitted
scott@scott-laptop:~$ sudo su
root@scott-laptop:/home/scott# swapon -a
root@scott-laptop:/home/scott# 

```

Scott

---

### Post by oldrocker99 on 2009-08-20
Interesting. I am running Intrepid on a Toshiba L305D-S5895, and suspend and hibernate work perfectly on it.

:guitar:

---

### Post by Windows Nerd on 2009-08-20
Okay, last post for about 10 hours:

I have enabled swap and it is active and shows up and all that, but my problem remains...

I still cannot "wake" my computer after it hibernates/suspends. I saw an alternative solution on page two, going to check that out later.

Scott

---

### Post by Windows Nerd on 2009-08-20
> **AlexsAntidote said:**
> I have been using Ubuntu since 7.04 on my Acer Notebook and for a long time could not get the suspend/hibernate to work. I tried everything... 

However, I found a fix (at least for my problem) inadvertently while trying to fix the freeze bug with 9.04 and now suspend and hibernate work flawlessly for me.

Here's what I did:

Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do ```
sudo apt-get update && sudo apt-get upgrade
``` (this is especially important if you have a Nvidia video card).

Download and install the latest Kernel from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/") (if you have a 64 bit processor and installation, make sure you choose 64 bit, otherwise get the 386)

Restart and boot with the new kernel. Enjoy!

As making a swap partition did not help, I though this might. So far everything in the instructions have been completed without a hitch, but I do not know which .Deb package to download. I think it is either:

[linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")

OR

[linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")


I assumed it was these two because you said "Get the 386, unless you have 64 bit, which in that case, get the 64".

Which one do I get: the headers, image or both?

Note: There is also another entry that looks like this:

[linux-source-2.6.30_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-source-2.6.30_2.6.30-020630_all.deb")

Scott

---

### Post by Windows Nerd on 2009-08-21
Just something I just realized: would Update manager already have installed the latest versions of the Kernel?

Edit: After an extensive Google search, I found that most all the time, if suspend/hibernate do not work out of the box, chances are it never will. Looks like my laptop will now be chained to my desk unless I am running Windows, as I cannot enter power saving modes if I am, say at school or at a friends and forgot to bring my charger.

---

### Post by AlexsAntidote on 2009-08-21
> **Windows Nerd said:**
> As making a swap partition did not help, I though this might. So far everything in the instructions have been completed without a hitch, but I do not know which .Deb package to download. I think it is either:

[linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")

OR

[linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")


I assumed it was these two because you said "Get the 386, unless you have 64 bit, which in that case, get the 64".

Which one do I get: the headers, image or both?

Note: There is also another entry that looks like this:

[linux-source-2.6.30_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-source-2.6.30_2.6.30-020630_all.deb")

Scott

Sorry about that Scott... I should have been more specific before...

You need the headers, the image, and the all (headers)

[linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")
[linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
[linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")

```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb

sudo dpkg -i linux-headers-2.6.30-*.deb linux-image-2.6.30-*.deb

```

---

### Post by AlexsAntidote on 2009-08-21
> **Windows Nerd said:**
> Just something I just realized: would Update manager already have installed the latest versions of the Kernel?

Edit: After an extensive Google search, I found that most all the time, if suspend/hibernate do not work out of the box, chances are it never will. Looks like my laptop will now be chained to my desk unless I am running Windows, as I cannot enter power saving modes if I am, say at school or at a friends and forgot to bring my charger.

No, Update Manager would not already have installed that version of the Kernel. The 2.6.30 branch is going to be used for Karmic, but is not offered by default to Jaunty. You need to download and install it manually.

Also, in regards to your Edit... I refuse to accept that! You are doing very well with Linux already, why give up so easily?

If I had simply accepted that "advice" then I never would have been able to get the suspend/hibernate working on my laptop, but it's working now! So I just proved that "advice" wrong!

---

### Post by Windows Nerd on 2009-08-22
Okay, so I found something called TuxOnIce, previously known as Suspend 2. I installed it and all, rebooted, then tried to hibernate/suspend. It now "wakes" successfully after suspending. The only thing is that hibernate now has the same effect as suspend. As well, I can no longer see the battery Icon on the right side of my upper panel. But other than that, I can enter a power saving mode!.

Scott

PS: I added the PPT to the Software Sources, and getting the keyring thingy, and then installed it by running sudo apt-get update, and sudo apt-get upgrade. Did I do this correctly? This is my first time installing something using command line, having used .deb packages before. I am not even sure it installed successfuly/correctly: it does not show up in my installed list of software in add/remove.

---

### Post by 2FishInATank on 2009-08-22
Just a quick +1 to AlexsAntidote's solution of removing flashplugin-nonfree then reinstalling.

Symptoms - Dell Precision M4400 laptop running Jaunty x64, suspend and hibernation working fine until it automatically updated to kernel 2.6.28-15 recently. After this it would not wake up from suspend (didn't test hibernation) requiring hard reboot.

Solution - close browser then:
```
sudo apt-get purge flashplugin-nonfree
```

Tested suspend/resume - worked fine!

Then reinstalled flashplugin-nonfree:
```
sudo apt-get install flashplugin-nonfree
```

Tested suspend/resume - still working, hurrah!

Thanks AlexsAntidote - I'm a happy camper once more! :guitar:

---

### Post by AlexsAntidote on 2009-08-22
> **Windows Nerd said:**
> Okay, so I found something called TuxOnIce, previously known as Suspend 2. I installed it and all, rebooted, then tried to hibernate/suspend. It now "wakes" successfully after suspending. The only thing is that hibernate now has the same effect as suspend. As well, I can no longer see the battery Icon on the right side of my upper panel. But other than that, I can enter a power saving mode!.

Scott

PS: I added the PPT to the Software Sources, and getting the keyring thingy, and then installed it by running sudo apt-get update, and sudo apt-get upgrade. Did I do this correctly? This is my first time installing something using command line, having used .deb packages before. I am not even sure it installed successfuly/correctly: it does not show up in my installed list of software in add/remove.

I cannot vouch for TuxOnIce (Suspend 2) as I have never used it. Sorry. At least it seems to be working for you to some extent.

In regards to the keyring and etc. It sounds like you installed everything properly... But without seeing the output I am not sure.

If you are referring to the medibuntu keyring, you can see if you have it properly installed by doing the following in your terminal:
```
dpkg -l | grep medibuntu-keyring
```
If it is installed you will see it listed. The output should look something like this:
```

ii  medibuntu-keyring                          2008.04.20                                                 GnuPG key of the Medibuntu repository

```

If you are referring to the Ubuntu-X updates which I previously mentioned, you should be able to add the source to your repository sources (either by System->Administration->Software Sources, or by editing your /etc/apt/sources.list and adding it in manually -- be sure to create a backup copy first if you are not sure what you are doing).

Once the sources are added, you simply run the following in your terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

If you have any drivers or packages that are newer in the X-Updates then it will update them after the above commands. If not, nothing will change as you are not installing anything new on that, just updating to the latest drivers.

Once done with that you should install the new Kernel (as I mentioned before). You need all 3 of the deb packages I mentioned before and can install them from the command line (as I mentioned before).

Hopefully that will work.

---

### Post by AlexsAntidote on 2009-08-22
> **2FishInATank said:**
> Just a quick +1 to AlexsAntidote's solution of removing flashplugin-nonfree then reinstalling

...

Thanks AlexsAntidote - I'm a happy camper once more! :guitar:

That's awesome! I'm really glad it worked for you and you are very welcome 2FishInATank!

---

### Post by Windows Nerd on 2009-08-24
Ok, it was not Suspend2/TuxOnIce that helped me solve the problem (I removed it). Upgrading to the newest kernel (which is going to be used in Karmic apparently) and installing the Xorg Drivers Helped.

Do the following:

Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat...ive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do      

```

     sudo apt-get update && sudo apt-get upgrade 

```

Then do:

     Code:
     wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")

sudo dpkg -i linux-headers-2.6.30-*.deb linux-image-2.6.30-*.deb

---

### Post by AlexsAntidote on 2009-08-27
> **Windows Nerd said:**
> Ok, it was not Suspend2/TuxOnIce that helped me solve the problem (I removed it). Upgrading to the newest kernel (which is going to be used in Karmic apparently) and installing the Xorg Drivers Helped.

Do the following:

Add X-Updates to your repository list (found here: [https://launchpad.net/~ubuntu-x-swat...ive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") (don't forget to add the key), and then do      

```

     sudo apt-get update && sudo apt-get upgrade 

```

Then do:

     Code:
     wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")
wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")

sudo dpkg -i linux-headers-2.6.30-*.deb linux-image-2.6.30-*.deb

Exactly as I said previously! ;) I'm really glad it worked for you, hopefully it will help for others as well!

(ok well not *exactly* as I said, since you summed it up a little clearer into one post instead of a couple haha - great job!)

---

