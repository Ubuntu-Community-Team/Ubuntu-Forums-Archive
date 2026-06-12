---
title: "Ubuntu/Vista major issues."
date: 2011-03-09
forum: New to Ubuntu
---

### Post by MibunoOokami on 2011-03-09
I posted in another member's thread and also one of my own. Starting this new one so I don't take over the other persons thread and so I can address both problems. I'm starting with Ubuntu problem, then will move to windows.

> **MibunoOokami said:**
> I finished my fresh install last night (this time making a separate partition for /home to avoid any problems with files in the future) and whilst it was downloading updates I went to sleep. Woke up, everything looked fine, suspended my pc while I went out, came home to find it had restarted and on the desktop there were no toolbars, just my wallpaper. Not sure what to make of that but when I was browsing the new posts tab, I saw a thread started by another member with the same problem. Just working on a solution for that at the moment.
 

Did ctrl+alt+f2 and then typed ```
gnome-terminal
``` as per instructions on other thread. Got message, > failed to parse argument cannot open display Ran ```
killall gnome-panel
``` also per instruction and got message > gnome-panel: no process found> **coffeecat said:**
> Boot up the live CD rather than your new Ubuntu installation and open System > Administration > Disk Utility. Highlight your internal drive in the left pane and see what the right pane has to say about your SMART status.

Says >  Smart status not supported > **coffeecat said:**
> Run a self-test as well.

Sorry not sure how to do that.

> **coffeecat said:**
> It's just possible that a failing drive could account for some of the unexpected things that happened to you before, and could also be the reason for your newest problems in Ubuntu and Vista. Unfortunately, new-ish drives do fail on occasion. This is a possibility.

I sure hope not, but it might explain a few things.
One small question, is it possible to run the update manager from terminal? Is that the sudo aptitude upgrade command? I just remembered I never got the chance to install the further 281 updates that were there, even though they were supposed to have been downloaded during install.

 
Now to windows.
  
> **MibunoOokami said:**
> Anyway, I decided to log into Vista to see if that was still fine. As it happens, I tried to log in 3x and got an error message ```
user profile service
login process failed
cannot read user profile
```Tried for a 4th time and logged in successfully and what would you know, the Vista partition or whatever you want to call it has somehow reset to default, leaving only 1 or 2 programs installed that I had put on there. Just as well I was smart enough to copy some files that were on there from the odd occasion that I was using windows.
   
  Something else I forgot to mention, Vista keeps giving me a message that my disk space is low (32MB to be precise) and that makes absolutely no sense. It's a 54GB partition and I almost had that full and never had a message before. Now that it's gone back to default settings and all my data is gone, there should be mountains of space. Very strange.
  



Note: It took ages to post this because when using the live cd, the forum kept telling me I haven't used enough characters, and that I must have a minimum of 1 character. Saved it in open office, went to use Vista to post and can't login again. No error messages, no wrong password messages, the screen just turns black, then returns to the login page over and over. 



Thanks everyone.

---

### Post by MibunoOokami on 2011-03-09
I was just going over my notes and realized there was something I forgot to mention which might be important, because looks somewhat odd to me, but perhaps is normal.

When I was in the disk utility, I noticed an extended partition which is apparently 335GB and an EXT4 partition which is 299GB. In my ignorance that looks like 634GB when my drive is only 400GB 54GB of which is Vista. Is that meant to mean that out of 335GB, 36GB is being used as an extended partition? Perhaps I messed up during install? That still doesn't explain how the other member has the same Ubuntu problem though.

Sorry for the long posts. I am trying to figure out what has gone wrong and am trying to come up with as much detail as possible to make it easier to be helped.

---

### Post by mastablasta on 2011-03-09
> **MibunoOokami said:**
> One small question, is it possible to run the update manager from terminal? Is that the sudo aptitude upgrade command? .
 
servers don't have any desktop graphical interface, so yes.
 
[http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/](http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/)
 
 
sudo apt-get update
sudo apt-get upgrade
 
did you maybe have some proprietary graphics drivers installed before? if so you need to remove them first before doing the upgrade.
 
[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)

---

### Post by MibunoOokami on 2011-03-09
> **mastablasta said:**
> servers don't have any desktop graphical interface, so yes.
 
[http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/](http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/)
 
 
sudo apt-get update
sudo apt-get upgrade

Hi, just tried these commands but everything failed to update/upgrade. That's really strange.

> **mastablasta said:**
> did you maybe have some proprietary graphics drivers installed before? if so you need to remove them first before doing the upgrade.
 
[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)


It was a fresh install from a LiveCD, would the drivers not have  been removed when I formatted the linux partitions? I'm not sure if any  were installed or not.

---

### Post by MibunoOokami on 2011-03-09
> **QLee said:**
> Well that sucks, doesn't it!
 
When the system is in suspend it is no longer under control of the operating system, therefore that "restart" could not have been due to Ubuntu. Maybe coffeecat is correct suggesting possible hardware problems, although a hard drive fault is not going to make the system restart from suspend.
 
It sucks completely. Do you know what would make it restart when suspended?
 
 
 
> **QLee said:**
>  
However, Ubuntu doesn't do anything to the Windows partition when it is installed and it certainly would not put anything back to "default" or selectively remove programs you had installed. I can't even think of a hardware fault that might do something like that, more likely to be random errors or crash.
 
I am confident I had nothing to do with this. I avoided the windows partition during the install of Ubuntu and all I did was login and everything was gone except for 2 programs. I hate the thought that I could have done something so random that even advanced computer users are unsure what's going on, but in reality, couild a hardware fault really be responsible for this?

---

### Post by fabricator4 on 2011-03-09
> **MibunoOokami said:**
>  but in reality, couild a hardware fault really be responsible for this?

Absolutely

Definitely have a look at the SMART data for the drive and run a quick test.  I can't remember if you got to run fsck on the hard drive during one of your previous struggles trying to get the data off the machine, but it might be time to revisit that as well.

If the hard drive comes up clean, we need to check other things like memory.

There's definitely something going on with this beast.

Chris

---

### Post by MibunoOokami on 2011-03-09
> **fabricator4 said:**
> 
Definitely have a look at the SMART data for the drive and run a quick test.

SMART status is not supported apparently. Not sure what quick test I would need to run or if it is relevant since smart status is not supported.


> **fabricator4 said:**
>  I can't remember if you got to run fsck on the hard drive during one of your previous struggles trying to get the data off the machine, but it might be time to revisit that as well.

That's a terminal command right? I'm guessing there's an extra command required because fsck and sudo fsck both gave the same message. > fsck from util-linux-ng 2.17.2
 Unless that is all I should have expected?



> **fabricator4 said:**
> There's definitely something going on with this beast.

Yes and I think I have solved the Windows issue, will explain below quoting myself.

> **MibunoOokami said:**
> 
 I hate the thought that I could have  done something so random that even advanced computer users are unsure  what's going on, but in reality, could a hardware fault really be  responsible for this?

Well as much as I hate the thought I guess I was right about reality. I the windows issue may in fact be a direct result of human error. I think I may have logged into the recovery partition which I am to understand could have instantly removed 99.98% of my data. Now I am already feeling very stupid about this and somewhat peeved and I don't want you kind members who have been helping me, to also think that I am stupid, so please let me give an explanation about the situation.

Right before the very first problem I had which led me to this forum, both of the Windows partitions had the same name. "windows vista" I had no idea why there were 2 or what was what. When I entered the first one (back when I first got this pc and just after I installed Ubuntu) it came up with a menu that looked like a fix it menu, so I rebooted and entered that partition again perhaps once more after that. Then I decided to try the second partition and see what would happen, that brought me to the login page and everything ran as it should. Off the top of my head I seem to recall QLee or Coffeecat telling me that linux sort of crisscrosses the partition and labels. This seemed to explain why I had to use the second partition to use vista, so yesterday when I noticed the 1st partition actually called a loader and the 2nd one called recovery, I still clicked the second one thinking it was just misnamed and everything would be alright. Today I was going to reinstall Ubuntu again to try and fix that problem, so loaded the live CD, went into gparted and sort of glanced over at the windows partitions where I saw the second partition is 54GB and empty and the first partition which is 11GB is completely full. That's when it suddenly dawned on me, that the loader and recovery partitions were in the right order in grub, just not in the actual partition menu or whatever you call it. I must have been in recovery mode which will be the 11GB partition and that's why I would have got the full disk messages. So there you have it, human error after all. :oops:

One thing that still puzzles me is, the recovery partition acted differently than previously, instead of giving me a menu screen it brought me straight to a login screen and it didn't ask me any questions like do I want to try recover windows. Another puzzling thing, as I understand it, windows should have messed up grub by reinstalling, but grub still works fine, just not Ubuntu itself and after logging into Vista be it the recovery mode or not there was no time to do a reinstall or anything, my data was gone the second I logged in. I think a reinstall would have required a restart anyway. Are there any thoughts on this part of my post?

By the way, I didn't re-install Ubuntu because I remembered I need to wait to see what Coffeecat has to say about the Smart status.

Thanks all.

---

### Post by MibunoOokami on 2011-03-10
OK that's peculiar. Just did the SMART status check again and it's working now, not sure what to make of that. I'll post the output.

>  Updated: 8 minutes ago
Powered on: 251.6 days.
Temperature: 35&#1618;&#1618; C/ 95F
Self Assessment: Passed
Self-tests: Completed OK
Power Cycles: 1641
Bad Sectors: None
Overall Assessment: Disk is healthy
Read error rate: good
Throughput performance: Good
Spinup time: good
Start/Stop count: N/A
Reallocated Sector count: good
Seek error rate:good
Seek timer performance: good
Power-on hours: N/A
Spinup retry count: good
Power cycle count: N/A
G-sense error rate: N/A
Power-off retract count: N/A
Load/Unload cycle count: N/A
Temperature: N/A
Reallocation count: N/A
Current pending sector count: N/A
Uncorrectable sector count: N/A
UDMA CRC error rate: N/A
Disk shift: N/A
Loaded hours: N/A
Load/Unload retry count:N/A
Load friction: N/A
Load-in time: N/A
Head flying hours: Good

Not sure what all that means, but I'm sure someone here will be able to make sense of it.

Cheers.

---

### Post by MibunoOokami on 2011-03-15
I needed to use windows yesterday and had forgotten about the problem about not being able to login anymore. This time though, I decided to try Vista that is on the different partition, the one labeled as "Loader" and this is where things get awful strange. Loader is still the recovery centre just like it was when I was using 9.10, but get this, it is now on my 55GB partition not the 11GB one. How in the {insert desired profanity here} could/did that happen? I know this might be hard to believe and some may think it's completely impossible, but this has to have been a screw up with the Ubuntu upgrade/install there is just no other logical/reasonable explanation.

Moving on, I have re-reinstalled Ubuntu and haven't lost the tool bars this time. I am still having difficulties with the suspend protocol. It keeps restarting my PC. Well not restart so to speak coz the PC does turn off like it used to in suspend, but when I hit a key, instead of being taken straight to my desktop with all windows that had been opened still being there, I get taken to the grub menu and that's where basically the restart happens. It didn't do that in 9.10 so I know I'm not confused about the suspend function.

My power and volume icons that usually sit at the top right of the toolbar are missing, they disappeared when I removed the evolution shortcut. Is there a way to get them back? I already tried putting the icon back on the toolbar but the volume and power icons didn't return.

Last but not least, I am having issues with Ibus. Everytime my PC has restarted, I have to reinstall Ibus and this is beginning to annoy me above all things. Why won't it just stay installed and on my toolbar?

---

### Post by fabricator4 on 2011-03-15
> **MibunoOokami said:**
>  Loader is still the recovery centre just like it was when I was using 9.10, but get this, it is now on my 55GB partition not the 11GB one. How in the {insert desired profanity here} could/did that happen? 

Weird.  I don't see how the Ubuntu upgrade could have done that.  Something's very screwy.

> 
Moving on, I have re-reinstalled Ubuntu and haven't lost the tool bars this time. I am still having difficulties with the suspend protocol. It keeps restarting my PC. Well not restart so to speak coz the PC does turn off like it used to in suspend, but when I hit a key, instead of being taken straight to my desktop with all windows that had been opened still being there, I get taken to the grub menu and that's where basically the restart happens. It didn't do that in 9.10 so I know I'm not confused about the suspend function.


I think I've mentioned before, perhaps 10.04 LTS might be a better choice than 10.10, given all the problems you're experiencing. The only problem for you might be if the G3 internet device is not supported, but I think you'll find it will be.


> 
My power and volume icons that usually sit at the top right of the toolbar are missing, they disappeared when I removed the evolution shortcut. Is there a way to get them back? I already tried putting the icon back on the toolbar but the volume and power icons didn't return.


Right click on the panel, click "Add to panel", select "Indicator Applet" then click the "Add" button.  That should get several things back.  The evolution mail notification icon is part of the indicator applet, which might be why it disappeared.
[B](Edit) I just realised another sure fire way of losing the volume applet and a few others.  If you right click on the mail notification icon then click on "Remove From Panel" then it will take all the indicator applets (like volume) out.  They are all part of the same applet.  If there's a way of getting rid of the mail notification icon without getting rid of all the others, I don't know it.
(/Edit)[/B]

> 
Last but not least, I am having issues with Ibus. Everytime my PC has restarted, I have to reinstall Ibus and this is beginning to annoy me above all things. Why won't it just stay installed and on my toolbar?

I'm afraid I don't use Ibus, but I note now that it is installed by default.  Is this a GUI component of Ibus that you installed for extra functionality?  It might be installed, but just not running when you reboot. Try just restarting it, instead of loading it all over again.  If that works, you can put it in "Startup Applications" under Preferences so it starts up at boot time.

I tried looking for a forum or discussion group for Ibus, but a lot of those seem to be Chinese language forums.

Chris.

---

### Post by MibunoOokami on 2011-03-15
> **fabricator4 said:**
> Weird.  I don't see how the Ubuntu upgrade could have done that.  Something's very screwy.

Screwy indeed. As I understand it, Ubuntu should not have affected Windows at all, but I swear on all things holy, I didn't do anything in or near windows to have attributed to this. 



> **fabricator4 said:**
> I think I've mentioned before, perhaps 10.04 LTS might be a better choice than 10.10, given all the problems you're experiencing. The only problem for you might be if the G3 internet device is not supported, but I think you'll find it will be.

I misunderstood you. I thought I was to just keep doing the 6mth upgrades until the next LTS comes out (in 2013 was it?)




> **fabricator4 said:**
> Right click on the panel, click "Add to panel", select "Indicator Applet" then click the "Add" button.  That should get several things back.  The evolution mail notification icon is part of the indicator applet, which might be why it disappeared.

Cool, that kinda worked. My power button didn't come back, but my bluetooth one did which I didn't even realise was gone. Evolution is back though LOL, guess I have to bear with it for now.

> **fabricator4 said:**
> [B](Edit) I just realised another sure fire way of losing the volume applet and a few others.  If you right click on the mail notification icon then click on "Remove From Panel" then it will take all the indicator applets (like volume) out.  They are all part of the same applet.  If there's a way of getting rid of the mail notification icon without getting rid of all the others, I don't know it.
(/Edit)[/B]

LOL yep, that's how it happened to me. I much prefer Thunderbird, would be happy if they made that the default mail system of Ubuntu.

> **fabricator4 said:**
> I'm afraid I don't use Ibus, but I note now that it is installed by default.  Is this a GUI component of Ibus that you installed for extra functionality?  It might be installed, but just not running when you reboot. Try just restarting it, instead of loading it all over again.  If that works, you can put it in "Startup Applications" under Preferences so it starts up at boot time.

Yea the extra functionality is to write in other languages. Ibus is just in system>preferences> keyboard input methods. But I have to go there every time and didn't think to try pinning it to my toolbar. Do you mean restart Ibus or the PC. If Ibus, I have done that already, if you mean PC, I thought restart and reboot are the same thing. When I say reboot I am meaning restart.
[/QUOTE]

Another thing related to the issues in this thread and another I had going. When I try to safely remove my 100GB drive (some of you remember that as the read only drive) I get this error message.> Unable to stop drive.
Error detaching: helper exited with exit code 1: detaching device /dev/sdb 
USB device:/sys/devices/pci0000:00/0000:00.1d.7/usb2/2-2)
SYNCHRONIZE CACHE: failed: No such file or device.
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT:FAILED:No such file or directory 

---

### Post by el_koraco on 2011-03-15
as far as the power icon goes, try going into system, preferences, power management, the "general" tab, and there you should see an option to display the battery at all times. it think the default setting of the ind. applet is to only show the battery when it's (dis)charging.

---

### Post by MibunoOokami on 2011-03-15
Thanks for the reply. I was actually referring to the power button that presents options for restart, logout, shutdown etc. I got it though back by also selecting "indicator applet session".

---

### Post by fabricator4 on 2011-03-15
> **MibunoOokami said:**
> 
I misunderstood you. I thought I was to just keep doing the 6mth upgrades until the next LTS comes out (in 2013 was it?)

Yes, that was indeed what I did, so I might have made that suggestion.  I wasn't experiencing the kinds of problems you are though.  Finding a stable release that works on your machine is probably (definitely) more important than upgrading for the sake of it.

> 
Yea the extra functionality is to write in other languages. Ibus is just in system>preferences> keyboard input methods. But I have to go there every time and didn't think to try pinning it to my toolbar. Do you mean restart Ibus or the PC. If Ibus, I have done that already, if you mean PC, I thought restart and reboot are the same thing. When I say reboot I am meaning restart.


I don't know.  I'm confused :-)

I mean that when you restart the computer, Ibus should start.  I've just downloaded and installed IbusGTK (the GUI bit) and indeed it needs a bit of tweaking.  I've kind of run out of time to fiddle with it, but it seems that it doesn't set up the Ibus daemon to autostart, which you need to do if you don't want to have to do it manually each time you boot.

Try Googling Ibus daemon start or configuration and see if that throws up anything useful.  The Ibus help documentation or website might also be useful.  Someone else might be able to answer the question off the cuff, but I'll try to get back to this one.

> 
Another thing related to the issues in this thread and another I had going. When I try to safely remove my 100GB drive (some of you remember that as the read only drive) I get this error message.
[/quote]

That's nothing like I've ever seen.  Something not right there.  Close all open windows that might be using the drive (ie Nautilus, etc) open a terminal, and try:

```

sudo umount /dev/sdb

```

and see what happens.

Chris.

---

### Post by MibunoOokami on 2011-03-15
> **fabricator4 said:**
> 
That's nothing like I've ever seen.  Something not right there.  Close all open windows that might be using the drive (ie Nautilus, etc) open a terminal, and try:

```

sudo umount /dev/sdb

```and see what happens.

Chris.

Ha, well you're going to love this > /dev/sdb: not mounted thing is, it auto-mounted as soon as I plugged it in.

---

### Post by fabricator4 on 2011-03-15
> **MibunoOokami said:**
> Ha, well you're going to love this  thing is, it auto-mounted as soon as I plugged it in.

Ha.

I think I know.  I suspect a power problem on the USB interface, **and** a problem with the partition table on the drive. 

1) Does the drive have its own power supply?

2) Does Nautilus sometimes open unexpectedly, displaying the contents of the drive?

3) Does the drive suddenly become unavailable for no apparent reason (already know this one - that's what the error messages are saying)

4) If you plug the drive in , open a terminal and type "sudo fdisk -l" do you get an error message for sdb something like "Partition 1 has different physical/logical endings", or any other error message for that matter (please copy it here)


Chris

---

### Post by MibunoOokami on 2011-03-15
> **fabricator4 said:**
> Ha.

I think I know.  I suspect a power problem on the USB interface, **and** a problem with the partition table on the drive. 

1) Does the drive have its own power supply?

No

> **fabricator4 said:**
> 
2) Does Nautilus sometimes open unexpectedly, displaying the contents of the drive?

No

> **fabricator4 said:**
> 3) Does the drive suddenly become unavailable for no apparent reason (already know this one - that's what the error messages are saying)

Apart from being told it wasn't mounted yesterday when it was and being told it's "read only"... I would say no again.

> **fabricator4 said:**
> 4) If you plug the drive in , open a terminal and type "sudo fdisk -l" do you get an error message for sdb something like "Partition 1 has different physical/logical endings", or any other error message for that matter (please copy it here)
Chris

I don't think so.

```
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x75fe8965

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1394    11193344   27  Unknown
/dev/sda2   *        1394        7968    52807617+   7  HPFS/NTFS
/dev/sda3            7969       48642   326708225    5  Extended
/dev/sda5            7969       11800    30775296   83  Linux
/dev/sda6           11800       47953   290402304   83  Linux
/dev/sda7           47954       48642     5528576   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x339810e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x934d934d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12161    97683201    c  W95 FAT32 (LBA)

```

---

