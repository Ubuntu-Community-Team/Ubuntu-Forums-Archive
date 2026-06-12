---
title: "Help My ubuntu 11.04 is playing up"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by edwardpatch1 on 2011-09-01
when i start ubuntu it says the grub thing like the terminal at first do i reinstall it or do i need to type somthging or how do i repair it plz reply fast :)

---

### Post by BlinkinCat on 2011-09-01
What exactly does it say?
How old is the system?

---

### Post by edwardpatch1 on 2011-09-01
w8 let me try again and i will right the info down it was working before :)

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> 
Version of ubuntu?
version is 11.04

---

### Post by edwardpatch1 on 2011-09-01
[CENTER]GNU GRUB version 1.99 rc1-13ubuntu3[/CENTER]
[LEFT]Minimal BASH-like line editing is supported. For the first word, TAB Lists possible command completions. Anywhere else TAB lists possible device or file completion [/LEFT]

---

### Post by cipherboy_loc on 2011-09-01
It appears your /boot/grub/grub.cfg is broken. Boot a LiveCD and run the boot info script in my signature. You probably just need to CHROOT and then run update-grub, but not sure.


Cipherboy

---

### Post by edwardpatch1 on 2011-09-01
> **cipherboy_loc said:**
> It appears your /boot/grub/grub.cfg is broken. Boot a LiveCD and run the boot info script in my signature. You probably just need to CHROOT and then run update-grub, but not sure.


Cipherboy
how do i do that then

---

### Post by cipherboy_loc on 2011-09-01
There shouldn't be a need to re-install it. Here are a couple of tutorials on chroot and fixing grub:

[http://ubuntuforums.org/showthread.php?t=1692144](http://ubuntuforums.org/showthread.php?t=1692144)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Cipherboy

---

### Post by edwardpatch1 on 2011-09-01
> **cipherboy_loc said:**
> There shouldn't be a need to re-install it. Here are a couple of tutorials on chroot and fixing grub:

[http://ubuntuforums.org/showthread.php?t=1692144](http://ubuntuforums.org/showthread.php?t=1692144)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Cipherboy
i cant boot the cd from the bios or it says that my cpu is too old

---

### Post by saltmarshlamb on 2011-09-01
Use whatever you used to install with.

---

### Post by saltmarshlamb on 2011-09-01
You need to boot whatever you installed from so you can reinstall grub - links for which are given above. 

IF you installed _within_ windows - that is as Wubi - you need to say so.

---

### Post by edwardpatch1 on 2011-09-01
> **saltmarshlamb said:**
> You need to boot whatever you installed from so you can reinstall grub - links for which are given above. 

IF you installed _within_ windows - that is as Wubi - you need to say so.

its inside windows

---

### Post by saltmarshlamb on 2011-09-01
Wubi grub issues can be somewhat different - I've not used it more than once in the last 4 years. 

I've asked staff to change the prefix to wubi. 

Hope you get help.

---

### Post by edwardpatch1 on 2011-09-01
> **saltmarshlamb said:**
> Wubi grub issues can be somewhat different - I've not used it more than once in the last 4 years. 

I've asked staff to change the prefix to wubi. 

Hope you get help.
ok

---

### Post by Sef on 2011-09-01
> i cant boot the cd from the bios or it says that my cpu is too old

How did you install Ubuntu then?

---

### Post by edwardpatch1 on 2011-09-01
> **Sef said:**
> How did you install Ubuntu then?

from disc but in windows i launched disc then i choosed install in windows its been working but now its saying grub problem

---

### Post by philinux on 2011-09-01
> **edwardpatch1 said:**
> from disc but in windows i launched disc then i choosed install in windows its been working but now its saying grub problem

I dont use wubi but this may help you.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It's the wubi sticky thread in the General Help forum.

---

### Post by edwardpatch1 on 2011-09-01
> **philinux said:**
> I dont use wubi but this may help you.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

It's the wubi sticky thread in the General Help forum.

ok

---

### Post by BlinkinCat on 2011-09-01
Hi Edward,
For someone to help you, I think they will need the result of the boot info script -

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have any problem with that, this may help!

[http://ubuntuforums.org/showpost.php?p=11066123&postcount=2](http://ubuntuforums.org/showpost.php?p=11066123&postcount=2)

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> Hi Edward,
For someone to help you, I think they will need the result of the boot info script -

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have any problem with that, this may help!

[http://ubuntuforums.org/showpost.php?p=11066123&postcount=2](http://ubuntuforums.org/showpost.php?p=11066123&postcount=2)
ok how do i install it if i cant get in ubuntu ?

---

### Post by BlinkinCat on 2011-09-01
Keep at it Edward -

Keep it in mind that I am no expert on grub!

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> Keep at it Edward -

Keep it in mind that I am no expert on grub!

but ubuntu will not start at all so how do i download
p.s.
i really need my ubuntu on. my windows is to slow and i cant reinstall ubuntu or i lose my files :(

---

### Post by BlinkinCat on 2011-09-01
Refer to thread mentioned in #18

Problem 1. appears to refer to your problem - I can only suggest that you follow the answers specifically for that problem -

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> Refer to thread mentioned in #18

Problem 1. appears to refer to your problem - I can only suggest that you follow the answers specifically for that problem -

ok but i looked at 2 vids and 10 nsteps on other forums none helped

---

### Post by BlinkinCat on 2011-09-01
Can you boot into Windows? - If so Problem 2 may apply -

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> Can you boot into Windows? - If so Problem 2 may apply -
yes i can its just ubuntu

---

### Post by pgp_protector on 2011-09-01
If I'm understanding this right

You're system started with Windows(Version??)
You installed Linux From windows so you could dual boot (Right?)

now you can't boot to either version ?

If so, (Someone correct me if I'm wrong) but you should be able to use your windows disk to fix the boot section of your Hard Drive, then from their fix it so you can dual boot back to Linux.

---

### Post by BlinkinCat on 2011-09-01
Can you follow the answers for problem 2?

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> If I'm understanding this right

You're system started with Windows(Version??)
You installed Linux From windows so you could dual boot (Right?)

now you can't boot to either version ?

If so, (Someone correct me if I'm wrong) but you should be able to use your windows disk to fix the boot section of your Hard Drive, then from their fix it so you can dual boot back to Linux.
i can booty windows 7 but ubuntu is not starting its saying gnu grub problem but im not reinstalling ubuntu so is there another way

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> Can you follow the answers for problem 2?

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

no to hard its very hard for me to understand i am 12 for a start plus i am autistic which i cant under stand steps very gd and that

---

### Post by BlinkinCat on 2011-09-01
I'm not sure if solutions are for 11.04 - perhaps someone else can help!

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> I'm not sure if solutions are for 11.04 - perhaps someone else can help!
k all i need is another way that i can fix it without reinstalling ubuntu but all the one that i found were just if u were just about when ubuntus running

---

### Post by BlinkinCat on 2011-09-01
Do you really need to keep your Wubi installation?

Perhaps removing it via Windows Remove programs is an option?

Then if you wished, you could reinstall it - Perhaps you may consider installing a LTS version such as 10.04 for greater stability.

Your doing very well for a twelve year old Edward. - :P

---

### Post by pgp_protector on 2011-09-01
Ok looking over this thread we might be able to walk you through it.
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

1) boot windows and try running checkdsk /r 

After that finishes, shutdown windows cleanly & reboot (this might fix the problem if you're lucky)


2) The Ubuntu needs files that are located in C:\ubuntu\disk\root.disk & c:\ubuntu\disk\boot.
Check that they exist. if not they may of been "fixed/moved" by windows to a hidden folder

---

### Post by saltmarshlamb on 2011-09-01
With regard to no being able to boot with a cd - is that because you're having trouble getting it to do so with the BIOS- or is it that the cd drive is not working?

If it's because you're not able to get into and change the BIOS perhaps we can help you get that done. 

You'll find that even if you get through this - the future is likely to have you needing to boot with a cd.

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Ok looking over this thread we might be able to walk you through it.
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

1) boot windows and try running checkdsk /r 

After that finishes, shutdown windows cleanly & reboot (this might fix the problem if you're lucky)


2) The Ubuntu needs files that are located in C:\ubuntu\disk\root.disk & c:\ubuntu\disk\boot.
Check that they exist. if not they may of been "fixed/moved" by windows to a hidden folder
so what do i do checkdsc is not recognised

---

### Post by Johnb0y on 2011-09-01
[I]could try: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
 
this helped me with my xp/ubuntu issue... hope it helps you too :smile: 
 
p.s. it is free for private use... 			[/I]:)

---

### Post by pgp_protector on 2011-09-01
> **saltmarshlamb said:**
> With regard to no being able to boot with a cd - is that because you're having trouble getting it to do so with the BIOS- or is it that the cd drive is not working?

If it's because you're not able to get into and change the BIOS perhaps we can help you get that done. 

You'll find that even if you get through this - the future is likely to have you needing to boot with a cd.

Reading the guide for Wubi, the normal fixing of Grub might cause other issues.
[quote=wiki]Never try to correct Wubi boot problems by reinstalling Grub2. This will prevent Windows from booting and will not fix the Wubi install[/quote]

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> so what do i do

Boot windows, open explorer & right click on your c: drive properties.
On the tools tab, run error-checking (Check-now)

---

### Post by edwardpatch1 on 2011-09-01
> **Johnb0y said:**
> [I]could try: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
 
this helped me with my xp/ubuntu issue... hope it helps you too :smile: 
 
p.s. it is free for private use... 			[/I]:)

but in need to rubn ubuntu and i cant boot it up

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Boot windows, open explorer & right click on your c: drive properties.
On the tools tab, run error-checking (Check-now)

ok

---

### Post by pgp_protector on 2011-09-01
Also verify the these directories exist in windows


c:\ubuntu\disk\root.disk 
c:\ubuntu\disk\boot.

If I'm reading it correctly, these are where you Linux resides in wubi, if they're not their, windows may of cleaned them up.

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Boot windows, open explorer & right click on your c: drive properties.
On the tools tab, run error-checking (Check-now)

what does that do

---

### Post by Johnb0y on 2011-09-01
> **edwardpatch1 said:**
> but in need to rubn ubuntu and i cant boot it up

read it again... you dont have to be in ubuntu... it is an .exe file, boot into windows and run it there on the desktop...

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Also verify the these directories exist in windows


c:\ubuntu\disk\root.disk 
c:\ubuntu\disk\boot.

If I'm reading it correctly, these are where you Linux resides in wubi, if they're not their, windows may of cleaned them up.

there not there

---

### Post by edwardpatch1 on 2011-09-01
> **Johnb0y said:**
> [I]could try: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
 
this helped me with my xp/ubuntu issue... hope it helps you too :smile: 
 
p.s. it is free for private use... 			[/I]:)

u have to buy it

---

### Post by pgp_protector on 2011-09-01
You may want to look at this thread then for the Missing files.

[http://creekcodes.blogspot.com/2009/01/wubi-ubuntu-wont-boot-missing-rootdisk.html](http://creekcodes.blogspot.com/2009/01/wubi-ubuntu-wont-boot-missing-rootdisk.html)

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> u have to buy it

Bottom of the page is the link "[Download free for limited, non-commercial use]("http://neosmart.net/download.php?id=1")"

---

### Post by bcbc on 2011-09-01
I did a little write-up on this problem: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Bottom of the page is the link "[Download free for limited, non-commercial use]("http://neosmart.net/download.php?id=1")"

just downloading

---

### Post by saltmarshlamb on 2011-09-01
> **pgp_protector said:**
> Reading the guide for Wubi, the normal fixing of Grub might cause other issues.I know, I mentioned so earlier in the thread.
> **edwardpatch1 said:**
> u have to buy it

Go to the bottom of the page - there's a "Download free for limited, non-commercial use" option. When you get to the next page you can download without putting name in - just tried it :)

There's also a documentation link that might help you - though possibly it'll be a bit heavy to understand. 

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=96B8686ADD7ABF6E903B49359D58E131](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=96B8686ADD7ABF6E903B49359D58E131)

---

### Post by edwardpatch1 on 2011-09-01
> **bcbc said:**
> I did a little write-up on this problem: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

ok

---

### Post by edwardpatch1 on 2011-09-01
installed now what

---

### Post by BlinkinCat on 2011-09-01
> **Johnb0y said:**
> [I]could try: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) 
 
this helped me with my xp/ubuntu issue... hope it helps you too :smile: 
 
p.s. it is free for private use...             [/I]:)

Just out of curiosity Johnb0y - Was your installation Wubi or Dual boot?

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> Just out of curiosity Johnb0y - Was your installation Wubi or Dual boot?
wubi

---

### Post by edwardpatch1 on 2011-09-01
i have easy bcd what do i do now

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> i have easy bcd what do i do now

Given you say the c:\ubuntu\disk\root.disk files are missing you will probably need to follow this guide

as I don't think you can fix the boot loader if you've got no second OS to load to.

> **bcbc said:**
> I did a little write-up on this problem: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

---

### Post by edwardpatch1 on 2011-09-01
> **edwardpatch1 said:**
> but to much writing
check disc thing wont work

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> but to much writing

so one step at a time then :)

1) So what exactly happens when you try to run the Check Disk from the tools menu?
Does it return an error, give you a Blue Screen of Death, you're not allowed to run it, what?

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> so one step at a time then :)

1) So what exactly happens when you try to run the Check Disk from the tools menu?
Does it return an error, give you a Blue Screen of Death, you're not allowed to run it, what?
it says scheldule it

---

### Post by bcbc on 2011-09-01
easyBCD won't help - if you're getting a grub prompt then the bootloader is working as it should. If you're missing the root.disk then the expected result is the grub prompt.

So pgp_protector is absolutely correct on that. Finding the root.disk is the important thing

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> it says scheldule it

Then allow it to run on the next reboot & reboot and let it run.

---

### Post by edwardpatch1 on 2011-09-01
is there another way by getting the files i cant do this way :( and i need to get this html redy up tonight and i cant because its on my ubuntu

---

### Post by edwardpatch1 on 2011-09-01
it just comes up as disc checking canceled its not allowing it i did not press any button

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> it just comes up as disc checking canceled its not allowing it i did not press any button

Ok let's try the next step, do you know how to display Hidden Files?

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Ok let's try the next step, do you know how to display Hidden Files?

no can you help me out if u want i am not trying to force u but can u help me by controling my pc i dont mind if u say no but if u say yes or somthing tyhe software is team viewer but like i said im not trying to force u for helping me  i just sugested it because it might be a quicker way :)

---

### Post by pgp_protector on 2011-09-01
If Yes, look in your C: Drive for something LIKE C:\FOUND.0000 (the numbers may be different)

if No, to display Hidden files, open file explorer and click on your C: Drive so you see the root directory of the drive.

Under the menu "Organize" select "Folder and Search Options"
Select the Tab "View" and Under "Hidden Files & Folders" select "Show Hidden Files, Folders, And Drives" 

Click OK and refresh the view if needed.

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> no can you help me out if u want i am not trying to force u but can u help me by controling my pc i dont mind if u say no but if u say yes or somthing tyhe software is team viewer but like i said im not trying to force u for helping me  i just sugested it because it might be a quicker way :)

Work firewall won't let me.

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> If Yes, look in your C: Drive for something LIKE C:\FOUND.0000 (the numbers may be different)

if No, to display Hidden files, open file explorer and click on your C: Drive so you see the root directory of the drive.

Under the menu "Organize" select "Folder and Search Options"
Select the Tab "View" and Under "Hidden Files & Folders" select "Show Hidden Files, Folders, And Drives" 

Click OK and refresh the view if needed.
and then what

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> and then what
After enabling viewing hidden files do you see any directories called "C:\FOUND.0000 Or close to that (the numbers may be different)

> **edwardpatch1 said:**
> ???? works with ubuntu i had it and windows

My Work Firewall restricts how & what I can connect to, I can't connect to your computer from my end, not your end.

---

### Post by BlinkinCat on 2011-09-01
I don't know if Teamviewer can be downloaded to my Xubuntu?

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> after enabling viewing hidden files do you see any directories called "c:\found.0000 or close to that (the numbers may be different)
yes i can see the file


> 
[my work firewall restricts how & what i can connect to, i can't connect to your computer from my end, not your end.

??????

---

### Post by edwardpatch1 on 2011-09-01
> **BlinkinCat said:**
> I don't know if Teamviewer can be downloaded to my Xubuntu?

it can its free and its from teamviewer.com

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> yes i can see the file

Good we're almost done then :)

in that directory (found.0000) if you see a file called root.disk, move it to c:\ubuntu\disk\




> **edwardpatch1 said:**
> ??????
don't worry about it.

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Good we're almost done then :)

in that directory (found.0000) if you see a file called root.disk, move it to c:\ubuntu\disk\
no file called root.disc

---

### Post by edwardpatch1 on 2011-09-01
w8 i was mistaken there was no found00 file i miss seen it soz can u plz try to use team viewer it just gose through the firewall or what am i doing wrong

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> w8 i was mistaken there was no found00 file i miss seen it soz can u plz try to use team viewer it just gose through the firewall or what am i doing wrong

where their any directories called found. anything?

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> where their any directories called found. anything?
nope can we try teamviewer u dont know if it works inless u try

---

### Post by BlinkinCat on 2011-09-01
If you can't find it Edward, I doubt that I will - :(

---

### Post by bcbc on 2011-09-01
In Win7, found.000 didn't show up for me unless I turned off "hide protected OS files"  AS WELL AS "show hidden files".

To get there from a command prompt, hit start button, type cmd (don't press enter) look above to see CMD.EXE in the list. Right-click on it and Run as Administrator.

Then:
cd \found.000

If ubuntu is installed on D:, then first change to D: and then cd \found.000


If the \ubuntu\disks folder is missing, look for a folder:
DIR 
should output: dir0000.chk

Inside that should be root.disk and swap.disk
DIR dir0000.chk

---

### Post by edwardpatch1 on 2011-09-01
> **bcbc said:**
> In Win7, found.000 didn't show up for me unless I turned off "hide protected OS files"  AS WELL AS "show hidden files".

To get there from a command prompt, hit start button, type cmd (don't press enter) look above to see CMD.EXE in the list. Right-click on it and Run as Administrator.

Then:
cd \found.000

If ubuntu is installed on D:, then first change to D: and then cd \found.000


If the \ubuntu\disks folder is missing, look for a folder:
DIR 
should output: dir0000.chk

Inside that should be root.disk and swap.disk
DIR dir0000.chk
ok changed dir

---

### Post by madjr on 2011-09-01
i havent read all posts, but i hope these 9 pages are not just about reinstalling grub...

i mean this is a wubi install, it takes 5 seconds to delete and a few mins to reinstall...

or is there something am missing here?

---

### Post by edwardpatch1 on 2011-09-01
> **bcbc said:**
> .

Then:
cd \found.000

If ubuntu is installed on D:, then first change to D: and then cd \found.000


If the \ubuntu\disks folder is missing, look for a folder:
DIR 
should output: dir0000.chk

Inside that should be root.disk and swap.disk
DIR dir0000.chk
dont get this bit

---

### Post by edwardpatch1 on 2011-09-01
> **madjr said:**
> i havent read all posts, but i hope these 9 pages are not just about reinstalling grub...

i mean this is a wubi install, it takes 5 seconds to delete and a few mins to reinstall...

or is there something am missing here?

ur missing somthiong i dont wanna lose all my ubuntu files and my .html weebsite :(

---

### Post by bcbc on 2011-09-01
> **madjr said:**
> i hope these 9 pages are not just about reinstalling grub...

i mean this is a wubi install, it takes 5 seconds to delete and a few mins to reinstall...
Yes, you can delete it easily. But it won't help you get your data back.

---

### Post by edwardpatch1 on 2011-09-01
> **bcbc said:**
> Yes, you can delete it easily. But it won't help you get your data back.

so im not deleteing it so can i fix it

---

### Post by bcbc on 2011-09-01
> **edwardpatch1 said:**
> dont get this bit

I showed the commands and the expected output here: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Just look at the bottom of that page

---

### Post by edwardpatch1 on 2011-09-01
> **bcbc said:**
> I showed the commands and the expected output here: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Just look at the bottom of that page

wont help

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> ok changed dir

What's is in that directory.

> **bcbc said:**
> I showed the commands and the expected output here: [http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)

Just look at the bottom of that page
I don't think they're use to any form of command line interface.

---

### Post by edwardpatch1 on 2011-09-01
i have discinternals linux reader that will let me veiw ubuntu files

---

### Post by edwardpatch1 on 2011-09-01
i opened found.000 through disc internals and min that folder theerenis file0000.chk
file0001.chk
Move file thats it

---

### Post by bcbc on 2011-09-01
How big are those files?

---

### Post by edwardpatch1 on 2011-09-01
the file0000.chk is 0.15 kb
the file0001.chk is 0.00kb
the move file is 0.00kb

---

### Post by edwardpatch1 on 2011-09-01
disc internals only searchs for recoverable files on ubuntu

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> what do i need to do and fast

looking at the files sizes the ubuntu files appear to be missing completely.  You may be down to a reinstall needed.

---

### Post by bcbc on 2011-09-01
Those files aren't big enough to be anything of consequence.

I think you need to figure out why chkdsk isn't running. And try again. Also from Ubuntu, list the files in xxx/ubuntu/disks directory (where xxx is the mountpoint)

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> looking at the files sizes the ubuntu files appear to be missing completely.  You may be down to a reinstall needed.

so i lost my files :(

---

### Post by edwardpatch1 on 2011-09-01
> **bcbc said:**
> Those files aren't big enough to be anything of consequence.

I think you need to figure out why chkdsk isn't running. And try again. Also from Ubuntu, list the files in xxx/ubuntu/disks directory (where xxx is the mountpoint)
so how do i do that disk inrernals is not allowed to edit files

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> looking at the files sizes the ubuntu files appear to be missing completely.  You may be down to a reinstall needed.

so how do i get my files back after reinstalling

---

### Post by edwardpatch1 on 2011-09-01
now it says 
Try (hd0,0): NTFS5:error: "prefix" is not set
error: no such devix /ubuntu/disksroot.disk
then goes to GNU GRUB

---

### Post by Johnb0y on 2011-09-01
> **BlinkinCat said:**
> Just out of curiosity Johnb0y - Was your installation Wubi or Dual boot?

sorry for delay, working, anyway...wubi, thought i was being a quick, smart a$$ and thought i could do a "quick" dual boot, but nope so i ran that and it worked epic first time...

---

### Post by Johnb0y on 2011-09-01
basic steps: [http://www.ehow.com/how_4900122_use-easybcd-windows-xp.html](http://www.ehow.com/how_4900122_use-easybcd-windows-xp.html)

more steps: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

and similar here: [http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)

p.s. yes i know they refer to different OS's, but if you read and understand, they are pretty much the same... :)

---

### Post by pgp_protector on 2011-09-01
> **edwardpatch1 said:**
> so how do i get my files back after reinstalling

Out of my pay grade (Sorry I don't know)
I'm hoping others can help you out, but it looks like you've lost your boot image and maybe other info that was in the ubuntu directory.

---

### Post by edwardpatch1 on 2011-09-01
> **pgp_protector said:**
> Out of my pay grade (Sorry I don't know)
I'm hoping others can help you out, but it looks like you've lost your boot image and maybe other info that was in the ubuntu directory.
wso can i get them back by repairing it

---

### Post by edwardpatch1 on 2011-09-01
> **Johnb0y said:**
> basic steps: [http://www.ehow.com/how_4900122_use-easybcd-windows-xp.html](http://www.ehow.com/how_4900122_use-easybcd-windows-xp.html)

more steps: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

and similar here: [http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm](http://apcmag.com/how_to_dual_boot_vista_and_xp_with_vista_installed_first__the_stepbystep_guide.htm)

p.s. yes i know they refer to different OS's, but if you read and understand, they are pretty much the same... :)
ok i will check when i get on my pc tomoz

---

### Post by madjr on 2011-09-01
> **edwardpatch1 said:**
> ur missing somthiong i dont wanna lose all my ubuntu files and my .html weebsite :(

ok, i see, i hope you can save your files!

wubi is really to just quickly test ubuntu for a few days see if things work, because you can never trust a virtual file system inside windows.

this is why i prefer to install ubuntu to **its own real partition**, that way if windows corrupts things for any reason it wont affect your ubuntu install. And getting yo your files and saving then using a live-cd is as easy as 123...

---

### Post by westie457 on 2011-09-01
Hi.

Have read all the way through this thread and come to the conclusion all is not lost.

My hat is off to everyone involved, you have all shown a lot of patience and understanding to a 12 years old boy.

On my dual-booting system I have a program installed in Windows that allows reading of and writing to an EXTy partition. The EXT can be 2,3 or 4.

The program is called Ext2Fsd and is available from this link. [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html). It is free as well.

Also I found this old thread that says 'Ext2Fsd can read and write to the Wubi file system.

[http://ubuntuforums.org/archive/index.php/t-960062.html]("http://ubuntuforums.org/archive/index.php/t-960062.html")

---

### Post by bcbc on 2011-09-01
You need to run chkdsk. If the root.disk file is missing and there is nothing in \found.000 then it's the only way to recover it. But whether it's recoverable or not depends on the level of corruption.

If it [keeps cancelling the chkdsk]("http://support.microsoft.com/kb/975778"), then boot to a repair prompt and run it from there. Or review that link - maybe it applies.

It's entirely possible that the root.disk is gone, but it's best to try everything possible to recover before giving up.

---

### Post by edwardpatch1 on 2011-09-02
> **bcbc said:**
> You need to run chkdsk. If the root.disk file is missing and there is nothing in \found.000 then it's the only way to recover it. But whether it's recoverable or not depends on the level of corruption.

If it [keeps cancelling the chkdsk]("http://support.microsoft.com/kb/975778"), then boot to a repair prompt and run it from there. Or review that link - maybe it applies.

It's entirely possible that the root.disk is gone, but it's best to try everything possible to recover before giving up.

i cant recover it tho

---

### Post by edwardpatch1 on 2011-09-02
> **westie457 said:**
> Hi.

Have read all the way through this thread and come to the conclusion all is not lost.

My hat is off to everyone involved, you have all shown a lot of patience and understanding to a 12 years old boy.

On my dual-booting system I have a program installed in Windows that allows reading of and writing to an EXTy partition. The EXT can be 2,3 or 4.

The program is called Ext2Fsd and is available from this link. [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html). It is free as well.

Also I found this old thread that says 'Ext2Fsd can read and write to the Wubi file system.

[http://ubuntuforums.org/archive/index.php/t-960062.html]("http://ubuntuforums.org/archive/index.php/t-960062.html")
its only helps windows not ubuntu

---

### Post by westie457 on 2011-09-02
> **edwardpatch1 said:**
> is it for windows???

Yes it is for Windows.

---

### Post by edwardpatch1 on 2011-09-02
> **westie457 said:**
> Yes it is for Windows.

it only helps windows tho not ubuntu

---

### Post by edwardpatch1 on 2011-09-02
im going on holiday today and  going back home after a week

---

### Post by edwardpatch1 on 2011-09-02
it wont work with windows 7 anyway

---

### Post by westie457 on 2011-09-02
It does work with Windows 7. I have it installed on my system.

---

### Post by edwardpatch1 on 2011-09-02
> **westie457 said:**
> It does work with Windows 7. I have it installed on my system.

can u give direct link

---

### Post by westie457 on 2011-09-02
Link to the download page. [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by edwardpatch1 on 2011-09-02
> **westie457 said:**
> Link to the download page. [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

wont work on that it says not for windows 7

---

### Post by madjr on 2011-09-02
> **edwardpatch1 said:**
> wont work on that it says not for windows 7

if it works for vista it "should" for 7. Here's how:

[http://www.networkedmediatank.com/showthread.php?tid=23220](http://www.networkedmediatank.com/showthread.php?tid=23220)

[http://www.robertbeal.com/528/mount-ext3-in-windows-7-x64](http://www.robertbeal.com/528/mount-ext3-in-windows-7-x64)

[http://forum.xda-developers.com/showthread.php?t=567577](http://forum.xda-developers.com/showthread.php?t=567577)

a little searching (google) usually gives you the answer if in doubt ;)

---

### Post by edwardpatch1 on 2011-09-06
hi sorry for no replies im on holiday and i just found WIFI and i also forgot to say i have other computers on WUBI and they have a grub.cfg file now can i copty and paste them and put them on my USB stick and can i put them in through my windows

---

### Post by edwardpatch1 on 2011-09-08
can somone help me fast please

---

### Post by saltmarshlamb on 2011-09-08
> **edwardpatch1 said:**
> hi sorry for no replies im on holiday and i just found WIFI and i also forgot to say i have other computers on WUBI and they have a grub.cfg file now can i copty and paste them and put them on my USB stick and can i put them in through my windows

having another grub file from another pc is not going to be of any help if you've not got the wubi root disk file

_if_ that file is missing then I would think that you're stuck and will need to reinstall

if there was things that you needed in the wubi then this at least will be a wakeup call to deal with suitable backup plans

if you do go down the reinstall route then I would suggest you forget wubi and go for a clean dualboot install

---

### Post by edwardpatch1 on 2011-09-08
> **saltmarshlamb said:**
> having another grub file from another pc is not going to be of any help if you've not got the wubi root disk file

_if_ that file is missing then I would think that you're stuck and will need to reinstall

if there was things that you needed in the wubi then this at least will be a wakeup call to deal with suitable backup plans

if you do go down the reinstall route then I would suggest you forget wubi and go for a clean dualboot install
i can boot itg on my disc now is that gd????/

---

### Post by saltmarshlamb on 2011-09-08
If you can boot it then I'd guess that the threads solved then :)

---

### Post by madjr on 2011-09-08
> **saltmarshlamb said:**
> having another grub file from another pc is not going to be of any help if you've not got the wubi root disk file

_if_ that file is missing then I would think that you're stuck and will need to reinstall

if there was things that you needed in the wubi then this at least will be a wakeup call to deal with suitable backup plans

if you do go down the reinstall route then I would suggest you forget wubi and go for a clean dualboot install

i do a agree with this.

your wubi install is pretty ruined, you're trying to revive a dead person here (which we all know, once a person dies you cant revive.. ).

anyway did you try installing the fs-driver in windows 7? That's probably your last chance.

---

### Post by edwardpatch1 on 2011-09-08
> 
anyway did you try installing the fs-driver in windows 7? That's probably your last chance.

how do i do that

---

### Post by edwardpatch1 on 2011-09-08
> **saltmarshlamb said:**
> if you can boot it then i'd guess that the threads solved then :)

i cant boot my ubuntu

---

### Post by saltmarshlamb on 2011-09-08
> **edwardpatch1 said:**
> i cant boot my ubuntuThen what does this previous post mean?

> **edwardpatch1 said:**
> i can boot itg on my disc now is that gd????/


If the root file is not there I would suggest that you'll not be getting anywhere.

---

### Post by madjr on 2011-09-08
> **edwardpatch1 said:**
> how do i do that


ok, so i guess you didnt read my post:

[http://ubuntuforums.org/showpost.php?p=11211618&postcount=118](http://ubuntuforums.org/showpost.php?p=11211618&postcount=118)

---

