---
title: "Is a dual-boot with karmic and xp using RAID and LVM possible?"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by JayRobert on 2010-01-27
After more than 10 years away from UNIX / Linux, I am in the process of setting up a new box at home.  I would really like to migrate entirely away from Windows, but I fear I may need it for work, and since I've been using XP since it came out (what, 8 years now?) I plan to stick with that rather than learning Windows 7 for the Windows stuff I may need to do.

Since I'm impatient, earlier this week I set up a dual-boot system with Karmic 9.10 (with Kubuntu desktop) and XP Professional SP3. I have a 40GB SSD with 12GB for XP and the rest for /boot, swap and /.

I read about RAID and LVM when I was in the process of building this machine, and it seemed like it would be very cool to have, so I also have 3 - 640GB Western Digital drives with each entire drive set up on RAID5, and the entire RAID array as a volume group. Over that I have a logical volume for (I thought) Windows, formatted in FAT32, and then logical volumes (acting as partitions) for /home, /opt, /tmp, /usr and /var formatted in ext3. Root on the SSD is also its own logical volume. I have encrypted the linux partitions except /boot, but not the FAT32 partitions.

Of course, I went ahead and set up a RAID5 assuming I'd be able to make Windows XP see it, but it only sees the three drives. Is there any way to make XP see the LV with the FAT32 file system on it, or do I need to start over?

Or could I load the apps I need onto the FAT32 LV using Wine?  Can I really abandon Windows entirely using Wine?  The only Windows apps I may *need* for work are Access and Excel.  The other Windows apps I *want* (don't *need*) are all games.  The gamers at work say most will run in Wine, but if I'm going to be up all night, it won't be to play World of Warcraft, it will be to build some report or db, so it has to work every time.

If I have to start over, would I be better off giving one of the 640GB drives to Windows and making the other two into a RAID1 for Karmic? (Part of the reason I want to use Ubuntu is because it makes doing RAID and LVM pretty easy.  I tried first to do it using Gentoo and some incomplete instructions from the 'net, but I ended up with a big hash all over the 3 drives. I'm still not sure what I did, exactly.)

Another thing I like about Ubuntu is that it also supports KVM. What I really want to do is only run XP as a virtual machine on top of Karmic so that XP never sees the Internet (I really hate viruses), but I'll worry about figuring that out after I figure this part out. (Is KVM the way to go?  Xen?  I'd like to use open source, if possible.)

BTW, my mobo does have a fakeRAID capability, but after reading many posts I am hesitant to use that. Also, if it helps, processor is AMD Phenom II x4, 8GB DDR3, NVIDIA graphics card.

I'm not worried about losing data (yet), as this is a fresh machine with nothing to lose but the time I've put into the current setup, so if I have to, I can start over, painful as that would be. I do want to have either a RAID1 or RAID5 mirror for the linux data, not as concerned about that with the Windows data.

Any suggestions on how I should proceed from here?  Am I way too ambitious in what I want to do as a newb?  (It's OK, I can handle the truth.)

---

### Post by Hospadar on 2010-01-27
I'm not sure about your raid situation, I've never set that up.  I can only imagine the easiest thing to do would be to have a separate non-raid drive for windows.  Also I see no need to have windows on fat32, linux has great native support for ntfs nowadays and ntfs is a much better filesystem.  I also know that for some situations you need to get the raid drivers on a floppy disk for the windows installer, or you can slipstream them in with something like nlite.

I would suggest you just use a windows VM.  The only think you really can't do in a VM is play 3d video games or do huge cad stuff.  If you needed that, I'd either use one of your drives for windows or grab a cheap 80-gig drive somewhere and use that as your windows boot.  I use virtual box for all of my windows need and have never had a problem.  Virtualbox is super easy to set up, and can be done all in the GUI.  I'd suggest you get it from sun's website, they have their own repository which has some extra features like usb support and some other things.


[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Some games work just fine under wine, typically those which are more popular, like wow, team fortress 2 (last time I checked), counterstrike, what have you.  Wine has a great database of what works, how well it works, and what sorts of weird things you may need to do to get things working.

[http://appdb.winehq.org/](http://appdb.winehq.org/)


I know there are other virtualization tools, xen, vmware, etc, which as I understand it are just fine and work great, but for the desktop user virtualbox is really the best as far as I'm concerned.  The others I gather are more targeted towards server-type applications (which is fine, and virtualbox does that too) but for a desktop user it just means more scripting and learning lots of commands for something you'll rarely use anyways.

---

### Post by JayRobert on 2010-01-27
Thanks for the response and the link.  I guess I will reinstall both this afternoon, unless someone knows of a way to make Windows change from FAT32 to NTFS within the program.  (It's a choice made during install; I've never tried to change it once set up.)  (Yes, I know I'm in an Ubuntu forum, just asking in case you know.)  I had wanted to use ntfs when setting up XP, but most of the stuff I read said there was not much support in linux for ntfs - read-only, no write - still not sure I'll need it, but since I have to choose up front, I was cautious and chose fat32.

Thanks again!  I'll check back here in a couple of hours before I start over, hoping someone might have an easier way...

---

### Post by Hospadar on 2010-01-27
I can't image a way to change partition types, I'm sure it's possible in the sense of computer forensics, or critical systems, but I can guarantee it would at least involve copying the entire disk somewhere else, reformatting, then moving all the data back.  Long story short, just reformat, it would be much easier.

As to ntfs, I've been using ntfs from linux for years (with read and write) and never had any issues.  Probably any guides that claim ntfs support is anything but great are from a time before it worked perfectly out of the box (since it doesn't make a whole lot of sense to write up a how-to for something that works great with no intervention).

---

### Post by phillw on 2010-01-27
> **JayRobert said:**
>  someone knows of a way to make Windows change from FAT32 to NTFS within the program.
Thanks again!  I'll check back here in a couple of hours before I start over, hoping someone might have an easier way...

Hi, and welcome to the forums,

The official M$ HowTo --> [http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

Be careful with Karmic and RAID, grub1.97Beta (Grub2 in Karmic) and RAID are not on the best of terms.

grub1.98 (Which we're running in 10.04 alpha - Lucid) seems to addressed a lot of the issues.

You can use 9.10 & raid / lvm  with grub-legacy in 9.10, and all Ubuntu's before 9.10

8.04.3 would be one way forward, as 8.04.4 is due out tomorrow - you may want to wait for 8.04.4 - that will be upgradeable to 10.04 at the end of April.

Another choice would be burg, the maintainer of burg has back-ported RAID / LVM support back to 9.10.

I'm not sure where his 9.10 posting is, but in response to a request I made, further details can be found here --> [http://ubuntuforums.org/showthread.php?t=1378951](http://ubuntuforums.org/showthread.php?t=1378951)

bean123 is pretty quick to reply to any questions & seems to have a good track record in sorting out any technical questions that you have concerning what you want to do.

Food for thought !!

Regards,

Phill.

---

### Post by BT1 on 2010-01-27
As its been stated, a Virtual Machine Manager (I highly suggest Virtual Box) would be your best bet for a fail safe "Must have windows!" set up if you're shooting for a fuller Linux crossover. XP won't recognize Linux LVM and SOFTRaids in my experience, making things easy for everyone isn't really a strong point when it comes to windows-to-linux support.

When it comes to RAIDS, most of my experience comes from my SOFTRaid arrays. I have multiple thumb drives that I've set up a raid array on, and on that array is my virtual box hard drives, XP being one of those virtual machines. Needless to say it runs quite fast for what I need it for. I use WINE for games but usually I am too busy for games cause I'm a full time college student. WINE supports a wide variety of games, and its forums are very helpful if you have issues.

If you're looking for Office apps, try out OpenOffice's versions of those. I use excel and OpenOffice's word program, and I even have OpenOffice installed on multiple employees computers at my job, and they have intensive excel and word needs. No complaints yet, and on the slow 512 meg ram XP machines, people say it even runs faster *shrug*. They had me install it after they were lamenting having to buy more MS Office licenses. I brought forth the "free" option, and so far I get free donuts every morning in gratitude :D.

[http://www.openoffice.org/](http://www.openoffice.org/) if you're interested

I was able to make the full transition with KernelCheck (which updates my kernel so that my sound card is FINALLY supported), openOffice, WINE, and virtualbox.

I don't know much about changing FAT32 to NTFS, but I've always just reformatted after putting my important files on a spare hard drive. I just transfer them back over after I've re-installed the system.

Here's what you can try:

1.) Download the Ubuntu-Alternate .iso, burn it to CD or use unetbootin to put it on a thumb drive (much faster install in my experience)
2.) Set up a softRaid if hardware Raid isn't available, install Ubuntu on top of that array.
3.) After installing updates, hardware drivers if you must, check out the open office that comes with the install (yes, ubuntu comes with a free office productivity option that stands toe to toe with MS office, for free!), and if that doesn't make you happy...
4.) Go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) , download the one appropriate for your processor type and install.
5.) Get your XP CD and code ready, and create a virtual machine (it makes it pretty simple) and install XP on a virtual machine. Make sure to set it up like you normally would set up a fresh XP install (meaning do update manager, etc.) You can tweak the virtual machine too if you look into the options.
6.) run XP full screen on another workspace and just CTRL+ALT+Arrow Key back and forth when you need to.

That's what I do for people who ask me to make ubuntu their base system and install windows on top of it. They recognize ubuntu is more stable and having windows installed in ubuntu further boosts the security of the windows install. 

Have fun!

---

### Post by JayRobert on 2010-01-27
Thanks for the responses!  I think I'll try the virtual box setup suggested by BT1.  I appreciate the info re: switching from FAT32 to NTFS, but I think I'm going to have to reinstall XP anyway.

Now my question is, when you (BT1)  say install XP on a virtual machine, can that virtual machine reside on the Ubuntu-created LVM created during the Ubuntu install, or does it need its own separate drive?  Ditto the Virtualbox drive: can that reside on an Ubuntu LVM, or does it need its own drive?

In other words, when I install Ubuntu, I plan to give the 40GB SSD to /boot, swap and /.  That leaves me 3 - 640 GB drives.  Should I make all of them into a RAID5 LVM, plop the other Ubuntu partitions on there, and then figure out how to add LVs for Virtualbox and XP?  Or should I make 3 - 320 GB partitions for a RAID5 LVM for Ubuntu, plus 2 - 320 GB partitions for a RAID1 LVM for Ubuntu, and leave the remaining 320GB on one drive for Virtualbox and XP to "find" later?

Or should I make a RAID1 LVM out of two of the drives, and then leave the 3rd 640GB drive for Virtualbox and XP?

(I can't tell you how nice it is to have such problems, really -- I'm remembering when a 20GB hard drive was an extravagance.)

Thanks again!

---

### Post by JayRobert on 2010-01-27
PhilW, thanks for the link re: GRUB2, burg and RAID.  Since I'm determined to set up RAID, I'll be happy to test (if that's allowed).  Of course, I haven't any idea how to file bug reports (if necessary) or anything else, but I'm willing to help if I can.

---

