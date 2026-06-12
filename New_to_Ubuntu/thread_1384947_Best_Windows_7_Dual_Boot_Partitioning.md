---
title: "Best Windows 7 Dual Boot Partitioning"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Cody Larson on 2010-01-19
I want to run a dual boot system with Windows 7 and Ubuntu. This is my first time giving Linux a try. I figure if I am going to do this, I want to do it right, down to the last detail. First things first what is the best way to setup the partitions?

I have read all sorts of stuff ranging from setting up all sorts of different partitions to how such systems are antiquated. My original thinking was to just keep everything separated if possible, but Windows 7 creates two partitions at installation leaving only two primary partitions as far as I know. I believe that Ubuntu creates numerous partitions including the GRUB for dual booting. I've been reading up on logical vs. primary and so on and am at a loss as to how to set all of this up.

I lost all of my files when my OS got corrupted, so I would like to have the operating systems separate from my data in case of corruption etc. In a perfect world I would have my operating systems on two separate partitions and all of my personal files on the third which can easily be accessed and manipulated by both operating systems (I think it has to be FAT32 for this, correct?). Is this possible? Is this the best way to set this up? Or is this method truly antiquated and simply putting the operating systems into the same partition is better?

Thank you in advance for your help. I really enjoy using open source for web development and my phone (Joomla, Android) and can't wait to run my computer with Linux! Unfortunately, I am not savvy in the areas of partitioning and dual booting.

---

### Post by baddog144 on 2010-01-19
I'm no real expert on partitioning, but I will say that Linux and Windows can both access NTFS, so your data partition is probably best formatted as NTFS. FAT32 is getting old and is not quite as desirable as NTFS ;)

---

### Post by lucas1136 on 2010-01-19
i am not a linux genius but i can help you a bit

if you want to duel boot with windows and ubuntu only one can work with wireless internet. you can not have bothe working with wireless because once you install the wireless driver for ubuntu windows can not read and when its got windows working ubuntu can not work but it will work for wired connections for both or wired for ubuntu and wireless with windows. but if you sill want to do it this is how you duel them. if you get the ubuntu cd and put it (computer turned off) and then turn on the computer while the cd is in there it will ask you to try ubuntu without and change to your computer click enter
then u wait a while unitl it loads with ubuntu now you can look at ubuntu and explore to see if you really want to duel boot(if you decide not to then just take the disk out and turn of the computer and start again normally) but if you do want duel boot them click install on the desktop go through everything normaly untill you get to 'partitioner) there you can choose the option 'put them side by side choosing between at startup' click that option and go next go through the rest and it should work

hope i helped 
ps sorry for the long reply
pps you should make linux the only operating system its better then windows:)

---

### Post by J V on 2010-01-19
Well, in general, you put the partitions you want to be speedy (swap/linux in general) at the front of the HD (closer to the heads)

An extended partition is just a primary that can carry logicals, there is no downside to logicals, windows just uses primary to squeeze you out of options.

Generally what you want is:
Extended[INDENT]Swap (2 gigs or so)
10 Gig ext4 mounted at /
30 Gig ext4 mounted at /home
(Some people have a seperate /usr too but I don't see how this can work well for fresh installs)
rest in an ext4 partition unmounted (data partition etc)
[/INDENT]Windows stuff

Put the windows stuff first if you want it to be fast, linux if you want it to be... You will get tired of windows fairly quick so I suggest putting linux first :P

Also, if you *really* really want to, you can make symlinks, "shortcuts" to windows folders in your home folder, so when you save to ~/Pictures its actually saving on the windows partition at "\User\<urname>\My Pictures"

This will let you access it from both OSs (linux can read/write windows partitions, but windows can't do that on linux)

---

### Post by sliketymo on 2010-01-19
[http://ubuntuforums.org/showthread.php?t=1035999&highlight=Dual-boot+Win+7%2FUbuntu](http://ubuntuforums.org/showthread.php?t=1035999&highlight=Dual-boot+Win+7%2FUbuntu)

---

### Post by J V on 2010-01-19
Do NOT look at the above post, installing windows second is always a bad idea, and besides, you are installing linux second...

---

### Post by arochester on 2010-01-19
You might look at "Dual-Boot Windows 7 and Ubuntu in Perfect Harmony" on [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by rlogan on 2010-01-19
My preferred method for a dual boot Windows/Ubuntu machine is to have the following partition layout

1) Windows c: (used for OS/programs)
2) Windows d: (used for data (I rarely do this))
3) Ubuntu / (root partition - basically OS/programs)
4) Ubuntu /home (home partition - storage of personal data)
5) Linux Swap partition

The drawback with 5 partitions is that you have to use extended partitions so better to keep to 4 if you can.

Now as to what you do is completely up to you. In my case I tend to keep the Windows area to a minimum as Windows is rarely used in this house. 

Depending on the size of the drive is what I do. One machine here which is an older laptop has a 80Gb drive, which is split about 25Gb to Windows, 2Gb Swap file for Ubuntu, 10Gb Root partition for Ubuntu and the rest being the /home partition for Ubuntu.

Another machine here has a 500Gb drive and Windows has the luxury of about 35Gb and the rest split as before for Ubuntu.

Normally I make the swap file about the same as the RAM, maybe overkill but with big drives whats 2-4Gb anyway.

If you have any questions, please ask

Cheers 

Richard

---

### Post by oldfred on 2010-01-19
I pretty much agree with rlogan.

It depends on how much you will keep using windows and over time as you convert more  and more to Ubuntu your needs will change. But by then you will have a new hard drive or new system, so it may not matter.

I set my system up with windows on one drive and ubuntu on another 3 years ago. I did add a separate partition for windows data that I wanted to share particularly firefox and thunderbird profiles, so the data was the same in both systems. then we were about 50/50 win/ubuntu and I was trying to convert to ubuntu. We now are about 90% ubuntu on my desktop and 100% on my laptop. For 3 years I upgraded in place and had many issues on each upgrade. This time I decided to do a clean install, so I moved /home to a new partition and created another /data partition for Ubuntu data only. I still have a windows data partition but converted from FAT to NTFS as it allows files over 4GB and is a journalized system for better file recovery after an error. Clean install is a much better way to go as I have had no problems on my systems.

---

### Post by tad1073 on 2010-01-19
Here is my partition table sda6 is /, sda7 is /usr, sda8 is /home and sda 9 is /var. A hdd can only have up to 4 primary partitions so this is solved by using extended partitions, which can contain more than 4.

When installing ubuntu you want to use manual set up for partitions. I suggest 512 for a boot partition, 1.5* total amount of ram for swap, 12 gb for / and 6 gb for /home which would be a total of 20 gb. As far as the extended partiton, ubuntu will automagically create it.

There is a tool called NTFS configuration tool that will automatically mount ntfs partitons with read write access.

```
$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73908785

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15310   122976551    7  HPFS/NTFS
/dev/sda2           25755       77825   418260307+   7  HPFS/NTFS
/dev/sda3           15311       25754    83891430    5  Extended
/dev/sda5           15311       15372      497983+  82  Linux swap / Solaris
/dev/sda6           15373       17239    14996646   83  Linux
/dev/sda7           17240       21596    34997571   83  Linux
/dev/sda8           21597       24459    22997016   83  Linux
/dev/sda9           24460       25754    10402056   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8168 MB, 8168931328 bytes
255 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003cda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         993     7976241    b  W95 FAT32

```

---

### Post by OrangeCrate on 2010-01-19
> **Cody Larson said:**
> I want to run a dual boot system with Windows 7 and Ubuntu. This is my first time giving Linux a try. I figure if I am going to do this, I want to do it right, down to the last detail. First things first what is the best way to setup the partitions?...

<snip>



Doing it right **is** critically important. Here's a good set of instructions to follow:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by adam814 on 2010-01-19
> **lucas1136 said:**
> i am not a linux genius but i can help you a bit

if you want to duel boot with windows and ubuntu only one can work with wireless internet. you can not have bothe working with wireless because once you install the wireless driver for ubuntu windows can not read and when its got windows working ubuntu can not work but it will work for wired connections for both or wired for ubuntu and wireless with windows. but if you sill want to do it this is how you duel them. if you get the ubuntu cd and put it (computer turned off) and then turn on the computer while the cd is in there it will ask you to try ubuntu without and change to your computer click enter
then u wait a while unitl it loads with ubuntu now you can look at ubuntu and explore to see if you really want to duel boot(if you decide not to then just take the disk out and turn of the computer and start again normally) but if you do want duel boot them click install on the desktop go through everything normaly untill you get to 'partitioner) there you can choose the option 'put them side by side choosing between at startup' click that option and go next go through the rest and it should work

hope i helped 
ps sorry for the long reply
pps you should make linux the only operating system its better then windows:)

I dual-boot 9.10 and Vista x64 and my wireless works fine in both.

I definitely wouldn't recommend installing Windows second.  While you can do so carefully and avoid overwriting your Ubuntu partition in the same way you can do so with the Ubuntu installer even in the best case you'll have to re-install GRUB (since the Windows bootloader overwrites it), which isn't something I'd wish on someone trying out Linux for the first time.

Here's what I'd recommend (besides your Windows partition obviously):
1) "/" partition - minimum size 4G, if you have space I'd recommend around 10G
2) swap partition - same size as physical RAM (some people suggest 2x, I haven't found it necessary.
3) "/home" partition - whatever size you want to give it.  Mine is about 60G as I use it for media.

I separate the /home partition so that I have the option of doing a clean install with new versions of Ubuntu without losing my media files and settings.  If you just use a single partition for Ubuntu you'd have to format it to do a clean install.  Partitions besides / don't have to be formatted during installs.

It doesn't matter if any or all of those are logical vs. physical partitions.  With those 4 you *could* do all 4 as primary partitions, but I prefer to do all my Linux partitions in one logical partition and leave the rest for other systems.

---

### Post by donaldt on 2010-01-19
Ubuntu and windows can each have a wireless connection.  I have XP and Ubuntu 9.10 both operating on the same hard drive.  each one has it's own automatic connection to wireless.

---

### Post by Cody Larson on 2010-01-19
I am following the Perfect Harmony article linked to on an earlier post. What is the Round to cylinders option all about?

---

### Post by adam814 on 2010-01-19
It's whether or not to adjust the partitions so that they start and end on physical cylinder boundaries on the hard disk.  I don't think Linux naively assumes that to be the case, but some other operating systems might.

---

### Post by Miljet on 2010-01-19
As you have seen, if you ask 10 different people about the perfect partitioning scheme, you will get 10 different answers. The right answer is: whatever works for you.

I haven't seen it mentioned so I will through this in for consideration. Since Ubuntu releases new versions so rapidly, I make two partitions for Ubuntu. Every time a new version is released, I install it on a different partition. That way if the new version doesn't work out for some reason, I can always fall back to the previous version. Once the new version is up and running and I am comfortable with it, I can delete the old version and save the space for the next version.

---

### Post by PenguinInside on 2010-01-20
The thing with partitioning is to have a basic understanding of the issues, then you can make your own decision.

As far as many different partitions for a single OS installation (/tmp, /var, /opt, etc.) you don't need that for a home installation. That's oriented toward servers that have large numbers of users who could potentially sabotage the system by overfilling it.

You'll get 80% of the benefits of different partitions simply by having a separate home partition. Another option is to keep /home on the Ubunut partition, but to keep your large multimedia files on a common data partition also accessible from Windows.

FAT32 is one option for a common partition, NTFS is another.

Some issues: Large FAT32 partitions can't be formatted from Windows, but they can from Linux. NTFS can be read and written to by Linux, but if your NTFS is in an inconsistent state (i.e., you didn't have a clean shutdown), Linux won't write to it. It wouldn't be bad to do a chkdsk from Windows once in a while.

I have 20GB for Ubuntu, and a couple more 20GB partitions so I can play with a new release before making it my main OS. Since I have a separate home partition, it's not a big deal to switch OSs.

Post your understanding of the issues, and people will help you further.

---

### Post by Cody Larson on 2010-01-20
Thank you for all the help everyone!

I have a problem, however. I followed the article [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) step-by-step for the most part and installed Ubuntu after Windows. However, GRUB does not come up when I boot. It just goes to Windows. What do I do?

---

### Post by adam814 on 2010-01-20
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by Cody Larson on 2010-01-20
Thank you for that article. I have followed Method 1 and got GRUB to load now. However I cannot choose my OS. It just simply says:

```
GNU GRUB version 1.97~beta4

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ]

sh:grub>
```

What now?

---

### Post by meierfra. on 2010-01-20
Type this at the "sh: grub> "  prompt:

```
search -f --set /vmlinuz

probe  -u --set=UUID $root

linux /vmlinuz root=UUID=$UUID ro

initrd /initrd.img

boot


```

This should boot you into Ubuntu.
Open a terminal in Ubuntu and run

```
sudo update-grub
```

Hopefully that will be all to fix your problem.

But if this does not work, boot from the Ubuntu Live CD and follow these instruction to run the boot info script and post the RESULTS.txt: [http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Cody Larson on 2010-01-23
That did it. Thank you for all of your help. The Linux and Ubuntu community is absolutely amazing. I can't wait to dive in.

---

