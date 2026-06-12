---
title: "New install 10.04, reboots to Harware Monitor &amp; hangs"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Popeye.Tom on 2010-08-04
Hi all, 



This is cross posted in the Launchpad Questions area.  Reaching out to a different audience...hope I'm not breaking any sacred taboo on my first post!



This is my first installation of Ubuntu.
 New small system, all new hardware except case:
Biostar A785G3 AM3 Micro ATX mobo
Athlon X2 245, 2.9GHz, 65 watt, dual core
Crucial DDR3 1333, 2 x 1G kit
Corsair CMPSU-400CX, 400W power supply, 80+
WD Caviar Blue WD2500AAJS, 250GB
Liteon SATA DVD/r
 System posts fine recognizes CPU, RAM, HD, boot sequence set in BIOS.
 Loads and runs 10.04 from DVD fine:  System posts, goes to selection  dialog, pick trial from disk.  Hardware Monitor displays and then goes  to stickman and keyboard.  Loads & runs fine, open FF and browse  internet.
 Restart system seems fine and no error messages (that I  could see) during shutdown.  Restart system and from dialog select  Install.  Proceed through steps, Installer recognizes HD by p/n.  Set to  wipe and install on entire drive.  Set UID, PWD & system name.   Install proceeds without a hitch.  Get to end and system says it's time  to restart.
 System ejects disk & I remove it and press enter.  Posts, gets to  Hardware Monitor and then  hangs > no stickman & keyboad > no  HD activity, just sits.
 Suggestions?  Thoughts?
 Thanks,
Popeye.Tom

---

### Post by corrytonapple on 2010-08-04
Hit shift as you start up to get you to the GRUB menu. What do you see?

---

### Post by Popeye.Tom on 2010-08-04
> **corrytonapple said:**
> Hit shift as you start up to get you to the GRUB menu. What do you see?

Gotta run and play taxi cab.  I'll try and post results tomorrow.  Thanks!

---

### Post by Popeye.Tom on 2010-08-05
> **corrytonapple said:**
> Hit shift as you start up to get you to the GRUB menu. What do you see?

Hi Cory,

If I put the disk in the drive & it is set as the first in Boot sequence, I can get to the GRUB menu and it is complete.  If I don't have the disk in and it tries to boot from the installation on the drive then it proceeds as far as the Hardware Monitor report, which appears complete, but never any further so I cannot get to the GRUB menu.  Here is the information that I just posted on the Launchpad support area:

Hi marcobra and delance,

Marc, system meets minimum requirements.  I did not run a MD5 checksum on the iso, but I will.  I can say that I can browse the disk burned just fine and the contents displayed "look" good.  

Booting from the disk I never see Windoze - it doesn't exist!  New system, new hardware.  

*Running the OS loaded from the disk the 'trial' loads fine.  
  >system posts
  >Hardware Monitor reports CPU, system temps, ram, HD, etc
  >see command line...not there for long..."ISO...Linux...Debian..." loading message
  >Stickman and keyboard

If I let it go, it loads Ubuntu just fine from CD.

*I reboot the system and enter the GRUB menu.
  >Check Disk for errors:  "Check finished:  No errors found"
  >Reboot & enter GRUB
  >Running Memtest86 v 4.0    53% finished.  All passed so far, will update when done


Delance, after testing Ubuntu 10.04 x32 Desktop from the CD I rebooted the system and proceeded to the Installation from the first selection menu (Try It! or Install).

After successful completion of all steps of the installation I then proceeded to restart the system as direct by the installation wizard that the "Installation is complete.  You need to restart the computer..."  Push the Restart Now button, removed the disk when the drive opened and allowed system to restart.  

All closing text messages appeared to be fine during shutdown.  The system posts fine then displays the Hardware Monitor w/ CPU, system temps, RAM, HD etc  Then goes to flashing cursor and nothing.  I do not see the loading message "Linux....Debian....etc"  It simply sits, hung w/ a flashing _ cursor and does nothing.  Cannot enter GRUB, never gets there.  No Stickman, no keyboard.


UPDATE:  Memtest still running, 48 min.  on test 6, no errors found yet.

Thanks,
Tom

---

### Post by Popeye.Tom on 2010-08-05
Memtest started from GRUB menu completed.  Full pass

*****Pass complete, no errors, press Exc to exit*****

Upon reboot, entered GRUB menu and selected 'Boot from first Hard Drive'

system clears GRUB menu and reports:

"Booting from local disk....
_"

(quotes added)

hung....   just sits w/ _ (underscore) cursor.  No HDD LED activity.

Now running MHDD 4.6 disk scan test, in process.  Ran MHDD Seek & Read, allowed that to run for a bit, reported 15.1 average time, something like 54 for max.

See if I can find my disk w/ Perfect Disk, if I can't I'll have to go onto Gibson Research site and see if I can recover the copy I bought!  Until then, I'll let MHDD run.

---

### Post by Popeye.Tom on 2010-08-05
> **Popeye.Tom said:**
> 
See if I can find my disk w/ Perfect Disk, ...

Not perfect disk > Spin Rite!  ;)

---

### Post by corrytonapple on 2010-08-05
Also, what did you use to burn the disc? If the disc is burned at a high speed it can be prone to failures. Try re-burning the Ubuntu.iso at a lower speed (2x) and try again. Remember to use high quality discs!

---

### Post by Popeye.Tom on 2010-08-05
OK, I'll create a new disk.

I burned the ISO to disk using CDBurnerXP, but I let it run at full speed.

It did not want to put it on a CD, claimed the image was too large.  I burned it to a Sony DVD +R.  Could this be an issue?

I could copy the ISO image to a Win7 machine and try writing it to a FujiFilm CDR using the imbedded tools in 7.

Any thoughts on it being on a DVD being the source of the bad install?

Another option would be a USB thumb drive, but I'd have to check the BIOS and make sure it can use a USB port for boot, though it should!  

Also, MHDD 4.6 finished and found no errors.  SpinRite v6.0 is now doing a level 4 surface scan of the drive.  I may just leave this go, though I had forgotten just HOWWWW long SpinRite takes for a full surface scan.  It'll be working until tomorrow!

Thanks for your help!  I really appreciate it.

Tom

---

### Post by corrytonapple on 2010-08-05
> **Popeye.Tom said:**
> OK, I'll create a new disk.

I burned the ISO to disk using CDBurnerXP, but I let it run at full speed.

It did not want to put it on a CD, claimed the image was too large.  I burned it to a Sony DVD +R.  Could this be an issue?

I could copy the ISO image to a Win7 machine and try writing it to a FujiFilm CDR using the imbedded tools in 7.

Any thoughts on it being on a DVD being the source of the bad install?

Another option would be a USB thumb drive, but I'd have to check the BIOS and make sure it can use a USB port for boot, though it should!  

Also, MHDD 4.6 finished and found no errors.  SpinRite v6.0 is now doing a level 4 surface scan of the drive.  I may just leave this go, though I had forgotten just HOWWWW long SpinRite takes for a full surface scan.  It'll be working until tomorrow!

Thanks for your help!  I really appreciate it.

Tom
Ubuntu takes up less than 700MB. It won't expand on the CD. I burned my CD using the tools in 7.
Ubuntu recommends you use quality CD-R media.

---

### Post by Popeye.Tom on 2010-08-06
:)

I downloaded a new iso and did an MD5 check sum on it and it was good.  I burned and verified using the burn image functionality native in 7 and had it verify.

Reinstalling from this disc worked much better.  Ubuntu came up fine after the restart at the end of the installation.

I had the system download and install the Ubuntu tested and approved graphics drivers.

There are now the 244 updates that were available running.  It'll be fun to start using this and getting it really configured and setup well!

Corry, I really appreciate the time and patience you gave me in helping me resolve this.  I find it odd that it proved to be the disc burn when the disc check util from the GRUB menu said it was good.  But, the new disc worked when the original one did not, so I'm OK with that!

Cheers,
Tom

---

### Post by corrytonapple on 2010-08-06
You are welcome. Its what we all are here for.;)

---

### Post by tcbopper on 2010-10-30
No other tricks ??  I've installed freshy several times from CD, USB stick...no matter what I do it gets stuck at the hardware monitoring screen whenever I try to boot from the hard disk.  It boots fine from CD or the stick.  It sees the drives (when I boot from the CD and they are fine...I'm at a complete loss.  I even used the CD and it installed fine on another system....

Same mother board as you...AMD 635 Quad core
NVidia GT 9800

---

### Post by tcbopper on 2010-10-30
...memory test and disk test from CD boot menu find no errors.  I went as far as installing the 32 bit version "right next to it" from a DVD from Ububtu User DVD ....installs OK but whenever I try to restart or boot from the hard drive it hangs at the Hardware monitor screen.  SO now on a 640GB hard drive I've got 64 bit 10.10 and 32 bit 10.4 installed into their own partitions and am only able to boot from USB stick or cd/dvd........this is a fresh install so I can do/try anything...but i've tried to "start fresh" 8 or 9 times and it keeps coming to this.

---

### Post by tcbopper on 2010-10-30
OK....I think I know what the issue was/is....I had 2 640GB hard drives in the system....and I think the MB and Ubuntu were treating them as "1" in a "RAID" set up....I disconnected 1 of the hard drives and all is well......now.....I'll let everyone know if I have any luck getting a 2nd and 3rd hard drive in the system....plan on using it for entertainment/as a DVR....

---

### Post by corrytonapple on 2010-10-30
Tcbopper, could you please start a new thread with your issues? That would be better so people don't get the two issues confused. 
Thanks

---

### Post by tcbopper on 2010-10-30
OK...wasn't sure about how/what to do.  It was basically the same issue and pretty close to the same hardware as the original thread....is there a way to unsolve or "point" the new thread at "the old one"?

---

### Post by corrytonapple on 2010-10-30
> **tcbopper said:**
> OK...wasn't sure about how/what to do.  It was basically the same issue and pretty close to the same hardware as the original thread....is there a way to unsolve or "point" the new thread at "the old one"?
I would just create the new thread and link these old posts to the new one using quotes. Copy and paste them and stick it in the new thread. Do you still have an issue?

---

### Post by tcbopper on 2010-10-30
> **corrytonapple said:**
> I would just create the new thread and link these old posts to the new one using quotes. Copy and paste them and stick it in the new thread. Do you still have an issue?

Thank you for your time and seeing my post.....No, I don't have an issue anymore.  I believe the cause of the issue (for others) is that I had 2 hard drives connected to the mother board and the MB was trying to "RAID" them and Ubuntu was seeing 2 drives.  The solution was to reinstall w/ just 1 hard drive connected.

---

### Post by corrytonapple on 2010-10-30
> **tcbopper said:**
> Thank you for your time and seeing my post.....No, I don't have an issue anymore.  I believe the cause of the issue (for others) is that I had 2 hard drives connected to the mother board and the MB was trying to "RAID" them and Ubuntu was seeing 2 drives.  The solution was to reinstall w/ just 1 hard drive connected.
I am glad to see that your issue is solved. There is no need for you to start a new thread. I will note this fix for future reference. Have fun with your Ubuntu and if you need help post a new thread and I should see it.

---

### Post by JTU50 on 2010-10-30
I'm new to ubuntu and linux. Having the same type of problem posted here - installed from iso burned to cd. All I get on reboot is blinking underscore cursor. From reading the post here, I will try to download and burn new disk. Can someone tell me how to do an md5 checksum?
 
JTU50

---

### Post by corrytonapple on 2010-10-31
> **JTU50 said:**
> I'm new to ubuntu and linux. Having the same type of problem posted here - installed from iso burned to cd. All I get on reboot is blinking underscore cursor. From reading the post here, I will try to download and burn new disk. Can someone tell me how to do an md5 checksum?
 
JTU50
So I am assuming that you want to check the CD for errors. Boot from the CD and on that menu you get there should be an entry for "Check CD for Errors". Hover your selector over that and hit enter. It may take a while. Just my experience though. It is not always the CD though, in this case you may not have installed GRUB. Did you get a menu that let you install GRUB? Make sure there you click install GRUB. Do you still have Windows or did you wipe the whole Hard Drive (HDD or HD).

---

### Post by JTU50 on 2010-10-31
I did get a message asking me to install GRUB and I installed it. There is no other operating system present.  Disk checks out OK

---

### Post by corrytonapple on 2010-10-31
> **JTU50 said:**
> I did get a message asking me to install GRUB and I installed it. There is no other operating system present.  Disk checks out OK
If it is really bad than the Disk Check may be messed up too. Reinstall the ubuntu.iso to a new, high quality disk and see what happens. Reinstall using the whole Hard Drive to overwrite the corrupted install.

---

### Post by JTU50 on 2010-10-31
Update - I was able to boot from hd by using "boot from first hd" option on cd. Checked for grub in directory /boot. Received message that is wasn't installed (even though installation cd went through install) Received message to install grub by typing "sudo apt-get install grub" Did this and got returned message "package not available, but is referred to by another package This may mean package is missing, has been obsoleted or only available from another source. However the following packages replace it: grub-pc" Did install grub-pc which returned message "...grub-pc is already the newest version. 0 newly installed, 0 to remove and ) not upgraded"
 
Please advise

---

### Post by JTU50 on 2010-10-31
Problem solved, I think. When I originally installed Ubunto, I had no NIC card for this computer. It seems, GRUB is not on the CD, but must point to a site to get it and install. After installing NIC card and reinstalling from CD all works as it should - for now.

---

### Post by corrytonapple on 2010-10-31
> **JTU50 said:**
> Problem solved, I think. When I originally installed Ubuntu, I had no NIC card for this computer. It seems, GRUB is not on the CD, but must point to a site to get it and install. After installing NIC card and reinstalling from CD all works as it should - for now.
OK. If there are problems please post. We are here to help. ;)

---

### Post by JTU50 on 2010-10-31
It seems the issue is that this machine just takes a looooong time to boot.

---

