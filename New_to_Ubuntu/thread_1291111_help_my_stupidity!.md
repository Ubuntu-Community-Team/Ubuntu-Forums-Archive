---
title: "help my stupidity!"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by Kyle.Gant on 2009-10-14
hello all.
 
I am not sure what is wrong, but i have a hard drive that untill yesterday was fully partitioned with ubuntu jaunty. last night i used gparted to split the drive in half, and in the unpartitioned space i installed xp. now, i cant dual boot back into ubuntu, AND windows is crashing every 5 minutes. please help me!

---

### Post by drs305 on 2009-10-14
The first thing I'd recommend is to get back your Ubuntu system. Here are some links that should help you restore Grub and the ability to book back to linux:

[ Grub/XP/Vista Bootloader  ]("http://ubuntuforums.org/showthread.php?t=1014708")

[RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by coldReactive on 2009-10-14
Windows probably tried and succeeded in overwriting the GRUB bootstrap loader incorrectly.

[Google Search Is Your Friend](http://www.google.com/#hl=en&source=hp&q=fix+grub+after+windows+install&fp=2755c6b3e9b2e9)

---

### Post by Kyle.Gant on 2009-10-14
@ drs
 
i followed the directions of the first how-to you gave me, and now im back where i started on xp! at no point during any of it was i given the option to choose my os. I'm doing something wrong apparently. any suggestions?

---

### Post by coldReactive on 2009-10-14
> **Kyle.Gant said:**
> @ drs
 
i followed the directions of the first how-to you gave me, and now im back where i started on xp! at no point during any of it was i given the option to choose my os. I'm doing something wrong apparently. any suggestions?

You'll need to start the live CD and boot to repair/fix grub.

---

### Post by Kyle.Gant on 2009-10-14
is this?
> **coldReactive said:**
> You'll need to start the live CD and boot to repair/fix grub.

the same as this?:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

or is there something else i should be doing? i'm seriously lost, because i did the first part of that how-to again, and now im on ubuntu, and have no option to boot into xp.

also, does it help to mention i have absolutly NO idea how to set up a dual-boot system? i've never done it before, and apparently, i still havn't...

---

### Post by coldReactive on 2009-10-14
> **Kyle.Gant said:**
> also, does it help to mention i have absolutly NO idea how to set up a dual-boot system? i've never done it before, and apparently, i still havn't...

Same here, actually.

---

### Post by drs305 on 2009-10-14
> **Kyle.Gant said:**
> @ drs
 
i followed the directions of the first how-to you gave me, and now im back where i started on xp! at no point during any of it was i given the option to choose my os. I'm doing something wrong apparently. any suggestions?

Did you run the "How to restore the Ubuntu grub bootloader" section *from the LiveCD*? Did you receive any errors in the command line when you ran the commands?

---

### Post by Kyle.Gant on 2009-10-14
so do you have any idea what I'm doing wrong? because i would love to have a dual boot system, instead of this headache

---

### Post by Kyle.Gant on 2009-10-14
@drs

yes. i ran it and had no errors. i am in ubuntu now. but when i shut down the computer, and turn it back on, it goes straight to ubuntu, and dosnt give me the option to boot into windows if i want. this is my problem, as i want to have a dual boot system, but i didnt do something right at install (i guess).

---

### Post by Kazade on 2009-10-14
Have you tried this? [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Kyle.Gant on 2009-10-14
im sorry, i apparently didnt convey my noobness...but i didnt understand hardly any of that link...i did the part under "[SIZE=1]Recovering GRUB after reinstalling Windows" and i am still showing ubuntu only. im sorry, but im totally lost at this point.
[/SIZE]

---

### Post by MichealH on 2009-10-14
How i dual booted my system was install windows then ubuntu and grub will take over. [URL="https://help.ubuntu.com/community/WindowsDualBoot"]This may help.
[/URL]

---

### Post by Kyle.Gant on 2009-10-14
i agree it would probably help if i didnt already have ubuntu and xp installed and a TON of stuff on here....i might end up formatting the whole drive and starting over, but only as a last resort.

---

### Post by Ms_Angel_D on 2009-10-14
It's generally easier to set up a dual boot by installing Windows and Then Ubuntu, because windows is a domineering OS and will overwrite any bootloader that is not it's own. The easiest thing I could suggest is using a live cd to back up all your goodies, then formatting the drive into the two separate partions one NTFS and one ext3 using gparted. Then install windows first, followed by ubuntu.

Here's a couple of guides with Screenshots.

[LIST]
[*][How to dual-boot Vista with Linux (Vista installed first)]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")
[*][How to dual boot Windows XP and Linux (XP installed first)]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")
[/LIST]

---

### Post by MichealH on 2009-10-14
> **Kyle.Gant said:**
> i agree it would probably help if i didnt already have ubuntu and xp installed and a TON of stuff on here....i might end up formatting the whole drive and starting over, but only as a last resort.

This might help! [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Kyle.Gant on 2009-10-14
@michaelH

i got to this point: If, after installing grub, Windows does not appear in the boot menu you will need to edit /boot/grub/menu.lst (That is a small "L" and not the number 1 in menu.lst)

and got totally lost. this thing that poped up looks incredibly important, and im really worried about putting in/removing/ editing something without knowing what im doing.

attached is a screenshot of what im looking at. any more specifics about what this how-to is asking me to do, would be helpful.


also, i would like to appologize for taking everyone's sweet time away from them with my problems.

---

### Post by MichealH on 2009-10-14
The window you see is the text editor and to add Windows XP to your menu  [this will help]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs")

Dont worry you dont need to apologise were here to learn.

---

### Post by Kyle.Gant on 2009-10-14
*runs screaming from office with head on fire*

[I]20 mins later....

[/I]im not entirely sure what any of that meant. nor are my windows and ubuntu on seperate HDs...just seperate partitions. im sorry, i know im probably working the patience of you kind folks, but i really can't stress enough how computer retarded i am.

---

### Post by Kyle.Gant on 2009-10-14
ok, so i've sat and look at this for awhile, and i think all i need to do is add this to the wierd document thingy:

title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

the problem is that the code "(hd0,0) is my linux partition. how do i find out what the hd code for my windows partition is?

bear with me please! if im right about this, i have it licked, and if im wrong, then im putting a bullet in this whole thing and going back to windows untill i grow a new brain cell.

---

### Post by uberg on 2009-10-14
<in-large-friendly-letters>Don't panic.</in-large-friendly-letters>

Generally, when going for a Dual Boot it is suggested that you install XP/Vista/Lame/W7 installed first.  Windows does not play well with other operating systems.  So you put it on first and let it have the whole drive and Windows is happy.  Then you put the LiveCD in and repartition the hard drive and install Linux and Grub gets installed and Windows is happy because it never knows the difference.

However, it seemed that you installed Linux and then XP?  Is that what happened?  Don't panic.  It's okay if you did.  We just need to know.  And the data that you don't want to lose - Where is it?  On the XP partition or the Linux partition?

If the data is on the XP partition then you should be able to just pop in the live CD and reinstall Ubuntu in the correct partition and it will make the new Grub for you. 

If the data is in the Linus partition - Don't panic - then another solution will have to be pursued.

---

### Post by Kyle.Gant on 2009-10-14
@uberg

ok. here's the long and short of it.
several months back a friend told me to try ubuntu. i made and played on a live CD for awhile, and liked it enough to install. now, for whatever reason that i still dont understand, there was a problem on install that i assume was a PEBKAC error (Problem Exists Between Keyboard And Chair). this error popped up after a full format of the HD and a reinstall of windows, leaving 30gigs of un-partitioned space for ubuntu. the error caused a reformat of the entire HD (and a waste of an hour of work) and a FULL install of ubuntu. at this point, instead of pulling my hair out, and re-working EVERYTHING. i decided to leave the HD as it was with a full ubuntu partition. several months later (last night), i decided i wanted to play some of my windows games, and i was fed up with wine, which wasnt working for me (see earlier posts about my n00bness). i learned about gparted, installed it, booted on a live CD and re-partitioned the HD to be 50% ubuntu, and 50% unpartitioned. i installed windows on the unpartitioned section figuring that was that. but then after my restart, i went STRAIGHT to windows, no option to boot to ubuntu, where my months of collected movies, music, and photos are.

if you read through all the posts, i followed the first how-to linked to me, and after the first half of it, i was in ubuntu, and unable to access my windows partition, then i finished following the how-to and was back where i started (on windows with no ability to access ubuntu) so i followed the first half of the how-to a second time, and i am now in ubuntu again.

i am sure i have missed a crutial step here somewhere, but ill be a monkey's uncle if i knew what that step was.

---

### Post by uberg on 2009-10-14
Okay, give me a few (or more minutes) i want to pace and think this through before I reply again.  I will get back to you.  Soon.

---

### Post by oldos2er on 2009-10-14
> **Kyle.Gant said:**
> 
title Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

the problem is that the code "(hd0,0) is my linux partition. how do i find out what the hd code for my windows partition is?
 

 If Windows is installed on the second partition, try 

title Windows XP
rootnoverify (hd0,1)
makeactive
chainloader +1

---

### Post by Kyle.Gant on 2009-10-14
@oldos

if i put that in said .lst doc, and it is wrong, and i restart my computer, is it going to give me the finger and turn into a $1500 paperweight?

---

### Post by uberg on 2009-10-14
Can you post the output of the following command:
```
sudo fdsk -l
```

From an Ubuntu terminal of course.  :D

---

### Post by Kyle.Gant on 2009-10-14
i believe this is what you want:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8dee8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12208    98060728+  83  Linux
/dev/sda2   *       12209       24416    98060760    7  HPFS/NTFS
/dev/sda3           24417       24792     3020220    5  Extended
/dev/sda5           24417       24792     3020188+  82  Linux swap / Solaris
root@kyle-desktop:~# 


i had to open a fresh terminal, and wasnt in root, so i got an error message when i copy/pasted what you put. but i got into root and pasted it and got that ^

---

### Post by oldos2er on 2009-10-14
> **Kyle.Gant said:**
> @oldos

if i put that in said .lst doc, and it is wrong, and i restart my computer, is it going to give me the finger and turn into a $1500 paperweight?

 No.

---

### Post by Kyle.Gant on 2009-10-14
just tried the thing oldos said, and i am now in windows. that seemed to do it....

---

### Post by Kyle.Gant on 2009-10-14
i have reboted 3 times now and was able to seemlessly go from one OS to the other. now i just have to figure out why my windows xp copy keeps blue screening me without provocation...

---

### Post by uberg on 2009-10-14
Re: help my stupidity!
i believe this is what you want:

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8dee8de

Device    Boot    Start    End    Blocks         Id    System
/dev/sda1    1    12208    98060728+     83    Linux
/dev/sda2 *    12209    24416    98060760    7    HPFS/NTFS
/dev/sda3    24417    24792    3020220        5    Extended
/dev/sda5    24417    24792    3020188+    82    Linux swap / Solaris

I was afraid of that.

Back to what I was said to before Windows is egotistical.  It wants to be first.  In this case not only wants to be the first installed but it also wants to be the on the first partition.  There are workarounds and hacks, as already suggested and you are already pursuing.

I am not going to talk about those.  

I am going to suggest you consider the Blunt Force Approach.  Just reinstall everything.

Now in an ideal world you would have the means to make a backup of all your important data.  If you had all your important data backed-up you could proceed to Blunt Force Solution Number One:
    1. Backup you data (already done)
    2. Install XP - let it take the whole drive since we are starting from scratch
    3. Reinstall Ubuntu using it's partition tools
    4. Give XP the space you want to give it
    5. Divide your Linux partition:
        a. Swap space equal to twice your RAM
        b. A partition for the root partition: / - A lot of people say a minimum of 5gig; I would say at least 10 gig; I would do at least 20 gig
        c. The rest of the space for your data partition: /home
    6. Restore your backup

Unfortunately, it seems that you do not have the means to backup all your data at this point which leads me to Blunt Force Approach Two.  Follow this at your own risk!  There are some that will read this and shake in their boots.  But I have used this technique several times for different reasons and it has worked for me.

    1. Wipe out that Windows partition (sda2 in your case)
    2. Divide it into two partitions
        a. First one will eventually be your / partition: 5 gig minimum; 10 gig; 20 gig as before
        b. Second one will eventually be your /home folder
    3. Format them Linux friendly.  Ext3 has been the standard but Ext4 is working pretty fine for me
    4. Mount the partition that is to be your /home folder and copy all the data you want backed up into a folder there
    5. Put your Windows installation in the drive and reboot to install
    6. This is important - you are going to install Windows of the first partition where your Linux used to reside.  Install ONLY on this partition.
    7. Insert your Ubuntu CD
    8. Boot and start the install process
    9. Leave the Windows partition alone
    10.  Install / on the smaller of the new partitions you made
    11. Mount the larger of those new partitions as /home - DO NOT FORMAT
    12. Grub will now be set up properly
    13. When you boot into Ubuntu your old data folder will be on the partition mounted as /home along with your new home folder

---

### Post by uberg on 2009-10-14
And of course you already have it figured out.  Good luck with that Blue Screen though.

---

### Post by Kyle.Gant on 2009-10-14
i thank you for your help anyway, as i may be doing a /rage quit and formatting the whole hard drive anyway. the blue screen of death haunts me. i've given up for the day on it. i have a lifetime to fix it after all :)


to all of you, thank you SO MUCH for your help! it is extremely appreciated.


...now to go gauze my head burn and but on some tea....

---

### Post by uberg on 2009-10-14
A nice hot cuppa Jade Puchong will help put things in perspective.  If you decide to go the rage/re-everything route drop me a line.

---

### Post by MichealH on 2009-10-15
You are welcome we help people 24/7 and we all learn something new

---

