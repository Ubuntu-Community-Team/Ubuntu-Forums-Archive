---
title: "Only option in install is to use 100% of the disk."
date: 2009-01-25
forum: New to Ubuntu
---

### Post by thechansen on 2009-01-25
So as you can guess by my post count and me posting in the  absolute beginner forum, I'm new to Ubuntu.   I had Ubuntu running no problems with an XP dual boot situation.  Any problems I had, this forum and google had the answers, but I can't figure out this latest problem.   

I reformatted my hard drive to set up a quad boot, with XP, Vista, Windows 7 beta and Ubuntu.  I know, it's a bit silly to have all four, but I'm changing careers and I'm getting my various computer certifications.  And I've been using Macs for about 8 years now, and my knowledge of Windows isn't exactly fresh, aside from XP.  I never even used vista before.  Or Ubuntu for that matter (it isn't exactly foreign to me having spent some time in OS X terminal screen).

Now I got the three Microsoft OSes installed with out issue, but Ubuntu doesn't seem to want to install unless its  using 100% of the disk.  I have 4 partitions that I made using GParted live CD which windows of various flavor had no problem installing on.  Ubuntu has no option for guided partition along side other OSes, and I can't seem to figure out how to get this setup manually because every time I think I have it right,  I get a message about having to format the entire disk, which I cancel.  

Any suggestions on how to get this setup?  Should I do it in a different order?  I went Win 7, Vista, XP, and then Ubuntu.  I may do it differently because installing XP last seemed to mess up my boot menu, by basically not showing me my operating system options.

Aside from all of that mess, I enjoy using Ubuntu.  Took me forever to get HDMI audio to work with my 790GX motherboard, but once I did, everything was perfect.  Most of my time on my test rig was spent in Ubuntu.  But I am liking Windows 7.  Not as much as OS X, but I'm a fanboy.

---

### Post by Kellemora on 2009-01-25
Hi TC

Are you SURE it wants to use 100% of the DISK OR
Is it wanting to use 100% of the PARTITION, which is normal?????

I haven't reinstalled Ubuntu in a while, but have 3 machines here that are triple boot and it seems I had that same question myself many moons ago.  But I didn't keep notes back then to jog this old geezers memory banks.

However, I would suggest RATHER than using the 100% of the Partition, that you place HOME on it's own partition.  That way you can add, remove or change the OS without messing up HOME and what's in it.

A guru will be along shortly to help answer your question more fully than I can.

TTUL
Gary

---

### Post by drugon on 2009-01-25
Hey,

Windows has a bad habit of sometimes erasing the MBR when higher version of the OS is installed. now regarding installation of Ubuntu, make sure the partition for Ubuntu is NOT formatted by NTFS. make the partition as Unallocated (by deleting the partition volume) or as a free space as it uses different file system. once done, it will give you different options regarding where to install. 

once you get those options, select the option of "use single largest continuous space on the disk" which will refer to the unallocated or free space partition. 

as you are sing multiple windows OS's, I recommend you to get software called "System Commander 8" which is excellent for booting up various OS's especially Windows. It has a GUI interface.

Hope this helps.

---

### Post by thechansen on 2009-01-25
yup wants to use 100% of the disk not the partition or unpartitioned space.  I was thinking just reformat the whole thing again, make a small partition for boot and images, then go XP > Vista > Win 7 > Ubuntu.  The space for Ubuntu is unallocated space on the HD, but it won't let me create a partition for swap, ubuntu, and home.  The only option is one partition for ex3. Which obviously doesn't let me install ubuntu,  because there is no swap.  I might try loading up the live cd for gparted and create three partitions in there.

EDIT:  Yup went into gparted, created the partitions in there, reloaded ubuntu installer, and everything went perfect.  Back up and running.  thanks Drugon for the advise with system commander 8.  works nicely.

---

