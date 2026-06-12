---
title: "Restore GRUB after Windows 7 installation"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by dyecide on 2009-10-07
Hey,

I would like to recover my old GRUB menu after installing Windows 7. I had Windows 7 and Ubuntu 9.04 options, but after reinstalling Windows, it has disappeared.

I've spent the past hour with googling, and found a lot of info about how to restore GRUB after a Windows reinstall, but due to my Linux knowledge (been using Ubuntu 9.04 for 9 days) I'm not sure what to do, and I would like to ask for help here.

I have 4 partitions, Ubuntu is on thw 4th (hd0,3), Windows 7 is on the primary one (hd0,0 = C: ). I installed Ubuntu after Windows, and everything was fine, but today Windows crashed and I had to reinstall it, and it has deleted GRUB.

I tried EasyBCD, created a NeoGRUB bootloader, it said the menu file is on C:\NST\menu.lst . I have my menu.lst backed up, I overwrote it with the old one, but it doesn't work. After selecting NeoGRUB from the boot menu, I see my old boot menu, but Linux doesn't boot. Tried adding Linux aswell with both options ('GRUB isn't installed on the bootsector' ticked and unticked), but it just doesn't work. The sites say it's really simple and all, but I just can't get it working and it's starting to piss me off, since I'm not a noob otherwise, I just dno Linux (yet).
 
I would really appreciate any help, thank you.

---

### Post by oldfred on 2009-10-07
restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your ubuntu is  (hd0,3)  then this should do it from a liveCD:

In terminal
  sudo grub
  root (hd0,3)    <-- this must point to location of 'stage1', else see nb:
  setup (hd0)     <-- installs grub IPL to MBR of first hard drive. 
  quit
  Reboot

nb: if location of 'stage1' is unknown,
  find grub/stage1
or
  find /boot/grub/stage1
is needed, after step #1

---

### Post by dyecide on 2009-10-07
Thank you, though I already reinstalled Ubuntu :\

I tried this before: booted from the Live CD, opened a terminal, logged in as root, then:

sudo grub
find grub/stage1 - it said (hd0,3)
  root (hd0,3)
  setup (hd0,3)
  quit

And it didn't work. I guess what you said would have worked (setup (hd0)). It means I have to install GRUB to Windows's MBR?

---

### Post by lindsay7 on 2009-10-07
post the output of 

sudo fdisk -l  (that is the lower case letter L)

This will verify what partitions are are your computer and we can go from there.

---

### Post by oldfred on 2009-10-07
The computer start process loads the MBR from the first disk in BIOS. You have to have Grub in the MBR for the compter to boot and find grub and the menu.lst that lets you choose what to boot from.

Your installed grub to the third partition, If it is Ubuntu it would allow you to chainboot from another Grub install.

You installed to the third partition
setup (hd0,3)
you should have installed to the MBR of the first drive.
setup (hd0)

---

### Post by dyecide on 2009-10-08
Thanks, next time I will use (hd0).

Btw, the output of 'sudo fdisk -l' is:

/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        9561    51199155    5  Extended
/dev/sda3            9562       35966   212094032    7  HPFS/NTFS
/dev/sda4           35967       38913    23671777+  83  Linux
/dev/sda5            3188        9561    51199123+   7  HPFS/NTFS

---

### Post by richark on 2010-02-27
Just wanted to add my two cents, since I spent almost an hour fighting this problem.  In my case, there was a Win7 boot partition at (hd0,0) and when following the directions, it was never "fixing" that one.  I eventually got it to work by running:

>setup (hd0,0)

This wrote the grub config back to the little Win7 boot partition.

Hope that helps someone...

Kenny

---

### Post by nijamudeen on 2010-12-04
> **richark said:**
> Just wanted to add my two cents, since I spent almost an hour fighting this problem.  In my case, there was a Win7 boot partition at (hd0,0) and when following the directions, it was never "fixing" that one.  I eventually got it to work by running:

>setup (hd0,0)

This wrote the grub config back to the little Win7 boot partition.

Hope that helps someone...

Kenny
GRUB4DOS  0.4.4 2009-4-20,memory 639k/ 1788m Menu End 0×434CE
                                   [Minimal BASH -like line is
supported. For the first word, TAB list possible command completions.
Anywhere else TAB lists the possible completion of a
device/filename.ESC at any time exists.]
GRUB>root (hd0,1)
FileSystem type is ntfs,partition type 0×07
GRUB>setup (hd0)
Error 15 file not found
GRUB>setup (hd0,1)
Error 15 file not found


please help me immediately....................


    your's obediently

   A.Nijamudeen

---

### Post by nijamudeen on 2010-12-04
> **oldfred said:**
> restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your ubuntu is  (hd0,3)  then this should do it from a liveCD:

In terminal
  sudo grub
  root (hd0,3)    <-- this must point to location of 'stage1', else see nb:
  setup (hd0)     <-- installs grub IPL to MBR of first hard drive. 
  quit
  Reboot

nb: if location of 'stage1' is unknown,
  find grub/stage1
or
  find /boot/grub/stage1
is needed, after step #1
GRUB4DOS  0.4.4 2009-4-20,memory 639k/ 1788m Menu End 0×434CE
                                   [Minimal BASH -like line is
supported. For the first word, TAB list possible command completions.
Anywhere else TAB lists the possible completion of a
device/filename.ESC at any time exists.]
GRUB>root (hd0,1)
FileSystem type is ntfs,partition type 0×07
GRUB>setup (hd0)
Error 15 file not found
GRUB>setup (hd0,1)
Error 15 file not found


please help me immediately....................


    your's obediently

   A.Nijamudeen

---

### Post by nijamudeen on 2010-12-04
GRUB4DOS  0.4.4 2009-4-20,memory 639k/ 1788m Menu End 0×434CE
                                   [Minimal BASH -like line is
supported. For the first word, TAB list possible command completions.
Anywhere else TAB lists the possible completion of a
device/filename.ESC at any time exists.]
GRUB>root (hd0,1)
FileSystem type is ntfs,partition type 0×07
GRUB>setup (hd0)
Error 15 file not found
GRUB>setup (hd0,1)
Error 15 file not found


please help me immediately....................


    your's obediently

   A.Nijamudeen[/QUOTE]

---

### Post by wilee-nilee on 2010-12-04
> **nijamudeen said:**
> GRUB4DOS  0.4.4 2009-4-20,memory 639k/ 1788m Menu End 0×434CE
                                   [Minimal BASH -like line is
supported. For the first word, TAB list possible command completions.
Anywhere else TAB lists the possible completion of a
device/filename.ESC at any time exists.]
GRUB>root (hd0,1)
FileSystem type is ntfs,partition type 0×07
GRUB>setup (hd0)
Error 15 file not found
GRUB>setup (hd0,1)
Error 15 file not found


please help me immediately....................


    your's obediently

   A.Nijamudeen[/QUOTE]
[B]
Start your own thread and do this[/B]. 

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

PM me if your able to do all this, if you need help I wont respond to anything in this thread, after this post.

---

### Post by alihonarmand on 2011-05-19
Hi. I have got a problem in this area. I think it will make it more fun.
I installed Windows 7 and tried to recover Grub using grub-install. The system asked me something like changing the place where boot info goes and I typed "--force" and since then I have no OS starting point on my system. After hardware check there is no steps ahead of the black screen. I checked and got that I have got windows installed (all of its files are there). I don't want to format my disk. please help.

---

### Post by bdoe on 2011-05-19
Sounds like you completely nuked your MBR. Try booting off your Windows 7 Installation disc and select the option to repair your installation. This should create a new MBR and make Win7 bootable again. After that (and after you verify that you can boot into Windows again), try restoring GRUB again.

---

### Post by wildmanne39 on 2011-05-19
> **alihonarmand said:**
> Hi. I have got a problem in this area. I think it will make it more fun.
I installed Windows 7 and tried to recover Grub using grub-install. The system asked me something like changing the place where boot info goes and I typed "--force" and since then I have no OS starting point on my system. After hardware check there is no steps ahead of the black screen. I checked and got that I have got windows installed (all of its files are there). I don't want to format my disk. please help.
Hi, this link tells you how tofix your problem. [http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by surendranb on 2011-06-10
Hello everyone,

I faced the same problem as some of you might have.  Windows 7 install after Ubuntu 11.04 and Grub disappeared.  I tried reading up many of the solutions around including booting off a live cd and trying to reinstall grub - easier it may sound, I had to struggle for a few hours before coming up with the solution.

1.  Boot off a Live CD
2.  Mount the ubuntu partion to the OS.  I did this by sudo mount /dev/sda1 /mnt
3.  A series of commands as follows

sudo mount --bind /dev /mnt/dev 
sudo mount --bind /proc /mnt/proc 
sudo mount --bind /sys /mnt/sys 
sudo chroot /mnt

4. Once you have entered into the root mode grub-install /dev/sdx

sdx=your hard drive.. Mine had sda

Restart and Bingo !!!

---

