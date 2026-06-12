---
title: "Multiboot System Boot Failure?"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by ken0069 on 2010-04-05
OK so I've had this problem before and never got resolution for it that I could work with and so here I am again with a Windows drive failure on a multiboot system that now renders ubuntu 9.10 unuseable? 

You'll have to pardon me for my candid opinion on this but just why in the world would someone write a linux OS boot loader that was DEPENDANT on WINDOWS to boot?  With the boot loader acting this way, ubuntu is no better than the Windows OS it requires to boot?

I had a Windows xp drive fail yesterday and afterwards ubuntu will not boot either?  I've done Google.com searches out they yeng-yang with references to "ubuntu live" CDs that are pretty much non-existent.  All I can find is the regular install CD that is referenced here?  I did find one site that had another "flavor" of ubuntu v10.04 that I downloaded but that one IS NOT 9.10 either and all the documentation I've read specify ubuntu 9.10 "live"?

So since I can't find a simple solution to fix grub I now have a multiboot computer that I can't use without wiping out the ubuntu load that's on it and reinstalling and having to do a gazillion updates, reinstall add ons, etc?

So I need some help on how to configure grub to let ubuntu boot itself WITHOUT a Windowz XP drive in that box?  And it would also be nice to have a way NOT to have grub depend on Windows to boot ubuntu!

Any help anyone?  Oh, and please make it simple as I'm just not a command line person.

Thanks,

Ken

---

### Post by cgroza on 2010-04-05
GRUB does not depend on windows to boot Ubuntu!!!

---

### Post by halitech on 2010-04-05
First off, sorry to hear you are having issues. Second, GRUB and Linux are not dependant on Windows working *UNLESS* you installed using WUBI which makes Ubuntu basically operate as a program inside the windows file system.

The Regular install cd and the "Live cd" are the same thing, they both allow you boot into a Live operating system and install from within the running operating system as opposed to the alternate install cd which boots you right into a text based install.

You can download the regular install cd (aka the Live cd) here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by da burger on 2010-04-05
The installer cd is the live cd.

I think the problem may be that GRUB won't load properly unless it can find all the operating systems that it had entries for.

---

### Post by phredbull on 2010-04-05
1. Well, if it's actually a drive failure like you said, then any OS on that drive would be broken, be it Linux, Windoze, or Mac.

2. If I'm not mistaken, Grub needs to see the MBR located in the 1st primary partition in order for multiboot to work. Linux can be installed anywhere, but Windoze also needs to be installed in the 1st primary partition, so if Windoze breaks your MBR, then Grub won't work. (If this is the case and your Linux partition is actually OK, then you can fix the MBR, not sure of the specifics, do a search here on the forums.)

3. If you want to avoid this problem in the future,put Linux on its own drive.

Good luck!

edit: actually, I'm not sure if 3. above is true; even if Linux has its own drive, I think the MBR may still need to be located on the same partition as Windoze. I think this is unavoidable in a Windoze/Linux dual boot situation. Do a search on repairing your MBR.

---

### Post by ken0069 on 2010-04-05
Let me clarify what I have here.  

I was using TWO hard drives in the same computer with Windows loaded on one and ubuntu on the other.  

I've got a couple of multiboot systems and NONE of them will boot ubuntu if the Windows drive is disconnected!??  ALL OF THESE UBUNTU INSTALLS WERE DONE WITH _ONLY_ THE UBUNTU DRIVE CONNECTED.  After the installs were complete, THEN I connected the Windows drive.  I disconnect the Windows drive during the ubuntu install to keep from installing on the WRONG drive, been there, done that too.  

But someone please explain to me why ubuntu won't boot unless the Windows drive is also connected and working, especially since Windows wasn't even connected when ubuntu was installed?

Thanks,

Ken

---

### Post by flyfishingphil on 2010-04-06
What order is your boot order in? Does it specify to go to the HDD with windows first? If so, could it be that the boot is hanging up on a faulty program and not letting the unit continue to look? Maybe you could change the order in which it boots and make the HDD with Ubuntu the first hard drive it checks? (Not an expert, but sometimes that makes it easier to look at things from a different angle. Had problems too until I changed the boot order.)

---

### Post by 23dornot23d on 2010-04-06
Ok you beat me to it ..... similar thoughts .....

It sounds like the windows drive is the master in a two drive system ,,,
when initially setting up the drives one is Master and on is Slave

Have you looked at the BIOS settings to see which hard drive boots first ,,,
and if it identifies them  .... usually pressing F10 or F2 on boot takes you into the BIOS

I would start there ...... just look and see first ..... which is the boot drive .... and if
the BIOS identifies master and slave .... how old is this Desktop Computer does the
BIOS automatically detect the changes or do you have to set it ..... just first thoughts
on seeing this thread ..... 

( as newer computers seem to detect most things ..... and older ones are done manually )

The Slave drive may be the one you have loaded UBUNTU onto here ....
and possibly a reason it will not boot ......... but someone else might clarify it 
(this tends to only apply to older computers though ..... )


if this is the case or not ...... !!!

---

### Post by ken0069 on 2010-04-06
Some background information on what I do with ubuntu.

I run a couple of websites.  Both have forums on them, one being a primary and the other is a backup board in case the main one goes down.  Last summer my main board's administartor account got hacked.  This came after fighting with my hosting service Admin for 2 months about that "fake antivirus" crap kept getting on my computer when connecting to my Admin Email account, on his server.  He kept telling me nothing was wrong with his stuff while I was having to clean junk off on a weekly basis along with a couple of system reloads because so much junk got on the computer I couldn't save it.  Finally my Wife's money maker website also started infecting the Goggle bot and when here site got black listed, she moved all 7 of her websites to Godaddy.  That got his attention and he hired someone that DID find the junk on his server!

So I said all that to get to ubuntu and me.  I primarily use ubuntu for my website stuff and administrating my forum, etc because of the safety of the Linux system and lack of key loggers, which is how I believe my Admin password was compromised by some hacker trash!  

I spend about 80% of my time now on ubuntu and basically the only reason I keep Windows around is for some games I can't make run in Wine on Linux and I do run a computer repair shop and occasionally need a Windows OS for that.  

So while ubuntu is good in many ways, it's still not a "be all/do all" for me yet, which brings me back to this current problem  That computer that won't boot from that ubuntu drive, is the main one I normally administer my web forum from.  

Ken

---

### Post by ken0069 on 2010-04-06
OK, someone else was typing while I was.

All my systems are booted from which ever drive I select in BIOS.  One computer has 4 drives in it with XP, Vista, 7 and ubuntu.  The other two only have 2 drives but all boot drives are selected from BIOS in all 3 multiboot systems.  

Again, ALL ubuntu installs were done WITHOUT any Windows drives connected.

Ken

---

### Post by oldfred on 2010-04-06
While they have tried to change things to use UUIDs for grub and fstab not all setting seem to be that way or you may have configured your system using sda & sdb instead of UUIDs. If so then when you remove sda, sdb becomes sda and the system will not boot. Generally it is assumed you are not plugging in and unplugging drives.

I have 3 drives and no problems but the settings sda, sdb, sdc seem to be based on the SATA ports plugged into the motherboard.

---

### Post by 23dornot23d on 2010-04-06
That sounds like it might be the case ... OldFred .... 

I set up a laptop computer with USB drives and when I removed one 
the system would not boot ..... so had to set each up as a second drive ..... 
then once added flipping the BIOS between them lets them work ok  
as you say the order changes ..... 
not sure how the programmers can do anything for that when hardware is added and removed ..... 
but this may happen more in the future 

With more than one USB hard drive being plugged in and out of machines ....

---

### Post by ken0069 on 2010-04-06
> **oldfred said:**
>  Generally it is assumed you are not plugging in and unplugging drives.

Therein lies the problem, since the drive failed, what am I suppose to do?  And what if my Windows load gets horked up again and I have to do a system reload?

As for the drive designations, they are done using whatever the default is in ubuntu because I got no clue how to do anything different with'em.

So is there an "easy" fix for my current problem?  I tried some stuff I found on the internet yesterday but it was a "no go".

Thanks,

Ken

---

### Post by 23dornot23d on 2010-04-06
So there are 4 options if you have 2 drives ..........

1......(1 drive UBUNTU) If you just used Ubuntu on one drive and only have that drive plugged in as you initially installed it ....... it should work fine ....

2......(1 drive WINDOWS) If you use the Windows drive by itself it should work fine ....

3......(2 drives UBUNTU boot as first drive) If you have both drives plugged in at the same time ,,,, you need to ensure that the Ubuntu one is the main drive for it to boot ...... sda or whatever and the Windows drive as sdb ,,,,, that should then work  .... but to boot windows from it you also need to do this
(if you are using grub 2 ,,, you may be able to run grub-pc to detect the windows drive and partition and it should add Windows to the boot menu ........ using grub2)

4......(2 drives WINDOWS boot as first drive) If you have it this way - the Windows drive as sda it will not boot UBUNTU on sdb as the grub does not exist here to do anything with UBUNTU boot   ,,,, but it will still boot Windows ok as only the boot information for Windows exists on this drive as it was disconnected when you added UBUNTU.
I cannot see an easy way of fixing option 4 without re-installing UBUNTU with both drives plugged in ......... as this will add the new grub to the windows drive ....

Hope this helps in some way .....

If anybody knows different please add ..... after this .......

(I have edited it to give a little more clarification to the possibilities here ....)

---

### Post by oldfred on 2010-04-06
It should not matter whether windows is working or not just that a drive is plugged in and BIOS has it as first so it is sda. If you had windows on sdb and removed sda windows would not work either. 

Any system reconfiguration often requires updating some settings, usually just a reinstall of grub if you have used UUIDs in fstab.

---

### Post by ken0069 on 2010-04-06
Tried to reinstall grub yesterday morning but never could make that happen either?  Tried this from the "live 10.04" CD I downloaded.

I've got ubuntu 9.10 x86 on a CD that I used to install with.  Some here have said that CD is also a "live" CD but I've not seen that in the menu when it boots to CD?  The 10.04 one I downloaded seems to be the same as 9.10 as far as menus and stuff are concerned.  It just has a different default desktop from the regular 9.10 CD.

I've got a couple of old PATA drives laying around.  I'll try one of those in that box to see if I can make it work tomorrow.  

Meanwhile, I still need to figure out how to reinstall grub in ubuntu.  Any suggestions on this?

Thanks,

Ken

---

### Post by 23dornot23d on 2010-04-06
I do not know how to install GRUB separately ...........

other than doing a fresh install ...... BUT ..... 



The guy writing the tutorial below seems to know all about grub and installing it .......

he even puts it on a Flash Drive ...... it may be an idea to PM him and ask him if its possible ,,,

[http://ubuntuforums.org/showthread.php?t=1163686](http://ubuntuforums.org/showthread.php?t=1163686)

Its the best  info that  I can give you at this moment in time .... as I know that you

do not want to do a fresh install ........

---

### Post by oldfred on 2010-04-06
This covers windows and both versions of grub:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by LewRockwellFAN on 2010-04-07
> **phredbull said:**
> 1.  ... Grub needs to see the MBR located in the 1st primary partition in order for multiboot to work.  ... I think the MBR may still need to be located on the same partition as Windoze. ... 

Not quite. There is only one MBR per conventional HD and it isn't on ANY partition but is located on the outer rim in space not allocated to any partition. Indeed, that is where the data indicating the locations of the partitions resides. Perhaps you are thinking of boot sectors which do come one to a partition.

---

### Post by LewRockwellFAN on 2010-04-07
It might be helpful to know what type of drives these are. Also in what way they are disconnected. I have occasionally had drives that redered the whole system useless (not dead necessarily, sometimes it would boot, sorta, but hang or behave innapropriately afterwards) if I didn't disconnect BOTH the data cable AND the power cable. Don't ask me why. I had trouble believing it until I confirmed it by repeated experiment. Also one of the posts could, I believe, leave some readers confused about the meaning of master and slave. This has nothing to do with boot order and only applies to IDE (including ATAPI), or perhaps MFMs or other oddball or antique drives. At any rate not to SATA drives as far as I know. If you are using drives to which this is relevant, the master slave setup could, indeed, explain your problem, though not because of any effect on boot order, which, as far as I know, is a totally independent issue, and is normally controlled, as others have indicated through BIOS settings on the Mobo or sometimes, on a SATA controller card. If, as sounds likely, you are using SATA drives, there is no point in going into the complexities of IDE, master, and slave.

---

### Post by Seq on 2010-04-07
You're right in that you need to restore Grub from the liveCD.

What happened is basically this:

[LIST=1]
[*]Your BIOS finished finishes it's POST tests and needs to load some code.
[*]It looks on the first installed drive. Grub and the Ubuntu installer know this, so they installed the first stage of grub to the first drive, even though Ubuntu, the rest of Grub and it's configuration are all on the second drive. The BIOS doesn't look there.
[*]Your first drive is no longer present (removed, failed, wiped, etc).
[*]Your BIOS looks at the first drive (which was previously your second drive) and doesn't see anything, since grub's stage1 was installed to the only useful place: The (now missing) first bootable drive.
[/LIST]

The solution is to re-install grub. In the future, you may wish to manually install grub to any device that could potentially be responsible for booting your machine.

---

### Post by neopsalmist on 2010-04-07
So...to make sure I've got the right picture, you physically DISCONNECTED the Win drive(s) from this machine that you are having problems with while installing Ubuntu, then reconnected the drive. Also, you have some sort of boot drive selector when the machine boots up? Please let me know if I have this wrong.

Also, if the above is not correct, how do you select which operating system to boot into? Do you see the GRUB screen with a selection for Windows under "Other OS" or do you only see the MS selector with two boot options, one which you would have had to set up via other methods than GRUB?

---

### Post by LewRockwellFAN on 2010-04-07
> **Seq said:**
>  ...
What happened is basically this:

[LIST=1]
[*]Your BIOS finished finishes it's POST tests and needs to load some code.
[*]It looks on the first installed drive. Grub and the Ubuntu installer know this, ***so they installed the first stage of grub to the first drive, even though Ubuntu, the rest of Grub and it's configuration are all on the second drive.** *[emphasis added - LRF] The BIOS doesn't look there.
[*]Your first drive is no longer present (removed, failed, wiped, etc).
[*]Your BIOS looks at the first drive (which was previously your second drive) and doesn't see anything, since grub's stage1 was installed to the only useful place: The (now missing) first bootable drive.  ...
[/LIST]

Not if the OP was correct and truthful  in saying:
" ...  ALL OF THESE UBUNTU INSTALLS WERE DONE WITH _ONLY_ THE UBUNTU DRIVE CONNECTED. [emphasis OP's -LRF] After the installs were complete, THEN I connected the Windows drive. I disconnect the Windows drive during the ubuntu install to keep from installing on the WRONG drive ... "

Of course if GRUB had been updated since, it might be a different story.

---

### Post by Seq on 2010-04-07
> **LewRockwellFAN said:**
> Not if the OP was correct and truthful  in saying:
" ...  ALL OF THESE UBUNTU INSTALLS WERE DONE WITH _ONLY_ THE UBUNTU DRIVE CONNECTED. [emphasis OP's -LRF] After the installs were complete, THEN I connected the Windows drive. I disconnect the Windows drive during the ubuntu install to keep from installing on the WRONG drive ... "

Of course if GRUB had been updated since, it might be a different story.

I must have missed that, sorry for the clutter. I'm somewhat curious how he managed to boot Ubuntu at all, unless he was chain-loading from windows' boot loader, or some third-party utility. I may have missed that too.

---

### Post by ken0069 on 2010-04-07
I've got 3 computers configured this way and yes, all these ubuntu installs were done WITHOUT any other drives connected specifically to try to keep grub off my Windows drives.  

When I want to change the boot drive on all these computers I go into BIOS and select the drive I want to boot from and it will boot that drive every time I boot up until I change to another one.  The only time I ever see the grub screen is when I select the ubuntu drive to boot from in BIOS.

FYI, I tried to reinstall grub from the install CD and it's a "no go" and I get an error now when I try to boot that drive that says *_**grub error: "grub_puts_" not found**_*  I did a Google search and found some stuff to try to reinstall grub but none of them worked.  Now the grub boot screen comes up but it times out when it can't find sda1 and when I connect another drive to that computer and try to boot ubuntu it still won't boot and sits there and does nothing until I either power it off or pull the plug.

I've played around with Suse, Fedora, Red Hat and several other distros that never gave me this problem and all were loaded the exact same way I loaded ubuntu so it looks like I'll be going back to Suse for my web site work box.  At least I can depend on that one booting regardless of whether a Windows drive is present or not.  I ordered the 11.2 DVD off of fleabay this afternoon.  

I did manage to get my data off the ubuntu drive that won't boot by using that 10.04 live disk I downloaded Monday and I transferred those files to a Windows box on my network.  

Got a new 250 GB SATA drive to replace the failed Windows drive so I'll do a clean install of XP on that tomorrow.  

I want to thank all of you for your posts and suggestions.  Maybe the "powers that be" will see this and incorporate something to make it easier to repair grub and or offer more options with a GUI interface for those of us that are command line challenged!  I really like this distro but this problem has put it down the list for now.

Thanks,

Ken

---

### Post by 23dornot23d on 2010-04-08
Ok cheers Ken .....

It looks like a bug report was put in for the same situation you are in ........

here it is ..... it has some useful info too ..... so they are aware of the problem ,,,

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435)

according to this though they say it has been fixed in Lucid now .... 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/514269](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/514269)

which is what you used the 10.04 live disk ....

Hope whatever you use works ok ...... best of luck .....

---

### Post by ken0069 on 2010-04-08
> **23dornot23d said:**
> Fixed in Lucid which is what you used the 10.04 live disk ....
 
So is Lucid beta of the next release?

---

### Post by 23dornot23d on 2010-04-08
Lucid is the next release 10.04 ,,,, you are using the Beta which is close to the completed version.

See the link below in my footer ... here ... [https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)

It gives the dates for the final release and shows the way it is planned out  ....... 

April the 29th  is the final release date ......

---

### Post by ken0069 on 2010-04-09
Well since I'm retired and have more time on my hands than money in them, I decided to do some “testing” on this problem using Lucid since another posted had mentioned that my problem was fixed in this new release.
 

 First I did a reinstall of Winders on that new drive I got.  Then I disconnected that Winders drive and connected the drive that ubuntu 9.10 was on and proceeded to install Lucid over 9.10 with no internet connection available so it couldn't update itself during the install.  Once that install completed, I then connected the LAN cable and did the few updates that were available.   
 

 Once those were done I shut down Lucid, connected the Winders drive up and then rebooted to that Lucid drive with zero problems.  Then shut down again and booted from the Winders drive and again, all went well.  Then I shut down and disconnected the Winders drive and booted Lucid and it booted fine and I NEVER saw the grub boot menu during any of this.   
 

 This morning I booted the system to Winders and it went fine.  Shut down and booted to Lucid and all went fine and again, no grub boot screen.  THEN I did some updates on Lucid but before I allowed them to proceed, I checked to see if grub was going to be one of the updates.  It was as there were two grub updates available so I let them run to see what would happen.   
 

 So after the updates here is what happens now.  When I rebooted the ubuntu system I got the grub boot screen with the Winders drive listed so this confirms that the online update of grub is what changes stuff.  I'd seen this before but didn't know just how bad it would hork up trying to boot v9.10 if no Winders drive was available.  So, I booted both Winders and ubuntu Lucid by changing the BIOS settings after that update and both worked fine.   
 

 Then to see if my former problem would manifest itself I then shut down, disconnected the Winders drive and tried to reboot Lucid.  I was happy to see the grub screen come up and count down then the Lucid drive booted with NO Winders drive present so this confirms that my boot problem has been fixed with this new distro.  Bad news is I've got TWO other systems that are NOT fixed and are susceptible to the same fate as this one was.   
 

 So maybe someone will put out an update patch to address this for those of us still running 9.10!
 

 FYI, I like Lucid.  Although most of the stuff in it is very much like 9.10, the look and feel is a little different and I like that since the typical Ubuntu “dirt” theme never impressed me at all.  I'll probably still load up Suse 11.2 just to see if they fixed any of the problems from 11.1 that drove me here to begin with.

---

### Post by 23dornot23d on 2010-04-10
Good to hear ..... 

Glad your problem is solved now ..... can you mark this thread as solved ..... please

I too like Lucid Lynx and the new colors are growing on me .....  :)

fast boot time too ....

---

### Post by ken0069 on 2010-04-29
> **23dornot23d said:**
> Good to hear ..... 

Glad your problem is solved now ..... can you mark this thread as solved ..... please

Well, actually the problem is not solved that I know of as no one has confirmed that this problem in 9.10 is fixed too?  I guess I could try disconnecting a Winders drive on one of those 9.10 loads I'm still running to see but I haven't seen any Grub updates come in for that version?  I'll check shortly to see if it still happens with 9.10 and then figure out how to mark this thread as "solved".

Thanks

---

### Post by ken0069 on 2010-04-30
Nope, this problem is still present in 9.10.  I just tried to boot this system with the Windows drive disconnected and Ubuntu wouldn't boot.  

If a grub update broke it, then one would assume that another grub update could fix it?

---

### Post by timsdeepsky on 2010-04-30
I also had problems with grub2 after 9.10 and 10.04....It simply would never find grub and load it....I have 2 hard drives,,one with Ubuntu and one with xp for gaming....I unplugged the windows drive the and same thing,,only is said it could not find the drive that windows was on....Plug it back in and re-installed 3 times....Finally after third install of 10.04,,it finally found grub and away we went....Works really well by the way....So,,i do not know what changed....Go figure....again....

---

### Post by cuberts on 2010-04-30
> **cgroza said:**
> GRUB does not depend on windows to boot Ubuntu!!!
well right now I am having an issue of running Ubuntu from my flashdrive on a school computer, it shows that there is a i/o error, so I dont know why it does that, so is this a problem with my drive, or is it something about that computer that I was using? So I think that if someone answers my question, then it might help him

---

