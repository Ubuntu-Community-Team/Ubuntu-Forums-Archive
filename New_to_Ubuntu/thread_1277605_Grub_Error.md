---
title: "Grub Error"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by Splushka17 on 2009-09-28
First time installation of Ubuntu 9.04 parallel to my existing Windows XP. Windows XP sits on a SATA drive, installed Ubuntu on another empty IDE drive
When attempted to boot was getting continuous errors ".....Stage 1_5  Grub Error 17"
After reading through many threads and trying terminal commands to fix Grub (no success), ran a suggested script that produced "Results.tx" file which showed my ssytem configuration, where Linux is sitting at sdd1.
Tried the "sudo fdisk...." sequence of command that supposedly fixes the Grub - still same problem
At reboot, tried to change the bios boot priority to rearrange the order of my hard drives to at least get the XP to boot - same error 17
Tried to download the Supergrub CD Rom, but as I am currently running off the Live CD, it does not allow me to remove the Live CD in order to burn the Supergrub CDRom (??)
Evnetually, tried a asuggestion at one of the threads to use the Windows Live CD, use "Recover" option and run "Fixmbr" command to restore my Windows MBR (hoping to remove the Grub and at least boot back into XP, leaving the Ubuntu installation to a brighter day). After doing that still getting Grub error, but now it is "Grub Error 22"

At the end of my line...Please please Help!!??:confused:
Thanks to all!!!

---

### Post by chriskin on 2009-09-28
> **Splushka17 said:**
> First time installation of Ubuntu 9.04 parallel to my existing Windows XP. Windows XP sits on a SATA drive, installed Ubuntu on another empty IDE drive
When attempted to boot was getting continuous errors ".....Stage 1_5  Grub Error 17"
After reading through many threads and trying terminal commands to fix Grub (no success), ran a suggested script that produced "Results.tx" file which showed my ssytem configuration, where Linux is sitting at sdd1.
Tried the "sudo fdisk...." sequence of command that supposedly fixes the Grub - still same problem
At reboot, tried to change the bios boot priority to rearrange the order of my hard drives to at least get the XP to boot - same error 17
Tried to download the Supergrub CD Rom, but as I am currently running off the Live CD, it does not allow me to remove the Live CD in order to burn the Supergrub CDRom (??)
Evnetually, tried a asuggestion at one of the threads to use the Windows Live CD, use "Recover" option and run "Fixmbr" command to restore my Windows MBR (hoping to remove the Grub and at least boot back into XP, leaving the Ubuntu installation to a brighter day). After doing that still getting Grub error, but now it is "Grub Error 22"

At the end of my line...Please please Help!!??:confused:
Thanks to all!!!

have you tried reinstalling grub through the live cd?
it's like three commands or less

all you have to do is this : 
boot to the live cd, open the terminal
write "sudo grub" and enter
then "find /boot/grub/stage1"
it will spit a number, let's say (hd0,1)
then you go 
"root (hd0,1)"
"setup (hd0)"
and then write "quit"

restart and grub will be ok, linux will boot etc
now if windows isn't there, that's fixable as well  in a line or two , just make sure that the boot priority is on linux

---

### Post by Splushka17 on 2009-09-28
> **chriskin said:**
> have you tried reinstalling grub through the live cd?
it's like three commands or less

all you have to do is this : 
boot to the live cd, open the terminal
write "sudo grub" and enter
then "find /boot/grub/stage1"
it will spit a number, let's say (hd0,1)
then you go 
"root (hd0,1)"
"setup (hd0)"
and then write "quit"

restart and grub will be ok, linux will boot etc
now if windows isn't there, that's fixable as well  in a line or two , just make sure that the boot priority is on linux

Thanks! 
Tried similar before and didn't work, but I need a clarification now:

the number it spat is (hd3,1). On the following commands should I put
"root (hd3,1)" AND
"setup (hd3)" OR "setup (hd0)" ??

Thaks again!

---

### Post by chriskin on 2009-09-28
> **Splushka17 said:**
> Thanks! 
Tried similar before and didn't work, but I need a clarification now:

the number it spat is (hd3,1). On the following commands should I put
"root (hd3,1)" AND
"setup (hd3)" OR "setup (hd0)" ??

Thaks again!

if the boot priority is on the 4th drive, then go for hd3 :)
where you have the boot priority is something i don't know, but going for hd3 now and setting the priority to it is a good idea

---

### Post by Splushka17 on 2009-09-28
Ok, tried the complete sequence now, when I enter 
"setup (hd3)"
I get a message:
"Error 17: Cannot mount selected partition"

...??

---

### Post by Darkwing-Duck on 2009-09-28
Try this for fixing your MBR and grub. Hopefully it will work for you.
 
[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by Splushka17 on 2009-09-28
Thanks!!

Been there in my research earlier today...went through all the steps, when entering the command
"sudo grub-install --root-directory=/media/root /dev/sda --recheck"
I wold first get a quick "Can not find ...something" and then it would go to the expected 
"Installation finished. No error reported.[FONT=monospace]
[/FONT]This is the contents....."

Then rebooting gives me the same Error 22 problem

Appreciate your help, any more suggestions?

---

### Post by LewRockwell on 2009-09-28
> **Splushka17 said:**
> Ok, tried the complete sequence now, when I enter 
"setup (hd3)"
I get a message:
"Error 17: Cannot mount selected partition"

...??

"root (hd3,1)" tells grub where the menu.lst file is located(hd3,1 is hard drive 4, partition 2)

"setup (hd0)" tells grub which hard drive is set as the boot drive so grub can properly modify the Master Boot Record of that drive

hope that helps

.

---

### Post by Splushka17 on 2009-09-28
> **LewRockwell said:**
> "root (hd3,1)" tells grub where the menu.lst file is located(hd3,1 is hard drive 4, partition 2)

"setup (hd0)" tells grub which hard drive is set as the boot drive so grub can properly modify the Master Boot Record of that drive

hope that helps

.
Now if I enter either
"Setup (hd3)" or
"Setup (hd0)"
I am getting the same error
"Error 17: Cannot mount selected partition"

I am starting to suspect that my system (which is still booted off the Live Ubuntu CD) is not seeing the drive where Windows is residing - and that is the same drive where the MBR is supposed to be, right?

Any suggestions?

---

### Post by LewRockwell on 2009-09-28
since you're using the LiveCD you should be able to open a partition editor(gparted) session and give us some screenshots of what you're working with

when you visit the partition editor check to see if any of the listings show the "keys" or "locks" engaged

if that is the case then the drive is mounted and grub won't be able to work on it

.

---

### Post by Splushka17 on 2009-09-28
> **LewRockwell said:**
> since you're using the LiveCD you should be able to open a partition editor(gparted) session and give us some screenshots of what you're working with

when you visit the partition editor check to see if any of the listings show the "keys" or "locks" engaged

if that is the case then the drive is mounted and grub won't be able to work on it

.

Ok, done the gparted, here are the screen shots (sorry, I'm newbie, so couldn't insert them had to attach)

As you can see, plenty of keys, but no locks

dev/sdb1 is where my Windows XP lives (I suppose the Windows MBR is there too..?)
dev/sdd1 is where I installed the Ubuntu

Both have the "keys"...What can I do now?

BTW, thanks to all who are helping, being new to Linux I am really basking in the generosity of the community. Gotta go to sleep (work tomorrow, it's way past midnight here), but will be back tomorrow evening to try all the suggestions.

---

### Post by LewRockwell on 2009-09-28
> **LewRockwell said:**
> "root (hd3,1)" tells grub where the menu.lst file is located(hd3,1 is hard drive 4, partition 2)

"setup (hd0)" tells grub which hard drive is set as the boot drive so grub can properly modify the Master Boot Record of that drive

hope that helps

.

previously we directed you to use "root (hd3,1)" which was incorrect

after seeing your partition editor screenshots it is apparent that you should use "root (hd3,0)" which tells grub your menu.lst file is on drive 4, partition 1


also, the keys show that the partition is mounted and locked so it can't be altered

the LiveCD mounts ntfs partitions to give the new prospective user access to what is assumed to be their windows partitions and the data within them

obviously this then might require manually unmounting those partitions using either terminal commands or nautilus gui

.

---

### Post by Splushka17 on 2009-09-29
> **LewRockwell said:**
> previously we directed you to use "root (hd3,1)" which was incorrect

after seeing your partition editor screenshots it is apparent that you should use "root (hd3,0)" which tells grub your menu.lst file is on drive 4, partition 1


also, the keys show that the partition is mounted and locked so it can't be altered

the LiveCD mounts ntfs partitions to give the new prospective user access to what is assumed to be their windows partitions and the data within them

obviously this then might require manually unmounting those partitions using either terminal commands or nautilus gui

.

Ok, thanks.

SO do you suggest I re-run the 
"sudo grub"
..
..

Sequence with "root (h3,0) instead of root (hd3,1)? How/What am i to do then with unmounting the drives?

---

### Post by LewRockwell on 2009-09-29
> **Splushka17 said:**
> SO do you suggest I re-run the "sudo grub" Sequence with "root (h3,0) instead of root (hd3,1)?yes, rerun the sequence with the proper information

> **Splushka17 said:**
> How/What am i to do then with unmounting the drives?We are hoping that after you rerun the grub function then you won't need to worry about all the unmounting

.

---

### Post by Splushka17 on 2009-09-30
> **LewRockwell said:**
> yes, rerun the sequence with the proper information

We are hoping that after you rerun the grub function then you won't need to worry about all the unmounting

.

Ok, I ran the sequence of commands yesterday ending with "[COLOR=Blue]setup (hd3)[/COLOR]", as I entered "[COLOR=Blue]root (hd3,0)[/COLOR]" before it, and when I rebooted I got the same "**_Grub Error 22_**"
Now I entered the same sequence again but I entered "[COLOR=Blue]setup (hd0)[/COLOR]" instead. Below is the response I got in the terminal window:

[COLOR=Blue]Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd3,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.[/COLOR]

Will try ot reboot now and see how it works out...fingers crossed

---

### Post by ConXtionS on 2009-09-30
I'm crossing my fingers, toes, and other goodies for ya bro....
 
 
Good Luck

---

### Post by Splushka17 on 2009-10-01
> **Splushka17 said:**
> Ok, I ran the sequence of commands yesterday ending with "[COLOR=Blue]setup (hd3)[/COLOR]", as I entered "[COLOR=Blue]root (hd3,0)[/COLOR]" before it, and when I rebooted I got the same "**_Grub Error 22_**"
Now I entered the same sequence again but I entered "[COLOR=Blue]setup (hd0)[/COLOR]" instead. Below is the response I got in the terminal window:

[COLOR=Blue]Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd3,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.[/COLOR]

Will try ot reboot now and see how it works out...fingers crossed

Nope...:(
Before the command sequence I was getting error 22, now after I used the commands "[COLOR=Blue]root (hd3,0)[/COLOR]" followed by "[COLOR=Blue]setup (hd0)[/COLOR]" (using "setup (hd3)" bfore didn't work) I rebooted and got the message
[I][B]"Grub loading  stage 1.5.

Grub loading, please wait...

Error17"[/B][/I] 

and everything stops

Desperation rapidly setting in!!!](*,)

Anyone thinks trying to re-install the whole Linux from the distribution DVD may solve the problem?? Any other suggestions?

Thanks

---

### Post by Cebonet on 2009-10-01
Maybe you should change some settings in bios/cmos.

---

### Post by Splushka17 on 2009-10-01
> **Cebonet said:**
> Maybe you should change some settings in bios/cmos.


I tried to change the boot order of my hard drives, didn't help much. I suppose Grub focuses on the disks he wants to use regardless. I even tried to physically disconnect the drive where I installed Linux hoping that the system would boot to windows, but Grub kept giving me the same error..

But that was before I ran the command sequence above. Any specific suggestions?

---

### Post by LewRockwell on 2009-10-01
[http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17](http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17)

.

---

### Post by LewRockwell on 2009-10-01
> **Splushka17 said:**
> I tried to change the boot order of my hard drives, didn't help much. I suppose Grub focuses on the disks he wants to use regardless. I even tried to physically disconnect the drive where I installed Linux hoping that the system would boot to windows, but Grub kept giving me the same error..

But that was before I ran the command sequence above. Any specific suggestions?

does your BIOS report all your drives correctly?

honestly, we use single partitions for our operating systems and then use other partitions on other storage drives and also some optical media for our storage(some short-term and some long-term)

We also manually administer our grubs and menu.lst files

you can see what we've done with a couple of machines by checking out these threads:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.

---

### Post by Splushka17 on 2009-10-01
> **LewRockwell said:**
> [http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17](http://www.iknowkungfoo.com/blog/index.cfm/2008/6/16/Stupid-solution-for-Grub-error-17)

.

Hi LewRockwell,

I followed the link, then another link to the original location of the proposed solution by ***mbwardle*** at [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9), a total of 14 steps

As per my previous post and screen caps from partition editor, my Linux is sitting at  dev/sdd1 (is it right to assume that my Linux root is at the same place?)

Step 5) of the solution instructs to run the command [COLOR=Blue]"mount /dev/sdd1/ubuntu"[/COLOR], (where /dev/sdd1 is where my Linux is installed) upon which I got the error

***mount: can't find /dev/sdd1/ubuntu in /etc/fstab or /etc/mtab***

I am puzzled, as my partition editor clearly sees the /dev/sdd1, and also the Nautilus sees the drive clarely and can list the files on it.

Any advice on what can I do next?

Thanks

---

### Post by LewRockwell on 2009-10-01
if your BIOS isn't reporting all your drives then that is the problem

.

---

### Post by Splushka17 on 2009-10-01
> **LewRockwell said:**
> does your BIOS report all your drives correctly?

honestly, we use single partitions for our operating systems and then use other partitions on other storage drives and also some optical media for our storage(some short-term and some long-term)

We also manually administer our grubs and menu.lst files

you can see what we've done with a couple of machines by checking out these threads:

[http://ubuntuforums.org/showthread.php?t=1222961](http://ubuntuforums.org/showthread.php?t=1222961)

[http://ubuntuforums.org/showthread.php?t=1252042](http://ubuntuforums.org/showthread.php?t=1252042)

.


BIOS seems to report the 4 drives are there (I don't know what else can I get from the BIOS screen), boot order is CD ROM first, followed by Linux HDD then Windows HDD. When we started a couple of days ago, during one of the reboots I changed the order of booting drives to make the Windows drive higher than the Kinux drive, but that didn't seem to make any difference

I am also trying a similar approach whereby my Windows sits on dev/sdb1 (sdb2 and sdb3 are used for some file storage an internet downloads under Windows). The physical drive holding sdb1, sdb2 and sdb3 is a 300GB SATA
I am attempting to install Linux on a separate drive (IDE, 120GB) which my partition editor sees as /dev/sdd, and I have a two other physical drives that partition editor sees as sda and sdc which I use for some media files and otehr storage. 

So, same logic - a drive per operating system. Or do you suggest I should keep both systems on differnet partitions of the same drive?

I think it is a problem of Grub seeing drives in a different order (different map??) from BIOS, but I am not knowledgeabel enough to solve it

---

### Post by LewRockwell on 2009-10-01
Ok, now we're getting somewhere!

> **Splushka17 said:**
> BIOS seems to report the 4 drives are there (I don't know what else can I get from the BIOS screen), boot order is CD ROM first, followed by Linux HDD then Windows HDD. When we started a couple of days ago, during one of the reboots I changed the order of booting drives to make the Windows drive higher than the Kinux drive, but that didn't seem to make any difference

I am also trying a similar approach whereby my Windows sits on dev/sdb1 (sdb2 and sdb3 are used for some file storage an internet downloads under Windows). The physical drive holding sdb1, sdb2 and sdb3 is a 300GB SATA
I am attempting to install Linux on a separate drive (IDE, 120GB) which my partition editor sees as /dev/sdd, and I have a two other physical drives that partition editor sees as sda and sdc which I use for some media files and otehr storage. 

So, same logic - a drive per operating system. Or do you suggest I should keep both systems on differnet partitions of the same drive?

I think it is a problem of Grub seeing drives in a different order (different map??) from BIOS, but I am not knowledgeabel enough to solve it

you have got to get your boot order AND your grub settings in synchronization

so....

set your windows hard drive to boot right after your CD drive is checked

then use the earlier settings that we decided were correct for your grub```
root (hd3,0)
setup (hd0)
```

hopefully that will do it

.

---

### Post by LewRockwell on 2009-10-01
and...just to clarify once again...


root (hd3,0) tells grub to go to hard drive number four, first partition...to find the /boot/grub/menu.lst file


setup (hd0) tells grub setup to put the primary part of the grub bootloader into the Master Boot Record of hard drive number one


remember...grub uses "hd" for "hard drive" regardless of what your operating system uses(hd versus sd, for example)

and...grub starts counting from 0... "0"... the number zero... the keyboard map character zero

hopefully that helps

.

---

### Post by Splushka17 on 2009-10-01
> **LewRockwell said:**
> and...just to clarify once again...


root (hd3,0) tells grub to go to hard drive number four, first partition...to find the /boot/grub/menu.lst file


setup (hd0) tells grub setup to put the primary part of the grub bootloader into the Master Boot Record of hard drive number one


remember...grub uses "hd" for "hard drive" regardless of what your operating system uses(hd versus sd, for example)

and...grub starts counting from 0... "0"... the number zero... the keyboard map character zero

hopefully that helps

.

Thanks, will try it shortly

What you mean by drive number four is in what count/order? is it the order that shows in the partition editor, which calls the drives sda, sdb, sdc and sdd correspondoing to drives 1,2,3 and 4?

Appreciate you bearing with me...If it doesn't work, I'll be off-line for a couple of weeks while I travel and leave my desktop behind, but I'll reconnect soon as I'm back mid-Oct either to send a big thank you to all who helped or to ask for more support...

---

### Post by LewRockwell on 2009-10-01
> **Splushka17 said:**
> What you mean by drive number four is in what count/order? is it the order that shows in the partition editor, which calls the drives sda, sdb, sdc and sdd correspondoing to drives 1,2,3 and 4?

grub counts drives from ZERO...so hd0, hd1, hd2, hd3

other programs count from ONE...so hda, hdb, hdc, hdd

or in the case of "sd"...so sda, sdb, sdc, sdd


same goes for partitions as well:

grub counts partitions from ZERO...so (hd0,0), (hd0,1), (hd0,2), (hd0,3)

other programs count from ONE...so hda1, hda2, hda3, hda4

or in the case of "sd"...so sda1, sda2, sda3, sda4



hope that helps

.

---

### Post by presence1960 on 2009-10-01
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by LewRockwell on 2009-10-01
> **Splushka17 said:**
> I'll be off-line for a couple of weeks while I travel and leave my desktop behind, but I'll reconnect soon as I'm back mid-Oct either to send a big thank you to all who helped or to ask for more support...


OP bailed...thread dead for now...

.

---

### Post by Splushka17 on 2009-10-02
> **LewRockwell said:**
> OP bailed...thread dead for now...

.

I didn't bail, dude, I had to travel on business and I am on another continent now with my tiny Netbook, the Linux-affected desktop waiting at home. Still tremendously grateful for all the help, though...

BTW, I tried the last advice (changing boot order in BIOS to make Linux drive come on AFTER the Windows drive) and run the sequence of commands as per your latest instructions.

What happened is the system booted straight into my old Windows XP, without any sight of Grub at all.

Had to leave it at that, as was heading for the airport in 2 hours...Will revive the thread post October 15th..Thinking to re-install the whole Ubuntu from scratch  - let me know what you think whenever you have the time...

Thanks to all for support, talk again in 2 weeks.

---

### Post by presence1960 on 2009-10-02
> **Splushka17 said:**
> I didn't bail, dude, I had to travel on business and I am on another continent now with my tiny Netbook, the Linux-affected desktop waiting at home. Still tremendously grateful for all the help, though...

BTW, I tried the last advice (changing boot order in BIOS to make Linux drive come on AFTER the Windows drive) and run the sequence of commands as per your latest instructions.

What happened is the system booted straight into my old Windows XP, without any sight of Grub at all.

Had to leave it at that, as was heading for the airport in 2 hours...Will revive the thread post October 15th..Thinking to re-install the whole Ubuntu from scratch  - let me know what you think whenever you have the time...

Thanks to all for support, talk again in 2 weeks.

I read your post and was aware you did not bail, that's why I posted to run that Boot Info Script. It will tell us more about your setup & boot process than the rest of the posts on this thread combined. When you get back run the script and post the contents of the RESULTS.txt file generated on the desktop. In all probability you will not have to reinstall. Have a great trip.

---

### Post by baltadt on 2009-10-03
You might also want to try this.
enter your windows disk and select the repair option. select operating system click next. Open command prompt and type this EXACTLY   " Bootrec.exe/FixMbr " (upper/lower case does count) hit enter and restart. This worked for me.

---

