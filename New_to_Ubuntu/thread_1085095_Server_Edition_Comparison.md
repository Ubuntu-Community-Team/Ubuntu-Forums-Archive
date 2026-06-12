---
title: "Server Edition Comparison"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by tracerbullet on 2009-03-02
[COLOR="Red"]*I have gotten some more detailed info about the difference between desktop and server editions of Ubuntu. See further down the page for progress on this little project of mine.*[/COLOR]

Hi there!

I was looking at the Ubuntu specs, and while the normal distro requires 4GB of hard drive space, apparently Server Edition only requires 1GB!

So I came to wonder what exactly makes up those other 3GB that seem to be essential to a home / desktop user?

Specifically anything that would prevent me from using Server Edition for every day tasks like net browsing, a little bit of image editing, maybe a little python and such?

Could Server Edition double as a light-weight home distro for hard drive impaired computers, or is there something I am missing out on that would prevent this?

---

### Post by egalvan on 2009-03-02
The Server Edition has no Desktop Environment (KDE,Gnome,etc)
It is Command-line only.
It is possible to add a GUI if you wish.
I have one machine set up like that...it does have advantages.
server edition, then kde added.



Here is a quote from the docs...
[https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#id3023755](https://help.ubuntu.com/8.04/serverguide/C/preparing-to-install.html#id3023755)

[I]Server and Desktop Differences

There are a few differences between the Ubuntu Server Edition and the Ubuntu Desktop Edition. It should be noted that both editions use the same apt repositories. Making it just as easy to install a server application on the Desktop Edition as it is on the Server Edition.

The differences between the two editions are the lack of an X window environment in the Server Edition, the installation process, and different Kernel options.

Kernel Differences:

    *      The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.
    *      Preemption is turned off in the Server Edition.
    *      The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.
    *      The Server Edition is optimized for i686 processors while the Desktop Edition is optimized for both the i586 and i686.
    *      Virtualization is better supported in the Server Edition through the enabling of IPC namespaces, and the Xen hypervisor.
    *      Multiple routing tables for the IPv6 protocol are also supported in the Server Edition.
    *      For 32-bit systems the Server Edition is configured to use PAE which allows addressing up to 64GB of memory while the Desktop Edition is configured for 4GB.

[Note]
When running a 64-bit version of Ubuntu on 64-bit processors you are not limited by memory addressing space. [/I]

---

### Post by tracerbullet on 2009-03-03
I see.

And this would be a lack of a window manager exclusively? It still has all the pre-requisites for installing a window manager?

I'll have a look around the forums. =)

Edit:

Ok so as far as I can gather, GNOME / KDE both come out at around 200MB.

Assuming Server Edition also requires X, how much space does X require?

I reckon I could squeeze all my needs into roughly 1,5 gigs?

---

### Post by egalvan on 2009-03-03
> **tracerbullet said:**
> this would be a lack of a window manager exclusively? It still has all the pre-requisites for installing a window manager?

The lack of a desktop environment (which includes the window manager, among others) is the MAIN difference, not the ONLY one.
The other difference is the list of packages that are installed.
Desktop editions install more software, such as Office, 
Games, Graphics, Internet, etc...
These help account for the size difference.

To help illustrate, a couple of years ago I was using a dedicated
server install, it fit on one 1.44Meg floppy.
It only acted as a file server, allowing file sharing over a network.
Command-line, text-only. NO graphics of any sort.


> 
I'll have a look around the forums. =)
Edit:
Ok so as far as I can gather, GNOME / KDE both come out at around 200MB.

Assuming Server Edition also requires X, how much space does X require?


Server Edition does NOT require X, and does not install by default.
I don't know how large it is.
And it's not only the size of the package, but it's dependencies.

> 
I reckon I could squeeze all my needs into roughly 1,5 gigs?

Totally depends on what those needs are.
The fewer GRAPHICAL dependencies, the smaller the install will be.
"A Picture is Worth a Thousand Words"
also means that graphical software can be a thousand times larger :)

There ARE distros out there that fit on a CD-sized media,
and run server-type apps.
A few run off the cd and save config files to either a floppy or thumb drive.

Linux distros used to come on floppy-sized media 1.44Meg.
These were text-based distros, with few packages (such as office suites).
The trend towards graphics, and the growing number of packages included, has pushed the size to DVD territory 4.7Gig.

And again, yes, the Server Edition has full repository support, and uses the same APT-based package management system (apt-get on the command line, not Synaptic in a graphic window)
Equivalent releases use the same repos.
And the kernels have a few differences, which may work to your advantage.
I use the 32-bit server edition (8.04.2 LTS) for better memory management.
8 gigabytes worth of RAM. ALL of it used.
Once the next LTS version comes out, I'll probably up-grade to all 64-bit. Although I am experimenting with 64-bit Hardy.

In summary...

Figure out what you NEED.
This will show you the MINIMUM requirements
Then figure out what you WANT.
This will show you the ACTUAL requirements.

---

### Post by tracerbullet on 2009-03-03
> **egalvan said:**
> 
Ok let me word myself more clearly. I'm trying to set up an OS on less than 2GB of disk space. The idea is to have a "full" distro, because it would run smoother than a live CD.

That's why I was looking at Ubuntu Server Edition, because it seems to be optimized for performance, and it seems to have less useless junk packaged with it.

I need KDE (or GNOME, whichever takes less space, it doesn't really matter).

I need Firefox.

I need a basic text editor.

I'm assuming there's some sort of LAMP included. This is nice.

I would like to have GIMP, but this is not essential.

And that is basically my shopping list.

There might be a few things packed with Server Edition that I could live without, I don't know. But I'm assuming that it will use the full 1GB as advertised and that I have roughly 1GB to shop with.

---

### Post by egalvan on 2009-03-03
> **tracerbullet said:**
> Ok let me word myself more clearly. I'm trying to set up an OS on less than 2GB of disk space. The idea is to have a "full" distro, because it would run smoother than a live CD.

Yes, it is clearer, but we are still working at cross-purposes.
(Sorry, don't mean to sound rude or condescending.)
Mainly because of definitions/meanings.
These are almost totally defined by YOUR needs and wants.
"Full Distro", for instance.
Full for what?
File Server?
Web Server?
Database server?
Office suite?
Graphics manipulation?
Audio/video?
Program Development?
etc.etc.etc.

Let's go on...

> That's why I was looking at Ubuntu Server Edition, because it seems to be optimized for performance, and it seems to have less useless junk packaged with it.


No, Server Edition is optimized for "SERVER-based" performance.
This is NOT the same as any other type of performance.
Server Edition feels "laggier" because Disk I/O is optimized, at the expense of the operator I/O (and just about everything else, for that matter)
Which is why most folks feel that Server Edition is "slower" than Desktop Edition.
It's not, it's just that it's speed lies elsewhere.

As for "useless junk", again a matter of need/want, YOUR needs or wants.

To a gamer, the LAMP stack, GIMP, OpenOffice are all JUNK

To an office worker, the LAMP stack is JUNK

To a casual internet browser, LAMP, OpenOffice and GIMP are JUNK

You need to define what you need/want, and go from there.

Let's go on...

> I need **KDE** (or **GNOME**, whichever takes less space, it doesn't really matter).
I need **Firefox**.
I would like to have **GIMP**, but this is not essential.


These are examples of what PROGRAMS you want....
Not So Good.
> 
I need a **basic text editor**.
I'm assuming there's **some sort of LAMP **included. This is nice.

These are examples of what FUNCTIONS you need.
Much Better

When you state that you need a certain PROGRAM, you limit your choices.

When you state that you need a certain FUNCTION, you give yourself more options

Like this...
Do you need KDE or GNOME, or do you **need a Desktop Environment**?
KDE/Gnome are huge.
There are other DE's that are smaller (some much more so)
XFCE for instance.

Do you need Firefox, or do you need to **access the internet**?
Or do you need email access?
If you need internet access, there are other, smaller apps that can do the job.

And of course,
Do you need Ubuntu, or do you want a **distro to fill your needs**?
There are MANY other distros out there.
Some HUGE (over 9gig), some amazingly small (under 90meg)
Then there are the sub-distros, packaged for specific purposes.
Experimentation is key here.

> 
And that is basically my shopping list.
There might be a few things packed with Server Edition that I could live without, I don't know. But I'm assuming that it will use the full 1GB as advertised and that I have roughly 1GB to shop with.

Well, it is a good list, with the caveats/problems I've outlined.
but it may just be that all that you NEED to do is just not doable under Ubuntu with only 1GB. More work needs to be done, mainly becuase of the storage constrictions.

And running a LiveCd is not necessarily slow...
it depends on the distro's focus...
just look at Puppy Linux. Focused on being small.
It's a LiveCD that loads totally in RAM (with at least 256M)
and runs like the proverbial Bat out of Hell.
The standard download is under 100Meg.
There are larger versions that include more software.

Sorry for such a long post (rant?), but there are too many variables to give a POSITIVE OVERALL answer to your problem.
One can only give GENERAL INDICATIONS, and you will have to do some leg-work on your own.

Gotta go help my significant other with her home-work.

I'll be back tonight (it's 0830AM here). or later.

ErnestG

---

### Post by Roving Sign on 2009-03-03
[http://distrowatch.com/](http://distrowatch.com/)

Looks like some research is in order...

---

### Post by tracerbullet on 2009-03-03
> **egalvan said:**
> 
*(Full, meaning designed for installation on an internal hard drive, as opposed to a live distro that is designed for something else)*
No, you don't understand, I WANT those specific programs. And I WANT Ubuntu.

If I was just looking for a lightweight distro, I would go download what-have-you type live distro, Slax, Puppy, whatever, I would not be wasting anyone's time here on ubuntuforums. :P

My goal: Fit a proper working copy of Ubuntu (stripped as necessary down to the bare essentials (the stuff I outlined (yes that specific stuff))) into 2 gigs **(two gigabytes, not one)** of space.

Now if you can tell me with absolute certainty that this is not feasible, I will accept that and go do something else. But until proven otherwise, I will strive to accomplish this little project (yes I'm a bit of a megalomaniac).

---

### Post by tracerbullet on 2009-03-03
I altered the topic slightly to better reflect my quest. I intend to document my progress and discuss / ask for help in this thread.

---

### Post by halitech on 2009-03-03
if you want to have it as lean as possible and basically just have the apps you know you are going to use/need, then I would do a minimal install (would end up at the CLI) then install xserver, the desktop you want (XFCE or *box so it is smaller), then the apps. 

check out here for more info:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

or start at step 7 here after you do the minimal install:
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566) (yes I know it's Debian but Ubuntu is based on Debian so everything else will work)

---

### Post by mkvnmtr on 2009-03-03
I have done a few minimal installs of Ubuntu. You can leave out a lot of stuff. But if you are looking for a system that works well look at DSL. The whole thing comes in at 50Mb. You can run it off the disk, load it to memory or install it on that 2Gb hard drive and add the packages you want.
   There are others but DSL picked up my hardware and connected to the internet. It is a pleasure to use.

---

### Post by halitech on 2009-03-03
Only things I didn't care about with DSL was 1. root account enabled (and used) by default and 2. packages didn't seem to stay installed after a reboot if it was installed to the HD. Maybe I did something wrong but I would rather do a minimal install of Debian and then add what I want (which is basically what you get when you do the DSL HD install)

---

### Post by tracerbullet on 2009-03-03
> **mkvnmtr said:**
> DSL
If you had read my previous posts, I state that a live distro is exactly what I **DON'T** want. There is something about the way 'lives' are set up that makes them feel... clunky, when trying to use them as every day desktop installs.

This is why I was to start out with a distro designed to work well from inside a computer, but without all the bloat (lol) that comes with a typical "user friendly desktop OS".

@halitech: Those are some excellent guides! I might do something like that in fact.

Ok, so my options as far as foundations for my OS are:

**Ubuntu "Server Edition"** - Ubuntu site says 1GB.

**Ubuntu "Standard Edition"** - psychocats.net says a little over 1 GB.

**Debian "netinst" aka "Minimal Install"** - Didn't find an estimate yet, although the .iso is only 180 megs compared to the 700 megs of Ubuntu.


And my options as far as DE:

**KDE** - Seems bloated. How much / how easily can KDE be stripped down?

**GNOME** - Seems bloated. How much / how easily can GNOME be stripped down?

**xfce** - Seems minimalistic. How is the look and feel compared to KDE/GNOME?



tl:dr
I'm sorry if I seem to write a lot, but I'd like to spend some time and effort researching this stuff. After all, painting your tabletop miniatures is half the fun! Then afterward we'll play a round or two of Warhammer with them ^_^

---

### Post by halitech on 2009-03-03
> **tracerbullet said:**
> @halitech: Those are some excellent guides! I might do something like that in fact.

Ok, so my options as far as foundations for my OS are:

**Ubuntu "Server Edition"** - Ubuntu site says 1GB.

**Ubuntu "Standard Edition"** - psychocats.net says a little over 1 GB.

**Debian "netinst" aka "Minimal Install"** - Didn't find an estimate yet, although the .iso is only 180 megs compared to the 700 megs of Ubuntu.


And my options as far as DE:

**KDE** - Seems bloated. How much / how easily can KDE be stripped down?

**GNOME** - Seems bloated. How much / how easily can GNOME be stripped down?

**xfce** - Seems minimalistic. How is the look and feel compared to KDE/GNOME?



tl:dr
I'm sorry if I seem to write a lot, but I'd like to spend some time and effort researching this stuff. After all, painting your tabletop miniatures is half the fun! Then afterward we'll play a round or two of Warhammer with them ^_^

The Debian net install basically gives you the bare minimum to boot and thats about it. Everything else is pulled from the debian servers as you select and install. I think when I did my last install on my laptop, it was around a gig total. Currently after installing things I use alot its at 2.9gig (I have GIMP, IceWeasel, OOo3 and a lot of other stuff)

KDE and Gnome are both pretty bloated and hard to strip them down too much but you can install just the desktop then add the parts you want, will still be fairly heavy though. 

I use XFCE as my only DE using the steps in the second link I provided and I find its almost a combination of Gnome, windows and Mac. The nice thing is you can customize it to your hearts content on what you want it to look like.

---

### Post by tracerbullet on 2009-03-03
> **halitech said:**
> The Debian net install basically gives you the bare minimum to boot and thats about it.
Reading the Debian guide I'm really starting to like the sound of xfce.

I'm thinking I might want to get a package manager as well. Mostly for the fact that I'm a beginner and it might help me find the stuff I need.

---

### Post by halitech on 2009-03-03
if you follow the steps in the second link I posted it will walk you through it completely. I usually make a change in the steps in that when it first reboots, I do everything at the command line without starting the gui so just add synaptic to the list of programs to install and you will be up and running :)

---

### Post by tracerbullet on 2009-03-03
> **halitech said:**
> if you follow the steps in the second link I posted it will walk you through it completely. I usually make a change in the steps in that when it first reboots, I do everything at the command line without starting the gui so just add synaptic to the list of programs to install and you will be up and running :)
In step 7 of that guide, what exactly is **udev** and what is included in the goodies package?

---

### Post by halitech on 2009-03-03
udev allows for mounting of things like usb thumb drives and auto-detecing hardware. the goodies has all kinds of toys in it, not really needed I don't think but I use a few things from it and its small so I always install it.

I have some links bookmarked to help with speeding things up and multimedia if you want them.

better explanation of udev here: [http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)

---

### Post by tracerbullet on 2009-03-03
I see. So basically there's HAL for mounting CDs. And udev to mount external hard / flash drives.

I think I might not really need HAL. :-s

Anyway, I'm going to bed, and I'll attack the practical phase of this project tomorrow.

halitech, you are a fantastic helper, I am thoroughly enjoying this experience. =)

---

### Post by halitech on 2009-03-03
if you aren't planning on having any cdroms then possibly not but I've never installed without it so not sure what the effect would be to not have it. I think HAL does more then just cds though, just not sure ....


just looked it up and I think you should install it
[http://en.wikipedia.org/wiki/Hardware_abstraction_layer](http://en.wikipedia.org/wiki/Hardware_abstraction_layer)

---

### Post by tracerbullet on 2009-03-04
[http://linuxappfinder.com/package.php?package=hal](http://linuxappfinder.com/package.php?package=hal)

Oh yeah, I don't think I'd want to go cheap on THAT.

Edit: Ooh  your link is way better ^_^

I googled HAL and Wikipedia gave me HAL 9000 =(

Edit edit:

Here is the proper Wikipedia link with information about the hal that you apt-get (as opposed to the concept in general):

[http://en.wikipedia.org/wiki/HAL_(software](http://en.wikipedia.org/wiki/HAL_(software))

---

### Post by tracerbullet on 2009-03-04
So I did a Debian install according to the guide on the Debian forums, and it runs super smooth! :D

I even have almost 600 megs left out of the 2 gigs.

But, I can't for the life of me get xorg.conf to disable my touchpad. (setting /dev/input/mice to /dev/input/mouse0 did not help (mouse0 obviously is my external mouse))

Now I'm not expert, but my xorg.conf seems rather empty. There isn't even a ServerLayout section in it.

I suppose I will sleep on in and maybe I'll wake up with the solution.

---

### Post by halitech on 2009-03-04
Debian and Ubuntu use a lot of automagical setup so xorg.conf is basically ignored now. Does your external mouse work?

---

### Post by tracerbullet on 2009-03-05
> **halitech said:**
> Does your external mouse work?
It works great. If I set xorg.conf up with the /mouse1 option, then Debian ignores input from mouse0 (my external mouse) and it is effectively disabled.

However setting it to /mouse0 does not have the same effect; my external mouse works again, but the touchpad does too.

I did this on another distro and it actually worked. But that xorg.conf file had a proper ServerLayout section, and I could simply put in "Mouse0" "CorePointer".

Of course making a ServerLayout section on my Debian install crashes X with the error "No screen found" (screen works fine otherwise).

---

### Post by tracerbullet on 2009-03-05
So here's a fun fact about GRUB:

If you install it on a "slave" (I guess this is the reason, correct me if I'm wrong) hard drive, it re-writes the MBR on your master hard drive, and THEN puts the GRUB files on the slave drive.

So basically now, if I wipe my master (which contains Vista) drive, Vista will obviously be gone, and GRUB will be broken, so I can't boot into Debian.

If I wipe my slave drive, Debian will be gone, and GRUB will be broken, meaning I can't boot into Vista.

"Ahah!" you say. "But you can just boot from your Vista CD and run FDISK /MBR to boot into Vista again!"

Yes. Yes I can. But what if I (hypothetically) wanted to do it the other way around? How would I get Debian to boot after I wiped the Vista (master) drive?

Essentially what I am asking:

Is there a way to force GRUB to install itself exclusively on the slave drive, so that I can use BIOS to boot from either drive and get two different bootloaders? (Or alternatively, is there another tool/method that will do the job (booting Debian after I select its hard drive in BIOS)?).

And remember that this is on a laptop, so it's going to be hard to rip out one hard drive, if you are thinking of suggestion that. :P

---

### Post by egalvan on 2009-03-05
> **tracerbullet said:**
> If you had read my previous posts, I state that a live distro is exactly what I **DON'T** want.
 There is something about the way 'lives' are set up that makes them feel... clunky,
 when trying to use them as every day desktop installs.

This is why I was to start out with a distro designed to work well from inside a computer,
 but without all the bloat (lol) that comes with a typical "user friendly desktop OS".



OK, I'm back for a while...

And let's start by dispelling some "myths"...

A "liveCD" distro is, basically, designed to run off a CD/DVD without touching the hard drive, or any other storage device, on the host computer.
They can be desinged to run totally from RAM,
or can run from RAM if enough is present,
or can run from RAM and the CD/DVD if not enough RAM is present.
(or they can be designed to run in RAM and CD/DVD)
One can also have them run from a USB drive, BTW.

A LiveCD normally sets up a full Linux file system, inside RAM, where the software is run.
This mirrors the way a Linux system will set up a file system on a hard drive.

Running Ubuntu as a LiveCD is no different than installing it and running it from the hard drive. (so much so that the exact same iso is used for both)
Slower, yes, because it needs to access the CD/DVD for software, 
and this is, of course, slower that a hard drive.

Running  in this limited fashion is one reason LiveCD's feel "slower" or "laggier" than on run from a hard drive install.
But for many LiveCD, this is the ONLY reason they run slower.

What you mean by "clunky"?
It runs in fits and starts?
Pauses here and there?

Note that some LiveCD distros are optimized to run totally in RAM.
Try Puppy Linux.
As I've stated  before, if your machine has at least 256Meg, it will load in RAM, and run FAST!!!
It does not touch the hard drive, or the CD, after it boots.
But (and here is where Puppy shines) you can also install it onto the hard drive, and it will still load itself into RAM, and run from RAM.

I realize you want to use Ubuntu, and want certain software, and want to do it all in under 2gig.
As others have stated, starting with a bare-bones server install, 
then adding what you need can possibly get you this.
It will be work, but it will be educational as well. :KS
And I hope major fun. :)

And might I add that all software is designed to "run inside a computer" :)  sorry, I couldn't resist... ;)

But just to dispel your negative vibes about all LiveCD's being "clunky",
do try Puppy 4.2.
It's a small download... under 100mb.
I followed a guide on this forum to extract the four files needed for a hard disk install,
created a partition for Puppy, cleverly named it puppy,
added the proper stanza to GRUB's menu.lst,
and now happily boot Puppy whenever I feel the need-for-speed.

ErnestG

:popcorn:

(
Note, I am NOT suggesting that Puppy will cure all ills, 
and fulfill your server needs...
just that it's a fast, rather full-featured distro.
On my Dell GX280 desktop, and my HP MediaCenter laptop,
Puppy 4.2 found all the hardware, and runs very well.
The main Puppy partition is under 100Meg in size.
to this I have added  WAY TOO MUCH software, basically everything under the Puppy sun. which added 1.2GB. which is NOT needed.
)

---

### Post by tracerbullet on 2009-03-06
> **egalvan said:**
> 
Hi egalvan, and thanks for that very detailed post.

I quite understand what you are trying to say, but I just want to remind you that the whole purpose of this project is to avoid live distros.

I know for a fact what you are saying about lives is quite true, my main distro is actually a Slax install on an 8 gig flash drive.

I still stand by my "clunky", however, as it does tend to take breaks now and then to decompress modules.

At this point, let just document quickly what I have been doing so far:

I used halitech's link to set up a Debian minimal install, and it did actually come out around 1,5 gig with most of the stuff I added.

I then discovered that in the process of installing Debian, GRUB had nested itself in a few different places. Specifically in the MBRs of my hda and hdb, meaning I could not alter either at the risk of breaking the boot loader.

(As a side note, I did actually muck around with GRUB and it did break, and I think I may have melted the entire Debian install in the process, so I will be starting over again once I find a suitable replacement / modification for GRUB.)

---

### Post by tracerbullet on 2009-03-06
[COLOR="Red"][I]Note: Even though this post is meant to document my progress, and not necessarily as a guide for others, it may well happen that someone has the same problem and decides to use some of these steps.

Therefore, I wish to note that all apostrophes ' <-- these guys, are merely there to encase stuff, as I can't be bothered putting in code tags. So make sure when typing that you don't include any of my apostrophes.[/I][/COLOR]

Ok so here is my (ongoing) process to get Debian and Vista to boot from their respective hard drives using their respective bootloaders:

1. I did a minimal install of Debian following the steps from [this guide]("http://forums.debian.net/viewtopic.php?t=26566&start=0&postdays=0&postorder=asc").

[I]Note: In the process of installing Debian, GRUB overwrites your master hard drive's MBR (In my case this is my Vista drive).

GRUB is now a bit spread out. The /boot folder is on my Debian drive, while the relevant parts are written to the MBR on my Vista drive. This means I have to boot from my Vista drive, which then launches GRUB from the /boot/grub folder on the Debian drive (Confusing, right? :P ). [/I]


2. I found [another guide]("http://www.freesoftwaremagazine.com/articles/grub_intro?page=0%2C0") which details how to install GRUB manually, this way it writes to the MBR of whichever drive you choose.

*Note: In the process of installing GRUB manually, my Debian hard drive was detected as hd1 (as opposed to hd0, which is the master drive). When turning on the computer and using BIOS to boot from the Debian drive, it was rearranged to hd0. Thus:*


3. I modified the Debian GNU/Linux entry in GRUB to point at hd0 instead of hd1. I did this from within GRUB as such:

[COLOR="Red"]Edit: I just realized this process doesn't save any changes, it just uses the settings to boot, and then discards them.[/COLOR] It was not hard to locate the relevant lines in menu.lst and make these changes permanent.

--- 1. Select the entry in GRUB which you wish to edit.

--- 2. Press 'e'.

--- 3. Select the line which contains ' (hd1,0) ' and press 'e' again.

--- 4. Replace the 1 with a 0 and press enter.

--- 5. Press 'b' to boot with your new settings and see if it works.

*Note: There is another way of doing this, by modifying your menu.lst file. But since I could not boot into Debian at this point, and the necessary tools where right there, this was the easiest option for me. Your experience may vary. :D*


4. I rebooted my computer and (still having my Debian drive as hd0) repeated step 3 for the Vista entry in GRUB. I edited the entry and changed the first line from ' (hd0,1) ' to ' (hd1,1) '.

Vista boots as well now (Hurray!).


5. I am about to run fdisk /MBR to re-write a Windows MBR to my Vista drive. If I don't mess up this step completely, I should end up being able to boot my Debian drive from BIOS and entering GRUB, which will then boot Debian, AND boot my Vista drive from BIOS which will have the Windows MBR launching Vista.

Cross your coffee mugs! I hope this works ^_^

[COLOR="Magenta"]Edit: Ok this is retarded. Apparently Vista does not have fdisk. :shock:

Edit edit edit: For the record, chkdsk /mbr does nothing on Vista, either.[/COLOR]

Edit edit: Even more retarded. [www.microsoft.com](www.microsoft.com) is down. :shock: :shock:

I guess Bill forgot to pay his ISP this month.


6. INTERMISSION! In this step I have a coffee break and just goof off for a while.

I attempt to create a splash screen for my GRUB. This has no real functionality except making it look pretty.

The splash turned out [really nice]("http://www.eviloatmeal.com/2splash.png")! (Well I like it anyway, it really shines on my laptop monitor.)

7. At this point, I'm having a hard time coming up with more tricks to try, so I'm getting close to my last resort, downloading and burning a Vista recovery CD. That is, if I can find any CDs lying around.

---

### Post by egalvan on 2009-03-06
> **tracerbullet said:**
> Hi egalvan, and thanks for that very detailed post.

I quite understand what you are trying to say, but** I just want to remind you that the whole purpose of this project is to avoid live distros.**

Yeah, I understand that... and I respect your choices.
I just wanted to be sure you understood that the "LiveCD" label can mean different things, depending on the distro's authors ideas and philosophies.
Some de-compress completely when installed to a hard-drive, and some stay compressed (or partially so)
Different approaches, and they give different results...
but it's not the LiveCd side of it that makes the difference.
Which is what I want to emphasize.

> 
I know for a fact what you are saying about lives is quite true, my main distro is actually a Slax install on an 8 gig flash drive.

I still stand by my "clunky", however, as it does **tend to take breaks now and then to decompress modules.**

Just my point... slax apparently keeps some compression even when installed to a hard drive.
But not all LiveCd distro do this...
and it's not fair to see them all in this fashion... it can limit your distro choices.

Also, a USB FLASH drive is NOT an IDE-connected drive.
Yes, seek speeds are essentially zero.
Random/Sequential access thus becomes the same.
But the read/write speeds can be quite different, however.
Consumer-grade USB flash is generally VERY slow on write,
and even reads are not that fast.
So it's not really a valid comparison.
(the less-expensive SSD (Solid State Drive) devices use flash-like architectures, and they have very slow writes.
The more expensive SSD devices use a different architecture, and read/write much faster)

A distro designed to run from flash would have absolute minimum writes, and reduced reads; preferably zero on both, not attainable in practice.
A regular Linux install is quite disk-I/O intensive.
(indeed, *nix architecture is quite disk-I/O intensive)

And let's face it, regular Ubuntu is installed from a LiveCD. :)
(this is not true of the Alternate or Server installs)
 


> 
At this point, let just document quickly what I have been doing so far:

I used halitech's link to set up a Debian minimal install, and it did actually come out around 1,5 gig with most of the stuff I added.

I then discovered that in the process of installing Debian, GRUB had nested itself in a few different places. **Specifically in the MBRs of my hda and hdb, meaning I could not alter either at the risk of breaking the boot loader.**

once I find a suitable replacement / modification for GRUB.)


I'm not sure this is typical GRUB behavior...
It's been a few months since I installed to my multi-drive/multi-boot machine,
 and it's down for "enhancements" at the moment (4x2G RAM replacing 4x256M RAM, and a pair of 1TB drives replacing 2x200GB drives).

I can't verify this at the moment.

I woould say to verify this behavior before you spend too much time on other "solutions" to a problem that might not be.

And re-installing GRUB is fairly simple...
caljohnsmith (The Guru Master of All Things Boot) does it in four short commands (or less) :)

---

### Post by tracerbullet on 2009-03-06
> **egalvan said:**
> And re-installing GRUB is fairly simple...
Oh yes, definitely.

I reinstalled Debian and did a manual install of GRUB (see my previous post for walk through of what exactly I [S]broke[/S] did).

And it certainly works fantastically now. My next obstacle is figuring out how to restore my Vista MBR, since this laptop was not supplied with proper Vista CDs (just those in-house brand "Recovery" CDs, gosh I hate those!), and FDISK /MBR does not exist in Vista.

I'm not sure I have any more CD-RWs to burn through (no pun intended), so downloading an iso will also be tricky.

Edit:
Oh and I love my new [GRUB splash]("http://www.eviloatmeal.com/2splash.png")!

---

### Post by tracerbullet on 2009-03-06
> **tracerbullet said:**
> Edit edit: Even more retarded. **w****w****w****.mic****ro****so****ft.com** is down. :shock: :shock:
Holy **** ****, I just [realized what this is]("http://ubuntuforums.org/showthread.php?t=1087049&highlight=rootkit")...

---

