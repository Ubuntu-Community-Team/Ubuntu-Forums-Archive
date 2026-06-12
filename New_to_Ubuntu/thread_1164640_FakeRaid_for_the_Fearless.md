---
title: "FakeRaid for the Fearless"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by lile001 on 2009-05-19
Fearless, I am not.  I don't know very much at all about Ubuntu, but I'm faced with the task of installing Ubuntu on a machine that came with a RAID1 array. I can tell you it hasn't worked yet, straight off the Ubuntu install disk. It did work, if I busted the RAID at the BIOS level and just made it two non-RAID hard drives. But that was using the Ubuntu install disk without any other steps. 

  There are two things to start with.  First, on bootup, I see a RAID Bios setup screen that gives the following hint as to what it is:

INTEL Matrix Storage Manager option ROM V7.6.1.1001 ICH9R wRAID5

There are two physical drives, and this go-round I've convinced this thing that it has two volumes, VOLUME0 And VOLUME1.  One of these will have windoze, and one, hopefully has Ubuntu and hopefully we'll dual-boot.  There is no data on the hard drives, so we've got nothing to lose here.  They are set to RAID1.  We could make it all one volume, either way is acceptable.

I'm hoping this is what the FAKERAID page is about:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Now the very first line of this file sez:
"FakeRAID is not supported by Ubuntu. Trying to install Ubuntu on such a partition could easily result in the loss of all your data."

and the second line sez:

"How to install Ubuntu onto a ***fakeRAID*** system" 

OK- Even an idiot like me can tell these two statements are incompatible.  One of them has to be wrong.  Either you can install it or not, right? Is this a wild goose chase, and I should forget about RAID?

---

### Post by HDave on 2009-05-19
I have Ubuntu installed on three machines, each with a different RAID device-- though none of them match yours exactly.  Are you 100% sure your RAID setup is one of these "fake" RAIDs? According to the Intel website [here]("http://www.intel.com/support/chipsets/imsm/"), this thing has "evolved over time."

Also look [here.]("http://ubuntuforums.org/showthread.php?t=358120")

Worst case, forget about the RAID, configure them as 2 SATA drives.  You can easily install Ubuntu and Windows in a dual boot on one of them and use the other for data or whatever.

---

### Post by lile001 on 2009-05-23
I give up.  For a guy who picked up Ubuntu a two weeks ago, this is a completely daunting project.  Looking in the forums, I see numerous posts about RAID but with no answers at all.   I feel lucky that I got one post.  Thanks for trying, friend. 

When I start diving into one of those pages about DMRAID, FDISK or such, it is impossible to follow. I try, and things fall apart within minutes.  What I see on the screen doesn't look anything like the documentation.    What the hell are they talking about?  Can't these programmers speak English? I've got a technical degree, lots of experience with DOS and Windows computers, but I can't follow the gibberish. 

Ubuntu was supposed to be an attempt to bring the arcanities of Linux to the masses.  So far it's failed.  My advice to a new person wanting to use Linux:  Buy a box with Linux installed from the manufacturer.  If you don't, you'll probably be frustrated, if there is anything non-standard about that computer.  

I've spent two weeks re-installing Ubuntu every free night, time after time, Reading pages upon pages of gobbledybook, trying different approaches but the same result.  Ubuntu won't run under WUBI, won't work if the RAID is configured, and all of the fixes and HOWTOs are written in Klingon.  So far I've wasted at least 40 fruitless hours trying.  


 Screw it!

---

### Post by HDave on 2009-05-23
A few things:

1) I am suprised WUBI didn't work...did you post your issues with that?  Was it on the same computer as the funky RAID device?

2) I consider myself a power-user for Ubuntu and I took a look at the fake RAID instructions -- very complex.  In the opening paragraph it warns that Linux doesn't really work with fakeraid -- so I would probably give up and use the 2 disks at SATA disks.

3) Do not give up.  Ubuntu/Linux is forcing you to learn more about your computer than you want, but in the end it will be rewarding and beneficial for you to push through the pain.   Like you, I was all set to give up at first because -- get this -- I couldn't get Ubuntu to work with an external monitor!!  How ridiculous I though that it didn't "just work."  Now I know *why* I had those troubles and can also breeze through any graphics device & monitor problem.  The community here is very knowledgeable and helpful....don't give up...yet.

---

### Post by lile001 on 2009-05-24
> **HDave said:**
> A few things:



3) Do not give up.  Ubuntu/Linux is forcing you to learn more about your computer than you want, but in the end it will be rewarding and beneficial for you to push through the pain. 


Let's see, the little banner by your name says you've been doing things with Ubuntu for at least two years, probably many more.  So maybe two years from now, I might try fooling with RAID again on another box.  Meanwhile I have to get this blasted computer working within my limited skill set.  Giving up on RAID doesn't mean giving up on Ubuntu.  If a sage who's been doing this for years feels it is daunting, then I'd better not mess with it at least until I've read the Ubuntu for Dummies book. (is there one?  surely there is.)  Right now, Ubuntu is running on "The computer formerly known as having RAID"  i.e. I told the bios to forget about RAID and just use two hard drives.  One of them can be a backup, and I have 50% of the security that I'd had under RAID with no pain, by manually copying stuff to the backup drive every once in a while.   

Once again, my advice to other beginners, given my little experience - Don't mess with RAID, Ubuntu isn't there yet.   The learning curve becomes a learning cliff, and you're Wiley Coyote.  When there is Out-Of-The-Box, truly automatic support for RAID, then use it.  Until then, leave RAID to the Übergeeks.

---

### Post by cariboo on 2009-05-24
If you follow the howto step by step you will have a working raid array. The instruction on the page are for booting from the array also. If you are using a seperate drive for your installation, you can ignore the part about installing grub.

I've used the howto a couple of times and had great success.

There are a couple of things you should keep in mind while running a raid array, it will only protect you if a drive fails, if you have data corruption, it will be mirrored on both drives. Raid is not a substitute for a good backup policy. If your data is important to you, back it up as well as running a raid array.

---

### Post by HDave on 2009-05-25
> **lile001 said:**
> Giving up on RAID doesn't mean giving up on Ubuntu.

Glad to hear that.  I would add for what it is worth, I have installed Ubuntu on three RAIDs and it "just worked".

1) 3ware 9650
2) nVidia on-board RAID (3600 pro)
3) Intel ob-board RAID (can't recall the chipset)

I honestly don't know how to "set up" RAID in Ubuntu because in all three cases I didn't do anything but insert the install disk.

If you have the cash, the 3ware card is amazing....

---

### Post by Keithhed on 2009-05-25
I am using a Raid0 array.  Set up for Raid was through the motherboard bios.  Install went just like any other install after that point.  Debian was the only OS so far that didn't like the Raid0 with my hardware.

---

### Post by lile001 on 2009-07-03
> **cariboo907 said:**
> If you follow the howto step by step you will have a working raid array..

Au Contraire:  If /*I*/ follow the howto step by step, then about the third step the gibberish in the howto doesn't look anything like the gibberish on my screen, and I have no idea how to proceed at all since I don't understand any of it in the first place.  It will say "You will see X" and I see or error message "Z".  Asking about it here has simply produced more reams of gibberish that is also over my head, along with "It worked for me!" OK, congratulations, seriously, I'm glad it worked for you!  

For the last time, RAID on UBUNTU is not for beginners!  You guys that have done it are all experts, don't pretend you are not.  Could your grandma do it? No. I'll be surprised if anyone with less than a years experience with UBUNTU is ever successful at implementing RAID, Howto or no.  Anyone who can even FOLLOW the raid Howto has to have a bunch of experience with monkey-wrenching Linux or some other unix-like system.    You folks who have just sat down with Ubuntu on a new machine, take heed if you think you can get a RAID array working:  "Here there be dragons."

---

### Post by HDave on 2009-07-03
I think it's more about using well supported hardward of any kind, including RAID.  As you say, I am fairly well experienced with Ubuntu, but I still find using hardware that is not well supported to be extremely difficult...I myself have given up (for example using my 3G Treo as a modem).  

On the other hand, if you are using supported hardware, 99% of the time you have to do *NOTHING*.  It just works...silently, perfectly, every time.

I have two machines with two different, but supported RAID cards, and I honestly didn't due anything but set up the RAID configuration in the BIOS, boot the Ubuntu CD and install with all the defaults.  Never even saw the word "RAID" during the entire install process.

I agree with you it's probably time to punt on getting FakeRaid working in Ubuntu.

---

### Post by ronparent on 2009-07-03
lile001

I have only just now read this thread. It has given me several chuckles. I empathise and agree with you totally. I have had many learning pains trying to implement raid0 and raid1 on two systems. Those operations have been sucessful without any major misteps (only I might add because I wouldn't entrust a working win xp install on the raid by trying to install ubuntu to it - I installed to a separate non-raided drive in both cases). Now many solid days of working at it I understand more and am now confident that I could manage a raid install with confidence. 

Although I consider it a valuable learning exercise, it is not to be undertaken by a tenderfoot unless they are totally fearles and persistent to foolishness (me for instance). I disagree with HDave's inference that 8.04. 8.10 or 9.04 can be installed from the live cd without manual manipulation such as described in the Fakeraid HowTo. I understand how you could be totally frustrated and disgusted with the whole thing at this point.

Regards, ron

---

