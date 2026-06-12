---
title: "windows crashed, want to dual install ubuntu but..."
date: 2011-08-23
forum: New to Ubuntu
---

### Post by wellie on 2011-08-23
my laptop  ( Medion )has crashed,, winows xp,,it can not start windows,, i turn on my laptop and get following message..

"Windows cannot start because following file is missing or is damaged
\WINDOWS\SYSTEM32\CONFIG\SYSTEM
Try to repair the file with the installasionprogram for windows with the installiondisc
choose R at the first screenpic for reparation"
(translated from swedish"

my problems are the following, i have no installation disc, i have tried pirate copies but it  doesnt work..
i would like to try to reboat with ubuntu, ( i have a friend over that will introduce me to ubuntu ) ..so my other problems are... can i do a dual boot or should i just override windows xp?

i have loads of pictures on the harddrive that i dont wanna loose but i cant get a hold of them since my windows xp hase crashed...

would love some help and advice

best reguards..

---

### Post by kyletstrand on 2011-08-23
You can try a dual boot and mount the windows partitions through ubuntu and save your files and back them up.  Then do away with windows since it is not of any use to you.

---

### Post by androssofer on 2011-08-23
> **wellie said:**
> my laptop  ( Medion )has crashed,, winows xp,,it can not start windows,, i turn on my laptop and get following message..

"Windows cannot start because following file is missing or is damaged
\WINDOWS\SYSTEM32\CONFIG\SYSTEM
Try to repair the file with the installasionprogram for windows with the installiondisc
choose R at the first screenpic for reparation"
(translated from swedish"

my problems are the following, i have no installation disc, i have tried pirate copies but it  doesnt work..
i would like to try to reboat with ubuntu, ( i have a friend over that will introduce me to ubuntu ) ..so my other problems are... can i do a dual boot or should i just override windows xp?

i have loads of pictures on the harddrive that i dont wanna loose but i cant get a hold of them since my windows xp hase crashed...

would love some help and advice

best reguards..

i'd get urself an ubuntu live cd. boot up with that. then you can access the windows partition. so plug in an external hard drive, and you can move all the pictures etc on your windows to the external hard drive. 

then you can do the install and not have to worry about losing your files :-). you can dual boot with windows if you want. it will leave your broken windows as it is(provided you have enough free space on your HD) and put ubuntu beside it. so if in future you get a windows disc that works you can recover ur windows :-). or you can just blitz the whole drive and just hav ubuntu.. is up to you....

---

### Post by wellie on 2011-08-23
mount though ?? kk im new at this,,

but a dual installion i can do :) thanks for ur help :)

---

### Post by wellie on 2011-08-23
thanks for all ur help and quick replies:P

---

### Post by androssofer on 2011-08-23
> **wellie said:**
> mount though ?? kk im new at this,,

but a dual installion i can do :) thanks for ur help :)

the term mount sounds scarier than it is. when ur in a live cd. open the file browser... then on the left panel it should say sumthing like "xxxgb partition".(replacing xxx with the number of gb in ur windows partition). if u click on that, it will "mount" it for u, then u can access the files in ur windows parition as if u wer on windows :-)

---

### Post by wellie on 2011-08-23
well i downloaded the [ubuntu-11.04-desktop-i386.iso]("http://se.releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso")  on another laptop, burned it to a dvd, putted into my broken medion laptop and it cant read the cd/dvd,
 the same warnings came up as before

shall i download the alternative iso ?


best reguards;)

---

### Post by wellie on 2011-08-23
starting a new thread with this :)

---

### Post by grahammechanical on 2011-08-23
You may need to set the machine to boot from CD/DVD in the BIOS. If you are getting the same warnings then the machine is trying to boot from the hard disk.

Enter the BIOS before the machine tries to boot and set the CD drive as the first boot option. Then when you boot the machine will look on the CD drive first for an operating system before it looks on the hard drive for an operating system.

Regards.

---

### Post by wellie on 2011-08-24
how do I do this ???????:(:(:(:(


You may need to set the machine to boot from CD/DVD in the BIOS. If you  are getting the same warnings then the machine is trying to boot from  the hard disk.

Enter the BIOS before the machine tries to boot and set the CD drive as  the first boot option. Then when you boot the machine will look on the  CD drive first for an operating system before it looks on the hard drive  for an operating system.

---

### Post by wellie on 2011-08-24
how do I do this ???????:sad::sad::sad::sad:

---

### Post by Rex Bouwense on 2011-08-24
When you turn your computer on and before it boots from the hard drive you have to enter the BIOS.  This done by hitting the F2 key on most computers (Others may use a different key).  This will get you to the BIOS.  Once there move to boot order and just move the CD ahead of the hard drive.  Then save the changes and exit.  Now when you boot, your computer will first check the CD drive (ahead of the hard drive) for an OS to boot from.  I hope that is what you are asking.:popcorn:

---

### Post by wellie on 2011-08-24
thanks for your reply, I have done so but it would not read the CD anyway, trying to run ubuntu in parallel have you any other suggestions?

---

### Post by David Andersson on 2011-08-24
> **wellie said:**
> thanks for your reply, I have done so but it would not read the CD anyway, trying to run ubuntu in parallel have you any other suggestions?

In any case, you must first make your computer boot Ubuntu from the CD or DVD or an USB. From there you have the option to install Ubuntu first and rescue you photos later, or rescue your photos first and install Ubuntu later. (If I were you, I would rescue my photos first.)

(A word of caution. *If* the problem that windows cannot read a file is caused by the hard disk becoming old, there is a risk that the partition resizing phase of a dual boot installation will fail, and that more files in the windows partition are damaged. Hence, rescue your photos first.)

---

### Post by GWBouge on 2011-08-24
If you've got the boot order set up right (remember to Save before you exit the BIOS!) and it's still not booting from the CD, I'd say it's either a corrupt download/burn, or you burnt the .iso *file* instead of the *image*.

---

### Post by eriktheblu on 2011-08-24
Each system board will have it's own method to access BIOS. Check the literature that came with your computer, or the manufacturer's website.

A brief Google search indicates that with Medion, you should use F11 to access the BIOS.

---

### Post by wellie on 2011-11-29
fixed it thanks for all the replies.. dual booted it!

---

### Post by mörgæs on 2011-11-29
Good, then please mark the thread 'solved'.

---

