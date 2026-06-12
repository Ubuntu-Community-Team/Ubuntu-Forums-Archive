---
title: "Only two Options to partition, I need the third one"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by xtrememeasures10 on 2009-03-01
Ok First off im brand new on here So dont yell if this is in the wrong section. Tonight i reinstalled xp cause it was acting up and i have had this linux cd for ever and just never managed to install it.

To make a long story short i downloaded ubuntu 8.04 and im stumped at what to do when the partitioner comes up. Every tutorial that i have read says there are three options guided-entire disk, guided-resize disk, and manual. well i do not have the option of guided-resize.  From what i understand i need that option to have a dual boot. 

Heres how everything is setup.
I have 3 partitions which are all formatted in ntfs.
xp 38154.5mb
linux 37942mb
Hp quickplay 212mb

Xp has been installed and now im trying to install linux to the second partition. 

Thanks for the help in advance!
Matt~

---

### Post by Xiong Chiamiov on 2009-03-01
You'll have to choose manual partitioning.  Linux will require two partitions - a swap partition, usually about the size of your RAM, and an ext3 (or xfs, reiser, etc.) partition for the OS and your data.

---

### Post by xtrememeasures10 on 2009-03-01
> **Xiong Chiamiov said:**
> You'll have to choose manual partitioning.  Linux will require two partitions - a swap partition, usually about the size of your RAM, and an ext3 (or xfs, reiser, etc.) partition for the OS and your data.

Ok so When i choose manual it comes up with /dev/sda and thats all. my options are    new partition table and undo changes to partitions. 

How do i make it so i dont delete xp and i set the partitioner up so that i end up partitioning that 37942mb partition into two more separate parts. And by the way i have 2 gigs of ram.

---

### Post by Ms_Angel_D on 2009-03-01
Hello xtrememeasures I hope you'll find you like Ubuntu, I suggest you have a look at this excellent guide to dual booting windows xp and ubuntu with Xp installed first.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

I hope this helps,
Angel

---

### Post by howefield on 2009-03-01
When you select manual partitioning, you can see the "linux 37942mb" partition, yes ? (I am assuming it is empty and no data on it that needs to be saved ?)

Highlight that partition and press the edit button, then make an ext3 partition with all bar 4 gig of it and set it to /

Then edit the 4 remaining gig and make that your swap partition.

---

### Post by xtrememeasures10 on 2009-03-01
> **MetalHellsAngel said:**
> Hello xtrememeasures I hope you'll find you like Ubuntu, I suggest you have a look at this excellent guide to dual booting windows xp and ubuntu with Xp installed first.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

I hope this helps,
Angel

Thanks buddy So far i like it on this live cd but its bein a pain to install. That link you gave me is the one i looked at earlier when i was trying to install an older version and having the same problem.  Look at that how too again. Look at the 3rd page it shows the three options. My screen is the same as that one minus the first option that says resize lol.  Thanks tho man!

> **howefield said:**
> When you select manual partitioning, you can see the "linux 37942mb" partition, yes ? (I am assuming it is empty and no data on it that needs to be saved ?)

Highlight that partition and press the edit button, then make an ext3 partition with all bar 4 gig of it and set it to /

Then edit the 4 remaining gig and make that your swap partition.

No i cant the only thing that pops up is /dev/sda and im assuming thats my entire hard drive.   
The drive is empty but its formatted in ntfs. Im using the live cd right now and i can access that drive so i know linux can see it but it doesnt want to access that partition individually in the prepare partitions prompt.

---

### Post by clblanchard on 2009-03-01
you need to select the ntfs partition. then you choose a new size for it.  after that you should have the rest of the drive as free space.  in this space you should make at least 2 partitions, one for swap which you will only need from 512 mb to 1 gb for and one for / (the root file system) and personal data. personally I use 3 partitions, one for swap, one for /, and one for /home (your data).  that way when you update to the next release, assuming you are not using the long term release, you don't hose your configs and such.  let me know if that works for you.  oh yeah, just in case your are wondering why so little swap (virtual memory) space is needed, since you have 2 gb of ram you are not going to be "swapping" that much data.  Ubuntu and linux in general are way less memory intensive than most things on windows.  Hope i could help.:guitar:

---

### Post by xtrememeasures10 on 2009-03-01
Alright i dont know how to do screen shots so heres the next best thing.

[IMG]http://memimage.cardomain.com/ride_images/1/2251/181/5625090192_large.jpg[/IMG]
This is what im talking about not getting the third option

[IMG]http://memimage.cardomain.com/ride_images/1/2251/181/5625090193_large.jpg[/IMG]
When i click on manual and next this is the next thing that appears.


> **clblanchard said:**
> you need to select the ntfs partition. then you choose a new size for it.  after that you should have the rest of the drive as free space.  in this space you should make at least 2 partitions, one for swap which you will only need from 512 mb to 1 gb for and one for / (the root file system) and personal data. personally I use 3 partitions, one for swap, one for /, and one for /home (your data).  that way when you update to the next release, assuming you are not using the long term release, you don't hose your configs and such.  let me know if that works for you.  oh yeah, just in case your are wondering why so little swap (virtual memory) space is needed, since you have 2 gb of ram you are not going to be "swapping" that much data.  Ubuntu and linux in general are way less memory intensive than most things on windows.  Hope i could help.:guitar:

---

### Post by clblanchard on 2009-03-01
you have to select manual partition.  then you select the ntfs partition.  you make it what ever gb you want it.  ie. maybe you have a 100 gb hd drive
you make it 15 gb.  the partitioner will understand this if you select the ntfs partition and make it 15 gb. the rest will be free space. partition it as you see fit, leaving / enough room to store the O/S and your files and swap as your virtual memory buy not more than 1 gb.  you will not need more than that. in fact you will probably need only about 512 mb of swap if you have 2 gb of ram. once again i recommend making 3 partitions. one for /(the root) one for /home (your dir) and one for swap (you have 2 gb of actual ram,  I personally would not make this over 512 mb.)  just keep posting if you have problems. btw, what vid. card are you using?

---

### Post by -kg- on 2009-03-01
I am starting to think that you have a defective (or wrong) installation disk.  Just to check, I booted on my Hardy 8.04 Live CD installation disk, and as I definitely do know how to do screenshots, here are my appropriate screenshots:

[ATTACH]104934[/ATTACH]

[ATTACH]104935[/ATTACH]

As you notice from the first screenshot, I have 4 installation options.  I chose manual, and you can see that my options included more than yours presented.  This makes me think that either you have a defective download, or that you downloaded the wrong installation disk.

Are you sure you downloaded the Ubuntu Hardy 8.04 Live CD, or did you perhaps download the server disk or the alternate install disk by mistake?  How did you download it...http/ftp or torrent?  What steps did you take to assure the integrity of the download and burn of that disk?

You should have the options I have, but apparently you don't.  Check everything and make sure you have everything right.  When you select the "Manual" option, you should be presented with what I have, not what you have.  You should show "dev/sda" with the partitions contained on it, not just the device.

---

### Post by The Cog on 2009-03-01
Am I to understand that you used Windows to create an NTFS partition for Linux to go on? If so, that's no good. Linux cannot live on NTFS. But if you delete that NTFS partition again (use windows to do it), then the Ubuntu installer should then offer the option of something like Use the largest free space. Take this option, and teh installer will create a partition from that space (two actually), format them appropriately and install on there. I think this is the easiest way to go for you.

---

### Post by xtrememeasures10 on 2009-03-01
Yeah dude i defiantly have something wrong here.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
is where i downloaded it from. clicked on desktop edition then ubuntu 8.04lts.   Then the location i downloaded from was united states Michigan tech linux users groop.
Once the download was finished it was an iso file. I used sonic, a iso burning software that came with my hp. Burnt the disk, tossed it in the drive restarted the computer, booted from disk. selected install ubuntu, followed the prompts and vwalla now im here.
 

> **-kg- said:**
> I am starting to think that you have a defective (or wrong) installation disk.  Just to check, I booted on my Hardy 8.04 Live CD installation disk, and as I definitely do know how to do screenshots, here are my appropriate screenshots:

[ATTACH]104934[/ATTACH]

[ATTACH]104935[/ATTACH]

As you notice from the first screenshot, I have 4 installation options.  I chose manual, and you can see that my options included more than yours presented.  This makes me think that either you have a defective download, or that you downloaded the wrong installation disk.

Are you sure you downloaded the Ubuntu Hardy 8.04 Live CD, or did you perhaps download the server disk or the alternate install disk by mistake?  How did you download it...http/ftp or torrent?  What steps did you take to assure the integrity of the download and burn of that disk?

You should have the options I have, but apparently you don't.  Check everything and make sure you have everything right.  When you select the "Manual" option, you should be presented with what I have, not what you have.  You should show "dev/sda" with the partitions contained on it, not just the device.

---

### Post by xtrememeasures10 on 2009-03-01
Yes i used the windows partitioner to create the ntfs partition. So i should delete that partition? and what should i re partition it as?

> **The Cog said:**
> Am I to understand that you used Windows to create an NTFS partition for Linux to go on? If so, that's no good. Linux cannot live on NTFS. But if you delete that NTFS partition again (use windows to do it), then the Ubuntu installer should then offer the option of something like Use the largest free space. Take this option, and teh installer will create a partition from that space (two actually), format them appropriately and install on there. I think this is the easiest way to go for you.

---

### Post by xtrememeasures10 on 2009-03-01
Anyone had this problem? Im about to just give up and continue using pos windows all the time.

---

### Post by The Cog on 2009-03-01
> **xtrememeasures10 said:**
> Yes i used the windows partitioner to create the ntfs partition. So i should delete that partition? and what should i re partition it as?

Yes delete it. Do not repartition it as anything - leave the space unpartitioned, unallocated. Then let the installer use the free space and it will create the partitions it needs inside that unallocated space. It will create a smallish swap partition and a large partition formatted as ext3.

---

### Post by xtrememeasures10 on 2009-03-01
Awesome Thanks man that fixed it. Im installed and everything right now!

I inserted the xp recovery disk. booted from the disk and used the windows partitioner to delete the partition that i had alotted for ubuntu. exited the windows partitioner. booted back up, tossed in the ubuntu cd. booted the cd and it gave me the little bar to drag accross the screen! Thanks everyone! Now i have some playing to do with this.

> **The Cog said:**
> Yes delete it. Do not repartition it as anything - leave the space unpartitioned, unallocated. Then let the installer use the free space and it will create the partitions it needs inside that unallocated space. It will create a smallish swap partition and a large partition formatted as ext3.

---

### Post by xtrememeasures10 on 2009-03-02
Ok now i tried installing HP quickplay on the partition i had left for it and  only xp works. xp when it starts up says theres a disk error too. but it runs.

---

### Post by 3lancer on 2009-03-02
Sorry, not related to ur current problem, but i have exactly the same problem as did have and tried to leave a partition unallocated (free space) and install from the cd ubuntu 8.10 but it still does not show the guided resize option..

BTW im tryin to do a dual boot with vista already installed.

i accidently left my 1TB usb hdd in and it seems to like it and would allow a guided resize on tat but not my laptop hddd,,,

fdisk via live cd does detect tat i have 3 partition on the laptop hdd

extended, vistaOS:ntfs and Data:ntfs, 

currently i have
[ATTACH]105077[/ATTACH]

can the problem be tat the free space is at the header of my hdd?? or something

Thanks,
Toan

---

### Post by xtrememeasures10 on 2009-03-02
> **3lancer said:**
> Sorry, not related to ur current problem, but i have exactly the same problem as did have and tried to leave a partition unallocated (free space) and install from the cd ubuntu 8.10 but it still does not show the guided resize option..

BTW im tryin to do a dual boot with vista already installed.

i accidently left my 1TB usb hdd in and it seems to like it and would allow a guided resize on tat but not my laptop hddd,,,

fdisk via live cd does detect tat i have 3 partition on the laptop hdd

extended, vistaOS:ntfs and Data:ntfs, 

currently i have
[ATTACH]105077[/ATTACH]

can the problem be tat the free space is at the header of my hdd?? or something

Thanks,
Toan

I dunno man im pretty new to this os. But my free space was at the other end of it so maybe. I dont know how you would fix that other than re-running vista install. partitioning it again then installing vista on the first partition? maybe someone else that knows more of what there doing will have an insite to it. 

I guess you could also try defraging your hd that might move it too the front im not sure man.

---

### Post by 3lancer on 2009-03-02
could it be that, ubuntu installer required a certain amount of free hdd space b4 it allows guided resize on the hdd??

as u can c i only have like 8.5gb ,,, minimum 10GB mayb ?

---

