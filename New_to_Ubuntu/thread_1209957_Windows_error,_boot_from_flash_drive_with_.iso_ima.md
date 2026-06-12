---
title: "Windows error, boot from flash drive with .iso image?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by freddiespagheti on 2009-07-10
Just a couple days ago I turned my Ace AspireOne into a dual boot. It already had Windows XP and I added the Ubuntu Netbook Remix. Today I'd been looking around the forums for ways to sync both OS's firefoxes and I don't remember writing anything to the Windows drive but now I'm getting an error and can't boot winows anymore. (It's a hal.dll error if that helps)
It worked fine before so I'm assuming the problem relates to the firefox thing.

Anyways, I looked this error up and it can have multiple causes, but it seems the best way to fix it is to run a windows repair installation.

To do that I'm supposed to take a bootable .iso, burn it to a disk, and go from there.
But I don't have a cd drive.
Is there a way to, in Ubuntu, convert the .iso to an .img that i can boot from a flash drive?

Alternatively, if this is a more common problem and there's an easier way to fix it, please let me know.

---

### Post by Revolutionary101 on 2009-07-10
I don't think that there is any way for Ubuntu make a bootable Windows XP flash drive.

I have gotten the hal.dll error before too. This is caused by the Master Boot Record being changed by Ubuntu being installed. Can you still access your Windows Partition in Ubuntu?

---

### Post by freddiespagheti on 2009-07-10
Yep, what do I do?

---

### Post by Revolutionary101 on 2009-07-10
Do you have Gnome Partition editor installed? If not here is the code:

```
sudo apt-get install gparted
```

---

### Post by freddiespagheti on 2009-07-10
Got it. 
What next?

---

### Post by Revolutionary101 on 2009-07-10
Open Gnome Partition Editor under System>Administration>Gnome Partition Editor. Find your Windows Partition it should be listed as dev/sda1. Another clue to finding it would be that it is formated in NTFS. Then open your Windows Partition in File Manager aka Nautilus.

---

### Post by freddiespagheti on 2009-07-10
GNOME Partition editor isn't there.
I just tried adding to the menu, but it wasn't on the checklist.

?

---

### Post by jrox717 on 2009-07-10
In the menu editor, go to Applications > New Item
Name: Gnome Partition Editor
Command: gparted
click ok

---

### Post by Revolutionary101 on 2009-07-10
hmmm that is odd. Open terminal and type this in

```
sudo nautilus
```

When the new nautilus window appears go to the folder /usr/sbin. When you get into that folder find the file gparted. Open it. Then it will ask you a few things click on "Run". Tell me when you have done that.

---

### Post by LewRockwell on 2009-07-10
System > Administration > Partition Editor

or did they change it for the UNR?

I'm triple-booting my AOA-150-1864 with XP Pro SP3, Jaunty 9.04, Puppy Linux and I've got five more partitions just waiting for some *nix distros

.

---

### Post by freddiespagheti on 2009-07-10
It says I need root privileges to run gparted...?

---

### Post by Revolutionary101 on 2009-07-10
Type this into Terminal.

```
sudo su
```

It will ask you for the administrator password. Type it in.
Then type this.

```
gparted
```

It should open the gparted manager.

---

### Post by freddiespagheti on 2009-07-10
No, it didn't ask for a password, it just wouldn't let me in.
I just tried "partition editor" in the system>administration menu. 
It worked.
The partition is called
/dev/sda2
but when I enter that into the location bar in Nautilus, it says its not a folder.

---

### Post by Revolutionary101 on 2009-07-10
Okay keep the gparted window open. Now open your Windows partition (in Finder it should look like -- GB media) in Nautilus and look for the file Autorun.ini

---

### Post by boblemur on 2009-07-10
to fix windows from ubuntu, open your windows drive:

```
sudo fdisk -l
```
you will get something like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       96065   771642081   83  Linux
/dev/sdb2           96066      121601   205117920    7  HPFS/NTFS

```

look over the right at the system column, and find the entry that says "HPFS/NTFS" so in my example it would be:

```
/dev/sdb2           96066      121601   205117920    7  HPFS/NTFS
```

now get the name of the drive in this case its /dev/sdb2 (yours will probably be /dev/sda1 or 2

then type:

```

sudo mkdir /media/tmp
sudo mount /dev/sdb2 /media/mount -o force

```

remember to put your drive name in the 2nd command in place of /dev/sdb2

then run:

```
sudo nautilus
```

and navigate to /media/tmp/ and you will find your windows folder. download the attached zip file and extract it to your desktop. (its the dll thats corrupted).

then copy it from withing nautalus from /home/YOUR_USER_NAME/desktop/HALL.DLL

into /media/tmp/WINDOWS/system32/HALL.DLL and overwrite it.

so basiclly, you have gone into windows and replaced the dll that was broken with a fixed copy :)

hope this helps, if you get stuck let me know

---

### Post by Revolutionary101 on 2009-07-10
> **boblemur said:**
> then copy it from withing nautalus from /home/YOUR_USER_NAME/desktop/HALL.DLL

into /media/tmp/WINDOWS/system32/HALL.DLL and overwrite it.

so basiclly, you have gone into windows and replaced the dll that was broken with a fixed copy :)

hope this helps, if you get stuck let me know

Listen to me because from what you have told me it seems that hal.dll was not corrupted. It is doing this because the Master Boot Record can't find hal.dll.

---

### Post by freddiespagheti on 2009-07-11
@Revolutionary:
I can't find the autorun.ini file


> **boblemur said:**
> to fix windows from ubuntu, open your windows drive:

```
sudo fdisk -l
```you will get something like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       96065   771642081   83  Linux
/dev/sdb2           96066      121601   205117920    7  HPFS/NTFS

```look over the right at the system column, and find the entry that says "HPFS/NTFS" so in my example it would be:

```
/dev/sdb2           96066      121601   205117920    7  HPFS/NTFS
```now get the name of the drive in this case its /dev/sdb2 (yours will probably be /dev/sda1 or 2

then type:

```

sudo mkdir /media/tmp
sudo mount /dev/sdb2 /media/mount -o force

```remember to put your drive name in the 2nd command in place of /dev/sdb2

then run:

```
sudo nautilus
```and navigate to /media/tmp/ and you will find your windows folder. download the attached zip file and extract it to your desktop. (its the dll thats corrupted).

then copy it from withing nautalus from /home/YOUR_USER_NAME/desktop/HALL.DLL

into /media/tmp/WINDOWS/system32/HALL.DLL and overwrite it.

so basiclly, you have gone into windows and replaced the dll that was broken with a fixed copy :)

hope this helps, if you get stuck let me know

@boblemur:
I get an error after entering

sudo mount /dev/sdb2 /media/mount -o force
It says

fuse: failed to access mountpoint /media/mount: No such file or directory

A complete look at what I've done says:

freddie@freddie-laptop:~$ sudo fdisk -l
[sudo] password for freddie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         764     6136798+  12  Compaq diagnostics
/dev/sda2   *         765       15378   117386955    7  HPFS/NTFS
/dev/sda3           15379       18935    28571602+  83  Linux
/dev/sda4           18936       19457     4192965   82  Linux swap / Solaris
freddie@freddie-laptop:~$ sudo mkdir
mkdir: missing operand
Try `mkdir --help' for more information.
freddie@freddie-laptop:~$ sudo mkdir /media/temp
freddie@freddie-laptop:~$ sudo mount /dev/sda2 /media/mount -o force
fuse: failed to access mountpoint /media/mount: No such file or directory
freddie@freddie-laptop:~$ sudo mount /dev/sda2/media/mount -o force
mount: can't find /dev/sda2/media/mount in /etc/fstab or /etc/mtab
freddie@freddie-laptop:~$ sudo mount /dev/sda2 /media/mount -o force
fuse: failed to access mountpoint /media/mount: No such file or directory
freddie@freddie-laptop:~$ sudo mount /dev/sda2 /media/mount -o force
fuse: failed to access mountpoint /media/mount: No such file or directory

---

### Post by boblemur on 2009-07-11
Revolutionary101: (this is not an angry post :P )

but, dont you think if it was because it couldn't find the partition that windows would be complaining about missing something more important than hal.dll such as "ntldr" or "IO.SYS" as thats what has happened to me when i have broken windows in the way you are suggesting.

windows wont get upto the screen:

"C:\WINDOWS\system32\HALL.DLL is missing or corrupt" unless it finds the partition and begins the boot process and fails because it cant find that file, hall is important but its a sign that windows is there.

correct me if you think otherwise, but this is my take on the situation..

---

### Post by boblemur on 2009-07-11
sorry its /media/temp sorry my typo :S

---

### Post by Revolutionary101 on 2009-07-11
> **freddiespagheti said:**
> @Revolutionary:
I can't find the autorun.ini file

Sorry wrong file I meant "boot.ini" open it and it should look like this:

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

Where it says partition(1) replace the 1 with the number 2. That should fix all of your problems. Save the file. Then reboot and try booting up Windows.

---

### Post by oldfred on 2009-07-11
Once you get everything working, the Firebird and Thunderbird sites have info on how to sync data. This tip on this site has some info done several ways. [http://ubuntuforums.org/archive/index.php/t-660251.html](http://ubuntuforums.org/archive/index.php/t-660251.html).

I created a FAT32 partition back before the NTFS read/write was reliable in Linux and have the same firefox and thunderbirds data in the FAT32 partition. All data is the same regardless of whether I am in Linux or Windows. I also copy the directories to my portable when we travel, so I always have up-to-date bookmarks and email. Back then I had to edit a couple of config files to tell Firefox and Thunderbird where to look for the data. I believe now they may have made it even easier but have not had to update anything in configs though several updates.

---

### Post by boblemur on 2009-07-11
> **Revolutionary101 said:**
> Sorry wrong file I meant "boot.ini" open it and it should look like this:

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

Where it says partition(1) replace the 1 with the number 2. That should fix all of your problems. Save the file. Then reboot and try booting up Windows.


but why would ubuntu change this file?? if it has, thats interesting do you know why? (this is the reason why i though just replace hall) and if boot.ini has set that windows is on partition 1 it would never have booted in the past, it would only ever run the recovery console.

wouldnt u agree? what would change that file?

---

### Post by freddiespagheti on 2009-07-11
@boblemur:
Sorry, I replaced it, but it's still not working.

@Revolutionary:
I can't find the boot.ini file either...
I ran a search through the whole partition and nothing named that was there
there is a boot.ini.backup though...

Thanks oldfred, by the way.

---

### Post by Revolutionary101 on 2009-07-11
> **freddiespagheti said:**
> @boblemur:
Sorry, I replaced it, but it's still not working.

@Revolutionary:
I can't find the boot.ini file either...
I ran a search through the whole partition and nothing named that was there
there is a boot.ini.backup though...

Thanks oldfred, by the way.

@Boblemur
Ubuntu did not change the file. It moved the Windows partition. The Boot.ini file shows where the MBR is looking for the partition. By changing the partition (1) to a (2) that changes where it is looking for the hal.dll


@freddiespagheti
Do a search through the whole filesystem. But I gtg I will try and help you tomorrow if you haven't already fixed it.

---

### Post by boblemur on 2009-07-11
hmmm ok well if you cant find boot.ini that could very well be your problem.. its a prity important file..

it should be c:\boot.ini

at the top of your file browser you will see a path like /media/disk or disk-1 etc..

can you please goto terminal and paste me the output of:

```
ls -a1 /media/disk
```

this will help us whats wrong. make sure /media/disk is your windows partition that you are looking at under nautalus

---

### Post by boblemur on 2009-07-11
> **Revolutionary101 said:**
> @Boblemur
Ubuntu did not change the file. It moved the Windows partition.

are you sure??

windows is still /dev/sda2 where its always been, the first partition is compaq diagonstics

```
/dev/sda1 1 764 6136798+ 12 Compaq diagnostics
/dev/sda2 * 765 15378 117386955 7 HPFS/NTFS
/dev/sda3 15379 18935 28571602+ 83 Linux
/dev/sda4 18936 19457 4192965 82 Linux swap / Solaris
```

so its always been in that partition, the only thing ubuntu has done is shrunk it, which should have no effect on boot.ini

---

### Post by freddiespagheti on 2009-07-11
```
freddie@freddie-laptop:~$ ls -a1 /media/ACER
.
..
Documents and Settings
ede15900d52130d1aab29aa6845f
hiberfil.sys
I386
Intel
IO.SYS
IPH.PH
Iris_AO_Installation_Disk
Iris AO USB stick
MSDOS.SYS
MSOCache
NTDClient.log
NTDETECT.COM
ntldr
pagefile.sys
PixeLINK++.dll
Preload.aaa
Program Files
RECYCLER
RHDSetup.log
Sysinfo
System Volume Information
.Trash-0
VALUEADD
WINDOWS
XPH.TAG

```

---

### Post by boblemur on 2009-07-11
ok then save the attatchment, unzip it and put that boot.ini into your c:\ which is: 

/media/ACER


then reboot and see what your system says. :)

---

### Post by freddiespagheti on 2009-07-11
> **boblemur said:**
> ok then save the attatchment, unzip it and put that boot.ini into your c:\ which is: 

/media/ACER


then reboot and see what your system says. :)

Woot! It works!

Now would someone *please* tell me how on _earth_ that got deleted?
I know I didn't do it...

---

### Post by boblemur on 2009-07-11
i think that if you look you will see theres a folder called .trash-0

which is i think where linux puts it broken files because theres no lost+found on ntfs. i think it was more corrupted than deleted, and it was removed for some reason.

to be honest i have no idea, probably something to do with the partition being resized.

but at least it works now :) 

remember to mark this as solved.. and remember that this is what makes ubuntu great... there is no windows community like this. so when you learn more make sure u help others who have the same problem :)

also: i would run:

```
chkdsk /F c:
```

in windows if i were you, just to check over your partition to make sure its all ok...

:) cyaz...

---

### Post by Revolutionary101 on 2009-07-11
I am glad you got it fixed.

---

### Post by freddiespagheti on 2009-07-11
Thanks for your help everyone, I really appreciate it.
I'm sorry to say though, it's back...sort of.
It seems any time I do a complete shut down of Ubuntu (not hibernate) the boot.ini file will have problems so I have to reboot Ubuntu first, replace the file, hibernate Ubuntu, and *then  *start windows. 

It's not a major problem so long as I always hibernate Ubuntu, but it is a bit of an inconvenience. Any suggestions?

---

### Post by boblemur on 2009-07-12
thats very strange, do you hibernate in windows?

try replacing the file in ubuntu then restart twice, without restarting to windows, and then check if the file is there, because if its not then you know that ubuntu is definatly deleting it. then we can find out why.

if it dosent then we know that its windows thats doing something funny. and we can try find out why.

---

### Post by freddiespagheti on 2009-07-12
Alright, after several reboots in Windows and Ubuntu under different conditions, I have come to the following conclusions:

Ubuntu is deleting the file

Ubuntu will only delete the file if Windows has not been hibernated. (otherwise it won't mount the partition, and therefore won't access the file)

Ubuntu will only delete the file if Ubuntu's previous shutdown was a complete one (*not* a hibernation)

Ubuntu deletes the file as it starts up, *not* when it shuts down.

Any ideas?

---

### Post by LewRockwell on 2009-07-12
For Reference:

> **LewRockwell said:**
> I had an eerily similar experience with my Acer Aspire One AOA-150-1864 (seems many of the internals are the same as your Asus). Note usage of the Dell mini wlan 1390 card(Broadcom). I picked the netbook up used "on the cheap" and at first I thought I had been sold a piece of crap. It came with Windows XP Pro SP3 and the damn thing gave me fits connecting to my home wireless(Motorola Surfboard SB5101 Broadband Modem feeding a Linksys WRT54G). I must have messed around with that netbook for several hours resetting this and that and rebooting numerous times. Then I went into the router settings and started banging around there also. The one thing I did that might have cracked the nut was I switched from G-only to mixed(but after it started connecting I switched it back and it's still connected flawlessly).

After getting the wireless working and installing my favorite stuff on windoze(and using them to clean, spruce-up, and defrag windoze) I then set about partitioning the 120GB hard drive using a LiveCD of Puppy Linux(Gparted) via an internal cd-rom drive I had laying around and one of these gadgets which, I must say, no tech or hobbyist should be without([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)).

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

After the partitioning ritual(reducing the windoze partition in several smaller steps with the obligatory reboot into windoze between each reduction so checkdisk could do it's thing and so I could defrag with each reduction) I installed Puppy Linux and was pleased that it worked very well from the get-go(Puppy installation slipped the Grub bootloader in place also). Then it was off to the races to install Ubuntu 9.04 Jaunty Jackalope (full version) which also went without any problems at all. It took a minimal amount of time and fiddling to get it working with the wireless.

Of course there was the minor editing of the grub's menu.lst to get it looking "just right" and a couple of reboots into each system, but I must say that I am pleased with the performance and overall experience. I've also reserved five more partitions for future *nix distros as well.

One note with respect to the 8.9 inch display...it's small and it bothers my eyes more quickly than the bigger screens. I plugged it's VGA output into a nice 17 inch monitor I have on the tech bench and it looked great and was easy on my eyes.

I'd imagine using this little guy to drive a big monitor and, with a wireless keyboard and mouse assisting, it being a reasonably energy-efficient alternative to the regular desktop monsters consuming hundreds of watts unnecessarily.

.

---

### Post by freddiespagheti on 2009-07-13
Any thoughts on why Ubuntu doesn't like the file?

---

### Post by boblemur on 2009-07-13
1) how are you mounting the file system
2) did you run chkdsk under windows
3) does it do it if you remove the line from fstab. ie does it do it if the filesystem isnt mounted by ubuntu.
4) if you replace the file unmount windows and mount it again is the file gone?

sorry for the late reply

---

### Post by freddiespagheti on 2009-07-14
> **boblemur said:**
> 1) how are you mounting the file system
2) did you run chkdsk under windows
3) does it do it if you remove the line from fstab. ie does it do it if the filesystem isnt mounted by ubuntu.
4) if you replace the file unmount windows and mount it again is the file gone?

sorry for the late reply

Alright umm...
1) I'm not really sure...I'm still new to the Linux world. It should be doing it in some default manner. I don't think I've adjusted anything relating to that since I'm trying to not touch anything I don't yet understand.

2)Windows ran chkdsk automatically upon its first run after the Ubuntu installation. It said everything was all clear. Should I run it again?

3)...how do I test that?

4)The file stays even after Windows is unmounted and then remounted.

Alright, and this is probably important, I'm considering rectracting the statement that Ubuntu is doing the deleting:
-It seems I could shut down and restart windows (as long as I don't open Ubuntu) as many times as I want.
-But if Windows freezes and I have to force a power down, then when I start Windows right away afterwards, the file is gone (and I have to go into Ubuntu to fix it).

Also, the file doesn't always get deleted; even if windows and Ubuntu were completely shut down, and even if Ubuntu is the next thing I power up. It might not happen.

Could Grub have anything to do with it? I don't see how the file could be deleted upon a Windows crash, and Windows almost certainly doesn't do it at startup, otherwise it would be almost impossible to get in.

Might Grub mess with something before either OS really starts?

---

### Post by boblemur on 2009-07-17
can you please run

```
cat /etc/fstab
```

do you ever force mount the drive? say for example after a crash. this is the box that comes up and says run:

```
mount /dev/sda? /media/???? -t ntfs-3g -o force
```

3) boot ubuntu, dont open the windows drive... then reboot windows.

but if you can crash windows ( hard power off ) then the file is missing then it sounds like a windows problem, you may want to find your xp cd put it in the cd draw and run(in windows):

```
sfc /scannow
```
(just in case this breaks grub use, remember you are using root (hd0,2) and setup (hd0) when reading this: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/))

that will scan all your opp system files and replace/repair any that are broken, i seriously doubt that grub could do this, but if there is a grub error possibly. 

make sure that you can still get the error to occur before trying the next part!!!


**_read the rest of this next test before you go and try it... _**if you want to test it to see if grub is at fault, backup your mbr:

```
dd if=/dev/sda of=/home/freddie/Desktop/mbr_backup.img bs=512 count=1
```

then copy this to a USB stick, or somewhere off your laptop!

you can run in windows:

```
fixmbr C:\
```

and say yes to its questions this will restore the windows boot loader removing grub, then reboot windows a few times (and try crash it.... shouldn't be too hard it is windows after all :D)

see if you can get it to happen again... now you have 3 outcomes:

1) the file isnt deleted, then we can look at grub and why grub would do it.

2) the file is deleted, then you will have to gather more information about what the hell is going on when windows crash's.

3) your mbr breaks, and you cant boot (it will be scary but dw.)

if 3 occurs you will want to go into the liveCD **copy** the mbr_backup.img into the liveCD home folder (/home/ubuntu) and run:

```
dd if=/home/ubuntu/mbr_backup.img of=/dev/sda bs=1 count=64 skip=446 seek=446
```

now either way, you will want to restore grub so you will need to follow what i said above:

> (just in case this breaks grub use, remember you are using root (hd0,2) and setup (hd0) when reading this: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/))

let me know how your go :) sorry this is taking so long to resolve, hopefully we can get to the bottom of it soon enough.

---

### Post by freddiespagheti on 2009-07-21
Sorry it took me so long, I've been busy...

```
freddie@freddie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=31251224-2c6a-4c5d-b674-b103f06795ea /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=95c655f0-c20f-4ddd-8ce3-107e2111bbd2 none            swap    sw              0       0

```Oftentimes the partition appears on the desktop automatically, but not always. If by force mounted, you mean opened the partition when it didn't appear automatically, then yes, I've done that a couple of times.

I went into Windows, shut it down completely. Then I went into Ubuntu, did *not* open the drive, and then shut down Ubuntu completely. Next, I booted Windows and it gave an error.

And I don't have an XP CD. (or a CD drive actually, but I ordered one, it's on its way) 
Windows was preinstalled and that's all I got. There is also a pre-installed partition for repairing windows but initiating that would wipe the drive.

Edit: I just did the same thing, except this time, instead of booting into Windows at the end, I booted into Ubuntu, opened the drive and checked the file. It was still there.

---

### Post by boblemur on 2009-07-22
hmmm this is very weird, i think for now.. goto windows cmd and run 

```
sfc /scannow
```

and if it asks for the cd rom then you will know that windows is trying to repair a file which it sees as broke.

it also might be worth re running:

```
chkdsk /f c:\

```


also off: [http://www.experts-exchange.com/OS/Microsoft_Operating_Systems/Windows/XP/Q_24381851.html](http://www.experts-exchange.com/OS/Microsoft_Operating_Systems/Windows/XP/Q_24381851.html)

suggested that: the ASKUpgrade service was causing this, and disabling it in, services.msc will fix this.

so run:

```
services.msc
```

and go find that service (ASKUpgrade service) and change it to manual, then click stop, replace the file and try again ( if the service is even there )

if you cant find the service or what ever you obviously dont have the same issue.


hope this helps

---

### Post by freddiespagheti on 2009-07-27
> **boblemur said:**
> 
 also off: [http://www.experts-exchange.com/OS/Microsoft_Operating_Systems/Windows/XP/Q_24381851.html](http://www.experts-exchange.com/OS/Microsoft_Operating_Systems/Windows/XP/Q_24381851.html)

suggested that: the ASKUpgrade service was causing this, and disabling it in, services.msc will fix this.

so run:

```
services.msc
```and go find that service (ASKUpgrade service) and change it to manual, then click stop, replace the file and try again ( if the service is even there )

if you cant find the service or what ever you obviously dont have the same issue.


hope this helps


Wow, I'm not really sure what to say...I'm going through mixed emotions, the most prominent being a great frustration with the bonehead of a programmer that managed to create a program that recursively deletes one of the most vital files to running the Windows operating system. I really did **not** think that there would be any software out there to get on my nerves more than the XP language bar, but this has got me _really_ riled up. I mean honestly, how on _earth_ do you do something like that by accident?

I never even meant to put the Ask toolbar on my computer in the first place. I accidentally missed the chance to uncheck the option to include it while I was installing some other software - I can't even remember what. It didn't show up in Firefox so once it was on the computer I didn't care enough to uninstall it. I forgot about it within a few days.

That search engine needs someone to have a serious talk about who they're hiring as their software engineers. Really. 

Scratch that. Looks like someone already brought this up to the company that made it - over a year ago.
[http://forum.applian.com/showthread.php?p=8321](http://forum.applian.com/showthread.php?p=8321)

Apparently it's a partially Microsoft's fault too, since its some kind of security hole unique to IE 8...

Anyways, I'm really glad to have this fixed, thanks for your help, everyone. I'm gonna wait a couple days before I mark this as 'solved' - just to be sure it's really done for good.

---

### Post by boblemur on 2009-07-30
yay!!! :)

glad you got this fixed, if you need anymore help let me know...

---

### Post by z1000000 on 2009-07-31
Sorry to jump in on someone else's thread, but I have the same problem. I've been following through trying to fix my XP side but I'm stuck.

I was having problems unmounting memory sticks, I used Gparted to name a disk, then deleted it along with the trash file, I think.

I've downloaded the zip file, found Boot.ini which is in my host file, but then I'm stuck.

Where should I put the new Boot.ini file?

In my Media file, all I have is cdrom, cdrom0 and disk. My machine is a Dell and there isn't a Dell file?

---

### Post by freddiespagheti on 2009-07-31
> **z1000000 said:**
> Sorry to jump in on someone else's thread, but I have the same problem. I've been following through trying to fix my XP side but I'm stuck.

I was having problems unmounting memory sticks, I used Gparted to name a disk, then deleted it along with the trash file, I think.

I've downloaded the zip file, found Boot.ini which is in my host file, but then I'm stuck.

Where should I put the new Boot.ini file?

In my Media file, all I have is cdrom, cdrom0 and disk. My machine is a Dell and there isn't a Dell file?


Hmm...
OK, go to Places<Computer

Once there you should see 'filesystem' - that's for Ubuntu
In addition to that (if you have a dual boot system) there should be another drive.
Mine is called ACER but yours would be called whatever Dell wanted to call it.
It could Dell, H38IUY, or literally anything in between.
The point is, it will be the one that's not 'filesystem'

Once you open it up, you should just be able to paste the boot.ini file right there.

Before you do that, boot.ini may need to be edited specifically to suit your computer - I wouldn't know though, I'm just guessing.

If you can't find anything other than 'filesystem', then I think it means that Ubuntu doesn't know the other partition is there, in which case I don't really know what to tell you.
Someone with more experience may be able to figure it out though.

Let us know what you find.

---

### Post by z1000000 on 2009-08-01
Hi and thanks

I've got Hardy Heron loaded in Windows XP, through the WUBI thing, so I guess it's not officially a dual boot job. When I go to Places + Computer, I have Icons for CD/RW/DVD/RW DRIVE and FILESYSTEM only. If I open Filesystem, and open Host, Windows is in there, and Boot.ini is next to it.

Do you think I can just paste Boot.ini there, where the original Boot.ini file is, or should I remove the old and paste the new.?

Before I got stuck, I opened Nautilus and Terminal, and did something, and terminal said Boot ini wasn't recognised or something implying that was the problem.

Thanks, it will be so cool if I can fix this through Linux.

---

### Post by freddiespagheti on 2009-08-01
Hmm...

Unfortunately this is beyond my scope - which, as you know if you followed this whole thread, is actually quite limited.

I expect someone more knowledgeable than I will come along and have pity on your perilous plight (heehee, alliteration).

I will stay with you, however, for moral support.

---

### Post by boblemur on 2009-08-01
Hey, could you please post your exact error??

as if you already can find boot.ini then it is probably not a problem with boot.ini

never the less, could you please post the output of

```
sudo fdisk -l
```

and the contents of boot.ini (that you can find) as well as the full path of where you found it.

---

### Post by z1000000 on 2009-08-01
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          13        6902    55343925    7  HPFS/NTFS
/dev/sda3            6904        7295     3148740   db  CP/M / 


When I try and start XP it comes up with windowsroot>\system32\hal.dll missing or corrupt. 
Thanks

---

### Post by z1000000 on 2009-08-01
[boot loader]

timeout=15

default=c:\wubildr.mbr

[operating systems]

c:\wubildr.mbr="Ubuntu"

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by Geoff918 on 2009-08-01
Maybe check out [http://www.pendrivelinux.com](http://www.pendrivelinux.com)

I've used that before, now Ubuntu isn't designed to run from a flash drive, so it's imperfect--but it will get you up and running. (Look for Ubuntu link)

---

### Post by z1000000 on 2009-08-01
Places/computer/filesystem/host
In there is the windows file and next to it is the Boot.ini file

Thanks again.

---

### Post by boblemur on 2009-08-02
ok, well this dosent sound like the same issue as the main one in this tread.

please goto earlier in this thread and find the hall.zip and extract it into..

/host/windows/system32

and then try again this may be the problem although it dosent seem like it.

and im sorry but i dont know how to help you as i have never used the ubuntu inside windows thing before.

good luck :)

---

### Post by z1000000 on 2009-08-02
Thanks everyone, but it didn't work. I'll fiddle about but maybe it's time to load Ubuntu over windows.

Doh! Now neither will start, I'm on a live CD. Luckily I have a few so I may play about and try some
other distros before loading 9.04 as the sole OS.

---

### Post by Dark Aspect on 2009-08-02
> **Revolutionary101 said:**
> I don't think that there is any way for Ubuntu make a bootable Windows XP flash drive.

Well, [ms-sys]("http://mirrors.kernel.org/ubuntu/pool/universe/m/ms-sys/ms-sys_2.1.0-1_i386.deb") can create mbr on windows drives. That makes it bootable but I doubt thats the problem here if he is getting a hal error.

To the OP, when you say flash drive are you referring to USB? Windows was not made to boot from such a device but you can send me PM, I know a few methods.

---

