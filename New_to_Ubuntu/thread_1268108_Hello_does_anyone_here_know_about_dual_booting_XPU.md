---
title: "Hello does anyone here know about dual booting XP/Ubuntu? Please help"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Daylon on 2009-09-16
I'm having trouble getting Grub to show a WORKING windows option i've been trying this under the Ubuntu grubs:

title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

I have tried alot of 0,1 0,0 0,4 0,5 combinations with a friend and I haven't gotten it to work. 0,5 returned as no such partition (that's all I remember lol I keep forgetting the message it shows) and 0,1 showed as invalid or unexecutable.

Here is my sudo fdisk -l


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbee8bee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         665     5333580    5  Extended
/dev/sda2   *         666        9783    73240335   83  Linux
/dev/sda3           19215       19457     1951897+  82  Linux swap / Solaris
/dev/sda5               2         665     5333548+   7  HPFS/NTFS


I am sure /dev/sda5 is my windows partition if that helps lol..


Kindly take the time to reply it is much appreciated

---

### Post by LowSky on 2009-09-16
try 0,3

GRUB starts with 0
with knowing that
Extended =0
linux=1
linux swap =2
windows=3

---

### Post by Daylon on 2009-09-16
> **LowSky said:**
> try 0,3

GRUB starts with 0
with knowing that
Extended =0
linux=1
linux swap =2
windows=3

ahhh it came back as no such partition when i chose windows )': why do I feel like that was my last chance

---

### Post by Daylon on 2009-09-16
also this right here is my WHOLE menu.lst

[B][http://pastebin.org/18358](http://pastebin.org/18358)

[/B]I am off for school however I will be back later so please do post your thoughts.


ALSO IM HAVING ONE OTHER PROBLEM:

Everytime I boot my graphics are really shaky so I have to go into my NVIDIA X Server Settings and change this thing called Hz next to resolution from "87 (Interlace)" to "Auto" when I switch it to Auto it stops the graphics shaking :/ Anyone know how to save it and make it Auto everytime I boot?

---

### Post by Calmor on 2009-09-16
There's apparently some hangups when trying to boot an extended partition that's formatted NTFS.

Here are some people commenting on it:

[http://www.linuxforums.org/forum/ubuntu-help/60947-convincing-grub-dual-boot-winxp-extended-partition.html]("http://www.linuxforums.org/forum/ubuntu-help/60947-convincing-grub-dual-boot-winxp-extended-partition.html")

Apparently, rootnoverify instead of root may help, but this thread was still unresolved there as well.  You should be booting (hd0,4) however... as /dev/sda5 would map to 4. 

As for your X-server settings, does the "save settings" option work (instead of just apply)?

If not, you may be editing your xorg.conf file...

---

### Post by louieb on 2009-09-16
I don't see a partition capable of holding a boot-able window install.   In order for windows to be boot-able it should be in a primary partition and the partition  should have the boot flag turned on.  sda5 is a logical partition and sda2 has the boot flag on. (note only one partition per disk should have the boo flag on - Windows requires it - Linux does not care if its set or not.)  

testdisk could probably change sda5  back to a primary partition (sda1) with the boot flag on. 

Note that sda1 and sda5 use the same area of disk - not usually a problem - unless that area holds your windows installation.  

Wonder how the windows install partition got that way?

---

### Post by Sef on 2009-09-16
> I don't see a partition capable of holding a boot-able window install. In order for windows to be boot-able it should be in a primary partition and the partition should have the boot flag turned on. sda5 is a logical partition and sda2 has the boot flag on. (note only one partition per disk should have the boo flag on - Windows requires it - Linux does not care if its set or not.) 

Windows needs to be on the first primary partition.

---

### Post by Daylon on 2009-09-16
> **Calmor said:**
> There's apparently some hangups when trying to boot an extended partition that's formatted NTFS.

Here are some people commenting on it:

[http://www.linuxforums.org/forum/ubuntu-help/60947-convincing-grub-dual-boot-winxp-extended-partition.html](http://www.linuxforums.org/forum/ubuntu-help/60947-convincing-grub-dual-boot-winxp-extended-partition.html)

Apparently, rootnoverify instead of root may help, but this thread was still unresolved there as well.  You should be booting (hd0,4) however... as /dev/sda5 would map to 4. 

As for your X-server settings, does the "save settings" option work (instead of just apply)?

If not, you may be editing your xorg.conf file...

i've been trying to save but this is what I get:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by arapa on 2009-09-16
> **Daylon said:**
> i've been trying to save but this is what I get:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

you need to be root to make changes to the X11 directory where the configuration file lives - if you're not being prompted for password when you open the X Server settings:

press ALT F2 and type:

```
gksu /usr/bin/nvidia-settings
```

---

### Post by egalvan on 2009-09-16
> **Daylon said:**
> 

Here is my sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         665     5333580    5  Extended
/dev/sda5               2         665     5333548+   7  HPFS/NTFS
/dev/sda2   *         666        [COLOR="Red"]9783[/COLOR]    73240335   83  Linux
/dev/sda3           [COLOR="Red"]19215[/COLOR]       19457     1951897+  82  Linux swap

```

I am sure /dev/sda5 is my windows partition if that helps lol..


Observations...
Rearranging the partition information to show the physical starting block numbers shows--

sda1 is the first partition, an extended partition.

sda5 is a logical partition, which takes up the whole sda1 partition.

sda2 is the second partition, a primary

sda3 is the third partition, a primary, swap, which starts a fair ways after the end of the previous (sda2).

Partitions are not in disk order.

sda2 has the BOOT FLAG set.

sda5 appears to be the XP partition.
This is the first partition on the drive.

Suggestions...
use gparted to change the boot flag on sda5 to "active".

If this were my machine, I would save whatever data I had,
wipe the drive,
and start over with a nicerr partition schema.

sda1  primary  XP
sda2  primary 
sda3  swap
sda4  extended
_sda5  boot
_sda6  root
_sda7  home

---

### Post by Daylon on 2009-09-16
> **egalvan said:**
> Observations...
Rearranging the partition information to show the physical starting block numbers shows--

sda1 is the first partition, an extended partition.

sda5 is a logical partition, which takes up the whole sda1 partition.

sda2 is the second partition, a primary

sda3 is the third partition, a primary, swap, which starts a fair ways after the end of the previous (sda2).

Partitions are not in disk order.

sda2 has the BOOT FLAG set.

sda5 appears to be the XP partition.
This is the first partition on the drive.

Suggestions...
use gparted to change the boot flag on sda5 to "active".

If this were my machine, I would save whatever data I had,
wipe the drive,
and start over with a nicerr partition schema.

sda1  primary  XP
sda2  primary 
sda3  swap
sda4  extended
_sda5  boot
_sda6  root
_sda7  home


[[IMG]http://img268.imageshack.us/img268/8079/screenshotpj.png[/IMG]](http://img268.imageshack.us/i/screenshotpj.png/) [[IMG]http://img268.imageshack.us/img268/screenshotpj.png/1/w1024.png[/IMG]](http://g.imageshack.us/img268/screenshotpj.png/1/)


Hello I did what you suggested I right clicked dev/sda5 and clicked manage flags but I'm unsure of what to do now I don't want to mess anything up.

---

### Post by egalvan on 2009-09-16
You'll notice that sda2 has the boot flag set.

You should set the boot flag on sda5.

But this may not be sufficient to have a stable, bootable XP.

There is a program that is capable of changing an extended into a primary, merely by changing some bits in the extended file table.
I can't recall the name at the moment...

And here is a screen-shot of my system...

---

### Post by Daylon on 2009-09-17
i set the boot flag to sda5 and it still didn't let me boot up windows

---

### Post by louieb on 2009-09-17
> **Daylon said:**
> i set the boot flag to sda5 and it still didn't let me boot up windows

Thats because sda5 is a logical partition. Your going to have to change sda5 to a primary partition. Gparted can not do it. 

for the inexperienced - testdisk is  probably the safest - but sfdisk and fdisk can do it too. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598") 

Looking at the Gparted screen shows you have another option. Since you have a large amount of unallocated space and only 3 primary+ extended partitions. You can copy sda5 to a new primary partition.  set its boot flag on - and try to boot to it.  [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 

at any rate this should be done with a live CD - I recommend the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  - it will have the latest versions of Gparted and the other programs.

---

### Post by egalvan on 2009-09-17
> **egalvan said:**
> 
You should set the boot flag on sda5.

But this may not be sufficient to have a stable, bootable XP.


> **Daylon said:**
> i set the boot flag to sda5 and it still didn't let me boot up windows

Yepper, Windows does not like booting from an extended partition.

It IS possible, but a bit of a go. Really better to do it right.

find the software to change the partition type.

In post #14, **louieb** has recommended PartedMagic...

I agree, that is an EXCELLENT distro for disk management.

And if you use it, and like it, then consider a small donation to the authors,
I donate $2 a month because I use it as a business tool.

And the authors are receptive to suggestions and comments about their software.

---

### Post by Daylon on 2009-09-18
ahh in gparted it isn't letting me right click and copy the windows partition because it's showing an error that says "Unable to read the contents of this file system! Because of this some operations may be unavailable." /:

---

### Post by louieb on 2009-09-18
> gparted it isn't letting me right click and copy

Saw the triangle by it but though it was worth  trying.

---

### Post by Michalxo on 2009-09-19
> **Daylon said:**
> ahh in gparted it isn't letting me right click and copy the windows partition because it's showing an error that says "Unable to read the contents of this file system! Because of this some operations may be unavailable." /:

If it is NTFS partition, then install ntfsprogs package ;)
```
sudo aptitude install ntfsprogs
```
gparted should know then how to use ntfs partitions ;)

---

### Post by Daylon on 2009-09-19
> Looking at the Gparted screen shows you have another option. Since you have a large amount of unallocated space and only 3 primary+ extended partitions. You can copy sda5 to a new primary partition. set its boot flag on - and try to boot to it. [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm") 
Alright I did what the last post said and I can now handle my NTFS partition, what should I do once I copy and paste it into a new partition? Should I delete the old one? Can you explain what to do word by word or the best you can? I'm new at this hehe. Thankyou all so much it is all appreciated!

The following is my sudo fdisk -l
also my menu.lst (I'm not sure if the root hd part is correct I think it should be 0,3 but believe me I have tried all sorts of combinations to get it to boot and nothing worked)

[http://pastebin.ca/1571702](http://pastebin.ca/1571702)

[http://img41.imageshack.us/img41/7763/screenshot1pd.png](http://img41.imageshack.us/img41/7763/screenshot1pd.png) 

And here is the latest on my GPartED to supply you with the most information I can

---

### Post by Bartender on 2009-09-19
I don't want you to act on my suggestions because I'm not at all sure what the heck happened here.  Maybe some of the smarter guys will have better ideas.

I'll tell you what your screenshot looks like to me.  It looks like Windows is gone.  I'm guessing that sda5, the little logical NTFS partition, is nothing more than some sort of proprietary partition that the manufacturer set up for utilities or recovery.  It's way too small to have been the original Windows partition.

If my guess is right, you're wasting time trying to make it bootable because there's nothing to boot.

I think you're going to have to reinstall Windows if you want it on this HDD.  Please tell me you made recovery discs earlier.  If not, you should be able to get a recovery disc or discs from the manufacturer for a nominal charge.  

If you do want Windows, then you need to decide exactly how you're going to accomplish that.  Theoretically, you could move Ubuntu way over to the right and install Windows to the left-hand spaces, but installing Windows AFTER Ubuntu's been installed is trickier than the other way around.

The simplest would be to wipe Ubuntu and start all over but it looks like you've spent some time tweaking Ubuntu and it's be a shame to toss all that over the side.

---

### Post by Daylon on 2009-09-19
> **Bartender said:**
> I don't want you to act on my suggestions because I'm not at all sure what the heck happened here.  Maybe some of the smarter guys will have better ideas.

I'll tell you what your screenshot looks like to me.  It looks like Windows is gone.  I'm guessing that sda5, the little logical NTFS partition, is nothing more than some sort of proprietary partition that the manufacturer set up for utilities or recovery.  It's way too small to have been the original Windows partition.

If my guess is right, you're wasting time trying to make it bootable because there's nothing to boot.

I think you're going to have to reinstall Windows if you want it on this HDD.  Please tell me you made recovery discs earlier.  If not, you should be able to get a recovery disc or discs from the manufacturer for a nominal charge.  

If you do want Windows, then you need to decide exactly how you're going to accomplish that.  Theoretically, you could move Ubuntu way over to the right and install Windows to the left-hand spaces, but installing Windows AFTER Ubuntu's been installed is trickier than the other way around.

The simplest would be to wipe Ubuntu and start all over but it looks like you've spent some time tweaking Ubuntu and it's be a shame to toss all that over the side.


I understand. One problem though, that IS my exact Windows partition as the whole reason I wanted to switch to Ubuntu was to resize that partition, I was sick of message popups saying "Fatal Disk Space" ect when i go to Places  in my Gnome Panel I see computer and under that I see 5.5GB Media which shows all of my Program Files such as my gaming ones my AVG Vault my Windows files ect, so I don't think that my partition is gone?

---

### Post by Bölvaður on 2009-09-19
Here is what I would do.

Take backups of your data, wipe everything off the disk and start over. One of the reasons why you should start over is to make a dedicated data partition where you have all your personal files. So you will never have to touch them when you do fresh installs in the future.


Also try:

```
title Microsoft Windows XP Professional
root (hd0,3)
savedefault
makeactive
chainloader +1
```
try hd0,1 and hd0,2

---

### Post by Daylon on 2009-09-19
I have tried those partitions too. And no I cannot delete the partition because I do NOT have a windows CD

---

### Post by louieb on 2009-09-19
i see the waring triangle is gone - try to copy w/Gparted again. Copy to a primary partition  - going to be sda4  (only on left) - resize larger if want at the same time put the boot flag on sda4 -   don't delete to old until when and if the new is booting.

If the copy works try this entry in /boot/grub/menu.list

```
title Microsoft Windows XP Professional
rootnoverify (hd0,3)
makeactive
chainloader +1
```

Let us know what happened.

---

### Post by Daylon on 2009-09-20
> **louieb said:**
> i see the waring triangle is gone - try to copy w/Gparted again. Copy to a primary partition  - going to be sda4  (only on left) - resize larger if want at the same time put the boot flag on sda4 -   don't delete to old until when and if the new is booting.

If the copy works try this entry in /boot/grub/menu.list

```
title Microsoft Windows XP Professional
rootnoverify (hd0,3)
makeactive
chainloader +1
```Let us know what happened.


It's not letting me Paste my Windows partition onto the new one I created >.<

---

### Post by louieb on 2009-09-20
You need to look at the link  [Gparted Documentation - Copying]("http://gparted.sourceforge.net/larry/move/move.htm")  I put in post #14. It explains how to much better that I can. The short of it is:  do your paste into unallocated space.

---

### Post by Daylon on 2009-09-22
Okay everyone this is what I have, I copied my sda5 partition and pasted it onto my unallocated space and resized the copy of it a little bigger while I was at it. This is the picture of menu.lst and Gparted process let me know if anything is wrong

[[IMG]http://img101.imageshack.us/img101/9436/screenshot14.th.png[/IMG]](http://img101.imageshack.us/i/screenshot14.png/)

thanks again everyone!

---

### Post by louieb on 2009-09-22
After the copy finished you should have a partition called /dev/sda4.  Is that correct? 

If so then put the boot flag on it.  (right click > manage flags). If the boot flag is on another partition you will have to remove it from that partition 1st.

Your menu.lst entry is correct as is.  Should work.

---

### Post by Daylon on 2009-09-22
> **louieb said:**
> After the copy finished you should have a partition called /dev/sda4.  Is that correct? 

If so then put the boot flag on it.  (right click > manage flags). If the boot flag is on another partition you will have to remove it from that partition 1st.

Your menu.lst entry is correct as is.  Should work.

The GPARTED transitions went perfectly I have a successful copy of the windows partition, just bigger (what i wanted in the first place) BUT I have an error when I boot windows in grub it says:

Starting up...
NTLDR is missing
Press Ctrl+Alt+Del to restart

And when I restart and select Windows it still happens (not a surprise)
but I can still boot Linux perfectly fine.
any ideas how I can fix this? I've googled and youtubed some similar tags but I do not understand them. I like the people on this forum they help me out step-by-step it's noob-friendly haha. once again, any ideas and theories will be greatly appreciated I feel that I'm MUCH closer to having a successful dual-boot thanks to you guys!

Also I've just finished up doing some more googling and some sites said something about grub.conf, mine is empty, just thought that might be an important factor in my problem! One more thing let me show you my CURRENT sudo fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbee8bee8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2         665     5333580    5  Extended
/dev/sda2             666        9783    73240335   83  Linux
/dev/sda3           19215       19457     1951897+  82  Linux swap / Solaris
/dev/sda4   *        9784       14046    34242547+   7  HPFS/NTFS
/dev/sda5               2         665     5333548+   7  HPFS/NTFS

```

sda4 being my NEW Windows XP partition, resized it and made it a little bigger while I was making it a primary partition.
sda5 being my OLD Windows XP partition, that one was a LOGICAL partition or still is! Note: I have been booting off hd0,3 as that's the one that gave me the NTLDR is missing.

---

### Post by louieb on 2009-09-22
Cool your getting close. You'll need to find a copy of the windows boot files. I've seen them  around on the net. Never mind I found my copy. Should just have extract ntldr and copy it to c:/

---

### Post by Daylon on 2009-09-22
> **louieb said:**
> Cool your getting close. You'll need to find a copy of the windows boot files. I've seen them  around on the net. Never mind I found my copy. Should just have extract ntldr and copy it to c:/

I downloaded your NTDETECT.COM and NTLDR  and Boot.inifiles and extracted them into the following:
[[IMG]http://img529.imageshack.us/img529/628/screenshot15ap.th.png[/IMG]]("http://img529.imageshack.us/i/screenshot15ap.png/")

Is that the correct place? Also after extracting those files there is it just as easy as rebooting and trying to boot Windows or is there another process? I have to leave for school now but I will check this as soon as I get home, thanks alot for the files! I appreciate your help.

Update: I saved all the files into that location and I went ahead and rebooted and still got the same message NTLDR is missing ect. I must have saved it in the wrong spot! Can you tell me the EXACT location of your files? Like is it inside of the Windows/System folder? or the Windows/System32 ect? Thanks again.

---

### Post by louieb on 2009-09-22
Yes thats where they go. - in the root c:/ directory - at least thats where mine are. 

Just though of something - may have to edit boot.ini to reflect the install partition change.  

```

[Boot Loader] 
timeout=30 
Default=multi(0)disk(0)rdisk(0)partition[COLOR=Red](4)[/COLOR]\Windows 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition[COLOR=Red](4)[/COLOR]\Windows="Windows XP" /fastdetect 


```

---

### Post by Darkwing-Duck on 2009-09-22
sounds like restoring GRUB from the Ubuntu side might work too. Here is a a tutorial that might help you with restoring GRUB and running both windows and Ubuntu.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Any more questions let us know!

---

### Post by Daylon on 2009-09-22
> **louieb said:**
> Yes thats where they go. - in the root c:/ directory - at least thats where mine are. 

Just though of something - may have to edit boot.ini to reflect the install partition change.  

```

[Boot Loader] 
timeout=30 
Default=multi(0)disk(0)rdisk(0)partition[COLOR=Red](4)[/COLOR]\Windows 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition[COLOR=Red](4)[/COLOR]\Windows="Windows XP" /fastdetect 


```


I have tried that and editted the text to my corresponding partition and still the same error :/ about to give up soon (why is microsoft so stupid with dual-booting)

---

### Post by louieb on 2009-09-22
Forgot  about this too. Windows and linux use different line endings  may be windows is not reading the file correctly - shoot in the dark.
gist is use Geany to edit. 
quote from [http://www.brighthub.com/computing/linux/articles/19628.aspx](http://www.brighthub.com/computing/linux/articles/19628.aspx)
> 
**Different Line Endings**
 For text files, the difference between operating systems is the character used to mark the end of each line. Unix and Linux use LF (Line Feed) and DOS/ Windows use CR/LF (Carriage Return/ Line Feed). A quick way to see the type of line endings is to open a terminal and use the File command. If File reports "ASCII text" then the line endings are Unix. Instead, if it says, "with CRLF line terminators," then the file is ready for Windows. Many Linux text editors can edit either, but that's not always the case with Windows editors. Luckily, if you use Linux, it's easy to change the endings.
 **GUI Text Editors**
 Two popular Linux text editors have the built-in ability to change line endings. Unfortunately, the bundled GNOME editor in Ubuntu, gedit, does not have this. Instead, try [Geany]("http://www.geany.org/"), a small GTK programmer's and text editor. To install Geany, open up a terminal and type: "sudo apt-get install geany". Choose your desired line ending from the the Document Menu. Then save. For those who prefer KDE, the bundled editor, [Kate]("http://kate-editor.org/kate"), has the same function under the Tools menu.



---

### Post by Daylon on 2009-09-23
I have completely wiped my hard driver and successfuly installed Windows XP Pro SP3 everything looks fine I installed my Video/Sound/Networking Drivers and all seems intact. I will now install Ubuntu via Live CD and install it on a SEPERATE partition, when I do though, should I install it in a Logical partition that way there is no chance of the XP partition becoming a logical one? (since xp has to be primary to boot)

---

### Post by oldfred on 2009-09-23
It really does not matter. Windows must be in a primary partition and Linux does not care. Only 4 primary or 3 primary and many additional logical partitions in the extended partition. If you are adding extra partitions for /home or shared data in another NTFS partition then you will need to add some of these in the extended partition.

More info:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Daylon on 2009-09-25
Thankyou all very much, I now have a dualbooting computer thanks to you all it was very appreciated. Myth busted! Just kidding Thread solved! haha

---

### Post by louieb on 2009-09-25
Thanks for letting us know. Good luck, lou.

---

