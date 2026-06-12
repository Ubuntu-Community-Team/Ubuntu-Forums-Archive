---
title: "PC will not boot"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by DJnRF on 2010-04-14
I have a dual boot system with XP Pro on the primary HD, and Ubuntu on 
a slave drive. I had deleted some files and evidently deleted something 
that prevents my PC from booting on a restart. It gets to "Grub Loading" 
but then stops and shows "Grub Rescue" on the screen. How do I do a 
'Grub Rescue'? 
 
Normally, the PC would load Grub, then take me to a list of files to select 
to load. This is where I would either choose XP or the Ubuntu drive. 
After my selection it would open the drive I selected. 
 
I am unable to get into Safe Mode, or get to a command prompt. I am 
not able to access my floppy drive, or the CD drive. If I use the 
XP setup floppies I do get into them, but would then have to go to 
a full XP install on the CD, which without the ability to install without 
format of my drive to lose everything, I do not wish to do. (I really 
hate everything MS has done to things since Win3.11) 
 
Are there any boot discs for the MBR for XP, or Ubuntu that can 
be used to restore my system? What can I do?

---

### Post by undecim on 2010-04-14
2 questions:

Did you install ubuntu with Wubi or from the Live CD?

What files did you delete?

---

### Post by DJnRF on 2010-04-14
> **undecim said:**
> 2 questions:
 
Did you install ubuntu with Wubi or from the Live CD?
 
What files did you delete?
 
 
 
I installed Ubuntu with the free CD sent. It is the 
9.10 version. 
 
As to the files, all were within the XP drive. Some 
were files I had saved of my work in publishing, and 
document formats, and some were image files, but 
some were also what I thought were unused MS 
updates. Something then must have not been 
'unused'.  
 
I have gotten a message box on a couple of tries 
to boot that informed me that the "infochk program" 
was missing, and that the boot process was terminated. 
It would then loop back to the restart. 
 
In all instances of attempt to boot to any HD OS it 
gets to "Grub loading", and then will go no further.

---

### Post by pavel989 on 2010-04-14
boot the live cd, mount the drive somehwere in /media, or just mount it and run "mount | tail -1"  (i think thats the command)
then do sudo sudo grub-install --root-directory=/media/your_ubuntu_install /dev/sda

the ubuntu install is so that u can install it into the /boot dir, and /dev/sda should be the partition ubuntu is installed in

---

### Post by DJnRF on 2010-04-14
> **pavel989 said:**
> boot the live cd, mount the drive somehwere in /media, or just mount it and run "mount | tail -1" (i think thats the command)
then do sudo sudo grub-install --root-directory=/media/your_ubuntu_install /dev/sda
 
the ubuntu install is so that u can install it into the /boot dir, and /dev/sda should be the partition ubuntu is installed in
 
 
 
Well, I seem to have goofed with my info. I had stated the msg was "infochk" when 
in reality it is "Autochk program is missing".  
 
When I do a restart with the XP disc in the CD tray I get nothing. When I put in 
the Ubuntu disc it will load to the screen to select the OS I wish to boot. If I 
select XP I will get to a WinXP screen, but then a popup message informs me that 
the Autochk program is missing, and the PC then loops back to a restart.  
 
If I select the drive with Ubuntu it does fully load and open.  
 
I noticed that on my primary drive with XP it also shows as having Ubuntu on 
that drive. That is probably where I had originally tried to install Ubuntu 8.04, 
but couldn't get it to install. That is when I used a second HD to install 9.10. 
 
Now, since Ubuntu changes the primary drive loading to the "Grub" loader, I 
believe that something in the XP MBR, however it was changed to work with 
either XP, or Ubuntu, has been deleted so as to not allow XP to load.  
 
Any other ideas?  I still cannot get the PC to recognize the LAN connection 
to get that PC online, and I have only borrowed this one for a couple of days.

---

### Post by oldfred on 2010-04-14
So we can see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

If it is just windows issues you may want to use the XP repair disk to run chkdsk and repairs on the XP partition.
XP repair disk
[http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)

[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by DJnRF on 2010-04-14
> **oldfred said:**
> So we can see where everything is at:
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.
 
If it is just windows issues you may want to use the XP repair disk to run chkdsk and repairs on the XP partition.
XP repair disk
[http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip](http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip)
 
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)
 
 
 
Just a quick update.  I had to leave for a while. 
 
I read over everything here including the link on the boot info. 
I even downloaded the XP repair disc on this machine, and put 
it on a CD. This machine does not have a floppy drive so I could 
not make a bootable floppy that is available in that program. 
 
I also checked the MS help desk page, and the other resource 
page. 
 
So far; ........ 
Nothing works!  
 
I can boot into the Ubuntu drive. After using that CD I can 
get to the drive selection screen to open Ubuntu on the 
slave drive. I cannot open the XP, though. 
 
Since the primary drive has XP any attempt to use the CD  
repair disk, or the XP disc fails. When attempting to boot 
the only program that will open is with the setup discs on 
the six floppies. Nothing in the OS choices menu, or the 
F8 key selections will work as everything always leads to 
a popup that says the Autochk program is not found, and 
it is shutting down. That automatically leads me back to 
the restart to boot. 
 
Nothing so far has allowed me to gain any access to the 
CD drive, or a command prompt. 
 
It also seems that since my cable modem, and the card 
were installed in Windows it will not alloow me to get 
Ubuntlu online. I even tried a manual setting instead of 
automatic connection. Nada!  
 
It seems that unless there is some way that commands 
from within Ubuntu can correct the problem on the 
primary drive with the non-working XP, or get that 
drive to recognize, and load chkdisk, or some CD for 
Windows, or some floppies that are actually boot discs 
for XP instead of setup discs that none of the methods 
thus far will correct the problem. I would first have to 
overcome the lack of the ability to load a CD, or get 
a command prompt. 
 
Any and all ideas, suggestions, etc would sure be 
appreciated. (I only have this machine for another 
day, or two at the most.)  
 
I will keep everyone updated with any progress.

---

### Post by oldfred on 2010-04-14
These are Vista or & repair disks and will not fix boot problems for XP but supposedly will run the chkdsk program for XP.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

Are you connecting directly to your cable modem or thru a router?

---

### Post by DJnRF on 2010-04-15
> **oldfred said:**
> These are Vista or & repair disks and will not fix boot problems for XP but supposedly will run the chkdsk program for XP.
 
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.
 
Are you connecting directly to your cable modem or thru a router?
 
 
Well, since my PC is an older unit I had to buy a full version of XP Pro to upgrade 
from the Win98 that was on it previously. When I got XP Vista, and Win7 were not 
even yet advertised to come around. Of course that means that I don't have a 
copy of the discs you mention. 
 
I have tried to connect to both of the above links, but neither link can be 
found. After several attempts by using different approaches I figure that 
the links are no longer valid.  
 
I connect directly through a cable modem.

---

### Post by m4tic on 2010-04-15
I read the first post, apologies.
If you want to reinstall grub do:
Boot from your "Ubuntu live cd" and not windows or a floppy
(ALL OPERATIONS DONE IN TERMINAL ->APPLICATIONS>ACCESSORIES>TERMINAL)
(where x is your "Ubuntu installation" device letter and X is partition number)
 
First you have to know your drive information
This command will list your partitions and ubuntu should be on an EXT4/EXT3 type
```
sudo fdisk -l
```
```
sudo e2fsck -f -y -v /dev/sdx
```
 
```
[FONT=Courier New]sudo mount /dev/sdx# /mnt[/FONT]
[FONT=Courier New]sudo mount --bind /dev /mnt/dev[/FONT]
sudo mount --bind /proc /mnt/proc
[FONT=Courier New]sudo chroot /mnt[/FONT]
[FONT=Courier New]#grub-install --recheck /dev/sdx[/FONT]
 
[FONT=Courier New]#reboot[/FONT] 

```
 
Then when it boots, go to your ubuntu partition and enter in terminal ```
sudo update-grub2
```
 
After the last command. It probably include all OS's on the other device

---

### Post by DJnRF on 2010-04-15
> **m4tic said:**
> I read the first post, apologies.
If you want to reinstall grub do:
Boot from your "Ubuntu live cd" and not windows or a floppy
(ALL OPERATIONS DONE IN TERMINAL ->APPLICATIONS>ACCESSORIES>TERMINAL)
(where x is your "Ubuntu installation" device letter and X is partition number)
 
First you have to know your drive information
This command will list your partitions and ubuntu should be on an EXT4/EXT3 type
```
sudo fdisk -l
```
```
sudo e2fsck -f -y -v /dev/sdx
```
 
```
[FONT=Courier New]sudo mount /dev/sdx# /mnt[/FONT]
[FONT=Courier New]sudo mount --bind /dev /mnt/dev[/FONT]
sudo mount --bind /proc /mnt/proc
[FONT=Courier New]sudo chroot /mnt[/FONT]
[FONT=Courier New]#grub-install --recheck /dev/sdx[/FONT]
 
[FONT=Courier New]#reboot[/FONT] 

```
 
Then when it boots, go to your ubuntu partition and enter in terminal ```
sudo update-grub2
```
 
After the last command. It probably include all OS's on the other device
 
 
 
[SIZE=2]&#12288;[/SIZE]
[SIZE=2]&#12288;[/SIZE]
[FONT=Verdana]I cannot understand the reason to reinstall Grub at this point. [/FONT]
[FONT=Verdana]Let me explain. When the problem first started where I could [/FONT]
[FONT=Verdana]not restart WinXP the boot process stopped at the point where [/FONT]
[FONT=Verdana]it showed Grub Loading. I would get some message to the [/FONT]
[FONT=Verdana]effect that it couldn't find something or other, and I would [/FONT]
[FONT=Verdana]get just a cursor. Nothing would do more than to just advance [/FONT]
[FONT=Verdana]the cursor to another line, and any commands would just be [/FONT]
[FONT=Verdana]shown as invalid, and give me another cursor with a blank line. [/FONT]
[FONT=Verdana]&#12288;[/FONT]
[FONT=Verdana]After the suggestion to use the Ubuntu CD things changed [/FONT]
[FONT=Verdana]some. Restarting with the Ubuntu CD did get Grub to load [/FONT]
[FONT=Verdana]fully, and take me to the selection screen where I could select [/FONT]
[FONT=Verdana]the Hard Drive of the particular OS that I wanted to boot into. [/FONT]
[FONT=Verdana]That screen showed the Ubuntu HD, and the XP HD. When I [/FONT]
[FONT=Verdana]select the Ubuntu drive, Ubuntu does open, and all programs [/FONT]
[FONT=Verdana]function. The only thing is that it does not connect to my [/FONT]
[FONT=Verdana]modem. I even tried to set up with a manual connection to no [/FONT]
[FONT=Verdana]avail. Manual does no more than the automatic as it had been [/FONT]
[FONT=Verdana]set to do. I expect that the reason for this is that the XP [/FONT]
[FONT=Verdana]drive is the original, primary drive where all the PC hardware [/FONT]
[FONT=Verdana]had been set up to work. This would include the Ethernet [/FONT]
[FONT=Verdana]card, and my modem. Since XP will not load, the setup for [/FONT]
[FONT=Verdana]the network interface won't either. [/FONT]
[FONT=Verdana]&#12288;[/FONT]
[FONT=Verdana]Now, when I boot to XP it will take me to the screen where [/FONT]
[FONT=Verdana]it shows XP starting, but before it can start I get a blue, [/FONT]
[FONT=Verdana]popup box that says; "Autochk program not found. Shutting [/FONT]
[FONT=Verdana]down." The PC then goes right back to a restart all over [/FONT]
[FONT=Verdana]again. [/FONT]
[FONT=Verdana]&#12288;[/FONT]
[FONT=Verdana]So, Ubuntu appears to work just as it should, but it just [/FONT]
[FONT=Verdana]cannot get connection to the Internet. Another thing that [/FONT]
[FONT=Verdana]I have not been able to do is to get Ubuntu to recognize, [/FONT]
[FONT=Verdana]and use the floppy drive. The suggestions I got previously [/FONT]
[FONT=Verdana]have not helped. I do use the floppy drive a lot. Many of [/FONT]
[FONT=Verdana]the things I do need this, and the CD/DVD is not as [/FONT]
[FONT=Verdana]useful at those times. When I can finally get a new PC [/FONT]
[FONT=Verdana]I will install a floppy as most new ones do not have them. [/FONT]
[FONT=Verdana]&#12288;[/FONT]
[FONT=Verdana]I seem to have many problems in the understanding of this [/FONT]
[FONT=Verdana]whole, new language used with the Linux system. When I first [/FONT]
[FONT=Verdana]started on computers back in the early 90's (about 92) I got the [/FONT]
[FONT=Verdana]DOS books, studied them, and learned what I needed for most [/FONT]
[FONT=Verdana]everything. Of course, that was back when we had real control [/FONT]
[FONT=Verdana]over our computers with the DOS program. (today that control [/FONT]
[FONT=Verdana]has been totally lost due to the fact that DOS was placed [/FONT]
[FONT=Verdana]inside the OS preventing full control over the OS. I would [/FONT]
[FONT=Verdana]dearly love to use my 6.2 DOS on my PC without an OS [/FONT]
[FONT=Verdana]having the Disc Operating System contained within the [/FONT]
[FONT=Verdana]OS of my choice.) With the old DOS system I would be [/FONT]
[FONT=Verdana]able to boot into that alone, and find any problem in an [/FONT]
[FONT=Verdana]OS to be able to make needed repairs, restoration, change, [/FONT]
[FONT=Verdana]etc. (When I can afford a new PC I will install DOS first, [/FONT]
[FONT=Verdana]then whatever OS I would want.) [/FONT]
[FONT=Verdana]&#12288;[/FONT]
[FONT=Verdana]Now, in thinking, could I remove the primary drive with [/FONT]
[FONT=Verdana]XP, change the CMOS, and HD detection in my PC to [/FONT]
[FONT=Verdana]show only the Ubuntu drive, then set it up as the only [/FONT]
[FONT=Verdana]drive to see, and connect with all the PC hardware without [/FONT]
[FONT=Verdana]losing any of the files I already have on it? All of the [/FONT]
[FONT=Verdana]work I have already in Ubuntu is copies from what I [/FONT]
[FONT=Verdana]have in Windows. I got Ubuntu set up as a dual boot, [/FONT]
[FONT=Verdana]slave of the Windows drive so that I could learn it, and [/FONT]
[FONT=Verdana]get it set to replace Windows eventually. I have been [/FONT]
[FONT=Verdana]seeking programs that are compatible with my Windows [/FONT]
[FONT=Verdana]programs, but designed for a Linux OS. So far I have [/FONT]
[FONT=Verdana]not been able to find a publishing program to compare [/FONT]
[FONT=Verdana]to my Serif, but Open Office is a reasonable facimile of [/FONT]
[FONT=Verdana]the MS Office, and MS Word. It is just taking a while to [/FONT]
[FONT=Verdana]learn the new language, and find the right programs. [/FONT]
[FONT=Verdana]&#12288;[/FONT]
[FONT=Verdana]I hope this info helps to clarify my problem. I really would [/FONT]
[FONT=Verdana]like to find some good floppy repair discs for XP. The [/FONT]
[FONT=Verdana]usual way is to use the original OS installation CD to [/FONT]
[FONT=Verdana]do this, however, this method does not work as the [/FONT]
[FONT=Verdana]PC won't boot to that XP CD even though I have set [/FONT]
[FONT=Verdana]the PC to boot to the CD, then C drive, then A. It does [/FONT]
[FONT=Verdana]see a disc put into the A drive, though. It even sees [/FONT]
[FONT=Verdana]a non-system disc when just any floppy is inserted. [/FONT]
[FONT=Verdana]It does not see any other CD other than the Ubuntu [/FONT]
[FONT=Verdana]CD. [/FONT]

---

### Post by oldfred on 2010-04-15
I have stopped using floppies. I use the USB keys all the time now. Even as CD's for ISO booting.

Microsoft XP boot disk floppy
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

You still can install a DOS to your system. I think it is freeDOS.
[http://www.freedos.org/](http://www.freedos.org/)
I have seen where some just create a partition for it.

You can also change hard drives around. If you have everything using UUIDs it will work without issue, but often something are referred by drive, partition and they have to be updated. Typically grub & fstab are the places to review drive settings.

---

### Post by DJnRF on 2010-04-15
[QUOTE=oldfred;9127104]I have stopped using floppies. I use the USB keys all the time now. Even as CD's for ISO booting.
 
Microsoft XP boot disk floppy
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)
 
Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)
 
You still can install a DOS to your system. I think it is freeDOS.
[http://www.freedos.org/](http://www.freedos.org/)
I have seen where some just create a partition for it.
 
You can also change hard drives around. If you have everything using UUIDs it will work without issue, but often something are referred by drive, partition and they have to be updated. Typically grub & fstab are the places to review drive settings.[/QUOTE 
 
 
 
I will get the one for the Linux programs, but already have the six discs 
for the XP setup. That is the only way I can access my CD drive for XP. 
The main problem with these discs on my PC is that they only will allow 
for a complete, new installation. The recovery console feature does not 
work for my installation. The only reason I can find for this is that the 
recovery console method must not have SP 2, or higher installed. I have 
SP 3 now. MS never updated these discs to accomodate that feature. 
The clue in the MS info on how to use these discs tells the story in 
one sentence: 
"**Step 3: Start your computer by using the first Setup **
**disk to begin _a new Windows XP installation_**" 
 
That is exactly what mine does. In the 'old' days a person would have 
a choice listed to reinstall Windows without formatting. This would 
preserve all the other files/folders that a person had placed on the 
drive. MS has taken that option away from people. After all, if a 
person could do this to prolong the life of his OS, MS would not be 
able to develop, and sell as many new ones. Why would a person 
want to buy a new system when they can make the old one last 
so long, and keep it 'refreshed'. 
You might want to read the following article: 
[http://blogs.zdnet.com/Bott/?p=1925&tag=col1;post-1925](http://blogs.zdnet.com/Bott/?p=1925&tag=col1;post-1925) 
 
This is exactly what I have been saying to people for years. 
 
I'll be trying some of these things on my PC now to see if I can 
get it working online with Ubuntu so that I have something to 
continue working with after I lose my borrowed one tomorrow. 
 
I will try to keep everyone updated.

---

### Post by DJnRF on 2010-04-16
I have finally come up with an answer! 
 
I haven't tried it yet because it requires that I make a floppy 
disc for the 'fix'. As this, a borrowed, newer type machine 
does not have a floppy drive, and since mine that needs 
the repair can only recognize the floppy with the problem, 
I am going to have to get an external A-drive to apply the 
fix. (I intend to always keep such a drive as there are 
many times, and problems that still require one.) 
 
I think everyone should read about this problem as it does 
very mluch affect Linux, dual boot users. (note this in the 
paragraph four up from the end of the article.) 
 
The article can be found in this blog: 
[http://www.techspot.com/vb/topic7746.html](http://www.techspot.com/vb/topic7746.html) 
 
I did manage with the help of the DLG floppy from 
Western Digital to get into chkdsk. As this program 
attempts to 'recover' what it sees that should be 
(according to MS), it did not correct the problem, but 
it sure did eliminate all needed to boot into Ubuntu. 
(Just another example of how MS does not allow a 
person to have actual control over their PC.) Back 
when DOS had to be installed first to be able to 
install an OS a person could actually have gone into 
DOS (completely outside of any OS), found the 
problem, and fixed it. 
 
I hope to have a final to all this soon. I will let you all 
know. A bit of knowledge is always good. (My problem 
is that this tired, getting very old brain just doesn't 
absorb new things very quickly, or well.)

---

### Post by zer010 on 2010-04-16
IMHO, I would copy all personal files etc to a flash drive. Make a list of wanted apps. Then start fresh with formatted clean installs of xp  1st (if wanted) and ubuntu last.

---

### Post by DJnRF on 2010-04-16
> **zer010 said:**
> IMHO, I would copy all personal files etc to a flash drive. Make a list of wanted apps. Then start fresh with formatted clean installs of xp 1st (if wanted) and ubuntu last.
 
 
 
That seems nice, BUT ...... 
I don't have a flash drive and on my SS income, can hardly afford the 
price of a floppy disc. 
 
Also, I have to try to restore XP with all the existing files intact. I am 
a writer, and have many files saved that would lose the last month of 
work. (And, that is a whole lot of work taking up almost 4GB.)  As soon 
as I can afford to do so I intend to get a new tape drive. My older one 
will not work with XP, and I have found a tape drive to be much better 
than CD's, or DVD's for backups. I can also restore from a tape drive 
outside of Windows if I load a DOS program. Windows can be completely 
restored with a tape drive program for DOS (which I have). 
 
I like clean, formatted installs, but not when I have so much to lose. 
It would take me two to three months to redo everything done over 
the past month. That is a lot of lesson plans, lectures, and chapters 
I have to 'pull' from my mind, and retype. I guess it would be easy 
for one that doesn't really use a PC for much other than games, 
entertainment, and email.

---

### Post by oldfred on 2010-04-16
I took a look at your link. It seemed to have several suggestions but one was changing the partition type. You can easily do that in linux with sfdisk. But sfdisk can be dangerous because it can change anything related to partitions. 

This will show partitions and the ID is the type:
```
sudo sfdisk -l
```

This lists all the various types including those discussed:
```
sfdisk -L
```

changing types:
[http://ubuntuforums.org/showthread.php?t=1433002](http://ubuntuforums.org/showthread.php?t=1433002)

---

### Post by DJnRF on 2010-04-17
> **oldfred said:**
> I took a look at your link. It seemed to have several suggestions but one was changing the partition type. You can easily do that in linux with sfdisk. But sfdisk can be dangerous because it can change anything related to partitions. 
 
This will show partitions and the ID is the type:
```
sudo sfdisk -l
```
 
This lists all the various types including those discussed:
```
sfdisk -L
```
 
changing types:
[http://ubuntuforums.org/showthread.php?t=1433002](http://ubuntuforums.org/showthread.php?t=1433002)
 
 
 
Since I found that the problem actually is generated by Windows, and 
was able to get the system into chkdsk on the Windows drive, I was 
also able to get into the XP repair program. With the attempts to fix 
the boot process I allowed it to be changed back to the original 
configuration. This move (rather dumb move on my part) also removed 
any of the boot record that is required to be able to boot into 
Ubuntu. Now that means that I don't even have the offline use of 
Ubuntu until I first fix the problem with the partioning in Windows. 
 
I have downloaded the PTEDIT program but I can't make the bootable 
floppy to make the repairs on XP until I get to a PC with a floppy 
drive, amd WinXP. I made a bootable repair floppy on my Win98 
PC, and ran it to see if it would work. It does work just fine, so 
all I need to to make a repair floppy with the boot record for XP. 
 
Once I get that done I should be able to get it working, and online. 
The next course of action will be to set up Ubuntu as a secondary 
master instead of a slave drive. 
 
I tried to install a spare floppy drive in this borrowed PC, but it 
does not have a place to mount the drive, nor a proper connector 
on the M-board. If my other daughter doesn't have a floppy drive 
on her PC, I will have to break down and buy an external drive. 
I'll find out tomorrow, and keep all posted on my progress.

---

### Post by oldfred on 2010-04-17
Just an update the links in Post #9 are working again. They did not work for me either 2 days ago, but yesterday and today I was able to connect.

---

### Post by DJnRF on 2010-04-17
> **oldfred said:**
> Just an update the links in Post #9 are working again. They did not work for me either 2 days ago, but yesterday and today I was able to connect.
 
 
 
Yes, I got them to work last night when I checked. 
 
Both my daughters that live locally have new PC's without 
floppy drives. One daughter is mounting one, but not yet 
finished doing so. Besides, the new don't have XP. 
 
I checked on a new external floppy this morning, but when 
I saw the price locally I decided that I'll just make one later. 
In the meantime I found an old HD that was large enough so 
that I could format it, and install XP on that one. That will 
give me the bootable floppy I need. It should be done here 
soon now. Another half hour, or so. Then I will get my PC 
hooked up again to install the floppy to see if that will work 
the intended manner to fix my problem. I should know in 
another couple of hours, or so. (That is if I don't have to 
run errands for either of the daughters as is normal on the 
weekends.)

---

### Post by DJnRF on 2010-05-04
Finally I have gotten another PC working, but still no 
progress on my primary. 

I did remove the Ubuntu hard drive from the PC with 
the problem, and put it in this one to see if it would work. 
I figured that if the problem existed on the XP drive, it 
might not have affected the Ubuntu drive that was 
connected as a slave in the dual boot system. Wrong! 

In trying to boot this drive as a master/single on this 
PC I get the message 'Invalid drive partition'.  

Now, is there a way that I can correct this without 
destroying the data, or the Ubuntu OS on this drive? 
I had installed the Ubuntu CD on the drive separately 
from the XP drive, and only set it as a slave afterward.

---

### Post by oldfred on 2010-05-04
When you plug & unplug drives any reference not using UUIDs get messed up. Both drives think they are drive 0 and obviously one is not.

WinXP has drive reference in boot.ini. Grub & fstab have UUIDs or sdax or hdx,y references. You can individually correct these but it is not alwasys easy.

If you just want to boot windows. You can install a basic windows boot loader from Ubuntu (if liveCD /dev/sda may be different) :
Restore basic windows boot loader 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To review where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by DJnRF on 2010-05-04
> **oldfred said:**
> When you plug & unplug drives any reference not using UUIDs get messed up. Both drives think they are drive 0 and obviously one is not.

WinXP has drive reference in boot.ini. Grub & fstab have UUIDs or sdax or hdx,y references. You can individually correct these but it is not alwasys easy.

If you just want to boot windows. You can install a basic windows boot loader from Ubuntu (if liveCD /dev/sda may be different) :
Restore basic windows boot loader 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To review where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.


All well, and good, but...... what or how does one do this 
when neither drive, together, separately, and/or independently 
can boot into any place to do anything?  

When both drives were in the same PC, where both XP, 
and Ubuntu were installed on their respective drives as 
a single drive, then the Ubuntu drive was working as a 
stand-alone drive just as was the XP drive, and finally 
both were installed in the same PC with the Ubuntu drive 
being listed as Slave, and the XP as Master, which made 
the dual boot system, and now neither will boot up in the 
only PC I now have available, which can only handle one 
drive installations, just how could I do what these two 
suggestions require?  

I am not sure just what caused the problem, but it seems 
to exist separately in both drives even when they are 
installed in this single-drive PC. (It is a pre-2000 machine 
that has been 'worked over' by several before I got it.)  
So, basically what I have to 'fix' with either drive is a 
drive that will not get beyond a message in the attempt 
to boot. From that point on I am not able to do anything 
other than to restart just to go through the same regimen 
all over again. I only have one PC working, and it will 
not support more than the one hard drive at a time. I have 
already tried that several times with other, smaller drives 
that I set up with XP on this same machine. It just does 
not support two drives at once.

---

### Post by oldfred on 2010-05-04
If you are having issue with both drives are they connected correctly?

IDE drives were/are not the easiest to get correct. Older ones used 40 conductor cable and required the jumpers to be correct for master/slave.

Newer one's set jumpers to cable select and use a newer 80 conductor cable that the color of the connector determines master or slave. If you are using a 40 conductor cable in cable select it can cause problems.

[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)

---

### Post by DJnRF on 2010-05-06
> **oldfred said:**
> If you are having issue with both drives are they connected correctly?

IDE drives were/are not the easiest to get correct. Older ones used 40 conductor cable and required the jumpers to be correct for master/slave.

Newer one's set jumpers to cable select and use a newer 80 conductor cable that the color of the connector determines master or slave. If you are using a 40 conductor cable in cable select it can cause problems.

[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)


Yes, they are correct. It is easy to place the jumpers properly, 
and even insure the bios is correct. In placing them in this old 
PC, as I can only have one drive in at a time, each I put in is 
set to single, and they are recognized by the bios. Both drives, 
the XP one, and the Ubuntu one are the same make/model/size 
drive, so getting them right is easy. The jumper settings for 
these is just the choice of single, master, or slave. I have tried 
both with the jumper settings in both the single, and master 
positions to be sure, but I get the very same hangup on this 
machine as I do on the PC where they were both installed. 

Neither of these drives have the cable select setting, and both 
are the older type. They are not actually 'old' drives as both 
were purchased in the past two years. The Ubuntu drive one 
was just purchased last year in August. both are Western Digital. 

I did even manage to get WD support to talk to me on the 
problem to see if they had any input. I ended up wasting my 
time as well as theirs for over an hour as they were not able 
to give any help.  

I have wanted to try the UBCD4Win method to see if that 
can help me get into the drive to copy the files so that I 
don't lose them, or have to pay the big bucks to have the 
drives mirrored. However, in making that method work 
requires that I copy my XP CD into a file that I can use 
in the UBCD4Win program to force the drive to boot to 
copy the files. It might not fix the problem, but it should 
get me in to copy them all. 

The problem is that my CD is old, and some of the 
files are corrupted so that they don't copy. I even tried 
the Unstoppable Copier that is recommended to try to 
get all the bad files to copy, but it doesn't work on 
all that are bad. I finally found a new retail version 
that a guy has. A daughter knew him, and talked to 
him, then had me call and talk to him. He is going to 
send me that one to replace mine. He said he got it 
when a place went out of business, and never used it. 
He said he now has Vista so he no longer needs the 
XP Pro retail one he has. It has never been used, and 
is still in the original box. At least I will have a good 
disc again, and two MS Keys. 

The whole problem is perplexing, to say the least.

---

### Post by oldfred on 2010-05-06
If they are only two years old the cable should be a cable select. 
Is the cable 80 conductor with three different color plugs? If so you should set jumpers on hard drive to cable select. Master is the end and the one near the end is slave.

The old 40 conductor cables all have the same color connector.

---

### Post by DJnRF on 2010-05-07
> **oldfred said:**
> If they are only two years old the cable should be a cable select. 
Is the cable 80 conductor with three different color plugs? If so you should set jumpers on hard drive to cable select. Master is the end and the one near the end is slave.

The old 40 conductor cables all have the same color connector.


The drives are only that old, but they are the older style 
I have used for years. They are the WD 800JB drives. 
The PC is a very old HP, and only has the 40 conductor 
cable. 

I mistakenly stated that the drives do not have a cable 
select on them. They do have, but the cable nor the PC 
can work with cable select. Due to this I only 'see' the 
drive as having settings for single, master, and slave. 

On this model drive the Master is center, the slave is next 
to the end, and the cable select jumper setting is on 
the end. A single drive setting would be no jumper.

---

