---
title: "Partition manager doesnot detect windows !"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by firoz3321 on 2010-01-28
I'm new to LINUX and i recently received the UBUNTU cd 
delivered home. 

I tried to install UBUNTU but it detects the HARD DISK as one 250Gb partition. I actually have 6 partitions. and i have Windows XP installed on one of the partitions. When i boot from the UBUNTU CD it does not detect the Windows partition.

I tried to search the net but i could not get the expected solutions. I'm eager to use the UBUNTU, please help me.

---

### Post by J V on 2010-01-28
Could you open a terminal and post the output of this please:
```
fdisk -l
```

---

### Post by firoz3321 on 2010-01-28
now i'm on XP. and from The live CD i'm not able to connect to NET as i'm totally new the LINUX.

---

### Post by chewearn on 2010-01-28
1.
Boot into the Live CD.

2.
Open a Terminal:
Top Left Menu > Application > Accessories > Terminal

Type this into the Terminal window:
```
sudo fdisk -l > out.txt
```3.
Plug a USB thumbdrive into the PC.
 Wait a few seconds, and the thumbdrive should showed up in the desktop as an icon.
 
4.
Open the Home folder.
Top Left Menu > Places > Home

5.
Drag-drop the file "out.txt" from Home folder to the thumbdrive's icon on the desktop.

6.
Right-click on the thumbdrive icon, select "Unmount volume" (or something like that).  And unplug the thumbdrive.

7.
Now, go to your WinXP PC and copy-paste content of "out.txt" to this forum thread.

---

### Post by firoz3321 on 2010-01-28
I took screen shots and saved to one of my partitions. but the Terminal window screen shot says invalid image.

I'll have to try again.

is it "fdisk -l" or "fdisk -1" i mean "Alphabet L" or "number 1"

Typing "fdisk -l" shows nothing. but typing "fdisk" shows some information.

EDIT:

I'm really sorry, i just typed "fdisk -l" instead of "sudo fdisk -l"


I also tried this:
> Give this a try:

1) If you have more than one hdd in your system, disconnect all but the drive you are trying to install Karmic on
2) Boot into live session using the 9.10 Live CD (without installing)
3) Open Terminal and run "sudo apt-get remove dmraid" (without quotes)
4) Close Terminal and run the installer by double-clicking on its icon

See if that will get the installer to recognize your hard drive. If this works for you, you may have to uninstall dmraid again 

after installing GParted, which installs dmraid as part of its package if it's not already installed.


from one of the posts from this forum, but no use :(

---

### Post by firoz3321 on 2010-01-28
Any body there ?

---

### Post by chewearn on 2010-01-28
> **firoz3321 said:**
> is it "fdisk -l" or "fdisk -1" i mean "Alphabet L" or "number 1"

Typing "fdisk -l" shows nothing. but typing "fdisk" shows some information.

EDIT:

I'm really sorry, i just typed "fdisk -l" instead of "sudo fdisk -l"



"sudo fdisk -l" with alphabet "el".

---

### Post by firoz3321 on 2010-01-28
Ok, thank you. i'll post the txt file soon now. and did you see the attachments ? all the partitions are visible in the "COMPUTER" but i cant detect the partition while installing. i want to install linux in "D" drive.

---

### Post by chewearn on 2010-01-28
> **firoz3321 said:**
> Ok, thank you. i'll post the txt file soon now. and did you see the attachments ? all the partitions are visible in the "COMPUTER" but i cant detect the partition while installing. i want to install linux in "D" drive.

Yes, I tried to understand your problem, but I am not sure what's going on at this time.

---

### Post by firoz3321 on 2010-01-28
I copied and pasted in to a text file. it got all scrambled. i tried to line it up but dont think its lined up properly.

does this info help or do i need to boot again ? :(

> 
To run a command as administrator (user "root"), 
use "sudo <command>".

See "man sudo_root" for details.


ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 
63 sectors/track, 
32301 cylinders

Units = cylinders of 15120 * 512 = 7741440 bytes


Disk identifier: 0x889e3246

   Device Boot      Start         End      Blocks   Id  
System
/dev/sda1   *   		        1        5418    40960048+  	   7  
HPFS/NTFS
/dev/sda2        	    5419        8128    20486656           7  
HPFS/NTFS
/dev/sda3        	    8128       18964    81920000  	   7  
HPFS/NTFS
/dev/sda4          	    18964       32302   100836352 	   f  
W95 Ext'd (LBA)
/dev/sda5           18964       24382    40960000 	   7  
HPFS/NTFS
/dev/sda6       	    24383       27767    25590568+	   7  
HPFS/NTFS
/dev/sda7      	    27768       32302    34273280 	   7  
HPFS/NTFS
ubuntu@ubuntu:~$ 


---

### Post by clhsharky on 2010-01-28
HI 

Which distribution of Ubuntu are you trying to use? 8.04 or 9.10 I hope. Lucid testing does have installation problems with the partition manager on the live cd. Lucid testing should only be used by  experienced users willing to deal with issues.


Sharky

---

### Post by firoz3321 on 2010-01-28
> Disk identifier: 0x889e3246

   

Device Boot      Start         End      Blocks        Id     System
 
/dev/sda1   *        1          5418    40960048+     7      HPFS/NTFS
/dev/sda2      	    5419        8128    20486656      7      HPFS/NTFS
/dev/sda3      	    8128        18964    81920000     7      HPFS/NTFS
/dev/sda4      	    18964       32302   100836352     f      W95 Ext'd (LBA)
/dev/sda5           18964       24382    40960000     7      HPFS/NTFS
/dev/sda6      	    24383       27767    25590568+    7      HPFS/NTFS
/dev/sda7      	    27768       32302    34273280     7      HPFS/NTFS



I'm using "9.10" UBUNTU. 

"Lucid testing" i dont know what you mean by "Lucid testing".
This is my first struggle to install LINUX. i tried many times before, but never succeeded. i just gave up every time. but this time i want to install it.

---

### Post by firoz3321 on 2010-01-28
Any body there ?

---

### Post by firoz3321 on 2010-01-28
Guys i'm still holding the CD in my hand !

---

### Post by chewearn on 2010-01-28
Sorry, I have to leave my desk for an hour or two.  If you want instant help, I can only suggest using #ubuntu IRC channel.

---

### Post by firoz3321 on 2010-01-28
ubuntu IRC channel ??
i dont know what it is

---

### Post by Paddy Landau on 2010-01-28
> **firoz3321 said:**
> Any body there ?
Please be patient! We do this in our spare time as volunteers. Eleven minutes isn't enough time to wait.

-------

I don't know the answer to your problem, but I'm going to give you a bit of background, so that you can better understand what might be happening.

-------

Windows names the partitions C:, D:, E: etc. I'll come back to this in a few paragraphs...

-------

In Linux, you will see the "real" names of the drives and partitions. The drives are called (usually) sda, sdb, sdc and so forth. You will see them listed under "dev" (devices), hence /dev/sda, /dev/sdb, /dev/sdc, etc.

These reflect the real, physical drives. If you have exactly one drive (which your screenshots indicate), then it's called sda (or /dev/sda). If you then add a flash drive, it will be named /dev/sdb. Add an MP3 player and it becomes /dev/sdc.

(The names depend on the order that you add them, so tomorrow, if you add them in a different order, they will have different names. Your internal hard drives always have the same names because your computer sees them first every time you boot.)

Every drive needs to be partitioned into one or more partitions. These are numbered. Hence, if your drive (/dev/sda) has seven partitions, they will be numbered /dev/sda1, /dev/sda2, /dev/sda3, etc.

If your flash drive has exactly one partition (which is usual), it will be /dev/sdb1.

N.B. It is possible to have the partition numbers out of order, e.g. sda1, sda2, sda5, sda6, sda7, sda10, sda9. It is **perfectly OK** if this is the case.

-------

There is one more thing. If you look up *primary*, *extended* and *logical* partitions (try this forum or Wikipedia), you'll find that you should have at least one extended partition -- in your case it's sda4. Partitions sda1, sda2 and sda3 are *primary* partitions. sda4 is an *extended* partition, which is simply a holder for subsequent partitions. sda5, sda6 and sda7 are *logical* partitions that are held inside sda4.

(This set-up exists because, for historical reasons, a drive cannot have more than four partitions. The extended partition structure allows you to have as many partitions as you like.)

Thus, for *practical* purposes, sda4 is not considered a partition in its own right that you can use; instead, it's a holder for the other partitions.

-------
 
 Windows names the partitions as it receives them. So, it should name your partitions as follows:
sda1 = C:
sda2 = D:
sda3 = E:
sda4 (no drive because it's an extended partition)
sda5 = F:
sda6 = G:
sda7 = H:
There could be something, e.g. a driver, that changes this ordering or hides some of your partitions.

If you add a flash drive, its partition will become drive I:.

And so on.

-------

So, I suspect -- but cannot be sure -- that your D: drive is in fact /dev/sda2 on your hard drive.

On the Live CD, go to Places and look what's on /dev/sda2 to double-check whether it is what you believe is drive D:.

Let us know what you find.

---

### Post by chewearn on 2010-01-28
I'm not sure why a list of partitions is not showing up in the Ubuntu installer.  But your current set-up is quite complicated and it might be advisable to not rely on the Ubuntu installer partitioning tool.

I would suggest this instead:

Use Windows build-in disk manager (or any Windows third party tool)  to rearrange the partitions, and create one contiguous free (and unformatted) space at the end of the hard drive (inside the extended partition /dev/sda4).

Then, when coming back to Ubuntu Installer, it should offer an option that reads "Install onto the largest free contiguous space".  (not exact wording, but something like that).  Choose this option, and Ubuntu should go into the free unformatted space.

---

### Post by firoz3321 on 2010-01-28
I just now HAD to install VISTA.
 
I was on LIVE CD trying to see what "Paddy Landau" was saying. And i accendentally clicked on something i shouldn't have.
 
EVERY PARTITION IN MY HDD is GONE !!
 
DAMN Linux !
 
All my data is gone ! :(
 
I think installing UBUNTU now would be easy, as i was worrying that my data might be lost if i chose some wrong settings, but now that my DATA is gone already, trying would not harm me any more !!

---

### Post by steindor2 on 2010-01-28
nevermind

---

### Post by Paddy Landau on 2010-01-28
> **firoz3321 said:**
> I just now HAD to install VISTA.
 
I was on LIVE CD trying to see what "Paddy Landau" was saying. And i accendentally clicked on something i shouldn't have.
 
EVERY PARTITION IN MY HDD is GONE !!
I'm not quite sure what Vista and the Ubuntu Live CD have to do with each other.

What did you "click" on the Live CD to delete all your partitions? It's straightforward, but not that straightforward! Did you use the Partition Manager (GParted)?

If yours is a factory-restore Vista CD (as opposed to a shop-bought native Vista CD), then it most likely deletes everything off your hard drive before installing Vista (that's my experience, anyway). Is that the case with you?

Or have I misunderstood, and you installed Vista *after* you deleted the partitions?

---

### Post by firoz3321 on 2010-01-28
> **Paddy Landau said:**
>  
Or have I misunderstood, and you installed Vista *after* you deleted the partitions?
 
Yes i used GeParted ( or some thing like that ) 
 
And I installed Vista *after* I Got deleted my partitions.

---

### Post by Paddy Landau on 2010-01-28
I'm sorry that you had such problems.

GParted normally gives a big warning about applying the changes; I can only guess that you either misunderstood the warning, or accidentally pressed the wrong button (I do that too, sometimes).

You'll need to restore your data from your backups.

If Vista has taken your entire drive, then you must use Vista to clear space for a partition, *not* GParted. That's because of an occasional bug with GParted, which can make shrinking the Vista partition risky.

Once you've shrunk the Vista partition to clear space, then you can use GParted (from the Live CD) to create a new partition on the spare space (don't touch the Vista partition!). I would recommend three *logical* partitions inside an *extended* partition:

[LIST]
[*]2Gb *swap* (or, if you have more than 2Gb RAM, then the size of your RAM)
[*]10Gb ext4 for your *root* directory (where all your programs will go)
[*]The remainder ext4 for your *home* directory (where all your data will go).
[/LIST]
Once you've created those partitions, install Ubuntu.

If you have any confusion about any of this when trying to install Ubuntu -- or any concern that you might be doing the wrong thing -- start a new thread with your questions.

---

### Post by firoz3321 on 2010-01-28
Thank you very much !

---

### Post by oldfred on 2010-01-28
In post #5 you show multiple drives, you do have to be careful on which drive is which. On the third screen you show the drive selection with the down carot on the right side of the drive list. I regularly have issues with two 160GB drives and cannot in all places tell which is which.

Several graphical install examples so you can see the screens. If not Karmic the only difference is the install of grub2 and ext4 as defaults.

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)
Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)
Installing Ubuntu 9.10 Step-by-step installation tutorial with screenshots
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
Jaunty Jackalope / Windows7 Ultimate MultiBoot 'C' (with checkbox graphic for vista/7) 
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by firoz3321 on 2010-02-08
Finally I installed UBUNTU on my system.

This time it detected my VISTA. I deleted one partition from vista.

While installing the UBUNTU i selected Continuous Free Space.

Its now working fine.

I have 2 requests:

1. I cannot connect to internet from UBUNTU. 
   I use direct LAN connection without any ROUTER or MODEM.
   I set WIRED connection but i can't connect.

2. I want to set VISTA as the first option in the BOOT MENU.


Thank You in advance.

---

### Post by Paddy Landau on 2010-02-08
> **firoz3321 said:**
> I have 2 requests:

1. I cannot connect to internet from UBUNTU. 
   I use direct LAN connection without any ROUTER or MODEM.
   I set WIRED connection but i can't connect.

2. I want to set VISTA as the first option in the BOOT MENU.
I'm pleased that you managed to get that done.

Question 1: Please ask in a new thread. Give as many details as you can -- do you get error messages, how are you trying to connect, what hardware do you have?

Question 2: This has been asked (and answered) on the forum. Do a search for it. Make sure that you check what version of Ubuntu you're using, as the answer varies. If you don't understand what you find, please ask in a new thread.

Please mark this thread as "Solved".

---

### Post by oldfred on 2010-02-08
I agree with Paddy Landau 
In the new thread on your network issues post ifconfig from ubuntu terminal and ipconfig from windows cmd line.

But a quick answer on the second problem if you have installed Karmic with grub2 and not an upgrade with old grub.

find your windows entry in grub.cfg and copy to grub default like this (red) Vista entry 
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to:
#GRUB_DEFAULT=0
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"
Then do:
sudo update-grub

If you have old grub and this may work for grub2 if you are on line and can download it.
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by firoz3321 on 2010-02-09
Thank You very Much for the Replies and guiding me through.

I'll create a new thread for the NETWORK settings.

Thank you again ! :popcorn:

---

