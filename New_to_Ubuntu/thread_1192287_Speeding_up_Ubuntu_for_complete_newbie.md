---
title: "Speeding up Ubuntu for complete newbie"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by rubik on 2009-06-19
Hey ya'll! I just dual-booted my dell laptop with ubuntu but I'm having speed issues. Booting is fast (15s) but it opens programs and menus much more slowly than windows vista, and it struggles with visual effects. I mean, anything should be faster than vista, right? First I thought I needed to install the driver for the cpu, but I couldn't find any for ubuntu. Here are my machine specs:

Dell Inspiron 1525
Intel 2.0 GHz Dual Core processor
3 GB RAM
Running Windows Vista and Ubuntu 8.04

Can I make ubuntu run any faster? Am I missing something here? I though linux was supposed to be fast!
Thanks for the help!

---

### Post by shae on 2009-06-19
You may not be able to make it that much faster, but a useful guide for such tweaking is: [http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/](http://kmandla.wordpress.com/projects/set-up-ubuntu-for-speed/)

---

### Post by jonobr on 2009-06-19
could you try disabling your video effects to start and see if that makes things any better,
(im not on my ubuntu desktop at the moment. so right click on the deskstop select backgroubd props, go to the tab at the end (visual effects??) and then select none,

from there, can you let us know what apps your running that appear slow...

Some apps may take a bit of time to start, so its all relative...

if its just general stuff lets us know what your doing

---

### Post by cariboo on 2009-06-19
Do you have a restricted graphics driver installed? Check System-->Administration-->Hardware drivers. Click the driver and it should install automagically.

---

### Post by dailyacts56 on 2009-06-19
How big is your hard drive?

With 3 GB of RAM, I cannot understand why Ubuntu is so slow and the reasons you are having other problems.

I have an HP Slimline. It has 1 GB of RAM and 186 GB of hard drive space. Ubuntu literally flies on my computer. 

I do not know the answers to your problems because I am a newbee to Ubuntu, but I wish you the best of luck fixing your difficulties.

---

### Post by rubik on 2009-06-20
Boy, you guys sure respond fast!

I already have the visual effects set to "none" because it won't let me set them any higher. After searching for a moment for "graphics drivers" it says that visual effects cannot be enabled. Main offenders for slow programs are mozilla, rhythmbox, and word processor.

When I went to the list of drivers, all it listed was one for the wireless. Probably a problem there...

Hard disk size is 250 gb, but the partition is 20. rpm is 5800 I think.

---

### Post by shae on 2009-06-20
In my experience with Linux, Firefox and OO.o are a little bulky in terms of start-up time and overall experience.  Unfortunately, there is not much you can do, but you could try Swiftweasle or Epiphany-browser and see if they are faster to your likeing.  You could also try Abiword and Gnumeric for faster word processing and spreadsheets.

Rhythmbox usually is not much of a problem, unless you have a very large library.

---

### Post by sloggerkhan on 2009-06-20
If you use intel integrated graphics, there are currently performance regressions in the driver. These may be slowing your desktop experience.

---

### Post by theozzlives on 2009-06-20
> **rubik said:**
> Boy, you guys sure respond fast!

I already have the visual effects set to "none" because it won't let me set them any higher. After searching for a moment for "graphics drivers" it says that visual effects cannot be enabled. Main offenders for slow programs are mozilla, rhythmbox, and word processor.

When I went to the list of drivers, all it listed was one for the wireless. Probably a problem there...

Hard disk size is 250 gb, but the partition is 20. rpm is 5800 I think.

The only thing I can think of is you only have 20 GB for Ubuntu. I make my root (/) 10-20 GB (depending on the HD), then with 3 GB RAM you need at least 6 GB for swap, then whatever for /home (I use the rest of the drive, but I use [VirtualBox]("http://www.virtualbox.org") for Windows).

BTW: What GPU do you have?

---

### Post by treesurf on 2009-06-20
I agree it sounds like you may have one of the troublesome intel chipsets.  Check out this thread for solutions:  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Typing "lspci" in the terminal should tell you what your video controller is, among other things.

---

### Post by ramjet_1953 on 2009-06-20
Your speed problem is almost certainly that you are not running the correct video driver for your system.

Let us know what video card or chipset that your system has and we may be able to provide a solution.

If you run this command in a terminal and check the [COLOR="Blue"]* display[/COLOR] section you will see what your video hardware is.

```
sudo lshw
```

Regards,
Roger :D

---

### Post by powel212 on 2009-06-20
+1 epiphany browser for speed.

Powel

---

### Post by rubik on 2009-06-21
* display says the card is "Mobile GM965/GL960 Integrated Graphics Controller" by Intel.

I'll also shrink my vista partition and try out epiphany tomorrow.

---

### Post by ShinHadoken on 2009-06-21
Ok, use the Partitioner within Vista for this. If you do, Windows does a LOT less complaining than it does if you use Gparted or an alternative. Also, keep in mind that shrinking your Vista partition is useless if you don't expand your Ubuntu partition. Fo this, I recommend getting Gparted through APT/Synaptic. As for your speed issues, make certain your swap space is AT LEAST 6GB. For a desktop system, you should have a swap space twice the size of your physical memory. This will allow you to run a large number of applications (most of which will be idle and easily swapped, providing more RAM for your active programs).

Now, the most probable case for your Ubuntu install running so poorly is the graphics issue you are having. I second treesurf's notion, and suggest you look at this [thread]("http://ubuntuforums.org/showthread.php?t=1130582"). If this doesn't work, let us know, because the issue if definitely graphics related. It might help us to know a little more about the machine--I believe you mentioned something about Dell, is this a laptop you've purchased?

---

### Post by rubik on 2009-06-22
Actually, linux is running on an unpartitioned space on the hard drive. Only vista is on a partition.

I read that thread, but I got a bit scared when I saw the disclaimer at the top, 
"Warning: Although I have made an effort to make this guide as accessible as possible, if you are a beginner to Ubuntu then you are not recommended to follow this guide at all. Even if you stick to the safest method outlined, your system may experience difficulties due to the installation of unofficial drivers. Consider yourselves warned."
Is there something I need to do to make it safer?

My laptop is a Dell Inspiron 1525, bought it a little less than a year ago. If you need any other information, I'll be happy to give it to you.

---

### Post by Steelmourne on 2009-06-22
It could be the graphics driver. Enter lspci > hardware.txt in terminal, then open up the file in your home folder and search for the vga controller. Manually installing drivers may be possible. If not try defragmenting from within windows, or give xubuntu a shot

---

### Post by Knacker on 2009-06-22
Definitely a problem with your graphics: I've had similar issues with my intel chip and jaunty. Two things you should try: 

1) First, be sure that you have the latest xserver-xorg-video-intel package. If you go into synaptic package manager and search for "xserver-xorg-video-intel", the latest version (synaptic should show this) should be 2:2.6.3-0ubuntu9.3 (note the 9.3). The simple way to know is, once you've found this package in synaptic, to right click on it and if there is an "upgrade to latest version" option, click it. Then restart your computer, see if that fixes things. If you're up to date and there is no later version, then you may also consider option 2...

2) Go to this page and follow the instructions. 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Very simple, and even more simple to undo if you don't get any benefit (instructions for how to undo are included). This has worked for a lot of people too.

Hope this Helps!

---

### Post by ShinHadoken on 2009-06-23
> **Knacker said:**
> Definitely a problem with your graphics: I've had similar issues with my intel chip and jaunty. Two things you should try: 

1) First, be sure that you have the latest xserver-xorg-video-intel package. If you go into synaptic package manager and search for "xserver-xorg-video-intel", the latest version (synaptic should show this) should be 2:2.6.3-0ubuntu9.3 (note the 9.3). The simple way to know is, once you've found this package in synaptic, to right click on it and if there is an "upgrade to latest version" option, click it. Then restart your computer, see if that fixes things. If you're up to date and there is no later version, then you may also consider option 2...

2) Go to this page and follow the instructions. 
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
Very simple, and even more simple to undo if you don't get any benefit (instructions for how to undo are included). This has worked for a lot of people too.

Hope this Helps!
I second this motion.

---

### Post by rubik on 2009-06-24
Defragging didn't seem to help, even when from within windows.
My intel package said "ubuntu9" instead of 9.3, but it didn't give the option to upgrade.
I also clicked on the link, but me being a Complete Newbie, I had no idea what they were talking about when they said /etc/apt/sources.list.

[FONT=Verdana]Thanks for your patience![/FONT]

---

### Post by philcamlin on 2009-06-24
hmm my ubuntu isnt slow :popcorn:

---

### Post by Sjeti on 2009-06-25
You don't really need a swap 2x the size of your RAM.  Most people won't even notice if they don't have a swap.  

The only time your swap will get used significantly will be if you hibernate, at which 1 or 1.5x your ram in swap space should do.

---

### Post by AnimalMagic on 2009-06-25
> **rubik said:**
> Actually, linux is running on an unpartitioned space on the hard drive. Only vista is on a partition.


Nobody picked up on this? Ubuntu is slow if run off the live CD or the wubi install... Not sure what OP means by 'running on an unpartitioned space'

Swap space is rarely used by ubuntu, so 6 gb is waste unless you are really loading your system.

---

### Post by Papa-san on 2009-06-26
Yeah, I just read thru this thread and noticed that he is running a live CD.

Rubik:
You need to go ahead with the install. If you were using a 'Windows live CD'(which doesn't really exist), it would take as long or longer to load your programs.

The other thing to keep in mind is that any changes you make to your 'system configuration' are going to be temporary. Installing new drivers while in a live environment is useless because you will have to do them all over again each time you re-boot into a live session of Ubuntu.

Now, as someone who has three of the 1525's, I can tell you that it will work very well on your laptop. The only real issues you may run into are :
- 1 Your wireless card. Do the ```
lshw -C network
``` and you'll be able to see which one you have.


- 2 Operator error. 
I was a true n00b when I set them up with Ubuntu, so I can help walk you through it.
P.S. - I have 2 GB of swap, and it has NEVER been fully utilized. You won't need more than that, and by the time you do, you'll know how to give yourself some extra space!

---

### Post by rubik on 2009-06-26
Oh sorry, I didn't mean to say that. I did install Ubuntu from the disk onto the drive, and it is on a partition separate from vista. I use the GRUB bootloader to boot. Here's the website that told me how:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Terminal said my wireless card was BCM4312 802.1b/g made by Broadcom.

Papa-san, a walkthrough sounds VERY nice. At least at first, I only installed ubuntu because I was bored, so I'm a complete noob.

---

### Post by raymondh on 2009-06-26
Reading materials from fellow-member lovinlinux:

[http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Good luck.

---

### Post by Papa-san on 2009-06-26
The instructions on that site look pretty good. Unfortunately, they didn't include installing it with a separate '/home' partition, which I would HIGHLY suggest. (A separate /home partition will allow you to keep all of your personal stuff in the _likely_ event of having to do a re-install.) 
Now is a good time to do it, as you don't have a lot of stuff in there that isn't easily replaceable. 

In the how-to that you used, you will want to go through the 'Install' again. (Page 3) When you reach "Prepare disc space" you will want to choose "Specify Partitions Manually (advanced)"

First, please let us know how you actually partitioned your drive:
Go to System>Administration>System Monitor. Then click the "File Systems" tab. Collect a screenshot and attach it to your next post.

I'm headed to bed soon, but in the AM, I'll try to include a link to a good how-to on setting up a separate /home partition. (Unless someone else happens to know of one! :D lol)

Look [here:]("https://help.ubuntu.com/community/CategoryInstallation") for starters... a lot of good info!

---

### Post by raymondh on 2009-06-26
> **Papa-san said:**
>  (Unless someone else happens to know of one! :D lol)

Here's a link of another UF member helping a fellow create and manual install a separate /home.

Starts at post 8 by Didius Falco.  Note that OP had a unallocated space already set.  Something you can do from windows, using the windows disk management tool.

[http://ubuntuforums.org/showthread.php?t=1175277](http://ubuntuforums.org/showthread.php?t=1175277)

Post back if you decide to create a separate /home partition and need assistance.

More link:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck.  Back-up your files first.  Anytime you work on partitions and partitioning, there is no gurantee.

---

### Post by Papa-san on 2009-06-26
I highly recommend most of the 'psychocats' stuff you'll find! And, since you did it the right way by using the Windows disc management tool to allocate your space, You should be able to follow it and make it work properly!
Then we'll get the rest of the Dell 1525 stuff tweaked for you!

g'nite all!

---

### Post by rubik on 2009-06-29
Sorry guys that I took so long to reply, I hope you don't mind...

Anyway, attached is a screenshot of the system monitor window. There's nothing important that's saved within linux, so erasing the partition shouldn't be a problem.

Thanks!

---

### Post by Papa-san on 2009-07-16
Sorry 'bout the delay...
Just spent 16 days camping... 
What a good time! But glad to be home!

The link posted above for the psychocats 'separatehome' instruction page will allow you to make the necessary changes without re-installing. My personal preference is to do it as a part of a clean install, but maybe that is all my windows experience talking. (Ya just can't make 'repairs' or 'modifications' to windows without it getting screwed up... that's just the nature of windows.)
I would suggest that you allot no less than 8 gigs of space for your root ( / ) partition. You used 6.5 on the install, and might want a bit more for later additions. Your /home should be OK with about 10 gigs, and use whatever is left as your swap.- Some people reccomend a swap that is twice the size of your available system memory, but as the 1525 comes with 2 gigs of memory, a 4 gig swap is a bit wasteful unless you count on using 'hibernate' frequently. (The swap is used to write everything from memory onto the harddrive when you hibernate.) If you go with about 2 gigs and find that it isn't enough, you can use Partition Magic to move some extra space to swap...

Once that's done, let us know, and we can help you get the wireless and display tweaked...

---

### Post by rubik on 2009-07-21
I just got back from a trip myself - hope you had fun!

I followed the psychocats tutorial, gave myself 10 gigs for /home and 2 for swap - though I don't see any noticeable effects yet. Thanks again!

---

### Post by raymondh on 2009-07-21
> **rubik said:**
> I just got back from a trip myself - hope you had fun!

I followed the psychocats tutorial, gave myself 10 gigs for /home and 2 for swap - though I don't see any noticeable effects yet. Thanks again!

welcome back.

The advantage of a /home comes when you have to re-install or upgrade ubuntu.  Your user config settings, data, bookmarks, etc are stored in /home.  Should the time come when you have to do a re-install/upgrade, you just reformat root (/) -ubuntu system files- and retain your old /home.  No need to re-tweak your new set-up by then.

Swap is an overflow of RAM.  On a 4GB RAM set-up, you won't notice it  being used much.  On a 512mb RAM set-up, you'll notice it when you start running resource-intensive apps .. or multi-tasking .. or hibernating.

Going back to your original thread title, you may want to PM forum member *lovinglinux* and ask him to take a look at this thread so that other may benefit as well.

Good Luck.

---

### Post by elliotn on 2009-07-21
Ja I gave 1GiB swap but havent seen it being used. Or felt the benefits,
Btw what if I backup home and restore it when I reinstall

---

### Post by lovinglinux on 2009-07-24
> **raymondhenson said:**
> Going back to your original thread title, you may want to PM forum member *lovinglinux* and ask him to take a look at this thread so that other may benefit as well.

I'm here :)

What's up?

---

### Post by pbotros1234 on 2009-07-24
I had the same problem: intel graphics and slow ubuntu. The reason it is slow is because the current intel graphics drivers for linux are not very good.

Follow this guide, it helped me a lot. [HERE]("http://ubuntuforums.org/showthread.php?t=1130582")

And don't worry about the disclaimer at the top, there are easy uninstall directions at the bottom.

And feel free to ask any questions. :)

---

### Post by Papa-san on 2009-07-25
> **elliotn said:**
> Ja I gave 1GiB swap but havent seen it being used. Or felt the benefits,
Btw what if I backup home and restore it when I reinstall

You won't really notice 'benefits' from having a decent sized swap, so much as you will experience 'pains' if it isn't big enough!
The point of the separate /home partition is that it doesn't need to be restored after a re-install. (However, I agree that a backup is always a good idea!)
EDIT:
The guide mentioned (and linked to) by 'pbotros1234' looks quite comprehensive, and the repair instructions do as well! Start with the 'Safe' setup and decide if that is going to be sufficient for you! If not, you can always move up to the next level, but I chose not to mess with kernels until I did a lot of Ubuntu learning...

---

