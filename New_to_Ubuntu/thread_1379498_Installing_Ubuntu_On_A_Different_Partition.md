---
title: "Installing Ubuntu On A Different Partition?"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Dreakon on 2010-01-12
Hello, I've been using Windows for a while now.  When I got my laptop, it bugged me that the hard drive was split half and half into 2 partitions because then I couldn't organize things as I wanted to.  So I decided to fix that and make it one large harddrive again (250GB) using something called GParted Live.

Anyways, that's all history.  I'm interested now in making one smaller logical partition (say 10-20gb?) for Ubuntu to sit on, then have it load that instead of the Windows installation on the other partition.  This way I get to keep all of my files and if I choose to go back to windows, I can use this partition again for that and keep my personal files and media seperate from the operating system.

My questions?
a) Is this an accurate way to do this, or did I somehow make this up in my head?

b) How much space should I allocate to this new partition that ideally will only be left for Ubuntu?  I don't plan on putting anything but the system files on there... if possible.  I'm not sure how much space the system takes up though for the average Linux user and have a nice buffer.  5gb, 10gb, 20gb?

---

### Post by Puck7 on 2010-01-12
Yes, you are right, this is called dual-booting, and ubuntu (grub) will handle which partition to boot.

Eventually you will need 3 partitions.

1.swap - usually the amount of your ram, or max 1 GB
2.your current windows partition
3.ubuntu partition

The space of the ubuntu partition depends on what you wish to use it, but I'd say you won't really exceed 20 GB's. I use 19.1GB on a machine that was installed back in May and I have 6 GB of moves + music.

---

### Post by warfacegod on 2010-01-12
.01 You should be okay with the resize as long as you do it in Windows

.02 10 or 15 GB ought to be plenty

You will need to give yourself NTFS write ability after your install so that ubuntu can use your files in Windows.

Search NTFS in Synaptic and install the NTFS-progs or something like that.

We're always here to help if you need it.

---

### Post by adam814 on 2010-01-12
You just want to make a 10-20 GB partition to install Ubuntu in?  You can do that with GParted (it's on the Ubuntu LiveCD).

You could probably get away with 5GB on a default install.  10GB would give you a little more flexibility though.  I use Ubuntu as a primary OS and on a 320GB disk I have a 20GB / partition and 60GB for /home with a small swap partition as well.

---

### Post by Dreakon on 2010-01-12
I don't intend to keep anything but the Ubuntu files on the smaller partition.  All movies, music, anime, tv shows, games, applications and software in general will, ideally, be on the larger partition.

I have a 250gb hard drive.
- 240gb Partition for media and software.
- 10gb Partition for Ubuntu system files and whatever else it needs.

Does this seem plausible?  Can I install software and games in Linux on a partition seperate from the system files?  Would I be better off with 15gb for Ubuntu?

EDIT: What is a swap partition?  I never needed one for Windows lol.  That I know of...

---

### Post by Puck7 on 2010-01-12
It's always better to give more, so in this case 15GB would be fine.

Ubuntu/Linux is made by the /root part, which is for the system files, and the /home/ folder which is for the personal settings of the users on the system. Usually /home/ and /root are on the same partition. Your games would be installed in /root and the configuration files would be in /home/.

So installing games to another partition won't really work, unless they are games that don't need to be 'installed', just downloaded and ran, like [Urban Terror]("http://urbanterror.net").

[This]("https://help.ubuntu.com/community/SwapFaq") can explain swap pretty well.

---

### Post by warfacegod on 2010-01-12
> **adam814 said:**
> You just want to make a 10-20 GB partition to install Ubuntu in?  You can do that with GParted (it's on the Ubuntu LiveCD).

You could probably get away with 5GB on a default install.  10GB would give you a little more flexibility though.  I use Ubuntu as a primary OS and on a 320GB disk I have a 20GB / partition and 60GB for /home with a small swap partition as well.

Windows has been known to get really cranky (read broken) about being resized by apps that aren't its own.

My 9.10 install is currently taking up around 4 GB including swap. 10 GB should work fine.

---

### Post by adam814 on 2010-01-12
That's plausible enough.  For me a separate "/home" partition makes sense in a desktop/laptop setup, but not splitting it up further.  Although some people like having a separate "/usr" and "/var" as well.

Given those 10GB (and assuming you didn't have more than 2GB of RAM) I'd split it up 4GB for "/", 4GB for "/home" and 2GB for swap.  Assuming 4GB of RAM I'd go for the 15 and split it 5/6/4.

Windows uses something called a page file, which works the same way as a Linux swap partition.  In fact, some linux distros use a swap file instead of a separate partition too, but Ubuntu doesn't without a lot of tweaking.

---

### Post by adam814 on 2010-01-12
> **warfacegod said:**
> Windows has been known to get really cranky (read broken) about being resized by apps that aren't its own.

My 9.10 install is currently taking up around 4 GB including swap. 10 GB should work fine.

I guess I lucked out then when I did so.  It griped about it on the next boot (ran chkdsk), but settled down after that.

It helps to defrag from Windows first.

---

### Post by Dreakon on 2010-01-12
> **warfacegod said:**
> Windows has been known to get really cranky (read broken) about being resized by apps that aren't its own.

My 9.10 install is currently taking up around 4 GB including swap. 10 GB should work fine.
What application do you suggest I use?  I used GParted Live several times in the process of getting my hard drive set up with Windows, and a couple of times on the partition that Windows was installed on, and haven't run into any trouble.  I want to do this right though and keep Windows intact until I know I can access everything on a successful Ubuntu installation.

> **Puck7 said:**
> [This]("https://help.ubuntu.com/community/SwapFaq") can explain swap pretty well.
So should I create the swap partition in GParted Live before I install Ubuntu, or set up the swap afterwards?

---

### Post by Puck7 on 2010-01-12
You can create the swap when you wish, but it can be done during the partitioning on the Ubuntu installer. Before you do this, please make sure you've backed up your data, just in case, you know, no need to loose data.

---

### Post by Dreakon on 2010-01-12
Should I do the partition creating and resizing of the old (large) partition in the Ubuntu installer, or should I use my seperate GParted Live CD?

---

### Post by warfacegod on 2010-01-12
XP mostly does okay with it Vista does not. It has something to do with were Vista puts some files (maybe the MBR, don't remember) and them getting over written in the resize operation. It's hit or miss. Sometimes your ok sometimes not. I've been pretty lucky myself. I don't know how 7 will react to being resized.

---

### Post by adam814 on 2010-01-12
I think warfacegod is suggesting using the "Shrink Volume" option in the Computer Management Console in Windows Vista/7.  I don't think there's an exact equivalent in XP (Maybe Partition Magic does it?)

It shouldn't matter whether you create the swap partition before the install or during the install.  After installing it might be a pain to do though.

---

### Post by Dreakon on 2010-01-12
But will I have the option to use the free space on this partition (the current partition takes up the entire hard drive) to create a new partition specifically for Ubuntu in the installer?  Keeping the rest of the data on the larger partition intact?

Or would it be better to make the partition using the GParted Live CD, then replace the CD with the Ubuntu installer and install Ubuntu on the new partition?

---

### Post by warfacegod on 2010-01-12
> **adam814 said:**
> I think warfacegod is suggesting using the "Shrink Volume" option in the Computer Management Console in Windows Vista/7.  I don't think there's an exact equivalent in XP (Maybe Partition Magic does it?)

It shouldn't matter whether you create the swap partition before the install or during the install.  After installing it might be a pain to do though.

Yeah, that would be it. You *PROBABLY* won't need to bother if it's XP, just use Gparted during the install. If it's Vista well, there's this game called Russian Roulette.

---

### Post by Dreakon on 2010-01-12
> **warfacegod said:**
> Yeah, that would be it. You *PROBABLY* won't need to bother if it's XP, just use Gparted during the install. If it's Vista well, there's this game called Russian Roulette.
Well, honestly, the goal is to delete any remnant of Windows off of the larger partition if I find Ubuntu satisfying enough. :)

Then, also, I could reinstall Windows on the new partition and leave my files uneffected if Ubuntu fails me enough to warrant going back.

---

### Post by pathfindermwd on 2010-01-12
[QUOTE=warfacegod;8654421]Windows has been known to get really cranky (read broken) about being resized by apps that aren't its own.

Having just gone through this I would very strongly agree!!! 

Not to scare you, but be careful, it can get ugly.  Try to do it from a windows application, specific to your windows O.S.  And have another maching handy for internet help if possible, or someone who knows what they're doing.

---

### Post by Dreakon on 2010-01-12
Well, I'm on Ubuntu as I speak.  I loaded up Windows and it worked okay, just needed to run a CHKDSK.

My final question on the matter, when I boot up the PC, I get a menu with 2 Ubuntu options, 2 memtest options and my Windows partition (to load it).  If I were to say... delete everything Windows related off of that partition... would it be possible to have it just load Ubuntu by default?  And not have that menu come up at all?

Thanks for all the help guys!

---

### Post by warfacegod on 2010-01-12
Since you are relatively knew to linux, I recommend not messing with the grub menu just yet. It's a minor inconvenience, I know, but modifying grub can have some bad consequences if not done properly.

---

### Post by Dreakon on 2010-01-12
Can I at least remove the "Windows" partition from the list somehow?  If I can get Ubuntu running well enough, I intend to remove everything Windows related on the larger partition.

---

### Post by warfacegod on 2010-01-12
Type ```
sudo update-grub
``` in a terminal, that might at least move ubuntu to the top of the list. If you remove Windows do that after and it will remove it.

---

### Post by Dreakon on 2010-01-14
Alright, I have another question.

If I were to go into GParted Live seperately from the Ubuntu installer and create a 15 gb partition (of the 250gb hard drive), then install Ubuntu cleanly onto that partition... would my computer load Ubuntu first, or my copy of Windows sitting on the larger 250gb partition?

If possible, I want to create the 15gb partition and have Ubuntu load, then delete everything Windows related off of the larger partition.  This would hopefully keep that menu (the grub I guess its called) from coming up when I turn on my laptop, of what I want to load since I'm not trying to dual boot.  Or will the grub menu come up no matter how many O/S's I have on my hard drive?  The goal is to get rid of the grub menu and just load the default Ubuntu every time.

How much logic is there to this? lol  Or am I talking out my behind?

---

### Post by adam814 on 2010-01-14
Which one loads by default at boot depends on your GRUB config, not which one is on the larger partition.

I'd imagine GRUB would show a menu even with only one OS installed since it would still have the recovery and memtest options too.  GRUB legacy had a "hiddenmenu" option.  I'm not 100% sure how to set that up in GRUB2.

You could set the timeout in /etc/default/grub to a lower value so the menu isn't open as long.  I wouldn't set it to 0 in case a kernel upgrade doesn't work out for you and you need to get to your old one.

---

### Post by warfacegod on 2010-01-14
Try this:

[http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu]("http://ubuntuguide.net/manually-addingremoving-entries-to-grub-2-menu")

---

