---
title: "Not enough space to install Ubuntu?"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Tennis on 2011-01-08
Well I was proud of myself for getting through all the steps to the part where I place the CD with Ubuntu on it in the drive, and restart the computer. The install got to 61% where it then said that there wasn't enough space. I think this might be because I didn't "partition" the C drive.

Could somebody tell me if that is actually what I did wrong, and if yes, how do I do that?

I got "computer management" up, but there is no C drive in the list under disk management.

Thanks for the help \\:D/

---

### Post by mikewhatever on 2011-01-08
If you tell us what you did, we can tell you if it was wrong or not.:P
Linux designates partitions differently, not as C or D, but as sda1,sda2,etc.

---

### Post by Tennis on 2011-01-08
> **mikewhatever said:**
> If you tell us what you did, we can tell you if it was wrong or not.:P
Linux designates partitions differently, not as C or D, but as sda1,sda2,etc.

I just restarted the computer, and selected Windows again, and that's where I'm at now. The install for Ubuntu never finished, was at 61%. (not enough memory)

---

### Post by mikewhatever on 2011-01-08
**Not enough memory** means there isn't enough RAM to run the installer.
**Not enough space** means there isn't enough disk space to install everything.
Which one was it?

---

### Post by Tennis on 2011-01-08
Going off of memory I think it was not enough space. Should I go back and check though?

---

### Post by mikewhatever on 2011-01-08
Then allocated more space during the installation.

---

### Post by Tennis on 2011-01-08
Error 28: no space left on device

This is due to insufficient disk space for the install to complete on the target partition. Please run the installer again and select a larger partition to install into.

Pasted with the power of android. :-P

---

### Post by Tennis on 2011-01-08
> **mikewhatever said:**
> Then allocated more space during the installation.

How would I do this?

---

### Post by Tennis on 2011-01-08
Could someone help? I want to get this done tonight.

---

### Post by Tennis on 2011-01-08
Summary:

I restart computer with Ubuntu CD in. Install gets to 61%, then:

Error 28: no space left on device

This is due to insufficient disk space for the install to complete on  the target partition. Please run the installer again and select a larger  partition to install into.


Please, help me figure out what I need to do. I really want to experience Ubuntu.

---

### Post by mikewhatever on 2011-01-08
> **Tennis said:**
> Could someone help? I want to get this done tonight.

Patience, my friend. We are all volunteers here

How much free space do you have on the hdd?

---

### Post by Tennis on 2011-01-08
I don't know if this is what you mean, but:

Local Disk (C:)

Free space: 5.33 GB
Total size: 69.0 GB

---

### Post by Tennis on 2011-01-08
How much free space should I have to make the install? I can clear out some stuff in C drive that I won't need when I switch to linux.

---

### Post by vacco on 2011-01-08
Could you post a screenshot of your disk in disk management? (Right click on (My) Computer-->Manage-->Disk management)
I trust you made a seperate partition for Ubuntu.

---

### Post by Tennis on 2011-01-08
No I haven't made one. I was in disk management, but there was no C drive.

---

### Post by mikewhatever on 2011-01-08
So, you have only one partition (C:\), with 5.33 GB of free space? I'd recommend allocating at least 20GB to Ubuntu for any serious use.

---

### Post by Tennis on 2011-01-08
Now it says "The dependency service or group failed to start." and "Unable to connect to logical disk manager service." When I click on disk management now.

---

### Post by Tennis on 2011-01-08
[http://www.youtube.com/watch?v=bwNLNYhTaEk](http://www.youtube.com/watch?v=bwNLNYhTaEk)

This looks like a good tool, but put 20 GB instead of 100? But mine just doesn't want to work.

---

### Post by Tennis on 2011-01-08
[IMG]file:///C:/DOCUME%7E1/ZACFEL%7E1/LOCALS%7E1/Temp/moz-screenshot.png[/IMG][IMG]http://i56.tinypic.com/1q5qo7.jpg[/IMG]

:(

---

### Post by vacco on 2011-01-08
> **Tennis said:**
> No I haven't made one. I was in disk management, but there was no C drive.

Then how is your system operational? :P

By the way, I do not think Ubuntu require more than 3 GB or so, meaning the install should be possible. Are you using the original Ubuntu CD (not Kubuntu, Ubuntu studio or anything else)?

---

### Post by vacco on 2011-01-08
I have never seen that error message before, but a quick Google search gave me this: [http://www.tomshardware.com/forum/58944-45-problem-logical-drive-manager](http://www.tomshardware.com/forum/58944-45-problem-logical-drive-manager). You should try it out.

---

### Post by libssd on 2011-01-08
A FULL installation of Ubuntu fits comfortably (about 50%) in 8gb; more is better if you want to have room for data.

Assuming that your Windows partition is not chock full, start the installer from optical drive again, and do a fresh install, choosing the manual option for partitioning. Shrink the Windows partition enough to free up at least 8gb, preferably 16gb or more of disk space. Then create a boot partition (mount point = /) for Ubuntu, plus swap roughly equal to your RAM, if you want to use suspend and/or hibernate. If space is tight, you can install with little or no swap (*e.g*., 256mb), but you won't be able to hibernate.

---

### Post by Tennis on 2011-01-08
> **vacco said:**
> Then how is your system operational? :P

By the way, I do not think Ubuntu require more than 3 GB or so, meaning the install should be possible. Are you using the original Ubuntu CD (not Kubuntu, Ubuntu studio or anything else)?


[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

This is what I'm using.

---

### Post by Tennis on 2011-01-08
> **vacco said:**
> I have never seen that error message before, but a quick Google search gave me this: [http://www.tomshardware.com/forum/58944-45-problem-logical-drive-manager](http://www.tomshardware.com/forum/58944-45-problem-logical-drive-manager). You should try it out.


Did that, same result.

---

### Post by mikewhatever on 2011-01-08
> **vacco said:**
> Then how is your system operational? :P

By the way, I do not think Ubuntu require more than 3 GB or so, meaning the install should be possible. Are you using the original Ubuntu CD (not Kubuntu, Ubuntu studio or anything else)?

The installer requires 4GB of free space, but if that's all you allocate, guess how fast will it run out of space.

---

### Post by vacco on 2011-01-08
Hmm... maybe you could boot up your live CD and try to do the same thing with the disk tool there.

And yes, that's the standard Ubuntu CD you've got there.

---

### Post by Tennis on 2011-01-08
> **vacco said:**
> Hmm... maybe you could boot up your live CD and try to do the same thing with the disk tool there.

And yes, that's the standard Ubuntu CD you've got there.



But how would I do that if I can't even install it...

---

### Post by vacco on 2011-01-08
I'm just thinking it would be easier to guide you with your drive if we knew how the partition table looked.

Disk tool should be included on the live CD, so you do not need to install anything to use it.

---

### Post by Tennis on 2011-01-08
Finally some progress:

[IMG]http://i54.tinypic.com/20k5cu0.jpg[/IMG]

Now how can I get it so I can actually see, then partition my C drive?

---

### Post by Tennis on 2011-01-08
[http://forums.cnet.com/7723-6142_102-343501.html](http://forums.cnet.com/7723-6142_102-343501.html)

Gonna try that... seems I have some malware.

---

### Post by Tennis on 2011-01-08
That malware scan didn't work. Current status is still that above picture.

---

### Post by Tennis on 2011-01-09
Is there any other way to partition the C drive besides Computer Management? Like something I can download.

---

### Post by Tennis on 2011-01-09
> **Tennis said:**
> Is there any other way to partition the C drive besides Computer Management? Like something I can download.

Going to try this out: [http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html](http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html)

---

### Post by Tennis on 2011-01-09
> **Tennis said:**
> Going to try this out: [http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html](http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html)


This won't work because the biggest partition I can make is like 3GB, which is my free space.

---

### Post by skyzthelimit230 on 2011-01-09
you might want to try GParted if you want to reize and create a new partition. Its a good tool besides the Dis Management feature of Windows.

Also, you might want to try defragging your C:/ Drive

---

### Post by 1clue on 2011-01-09
What is your intent?

Do you plan on installing Ubuntu and having nothing else on the system, or do you intend to have a dual boot system with both Windows and Ubuntu?

Dual boot is possible, but I've never been especially fond of it.  I've also never even tried windows and Linux dual boot.  Given the trouble you've had just understanding formatting I would recommend that if you intend to keep your Windows install functional then you figure out a way to swap drives until you get more practice.  Don't even have the Windows drive installed when you install Ubuntu.

Pop the drive out of your computer, figure out what exactly it is (model number etc) and go get another one from Best Buy or whatever is close.  Pop in the new one, start off the CD and tell Ubuntu to use the entire disk.

---

### Post by Tennis on 2011-01-09
> **1clue said:**
> What is your intent?

Do you plan on installing Ubuntu and having nothing else on the system, or do you intend to have a dual boot system with both Windows and Ubuntu?

Dual boot is possible, but I've never been especially fond of it.  I've also never even tried windows and Linux dual boot.  Given the trouble you've had just understanding formatting I would recommend that if you intend to keep your Windows install functional then you figure out a way to swap drives until you get more practice.  Don't even have the Windows drive installed when you install Ubuntu.

Pop the drive out of your computer, figure out what exactly it is (model number etc) and go get another one from Best Buy or whatever is close.  Pop in the new one, start off the CD and tell Ubuntu to use the entire disk.

I just wanted to see what it was like... and I'm getting pretty mad. Been at it for 10 hours. I don't care about Windows, I just want to run Ubuntu... 

Side note: cleared some C drive space, currently have 13kb free.

---

### Post by Tennis on 2011-01-09
Well that's the end of all that bs. Laptop is broken. Just starts up, asks for safe mode, command mode or normal, all options force a shutdown.

---

### Post by Kasami on 2011-01-09
I get the feeling you courrupted some of your windows boot files while you were trying to install Ubuntu. Do you have a windows recovery or install disk?

---

### Post by 1clue on 2011-01-09
If you don't care about Windows or any of your data on that laptop then it doesn't really matter if Windows won't boot.

You can get this going.  Forgive my lack of specific knowledge, it's been awhile since I installed Ubuntu so the installer is no longer the same.

I assume you burned the image you downloaded to a CD?  If not, please do so and boot off that.  If you don't care about Windows then make sure you're using something other than the Ubuntu Windows installer.  If your laptop has 32 bit hardware then be sure you have a 32 bit image.  If it's 64 then it won't matter much either way.

At some point the installer will ask you where to install.  Last time I installed it had an option to use the entire disk.  Choose that, or delete any existing partitions if there is no such option.  Be sure to write the changes to the disk.  Keep in mind that by doing so you have pretty much removed any hope of running that version of Windows on your laptop.

I would stick with the defaults as much as possible at this point.  Let Ubuntu decide how to partition the disk and what software to install.

I know you've struggled, but FWIW Ubuntu is extremely easy to install if you're not trying to keep anything else going too, AND as long as you have the correct image.  I've done it in about 5 minutes of human work.

I think your problem has been failure to partition and write the partition.  Just about everything else I can remember, the defaults will give you a running system.  But you need to get the partition right first.

---

### Post by Tennis on 2011-01-09
> **1clue said:**
> If you don't care about Windows or any of your data on that laptop then it doesn't really matter if Windows won't boot.

You can get this going.  Forgive my lack of specific knowledge, it's been awhile since I installed Ubuntu so the installer is no longer the same.

I assume you burned the image you downloaded to a CD?  If not, please do so and boot off that.  If you don't care about Windows then make sure you're using something other than the Ubuntu Windows installer.  If your laptop has 32 bit hardware then be sure you have a 32 bit image.  If it's 64 then it won't matter much either way.

At some point the installer will ask you where to install.  Last time I installed it had an option to use the entire disk.  Choose that, or delete any existing partitions if there is no such option.  Be sure to write the changes to the disk.  Keep in mind that by doing so you have pretty much removed any hope of running that version of Windows on your laptop.

I would stick with the defaults as much as possible at this point.  Let Ubuntu decide how to partition the disk and what software to install.

I know you've struggled, but FWIW Ubuntu is extremely easy to install if you're not trying to keep anything else going too, AND as long as you have the correct image.  I've done it in about 5 minutes of human work.

I think your problem has been failure to partition and write the partition.  Just about everything else I can remember, the defaults will give you a running system.  But you need to get the partition right first.


Well now my CD wont work. It says one is the files is missing. I really hate this. Its obviously not an easy install. Rooting and installing customs roms for my android is much easier.

---

### Post by 1clue on 2011-01-09
I'm guessing that something else is going on.  Try a hard shutdown and then boot into the bios to make sure that the cdrom is booting first.

If your CD worked before and doesn't work now, then you probably either scratched it or maybe damaged the computer when you drop-kicked it down the steps that last time.  :)

If you're tired then take a break, get some sleep and try again tomorrow.  If your CD still doesn't work, then go burn another one from a fresh download, if there's something wrong with the image you've been using then that should get rid of it.

Seriously, if you're using generic hardware and download the correct image, you shouldn't need more than 5 minutes of human work and then just let it run, and you'll have a bootable system.

---

### Post by Tennis on 2011-01-09
Well now I had a blue screen on startup, pretty sure it was a virus. Now it doesn't respond to the power button. Dont wanna spend money at geek guys.

---

### Post by Kasami on 2011-01-09
What does the blue screen look like? Does it have any text on it?

---

### Post by Tennis on 2011-01-09
> **Kasami said:**
> What does the blue screen look like? Does it have any text on it?

It says to disable anti virus, disk defeat or backup utilities. Then it says to run CHKDSK /F to check you hardrive corruption.

---

### Post by libssd on 2011-01-09
> **Tennis said:**
> It says to disable anti virus, disk defeat or backup utilities. Then it says to run CHKDSK /F to check you hardrive corruption.
That means it's trying to start Windows, not Linux, since CHKDSK is a Windows utility. I believe that the correct syntax is chkdsk c:/f

**Reference**: [http://en.wikipedia.org/wiki/CHKDSK](http://en.wikipedia.org/wiki/CHKDSK)

Even though it antedates the current release of Ubuntu by several years, _[The Ubuntu Pocket Guide and Reference]("http://www.ubuntupocketguide.com/index_main.html")_, by Keir Thomas, has the best overview of how to install Ubuntu that I have seen -- including some precautions that you may not have taken, such as making a restorable backup, and defragmenting the hard drive before resizing the Windows partition and then creating a Linux partition from the space made available.

---

### Post by Miljet on 2011-01-09
By any chance, have you been trying to install Ubuntu from within Windows, using Wubi?

---

### Post by Tennis on 2011-01-09
What ever I'll have to spend college money on a new laptop. What should I get? Or should o just get a new hard drive?

---

### Post by Tennis on 2011-01-09
> **Miljet said:**
> By any chance, have you been trying to install Ubuntu from within Windows, using Wubi?


No I haven't.

---

### Post by 1clue on 2011-01-10
Dude.

Unless you have a really old laptop that's not worth working on it's probably fine.  There is very little chance that what happened is anything other than messing up your boot loader when trying to install Ubuntu.

---

### Post by mikewhatever on 2011-01-10
> **Tennis said:**
> What ever I'll have to spend college money on a new laptop. What should I get? Or should o just get a new hard drive?

Just run a filesystem check (chkdsk /f) from Windows recovery console. Google has lots of entry on how to do it. There is probably nothing wrong with the disk, let alone the laptop.

---

### Post by 1clue on 2011-01-10
If I got discouraged that fast I couldn't even run my mac.  I've had more serious problems with it than what you have here, and I haven't even changed anything on it.  I strongly suspect this is the first OS you've ever tried to install, because Ubuntu is about as easy as it gets.  There is no Mac os or Windows os that goes in this easy.

If you're looking for an excuse to buy a new laptop, we won't even try to stop you.  I've used much flimsier excuses than this, and now my excuse is simply, "because I want to."  Just don't blame it on Ubuntu.

Maybe you should look into Gentoo?  [http://www.gentoo.org](http://www.gentoo.org) is what I'm running on my desktop right now.  With that you compile everything from source code.  As soon as you get a bootable system that has a compiler on it, you compile the kernel.  After that you compile absolutely everything else you already had on the system, including the compiler.  From there you start installing software, all of which you compile on your local host.

---

### Post by Habeouscorpus on 2011-01-10
Eek. Gentoo for beginners? That's intense. 

You don't have to get a new computer. Your problem is that the data on the hard disk is all messed up, not the actual physical disk. The Windows Recovery disk has an Autorecover feature on it that'll get it going right as rain. I believe you hit a button during the startup?

---

### Post by Kreacher on 2011-01-10
Real simple question here: Is the computer (laptop?) set to boot from the CD first? If not, then putting any bootable disk in the CD drive and pressing the power button will do nothing but try to boot whatever is on the hard drive. 

I've also found that pressing and holding the power button for about a minute will sometimes power off even a stuck system. 

To me, the message that a file is missing indicates that the computer is trying to boot off of the hard drive instead of the CD drive. Otherwise it would have booted the Ubuntu live CD ... assuming that was what was in the CD drive.

If the hard drive has not been repartitioned, there might be a "factory install" or rescue/recover/restore partition on the hard drive than can restore the system to the factory first boot setup.

Of course, I can be wrong all the way around.

---

### Post by libssd on 2011-01-11
> **Tennis said:**
> What ever I'll have to spend college money on a new laptop. What should I get? Or should o just get a new hard drive?
Installing on a separate drive eliminates all possibilities of interactions. I ran Ubuntu in a 32gb partition of the 160gb drive in my netbook for about a year, before replacing it with a 32gb solid state drive, on which only Ubuntu is installed. IF you want install Ubuntu only, a new drive is a cheap solution. But, if you want to install Ubuntu only, it should be equally possible to wipe your old drive, and install without spending any money.

---

### Post by libssd on 2011-01-11
> **1clue said:**
> If I got discouraged that fast I couldn't even run my mac.  I've had more serious problems with it than what you have here, and I haven't even changed anything on it.  I strongly suspect this is the first OS you've ever tried to install, because Ubuntu is about as easy as it gets.  There is no Mac os or Windows os that goes in this easy.

If you're looking for an excuse to buy a new laptop, we won't even try to stop you.  I've used much flimsier excuses than this, and now my excuse is simply, "because I want to."  Just don't blame it on Ubuntu.

Maybe you should look into Gentoo?  [http://www.gentoo.org](http://www.gentoo.org) is what I'm running on my desktop right now.  With that you compile everything from source code.  As soon as you get a bootable system that has a compiler on it, you compile the kernel.  After that you compile absolutely everything else you already had on the system, including the compiler.  From there you start installing software, all of which you compile on your local host.
While I might be willing to argue that OS X installation is easier than Ubuntu, there really isn't much difference between the two; I have no direct experience with installing Windows 7, so I can't offer any knowledgeable comment there. 

Previous questions by the OP suggest that his technical skills may not sufficient to install Gentoo. Perhaps his best option at this point is to find a more knowledgeable friend to help with restoring Windows (assuming he has a recover disk), then start over.

**OR**, if he really wants to use Ubuntu, do so on a small, inexpensive drive; I received a flyer from Micro Center last week, with closeout pricing of $49.95 for the OCZ Vertex 30 (actually 32gig) solid state drive. I've been using one of these (which cost me a bit more than $50 :(  ), and it is extremely fast: 10.04 boots in about 20 seconds, shuts down in 4 seconds. If I really, really need Windows (I haven't yet), it takes less than a minute to pull the access cover and swap drives, which is less time than it takes Windows to boot. :P

---

### Post by verymadpip on 2011-01-11
I think it's possible to download a Windows 7 recovery disc from the interweb.  I found this link:

[http://www.raymond.cc/blog/archives/2010/05/09/download-windows-7-system-recovery-discs-iso-32bit-and-64bit/](http://www.raymond.cc/blog/archives/2010/05/09/download-windows-7-system-recovery-discs-iso-32bit-and-64bit/)

which appears to have some tips (well, one) for trying to recover Windows 7.  I can't vouch for the integrity of the downloads available at the end of the article.  I have, however, seen some links in other posts in these forums to windows recovery discs.

[I lost Vista (which was a blessing as it goes) & all my pics & stuff (NOT a blessing) the first time I tried to install Ubuntu in a dual boot.  If I'd done my own research, & done it properly, that wouldn't have happened.  That did lead me to using Ubuntu as my main OS though :D].

(I currently dual boot with XP which I pretty much only use for Call of Duty)

---

### Post by libssd on 2011-01-11
> **verymadpip said:**
> [I lost Vista (which was a blessing as it goes) & all my pics & stuff (NOT a blessing) the first time I tried to install Ubuntu in a dual boot. **If I'd done my own research, & done it properly, that wouldn't have happened.**  That did lead me to using Ubuntu as my main OS though :D].
This is one of my pet peeves with Canonical -- the Ubuntu site is structured in a way that encourages installation before reading the documentation. The flow of the home page is:
[LIST]
[*]Take a tour
[*]Download Ubuntu
[*]Join the Community
[*]Get Support
[*]Find a Partner
[/LIST]
**[rant]**
Nowhere will you find a hint to RTFM, or that anything could go wrong, or a recommendation to back up your system before attempting to install Ubuntu. Canonical implies that installing Ubuntu is as easy as falling off a log -- which it is, if everything works on the first try. **But a significant number of users have installation problems with every release**. Canonical says, *"Most of users voting here are users with issues, users with painless experience are not likely to come here. So the statistics here do not represent the reality."* 
[B][I]
[LIST]
[*][What is your Lucid Lynx install/upgrade experience ?]("http://ubuntuforums.org/showthread.php?t=1465548") 28% "Flawlessly"
[*][What is your Karmic Kola install/upgrade experience ?]("http://ubuntuforums.org/showthread.php?t=1305924") 31% "Flawlessly"
[*][What is your Jaunty Jackalope install/upgrade experience ?]("http://ubuntuforums.org/showthread.php?t=1133869") 30% "Flawlessly"
[*][What is your Intrepid Ibex install/upgrade experience ?]("http://ubuntuforums.org/showthread.php?t=963853") 21% "Flawlessly"
[/LIST]
[/I][/B]
I don't know how Canonical arrives at their assumption, but I know that the first time I participated in one of these polls  (Jaunty) I had a good experience, and reported such. Karmic had issues, and Lucid was just about flawless (possibly because, by that time I had enough experience to know that I needed to read the documentation and do my own research before installing). I have participated in the polls for each of these releases. So, these responses may not represent the *complete* reality, but the reality they represent is a real and unpleasant one for thousands of people -- some of whom give up on Ubuntu as not worth the trouble, and then tell their friends that Linux sucks.
**[/rant]**

These comments probably don't belong in this thread, and I have expressed similar opinions elsewhere on this forum in the past. Ubuntu is still my favorite Linux distro, and I'm a big fan, but I wish Canonical would be a little more upfront about acknowledging that stuff happens, and new users should do some due diligence before just downloading and installing the thing.

And now, back to our regularly scheduled broadcast....

---

### Post by 1clue on 2011-01-12
Now I feel like I need to go back and explain my previous post.

I find it frustrating that the OP tells us a problem and then won't really answer diagnostic questions.  The system is almost certainly just having a minor difficulty, and he won't even let us know enough to help.

First off, the Gentoo comment was sarcasm.  I use it, I'm typing from Gentoo machine, and it works well for me.  Not recommending it to anyone who isn't an expert.  I also use Ubuntu on systems at work.

Second, installation simplicity:

I'm basing my installation simplicity/times on older operating systems.  I haven't installed Ubuntu for a year or so, and haven't "followed the yellow brick road" for quite a bit longer than that.

Some years back when I first tried Ubuntu out, it was at work with one of the IT guys.  We burned a CD, installed it and when it was done we looked at each other and said, "Wow that was fast."  Then we took another box and tried it again using mostly defaults and with a stop watch.  From turning the power on with the CD in it to rebooting off the newly installed disk, it took us almost exactly 5 minutes.  There was almost nothing that actually needed some setting other than the default, and those defaults worked pretty well.

Comparing that to Mac OS, also an old version, we had to enter license keys and do all sorts of other things.  No way it could happen in 5 minutes or 10 either.

Most of my more recent Ubuntu installations were Ubuntu Server.  Doesn't count since it's not a desktop.  I just didn't want to have more than I actually needed on the system, so I installed server and then put on the desktop and whatever else I needed individually.  That also takes quite a bit longer than 5 minutes.

---

### Post by garyhibdon on 2011-01-12
well the guy with the issue seems to be pretty quiet, and everyone else seems to be, excuse my french, but pissing and moaning back and forth. the guy OBVIOUSLY doesnt understand half of what anyone is saying.


so, guy with the issue, drop the disk in the cd-rom drive. watch for the bios button and hit it. in the boot section set your hdd first(it explains on the side how to change the options) then restart the computer. it will load the cd up. allocate the entire hard drive for linux and then let it do its thing. 



beyond that, let us know how it goes. and, GOOD LUCK!!!

---

### Post by mikewhatever on 2011-01-12
> **libssd said:**
> This is one of my pet peeves with Canonical -- the Ubuntu site is structured in a way that encourages installation before reading the documentation. The flow of the home page is:
[LIST]
[*]Take a tour
[*]Download Ubuntu
[*]Join the Community
[*]Get Support
[*]Find a Partner
[/LIST]

...

OK, but these above encourage installation as much as articles on global warming. Do me a favor, you are just looking for someone to blame. Even if Canonical had slapped "!!DOCUMENTATION!!" banners all over the site, the majority would have just skipped it. Why? Because people hate documentation. Besides, the OP obviously has a problem with Windows, and I very much doubt a pile of Ubuntu documentation would have eliminated it.

---

### Post by oldos2er on 2011-01-12
[delete]

---

### Post by oldos2er on 2011-01-12
[QUOTE=1clue;10346902]I find it frustrating that the OP tells us a problem and then won't really answer diagnostic questions.  The system is almost certainly just having a minor difficulty, and he won't even let us know enough to help.
/QUOTE]

That happens frequently here. I'm tempted to say "get used to it," but I'm not used to it myself. Not sure what to do other than encourage people to ask questions about anything they don't understand.

---

### Post by verymadpip on 2011-01-12
Now I feel I should explain myself more clearly:

I wiped out my box because I was too lazy & impatient to check out how to dual boot.  It had nothing to do with poor documentation yada, yada ,yada.  If I'd bothered to check it out I'd have known that Ubuntu took care of the partitioning (with a little input from myself) instead of mashing buttons when a different tool didn't work quickly enough for me.

Entirely my own fault :(

I concur with garyhibdon, get that cd in there.........&, Tennis, it'll ***never*** be this much trouble again  
(hopefully) ;)

---

### Post by libssd on 2011-01-12
> **1clue said:**
> Now I feel like I need to go back and explain my previous post.

I find it frustrating that the OP tells us a problem and then won't really answer diagnostic questions.  The system is almost certainly just having a minor difficulty, and he won't even let us know enough to help.

First off, the Gentoo comment was sarcasm.  I use it, I'm typing from Gentoo machine, and it works well for me.  Not recommending it to anyone who isn't an expert.  I also use Ubuntu on systems at work.
Sarcasm, especially really good sarcasm like yours, can be difficult to spot in an online environment. This is one of the few areas where smilies are actually useful.

I may have missed it, but my recollection is that at no time did the OP identify his hardware, beyond saying that it was a laptop. But the fact is, **MOST** people are incapable of providing a good description of what they have done to muck up a computer. When I was doing tech support, we had a saying, "The user is always lying." Not intentionally, mind you, just not providing an accurate account of things.

I have seem some threads where a noob was brusquely blown off by more experienced users; this was not one of them, most responses were patient and polite. Problem solving is not a one-way conversation, but in this case, that's pretty much where we ended up, but not for lack of trying.

---

### Post by libssd on 2011-01-12
> **oldos2er said:**
> [QUOTE=1clue;10346902]I find it frustrating that the OP tells us a problem and then won't really answer diagnostic questions.  The system is almost certainly just having a minor difficulty, and he won't even let us know enough to help.
That happens frequently here. I'm tempted to say "get used to it," but I'm not used to it myself. Not sure what to do other than encourage people to ask questions about anything they don't understand.[/QUOTE]
I am a librarian, and one of the techniques we were taught was something called "the reference interview." The idea is that  someone who comes to a library reference desk with a question rarely asks about what he really wants to know; one of the jobs of the reference librarian is to ferret out what the user is really after. Same principal applies here, but it's more difficult without eye to eye contact, and if the other person refuses to interact, not much can be done. 

I've seen the same thing happen in motorcycle/car forums. Someone posts a problem (often in bitter, frustrated language) then doesn't respond when others in the forum ask for more information.

I have tremendous respect for those people who earn their living on tech support lines. They almost always have someone on the other end of the line who is not in the best of moods (that includes me, several times, when dealing with Comcast), and the good ones are able to talk most people through to a successful outcome (if that is possible). I dealt with a Verizon tech support person last week, trying to activate a Verizon 3G data account for a Chrome notebook -- something that had frustrated me since December 17. I could have been a 75-year old who had never used a computer before, and would have been able to follow her instructions. The important thing was that I stayed on the line for the 30 minutes it took to activate the service. Her customer service was so good that I sent Verizon a compliment after; I hope I provided enough information for her to be individually recognized.

---

