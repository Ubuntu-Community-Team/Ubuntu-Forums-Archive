---
title: "How do you actually boot Ubuntu?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by Destructor on 2009-05-23
Hi,

Please speak to me as if I was an eight-year-old child that knows NOTHING about computers. I have browsed a few of the forums in 'Absolute Beginner' and they are laden with a lot of tech talk that I don't fully understand.

I have installed Ubuntu as a dual install on my computer. My intention, if Ubuntu works out, is to remove Windows entirely (all I need to figure out is how to get the wireless working and the monitor configuration sorted and... well, that's for another thread). However before I can get onto those other issues, I have a much more basic one- I can't actually activate Ubuntu! If I turn my computer on, Windows boots. It said it would give me the option at startup to choose my OS. No such option appears. I feel foolish for even asking but... how do I actually START Ubuntu once it is installed?

Thanks.

---

### Post by QIII on 2009-05-23
When you first turn on the computer, do you see a basically dark screen with some text in the upper left-hand corner that says "Grub loading"?

---

### Post by Jjohn on 2009-05-23
Press one of your arrow keys when the computer starts i think that will show your boot options then select the one you want

---

### Post by kiridude on 2009-05-23
Tell us how you installed Ubuntu so we can see if you did something wrong.

---

### Post by Destructor on 2009-05-23
> **QIII said:**
> When you first turn on the computer, do you see a basically dark screen with some text in the upper left-hand corner that says "Grub loading"?

No, the first screen I see after activating the computer says 'HP' in big letters and then some boot options like F2 and F10 below that.

> Press one of your arrow keys when the computer starts i think that will show your boot options then select the one you want 	

I pressed down and right arrows repeatedly during the bootup process- no difference, it went directly to Windows.

			> Tell us how you installed Ubuntu so we can see if you did something wrong. 		

The first thing I did was create the install disc. This worked. I played around with Ubuntu for a while running it purely from the disc and liked it. I restarted the computer and this time selected 'Install'. It asked me a series of questions that I answered, it processed for a while and then told me it was installed. Ubuntu activated and I installed VLC and the driver for my gfx card and wireless device. It indicated I should reboot. I did, and I have been unable to boot into anything other than windows since that time.

The computer is an HP Compaq nx9105.

---

### Post by Jjohn on 2009-05-23
I had a google around and did not find any help there. I wonder if you got a set up error someplace in the install. :?

---

### Post by pspsampsp on 2009-05-23
try pressing the escape key during boot and see if that works.

---

### Post by QIII on 2009-05-23
If you are not getting the GRUB message, then you may have missed something in your install.  When dual booting, you want GRUB to handle loading so it can give you the option of going to Windows or Linux.

I have never installed Windows/Linux as a dual boot on a single physical drive -- I always use two.  Much easier.

I'm going to see if I can find a link to a tutorial.

Hang tight.

---

### Post by hayden92 on 2009-05-23
Pressing the ESCAPE key will work if you get a screen during bootup that says something like "press ESCAPE to enter GRUB"

Then you should get a list of either Windows or Ubuntu

---

### Post by kiridude on 2009-05-23
In Windows (vista), go to control panel > administative tools > computer management > storage > then disk management. Here look and tell us how your disk is partitioned (how many partitions and their names). In your installation process what did you do at the disk partitioning part? I want to see if Ubuntu is actually installed before we start looking at grub issues.

---

### Post by QIII on 2009-05-23
After you have given kiridude the info he asked for, take a look at a tutorial I'll link to at the bottom.

There is a tutorial in the Ubuntu documentation, but it looks like you really need to know a bit about Ubuntu to begin with.

Anyway, this is for an older version (8.04) but the process should be the same.  Let us know if this is how your install went.

You should get the GRUB loader first after the installation, but apparently that's not working for you.

Here's the link

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Destructor on 2009-05-23
> **kiridude said:**
> In Windows (vista), go to control panel > administative tools > computer management > storage > then disk management. Here look and tell us how your disk is partitioned (how many partitions and their names). In your installation process what did you do at the disk partitioning part? I want to see if Ubuntu is actually installed before we start looking at grub issues.

Okay. I am using XP, but I managed to find the appropriate info.

There appears to be three partitions. They are all type 'basic'.

The first is called C: and is 53.39GB NTFS. It is labelled primary partition. It is marked 'Healthy (system)'

The second is unlabelled and is 2.33GB. It is marked 'Healthy (Unknown partition)' and is colour coded as a 'logical drive'.

The third is also unlabelled and is 173MB. Also marked 'Healthy (Unknown partition)' and is colour coded as a 'logical drive'.

The latter two partitions have 100% free space. The Primary partition is 34% free.

		> After you have given kiridude the info he asked for, take a look at a tutorial I'll link to at the bottom.

I'll look into that now, thanks.

---

### Post by Destructor on 2009-05-23
> **QIII said:**
> After you have given kiridude the info he asked for, take a look at a tutorial I'll link to at the bottom.[]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

As far as I'm aware, this is the process I went through, except for the absence of the GRUB booting option when turning on the computer. Mine boots directly to Windows. Hitting Escape during the boot process takes me to BIOS but I don't see any mechanism for booting to Ubuntu.

---

### Post by Destructor on 2009-05-23
My instinct now is to delete the partitions and re-attempt the install process. I would appreciate any advice on this issue.

---

### Post by presence1960 on 2009-05-23
> **Destructor said:**
> My instinct now is to delete the partitions and re-attempt the install process. I would appreciate any advice on this issue.

Don't delete anything yet, those 2 other partitions may be your Ubuntu and swap partitions.. Boot the Ubuntu Live CD. Choose try Ubuntu without any changes to your computer (or similar). When you get to the Desktop Go Applications > Accessories > Terminal. Run this command in terminal > sudo fdisk -l BTW that ia a lowercase L. Post the output back here. This will give us the info on your partitions and then we can try restoring GRUB.

---

### Post by Destructor on 2009-05-24
> **presence1960 said:**
> Don't delete anything yet, those 2 other partitions may be your Ubuntu and swap partitions.. Boot the Ubuntu Live CD. Choose try Ubuntu without any changes to your computer (or similar). When you get to the Desktop Go Applications > Accessories > Terminal. Run this command in terminal  BTW that ia a lowercase L. Post the output back here. This will give us the info on your partitions and then we can try restoring GRUB.

Okay, I have activated Ubuntu from the disc (I am, in fact, writing to you from within Ubuntu- I can tell you that I am genuinely excited to get this working properly) and entered the terminal command. This came back:

[B]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbeb9beb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6970    55986493+   7  HPFS/NTFS
/dev/sda2            6971        7296     2618595    5  Extended
/dev/sda5            6971        7274     2441848+  83  Linux
/dev/sda6            7275        7296      176683+  82  Linux swap / Solaris[/B]

Hope that helps, thanks!

---

### Post by presence1960 on 2009-05-24
try this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

#4 should spit out (hd0,4) use that for #5. If not use what it presents to you.
At #6 I would use setup (hd0) to install GRUB to MBR

---

### Post by presence1960 on 2009-05-24
On further review it looks like your Ubuntu partition is only 2 GB and your swap is 173MB - **way too small!!** Your windows is 55GB.

I would reinstall and this time make sure you make enough space for your Ubuntu partition(s). If unsure about how to set up the partitions post back here.

---

### Post by presence1960 on 2009-05-24
Make sure you have defragged Windows at least one time prior to installing Ubuntu!

---

### Post by Destructor on 2009-05-24
[FONT=monospace]Okay I got up to step 4 in the instructions. When I typed: 'find /boot/grub/stage1' it didn't give me hd, it said:

Error 15: File not found

Anyway, reading on, it looks like my best step  is to reinstall Ubuntu but with a larger partition this time. Before I do this, I need to ask: Do I need to delete the existing partition/ubuntu install before I do this?

I will defrag the drive before I do this also. 

Thanks for the help.
[/FONT]

---

### Post by presence1960 on 2009-05-24
while in the Live CD click System > Administration > Partition Editor. Use this to delete the 2 Ubuntu partitions. Then defrag Windows and boot the Ubuntu Live Cd and use Partition Editor again to resize the Windows partition. Then when you install choose the manual option at the partitioner screen and use the free space for Ubuntu

P.S. The most important thing is to back up anything you don't want to lose. Anything can happen at any moment, especially during partitioning. Don't be one of the sorry ones who didn't back up.

---

### Post by Temposs on 2009-05-24
I think part of your instructions is a bit unclear, presence1960. I think what you mean is after he deletes the Ubuntu partitions and defrags Windows, he should resize the Windows partition **to take up the entire hard drive**. Please feel free to correct me on any of my points.

Let's see if I can enumerate presence1960's instructions better:
1) Boot LiveCD without Install
2) System > Administration > Partition Editor, delete the Ubuntu partitions(these are the two small partitions).
3) Boot Windows
4) Defrag Windows
5) Boot LiveCD without Install
6) System > Administration > Partition Editor, resize the Windows partition(your only partition left) so it takes up the entire hard drive.
7) Click the "Install" icon
8) During the partition setup of installation, select "Specify partitions manually" and choose to use free space for Ubuntu.

I think that's it. Please correct any of my points if they're off. Trying to make our friend's experience as painless as possible.

EDIT: I agree that the problem is likely that our friend Destructor didn't defrag his Windows install before installing Ubuntu, which meant Ubuntu could only acquire a small piece of hard drive real estate at the end of the hard drive, too small for Ubuntu to use.

---

### Post by presence1960 on 2009-05-24
> **Temposs said:**
> I think part of your instructions is a bit unclear, presence1960. I think what you mean is after he deletes the Ubuntu partitions and defrags Windows, he should resize the Windows partition **to take up the entire hard drive**. Please feel free to correct me on any of my points.

Let's see if I can enumerate presence1960's instructions better:
1) Boot LiveCD without Install
2) System > Administration > Partition Editor, delete the Ubuntu partitions(these are the two small partitions).
3) Boot Windows
4) Defrag Windows
5) Boot LiveCD without Install
6) System > Administration > Partition Editor, resize the Windows partition(your only partition left) so it takes up the entire hard drive.
7) Click the "Install" icon
8) During the partition setup of installation, select "Specify partitions manually" and choose to use free space for Ubuntu.

I think that's it. Please correct any of my points if they're off. Trying to make our friend's experience as painless as possible.

EDIT: I agree that the problem is likely that our friend Destructor didn't defrag his Windows install before installing Ubuntu, which meant Ubuntu could only acquire a small piece of hard drive real estate at the end of the hard drive, too small for Ubuntu to use.

If windows is resized to take up the entire hard disk then you can't use the manual option because there would be no free space since windows occupies the entire disk. If done this way the option to choose at the partitioner screen on the install will be guided resize. You can then grab the right side of the windows partition and slide it to the left to resize the windows partition and create space for the Ubuntu partition. Either way is correct. I prefer to manually set the partitions myself.

Here is a link to illustrate. scroll down to #8. [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I agree with your assessment of Destructor's problem, that is probably just what happened to his install.

---

### Post by Destructor on 2009-05-24
Thanks for all this guys, I am about to try your suggested solution. Quick question- when it comes time to partition the drive, how much space, ideally, should be provisioned for Ubuntu's partition, since it seems I left too little space for it last time I installed.

---

### Post by presence1960 on 2009-05-24
> **Destructor said:**
> Thanks for all this guys, I am about to try your suggested solution. Quick question- when it comes time to partition the drive, how much space, ideally, should be provisioned for Ubuntu's partition, since it seems I left too little space for it last time I installed.

I would give it half unless you aren't going to store a lot of files on Ubuntu. If that is the case 12-15 GB will be plenty. if you want to store files on Ubuntu go with 30GB. If you intend on eventually getting rid of windows be bold: give ubuntu 40GB, 20 GB will be plenty for XP.

**_VERY IMPORTANT-back up your data and defrag windows!!!_**

Good luck. I am going to bed. Hopefully temposs will be around if you need help. If not someone will be glad to help you.

---

### Post by Destructor on 2009-05-24
> **presence1960 said:**
> I would give it half unless you aren't going to store a lot of files on Ubuntu. If that is the case 12-15 GB will be plenty. if you want to store files on Ubuntu go with 30GB. If you intend on eventually getting rid of windows be bold: give ubuntu 40GB, 20 GB will be plenty for XP.

**_VERY IMPORTANT-back up your data and defrag windows!!!_**

Good luck. I am going to bed. Hopefully temposs will be around if you need help. If not someone will be glad to help you.

Hi folks,

I followed these instructions and I now have Ubuntu running and GRUB showing at startup. I am having some other problems but they are unrelated to this one so I'll start them in new threads- I am sure you will all be seeing a lot of me. 

Many thanks for getting me this far!

---

