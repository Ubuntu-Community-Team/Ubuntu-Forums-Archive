---
title: "I need networking software that can do this..."
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by TheForkOfJustice on 2006-08-28
I need open source software that can install Ubuntu over a large network according to very precise specifications.

In case you are all wondering, we plan to use the following configuration to set up a network in a hospital for the Medical Ubuntu project which could save hospitals billions.

Please recommend software and/or console commands that utilize programs already present in Ubuntu. Someday we may need to build a GUI to unite all of these actions but I want to have some idea of what packages and commands I'll need.

They must be able to do this:

**==>** Organize Partitions every system on the network like so:
- 1GB for a hidden and encrypted 'recovery partition'
- 1GB for 'swap'
- 10 GB for '/'
- 5-10 GB for '/home'

**==>** The recovery partition is only accessable to the sysadmin who must present an encryption key. Similar to how Truecrypt works. Is something like this in the repository?

**==>** The recovery partition must store a copy of the network configuration data and a copy of the installation CD.

**==>** The sysadmin can manually initialize a command that will remaster the backup image on the recovery partition after a good update (much like how Windows copies its updates to the i386 folder).

**==>** When a bad update occurs (I'm looking at you Xserver) the network can be restored when the sysadmin runs a program and presents the encryption key from LiveCD or bootable floppy.

**==>** Once Ubuntu is installed on any system below the sysadmin level, it will 'zombify' and begin installing Ubuntu on other systems on the network according to the configuration data copied to the recovery partition. Hopefully, this will make network setup a lot faster. 

**==>** The sysadmin's computer won't be a zombie so they'll have the resources available to stop any part of the process.

**==>** Manual configurations or templates can be used to configure the network.

**==>** Zombies revert to normal systems when the network setup finishes. 

**==>** The rest of the disk will be divided into partitions depending on the remaining empty space. (20GB partitions as long as >25GB remains unallocated, hidden?, protected?, mounted?, Windows partition?, etc...this will be the decision of the Sysadmin since the extra space is superfluous at this point)

**==>** Configure shared workstations to put their '/home' folder on a seperate and proected server. I know this is how Windows networking software is usually set up (Novell?).

**==>** Make it so shared workstations are configured depending on who logs into it. Again, Novell is like this in Windows.

**==>** Make it so members of a department will only be able to log into a workstation (Single-Group access) and that certain actions will prompt a user from this group for their password (like Synaptic does).


Let me know if there is also a program or scripting HOWTO that will help me automate this process.

If none of this exists will some kind soul make it? Ubuntu would be great as a network solution if we could get this going, and not just for hospitals.

If you see flaws or have suggestions post your ideas.

It's all for a good cause.

---

### Post by handy on 2006-08-29
What a magnificent project...

Absolutely awsome potential to save peoples lives due to the financial benefits to hospitals.

I wish you all the very best... :cool: :KS :cool:

---

### Post by funchords on 2006-08-29
> **TheForkOfJustice said:**
> 
**==>** Once Ubuntu is installed on any system below the sysadmin level, it will 'zombify' and begin installing Ubuntu on other systems on the network according to the configuration data copied to the recovery partition. Hopefully, this will make network setup a lot faster. 
Now that's one way to gain market share!:biggrin:

---

### Post by funchords on 2006-08-29
Can we make any assumptions about these systems?  

1.  Are they already running and networked somehow, and Ubuntu is replacing the OS?

2.  Are they all the same, or similar?

3.  How will a machine that is to be installed going to be identified by the trickle-down install technique?  Or, put another way, how is a machine that is to be excluded from the install going to be identified such that the other machines leave it alone?

> ==> Configure shared workstations to put their '/home' folder on a seperate and proected server. I know this is how Windows networking software is usually set up (Novell?).

==> Make it so shared workstations are configured depending on who logs into it. Again, Novell is like this in Windows.

==> Make it so members of a department will only be able to log into a workstation (Single-Group access) and that certain actions will prompt a user from this group for their password (like Synaptic does).
I don't have any enterprise experience with this, but a central Samba server acting as a login authenticator/domain controller should be able to do this part.  It's pretty much what it's supposed to to.  And, of course, it can handle the home directories as well.

---

### Post by tturrisi on 2006-08-29
There are existing utils that can do some of what you want, such as os deployment-installs over a network, backups, cloning etc.  These utils are not included in a default Ubuntu install.  I suggest (to begin with) searching through the Debian Packages dirs to get an idea of what's available:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)  (Administration, Utilities section)

I too am in process of setting up a doc's office with a Deb server & EMR services.  I have been testing different EMR products. (openEMR & others).

Is there an Ubuntu Med iso that I can download & if so where?

---

### Post by TheForkOfJustice on 2006-08-29
No iso yet since we are brand new but we do have a section in ubuntuforums. Look in the 3rd party section for 'Medical Ubuntu'.

Also, you really should contact our lead man rattlerviper. We would love to know what you are up to and what packages you are using since you apparently have some personal experience for the needs of a practioners office.

It would help us greatly if you were to post what packages you installed or plan to use in our forum. We are trying to keep the number and size of the software we plan to use to a stark minimum,  not only because of the 700MB limit of the CD image but also because hospital equipment tends to be older, slower, and without DVD drives.

You would also be a great addition to our staff. *hint hint* :KS

---

### Post by TheForkOfJustice on 2006-08-30
> **funchords said:**
> Can we make any assumptions about these systems?  

1.  Are they already running and networked somehow, and Ubuntu is replacing the OS?

Yup. Already connected and replacing Windows with only free and open source software. Different departments may have different sysadmins and setups for various reasons but there should be nothing stopping them from communicating with each other or using shared databases if the sysadmins want to.

In fact, we will have to make sure a RAID network is set up to store patient info and other documents on both the 'practioner' (single-user) and 'hospital' setting (big ol' network). We have to make sure all data is secure and the system will rarely have hiccups, naturaly. 

In light of the xserver 10.3 patch snafu we have decided to hold our own repos. It also gives us time to make sure none of our packages break when something in the ubuntu repos gets updated.

Too bad our 'zombies' can't install on remote networks and systems.

Damn those other systems and their Administrator privileges! :p

> 
2.  Are they all the same, or similar?


We are talking about hospitals here so their systems are more likely to be i386 with limited media capabilities. But to be on the safe side we plan on using Eft as our base and will have the same hardware-detecting capabilities.

Any software we make will likely use only python and sqlite so our dependencies are minimal.

> 
3.  How will a machine that is to be installed going to be identified by the trickle-down install technique?  Or, put another way, how is a machine that is to be excluded from the install going to be identified such that the other machines leave it alone?

I don't have any enterprise experience with this, but a central Samba server acting as a login authenticator/domain controller should be able to do this part.  It's pretty much what it's supposed to to.  And, of course, it can handle the home directories as well.

I have zero network setup experience myself and have never touched a RAID setup either, which is fine since I'm not the network maven for the project (we're new and haven't attracted one yet).

I can see Samba being the easy solution for this since all of these systems will have Windows on them by default with permissions already set for the sysadmin. Our install could detect the systems and drivers, use parted to shrink the windows partitions and create a 'virtual CD' type of drive that would assist in the installation of Ubuntu with the config data of the system's drivers, driver configuration, the network map and on which networked computers to install Ubuntu. It is best to only install Ubuntu on some at a time and make sure those are up and running first than the whole network, which leaves it unavailable to do daily work and it COULD run into hardware troubles. We want to avoid nightmare scenarios here.

I'm assuming that this way is better than running around the hospital installing Ubuntu on each system manually and then connecting them.
 
What I guess we really need is a GUI that would use Samba and a set of script templates to configure a network to specific needs right away.
We also need to catalogue the packages needed and so on since we need to audit everything that's getting installed.
...
Oi, the work ahead! ](*,):p
...
I should be able to test Samba out at least between my desktop, my laptop and my Aunt's computer upstairs since we are all behind the same gateway.

However, we still need that network maven. I'm no expert.

---

### Post by rattlerviper on 2006-08-30
I'm no Linux networking expert either](*,) ...I wish I would have known my intrests would fall to Linux when I was taking all those college courses when I was fresh out of high school:mad:

We may have to make them run around doing a network installs...Heck  all the MIS people at the hospitals I have worked at had it down to a T Hit this computer then that one.  Possibly after we get a linux networking expert on the project we can make the job easier. 

> We are talking about hospitals here so their systems are more likely to be i386 with limited media capabilities. But to be on the safe side we plan on using Eft as our base and will have the same hardware-detecting capabilities.

Is that how it is in Canada? I always thought of Canada as more progresive I guess. All of the hospitals down here have "dated" but fairly modern systems P2 and P3 uasully...in fact one of them I worked at had a several hundered thousand dollar server room.  None the less we need to be prepared for people in developing countries using it which means light light light, since many will be putting it on "antique" systems.

---

### Post by tturrisi on 2006-08-30
re installing from an image over a network:
[http://linuxplanet.com/linuxplanet/tutorials/5667/1/](http://linuxplanet.com/linuxplanet/tutorials/5667/1/)

I would not use samba but would choose to use single servers with mysql to store network files, emr systems, etc.  This way, any user on the lan can access the data or desired service via a web browser.  I'd also use php scripts to handle sql queries for the data, thus no need for separate applications on each workstation (spreadsheet, word processors, etc.  And if need to use office software limit it to abiword & gnumeric, both lightweight fast applications.  (openoffice is slower & bloated & won't need all the extras features if use sql)

Another option, considering the possibility of the hospital using older systems is to just use a thin client on each workstation. No os installed on disk but boot from cd & run everything live.  The cd could be configuired to auto mount a logical (file storage partition that is same on all workstations) & swap partition on the hard drive and the file storage partition could also hold the /home/user .config files or a file that "remembers" user preferences.  Obviously the live cd would include the option to install e/g to hard drive.

Also, if use lamp or similar then also use ssl for http connections.

---

### Post by TheForkOfJustice on 2006-08-30
P2 and P3 are i386. Expect Celerons. RAM +/- 256MB. 

Probably just enough on many of them just to get XP or NT going, run MS Office and access the internet.

Limited media = just a CDROM (if one at all) and on-board video. They aren't gamers and people buying a lot of systems don't pay for more than they need. Best systems are likely the ones you see when you enter the door.

I would expect P3-level Celerons to be the norm but we should build our iso with slightly older machines in mind.

A few years back I used to work at a commercial lab using  a Win95 POS with a version of Excel that must have been from 1996. I'll bet you anything that it's still being used simply because it still did its simple task well and never crashed. As long as a computer can do its simple task well it may still be used. It makes sense when you consider they were just getting out of bankruptcy.

And, yes there are the 3rd world countries who would use older gear for certain, but they would LOVE us if we could make something that would work on their systems. In fact we should really make this program with them in mind.

I'm not saying that Medical Ubuntu will have to be like Damn Small Linux. I'm saying that all software we include should not soak up more resources than necessary. Especially if we can find a low-resource substitute for a 'bloated' program.
 
Anyway...

The last time I fiddled with the LIS system it was basically a DOS interface running from a window. Visual BASIC, I think. Blue screen with spaces you could type stuff in and you would move between them with the tab key.

Whatever we include it must be just as fast to be considered a decent substitute. Speed and simplicity will be the first thing they'll notice.

I'm going to be gathering a lot of info over the next week or so and I am going to make notes about the LIS interface and other software they use and get copies of the requisition forms of a couple of places. Might as well get a description of the hardware that they use while I'm at it.

What I'm really interested in though is the ability to print barcodes. Automation is common and they usually track samples this way. Scan them and the patient info appears right on the screen. A necessity for our lab software.

---

### Post by rattlerviper on 2006-08-31
Ok, I was thinking you meant real 386 machines were being used up in canada!  Honestly a celeron version of a P3 with 256mb of ram is not very limiting at all:)  I run a celeron CuMine @1.1ghz with 512mb of ram.  I have installed sarge(debian) on a laptop with 64mb of ram and a 300mhz cpu.  Since Ubuntu is based on debian I would think we will have alot of luck catering to the lower end machines.

> What I'm really interested in though is the ability to print barcodes. Automation is common and they usually track samples this way. Scan them and the patient info appears right on the screen. A necessity for our lab software.
I have not looked into it yet, but I would assume there must be some sort of software for printing and reading barcodes since Unix is used by many large corporations worldwide it would make sense they would also use it for inventory control.  Hopefully we find that it is open source, and can then use it to integrate into the sytem as needed.

tturrisi, may I have permision to the buddy list here on the forums(not sure that's what they call it)  Your vast knoledge of Linux networking could come in very handy as a refence for us:D

---

### Post by tturrisi on 2006-08-31
> **rattlerviper said:**
> tturrisi, may I have permision to the buddy list here on the forums(not sure that's what they call it)  Your vast knoledge of Linux networking could come in very handy as a refence for us:D
lol.  I don't have a vast knowledge of linux networking, just experience running a debian woody server & a sarge server at home.  And installing debian about 200 times!  And building my own business application (flooring installation) using php & mysql (it's an database accessable via a browser using php scripts where I can enter data for a client, make an estimate for a job, monitor some stats, log finances, etc).

My father was a podiatrist so am familiar with some of what's needed for a EMR.  My 2 brothers took over his practice & my younger brother wants to move over to EMR but does not want to spend 25k on it!

So I began researching EMR a few weeks ago & tried several different packages on a Debian etch box.  OpenEMR is by far the easiest to install & get up & running, while others, like MirrorMed are easy to install too.  But Vista is way too complicated for me to spend time with, but would be the ideal package to use.

All he wants is patient records, no billing because he already has that setup with a commercial package on Windows & I see no need to tamper w/ what works well for him already.

What I plan to do is setup a basic deb server running lamp and an EMR, setup a new XP laptop for him & he can then access the EMR via a browser in any treatment room and use Dragon to speak the input.  Dragon Nat Speaking works well with html forms.

As for Buddy Lists, I don't use that feature, but feel free to PM me anytime & if we agree on enough things then we can use email.

---

### Post by TheForkOfJustice on 2006-09-02
You sir, have just proven yourself more useful than you think you are :grin:

---

### Post by mdr on 2006-09-07
given the vast range of pc - would it not be easier doing a med version of edubuntu ? aka using terminal servers ?

just a thought...

---

### Post by TheForkOfJustice on 2006-09-08
> **mdr said:**
> given the vast range of pc - would it not be easier doing a med version of edubuntu ? aka using terminal servers ?

just a thought...

We thought about it but we decided to try and stick with Ubuntu so we will be more in-line with the updates. We will most likely include icewm for a more resource-friendly environment.

Best to be a fork of Ubuntu than a fork-of-a-fork of Ubuntu. :D

---

