---
title: "Urghh.. trying to Dual-Boot Vista&amp;Ubuntu, failing ALOT."
date: 2009-01-24
forum: New to Ubuntu
---

### Post by wildfire95 on 2009-01-24
Dont get me wrong, i LOVE linux and ubuntu. I even edited a Linux distro for myself before, but installnig Ubuntu is confusing for me... but i doubt its Ubuntu thats causing the problems.

You see, i have a single HDD (250GB) and no partitions, when i used a Windows program to create a partition for Ubuntu to go onto, the programs asks to restart my PC, (i tried 2 programs, same results) but when it boots back up i got a BlueScreenOfDeath. 

I tried in Ubuntu, but for some strange reason i couldnt figure out how to make it create a partition instead of using my entire HDD, and formatting my Vista and all my files (which it attempted to do, had to do a "speed-shutdown"),

I know it isnt a Defrag problem, my PC is cleaned every weekend automatically. Do i have to create the partition in a seperate part of the ubuntu install section? Or is there a program included in the liveCD which can create partitions?

Please tell me what to do, or reccomend me a good guide to use to get this Dual-Boot going... because im getting a new "Gaming" PC, and my current model only has 1GBRam so im going to use my current 1 as a Dual-Boot with Ubuntu and Vista... Ubuntu is amazing in my eyes and will suit me perfectly, and well i paid for vista so i reallly dont like dumping it after a few months, £100 wasted if i do.

Your ever-growing fan,
Thanks,
Cameron

---

### Post by SunnyRabbiera on 2009-01-24
When installing from the live cd use the guided mode for dual boot, it should do the trick.
If you are using wubi it does have issues.

---

### Post by billgoldberg on 2009-01-24
> **wildfire95 said:**
> Dont get me wrong, i LOVE linux and ubuntu. I even edited a Linux distro for myself before, but installnig Ubuntu is confusing for me... but i doubt its Ubuntu thats causing the problems.

You see, i have a single HDD (250GB) and no partitions, when i used a Windows program to create a partition for Ubuntu to go onto, the programs asks to restart my PC, (i tried 2 programs, same results) but when it boots back up i got a BlueScreenOfDeath. 

I tried in Ubuntu, but for some strange reason i couldnt figure out how to make it create a partition instead of using my entire HDD, and formatting my Vista and all my files (which it attempted to do, had to do a "speed-shutdown"),

I know it isnt a Defrag problem, my PC is cleaned every weekend automatically. Do i have to create the partition in a seperate part of the ubuntu install section? Or is there a program included in the liveCD which can create partitions?

Please tell me what to do, or reccomend me a good guide to use to get this Dual-Boot going... because im getting a new "Gaming" PC, and my current model only has 1GBRam so im going to use my current 1 as a Dual-Boot with Ubuntu and Vista... Ubuntu is amazing in my eyes and will suit me perfectly, and well i paid for vista so i reallly dont like dumping it after a few months, £100 wasted if i do.

Your ever-growing fan,
Thanks,
Cameron

On the Ubuntu live cd, there is an partition editor installed.

It's called "gparted", but I think in the menu it's called "gnome partition editor".

Just press "alt+f2" and enter "gksudo gparted".

Then create a seperate partition for your Ubuntu install (and maybe a small one for the swap).

Then when installing Ubuntu, you'll need to go to "manual" in the partition part of the install.

On the big partition you created, pick "/" as mount point.

For the swap you created, pick "/swap" as mount point.

---

### Post by wildfire95 on 2009-01-24
> **SunnyRabbiera said:**
> When installing from the live cd use the guided mode for dual boot, it should do the trick.
If you are using wubi it does have issues.

In the windows programs, it give em the B.S.O.D and the partition dont show up xD

---

### Post by theozzlives on 2009-01-24
Use the partition resizing tool that came with Vista and in the install program choose Guided Use Free Space.

---

### Post by tntxx9 on 2009-01-24
you can do one thing ! back up all your data , defrag you pc using a good program (in my opinion the vistas on isn't the best ...) the put the ubuntu 8.10 live cd  in the pc, restart it so it goes to the ubuntu menu , and when it comes to choose the partition, you have one option to create a partition to install ubuntu in it ...
That was wat i done to have my ubuntu installed at my vista HDD ;) any question about what i sayd , just ask ^^

---

### Post by balaknair on 2009-01-24
If you're planning to dual-boot Vista and Ubuntu, I'd suggest using the disk management tools in Vista to create free space(not a partition, just the free space), then booting into the LiveCD and selecting the 'Guided install- Use largest continuous free space' option). Vista tends to get really unhappy if you mess around with its partition with other software.

1) Boot into Vista--> *Defragment the hard drive before attempting any partition resize oerations*
Right click the My Computer icon> Manage--> Disk Management

2) Right click on the partition shown> Shrink Partition

3) Select how much space you want to free for your Ubuntu partition(at least 5 GB) and click the 'Shrink' button. *Do NOT format/partition the freed up space*.

4) Reboot 

5) Now boot into the Live CD and start the install process. When you get to the partitioning step, select the 'Guided install- Use largest continuous free space' option. Ubiquity(the Ubuntu installer) will automatically select the freed up space and format it for a Linux install.

---

### Post by wildfire95 on 2009-01-24
> **balaknair said:**
> Vista tends to get really unhappy if you mess around with its partition with other software.



Yea, i realised =D

Im going to try out what you have all advised me to do in an hour or 2.. ill post the results in this thread later ;) 

Thankyou, 
Cameron.

---

### Post by balaknair on 2009-01-24
OK

All the best.

---

### Post by yeats on 2009-01-24
This is an excellent guide:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

If you run into the situation where Vista's "shrink volume" doesn't provide enough space, here's what to do:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Good luck!

---

### Post by cprofitt on 2009-01-24
> **wildfire95 said:**
> Dont get me wrong, i LOVE linux and ubuntu. I even edited a Linux distro for myself before, but installnig Ubuntu is confusing for me... but i doubt its Ubuntu thats causing the problems.

You see, i have a single HDD (250GB) and no partitions, when i used a Windows program to create a partition for Ubuntu to go onto, the programs asks to restart my PC, (i tried 2 programs, same results) but when it boots back up i got a BlueScreenOfDeath. 

I tried in Ubuntu, but for some strange reason i couldnt figure out how to make it create a partition instead of using my entire HDD, and formatting my Vista and all my files (which it attempted to do, had to do a &quot;speed-shutdown&quot;),

I know it isnt a Defrag problem, my PC is cleaned every weekend automatically. Do i have to create the partition in a seperate part of the ubuntu install section? Or is there a program included in the liveCD which can create partitions?

Please tell me what to do, or reccomend me a good guide to use to get this Dual-Boot going... because im getting a new &quot;Gaming&quot; PC, and my current model only has 1GBRam so im going to use my current 1 as a Dual-Boot with Ubuntu and Vista... Ubuntu is amazing in my eyes and will suit me perfectly, and well i paid for vista so i reallly dont like dumping it after a few months, £100 wasted if i do.

Your ever-growing fan,
Thanks,
Cameron

 I would resize Vista partitions using the built-in tool included with Vista. Just go to the disk management and right-click on the partition. You will be able to resize it and then use the LiveCD to install Ubuntu.

---

### Post by balaknair on 2009-01-24
@chrissharp123

That was a great article at howtogeek. Wish I'd read that one before attempting to fix a friend's laptop for him(there was just one 160 GB partition, he wanted to split it into C:\ 30 GB, E:\ 100 GB, F:\ ~30GB(the remaining space, and after messing with Vista's disk management and failing, he tried Partition Magic, and ended up with Vista refusing to boot). He also had Norton installed, to complicate things. It took over three hours to just get the system to boot. I ended up using most of the tweaks/hacks mentioned in the article one by one. If I'd read it earlier, that would have saved at least an hour of experimentation.

Thanks for the link.

---

### Post by wildfire95 on 2009-01-24
It failed complety, in the LIVECD partion manager it told me to run:
chkdsk /f

Whats that?

And in the vista one, i have 1GB ram and it kept telling me even when i had closed every other program ~
"Not enough memory"

---

### Post by balaknair on 2009-01-24
When using GParted(the LiveCD partition tool), does the error say anything about 'dirty bits'? 

*chkdsk /f* ---> This runs the Check Disk for errors utility in windows. You get this error because GParted detects errors in your hard drive(or the drive/partition has been flagged 'dirty' by Windows- ie, Windows thinks there are errors on the drive). This could be because of the tools you used earlier not doing their job correctly, or simply because of the drive not being unmounted properly when Vista crashed(the BSODs you got).

To run a chkdsk, log in to Vista and open My Computer--> Right click on the drive icon and select 'Properties'--> 'Tools'--> 'Error checking'--> 'Check now'. In the pop-up window that now appears select both options(to fix fs errors and to recover bad sectors). The disk check will start when on the next reboot. If you cannot boot into Vista, use the Vista DVD or system restore disk to boot up and select the 'repair' option.
 
'Not enough memory'--> 1 GB of RAM is the bare minimum to run Vista. Vista tends to be sluggish even on 2 GB RAM if Aero is enabled. 
But this error you're getting may not be anything to do with the installed RAM. It could also be that Vista can't find your swap file after the earlier partition manipulation or something got locked down/corrupted(or all of the above).


1) If you have a Vista install DVD(or a system restore DVD/CD from the manufacturer), the best option is to wipe the disk clean after backing up any important files/data you want to save, reinstall Vista*[on the first partition with about 20-30 GB, with the remaining space divided up into a) shared NTFS partition for Vista and Ubuntu, approx. 200GB and b) unformatted free space to install Ubuntu to, approx. 10-20 GB for root(/), and 1-2 GB for Swap]*, then install Ubuntu('Guided: Use largest continuous free space' option or use the manual partition option if you have some idea about partitioning).

2) If you do not have a Vista DVD to install from, run chkdsk as described above, defrag the disk with a proper defrag utility(I recommend Power Defragmenter, the defrag tool in Windows is pretty lame, and you might need to defrag the drive 2-4 times in a row before it gets properly defragged), disable the pagefile, and then try shrinking the partition again with Vista's disk management tools. If you still get the 'not enough memory error', boot into the LiveCD and try Gparted again(try using the manual partitioner this time and see what the hard drive looks like to Gparted).

3) If you don't have a Vista DVD and cannot boot into Vista, the Ubuntu LiveCD can help repair your Vista partition using a tool called testdisk(you will need a working internet connection when logged in on the LiveCD however, since the tool must be downloaded from the Ubuntu server), but given how touchy Vista can be and since I know very little about what state your hard drive is in right now, I wouldn't recommend it for now.

Recommended reading:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.howtogeek.com/howto/windows-vista/guide-to-using-check-disk-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/guide-to-using-check-disk-in-windows-vista/)
[http://www.geekgirls.com/windows_defrag.htm#efficient](http://www.geekgirls.com/windows_defrag.htm#efficient)
[https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you want to try Manual Partitioning on the LiveCD, read this first:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by yeats on 2009-01-24
@balaknair

Yes - I used that to cram Ubuntu on my wife's computer.  Fortunately, it booted up normally and I didn't have to suffer what you went through :-).

---

