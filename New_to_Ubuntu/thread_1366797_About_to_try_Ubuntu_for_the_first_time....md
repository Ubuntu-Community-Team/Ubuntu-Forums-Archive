---
title: "About to try Ubuntu for the first time..."
date: 2009-12-28
forum: New to Ubuntu
---

### Post by solutionorppt on 2009-12-28
Hello. Long story short, I have finally had it with Vista (reasons are below if anyone's interested).  I have an HP Pavillion Slimline w/ dual Athlon 64's (2.6 GHz, 2MB RAM) and a 320 GB HD.  My basic question is this: Am I better off...

1) Installing Ubuntu along side Vista32 and selecting at startup
    1a) with partitioning
    1b) without partitioning
OR
2) Running Ubuntu on a VM inside vista (if so, reccomend a VM)
OR
3) Doing one of the above on my old laptop (2001 Compaq Armada E500; Pentium 3 128 MB RAM, don't remember clock speed offhand, 20 GB HD) with Ubuntu or with an earlier *nix release?

I am not the most programming savvy person, but I grew up with the old x86 DOS computers going back to about 1993.  (I was initially upset when I realized how ineffective the command prompt in vista is and have become fairly adept at running my DosBox.)  I'm not intimidated by the idea of running a command line/prompt, but want to get used to how the system works before committing to it.

Thanks.


 The new file permissions are beyond absurd; I can't even delete my own folders when I am running my machine as an admin without having to give *myself* ownership through a series of commands in the "elevated command prompt" (seriously... [a href="http://www.vistax64.com/tutorials/67717-take-ownership-file.html"]look here[/a] ). I run some processing intensive software on my home PC for both education (molecular modeling programs, Mathematica, etc.) and my music obsession (FLAC converter, mkw compression schemes) and I can't use half the processing power on my PC without upgrading to 64 bit and losing the ability to use many of my software packages that aren't compatible with 64-bit vista.

---

### Post by tom.swartz07 on 2009-12-28
> **solutionorppt said:**
> Hello. Long story short, I have finally had it with Vista (reasons are below if anyone's interested).  I have an HP Pavillion Slimline w/ dual Athlon 64's (2.6 GHz, 2MB RAM) and a 320 GB HD.  My basic question is this: Am I better off...

1) Installing Ubuntu along side Vista32 and selecting at startup
    1a) with partitioning
    1b) without partitioning
OR
2) Running Ubuntu on a VM inside vista (if so, reccomend a VM)
OR
3) Doing one of the above on my old laptop (2001 Compaq Armada E500; Pentium 3 128 MB RAM, don't remember clock speed offhand, 20 GB HD) with Ubuntu or with an earlier *nix release?

I am not the most programming savvy person, but I grew up with the old x86 DOS computers going back to about 1993.  (I was initially upset when I realized how ineffective the command prompt in vista is and have become fairly adept at running my DosBox.)  I'm not intimidated by the idea of running a command line/prompt, but want to get used to how the system works before committing to it.

Thanks.

 I run some processing intensive software on my home PC for both education (molecular modeling programs, Mathematica, etc.) and my music obsession (FLAC converter, mkw compression schemes) and I can't use half the processing power on my PC without upgrading to 64 bit and losing the ability to use many of my software packages that aren't compatible with 64-bit vista.

Alrighty,

As a first time user, I would suggest that you try it out using either a USB or CD. This way, you could look and see what its all about. BE AWARE that the OS will feel 'slow' as youre loading everything from a cd or usb on the fly, as opposed to from a high speed hard drive.

As a 64-bit user myself, theres only one kink that Ive ever come across, and that is with flash. Default flash has hiccups, but its easily fixable.


Since you are still starting off with Ubuntu, and you decide that you actually want it on your system to see how it will run from the HDD, Install it side-by-side.
This way, if you dont like it for some reason, or you still need files (im sure you will coming from Windows)

Most of your applications are available on Ubuntu, and run quite well. I have both Mathematica and Maple on my system flawlessly. 


Regarding your love for FLAC, I would suggest looking into Medibuntu packages once you get your system up and running. These will enable support for practically any media file ever.



Hope this helps! Have fun!

---

### Post by LuisGMarine on 2009-12-28
If it is your first time I would recommend doing the dual-boot.  Personally I would recommend using the "more stable" version of Ubuntu which is 8.04 Hardy.  Don't get me wrong, 9.10 is great, but I was one of the few that was having extreme problems just installing it.  

8.04 LTS version is more stable, just because the fact that they don't put bleeding edge packages, but instead fine tune the OS.  Thus, allowing more time for beta testing and getting more kinks worked out. 

Being that this is the first time that you are running Ubuntu I would recommend you stick with the 32-bit version, just until you get the hand of what is going on.  You could install the 64-bit version but it sometimes is a bit trickier to get things like java and flash working.  Although there are scripts out there that do all these things for you.  Personally you seem like the smart person, so what the hell go with 64-bit and if you run into trouble just ask here and someone will help you out.you 

I would burn the cd, and run Ubuntu off the cd in whats called "live mode" just to see what the desktop looks like.  Don't be discouraged by the speed either, it's a bit different going from on the fly (Live CD) to actually having these files installed on your hard-drive.  As for the programs you are using I don't know much about, but either 1 they can work on Ubuntu, or there are just as great open source alternatives.

---

### Post by MooPi on 2009-12-28
Actually 64bit flash is a snap and should not pose a problem.

---

### Post by audiomick on 2009-12-28
I'd suggest a dual boot.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Most posts I have seen recommend using Windows tools to re-size a Vista partition.Back up anything important. Chuck out all the superfluous stuff (old files and what have you) de-install redundant programs and de-frag a couple of times. Shrink the partition with the windows partition tool, then start it a couple of times and let it do any file checks it wants to do.

Then, start the Ubuntu installer and install into the empty space.

If you want to get into it a bit, you could think about making a separate /home partition. This is where all your user setup stuff and your data lands. If you should have to re-install at any point, you can re-mount it and have all your stuff back where it was.

If you want to use hibernate, you need a swap partition as big as (or a fraction bigger) your RAM. If you don't want to hibernate, 1GB or so of swap should do you.

---

### Post by Sef on 2009-12-28
Also you could download [URL="http://wubi-installer.org"]Wubi.
[/URL]

---

### Post by tom.swartz07 on 2009-12-28
Also,

Remember that the way that your Ubuntu looks when you first load it up is by no means how it will always look.


This is my current desktop: it grabs Bing.com's daily background image and sets it as my background, I have a dock called Avant Window Navigator on the bottom instead of the boring panels.
[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Szlhf10IO-I/AAAAAAAAAKM/DZEXzJaomp4/s800/Screenshot.png[/IMG]

Ubuntu is like the "Droid" of the computer world. In a world of Windows and headaches, Ubuntu does. If you don't like something about your computer, you can change it with little to no problem.

---

### Post by solutionorppt on 2009-12-28
audiomick - 

I can't actually delete old/useless files. This is what has accelerated my rage at MS into abject hatred...

Thanks for the input guys, I will give it a shot running off of an external drive to get a feel for it...

Anyone know offhand if it will run fastest off a CD, USB flash or HCSD card?

---

### Post by LuisGMarine on 2009-12-28
not to go off topic too much, but the app to the right is called conky right?

---

### Post by tom.swartz07 on 2009-12-28
> **LuisGMarine said:**
> not to go off topic too much, but the app to the right is called conky right?

Yep

---

### Post by solutionorppt on 2009-12-28
tom - 

to continue off-topic topics, that avatar was one of my favorite shirt.woots ever

---

### Post by audiomick on 2009-12-29
> **solutionorppt said:**
> audiomick - 

I can't actually delete old/useless files. This is what has accelerated my rage at MS into abject hatred...

Thanks for the input guys, I will give it a shot running off of an external drive to get a feel for it...

Anyone know offhand if it will run fastest off a CD, USB flash or HCSD card?

Don't know what a HCSD is, but CD is the slowest option.

---

### Post by tom.swartz07 on 2009-12-29
it would run fastest from USB, only if you have a recent 2.0 controller. If not, all of the speeds would be about the same.


Running in live is slow no matter what, and even with USB its not that much of a boost.

Just take it with a grain of salt.


Oh, and yeah- I love woot.

---

### Post by robertcoulson on 2009-12-29
Hi [tom.swartz07]("http://ubuntuforums.org/member.php?u=831692")
Sorry to bother you, but what is the dock called at the bottom of your desktop pic you have attached...??...I like it
Bob

---

### Post by thatguruguy on 2009-12-29
It's avant window navigator.  It's available through Synaptic or the Ubuntu Software Center.  Just search on "avant".

---

### Post by tom.swartz07 on 2009-12-29
> **robertcoulson said:**
> Hi [tom.swartz07]("http://ubuntuforums.org/member.php?u=831692")
Sorry to bother you, but what is the dock called at the bottom of your desktop pic you have attached...??...I like it
Bob

Heck no- youre not a bother at all.
I use 2 docks in fact. The one at the bottom is Avant Window Navigator. Its available in the software center.



If you dont like that, or want something else, I recommend Docky. You have to download that one this way:

If youre using Karmic
```
sudo add-apt-repository ppa:docky-core/ppa
```

Run an update and then simply: -
```
sudo apt-get update && sudo apt-get install docky
```

---

### Post by spikyjt on 2009-12-29
In response to speed of a 'live' system, USB HD will be fastest, then HCSD (although this could be faster, depending on the card and how it is connected), then CD (which will be a lot slower than both the others. Check out Pendrivelinux for scripts to get you started.

---

### Post by mechro on 2009-12-29
@ tom.swartz07...

Presumably you can fry a funcking egg on your CPU?!! :D ;)

---

### Post by tom.swartz07 on 2009-12-29
> **mechro said:**
> @ tom.swartz07...

Presumably you can fry a funcking egg on your CPU?!! :D ;)

HAHA! yeah, my computer always runs a little toasty...
I guess I should pick it up off of the bed once in a while to let some air at it! :P

---

### Post by mechro on 2009-12-29
... I wasn't casting aspersions at your CPU Temp... I just loved your weather report. :)

---

### Post by solutionorppt on 2009-12-31
OK, tried to install wubi, but it tells me immediately upon running the installation executable (pyrun.exe) that: "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR1"

Also, does *nix use a file ownership system? I'm kind of tired of being told I can't delete X because I don't have permission, particularly off of external media on USB/SD mass storage devices.

---

### Post by candtalan on 2009-12-31
> **solutionorppt said:**
> OK, tried to install wubi, but it tells me immediately upon running the installation executable (pyrun.exe) that: "There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR1"

Also, does *nix use a file ownership system? I'm kind of tired of being told I can't delete X because I don't have permission, particularly off of external media on USB/SD mass storage devices.

I would tend to avoid wubi. It is brilliant for  a short term install inside windows for people who do not know what backup, or partition, means, and it is a safe install process. However it rests on top of your ntfs system.  If you do still decide to use the wubi install then the easiest way is to run vista and put the live CD into the CD drive into a running windows machine, then choose the second option to install inside windows.

However, I would recommend an option mentioned earlier here, to re size your vista using resize tools available in vista. Leave empty space on the drive, do not create a new partition, just leave it unused.

Then boot from the live CD, and from the initial menu choose, Install ubuntu. 

Then at the partitioner stage of the install process, choose the option to install into the
'largest unused space on the drive'

hth

---

### Post by peace.gangsta on 2010-01-26
> **tom.swartz07 said:**
> Also,

Remember that the way that your Ubuntu looks when you first load it up is by no means how it will always look.


This is my current desktop: it grabs Bing.com's daily background image and sets it as my background, I have a dock called Avant Window Navigator on the bottom instead of the boring panels.
[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Szlhf10IO-I/AAAAAAAAAKM/DZEXzJaomp4/s800/Screenshot.png[/IMG]

Ubuntu is like the "Droid" of the computer world. In a world of Windows and headaches, Ubuntu does. If you don't like something about your computer, you can change it with little to no problem.
I find your desktop really impressive 
Can you explain a bit more about the conky,AWN and the bing desktop thingie..

---

### Post by J V on 2010-01-26
I would suggest with partitioning, swap first 1 gig should do it, then 10 gig /, then max 40 gig /home, and if you want more space, use a data partition...

this means the fastest HD access is given to swap, second fastest to your apps, and third fastest to your home, also means a fresh install you get to keep your stuff...

---

### Post by peace.gangsta on 2010-01-26
> **tom.swartz07 said:**
> Also,

Remember that the way that your Ubuntu looks when you first load it up is by no means how it will always look.


This is my current desktop: it grabs Bing.com's daily background image and sets it as my background, I have a dock called Avant Window Navigator on the bottom instead of the boring panels.
[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Szlhf10IO-I/AAAAAAAAAKM/DZEXzJaomp4/s800/Screenshot.png[/IMG]

Ubuntu is like the "Droid" of the computer world. In a world of Windows and headaches, Ubuntu does. If you don't like something about your computer, you can change it with little to no problem.
Ok I got the awn and am getting a bit of the bing thing but man I seriously I could murder for a conky like yours!!!!
Please post your .conkyrc files[]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")[-o<!!

---

### Post by egalvan on 2010-01-27
> **peace.gangsta said:**
> ...seriously I could murder for a conky like yours!!!!
Please post your .conkyrc files


+1 for the .conkyrc files

Please share!

without the murder, of course... :)

---

### Post by egalvan on 2010-01-27
> **solutionorppt said:**
> 
3) Doing one of the above on my old laptop (2001 Compaq Armada E500;
 Pentium 3 128 MB RAM, don't remember clock speed offhand, 20 GB HD) with Ubuntu or with an earlier *nix release?

I'm not intimidated by the idea of running a command line/prompt, but want to get used to how the system works before committing to it.

On that older machine, you can try just about any *nix distro,
if you install a minimal system, no GUI.
Command Line Only!
Note... these are also refered to as `server install`.


You are much more limited if you want a GUI-type system.
I can recomend Puppy or Slitaz, they will work well with only 128M of RAM.

> 
 The new file permissions are beyond absurd;
 I can't even delete my own folders when I am running my machine as an admin without having to give *myself* ownership through a series of commands in the "elevated command prompt" 

The advanteges of *nix in this regards is that you can adjust the permisions. 
It`s done once, and you are done.
What you want to do has been done countless times before...
no need to re-invent the wheel here.

And welcome to the *nix world
Where you will find Choices.

:p

---

### Post by shae on 2010-01-27
> **solutionorppt said:**
> Also, does *nix use a file ownership system? I'm kind of tired of being told I can't delete X because I don't have permission, particularly off of external media on USB/SD mass storage devices.

Linux makes use of a very powerful permissions system, which I think UAC is in some ways an attempt to copy.  System files are owned by root and cannot be removed by a normal user.  All the files you own are in your home folder and you can remove these without any problem, unless you accedently get something as root in there.

When you want to run as root, you are able to through the GUI by being prompted for your password or by prepending command line programs with sudo.

Initially this might sound just as bad as your current experience with Vista, but it really isn't.  Programs in Linux are designed from the bottom up with this permission system in mind.  In Winodws, the advanced permissions were just somewhat bolted on with Vista.

---

### Post by peace.gangsta on 2010-01-27
> **egalvan said:**
> +1 for the .conkyrc files

Please share!

without the murder, of course... :)
lol

---

### Post by PhoHammer on 2010-01-27
> **candtalan said:**
> I would tend to avoid wubi.... it rests on top of your ntfs system. 

May I ask why this is a bad thing? I'm looking into a wubi install (even though I've done 
countless traditional install). I'm triple booting a MacBook and I don't want to bork my win7
 and mac os x installs by partitioning.

---

### Post by J V on 2010-01-27
if windows gets fragmented, linux gets fragmented... If you can't get the file big enough on windows, you can't get the file big enough... etc etc...

---

### Post by tom.swartz07 on 2010-01-28
> **peace.gangsta said:**
> lol

I just posted the guide on the how-to's section. It should be approved soon. Ill let you know when it is.

Sorry to hijack the thread- I just wanted to update those who were interested.

---

### Post by reynierpm on 2010-11-28
> **tom.swartz07 said:**
> I just posted the guide on the how-to's section. It should be approved soon. Ill let you know when it is.

Sorry to hijack the thread- I just wanted to update those who were interested.

Where exactly is the guide? I´m looking for How To section but doesn't found nothing.

---

