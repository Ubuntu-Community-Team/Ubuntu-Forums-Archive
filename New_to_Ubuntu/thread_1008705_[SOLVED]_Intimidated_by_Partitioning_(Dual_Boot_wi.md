---
title: "[SOLVED] Intimidated by Partitioning (Dual Boot with Vista)"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by KeilanS on 2008-12-11
Hey everyone,

I've been meaning to try Linux for awhile, but kept getting frustrated. I've decided that my frustration is largely because I've been trying to do it on the Pentium 3 dinosaur in my storage room. So I want to dual boot on my new Vista laptop.

So, my concern now is to get this dual boot thing up and running. And I'd really like to do it without changing anything about my windows partition. I'd rather not reinstall programs and all that. My current HDD status is:

OS(C: ) - 130GB free of 220GB
RECOVERY (D: ) - 5.79GB free of 9.99GB

I'd like to split off maybe 30-50GB of that C drive to use as a Ubuntu partition.

Any chance somebody could link me to a guide and/or post an idiot proof step by step walkthrough on how to do this while keeping my data? (The data is backed up of course, but I'd still like to leave it in tact if possible).

Edit: I realized I should give some more detail about where I'm at. I have installed a working install disc for Ubuntu 8.10 32-bit. Now I just need to figure out how to make it put Ubuntu on my laptop. :P
Thanks
-Keilan

---

### Post by mikewhatever on 2008-12-11
Here you are [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall).

While a combination of P3 and Ubuntu would not have given you a speed daemon, it would have been a good and workable setup to try and learn. Why did you get frustrated?

---

### Post by KeilanS on 2008-12-11
That page looks helpful, although I am still slightly confused on what I should be doing on the partition step.

On step 5 in the [link]("https://help.ubuntu.com/community/GraphicalInstall"), I select my main partition (C), am I telling Ubuntu to wipe out that partition completely? Or is the next step asking me how much of the disk I want to use for Ubuntu?

I'm just paranoid I'll end up wiping out Vista and running into trouble reinstalling it. Because I would be in big trouble without some kind of Windows version to use.

And the reason I gave up on the P3 was mainly partitioning trouble. And even after I got Xubuntu running, it wouldn't display properly (I'm sure the fossil of a graphics card had some issues working with Ubuntu).

---

### Post by heathlair on 2008-12-11
Consider using the Wubi installer.  While in windows, pop a 8.04 or 8.10 cd in and follow the instructions for Wubi.  This will install ubuntu in a folder and let you boot into it.  It's really great and works easier than dualbooting.

---

### Post by sofasurfer on 2008-12-11
Download Gnome Partition Editor, use it to shrink your Winblows partition so that you have some free space on your disk and then just insert the Ubuntu disk into the drive and install it to the "largest continuous free space" as you are given that choice. Then when its installed you can boot to which ever OS you choose. 

If I can do it anyone can.

---

### Post by KeilanS on 2008-12-11
That sounds promising. Although are their any downsides to using Wubi as opposed to actually giving Ubuntu a partition? I like how easy it sounds, but I don't want to cripple Ubuntu.

---

### Post by KeilanS on 2008-12-11
> **sofasurfer said:**
> Download Gnome Partition Editor, use it to shrink your Winblows partition so that you have some free space on your disk and then just insert the Ubuntu disk into the drive and install it to the "largest continuous free space" as you are given that choice. Then when its installed you can boot to which ever OS you choose. 

If I can do it anyone can.

Ah, I didn't see this post when I made my last reply. This sounds pretty simple, however I just googled Gnome Partition Editor and the website seems like it only offers downloads for Linux. The files were all in the format .tar.bz2. Now I know that .bz2 is just a compression sort of like .zip, but I'm not sure how to work with a .tar file.

Sorry for the newbie questions. Although to be fair, I am in fact a newbie. :)

EDIT: I've been looking around, and found a partition editor in Vista. It looks like this [(picture)]("http://i308.photobucket.com/albums/kk323/KeilanS/Untitled2.jpg"). Would I be able to shrink my C drive (Vista says I can shrink by 40GB) and then install Ubuntu in that space using the "use the largest continuous free space" option?

---

### Post by CatKiller on 2008-12-12
> **KeilanS said:**
> Ah, I didn't see this post when I made my last reply. This sounds pretty simple, however I just googled Gnome Partition Editor and the website seems like it only offers downloads for Linux.

GParted is included on the Ubuntu cd. System -> Administration -> Partition Editor. This may well be easier to understand than the instance in the installer itself.

The GParted website has live cds as well as live USB images to download. You can use one of those if you prefer. The .tar.bz2 files are compressed archives of the GParted source code. You probably don't want those at this stage of your learning ;)

EDIT:

> **KeilanS said:**
> EDIT: I've been looking around, and found a partition editor in Vista. It looks like this [(picture)]("http://i308.photobucket.com/albums/kk323/KeilanS/Untitled2.jpg"). Would I be able to shrink my C drive (Vista says I can shrink by 40GB) and then install Ubuntu in that space using the "use the largest continuous free space" option?

I'd imagine so, although I've never used it. All you're really interested in at this point is getting a continuous block of unpartitioned space. If you're more comfortable doing that with a Windows application than one that runs on Linux, then go for it. Generally it's safest not to be using the partition that you're editing at the time you're editing it though, which is why the standard Linux method is to be running from a live cd instead.

---

### Post by CatKiller on 2008-12-12
> **KeilanS said:**
> On step 5 in the [link]("https://help.ubuntu.com/community/GraphicalInstall"), I select my main partition (C), am I telling Ubuntu to wipe out that partition completely? Or is the next step asking me how much of the disk I want to use for Ubuntu?

The first part of Step 5 is selecting which disk you wish to fiddle with. The next part defines the fiddling - whether that is to wipe it completely, or to resize the first (largest?) partition.

---

### Post by KeilanS on 2008-12-12
Thanks CatKiller!

I think I will try using the Vista partition manager. Hopefully that works for me.

Sadly I have just learned that I will have to send this computer in for repairs (bad GPU), so I will probably be back here with more questions in 8-10 business days. :P

---

### Post by CatKiller on 2008-12-12
Don't forget to back up any important data before you begin. Interrupted power is irritating at any time, but when you're in the middle of partitioning, it can be quite catastrophic. Plus it mitigates against any temporarily-thick moments.

I hope you get your computer back quickly.

---

### Post by spcwingo on 2008-12-12
Did you try xforcevesa on the P3 PC?  I'm running Ubuntu on an old P3 system with a S3 Virge video card.  It too had problems initially with video, but a quick edit of the /boot/grub/menu.lst cleared that right up.  As far as the laptop...to just try it initially, I suggest a wubi install as others have mentioned.

---

### Post by uwave on 2008-12-12
Altho not obvious to a first time user is the slider bar in the partition menu.
That really confused me when I first tried to partition my drive was the fact that they forgot to mention that you have to use the slider to change the size of the partitions.. not type or enter anything.
I think someone needs to re-write the instructions in that menu to reflect the use of the slider.
That had me stumped for two weeks before I finally found someones post on how to do it..
And I am an IT admin...

Good luck and enjoy

---

### Post by EnGorDiaz on 2008-12-12
> **uwave said:**
> Altho not obvious to a first time user is the slider bar in the partition menu.
That really confused me when I first tried to partition my drive was the fact that they forgot to mention that you have to use the slider to change the size of the partitions.. not type or enter anything.
I think someone needs to re-write the instructions in that menu to reflect the use of the slider.
That had me stumped for two weeks before I finally found someones post on how to do it..
And I am an IT admin...

Good luck and enjoy

follow my guide in my signature

theres a section gparted using the livecd

---

### Post by altonbr on 2008-12-12
Basically, here are my steps and caveats.

(I really need to write a guide).

(1) Make sure Windows is already installed. (check)
[INDENT] Windows requires being installed first as it destroys the boot loader as it does not play nicely with other operating systems (how Microsoft). If you have Windows installed first, then you can let Linux take care of the rest.
[/INDENT](2) De-fragment, de-fragment, de-fragment!
[INDENT]Windows does NOT de-fragment its hard drives automatically (I won't bore you with the technical details of why), so it is important to de-fragment before partitioning. Why? Having a fragmented hard drives means that you could have files sitting anywhere on the hard drive, including the spot that you're now destroying by creating a new partition. If you de-fragment, all the files (more or less) will sit in one continous string from beginning to where ever the data ends, allowing you to create a new parition on the tail end of the hard drive.
[/INDENT](3) Partition your hard drive using the [Ubuntu Desktop LiveCD]("http://releases.ubuntu.com/intrepid/ubuntu-8.10-desktop-i386.iso") and gParted, which is included on the CD
[INDENT]Running gParted off the Ubuntu LiveCD will allow you to adjust the partiton sizes and formats with more control than doing it through the Ubuntu installer. The way I would personally parition your hard drive is to take 29GB off the end for Ubuntu (make it 'ext3') and 1GB for swap (make it 'swap').
[/INDENT](4) Install Ubuntu as normal, but using your new partition
[INDENT]When the Ubuntu installer asks you where you'd like to install to, select the newly created 29GB partition through the 'manual' option and mount it as root (or '/'). Then you should be laughing.
[/INDENT]Of course, you're gonna want to be able to share the data between the two operating system, but that's beyond this thread I think. I usually engineer it so that Windows' My Documents reads from a partition which is actually my /home hard drive in ext3 format, but you can also do the reverse and mount your Windows parition in your /home drive.

Sorry if I've confused you, I have a habit of being pedantic and overly technical.

---

### Post by uwave on 2008-12-12
Thanks Guys,
That helps me quit a bit knowing those tid-bits.
I will bookmark this stuff and use it next time I do a dual boot job
as I too am wandering away from MS as fast as I can.
My original post was for the thread poster as I thought maybe he was going thru the growing pains as I was.
I already had an MS os running.
And it was from a post here somewhere that I found someone's instructions on how to do it, and I almost missed the slider there as well..
Alto I already think I'm to technical by nature it is appreciated.
that'l teach me to re-read what I see.

Cheers

---

### Post by pablolie on 2008-12-12
If you are running Vista already, go to Control panels and resize the hard drive already. That will make Ubbuntu make it find its home very straightforward - at least that is the way I finally managed to install Ubuntu 8.10 64 on a mirrored RAID, on which I had Vista Ultimate 64 running previously. Personally, I found the alternate CD easier, ebcause the standard CD gave me scary options that made me afraid of wiping out Vista. The alternate CD is very well behaved and asks your opinion every step, and is very intuitive.

---

### Post by Jacobmg on 2008-12-12
Hello, 
This is my first post on the Ubuntu forums, I feel as if I couldn't have picked a better subject.

Dual booting, well, triple booting (Vista x64 + XP x32 + Intrepid 32_64) is a situation I've researched extensively before making the big "deal".

I started with a Lappy that already had Vista x64, I installed XP then Ubuntu, ALL on one disk! I might be able to help.

[quote="altonbr"]Basically, here are my steps and caveats.

(I really need to write a guide).

(1) Make sure Windows is already installed. (check)

    Windows requires being installed first as it destroys the boot loader as it does not play nicely with other operating systems (how Microsoft). If you have Windows installed first, then you can let Linux take care of the rest.

(2) De-fragment, de-fragment, de-fragment!

    Windows does NOT de-fragment its hard drives automatically (I won't bore you with the technical details of why), so it is important to de-fragment before partitioning. Why? Having a fragmented hard drives means that you could have files sitting anywhere on the hard drive, including the spot that you're now destroying by creating a new partition. If you de-fragment, all the files (more or less) will sit in one continous string from beginning to where ever the data ends, allowing you to create a new parition on the tail end of the hard drive.[/quote]

You MUST defragment like my friend altonbr has stated, however, the Vista Defragmenter application is not as great as a third-party tool, like Ultimate Defrag or my favorite, Raxco Perfect Disk. Perfect Disk has an applet in the GUI that shows exactly where on the disk your files are placed.

Instead of going strait to the LiveCD's partitioner, I would recommend using Vista's Disk Manager, because it gives you the option to "shrink" your volume (C: drive, Vista partition). Since your are new to Ubuntu (like myself) the partition manager in Ubuntu can be a little intimidating, also I felt more comfortable have the space unallocated before formatting in the ext3 format.


To use Vista's disk manager--> right click "computer" --> click "manage"--> expand the "storage" section--> select "disk management"
here's a quick link to some screenshots of Vista's disk manager [http://articles.techrepublic.com.com/5100-10878_11-6170510.html]("http://articles.techrepublic.com.com/5100-10878_11-6170510.html")
In the disk manager you should see your C: drive as an "active, healthy partition"--> right click C: drive --> choose "shrink volume" (since you've defragmented, all of you're free space should be available) 

*If your available shrink space is NOT as much as you need, you will need to disable a few of Vista's system tools and programs. Pagefile, Hibernation, and System Restore.*<---Google "how to disable___" (you will probably need to use Vista's "Disk Cleanup" and defragment again)

After disk manager finishes shrinking your volume, you should notice the chosen amount of MB (30-50 GB = +-30000-50000 MB) as "unallocated space"--> ALL of your data will still be fully intact-->you are finished with Vista....for now.

Follow the Ubuntu install "How-to's" from here. I installed from the liveCD by choosing "try Ubuntu" from the liveCD boot options menu. If I can give you one more word of advise. When using the Ubuntu partition manager DO NOT select "guided" install.  I would suggest the Manual option   

Good Luck
Jacobmg

---

### Post by muteXe on 2008-12-12
+1 for partitioning within vista and not gparted.  I used GParted, and whilst my installation of linux worked fine, my vista started blue-screening :(  Although admittedly I only used vista's defragger before installing as well....

---

### Post by caljohnsmith on 2008-12-12
+2 for using Vista to do your partitioning; if you use Ubuntu's gparted partition editor to resize Vista, it usually temporarily breaks Vista until you use a Vista Install/Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table, but gparted knows nothing about updating Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Install/Recovery CD.

But unfortunately, some people have problems getting Vista's Disk Management to shrink the Vista partition as much as they want. To help prevent problems, you can:
[LIST]
[*]**Disable the pagefile:**
Right-click "Computer" > Advanced System Settings > Advanced > Performance Settings > Advanced > Change Virtual Memory. Click on "No pagefiling" and then "Set." After reboot, delete C: pagefile.sys. To do that you might need to check "show hiddenfiles" and uncheck "hide system files" by doubling-clicking Computer > Organize > "Folder Options" > View.

[*]**Disable hibernation**:
Open a terminal as administrator: press the Windows key and "r" at the same time to get the run program/command dialog, then type "cmd", then press Ctrl-Shift-Enter, and finally type "powercfg -h off".

[*]**Disable "snapshots":**
Right-click Computer > Advanced System Settings > System Protection and uncheck all the drives.

[*]**Try shrinking the Vista partition more than once: **
After doing the above steps, if you can't shrink the Vista partition as much as you want, shrink it as much as Vista will let you, and then repeat the process again. 
[/LIST]
Good luck and let us know how it goes. :)

Credits: Many thanks to forum member meierfra for providing the above steps for shrinking Vista.

---

### Post by Paqman on 2008-12-12
> **KeilanS said:**
> That sounds promising. Although are their any downsides to using Wubi as opposed to actually giving Ubuntu a partition? I like how easy it sounds, but I don't want to cripple Ubuntu.

There are two small caveats:
[LIST=1]
[*]You won't be able to hibernate. Suspend will still work fine though.
[*]You shouldn't use it on a desktop if you may experience a power cut. Wubi creates a virtual partition on the Windows partition which may break if not shut down right. Not a problem on laptops, as they have batteries and will always shut down cleanly.
[/LIST]

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by Captain_tux on 2008-12-12
> **caljohnsmith said:**
> +2 for using Vista to do your partitioning; if you use Ubuntu's gparted partition editor to resize Vista, it usually temporarily breaks Vista until you use a Vista Install/Recovery CD to fix Vista again. The reason is because Vista (unlike any other OS I know of) maintains its own HDD partition table outside of the main one in the HDD's MBR (Master Boot Record); so if you use something like gparted to repartition, it updates the MBR with the new partition table, but gparted knows nothing about updating Vista's own partition table. That then usually makes Vista unbootable until you can fix Vista's partition table with a Vista Install/Recovery CD.


Are you referring to a laptop or desktop? Or does it matter??

Because I guess I got lucky... well, then again, I used QtParted from the Knoppix Live CD to partition my disk (guess I feel more comfortable with it), then installed 8.04 in their respective partitions (**/**, **swap** and **/home**. I haven't had any problems dual booting with Vi$ta - and the *only* reason that I'm even allowing Vi$ta to exist on my laptop is to sync my Garmin GPS watch, as Linux doesn't have compatability with Garmin software :(

BTW - I found this link just a few moments ago ... thought it might be of help to other newbies (like me!): [http://easylinuxcds.com/blog/?p=139]("http://easylinuxcds.com/blog/?p=139").

---

### Post by caljohnsmith on 2008-12-12
> **Captain_tux said:**
> Are you referring to a laptop or desktop? Or does it matter??

Because I guess I got lucky... well, then again, I used QtParted from the Knoppix Live CD to partition my disk (guess I feel more comfortable with it), then installed 8.04 in their respective partitions (**/**, **swap** and **/home**. I haven't had any problems dual booting with Vi$ta - and the *only* reason that I'm even allowing Vi$ta to exist on my laptop is to sync my Garmin GPS watch, as Linux doesn't have compatability with Garmin software :(

I think it depends mostly on what partition changes you do as to whether it will be enough to break Vista. If you do minor partition changes like maybe resizing a partition that isn't Vista's partition, when you boot Vista after that, I think Vista might say "Vista has detected recent changes to your hardware configuration" or something of that sort; Vista will then try to adjust itself accordingly. But really it isn't the end of the world if doing partition changes breaks Vista, because you can almost always fix Vista after that if you have a Vista Install/Recovery CD. :)

---

### Post by KeilanS on 2008-12-12
I just realized this had a 3rd page.

Thanks for all the help everyone! I will try this stuff out as soon as I get my laptop back from Dell.

---

