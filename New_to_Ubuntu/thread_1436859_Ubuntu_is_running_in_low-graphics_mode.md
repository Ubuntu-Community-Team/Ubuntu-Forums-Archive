---
title: "Ubuntu is running in low-graphics mode"
date: 2010-03-23
forum: New to Ubuntu
---

### Post by boxcorner on 2010-03-23
The following error was encountered.  You may need to update your configuration to solve this.
(EE) Failed to load /usr/lib/xorg/modules/driver/nvidia-drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

According to: System > Admin > Hardware Drivers
NVIDIA accelerated graphics driver (version 96) [Recommended]
This driver is activated and currently in use.

Ever since I re-installed Ubuntu, from time-to-time it hangs, requiring a re-boot.  This is the first time I've seen this error.
Any suggestions? Should I remove and re-install the driver? Thanks.

---

### Post by Daniel1994 on 2010-03-23
I've got this problem in my VBOX installation of lynx. I think *my *problem lies within Virtualbox, but if it doesn't, it might be the beta version.

are you running 10.04?

---

### Post by warfacegod on 2010-03-23
> **boxcorner said:**
> The following error was encountered.  You may need to update your configuration to solve this.
(EE) Failed to load /user/lib/xorg/modules/driver/nvidia-drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

According to: System > Admin > Hardware Drivers
NVIDIA accelerated graphics driver (version 96) [Recommended]
This driver is activated and currently in use.

Ever since I re-installed Ubuntu, from time-to-time it hangs, requiring a re-boot.  This is the first time I've seen this error.
Any suggestions? Should I remove and re-install the driver? Thanks.

Try removing then reinstalling the driver. If the recommended driver if the 96, that implies that your video card is somewhere more towards the elderly side of things. Might be a good idea to get a newer card. If you do, I strongly suggest you stick with an nVidia based card.

---

### Post by warfacegod on 2010-03-23
> **Daniel1994 said:**
> I've got this problem in my VBOX installation of lynx. I think *my *problem lies within Virtualbox, but if it doesn't, it might be the beta version.

are you running 10.04?

Its probably a combination of both. I tried Lucid for a brief time and got the same message. Most of the time, it wouldn't even be able to have X start. Running as a virtual machine is likely exacerbating your problem. Try Lucid Live without running virtual and see what happens.

---

### Post by Gregorybekkers on 2010-03-23
I've got the same card..
Download the driver from NVIDIA.
then exit the xserver
then install the Nvidia driver
sh <filename>
then u can type startx and that will start the xserver again.

---

### Post by warfacegod on 2010-03-23
The 96 driver has been around and well supported for years. I don't think anybody's even done any major work on it in some time (I could be wrong). Why would getting it from nVidia make any difference?

---

### Post by boxcorner on 2010-03-23
@ Daniel1994
No, I haven't installed VirtualBox.  On one occasion the number of workspaces collapsed from 4 to 2, consequently Compiz stopped working.

@ warfacegod
That's Plan-B ...

@ Gregorybekkers
It worked fine with my original Ubuntu installation.  The problem's only appeared since re-installation, when I created separate logical partitions.

**UPDATED**: Tuesday, 23 March 2010 @ 15:58:26
Removed the driver and re-booted.
**UPDATED:** Tuesday, 23 March 2010 @ 19:28:25
Ubuntu continues to crash, despite removing the driver,

Ubuntu is still not working properly.  
I removed the driver via: System > Admin > Hardware Drivers
Does that do a full uninstall?
According to: [https://help.ubuntu.com/community/NvidiaManual#Uninstalling the Driver]("https://help.ubuntu.com/community/NvidiaManual#Uninstalling the Driver") 
Uninstalling the Driver: Terminal > sudo sh NVIDIA* --uninstall
When I tried, result: Can't open NVIDIA*
Applications > Accessories > Search for Files > NVIDIA* finds 68 files in /etc, /lib, /usr and /var
Does "Can't open" mean files or directories are locked?
I'm not sure whether the problem is the driver hasn't been uninstalled properly, or if it's a hardware problem.
Any more suggestions?  Thanks.

---

### Post by warfacegod on 2010-03-23
```
sudo apt-get install envyng-core
```

This will install an app that will search out the best driver for your video card and install it.

---

### Post by boxcorner on 2010-03-24
@ warfacegod
Ran: sudo apt-get install envyng-core
Result: Setting up envyng-core (2.0.1ubuntu3) ...
EnvyNG option appeared in: Applications > System Tools
Mouse hover tool-tip shows: Install/Uninstall the ATI or the NVIDIA driver
Clicking on EnvyNG causes menus to close, but otherwise nothing seems to happen.
System > Apps > Hardware Drivers remains unchanged.
How do I know whether a driver is installed, or not?
**UPDATED:** Wednesday, 24 March 2010 @ 09:34:32
Google searched EnvyNG & found: [http://news.softpedia.com/newsImage/EnvyNG--2.png/]("http://news.softpedia.com/newsImage/EnvyNG--2.png/")
Guess that's what I should be seeing.
Also found: [https://wiki.ubuntu.com/EnvyNG]("https://wiki.ubuntu.com/EnvyNG")
"Unfortunately, currently it can cause conflicts ..."
EnvyNG seems not to be working as expected.  
**UPDATED:** Wednesday, 24 March 2010 @ 09:51:39
Tried: System > Admin > Synaptic, completely removed envyng-core & reinstalled.
Result: no change. Any more suggestions?  Thanks.

---

### Post by warfacegod on 2010-03-24
It's been a while since I used it, I forgot to tell you to install envyng-qt if you want a graphical interface.

Better yet, save yourself some disk space and run envy from the Terminal:

```
envyng -t
```

---

### Post by boxcorner on 2010-03-24
EnvyNG now runs & shows installed driver version 96.43.13-0ubuntu6
System > Admin > Hardware Drivers: shows NVIDIA (v96) inactive
"A different version of this driver is in use".
Does the activate button refer to the original v96 or the v96.43.13-0ubuntu6 installed by EnvyNG?
Should this be left as it is, or does it need to be activated for the driver installed by EnvyNG to take effect?

---

### Post by warfacegod on 2010-03-24
I think envy should have asked you if you would like it to activate the driver. Leave it alone for a bit and see if things are working properly.

---

### Post by dzon65 on 2010-03-24
> **warfacegod said:**
> I think envy should have asked you if you would like it to activate the driver. Leave it alone for a bit and see if things are working properly.

Envy ey?

---

### Post by boxcorner on 2010-03-24
> **warfacegod said:**
> I think envy should have asked you if you would like it to activate the driver. Leave it alone for a bit and see if things are working properly.
It's crashed several times since the new driver was installed.  I'm not convinced it's software related.  Appears more like problems I've seen before, caused by overheating.  Sometimes the display just freezes, whilst other times it breaks up.  Will investigate the hardware tomorrow and post an update, if I find anything significant.  Thanks for your help.

---

### Post by warfacegod on 2010-03-24
Ah! Crashing and freezing! Likely hardware related, yes.

---

### Post by boxcorner on 2010-03-25
Culprit seems to be graphics card heat-sink fan.  Sometimes fails to start when the system boots, but runs given a nudge.  Have ordered a replacement, meanwhile have left case open and jury-rigged another fan blowing on adapter cards.  Seems most likely cause.

---

### Post by warfacegod on 2010-03-25
> **boxcorner said:**
> Culprit seems to be graphics card heat-sink fan.  Sometimes fails to start when the system boots, but runs given a nudge.  Have ordered a replacement, meanwhile have left case open and jury-rigged another fan blowing on adapter cards.  Seems most likely cause.

Sounds like good temporary solution. I wouldn't run your system for too long like that though. Maybe an hour or two at most. Its almost certainly messing with the normal airflow for the processor.

---

### Post by boxcorner on 2010-03-25
> **warfacegod said:**
> Sounds like good temporary solution. I wouldn't run your system for too long like that though. Maybe an hour or two at most. Its almost certainly messing with the normal airflow for the processor.
Have my doubts that was the problem because the graphics card is now plenty cool enough, but Ubuntu still hangs so apps that are running continue to work but others can't be started.  The processor temperature seems fine.  Sometimes Ubuntu crashes, back to the password entry page, but the system itself doesn't crash forcing re-boot.  All this began since I did a manual install with ubiquity, creating logical partitions.  Originally I did a guided install with ubiquity.  I'm tempted to try another guided install, to be sure it's nothing to do with my configuration.  I can't make up my mind whether it's hardware or software, hence feel that a clean install would at least reduce the number of variables.

---

### Post by warfacegod on 2010-03-25
That was going to be my next suggestion, do a fresh install. I've never had any problems with, nor have I heard of, manual installs causing your problem. Unless, of course, you have some crazy partition scheme with lots of extended and logical partitions...:p

---

### Post by boxcorner on 2010-03-25
> **warfacegod said:**
> ... extended and logical partitions ...
Please correct me if I'm wrong, but as I understand it, a disk can hold just four primary partitions, only one of which can be divided into multiple logical partitions, which is known as an extended partition.  Hence it's the extended partition that contains logical partitions.  

BTW - My data is backed up on an external drive, which is connected via USB.  It's been disconnected today, while Ubuntu has been doing wild things.  Since I reconnected it this evening, to backup my Thunderbird profiles, Ubuntu has been running without a hitch.  Perhaps purely coincidental. Can't help wondering, though, whether it was connected when I reinstalled Ubuntu and hence might be related to this problem.  Obviously I'll need to leave it connected for a while and then run Ubuntu with it unmounted.  There's got to be a logical explanation to this problem somewhere.

PS - Crashed again, dropping me back at the password entry screen. Might try clean install during the weekend.  Meanwhile , will try leaving Windows XP running for a while, to see whether it continues crashing, to be sure it's not hardware related.

---

### Post by warfacegod on 2010-03-25
Yes, 4 primary partitions. An Extended partition would be counted as one Primary while containing several Logical partitions. Theoretically you can have as many Logical partitions as you like. I saw, in one case, a drive with the 4 Primaries and I think 18 Logical partitions. As you can imagine, it was an utter mess.

It is probably a coincidence. Unless you put your /home folder on the external, which isn't normally a good idea. If you have backup software set to automatically update your backups on that External, that might cause Ubuntu to misbehave itself. Although I don't know why it wouldn't have simply told you that the backup media wasn't present.

Before you do a new install, try this:

```
sudo apt-get purge gdm
```

Then:

```
sudo apt-get install gdm
```

You also might want to try opening Synaptic and under Edit (top left) selecting Fix Broken Packages.

---

### Post by boxcorner on 2010-03-26
> **warfacegod said:**
> ... Unless you put your /home folder on the external ... If you have backup software set to automatically update your backups on that External ...
Before you do a new install, try this ...
All my Ubuntu directories are logical partitions of /dev/sda1 (extended) including /boot.  I've since read that /boot should be on a primary partition.  I've read elsewhere that on older systems it should be completely below cylinder 1023, but I don't know what "older systems" means.  I built my desktop in 2003, so it's ancient.  My /dev/sda5 is mounted at /boot. I back up my data manually.  Windows XP ran an app all night without any glitches, so I'm inclined to think the problem is my Unbuntu installation, or configuration.  Thanks for the code.  Need to continue using Ubuntu today, will see how it behaves and then probably do a clean install tomorrow.  Will post updates.  I enjoy these challenges; I'm learning more about Linux.
_Updated Friday, 26 March 2010 @ 10:05:16_
Ubuntu crashed again: both panels, plus all windows and icons disappeared, just leaving the desktop window background.
Ran Fix Broken Packages in Synaptic: Successfully fixed dependency problems (seems to be standard message, so not sure that it actually fixed anything, because the same message is repeated each time it is run).
Ran sudo apt-get purge gdm & sudo apt-get install gdm.  An error was reported when I ran sudo apt-get purge gdm, but Ubuntu crashed back to the login page before I could copy & paste the error message here.  
After running  sudo apt-get install gdm an error message was displayed in a window on the desktop: "The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet Do you want to delete the applet from your configuration?"  I clicked on Delete.
A crash report icon appeared on the top panel:  Sorry, the package "gdm 2.28.1_Oubuntu2.1" failed to install or upgrade.  I clicked on Report Problem.

---

### Post by warfacegod on 2010-03-26
"All my Ubuntu directories are logical partitions of /dev/sda1 (extended) including /boot."

...which brings us right back to "some crazy partition scheme".:p

Here's an example of a good way to do things:

sda1 is my main partition. It contains only my OS. For manual partitioning during install, mark this simply as /. I wouldn't make this any smaller than 5 GB. At least 8 GB is better.

sda2 is my Home folder. It contains my files and stuff(obviously). Home is where Linux also stores most of your user settings. So if I do a fresh install, it will look and behave pretty much like the old install. If that ends up being a problem, I can hit Ctrl+H to show hidden files, highlight all the ".filename" stuff, delete it and everything reverts back to default. Simply mark as /home. This one can be any size you like.

sda3 and 4 are set up the same way for each other. sda3 is where I put Os's that I'm going to experiment with (read as "do bad things to"). sda4 is its Home folder. You can ignore 3 and 4, you likely won't need them.

Now, you'll notice that these are all Primary partitions and that I have no extended partitions, hence no swap. I don't Suspend/Hibernate (I forget which uses swap) nor do I do any video encoding so, for me, a swap partition becomes wasted space and slows down my system. A simple definition of swap space is: RAM on your hard drive. If I don't have swap, my system can't use it and therefor must use real RAM which is faster than seeking through and reading/writing to a spinning disc.

If you have a small amount of RAM, say 512 MB, then a swap partition would be a good idea. Only you can determine how big it should be. A good rule of thumb is equal to or bigger than your RAM but not much more than double. You'll need to create an Extended partition. Then within that, create a Logical partition to your desired size and mark it as /swap.

You also mentioned having Window XP. You'll want to be careful of not messing around too much with its partition size, if at all. XP is allot more forgiving of such things than Vista or 7 but it's still a risk.

One final note. You don't have to use sda1 and sda2 as I've described (hell, you don't have to use separate partitions at all if you don't want to). You can do it as sda2 and 4. The OS should be first though. If you have two Internal drives you can set it as sda3 as / and sdb2 as /home.

---

### Post by boxcorner on 2010-03-27
[FONT=Verdana]Well of course I didn't mean I'd literally put every single directory in a logical partition, indeed that would be crazy.  It's somewhat confusing though because the Ubuntu installation procedure itself allows separate partitions for /(root), /boot, /tmp, /var, /opt, /srv, /usr/local, /usr and /home to be created and some people such as yourself [/FONT][FONT=Verdana]recommend keeping some parts of the system (eg /home) partitioned[/FONT][FONT=Verdana], while others recommend putting /boot in a separate primary partition.  Nevertheless I appreciate your advice and would have gladly followed it if I could and had I not already proceeded as follows.

After my last post I tried to run apt-get purge gdm & sudo apt-get install gdm again, so I could note the error message ... of course it crashed part way through. I tried running them again, but was stuck at the command prompt and not knowing enough about how to get back to the GNOME gui decided to do a clean re-install for dual boot, earlier than planned. 

I used gparted from live CD to delete the Linux partitions on /sda, [/FONT][FONT=Verdana]leavingXP on /sda3. My NTFS Windows data is on /sdb.[/FONT][FONT=Verdana]  I then selected install alongside existing OS only to find Ubuntu had partitioned and installed with a swap partition on /sdb !  So I returned to gparted deleted the Linux partitions on /sdb and then used the manual option to force Ubuntu to install on /sda, alongside XP.[/FONT]

Not having yet read your post, I chose to try putting /boot in a separate primary partition, so /boot is now mounted at /sda1 and /(root) is mounted at /sda2 with extended logical partitions for /home, etc. The installation seemed to force a swap partition.  I'll try this setup for a while.  If the glitches continue then I'll try a scheme that's more akin to yours, without /boot in a separate partition and without a swap partition, if I can.  Anyway, I have had an interesting tour of the live CD and learned a bit more about the way gparted and the way the different installation options work.  So, it's been fun.

---

### Post by warfacegod on 2010-03-27
Allot of this is personal preference. That's why you'll find different folks recommending different things. As far as the swap goes, I assume its popping up a window saying something "You have not specified a swap partition. It is recommended blah blah blah... ". Just click continue. It should go to the next step without making swap.

---

### Post by boxcorner on 2010-03-27
Ubuntu crashed again, so I purged and intalled gdm again, ran gparted and deleted the Linux partitions, again.  Then I re-installed Ubuntu following your suggested scheme.  So now I have sda1 mounted at /(root), sda2 mounted at /home and sda3 is my NTFS partition for XP.

Yes, it was popping up a window, saying something about not having specified a swap partition.  Previously, when I installed Ubuntu, I went back and set up a swap partition, but this time I actually read the entire message to the end and when I realised that I probably had enough RAM, I continued on as you suggested.  So now I don't have a swap partition.

Then I ran Memtest86+ ... after about an hour, suddenly the lower half of the screen was filled **[COLOR=Red]red [/COLOR]**with fast scrolling lines of **errors**.  It reached 294912 errors, before it stopped scrolling and the test continued.  Explains why  Ubuntu has been crashing!  There are 3 slots on the motherboard.  Originally I had two 256MB modules, but a few weeks ago I added a 1GB module.  Everything has been fine until recently, so not sure why one of the modules has failed.

I need time to read-up on Memtest86+ to figure out how best to isolate the faulty module.  I'm aware of [http://memtest.org/](http://memtest.org/) but any tips would be much appreciated.  Obviously, I could physically remove one module at a time and by process of elimination identify the faulty one that way.  However, presumably there is some way of doing it with Memtest86+ using ranges of addresses.

_Updated Saturday, March 27 2010 @ 15:09_
Have discovered [http://www.qbs-pchelp.co.uk/memoryproblems.html](http://www.qbs-pchelp.co.uk/memoryproblems.html) which is helpful and includes a useful methodology for determining which module is faulty.  Clearly this is going to take some time to resolve, but I now seem to be on the right track, at last.

_Updated Sunday, March 28 2010 @ 09:35_
No errors were reported by Memtest86+ when I tested each of the 3 memory modules individually in DIMM slot 1.  None were reported by Memtest86+ when I inserted the 1GB module in slot 1and when either of the two 256MB modules were inserted in slot 2.  None were reported by Memtest86+ when I inserted one of the two 256MB modules in any of three slots.  However, Memtest86+ reported many errors, as it did before, when I inserted the 1GB module in slot 1 and each of the 256MB modules in slots 2 and 3.  There are other permutations that could be tested, but it is very time consuming.  According to website listed above, my computer's motherboard or CPU might be faulty :-(

Does anyone here have expert knowledge on how best to use Memtest86+ in a situation like this?  For example, Memtest86+ lists my CPU and motherboard's chipset, but does it test their memory too, or only the memory modules inserted in the slots?  Presumably there some way of using the addresses referenced by the errors to diagnose exactly where the fault it located.  If so, how?  I'm aware that Memtest86+ should be left to run for at least 7 iterations.

_Updated Sunday, March 28 2010 @ 10:50_
I have now downloaded Memtest86+ v3.5 so will use that for further testing.  Meanwhile, any tips or pointers would be much appreciated.

---

### Post by warfacegod on 2010-03-28
I don't know much about memtest86 so I can't help you there. It sounds like your troubles started after you installed the 1 GB RAM card. I'm going to venture a guess here. It seems to me that the RAM cards you have aren't quite compatible with each other in your motherboard. Perhaps your cards have different latencies and the mother board is incapable of correcting for it. Could be they just don't like each other.

Check each RAM card to see if all of the specs match. Aside from the actual size of course.

---

### Post by boxcorner on 2010-03-28
I removed a 256MB module from slot 3 this morning and Ubuntu ran all day without a hitch. :D 

I intend to do more testing overnight.  I understand your suggestion, though I think it's unlikely because I bought the 1GB module from Crucial.   Before doing so, I downloaded, installed and ran their free diagnostic software and then double-checked its compatibility by phone, before ordering the DIMM on-line.  I plan to get another 1GB module sometime, so the 256MB ones will eventually be replaced.  

My desktop PC's been running fine for a few weeks now, however I did have a problem with the PSU but I replaced it before I increased the RAM.  Perhaps the motherboard, or one of the DIMMs were damaged when the PSU failed.  However, if that's that case then it's a bit odd that the problem's taken so long to surface.

---

### Post by warfacegod on 2010-03-28
Crucial RAM is excellent as well as their finder tool. I generally use their tool to decide which of their RAM I need and then buy it from newegg. The last time I got RAM, Crucial wanted to sell me two 1 GB cards for $230. US with shipping. I found the exact same Crucial RAM on newegg for $110 US shipped.

OCZ and Corsair also make excellent RAM.

Not necessarily odd. Computers are strange beasts sometimes. Some components can still run after being damaged in minor or even moderate ways. I have a video card with several transistor looking things broken off of it yet it still works.

---

### Post by boxcorner on 2010-03-29
Memtest86+ ran last night with the 1MB module in slot 1 and the second of the two 256MB modules in slot 2, without reporting any errors.  I intend to start testing the two module permutations involving slots 2 and 3 tonight.

It's certainly a bit puzzling.  Maybe a more logical pattern will emerge when it's been tested more thoroughly.  Hopefully the problem rests with socket 3 and not the CPU or the chipset.  Though Memtest86+ didn't report any errors when I ran a short test with only a single 256MB  module in slot 3, which is a bit worrying.

Assuming the computer uses the RAM incrementally beginning with  slot 1, then perhaps the problem occurred intermittently because the computer's requirement for RAM varies according to the demands being placed on it. Consequently the virtual addresses located in the 3rd memory module were being accessed less frequently.  Memtest86+ has only ever reported errors when all three slots have been occupied.  

If slot 3 is damaged then the computer would still be usable, but diagnosing whether it's the motherboard or CPU that's faulty would be tricky and of course much more expensive.

Anyway, thanks for the tips.  Some US suppliers won't ship abroad, or insist on customers buying from their overseas distributors, but it certainly sounds worthing checking.

---

### Post by warfacegod on 2010-03-29
Computers use RAM in order. Closest to the processor first, farthest is last.

---

### Post by boxcorner on 2010-03-30
Memtest86+ didn't report any errors when I left it running again last night, this time with one of the the two 256MB modules in socket 3 (ie slots 1 and 2 were empty).

---

### Post by warfacegod on 2010-03-30
I still think you might have some difference in the RAM cards that your motherboard can't handle. Using Crucials utility won't tell you if the RAM it suggests is totally compatible with what is already installed in your system.

---

### Post by boxcorner on 2010-03-30
> **warfacegod said:**
> I still think you might have some difference in the RAM cards that your motherboard can't handle. Using Crucials utility won't tell you if the RAM it suggests is totally compatible with what is already installed in your system.
With these same memory modules, Windows XP ran perfectly for a number weeks, before I installed Ubuntu.  Then Ubuntu ran perfectly, until I reinstalled it.  Originally, I thought the problem was connected with the re-installation, then the graphics driver and so on.  It's easy to get diverted and misinterpret causes of problems in situations like this.  I now believe the timing of the re-installation just happened to be coincidental.

Like you, I was cautious about mixing memory.  In fact, I phoned Crucial, before I placed my order and specifically asked that question, because I was worried about it.  Curiously, Memtest86+ didn't report any errors when the 1MB module in socket 1  was tested with one 256MB module in slot 2 and slot 3 was empty.  The problem only occurred when all 3 slots were filled.  You might well be right, but I have yet to run an all night test with the second 256MB module alone in slot 3.  I'd prefer to get that done first, before rushing into buying another 1GB memory module.  In fact, I'd also like to test the 1GB in socket 2, with a single 256MB module in slot 3, keeping slot 1 empty. Only then will I be convinced that it's definitely something to do with having all 3 slots filled, rather than the 3rd socket being faulty. 

Apparently Memtest86+ should be run for at least 7 iterations, hence it's more convenient for me to run the tests at night, as I need to use Ubuntu during the day.  In a way, I'd be quite happy if you were right, but I fear the motherboard is faulty.  I don't want to waste money buying another 1GB module, if there's a motherboard fault preventing memory addresses somewhere above 1GB+256MB from being accessed properly.  If I end up having to replace the motherboard then my memory modules might be incompatible.  My preferred option would be for slot 3 to be faulty, in which case I could put another 1GB module in slot 2 and simply leave slot 3 empty ... then problem solved.

Meanwhile, Ubuntu's been running like a dream, all the while I keep to 1GB+1MB.  So I no longer have any doubts that I'm headed in the right direction, running Ubuntu ... even if I'm not sure which particular path to follow to get out of this maze!

_Updated Wednesday, March 31 2010 @ 09:16:23_
According to [http://www.memtest86.com/#commands]("http://www.memtest86.com/#commands") "... the test has no knowledge of the memory or CPU type ..." so apparently the only way to prove your memory module incompatibility theory would be to buy another 1GB module.

Memtest86+ didn't report any errors when I left it running overnight, this time with the 1GB module in slot 2 and one of the two 256MB modules in socket 3 (leaving slot 1 empty).  However, the the recommended number of passes wasn't exceeded, the it needs to be left running  longer, so I'm postponing this particular test until Friday.  Meanwhile, I intend to run another single module test tonight.  

Despite the fact that last night's test was incomplete and hence inconclusive, it suggests that socket 3 is not faulty.  Also, the tests thus far suggest that the 1GB module can be used together with the 256MB one, in any pair of adjacent slots, with impunity.  Which reinforces the idea that the problem only occurs when memory addresses in excess of 1GB+256MG are accessed.  Hence my reluctance to purchase another 1GB.  It might work, or it might not.  I doubt there's much of a market for used memory modules.

---

### Post by warfacegod on 2010-03-31
Are you running a Dell by any chance? Some dells don't like having all of the memory slots taken up. eMachine and a few other brands of similar quality are sometimes the same way. It comes from using the cheapest parts possible to build them. The specs that are on paper for your motherboard are theoretical. The reality could be something utterly different. Part of the reason that parts are cheaper is because less testing was done on them.

I'm not suggesting that you get another 1 GB card (although 2 GB is better than 1:p).
> 
Despite the fact that last night's test was incomplete and hence inconclusive, it suggests that socket 3 is not faulty.

Personally, I would come to opposite conclusion. Has that happened with the other slots with any combination of RAM cards?

---

### Post by boxcorner on 2010-03-31
> **warfacegod said:**
> ... a Dell ...?
No, an old PC that I built way back in 2003, using an MSI KT3 Ultra-ARU motherboard and Athlon XP 1900 CPU. 
> **warfacegod said:**
> ... (although 2 GB is better than 1:p).

Yes, when it works ...
> **warfacegod said:**
> 
I would come to opposite conclusion. Has that happened with the other slots with any combination of RAM cards?
No, perhaps you misunderstood my post.  Previously I was testing single modules in individual slots. I've only recently begun testing pairs and more recently become aware of the need to run the test for more than 7 passes.  Testing 1GB+256MB modules together is tedious and last night simply wasn't long enough.  The test didn't get stuck; it had reached 6 and was still running, only I needed my PC for work.  I'll be able to repeat this particular test for much longer, starting during the day on Friday and running overnight.  Memtest86+ doc doesn't inspire much confidence: "... not all errors reported by Memtest86 are due to bad memory" ... "There have been numerous reports of errors in only test 5 on Athlon systems."

---

### Post by warfacegod on 2010-03-31
Sorry, I didn't realize that you stopped the test. I don't think you specifically stated that. Could be wrong though.

I had forgotten that you said you built this rig about seven years ago, again my fault. Bear in mind that seven years is physically old for electronics. I'm not talking about obsolete but actual wear on the electronics themselves.

If I recall, you said that it works fine with the 1 GB in slot 1 and the 256 in slot 2. Have you considered just leaving it at that? Another 256 isn't going to make much of a difference.

---

### Post by boxcorner on 2010-03-31
> **warfacegod said:**
> ... I didn't realize that you stopped the test ...
I don't think it stops itself, unless I'm missing something.

> **warfacegod said:**
> ... actual wear on the electronics themselves ...
Eons ago, when I studied such things, the MTBF curve looked like a tab (ie slope up, level off, drop down), though I gather nowadays it's sometimes referred to as the bathtub curve.  About as logical as a hierarchical root structure being referred to as a 'tree'.  MTBF for components being 'burned in' during initial test was likened to the light-bulb effect, either fails immediately, or lasts for ages, before dying.

> **warfacegod said:**
> ... Another 256 isn't going to make much of a difference ...
Actually, for some apps that I use, more would definitely be better (eg Blender).  My laptop died, hence I resurrected this desktop.  I cannibalized the hard drive though and housed it, so now it's a handy portable external USB backup drive.  Anyway, enough chat, it's time I started another test run.

---

### Post by JKyleOKC on 2010-03-31
> **boxcorner said:**
> Eons ago, when I studied such things, the MTBF curve looked like a tab (ie slope up, level off, drop down), though I gather nowadays it's sometimes referred to as the bathtub curve.  About as logical as a hierarchical root structure being referred to as a 'tree'.  MTBF for components being 'burned in' during initial test was likened to the light-bulb effect, either fails immediately, or lasts for ages, before dying.Actually, the "bathtub curve" label makes perfect sense if it's plotted as the Time TO Failure, which is the inverse of the MTBF and is what the manufacturers actually measure...

Some motherboard designs require that RAM chips be installed in matched pairs; one of my machines (about four years old now) has that requirement although most have not had it since the very early days.

I've also found by experience that a flaky RAM chip can cause very different results depending on which slot it's in. Most mobo manuals specify a sequence for using the slots, since the addressing may be determined entirely by how the slots are wired (i.e. only one of the slots may provide an address of 0x00000000) since the chips themselves cannot have a fixed address associated with them.

---

### Post by boxcorner on 2010-04-01
> **JKyleOKC said:**
> ... Time TO Failure ...
i c thanks, that seems perfectly logical

> **JKyleOKC said:**
> ...
Some motherboard designs require that RAM chips be installed in matched pairs ...
Nevertheless, KT3 Ultra user's guide says, "Memory modules can be installed on the slots in any order.  You can install either single- or double-sided modules to meet your own needs."  It goes on to say DIMMs can be combined in bank 0&1, 2&3 or 4&5 and total memory in each can be 64MB-1GB.  So, my DIMM modules and their insertion locations would appear to comply fully with requirements.

> **JKyleOKC said:**
> 
I've also found by experience that a flaky RAM chip can cause very different results depending on which slot it's in. 
Also, according to the documentation "... not all errors reported by Memtest86 are due to bad memory". That's quite a puzzle, given the number of permutations and variables, plus there's the added dimension of possible bugs in the test software - some have already been documented.  Intermittent hardware problems like this are tricky. Buying another 1GB module would appear to be the easiest way forward.

Anyway, I tested the 1GB module alone in slot 3 last night and Memtest86+ didn't report any errors.  I will test the 1GB in slot 2 with a 256MB module in slot 3 again tomorrow and then probably repeat the original test with all 3 slots filled again, before buying another 1GB module.

---

### Post by warfacegod on 2010-04-01
> Memory modules can be installed on the slots in any order.

While this may be true, it is generally best to put the biggest/fastest in the slot closest to the processor.

> MTBF for components being 'burned in' during initial test was likened to the light-bulb effect, either fails immediately, or lasts for ages, before dying.

In my experience with computers, from about 2001 onward, "ages" is seven years. I've worked with dozens of computers that start showing performance losses at about 5.5 to 6 years, even with a freshly installed OS on a new HDD. At around 7 years, they become so unreliable that using them or even salvaging any of the parts in them becomes pointless. The video card is usually about it. That isn't to say all computers from 2001 onward will do this but there have certainly been enough for me to see a pattern.

---

### Post by boxcorner on 2010-04-01
> **warfacegod said:**
> ... it is generally best to put the biggest/fastest in the slot closest to the processor ...
That's how they were arranged when the fault first occurred.

> **warfacegod said:**
> 
... In my experience with computers, from about 2001 onward ...


By comparison with mine, I probably belong in a museum.

> **warfacegod said:**
>  ... At around 7 years, they become so unreliable that using them or even salvaging any of the parts in them becomes pointless ...
Seven year itch?

---

### Post by warfacegod on 2010-04-01
I meant the computers themselves from 2001 forward. Although that is about when I started using them consistently. I've worked with plenty from the 90's also (PII and PIII "eras") and they seem to last longer. One example. I've got my wife on a Gateway from '98 with an AMD and the only thing wrong with it is that the USB's don't work and she fried them herself. If she hadn't, the thing would still be perfectly good.

---

### Post by lavinog on 2010-04-01
How much was the 1G ram?  I sometimes find that old ram upgrades can sometimes cost more than replacing the cpu/mobo/memory.

Also you mentioned that you have a 1M module..."all the while I keep to 1GB+1MB." is this correct?  Why even bother with 1M?

When you use memtest for different combinations, keep track of the information on the top left...If you notice a drastic speed difference between combos, that could be a part of your problem.
I find it best to do a partial test for each combination first (spend no more than 10mins)  You could save yourself a bunch of trouble if it finds an error immediatly.

I did not see that you tried memtest with all memory modules in place.  That would have been the first thing I would have tried.

---

### Post by JKyleOKC on 2010-04-01
I had a PII-MMX box running from 1995 until last October; it went out rather spectacularly when I shut it down and later tried to power it up. The power switch shorted and literally blew up. Not long afterward I replaced two other boxes that had been in service for more than 10 years. In all cases I salvaged the hard drives, all of which are still readable using a USB adapter; this lets me refer back to the ancient files when I need to.

I think the most frequent cause of this age limit is that the electrolytic capacitors on the boards eventually dry out and go bad.

In any event, the new replacement machine I got to replace the 14-year-old casualty runs much quieter and uses only about half the power of the old one despite having some 25 times as much RAM (2 GB instead of 80 MB) and much larger disks (250 GB instead of 80 GB). I'm now considering replacing the two remaining single-CPU boxes...

---

### Post by boxcorner on 2010-04-01
@ warefacegod
Nevertheless, I'm a dinosaur by comparison. Not all absolute beginners with Ubuntu necessarily lack experience using computers, other OS's, machine languages, etc.  Have you considered putting a USB adapter card in your wife's PC?

@lavinog
1GB, 184-pin DIMM from Crucial cost 26,45 EUR (ie approx 36 USD).  I'd be most impressed if you can show me where I can buy a better CPU, motherboard and memory for that price. The three memory modules are 1GB plus two 256MB ... not 1MB! Memtest86+ documentation recommends a minimum of 7 passes, but nevertheless thanks for the tip.  Yes, naturally I ran Memtest86+ with all 3 modules in place.  That's how the memory fault was identified in the first place.

BTW - Just for the record.  I've noticed that the bootable version that I downloaded, and have been using for testing, is actually called Memtest-86 v3.5, so references in my posts to Memtest86+ derive from the version displayed in my dual-boot installation of Ubuntu 9.10

@JKyleOKC
You haven't said how you intend to replace them, but I prefer to build my own PCs and upgrade rather than replace them entirely.  The modular construction of desktop PCs and ATX motherboard size standard readily lend themselves to this kind of approach.  It's possibly better for the environment, certainly better for my bank balance and I enjoy the learning experience.

---

### Post by JKyleOKC on 2010-04-01
> **boxcorner said:**
> You haven't said how you intend to replace them, but I prefer to build my own PCs and upgrade rather than replace them entirely.  The modular construction of desktop PCs and ATX motherboard size standard readily lend themselves to this kind of approach.  It's possibly better for the environment, certainly better for my bank balance and I enjoy the learning experience.I agree fully with you; the two boxes I mentioned are both more or less home-built. One came from a custom builder but I've since replaced its mobo twice (and the CPU both times) plus all of the drives. The other was a "bare-bones" package from a local parts house which I've also upgraded several times.

However at my age (I'm in my 80th year) it's become more difficult to handle all the parts, so that newest box came from Office Depot where it was on sale for just over $300 with 2 GB of RAM and an AMD dual-core CPU. I couldn't have bought the parts for that price, nor could I have been back up and running so rapidly! If I do replace the two old boxes, I'll probably have a single machine custom built at a local parts house so that I get exactly what I need and little or nothing more.

Both boxes are mini-towers (four 5.25-inch bays on the front panels) and the only parts in them that would be worth keeping are the cases themselves and one DVD-writer. Their hard drives are nearing EOL and are only 80 GB each, and one of them has PC133 RAM while the other is original DDR. Both are Athlon CPUs, but only 1 GHz. Neither power supply would be suitable for a modern mobo, so total replacement is probably the best bet.

For nearly 15 years I've been doing database recovery for applications that are based on Btrieve/Pervasive record managers, and it's a pretty fair supplement to Social Security. However it requires that I maintain Windows capabilities since that's what most of my clients use. My solution to this is VirtualBox and with adequate RAM and multi-core CPUs it does everything I need and has plenty of snap...

---

### Post by warfacegod on 2010-04-01
> Nevertheless, I'm a dinosaur by comparison. Not all absolute beginners with Ubuntu necessarily lack experience using computers, other OS's, machine languages, etc. Have you considered putting a USB adapter card in your wife's PC?

Gee, now you make *me* feel like a new guy.:p I've been around here long enough to figure out that most of the new guys are coming from Windows. Besides, you've shown, over the course of this thread, that you have a solid grasp of computing. LLLOOOOONNNNNGGGGGG story involved with the USB's in my wife's computer. Very short, put one in, took it back out when I was done with it.

Apparently there is some consensus on the old boxes lasting longer.

---

### Post by boxcorner on 2010-04-03
Ubuntu runs without a hitch when 1 or 2 memory modules are inserted, but not 3.  All modules have been tested in all 3 slots, in a variety of combinations, without any errors being reported.  The only time Memtest reported errors was when all 3 slots were filled.

Memtest-86 v3.5 ran yesterday and overnight with the 1GB module in slot 2 & a 256MB in slot 3, more than exceeding the required number of passes, without reporting any errors.

I will run Memtest once again tonight, with all 3 slots filled, just in case the problem is/was intermittent contact(s), perhaps caused by dirt.  If Memtest continues to report errors then I'll order another 1GB module (so I can run the 2 DIMMs adjacent to each other (in slots 1 & 2). 

@JKyleOKC
I fully understand.  I expect I'd do the same if I was in a similar situation myself.  I've hardly used Windows XP since I migrated to Ubuntu.  I've re-installed Ubuntu several times now, found it to be quick and easy compared with Windows.  There are none of the hassles associated with reactivation, constant updating of anti-virus, anti-spyware, etc.  Ubuntu works for me and works well.  When the PSU in this desktop failed, I replaced it with a more powerful quieter model, with a view to eventually upgrading the motherboard and CPU.  The case, optical and magnetic drives and adapter cards are all fine, though I might also upgrade the graphics card.  If/when I upgrade my hardware I might try visualization, or emulation and ditch dual-boot.

@ warfacegod
I become increasingly aware of my fallibility, as each year passes by, so am always happy to receive good advice from someone with more experience in something that's new to me.  It's helpful having someone to test my logic against.  Hardly surprising that most newcomers to come from Windows though, given it's dominance.  In my case, I used CLIs long before GUIs were invented, punched tape and cards long before the 8" floppy was invented, and Ge (later Si) transistors long before the microprocessor was invented.  I used PCs intensively during the late 80s, but since then have only built them for myself and family.  I've probably forgotten more than I can any longer remember.  Since then my involvement has been with software rather than hardware.  Consequently, I appreciate your willingness to share experiences with more up-to-date hardware and I'm grateful for your help in grappling with this problem.

It's bizarre.  When I returned the memory modules to their original positions (ie 1GB in slot 1, 256MB in slots 2&3), my PC ran perfectly trouble-free.  I fully expected Ubuntu to start crashing again, as it did before, but it didn't.  

Anyway, I'd already made up my mind to get another 1GB modules.    I needed to go away, so I ordered another 1GB module from Crucial  and then left Memory-86 v3.5 running for a couple of days.  When I got back, I expected to find a list of errors.  Instead, I discovered it had run 15 passes error-free.  So, now I'm completely puzzled - I'm not sure what to think, except Murphy's Law springs to mind!  

I should be happy, but I would rather understand why it kept crashing the way it did.  The contacts on the modules and sockets are gold-plated, so there shouldn't be a high-resistance or intermittent contact problem, unless perhaps some speck of dust/dirt was  dislodged during all the swapping around.  I will install the 2nd 1GB module, when it arrives, and continue using Ubuntu for a few days, before closing this thread, unless of course it starts crashing again ...

---

### Post by lavinog on 2010-04-08
Dust could have been the issue.  Maybe the constant reseating knocked it off. (did you look under the mobo?)

---

### Post by warfacegod on 2010-04-08
Have you gotten any updates during this process? There could have been some unrelated software issue that coincidentally started when you put in the new RAM and that has since been fixed by an update.

---

### Post by boxcorner on 2010-04-08
> **lavinog said:**
> ... (did you look under the mobo?)
Yes, I took the motherboard out recently, to put a new heatsink that I got from QuietPC on the chipset.  While it was out, I used a small brush and vacuum cleaner to remove as much dust as possible from inside the case, on the fan blades, etc.  Dust does seem to be the most likely cause, though.  It never ceases to amaze me, how much accumulates in PCs.  I'm gradually reducing fan noise.  When I replaced the PSU, I put in a higher powered model with a large single fan.

> **warfacegod said:**
> ... any updates during this process? There could have been some unrelated software issue that coincidentally started when you put in the new RAM and that has since been fixed ...
I run Update Manager daily, download and install all that it lists, plus I reload Sypnaptic and use it to mark, download and install upgrades. So, I suppose that's a possibility, too.  I was surprised by how much RAM has increased in price since January.  

_Addendum_
I've been running Ubuntu ever since I stopped the test and it's been perfectly stable.  The more I use this OS, the more I like it.

---

### Post by warfacegod on 2010-04-08
I run Update Manager daily, download and install all that it lists, plus I reload Sypnaptic and use it to mark, download and install upgrades. So, I suppose that's a possibility, too. I was surprised by how much RAM has increased in price since January.

You're running an older system and older RAM especially can get expensive as it becomes "obsolete". As fewer and fewer of them are made it gets to be more expensive to make them, keep production equipment around (and maintain), and ship.

---

### Post by lavinog on 2010-04-08
> **boxcorner said:**
>  Dust does seem to be the most likely cause, though.  It never ceases to amaze me, how much accumulates in PCs.  I'm gradually reducing fan noise.  When I replaced the PSU, I put in a higher powered model with a large single fan.

Some cases come with filters now to reduce dust accumulation.
In the past I used dryer sheets...they doubled as an air freshener.

---

### Post by boxcorner on 2010-04-08
> **warfacegod said:**
> ... older RAM especially can get expensive as it becomes "obsolete". As fewer and fewer of them are made it gets to be more expensive to make them, keep production equipment around (and maintain), and ship.
That's undoubtedly true in the longterm, but I would have thought it less likely to be the sole reason for price rises over a period of just a few months.  I've noticed that the price of RAM tends to fluctuate, much like the cost of oil.  So, my guess is it has as much to do with demand as with supply.  The world's economies are improving, so people are beginning to spend more, increasing demand.  Prices tend to rise when supply can't keep up with demand.

> **lavinog said:**
> Some cases come with filters now to reduce dust accumulation ...
That's interesting; I didn't know that.  Excellent idea, particularly if the filters are washable instead of disposable.
> **lavinog said:**
> ... I used dryer sheets...they doubled as an air freshener.
What you mean by "dryer sheets"?  Some sort of filter material available in sheet form, if so where did you get it from?

---

### Post by lavinog on 2010-04-08
> **boxcorner said:**
> That's undoubtedly true in the longterm, but I would have thought it less likely to be the sole reason for price rises over a period of just a few months.  I've noticed that the price of RAM tends to fluctuate, much like the cost of oil.  So, my guess is it has as much to do with demand as with supply.  The world's economies are improving, so people are beginning to spend more, increasing demand.  Prices tend to rise when supply can't keep up with demand.
[http://www.pcmag.com/article2/0,2817,2360019,00.asp](http://www.pcmag.com/article2/0,2817,2360019,00.asp)

> That's interesting; I didn't know that. Excellent idea, particularly if the filters are washable instead of disposable.
They are washable. It is a wiremesh.
[http://www.antec.com/demo/minip180/minip180_flash.html](http://www.antec.com/demo/minip180/minip180_flash.html)

> What you mean by "dryer sheets"? Some sort of filter material available in sheet form, if so where did you get it from? 
They are normally used for eliminating static cling when drying clothes in a clothes dryer. It is usually near the laundry detergent.

---

### Post by warfacegod on 2010-04-08
> **boxcorner said:**
> That's undoubtedly true in the longterm, but I would have thought it less likely to be the sole reason for price rises over a period of just a few months.  I've noticed that the price of RAM tends to fluctuate, much like the cost of oil.  So, my guess is it has as much to do with demand as with supply.  The world's economies are improving, so people are beginning to spend more, increasing demand.  Prices tend to rise when supply can't keep up with demand.

The condition of the Worlds economy is highly debatable and could easily lead to a political discussion (been there, done that, not doing it again). I'll just say this about the economy. I'm in Connecticut, U.S. and I'm not seeing any improvement nor does anyone I know in the U.S. nor do the people I know in several western European countries.

Supply and demand is another reason for the prices going up but I think you may have answered your own question. You mentioned oil. It's a vital part of the entire production process. The cards are plastic. The factories and machines need lubricant (don't know if it's oil based or not but it's likely). The trucks that ship the RAM need Diesel fuel which is made from oil. With oil prices going up (again), I'm not surprised in the least that your RAM costs more from a few months ago.

---

### Post by boxcorner on 2010-04-09
> **lavinog said:**
> ... pcmag ... article ...
... They are washable. It is a wiremesh ...
... usually near the laundry detergent ...  
Interesting article.  Superb case.  Haven't seen dryer sheets (in the EU).  Thanks.

> **warfacegod said:**
> ... the people I know in several western European countries ...
... your RAM costs more from a few months ago ...
Your tally plus this one ;) who paid 38,26 EUR (ie approx 51.15 USD) for the 2nd 1GB 164-pin DIMM.

_Addendum_
Here's something topical that you might find interesting [http://news.bbc.co.uk/2/hi/technology/8609885.stm]("http://news.bbc.co.uk/2/hi/technology/8609885.stm")

---

### Post by warfacegod on 2010-04-09
Possible A.I. solution? Terminators here we come!:P

---

### Post by boxcorner on 2010-04-10
The 1GB module arrived yesterday; now inserted in slot 2. Hence, System > Administration > System Monitor reports Memory 2.2 GiB 

Ubuntu no longer misbehaves or crashes; I'll run/test it for a day or two and then close this thread.  Thanks to everyone for all their help and suggestions.

> **warfacegod said:**
> Possible A.I. solution? Terminators here we come!:P
Who knows?  We certainly are living in exciting times.  This new development [[http://news.bbc.co.uk/2/hi/technology/8609885.stm]("http://news.bbc.co.uk/2/hi/technology/8609885.stm")] seems likely to change many aspects of our lives.  If the Chua & Williams *memristor* proves to be as revolutionary in electronics as the Bardean & Brattain *transistor* was, then the rate at which technology is progressing might be about to ramp up considerably.

---

### Post by JKyleOKC on 2010-04-10
> **boxcorner said:**
> Interesting article.  Superb case.  Haven't seen dryer sheets (in the EU).  Thanks.

The brand name my wife uses is Bounce (we're in the USA). Their primary function is to serve as a fabric softener, replacing the usual liquid that's added to the wash cycles. You may find them in that area of the stores...

I hadn't realized that they were porous enough to serve as filters, though. Since I have three cats, whose shed fur tends to clog up fans in a hurry, I'm going to try the idea out on my machines!

---

### Post by boxcorner on 2010-04-12
Mouse pointer froze while I was using the Epiphany browser.  Not sure if this related to the original problem.  Perhaps I [SOLVED] this thread too early!

---

### Post by warfacegod on 2010-04-12
> **JKyleOKC said:**
> The brand name my wife uses is Bounce (we're in the USA). Their primary function is to serve as a fabric softener, replacing the usual liquid that's added to the wash cycles. You may find them in that area of the stores...

I hadn't realized that they were porous enough to serve as filters, though. Since I have three cats, whose shed fur tends to clog up fans in a hurry, I'm going to try the idea out on my machines!

I've used them as temporary replacements for vacuum filters.

---

### Post by egalvan on 2010-04-13
> **boxcorner said:**
> Mouse pointer froze while I was using the Epiphany browser.  Not sure if this related to the original problem...

BoxCorner, I've lost track of who has the older hardware...

Have you done a close visual inspection of the capacitors on the motherboard? (and video card, and power supply...)

Here are two links with better info than I could type (I'm tired)

[http://en.wikipedia.org/wiki/Capacitor_plague](http://en.wikipedia.org/wiki/Capacitor_plague)

[http://images.google.com/images?q=bad+capacitors&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=gvrDS9yRLYSmnQe7mJTPDw&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CCgQsAQwAw](http://images.google.com/images?q=bad+capacitors&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=gvrDS9yRLYSmnQe7mJTPDw&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CCgQsAQwAw)

[http://www.badcaps.net/](http://www.badcaps.net/)

[http://www.badcaps.net/pages.php?vid=5](http://www.badcaps.net/pages.php?vid=5)

OK, that's four, not two... sue me... I'm *really* tired.

---

### Post by boxcorner on 2010-04-14
> **egalvan said:**
> ... I've lost track of who has the older hardware...[/url]

:lolflag: Since my original post, I have found paperwork showing that I built this particular desktop PC in 2002.  I replaced the PSU earlier this year.

[QUOTE=egalvan;9115175]...
Have you done a close visual inspection ...

Yes, I inspected the motherboard and graphics card carefully each time I removed and re-fitted them earlier this year, but each inspection was carried out unaided. 

> **egalvan said:**
> ... of the capacitors on the motherboard? (and video card, and power supply...)

No, I wasn't aware of this problem with faulty capacitors; I didn't pay any more attention to them than any of the other components.

> **egalvan said:**
> Here are ... links ...

Many thanks for telling me about this and for the very interesting links.   It certainly sounds like it would be well worth removing the PCBs again and inspecting their capacitors more closely, this time using a magnifying glass.  My eyesight is not as good as it used to be!

_Addendum_
No problems since the earlier incident, while using Epiphany.

---

### Post by lavinog on 2010-04-14
Many capacitors will have a grove (usually an X or a K) that provides a way for a capacitor to discharge without exploding in an overpressure condition.  A break at this grove is a good indication of a problem.  Sometimes a small break in the grove can slowly release its contents, and a residue might be present at the top of the capacitor.

---

### Post by boxcorner on 2010-04-16
> **lavinog said:**
> Many capacitors will have a grove (usually an X or a K) that provides a way for a capacitor to discharge without exploding in an overpressure condition.  A break at this grove is a good indication of a problem.  Sometimes a small break in the grove can slowly release its contents, and a residue might be present at the top of the capacitor.
Thanks for the tip.  My PC has been running trouble-free since the last incident I reported, however it froze again this morning while running Epiphany.  Of course, it may be entirely coincidental that the hangs occurred while running this browser.   Chromium runs without any difficulty.  Unfortunately Firefox is no longer usable, as it greys out consistently at the same point whenever it tries to load a web page.  I've completely un/re-installed it to no avail.  I'm currently waiting for a rainy day, so I can take the PCBs out to inspect their capacitors.  Meanwhile, the temptation to get out into the Spring sunshine do  some gardening is overwhelming.  As in many other parts of the world, it's been a long cold winter here and I've been cooped-up indoors in front of this computer too long!

---

### Post by warfacegod on 2010-04-16
> **boxcorner said:**
> Thanks for the tip.  My PC has been running trouble-free since the last incident I reported, however it froze again this morning while running Epiphany.  Of course, it may be entirely coincidental that the hangs occurred while running this browser.   Chromium runs without any difficulty.  Unfortunately Firefox is no longer usable, as it greys out consistently at the same point whenever it tries to load a web page.  I've completely un/re-installed it to no avail.  I'm currently waiting for a rainy day, so I can take the PCBs out to inspect their capacitors.  Meanwhile, the temptation to get out into the Spring sunshine do  some gardening is overwhelming.  As in many other parts of the world, it's been a long cold winter here and I've been cooped-up indoors in front of this computer too long!

I've seen several other threads about Firefox 3.6.4 graying out so it's highly unlikely that it's a hardware issue on your end.

---

### Post by lavinog on 2010-04-16
> **warfacegod said:**
> I've seen several other threads about Firefox 3.6.4 graying out so it's highly unlikely that it's a hardware issue on your end.

True, flash can be a culprit.

---

### Post by warfacegod on 2010-04-16
> **lavinog said:**
> True, flash can be a culprit.

I'm pretty sure that the threads I'd seen had to do with the new way 3.6.4 is handling Flash. Evidently the new way isn't working.

---

### Post by boxcorner on 2010-04-20
> **warfacegod said:**
> I've seen several other threads about Firefox 3.6.4 graying out so it's highly unlikely that it's a hardware issue on your end.
The mouse pointer froze again this evening, while running Epiphany.  That's the 3rd time while running Epiphany, meanwhile I've also been using Chromium and Seamonkey without any difficulty.  The weather's changing, so I plan to scrutinise the PCBs on Thursday.  Hopefully I'll be able to resume using Firefox later.

---

### Post by warfacegod on 2010-04-21
> **boxcorner said:**
> The mouse pointer froze again this evening, while running Epiphany.  That's the 3rd time while running Epiphany, meanwhile I've also been using Chromium and Seamonkey without any difficulty.  The weather's changing, so I plan to scrutinise the PCBs on Thursday.  Hopefully I'll be able to resume using Firefox later.

lovinglinux (the internet/torrent guru) just posted somewhere that the 3.6.4 flash issues have been fixed.

---

### Post by boxcorner on 2010-04-25
> **warfacegod said:**
> lovinglinux (the internet/torrent guru) just posted somewhere that the 3.6.4 flash issues have been fixed.
Thanks.  I re-installed Thunderbird and have been using it without any difficulty   [ except this ]("http://ubuntuforums.org/showthread.php?t=1422720"), until the mouse pointer froze again this morning. Consequently, I examined all capacitors on the PCBs very closely and couldn't see any signs of leakage or discolouration. So, now I have removed the 256MB DIMM from slot 3 and left the 1GB DIMMs in slots 1 and 2.  It will be interesting to see whether or not it continues to hang intermittently.

---

### Post by cuberts on 2010-04-25
> **boxcorner said:**
> The following error was encountered.  You may need to update your configuration to solve this.
(EE) Failed to load /usr/lib/xorg/modules/driver/nvidia-drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

According to: System > Admin > Hardware Drivers
NVIDIA accelerated graphics driver (version 96) [Recommended]
This driver is activated and currently in use.

Ever since I re-installed Ubuntu, from time-to-time it hangs, requiring a re-boot.  This is the first time I've seen this error.
Any suggestions? Should I remove and re-install the driver? Thanks.Try rebooting into Recovery mode, and select xfix, then restart.

---

### Post by boxcorner on 2010-04-26
> **cuberts said:**
> Try rebooting into Recovery mode, and select xfix, then restart.
Thanks for the suggestion.  I want to see whether this latest hardware change makes any difference, before trying anything else.  The remaining problem is solely the mouse pointer freezing, infrequently and intermittently.  It happened when running browsers, but I doubt that's significant.

---

### Post by warfacegod on 2010-04-26
> **boxcorner said:**
> Thanks for the suggestion.  I want to see whether this latest hardware change makes any difference, before trying anything else.  The remaining problem is solely the mouse pointer freezing, infrequently and intermittently.  It happened when running browsers, but I doubt that's significant.

If your using an optical mouse, make sure you have a mouse pad with a pattern. Optical mice don't like uniform colors. Especially red.

---

### Post by lockalidiot on 2010-04-26
About the original low-graphs issue. I have been running in to it too. First when I had 10.04 beta 2 on my test partition. I reinstalled my NVIDIA drivers and that seemed to solve that. Now, few days ago I did a fresh install of 10.04 RC and thus wiped out my 9.10. The 10.04 seemed to work well at first, but then I ran into this low-graphs issue again. This time reinstalling NVIDIA drivers haven't helped. Rebooting, once or twice usually makes the OS to boot properly.
I don't believe this is hardware issue as I don't/didn't have any similar issues with 9.10 or my Windows 7 Ultimate.

---

### Post by boxcorner on 2010-04-27
> **warfacegod said:**
> If your using an optical mouse, make sure you have a mouse pad with a pattern. Optical mice don't like uniform colors. Especially red.
I'm using the the same wireless optical mouse and pad that I used previously with Windows XP trouble-free, so I doubt that's the cause.  Nevertheless, I have now configured my clock preferences to display seconds, so when/if it happens again I'll have an immediate visual indication on-screen of whether it's just the mouse that's playing up.  Is there any way of monitoring the system state in Ubuntu (eg invoking the Resources widget from System > Administration > System Monitor), using a combination of key presses, like Ctrl+Alt+Del in Windows?

@lockalidiot
That's interesting.  Sounds like I'd best stick with 9.10 for the time being.

---

### Post by warfacegod on 2010-04-27
You could add an Hardware Monitor to your panel.

Right click panel> select Add to panel> select Hardware Monitor> click Add.

You can right click the monitor and select Properties to have it show different resources. For example, I've got mine showing CPU, RAM, Network use, and HDD I/O.

If you want to have a shortcut, you'll need to create it.

System> Prefs.> Keyboard Shortcuts> click Add> Name: whatever you like> Command: gnome-system-monitor> click Apply> click where it says disabled> assign it a shortcut by hitting those keys> close> test.

---

### Post by boxcorner on 2010-04-27
> **warfacegod said:**
> ... Hardware Monitor ...
Excellent, cheers.  Actually, mine's called *System Monitor*, but it seems to be the same thing.  
Now I almost wish the mouse pointer would freeze again, just to see what happens to these icons. :)

---

### Post by warfacegod on 2010-04-27
> **boxcorner said:**
> Excellent, cheers.  Actually, mine's called *System Monitor*, but it seems to be the same thing.  
Now I almost wish the mouse pointer would freeze again, just to see what happens to these icons. :)

My fault. It is System Monitor. I hadn't had my morning coffee yet.

---

### Post by boxcorner on 2010-04-28
> **warfacegod said:**
> My fault. It is System Monitor. I hadn't had my morning coffee yet.
Yes, caffeine works wonders for me too. In addition to the icons representing resource properties that you mentioned, I also selected *Load*.    I understand the percentages and bytes indicated by the others, however I'm not sure what 'load average' actually means.  For example, currently, according to the tooltip, "The system load average is 0.32".  What exactly does that mean, do you know?  How is this factor calculated?

_Addendum_
When I right-click on the system load icon and select *Help* a new window opens, but it's constantly blank (ie Loading ...)

---

### Post by warfacegod on 2010-04-28
I *believe* Load is the Average Load of all of the system components. As in, how close you are to maxing out your system.

---

### Post by cuberts on 2010-04-28
> **boxcorner said:**
> The following error was encountered.  You may need to update your configuration to solve this.
(EE) Failed to load /usr/lib/xorg/modules/driver/nvidia-drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

According to: System > Admin > Hardware Drivers
NVIDIA accelerated graphics driver (version 96) [Recommended]
This driver is activated and currently in use.

Ever since I re-installed Ubuntu, from time-to-time it hangs, requiring a re-boot.  This is the first time I've seen this error.
Any suggestions? Should I remove and re-install the driver? Thanks.Try doing:-
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by boxcorner on 2010-04-28
> **cuberts said:**
> Try doing:-
```
sudo dpkg-reconfigure xserver-xorg
```

Many thanks for your suggestion.  Two points spring to mind: (1)  you responded to a post that's now more than a month old and I wonder whether you've read any of the intervening posts (2) I'd feel a lot more comfortable about running the code, if I understood what it is supposed to do.

As a general point, I wish more people here would explain what the code that they post is supposed to do, rather than either assume that someone already knows, or is willing to run it blindfolded. Quite apart from the security issue, it would surely help newcomers with the learning process.  No offence intended.

---

### Post by boxcorner on 2010-05-04
Tempting fate: everything seems stable now, so I'm going to mark this thread SOLVED.  Many thanks to everyone who helped me ):P

---

