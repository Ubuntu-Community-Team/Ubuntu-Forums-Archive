---
title: "Unbuntu installed...now help please!"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by sussexslanter on 2009-06-10
So once I installed I turned my computer off, tried to go back to windows and it won't go.  I get the three options for ubuntu, plus "other operating systems" with two windows options "boot loader" and the one I really want as thats where all my important information is located which is the standard windows option.

But...as I use the arrow keys to attempt to select windows it won't let me.  The windows option won't highlight and I can't get there.

This sort of things is classic windows, not what I was expecting form ubuntu!  Help!

---

### Post by reeseslover531 on 2009-06-10
So you press the down key to try and get to the windows option, and you can't move the selector at all, or just you can't get to the windows options?

---

### Post by sussexslanter on 2009-06-10
I press the down key, it drops down to the recovery option, then the memory option, then the other OS options but then won't progress further, at which point it hangs and I can't then us the arrow key.  I've restarted several times, it won't highlight windows.

---

### Post by kansasnoob on 2009-06-10
We need a bit more info. Boot into Ubuntu and go to terminal. Then run the following commands and "copy-n-paste" the full outputs here.

```
sudo fdisk -l
```

```
cat /boot/grub/menu.lst
```

---

### Post by sussexslanter on 2009-06-10
OK here's the info:

  	 	 	 	 	 	  **sudo fdisk -l **
 

 Disk /dev/sda: 80.0 GB, 80026361856 bytes 
 255 heads, 63 sectors/track, 9729 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0xe02ae02a 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1               1         523     4194304   1b  Hidden W95 FAT32 
 /dev/sda2   *         523        9404    71337001    7  HPFS/NTFS 
 /dev/sda3            9405        9729     2610562+   5  Extended 
 /dev/sda5            9405        9707     2433816   83  Linux 
 /dev/sda6            9708        9729      176683+  82  Linux swap / Solaris
 

 **cat /boot/grub/menu.lst **
 

 # menu.lst - See: grub(8), info grub, update-grub(8) 
 #            grub-install(8), grub-floppy(8), 
 #            grub-md5-crypt, /usr/share/doc/grub 
 #            and /usr/share/doc/grub-doc/. 
  
 ## default num 
 # Set the default entry to the entry number NUM. Numbering starts from 0, and 
 # the entry number 0 is the default if the command is not used. 
 # 
 # You can specify 'saved' instead of a number. In this case, the default entry 
 # is the entry saved with the command 'savedefault'. 
 # WARNING: If you are using dmraid do not use 'savedefault' or your 
 # array will desync and will not let you boot your system. 
 default		0 
  
 ## timeout sec 
 # Set a timeout, in SEC seconds, before automatically booting the default entry 
 # (normally the first entry defined). 
 timeout		10 
  
 ## hiddenmenu 
 # Hides the menu by default (press ESC to see the menu) 
 #hiddenmenu 
  
 # Pretty colours 
 #color cyan/blue white/blue 
  
 ## password ['--md5'] passwd 
 # If used in the first section of a menu file, disable all interactive editing 
 # control (menu entry editor and command-line)  and entries protected by the 
 # command 'lock' 
 # e.g. password topsecret 
 #      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
 # password topsecret 
  
 # 
 # examples 
 # 
 # title		Windows 95/98/NT/2000 
 # root		(hd0,0) 
 # makeactive 
 # chainloader	+1 
 # 
 # title		Linux 
 # root		(hd0,1) 
 # kernel	/vmlinuz root=/dev/hda2 ro 
 # 
  
 # 
 # Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST 
  
 ### BEGIN AUTOMAGIC KERNELS LIST 
 ## lines between the AUTOMAGIC KERNELS LIST markers will be modified 
 ## by the debian update-grub script except for the default options below 
  
 ## DO NOT UNCOMMENT THEM, Just edit them to your needs 
  
 ## ## Start Default Options ## 
 ## default kernel options 
 ## default kernel options for automagic boot options 
 ## If you want special options for specific kernels use kopt_x_y_z 
 ## where x.y.z is kernel version. Minor versions can be omitted. 
 ## e.g. kopt=root=/dev/hda1 ro 
 ##      kopt_2_6_8=root=/dev/hdc1 ro 
 ##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
 # kopt=root=UUID=998e615b-0331-41c3-ab99-056b1402e440 ro 
  
 ## default grub root device 
 ## e.g. groot=(hd0,0) 
 # groot=998e615b-0331-41c3-ab99-056b1402e440 
  
 ## should update-grub create alternative automagic boot options 
 ## e.g. alternative=true 
 ##      alternative=false 
 # alternative=true 
  
 ## should update-grub lock alternative automagic boot options 
 ## e.g. lockalternative=true 
 ##      lockalternative=false 
 # lockalternative=false 
  
 ## additional options to use with the default boot option, but not with the 
 ## alternatives 
 ## e.g. defoptions=vga=791 resume=/dev/hda5 
 # defoptions=quiet splash 
  
 ## should update-grub lock old automagic boot options 
 ## e.g. lockold=false 
 ##      lockold=true 
 # lockold=false 
  
 ## Xen hypervisor options to use with the default Xen boot option 
 # xenhopt= 
  
 ## Xen Linux kernel options to use with the default Xen boot option 
 # xenkopt=console=tty0 
  
 ## altoption boot targets option 
 ## multiple altoptions lines are allowed 
 ## e.g. altoptions=(extra menu suffix) extra boot options 
 ##      altoptions=(recovery) single 
 # altoptions=(recovery mode) single 
  
 ## controls how many kernels should be put into the menu.lst 
 ## only counts the first occurence of a kernel, not the 
 ## alternative kernel options 
 ## e.g. howmany=all 
 ##      howmany=7 
 # howmany=all 
  
 ## specify if running in Xen domU or have grub detect automatically 
 ## update-grub will ignore non-xen kernels when running in domU and vice versa 
 ## e.g. indomU=detect 
 ##      indomU=true 
 ##      indomU=false 
 # indomU=detect 
  
 ## should update-grub create memtest86 boot option 
 ## e.g. memtest86=true 
 ##      memtest86=false 
 # memtest86=true 
  
 ## should update-grub adjust the value of the default booted system 
 ## can be true or false 
 # updatedefaultentry=false 
  
 ## should update-grub add savedefault to the default options 
 ## can be true or false 
 # savedefault=false 
  
 ## ## End Default Options ## 
  
 title		Ubuntu 9.04, kernel 2.6.28-11-generic 
 uuid		998e615b-0331-41c3-ab99-056b1402e440 
 kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=998e615b-0331-41c3-ab99-056b1402e440 ro quiet splash  
 initrd		/boot/initrd.img-2.6.28-11-generic 
 quiet 
  
 title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) 
 uuid		998e615b-0331-41c3-ab99-056b1402e440 
 kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=998e615b-0331-41c3-ab99-056b1402e440 ro  single 
 initrd		/boot/initrd.img-2.6.28-11-generic 
  
 title		Ubuntu 9.04, memtest86+ 
 uuid		998e615b-0331-41c3-ab99-056b1402e440 
 kernel		/boot/memtest86+.bin 
 quiet 
  
 ### END DEBIAN AUTOMAGIC KERNELS LIST 
  
 # This is a divider, added to separate the menu items below from the Debian 
 # ones. 
 title		Other operating systems: 
 root 
  
  
 # This entry automatically added by the Debian installer for a non-linux OS 
 # on /dev/sda1 
 title		Windows NT/2000/XP (loader) 
 rootnoverify	(hd0,0) 
 savedefault 
 makeactive 
 chainloader	+1 
  
  
 # This entry automatically added by the Debian installer for a non-linux OS 
 # on /dev/sda2 
 title		Microsoft Windows XP Home Edition 
 rootnoverify	(hd0,1) 
 savedefault 
 makeactive 
 chainloader	+1 



Hope that means something to someone!


Thanks if anyone can help.

---

### Post by golusweet on 2009-06-10
select other OS and press enter.

You can also access your windows files from ubuntu.

---

### Post by yaroto98 on 2009-06-10
I'm pretty sure you select "other os" to boot to windows, the windows text below "other os" is just a subtext description.

---

### Post by sussexslanter on 2009-06-10
[LEFT]Nope, that just tells me I've selected an "unrecognised device string" then takes me back to the main menu at which point I can't change the highlighted option.  I've tried this several times - if I move the highlighted option down using the arrow keys it will not respond to go back up and I have to restart with the power button again to get into a place where I can choose ubuntu.

I know I can access my own files from ubuntu, but this is a family PC and four other people want to use windows on a daily basis.  Ubuntu was just for me.
[/LEFT]

---

### Post by kansasnoob on 2009-06-10
Just to be clear, if you select:

> Microsoft Windows XP Home Edition 

Nothing happens?

No errors or anything?

---

### Post by jbruced on 2009-06-10
You may want to check out the supergrub website

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

That guy seems to know more about grub booting than anyone else.

---

### Post by sussexslanter on 2009-06-10
It won't let me highlight that option at all.  It drops down using the the arrow key, sometimes two places and sometimes three, but will not drop down to Windows XP.  If I try it won't go back up.  It just hangs.  The instant I drop it from the first ubuntu option the timer at the bottom of the screen goes.

---

### Post by reeseslover531 on 2009-06-10
That is so weird, I have no idea what is going wrong, maybe try changing the default option to the windows choice (I think 3).  Not sure

---

### Post by kansasnoob on 2009-06-10
Well, I'm puzzled:confused:

I'd never personally seen a separate ntfs "bootloader" partition and I've never seen grub just "freeze" like that.

Now, the timer should stop running as soon as you press esc or the arrow keys, that's proper behavior.

But other than that I'm puzzled, it sounds like it might be an XP BOOT.INI file problem, but I'm certainly not sure enough to recommend any changes.

There are several people here on the forums that are immensely more knowledgeable than I regarding boot issues.

I notice that presence1960 is trying to help someone with a similar problem here:

[http://ubuntuforums.org/showthread.php?t=1183407](http://ubuntuforums.org/showthread.php?t=1183407)

Sorry I couldn't be more help.

---

### Post by 4Orbs on 2009-06-10
You might try installing the Startup Manager thru Synaptic and see if Grub works more correctly afterwards. In Startup Manager you can change the default system for auto-boot. I seriously doubt this will fix anything, but it would be my next adventure if I were in your situation.

---

### Post by sussexslanter on 2009-06-10
OK two further questions then...

How do I change the default option to Windows (probably the best option anyway as it will still be the most active OS on this PC) and...

How do I uninstall ubuntu and change everything back to the way it was please?

---

### Post by sandyd on 2009-06-10
get the win xp cd, go to recovery console, login (if needed) and type in "fixmbr" (without quotes"

---

### Post by 4Orbs on 2009-06-10
You should find Startup Manager listed in the System -> Administration menu. Start it and then open the dropdown to select the correct Windows entry (not the Win recovery sector). At the next bootup, the Windows option on the Grub screen will be highlighted during the 10 second countdown, rather than Ubuntu.

---

### Post by bekind2thenoob on 2009-06-10
startup manager isn't installed by default you'll need to install it from add/remove.

---

### Post by louieb on 2009-06-10
Just a guess, but what you described sounds like a bad copy of grub was installed.  Your XP entry looks like it should)  Don't know why there is an entry for the hidded sda1 partition though. 
 Did you run the check media for defects option before installing Ubuntu?

I second **jbruced** suggestion of using a Super Grub Disk (post #10). See if it can boot your windows install.

---

### Post by reeseslover531 on 2009-06-10
> **sussexslanter said:**
> OK two further questions then...

How do I change the default option to Windows (probably the best option anyway as it will still be the most active OS on this PC) and...

How do I uninstall ubuntu and change everything back to the way it was please?

to change the default chang the line near the top that says ```
default 0
``` to ```
default 3
```

---

### Post by Bölvaður on 2009-06-10
> **carlee said:**
> get the win xp cd, go to recovery console, login (if needed) and type in "fixmbr" (without quotes"

that's not what he's asking for.

*deleted*[COLOR=Silver]
[COLOR=black]
press Alt+F2
type :```
gksu gedit /boot/grub/menu.lst
```[/COLOR]


[/COLOR]
 # You can specify 'saved' instead of a number. In this case, the default entry 
 # is the entry saved with the command 'savedefault'. 
 # WARNING: If you are using dmraid do not use 'savedefault' or your 
 # array will desync and will not let you boot your system. 
 **default		0 **
  
 ## timeout sec 
 # Set a timeout, in SEC seconds, before automatically booting the default entry 
 # (normally the first entry defined). 
 **timeout		10 **

change default to 3, that will change what option will be the default choice in grub
if you wish to have lower time before grub auto loggs you into the default choice you can lower timeout from 10 down to... 3 perhaps.
  

if that doesnt work you can cut all the text after (and including this text)


 # This entry automatically added by the Debian installer for a non-linux OS 
 # on /dev/sda1 
 title		Windows NT/2000/XP (loader) 

and paste it above ubuntu. which begins with:

 title		Ubuntu 9.04, kernel 2.6.28-11-generic 


so just put the windows text above the ubuntu one

if you do that the line has been disrupted and you'll need to set default to 0 again

**default		0 **

---

### Post by Linux000 on 2009-06-10
Try to reinstall grub with this

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by theozzlives on 2009-06-10
I know you're trying to help, but you guys gotta stop! I'm a tech and you confused me, no wonder he now wants to take Ubuntu off! You're telling him to do 3 different things all at once.

I would start with Startup Manager in add/remove and specify "Windows XP Home Edition" as your default boot option. See what that does.

---

### Post by egalvan on 2009-06-10
> **theozzlives said:**
> I know you're trying to help, but you guys gotta stop! I'm a tech and you confused me, no wonder he now wants to take Ubuntu off! You're telling him to do 3 different things all at once.

I would **start with Startup Manager in add/remove** and specify "Windows XP Home Edition" as your default boot option. See what that does.

I agree with this...

StartupManager is  MUCH easier for a beginner to understand and use.

StartupManager is not installed by default on 9.04.

Under Add/Remove, be sure to pick "all available software".
Or use Synaptic.


Although I also think this may be a defective install...
this is NOT normal GRUB behavior.

---

### Post by 4Orbs on 2009-06-10
> I would start with Startup Manager in add/remove and specify "Windows XP Home Edition" as your default boot option. See what that does.
In retrospect, I'm wondering if this might be a bad idea. If that link on the menu.lst is dead and points nowhere, and he is able to select it with Startup Manager, he will boot up to a black screen with no way to reset the Startup Mgr option back to Ubuntu. If the arrow keys still function on grub, then there should be no problem.

---

### Post by sussexslanter on 2009-06-11
OK here's the update:
 
Despite the last comment I tried to get Startup Manager through Add/Remove programs but it didn't appear on the 'All' list so I can't do that.  Synaptic did appear so I downloaded it.  It crashes every time.
 
This is the error message:
 
E: dkpg was interrupted, you must manually run 'sudo dkpg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
 
Then the report process fails.
 
Also, firefox has stopped working properly.   So that means I can't do google searches, and I can't sign on to this forum!  The login button just doesn't work, I get the arrow cursor not the pointy habd, when I press it all it does is clear the password.
 
What is going on?  It has the feel of a virus!  It feels more windows than windows.
 
Also my PC came with preinstalled XP so I need a different way of getting rid of ubuntu as I don't have the XP disk.

---

### Post by FishyFantasy on 2009-06-11
Are you using CD to install Ubuntu? Or are you using Wubi (install Ubuntu from Windows)

---

### Post by nothingspecial on 2009-06-11
> **sussexslanter said:**
> OK here's the update:
 

 
This is the error message:
 
E: dkpg was interrupted, you must manually run 'sudo dkpg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
 

 Did you run ```
sudo dpkg --configure -a
```

Did you make a windows recovery disk before you installed ubuntu?

Before you do anything else boot into ubuntu and backup anything you don`t want to loose.

---

### Post by sussexslanter on 2009-06-11
CD through the post.

---

### Post by theozzlives on 2009-06-11
Sounds to me like a failed install. Your GRUB don't work, and you have broken packages? In my early years I rebooted right after the install wrote GRUB, I figured it's just gonna write logs. Well I found out if one little thing (user error, bad burn on the CD, bad *.iso file, etc.) goes wrong the whole thing is shot.

I'd try downloading a new ISO, run MD5SUM, burn at the slowest speed. Then when you boot run a CD check. Before you install.

Since your Ubuntu is hosed, I'd put in the Windows disk, go to the recovery console, and run "fixboot" and "fixmbr", that'll get you into Windows.

---

### Post by FishyFantasy on 2009-06-11
I'm stupid because I remove Ubuntu through WIndows Disk Management and format that "Unknown Partition". Be sure to backup anything you need first. >> AND USE FIXMBR FIRST BEFORE FORMATTING THAT PARTITION <<
So, any appropriate way to remove Ubuntu?

---

### Post by sussexslanter on 2009-06-11
Yeah my problem is I can't access windows at the start up page, I'm only permitted to boot up ubuntu.  So if I want to get any files I have to go through ubuntu.
 
Also I don't have the XP disk.
 
So am I taking it down the local PC shop and paying them £100 to sort this for me?

---

### Post by nothingspecial on 2009-06-11
I got this from this page [[COLOR="Red"]here[/COLOR]]("http://www.supergrubdisk.org/w/index.php5?title=Howto_Boot_Windows_without_problems")

I have no idea if it will work or not.

> This is a permanent solution. After having done it you will no longer have to edit menu.lst.

You need to know how to edit menu.lst as a root or superuser.

To do this type ```
gksudo gedit /boot/grub/menu.lst
```

> You should search for a piece of code very similar to this one:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

and write this one instead of it:

title           Windows
rootnoverify            (hd0,0)
makeactive
chainloader     +1
boot

This way you can check if Windows boots. If Windows you might want to save it as the default option once you boot into it. Edit the file once again and add the savedefault line after the rootnoverify line. (In some situations savedefault hangs Windows boot) boot line is not compulsory. 

---

### Post by sussexslanter on 2009-06-11
I'm willing to give it a try since I'm resigned to taking it to the shop again.
 
But you'll need to break that last post down into sintructions that your average newt could understand and follow.

---

### Post by nothingspecial on 2009-06-11
Okay Open a terminal (accessories > terminal in your menu)and type (copy and paste if you like)
```

sudo cp /boot/grub/menu.lst ~/.menu.lst.backup
```

That will back up your boot menu because you are going to change it.

To change it type this ```
gksudo gedit /boot/grub/menu.lst
```


Near the bottom where it says this

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```

Change it to this
```

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```

Hope it works I`ll check back in 30 mins

---

### Post by sussexslanter on 2009-06-11
Tried it.  
 
Failed.
 
Lots of WARNING messages.
 
About 40 'S's.
 
Could nots.
 
Etc.
 
The few things that were working in firefox now don't work.
 
Can't access files.
 
Can't access web.

---

### Post by FishyFantasy on 2009-06-11
You should post all the error messages for him to analyse it. 

P.S: I'm new to Ubuntu too. Sorry I couldn't help you.

---

### Post by theozzlives on 2009-06-11
can you press a key combination to enter the recovery partition and go to the recovery console? Be careful if you do you could wipe the drive to factory defaults.

---

### Post by sussexslanter on 2009-06-11
This is what it told me exactly (I'm having to type it out manually, as I'm using laptop not the problem PC, as webmail doesn't work in firefox)...
 
(gedit:6727): Gtk-WARNING **:Attempting to set the permissions of 'root/.recently-used.xbel', but failed: No such file or directory
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
 
(gedit:6727): Gtk-WARNING **:Attempting to store changes into 'root/.recently-used.xbel', but failed: Failed to write file 'root/.recently-used.xbel.8WTGVU': ffush() failed: No space left on device
 
(gedit:6727): Gtk-WARNING **:Attempting to set the permissions of 'root/.recently-used.xbel', but failed: No such file or directory
 
(gedit:6727): Gtk-WARNING **: Could not create config directory

---

### Post by sussexslanter on 2009-06-11
What effect would be seen if the partition was not large enough?  Would ubuntu inform me of this directly and offer me the option of expanding?  Or would it just stop working properly?  Just a shot in the dark.

---

### Post by FishyFantasy on 2009-06-11
I think a 8GB partition is OK for an Ubuntu partition. I don't know the effect thought.

---

### Post by sussexslanter on 2009-06-11
How could I check it from within ubuntu and if necessary expand it?

---

### Post by FishyFantasy on 2009-06-11
Well I use this command >:
In terminal:

```
df -h
```

to check your Ubuntu partition size.

---

### Post by sussexslanter on 2009-06-11
OK that produces this:
 
Filesystem                      Size         Used         Avail          Use%    Mounted on
/dev/sda5                      2.3G         2.3G         0               100%    /
tmpfs                            723M         0              723M         0%       /lib/init/rw
varrun                           723M        104K         723M          1%      /var/run
varlock                          723M        0              723M          0%      /var/lock
udev                              723M        152K        723M          1%      /dev
tmpfs                            723M        512K         722M          1%      /dev/shm
lrm                               723M         2.4M         721M          1%      /lib/modules/2.6.28.11-generic/volatile
overflow                        1.0M         16K          1008K         2%     /tmp
 
This isn't what I was thinking of, I was after an overview of the hard disk partitions, but it might help someone tell me if thee's a problem here.  Looks to me like there's not enough available on the ubuntu partition.  But I know nothing about this stuff.

---

### Post by FishyFantasy on 2009-06-11
> **sussexslanter said:**
> OK that produces this:
 
Filesystem                      Size         Used         Avail          Use%    Mounted on
[COLOR="Red"]/dev/sda5                      2.3G         2.3G         0               100%    /
[/COLOR]tmpfs                            723M         0              723M         0%       /lib/init/rw
varrun                           723M        104K         723M          1%      /var/run
varlock                          723M        0              723M          0%      /var/lock
udev                              723M        152K        723M          1%      /dev
tmpfs                            723M        512K         722M          1%      /dev/shm
lrm                               723M         2.4M         721M          1%      /lib/modules/2.6.28.11-generic/volatile
overflow                        1.0M         16K          1008K         2%     /tmp
 
This isn't what I was thinking of, I was after an overview of the hard disk partitions, but it might help someone tell me if thee's a problem here.  Looks to me like there's not enough available on the ubuntu partition.  But I know nothing about this stuff.

Look at that red line. Used 100%. Available 0.(I got this problem too) I was using wubi to install Ubuntu last time which gave me A LOT OF problems like yours (But not cursor problem). My linux-generic was corrupted. And Firefox wasn't working properly. I had fixed it by reinstalling Ubuntu. Oh, wait, 2.3GB?????? Or is it just me..?

---

### Post by sussexslanter on 2009-06-11
That is my suspicion also.  So is it a reinstall or can I fix it from within?

---

### Post by nothingspecial on 2009-06-11
You have been terribly unlucky here. From what I can see, you have 2 major problems.

1 your ubuntu instalation is full

2 The linux boot loader has a problem and can`t find windows.

Do not try to resize your linux partition as this could lead to data loss. What we need to do is get you some space and fix grub (the boot loader)

Windows is still there so don`t panic.

The problem I have is that I know nothing of windows but I think that if you try to resize your partitions without defragging windows you could have problems.

I would remove a load of packages from your Ubuntu system to give yourself a little bit of space and then try to edit grub again. But I need someone who knows what grub should read.

I need to research this a bit before I give any more advice.

---

### Post by FishyFantasy on 2009-06-11
[http://ubuntuforums.org/showthread.php?t=1089958]("http://ubuntuforums.org/showthread.php?t=1089958")

Minimum size for a Ubuntu partition would be 5GB. (Lol. How much I need exactly?) Look at that link above.

---

### Post by nothingspecial on 2009-06-11
You need to be sure this won`t damage windows if you haven`t defragged. I`m not sure but you could **** up your windows. Wait to resize partitions till your sure.

---

### Post by sussexslanter on 2009-06-11
OK thanks for this.  I'll remove some stuff from ubuntu to free up space (games, etc) and await further instructions.  
 
Now that I take myself through the install again from memory I did not ever drag the handle across to resize partitions, and I recall wondering when that option was going to happen as it details it in the intall intructions in the free .pdf available from this site.  That was probably where all the trouble started.

---

### Post by nothingspecial on 2009-06-11
Remove as much as you can, open-office,all the games, gimp and f-spot. 


[COLOR="Red"][SIZE="5"]Do not remove evolution[/SIZE][/COLOR]

I thinkthat will remove your desktop although, if it were me I`d remove that too but I think you`d probably like some poiny clicky bits. (no offence :p)

When you`ve done that try the grub instructions again.

I`ve no idea weather that will work though.

Like I said You need someone who knows something about windows!

---

### Post by FishyFantasy on 2009-06-11
@nothingspecial

You mean, after sussexslanter remove all the things and configure grub, if successful, then he can go into windows? And remove Ubuntu then reinstall again?

---

### Post by nothingspecial on 2009-06-11
I won`t be able to check back for a few hours but I`ll give a short explanation if that will help.

When you start your computer a program called grub reads a file.

This is that /boot/grub/menu.lst  It tells the computer where all the operating systems are and how to boot them. I think it has been written incorrectly during the installation.

What we need to do is make it right. Trouble is, I don`t know how it should read.

Try to find out if resizing your partion will effect windows. If you find for definite that it doesn`t then go ahead and enlarge your ubuntu partition.

Then research how to install ubuntu, partitioning manually. Do not get this wrong. You must install ubuntu to the correct partition. I`ve no time to walk you through now. Pay close attention to identifying which partition is which or you could wipe windows.

Good luck. I`ll check back later.

---

### Post by nothingspecial on 2009-06-11
> **FishyFantasy said:**
> @nothingspecial

You mean, after sussexslanter remove all the things and configure grub, if successful, then he can go into windows? And remove Ubuntu then reinstall again?

I hope. I`m not 100%

---

### Post by sussexslanter on 2009-06-11
Can't remove quite a bit of stuff.  Some of the games have gone but this message pops up again:
 
E: dkpg was interrupted, you must manually run 'sudo dkpg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

---

### Post by nothingspecial on 2009-06-11
The clue is in the message

```
sudo dkpg --configure -a
```

---

### Post by sussexslanter on 2009-06-11
sudo: dkpg: command not found

---

### Post by FishyFantasy on 2009-06-11
What if sussexslanter install Ubuntu on two different hard disk? Like Windows is in C drive and Ubuntu in D drive? Resizing Ubuntu in D drive will mess up Windows in C drive? I don't get it.

---

### Post by nothingspecial on 2009-06-11
> **sussexslanter said:**
> sudo: dkpg: command not found

You gotta spell it right dpkg not dkpg

---

### Post by nothingspecial on 2009-06-11
> **FishyFantasy said:**
> What if sussexslanter install Ubuntu on two different hard disk? Like Windows is in C drive and Ubuntu in D drive? Resizing Ubuntu in D drive will mess up Windows in C drive? I don't get it.

Like I said I know nothing of windows. If that will work, confirm it but don`t let him get it wrong!

---

### Post by nothingspecial on 2009-06-11
> **nothingspecial said:**
> You gotta spell it right dpkg not dkpg

Ha,ha shows what I know.

You must have spelt it wrong on your laptop and I just copied it from your post and pasted it in.   :oops:

---

### Post by FishyFantasy on 2009-06-11
I think if he install Ubuntu in D drive and resize it, yes it might ??replace??overwrite?? some files he saved in D drive. (But not WINDOWS files, WINDOWS files are like those files in filesystem) But if Windows XP is installed in C drive, and Ubuntu is installed in C drive too then of course NONONONONO resizing.

---

### Post by sussexslanter on 2009-06-11
just the one hdd here.

---

### Post by FishyFantasy on 2009-06-11
> **sussexslanter said:**
> just the one hdd here.

Okay. Then you should follow nothingspecial's instructions and good luck. ;)

---

### Post by ubersolid on 2009-06-11
> **sussexslanter said:**
> OK here's the info:

  	 	 	 	 	 	  **sudo fdisk -l **
 

 Disk /dev/sda: 80.0 GB, 80026361856 bytes 
 255 heads, 63 sectors/track, 9729 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0xe02ae02a 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1               1         523     4194304   1b  Hidden W95 FAT32 
 /dev/sda2   *         523        9404    71337001    7  HPFS/NTFS 
 /dev/sda3            9405        9729     2610562+   5  Extended 
 /dev/sda5            9405        9707     2433816   83  Linux 
 /dev/sda6            9708        9729      176683+  82  Linux swap /Solaris


sda1 is NOT the windows installation, but probably a "recovery partiton".
sda2 is windows, the "*" under *Boot* in the above tells me that. And the size, and the NTFS filesystem.

  > 
 # This entry automatically added by the Debian installer for a non-linux OS 
 # on /dev/sda2 
 title		Microsoft Windows XP Home Edition 
 rootnoverify	(hd0,1) 
 savedefault 
 makeactive 
 chainloader	+1 



And that entry is correct as far as I can tell. hd0,1 = sda2. Grub starts counting from 0.
If I was you, I'd boot the computer from my ubuntu-cd, open a terminal, and mount sda5 (your Linux /), and edit /boot/grub/menu.lst:

First you need to be root:
```
su
mkdir /mnt/fixme
mount /dev/sda5 /mnt/fixme
nano /mnt/fixme/boot/grub/menu.lst
```

and set ***default 4***

Then save, and unmount /mnt/fixme:
```
umount /mnt/fixme
```
Reboot and try getting to Windows.

---

### Post by nothingspecial on 2009-06-11
> **ubersolid said:**
> sda1 is NOT the windows installation, but probably a "recovery partiton".
sda2 is windows, the "*" under *Boot* in the above tells me that. And the size, and the NTFS filesystem.

  

And that entry is correct as far as I can tell. hd0,1 = sda2. Grub starts counting from 0.
If I was you, I'd boot the computer from my ubuntu-cd, open a terminal, and mount sda5 (your Linux /), and edit /boot/grub/menu.lst:

First you need to be root:
```
su
mkdir /mnt/fixme
mount /dev/sda5 /mnt/fixme
nano /mnt/fixme/boot/grub/menu.lst
```

and set ***default 4***

Then save, and unmount /mnt/fixme:
```
umount /mnt/fixme
```
Reboot and try getting to Windows.

Thank you. Ctrl O    Enter   Ctrl X to save from nano btw

---

### Post by sussexslanter on 2009-06-11
With some advice here and lots of help from my mate I'm in windows.  Changed default to 5 not 4.  But very solid advice.  Cheers!

---

### Post by sussexslanter on 2009-06-11
Just running defrag in windows now.  How do I sort out the partitions?

---

### Post by sussexslanter on 2009-06-11
All things seem to indicate I use Gparted.  Not a problem there.  All advice indicates Gparted is on the Live CD so lets start with a really basic question, booting from CD with the Live CD in the drive, up comes the menu: Try Ubuntuetc, install ubuntu, check disc, test memory, boot from first hard disk.
 
Where is Gparted please???
 
I can sense I'm nearly there with this.  But little things are getting in the way!

---

### Post by nothingspecial on 2009-06-11
Boot into the live cd (try ubuntu)

In the menu somewhere is partition editor (might be system > adminidtration) can`t remember.

---

### Post by ubersolid on 2009-06-11
Just boot from the cd as you normally do, when you reach the desktop, look under the *Administration* menu. If it's not there, you can install it. Even if you are using a live system, use the Synaptic Package Manager from the same menu to install- Alternatively use *Add or Remove* from the *Programs menu*.

Just remember to back up your important files, just in case something goes wrong with the partitioning, better safe than sorry. Also, do not delete sda1 & sda2, as sda1 contains some important stuff that came with your pc, and sda2 is your windows install, which you probably will want to resize to make room for ubuntu. Resizing an NTFS partition can take a long time depending on how much you resize it, have patience with this.
I'm off to play some minigolf now, I'll check back later tonight, good luck and remember to take it slow, if you are unsure of something, ask first.

---

### Post by sussexslanter on 2009-06-11
OK we're nearly there.  I've resized the main partition (XP) down a bit.  There is at least 15G unallocated now.  
 
I'm guessing that my next move is to resize the linux partition up, as 2.3G is too small.  At least up to 10 or 15G.  
 
So I've gone through the process of partition, wait (a long time), then log in to windows, let the check disk thing sort itself out, restart again.
 
So now I need to resize the linux partition, so back into the Live CD, select try ubuntu, but now it won't load.  It gets to a prompt rather than the desktop.
 
What do I do at the prompt?

---

### Post by 4Orbs on 2009-06-11
Good to see your situation has improved since yesterday. And it sounds like you're starting to really enjoy the art of fine-tuning a sophisticated machine.

This would be a good time to do a quick reinstallation of Ubuntu, rather than laboring over sorting out the current install. Then again, troubleshooting and tweaking is an excellent way to gain a quick understanding of the inner workings.

---

### Post by sussexslanter on 2009-06-11
So just chuck the CD in again, select install ubuntu and go through the process again?
 
This time remembering to drag the partition up a bit at the appropriate time of course.
 
So that will just overwrite the existing set up, not create another?
 
Excuse my ignorance - but its been a time - just want to be sure.

---

### Post by 4Orbs on 2009-06-11
The quickest method would be to simply load the cd, select install now, select the option to manually partition. Then delete the Ubuntu partitions. Then create new partitions from the unallocated space. The way I would partition is to first create the swap partition as a Primary partition and specify its location at the "End" of the disk. Then I would create a 7 GB root / partition (logical) and specify location as "Beginning". Then create the /Home partition as logical and location as "Beginning" using the remaining space. If you don't want a separate /Home partition then just make the swap as above, then use the remaining space as the / partition. This is assuming you have already made a backup of your important stuff off the current Ubuntu system.

Also, you might run the option to check your cd for errors before moving on to the installation.

---

### Post by sussexslanter on 2009-06-11
There is nothing on the existing ubuntu system to be saved, it stopped working almost straight away.  
 
All that swap and primary stuff will be obvious once I start then?

---

### Post by nothingspecial on 2009-06-11
Maybe not.

When you go through the install select manual (advanced) when it comes to partitioning.

When it loads up you must be sure you are messing with the correct partition.

In the empty one right click and select new partition (or something like that)

I`m really sorry, I`m not using ubuntu at the moment and I am doing this from memory.

Create a 2gig partition and allocate it for swap.

Select the rest of the empty partition (right click). Tell it to format it to ext3. Where it says mount point just put a / in it ie 

mount point ```
/
```

Do not go ahead unless you are 100% positive you are installing ubuntu on the correct partition.

 [COLOR="Red"][SIZE="5"]You will wipe windows if you get this wrong[/SIZE][/COLOR]

---

### Post by 4Orbs on 2009-06-11
Yes, you create the partitions one at a time and each partition will have the option available for file system type (I prefer ext3 at this time), the mount location (you really only need the swap and / , but a separate /home is desirable if you feel you will be using Ubuntu for the long term.), and the choice of logical or primary partition. You can have only 4 primary partitions on a hard drive, but you can have 3 primary plus one extended (containing numerous logical partitions inside). The extended partition is automatically created if you select the "logical" option for a partition's type. Each time you create a partition the computer will rescan the hard drive and update the space allocation. The actual erasing and repartitioning doesn't occur until you click on the forward button. So you can re-do your partition scheme any number of times until you are satisfied with the looks of things.

---

### Post by nothingspecial on 2009-06-11
I don`t think we need to worry about /home partitions right now. This guy just wants his computer to work.

---

### Post by Linux000 on 2009-06-11
In jaunty you should be able to select use free space or something like that when you get to the partition menu, you shouldn't have to go through the manual partition thing.

---

### Post by 4Orbs on 2009-06-11
After the new system is installed, I suggest:
1. Don't change anything from default, for now.
2. Run the Update Manager and wait for all the updates to complete.
3. Reboot if necessary.
4. Open the Hardware Drivers Manager and activate the recommended driver for your graphics card. This sometimes causes grief because the progress bar doesn't move while the new driver is being downloaded and installed, and some people cancel the process after waiting a few minutes. This may not happen in your case.
5. If the driver installs properly, you will be told to reboot. And when Ubuntu appears after the reboot, it might be at a different screen resolution than before.
6. Get your multimedia stuff in order by following the Comprehensive Multimedea Audio/Video how-to thread in the Multimedia section of this forum.
7. Turn the music up loud and do the Ubuntu Boogie.

---

