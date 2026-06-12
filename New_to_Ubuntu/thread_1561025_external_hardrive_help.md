---
title: "external hardrive help"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by patrickpalmer on 2010-08-25
I recently purchased a HP simplesave external hd. when i try to use it, it says that the volume cannot be mounted. forgive me, but i am a rookie with computers. so help with how to use this device with linux, while still keeping it compatible with my windows computer would be a great help.

---

### Post by ajgreeny on 2010-08-25
Attach it and then run ```
sudo fdisk -l
```(that's a lower case L at the end) and report back here the output.

---

### Post by cptrohn on 2010-08-25
I used to just use Gparted live and reformated them into NTFS as the filesystem.... that way they would work with either OS.... even though my roomate put some videos on one of my externals that was formatted in ext4 and he said Windows did recognize that drive as well.

---

### Post by patrickpalmer on 2010-08-25
Okay, how do I "run"?

---

### Post by leprkhn on 2010-08-25
Open Accessories > Terminal

This is your Command Prompt (or CLI - for Command Line Interface); the most useful tool you have at your disposal.

Once open, enter the command from above and press enter. You'll get a lot of text-based output. You can Copy/Paste that text into this forum post.

---

### Post by patrickpalmer on 2010-08-25
af

---

### Post by patrickpalmer on 2010-08-25
okay now, what.

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

---

### Post by oldfred on 2010-08-25
When you type your password it does not show on the terminal screen. You just have to type it and it enter.

---

### Post by oldfred on 2010-08-25
fdisk did not see another drive.

It looks like it is designed to only work with windows as it includes windows software and auto installs some software into windows and copies data.

This forum for a mac said reformat & delete all the HP software that makes it work with windows.
[http://h30434.www3.hp.com/t5/Other-HP-Consumer-Products-and/HP-Simplesave-Desktop-on-Mac/td-p/132269](http://h30434.www3.hp.com/t5/Other-HP-Consumer-Products-and/HP-Simplesave-Desktop-on-Mac/td-p/132269)

Do you ever plan on using this with windows?

---

### Post by patrickpalmer on 2010-08-25
so i have hooked the hard drive up, and still it will not mount. there is a code that i gives to make it work but it doesn't i get this
 mount -t ntfs-3g/dev/sdb1/media/HP SimpleSave -o force
mount: only root can do that

---

### Post by oldfred on 2010-08-25
Anytime you get only root can do that use up arrow to bring the command back and home to be at the beginning of the line and insert sudo .

I still find I often forget to use sudo and have to add it after the terminal gives me the raspberries.

---

### Post by tech7 on 2010-08-25
> **oldfred said:**
> 
Do you ever plan on using this with windows?
Sorry to butt in here.  I'm following this thread because I plan to do something similar, myself.  Patrick, I know you mentioned in your first post that you want to keep it compatible with windows; do you plan on this being used in both systems?  Thanks! :)

---

### Post by Kinger23 on 2011-07-09
Having problems with one of these as well. Had been using it with another computer running Windows 7. Now that I have moved it over to Ubuntu(Natty) it seems to be the cause of a few problems. 1st> My computer won't boot past Bios screen when it is plugged in and 2nd> it seems to cause Natty to freeze up pretty consistently.
My first thought is to reformat it in Natty and 2nd would be to buy an internal to use in it's place. Would rather not do that because I've already put out the money for this 2TB. 

Wondering if I would be better off degrading to 10.10 or even moving to Ku or Xubuntu??

I am primarily using the computer as an HTPC with XBMC and also for Firefox or Chrome web surfing. Would like to optimize for 1080p playbook and web streaming.

1.9 Ghz Processor
2 GB Ram
ZOTAC 1GB GeForce GT 210GPU (HDMI to LED TV @ 1080p, VGA to monitor)

I will continue to search for solutions to the HDD problems and for info on HTPC optimization but would appreciation any feedback on where to go on this.

---

### Post by westie457 on 2011-07-09
[HTML]Having problems with one of these as well. Had been using it with another computer running Windows 7. Now that I have moved it over to Ubuntu(Natty) it seems to be the cause of a few problems. 1st> My computer won't boot past Bios screen when it is plugged in and 2nd> it seems to cause Natty to freeze up pretty consistently.[/HTML]

Hi a couple of suggestions.

1.  Boot into Windows then connect the drive. When the dust has settled find the icon with a green box and a tick in it and click on this. Select 'Safely Remove' then disconnect the drive.
Now reboot into Natty and connect the drive..... What happens... everything back to normal. Good. Say 'Thank You'
Natty still locks up not so good. Report back here.

---

### Post by Kinger23 on 2011-07-09
> **westie457 said:**
> 
1.  Boot into Windows then connect the drive. When the dust has settled find the icon with a green box and a tick in it and click on this. Select 'Safely Remove' then disconnect the drive.
Now reboot into Natty and connect the drive..... What happens... everything back to normal. Good. Say 'Thank You'
Natty still locks up not so good. Report back here.

Thanks for the advice. Gave it a whirl and...

- Above suggestion = Freeze up at Bios screen.
- Unplugged Drive, Rebooted into BIOS Setup, changed Boot Order from Floppy/HDD/CDROM to HDD/Floppy/CDROM = Boot into Windows XP
- Above suggestion + Reboot with new Boot Sequence = Another BIOS Screen Freeze up
- Unplug Drive and boot into Ubuntu no problem.

Thinking formatting the drive is best plan but willing to try anything else before trying it.

---

### Post by westie457 on 2011-07-09
> **Kinger23 said:**
> Thanks for the advice. Gave it a whirl and...

- Above suggestion = Freeze up at Bios screen.
- Unplugged Drive, Rebooted into BIOS Setup, changed Boot Order from Floppy/HDD/CDROM to HDD/Floppy/CDROM = Boot into Windows XP
- Above suggestion + Reboot with new Boot Sequence = Another BIOS Screen Freeze up
- Unplug Drive and boot into Ubuntu no problem.

Thinking formatting the drive is best plan but willing to try anything else before trying it.

Install testdisk from the Software Centre or in a terminal ```
sudo apt-get install testdisk
``` 

It does work on USB drives. Run it to check for problems do not allow it to write anything yet. Allowing testdisk to check all partitions is a good idea and if necessary it will re-write the mbr of the drive when you say so.

---

### Post by Kinger23 on 2011-07-09
> **westie457 said:**
> Install testdisk from the Software Centre or in a terminal ```
sudo apt-get install testdisk
``` 

It does work on USB drives. Run it to check for problems do not allow it to write anything yet. Allowing testdisk to check all partitions is a good idea and if necessary it will re-write the mbr of the drive when you say so.

How do I work it?? Do I have to run in terminal??

Update: Figured out how to get it to work in Terminal. Now wondering what info I'm looking for?
Update #2: Analyzed and got back: "no partition is bootable"
Update #3: Quick Search="Structure: Ok."

[IMG]http://postimage.org/image/2ag96kfs4/[/IMG]

---

### Post by Kinger23 on 2011-07-09
[[img]http://s2.postimage.org/2agj3siqs/Screenshot1.jpg[/img]](http://postimage.org/image/2agj3siqs/)

Here's a screencap.

---

### Post by westie457 on 2011-07-09
I was half expecting that to happen or to report a problem in the drive. 

Open Disc Utility with the drive connected and select the drive. Then click on Smart data to run drive self tests.
This will give a comprehensive report on the state of the drive.


Another command to try is ```
sudo badblocks
```

This will search your drive for bad sectors. Hopefully none will appear in the early part of the search but do not worry if a few are found. It happens a lot these days in new drives.

---

### Post by Kinger23 on 2011-07-10
Everything comes back ok. As you can see in the screenshot I also have a Verbatim 300GB USB External hooked up and the system runs great with it.

[[img]http://s4.postimage.org/hpweysk/Screenshot2.jpg[/img]](http://postimage.org/image/hpweysk/)

Update: As an aside. The HP HDD has been plugged in and mounted for the past hour or so and I haven't experienced any freeze ups... I seem to only have issues when writing to or from the disk...

---

### Post by westie457 on 2011-07-10
Just refreshed my memory on your problem. Let me get this straight.
There will be some thoughts as I write this so excuse any ramblings that appear to be off topic.

When the drive is connected your box cannot boot into Windows, correct? The bios is searching the drive for a boot sector and has a lot of disk to search through. The cure at least temporarily for this is unplug the drive boot into Windows and plug the drive in again. Follow the auto-run prompt or cancel, however this will keep happening until either the software on the drive is installed or you delete it from the drive. Any external drive must be safely removed from the system before shutdown, if not a lock is put on the drive which means it can only be used with one os in this case Windows.
One way to do this is in Windows Explorer. In the left-hand pane right-click the drive and select Eject from the menu, when Windows has said okay you can unplug the drive.


In Ubuntu when the drive is connected the auto-run part of the software on the drive is trying to run and Ubuntu or any Linux distro does not allow it. The conflict between the two is causing the system to lock up. 

_The Cure_

Allow the software to install itself to Windows then copy and paste it all to a safe folder for future use if you have to reinstall Windows and the drive. Then repartition and format the drive to how you want it.

OR just do the last sentence in the above paragraph.

And always safely disconnect the drive before shutdown to prevent os lock-outs.


Maybe Windows needs that software to be able to handle a drive of that capacity and Linux can handle it easily.

Hope you are not too disappointed with this outcome.

---

### Post by Kinger23 on 2011-07-10
I believe that I'm picking up what you're putting down. I did experience the lockout when trying to explore the folders within XP. What I am hearing you saying is that:

1> The drive is freezing up Ubuntu b/c of the extra autorun software and 
2> I have to "Eject" or "Remove Safely" each time I want to switch OS's.

I can put up with 2 as I use Ubuntu 99.9% of the time but I'm curious as to how to go about ridding the drive of the autorun software without reformatting the drive. Am I able to partition off a small part that has the autorun windows software on it that Ubuntu will ignore? 

Here's the contents of the drive:
[[img]http://s1.postimage.org/2kff0rc90/Screenshot3.jpg[/img]](http://postimage.org/image/2kff0rc90/)

And lastly, is there anyway to keep the bios from searching the external HDD for boot sectors?

---

### Post by Kinger23 on 2011-07-10
OK. I decided screw it. I'll reformat the drive and that will wipe it clean of everything. Including the Autorun HP Launcher Virtual Drive. Not so. Here's a screen grab of the weird files that are showing up on the newly formatted FAT HP 2TB drive. 
[[img]http://s4.postimage.org/2xyvsnfo/Screenshot4.jpg[/img]](http://postimage.org/image/2xyvsnfo/)
As you can see the HP Launcher is in the left pane. I've already ejected it but it does load up initially.

So, any ideas on how the hell I get rid of this HP Launcher??

---

### Post by westie457 on 2011-07-10
Had a look at the pic, not sure how many came with the drive. In your file Browser can you sort them by date they were created. You are looking for a group of file and possibly folders that were all created at the same time. In that list should be at least 4 files probably more. The 4 files are (autorun.inf hpsimplesave.exe hpsimplesavelogo.ico and install.exe). I think XP was not designed to work with drives of this size, that is partly why Windows would not boot. If your BIOS has been set to boot from USB before the internal drive that would cause the long wait while the disk was searched just for XP to report "no bootable disk found. Insert bootable Media and press any key to continue". If you want to keep that software for future use either install it to Windows then copy and paste those files that were created on the same date to a ntfs partition on your internal drive. And to stop the autorun interfering with any file system just delete autorun.inf. Everything will just sit where it is being ignored until you run the install.exe. There is no need to reformat the external drive now. Sometimes a picture really does say 1000 words, that screenshot cleared up my confusion.

Lastly and by way of personal experience the issue of the bios looking for boot sectors in the wrong place is either plug the drive in when the system has booted into any operating system or change settings in the BIOS so the usb drive is after the internal hard drive. I have a 160Gb usb drive without an autorun.inf file on it and the BIOS is set to boot from usb. This always causes my box to throw a fit about no boot drive found so have to restart. When the bios is set to boot from the internal and the external is connected I always get a chkdsk check on the external.

Moral of this post is only plug in to a running system and safely remove and unplug before shutdown or restart.

Glad to have been of help.

---

### Post by Kinger23 on 2011-07-10
I think you missed what I said above the screencap. I di in fact reformat and the screencap is of the reformatted drive. I don't know what those files are and Ubuntu won't let me delete them. Also the virtual drive that seems to be causing so many problems continue to auto run despite the reformat. I have no idea how considering the drive was wiped(?) on reformat. This screecap is the contents of the HP Launcher. The autorun is present but again Ubuntu won't allow me to delete it or send it to the trash.
[[img]http://s4.postimage.org/3bnpy2lg/Screenshot5.jpg[/img]](http://postimage.org/image/3bnpy2lg/)

I'll try to delete these in XP....?

---

### Post by westie457 on 2011-07-10
> **Kinger23 said:**
> OK. I decided screw it. I'll reformat the drive and that will wipe it clean of everything. Including the Autorun HP Launcher Virtual Drive. Not so. Here's a screen grab of the weird files that are showing up on the newly formatted FAT HP 2TB drive. 
[[img]http://s4.postimage.org/2xyvsnfo/Screenshot4.jpg[/img]](http://postimage.org/image/2xyvsnfo/)
As you can see the HP Launcher is in the left pane. I've already ejected it but it does load up initially.

So, any ideas on how the hell I get rid of this HP Launcher??

Pardon the phraseology here AAAAAAAARRRRRRRGGGGGGHHHHHHHH :lolflag:

You did that while I was doing the previous reply so have just seen it. Now you have done that you can either use Disc Utility or Gparted to repartition and then reformat the drive to any file system you want to use.

I am not on my linux box at the moment so cannot confirm what Disc Utility will allow you to do However Gparted will do it with no problems.

---

### Post by Kinger23 on 2011-07-10
Haha. No worries. 

As you can see the HP Launcher continues to hang on for dear life. I even tried reformatting it and it kicks back the error you see in the screencap.

[[img]http://s2.postimage.org/2og5wi8kk/Screenshot6.jpg[/img]](http://postimage.org/image/2og5wi8kk/)

How in the hell do I scoop out that little 700mbs that is driving me crazy!!?? AAAAAAAAAAAAAAAAAAAAAAAARGH is correct. lol

---

### Post by westie457 on 2011-07-10
Do you have Gparted installed?

---

### Post by Kinger23 on 2011-07-10
I do now.

:lolflag:

---

### Post by Kinger23 on 2011-07-10
OK, got GParted. Tried to creat a new FAT32 Partition on HP HDD....

[[img]http://s1.postimage.org/2lxusllfo/Screenshot7.jpg[/img]](http://postimage.org/image/2lxusllfo/)

---

### Post by westie457 on 2011-07-10
> **Kinger23 said:**
> I do now.

:lolflag:

Open Gparted and make sure you are looking at the correct drive. In this case I should think it is SDB. It should be the one that is reporting a total size of 2TB or 2000GB and one large partition and possibly 1 small as well. Now take a look at the attached screenshot. You should be able to see a small orange bar near the top. That is the option that is most likely to work. Directions are Gparted menu bar > Device > Create Partition Table.... Click here pop up window says (refer to 2nd picture) choose any of those clck apply and wait a few seconds one empty drive (fingers crossed). Now repeat and this time choose  ms-dos. Now you can reformat a NTFS so it can be read by Windows and Ubuntu. If for some reason it is rejected repeat the previous steps and select gpt as the partition table then format a NTFS.

---

### Post by westie457 on 2011-07-10
The drive is way too big for a fat32 format.

---

### Post by Kinger23 on 2011-07-10
A rundown of what I did in GParted. Computer froze the first attempt but successfully partitioned to ntfs the second time through. However, the HP Launcher continues to be there. As you can see in the second set of screencaps the files are all locked down as read only and it won't allow me to change them....
[[img]http://s2.postimage.org/2ozjtaoys/Gparted1.jpg[/img]](http://postimage.org/image/2ozjtaoys/)
[[img]http://s2.postimage.org/2ozn4ddyc/Gparted2.jpg[/img]](http://postimage.org/image/2ozn4ddyc/)
[[img]http://s1.postimage.org/2mm2cthok/Gparted4.jpg[/img]](http://postimage.org/image/2mm2cthok/)

Launcher:
[[img]http://s2.postimage.org/2ozqfg2xw/Launcher.jpg[/img]](http://postimage.org/image/2ozqfg2xw/)
[[img]http://s2.postimage.org/2p0207iec/Launcher2.jpg[/img]](http://postimage.org/image/2p0207iec/)

---

### Post by westie457 on 2011-07-10
I ahve go out shortly to get some more aspirin. So for now this is a last ditch attempt. And a very drastic and possibly dangerous one.
in a terminal run 'gksudo <whatever your file browser is>' this gives you full access to whatever is in your system so be careful and hopefully the ability to Shift+ Delete those pesky files out of your life and your hard drive. Ignore any warnings in the terminal window. As stated previously this can be dangerous to your system because there is no recovery option at all. Take your time and get it right first time. Now I really need to get those aspirin. 


GOOD LUCK. 

Oh one more thing exit the terminal as soon as possible and reboot. This warning is to do with the fact that while in root like that your system is wide open to anything and anybody with nasty ideas on the internet. While the chances are slim for anything bad to happen from outside it could still happen.

---

### Post by Kinger23 on 2011-07-10
Believe it or not but it still would not aloow me to Shift Delete......

---

### Post by mikodo on 2011-07-11
Have you thought of Nuking the drive with DBAN (Derrick's Boot and Nuke)? I have never used it, and I am sure you would have to BE EXTRA CAREFUL TO BE SURE YOU ARE HAVE CHOSEN THE CORRECT DRIVE BEFORE USING IT! (The external Drive you have been wrestling with).


[http://www.dban.org/download](http://www.dban.org/download)

[http://www.ultimatebootcd.com/dban.html](http://www.ultimatebootcd.com/dban.html)

[http://www.cit.cornell.edu/security/depth/practices/dban.cfm](http://www.cit.cornell.edu/security/depth/practices/dban.cfm)

You will find a lot more tutorials by seaching for DBAN. Please READ SOME before considering to use it!

EDIT:  Upon reading about DBAN; it seems Way Overkill and would take forever to rewrite several times on a 2 TB disk. 

I am sure an easier solution is available, from the right knowledgeable person.

Sorry to have wasted your time reading all of this.

---

### Post by westie457 on 2011-07-11
Hello again kinger23 this drive of yours is starting to annoy me. I think it is time to get tough with it and bring on the tanks. We are going to try using the command "gksudo nautilus" if you are running a Gnome Desktop or "gksudo konqueror" if you are running a KDE Desktop. The same warnings apply to this  as well. The syntax for using konqueror might not be right only because I do not use KDE. The removal process uses 'Shift+Delete', fingers, toes, arms, legs and eyes crossed that this works. 
All gone HOORAY. 
Still there?         AAAAAAAAAAAAAAARRRRRRRRRRRGGGGGGGGGGGGHHHHHHHHHHH.
In this link you can see -highlighted- a command to run in a terminal 
[http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))[COLOR="Red"]dd if=/dev/zero of=/dev/sda[/COLOR]
 Run that then have a lot of coffee go to work eat a meal go to sleep. You get the idea here?

When the process has finished to check all has gone okay run

 ```
dd if=/dev/sda | hexdump -C | head
```

The information below was taken from here. [http://en.wikipedia.org/wiki/Dd_(Unix](http://en.wikipedia.org/wiki/Dd_(Unix))

To zero out a drive:
 dd if=/dev/zero of=/dev/sda
To make sure that the drive is really zeroed out:
 dd if=/dev/sda | hexdump -C | head
The output of this command will resemble the following if the drive is blank:
 00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
 *
 201f78000
 16841664+0 records in
 16841664+0 records out
 8622931968 bytes (8.6 GB) copied, 1247.05 s, 6.9 MB/s
If the drive is blank, one line of blank bytes will be printed, followed by a '*' signifying repeated blank lines, followed by a line indicating the address of the line which ends the repetition, followed by the statistics which are printed after the output. The numbers in the statistics above are illustrative. If the drive is not entirely blank, there will be more than one line of data output. After running the last command you should have a screen that looks similar to the above.
You do HOORAY and High 5's all round.
You don't... OH CARP.

Run ```
sudo testdisk
```
If you do not have the terminal will let you know how to get it.
Allow testdisk to find all the partitions. There are a few types of these and testdisk allows you to choose what to look for. The first one is usually the one to pick and you can any of the others - only one per search. More coffee for you as the search goes ahead. Post the results, words and pictures please, here. 
That is enough to be going on with for now. I will be getting on with my life while you are doing all this. :lolflag:

---

