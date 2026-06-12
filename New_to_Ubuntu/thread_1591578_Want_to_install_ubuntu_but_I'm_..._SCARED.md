---
title: "Want to install ubuntu but I'm ... SCARED"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by baaadmoon on 2010-10-09
First: I really, *really* want to install ubuntu and make it my OS. Tired of Windows/Mac. Many of my MUCH more computer-savvy friends are doing this in my business. I *WANT* ubuntu!

Been reading this forum for couple of days now and I see LOTS of complicated problems w/installation that are WAY above my pay-grade. Trust me, to a average computer-user, like me, this stuff sounds *SCARY*.

My computer: Acer VM498G-Ui5650C/Window 7 Professional/Windows XP, 4GB RAMM, 500GB hard-drive.

I have attached two screen-grabs from my installation attempts. 
Screenshot-1.jpg shows 'Prepare' screen. I clicked 'Specify partitions manually (advanced).
Sceenshot-2.jpg shows the Install window. My hard-drive has four (4) partitions. THIS seems to be the problem.

When I go to System > GParted and try to split sda4 into another partition, I get a warning screen: "It Is Not Possible To Create More Than 4 Primary Partitions" (if yo want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to *remove* a primary partition first.)

This is scaring me.

Another solution came from one of the salesmaen at Frys electronics where I bought the Acer last week. He told me he had ubuntu on his computer on a *separate* hard-drive (b/c OEM hard-drives have so many partitions these days). So just buy a cheap 100GB internal, install it and then install ubuntu on that.

Does that sound like a likely fix to you? Will ubuntu installer give me the "side-by-side" option with a set-up like that?

thanx.

---

### Post by oldfred on 2010-10-09
Welcome to the forums.

It can seem scary at first. And this site is about those who have issues, so you do not see all those who do not have any issues.

You have one of the larger issues where win7 takes 2 partitions and vendors typically add a recovery that is just an image of your drive as purchased and another with misc utilities. The MBR/msdos system only allows 4 primary partitions. When the realized that was  a problem they allowed one primary to be converted to an extended (a container) for many logical. But if you have used all 4 you cannot add an extend without deleting one. Many do not want to delete any. You should use the system to write the backup image but only plan on using it, if you want your system totally erased.

The second hard drive is a good suggestion. You can install Ubuntu on the second drive and not change the windows drive at all. You do have to be careful and use the advanced button to install grub's boot loader to the MBR of the new Ubuntu drive, otherwise it defaults to the first (probably your windows) drive. You can easily reinstall the windows  boot loader if that does happen so it is not the end of the world.

I would suggest having repair CD's (not the system recovery from your drive).

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Your liveCD from Ubuntu will work as a repair CD for Ubuntu. 

I typically also download and create several others just in case. I have gparted, system rescue, parted magic, supergrub etc. I used to write CDs with the most current version but used a lot of CDs. I now just copy them to a multi- bootable USB key.

Some examples:
Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Dual boot with two drives, screens with Maverick have changed somewhat but the procedure is the same:
Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png]("http://members.iinet.net.au/%7Eherman546/p24/022f.png")
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by Gone fishing on 2010-10-09
It's right you can't have more primary partitions. 

You could back up whats on the Windows partitions then delete one of them the install Ubuntu to an extended partition.

However, it would be less scary to buy another hard drive and install to that. If you just install it will put grub on the mbr of the first hard drive - but that OK you will then be able to choose which OS to boot.

The second HD is a good option.

---

### Post by skyjacker on 2010-10-09
If you are really sick of M$ Windows, AND you dont't have any programs that ubuntu can't replace, why not install ubuntu on your hard drive as the ONLY operating system... Make a / partition of 8-10 gb, and assign the rest to /home. You can use a live CD for a while to see if you can get along with ubuntu.  After you install, you will be able to use the $$ you have spent on M$ Windows software on some nice meals.
GOOD LUCK

---

### Post by cpmman on 2010-10-09
This is what I did on my Compaq CQ61 for dual/multi boot:-

1. Do your cleanup and defrag using Windows disc utilities.
2. Create your recovery discs using Windows disc utilities.
3. Delete the recovery partition using Windows disc utilities.
4. Shrink your Windows partition to size as required using Windows disc utilities.
5. Load Ubuntu cd live disc.
6. Manually partition unused space as extended( I did 1. / {root} 2. /home and 3. linux swap {1.5 times your memory})
7. If you intend to have more than one Ubuntu release (or other distro) leave some unclaimed space for it/them.
8. After installation and reboot - reboot again into Windows to allow it to chkdsk etc. if it needs to.
9. Boot into Ubuntu and do an update (sudo apt-get update followed by apt-get upgrade or on the desktop gui 'System - Synaptic Package Manager - Mark all Upgrades').

Worked for me.  I also have a USB external disc on which I keep other distros - but it could be for Ubuntu if you do not want to do the single disc dual/multi-boot (in which case start at step 5. specifying sd{x} where x = b or whatever your clean disc is).

This is all recoverable if needed/wanted.

---

### Post by qyot27 on 2010-10-09
What would I suggest if you are absolutely paranoid and worry about how to make Windows and Ubuntu coexist on such a setup, and don't want to mess with the boot record or a second hard drive, is to use VirtualBox:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

With that, you can install Ubuntu to a virtual hard drive that doesn't touch any of Windows' underlying components.  With the listed specs for the model of computer you have (Core i5, 4 GB of RAM), performance shouldn't be an issue at all*, although you would definitely get better performance out of a dedicated install.  The same applies for Wubi-based installs, which use Windows' boot loader and encapsulate Ubuntu as a file on your NTFS partition (and therefore can be installed and uninstalled from within Windows), but otherwise act as a regular install of Ubuntu would.

*I should preface this by saying running a VBox install of Ubuntu on my parents' Intel iMac is probably still 5x faster (or more) than my typical computer running it natively, and that iMac is from 2006 - albeit recently updated to Snow Leopard.  The setup you mention could probably run circles around that iMac's performance, so I wouldn't worry about it too much.  I would still recommend doing a dedicated install once you feel more confident, though.

---

### Post by Zill on 2010-10-09
> **skyjacker said:**
> If you are really sick of M$ Windows, AND you dont't have any programs that ubuntu can't replace, why not install ubuntu on your hard drive as the ONLY operating system...
Good advice.

Unless you actually *need* Windows for some specific application then you would, IMHO, be far better off without it!  Windows tends to be a better OS for "games" but for "useful" applications Linux equivalents are often as good or better.

Linux-only here for around five years and loving it!

---

### Post by anewguy on 2010-10-09
Normally I don't recommend just blowing away what you already have, since (1) you are leary of Ubuntu and (2) you need something to fall back on for now.

If you want to make this a less scary idea, I would start with some basics first:

- get the complete list of the "internals" of your PC - what chipset the motherboard uses, what video adapter it is using, if wireless is present then also the maker and model of the it as well.

- research the forum, and be sure to ask plenty of questions - that' why we're all here - to see if there are any known problems with Ubuntu and your hardware.  See if any special drivers are needed, and if so, try to get them first and print off instructions.  If there are any special boot instructions (you may need to specify a parameter at boot time to work around video, depending on what you have) be sure to print those off.  This may all seem a little daunting, but believe me it's pretty easy, and doing your homework first in this regards will pay back when you actually start installing and want to use Ubuntu.

- download and burn the LiveCD of Ubuntu.  Boot it, play with it a while, see if you like it.  Somethings, in particular wireless, may not work with the LiveCD but don't worry - as long as you did your homework as I recommended you will know how to fix that when you install.

Okay, so now you're past all of that and really do want to install Ubuntu.  While you may think you want Ubuntu only, I would seriously recommend leaving Windows installed for now - you can always delete it later.  Instead, this is one instance where I do agree that getting a second hard drive would be best - it will make your life simpler for now because you can bypass any partition related issues with your Windows install, it keeps Ubuntu safely tucked away on its' own disk (this might help you feel a little more comfortable - knowing Windows is still there and untouched in case you have some sort of problem with Ubuntu).

Do follow everyone's advice and watch carefully when doing the install so you are sure to install grub (what is used for booting Ubuntu) on that 2nd disk as well.  In this way, you can still just boot your Windows as normal, and when you want to boot Ubuntu just change the boot sequence in the BIOS to use the 2nd drive first.

So, you've been using Ubuntu now for a while at this point, and you decide you'd like to make it a little easier to boot, but you want to keep Windows around also.  Post back when you are ready and we can help you install grub (the boot manager) so that you get a menu to select Ubuntu or Windows right at boot (so-called "dual boot").

If/when you get to a point you want to go totally Ubuntu and don't want Windows anymore, post back and we can help there as well.

So, what's the point of all this?

[LIST=1]
[*]try Ubuntu with the LiveCD to see if you want to try it
[*]add a 2nd drive and install Ubuntu only to it, leaving Windows alone and always available to you to fall back on
[*]when you've reached a more comfortable level, we can show you how to add a menu at boot time to select either Windows or Ubuntu
[*]when you are ready, we can help you get rid of Windows altogether.
[/LIST]

These set of steps will hopefully take some of the scary away and let you try things one step at a time until you are comfortable enough to move on to the next step.  It also has you do some homework first before you install so you can be prepared for any potential problems that you can be aware of up front.

Most of all, remember we are here to help, and ask us anything you feel uncomfortable about - no question is "stupid", no question is "below us".  We've all been there, and we just try our best to return the help. (not to mention you should see some of the questions I still ask!).

Dave ;)

---

### Post by baaadmoon on 2010-10-09
I picked up a 2nd internal hard drive for cheaps and have installed. NOW ...

What-the-heck is "Grub"? Do I Google 'Download Grub' and then just download it and install it from Windows with a nice & easy *.exe file? That would be nice.  Then, when I start my computer, a nice BIOS screen will ask me:

"Do you want to boot from the Hitachi (Windows OEM) hard-drive?

"Or, do you want to boot from Seagate hard-drive (ubuntu)?

I mean, could it be THAT simple? Please? Pretty please?

thanx

---

### Post by 23dornot23d on 2010-10-09
It can be that simple .... holding down F12 on mine gives me that MENU asking

**Which of the Disks to boot from at start up** ..... [COLOR=Blue]

( Its a BIOS option usually .... thats if its not already turned on .... watch your screen carefully at boot up its sometimes on the bottom line of the screen )[/COLOR]

---

### Post by baaadmoon on 2010-10-09
>
The second hard drive is a good suggestion. You can install Ubuntu on the second drive and not change the windows drive at all. 
>

Have installed 2nd drive. This is exactly what I want to do, But ...

>
You do have to be careful and use the advanced button to install grub's boot loader to the MBR of the new Ubuntu drive, otherwise it defaults to the first (probably your windows) drive. 
>

OK, I have NO idea where "the advanced button" actually IS. Is it on the Install Window? In ubuntu? Or on the BIOS Menu? Where?

And once I find this "advanced button", what's a "grub's boot loader"? Where is the "MBR"? I have NO IDEA what these things are. Do I find these things on the BIOS menus somewhere? Can U be any more specific?

>
You can easily reinstall the windows boot loader if that does happen so it is not the end of the world.
>

Uhhhhh ... that sounds pretty "end of the world" to me. If I somehow delete "the windows boot loader" it sounds like an expensive trip to the repair window at Fry's (where I bought this computer LAST WEEK) and a LONG wait and a 'Warranty Killer' and all sorts of bad stuff.

---

### Post by MattBD on 2010-10-09
+1 for VirtualBox - it's a great way of testing the water and getting used to the system without having to deal with any hardware problems. By installing Ubuntu in Virtualbox you can go beyond the limits you'd normally place on yourself without risking trashing your existing installed operating system. Effectively it'll be like installing it to a blank machine and you won't have to worry about the bootloader. Also, it'll let you boot straight off an ISO image - no need to burn a new CD.

GRUB is the Linux bootloader - it will give you a list of the installed operating systems and let you choose one to boot. If you try installing Ubuntu in Virtualbox (or anywhere else, for that matter) you'll get to see it when you boot up the first time.

You haven't mentioned what version you want to install - as Maverick Meerkat is released tomorrow, it would probably make sense to install that in preference to Lucid.

---

### Post by anewguy on 2010-10-09
Grub is one of the boot loaders for Linux, used by Ubuntu.  Where right now there is a little "data" at the front end of your hard disk that says to go to disk "x" and start loading Windows, grub takes its' place in Linux.  What some of us are recommending is that you leave your current disk as-is, so you feel comfortable knowing you always have it to fall back on.  With that in mind, the installation process for Ubuntu will load Grub, the boot loader, to one of your disks - usually the first, which in your case would change the way you currently do things (it would give you a boot menu, and if Ubuntu were ever lost, you would have to do some things first before you could just boot Windows again).  So, what we are recommending is that when you go through the installation process for Ubuntu, when it gets to partitioning, etc., choose "Advanced" and be sure to tell it to put grug on your new disk, not your existing one.

Once that has completed you will have the following:

- an unchanged Windows disk you can boot from just as before

- a new disk with Ubuntu installed and the Ubuntu's boot manager (grub) installed to it

Obviously, to boot Windows you would change nothing.

To boot Ubuntu, you would need to change the boot order in the BIOS (try the F12 thing at the point your hardware is initializing, before it starts loading Windows, as this seems to be more and more common).  Changing the boot order would tell your PC that when it boots look for a bootable (e.g., has a boot loader record - MBR) disk to look at your second disk with ubuntu installed first.  This should result in Ubuntu booting.

After you are comfortable with Ubuntu it is then a simple matter to give you the automatic boot menu where you choose between Windows and Ubuntu - we can even do this without changing your original disk if we have you just boot from your new disk all the time instead.

The boot menu option could be installed right from the start, but since you are a little leary, some of us thought it best not to touch what you currently have at all for the time being, and still give you the ability to run Ubuntu.

Personally, since you are a little leary, I would stay away from VirtualBox or any other virtual machine at this time.  Not that they aren't great - I've used them alot, usually in the opposite manner, running either another Linux distribution or Windows from within Ubuntu.  But for simplicities sake, and to leave your current existing installation exactly as-is for your peace of mind, some of us are recommending the options I have explained above.


Also - don't worry about accidentally deleting the Windows MBR (Master Boot Record - the litttle bit of "data" I explained earlier that tells your PC what to load from your disk).  Deleting it isn't the best idea, however it can be recovered.  It just won't be the prettiest thing in the world to have to do, and since you are pretty much a novice, we want to avoid that.


Dave ;)

---

### Post by baaadmoon on 2010-10-09
OK. I've  booted ubuntu from the ISO CD. I'm at the 'Install' Window, have set up The Clock, The Keyboard. The 'Prepare Disk Space' window is asking, "Where do yoiu want to put ubuntu 10.04.1 LTS? 
"Erase and use the entire disk" is checked. I'm leaving it checked. I changed the partitioned Windows disk (Hitachi) to the new Seagate disk (empty) in the pull-down menu. And ... clicked ... Install.

BTW, I saw the 'Advanced' button & the boot-loader. Not going to install boot-loader on my main Hitachi (Windows) Drive b/c I'm just basically too chicken-sh*t to do it. I'm afraid.  I'll just figure out some way to boot ubuntu manually (f12 / BIOS). Gotta say, I think, for the multi-partitioned OEM new computers these days, the 2nd drive is the answer.

As I type this ubuntu is 89% loaded. 

I can't wait to play around w/ubuntu.

---

### Post by Quackers on 2010-10-09
Did it reboot ok?

---

### Post by GabrielYYZ on 2010-10-09
i hope you like Ubuntu, i'm a new user (on monday, it'll be a week :P) and i'm head over heels with it. i also hope that your first install goes ok, 'cause even though fixing problems on Ubuntu is pretty simple compared to Windows (at least for me) the "ahh new O/S!!!" shock can be frightening.

my first install went wrong, i have 2 hard drives too and i messed up installing the O/S in 1 drive and the grub in the other drive... :(  what i did was just use ubuntu from the live CD, formatted the 2nd drive that had the grub and reinstalled it on the main HD while carefully paying attention to the options, i found my mistake and i fixed it. 

so yeah, good luck and i hope all goes well. Ubuntu truly is a great O/S.

---

### Post by buddhaPIMP on 2010-10-09
NObody's mentioned this and it's currently what i'm using is a Ubuntu installer called Wubi where you can install Ubuntu as a windows program and delete it no problems if you don't like it or screw it up when toying with it while learning your way around. It sets up as a dual-boot, the only problem i've heard its a little slower than an ISO install and the max allocated size is 30Gigs but a great start for beginners (or pussies) just kidding bro HAH.

---

### Post by Jetso on 2010-10-09
I'm new to Ubuntu, and I'm loving it, so I hope that you do to! I've only used it for about 2 weeks, and you'll be glad to know, that if you EVER have a problem, someone on these forums will know how to fix it. That is one of the great things about Ubuntu, is its support. I was scared at first too, but now I love it!

Have fun with Ubuntu!!!!

---

### Post by 5hadow5un on 2010-10-09
I just installed Ubuntu on my laptop this morning and am rather loving it.  I still have Win XP Prof on the first partition but as soon as I can download 10.10, I will banish Windows to the formless void from my machine.  Even if I have some problems with Meerkat, I still have two backup OSes, 10.04 and Lucid Puppy.  Might as well dive in as I already have my feet wet.:P

---

### Post by PatrickMoore on 2010-10-09
hey man take the plunge, I know it seems scary but in the end it is definately worth it. I use both windows and linux and find myself flirting more and more with the idea of just wiping windows off my computer. keep in mind that there are thousands or fine people on these forums that are willing to help make sure you have a healthy system. good luck

---

### Post by 5hadow5un on 2010-10-09
In truth, I am rather surprised at how well Lucid Lynx runs on my laptop:
Dell Latitude D600
Pentium M 1.5 GHz
1 GB DDR
60 GB HD

I keep finding myself moving the pointer to the upper right corners of windows to close/minimize/maximize...old habit,LOL.

---

### Post by GabrielYYZ on 2010-10-10
> **5hadow5un said:**
> In truth, I am rather surprised at how well Lucid Lynx runs on my laptop:
Dell Latitude D600
Pentium M 1.5 GHz
1 GB DDR
60 GB HD

I keep finding myself moving the pointer to the upper right corners of windows to close/minimize/maximize...old habit,LOL.

you could always get ubuntu tweak and switch them back to the upper right :P

---

### Post by anewguy on 2010-10-10
Nothing personal against the wubi installation method, but sometimes it generates problems that are either non-existent or easy to fix if a true install.

regarding not putting grub anywhere - did that really work, and were you able to boot?  I really didn't think it was possible to boot without grub (or one of the other boot managers, like LILO).  When you were at the advanced tab and saw where to install grub, you should have asked it to install to your new drive.  This would not have changed your Windows disk at all.

Besides the ease of nerves for you, part of the reason for putting grub on your new disk was so that moving to a dual boot menu would be easy - I think the menu will already be there when you boot from your new drive as long as you installed grub there!

Let us know if you were able to boot, then we may have a couple of questions for you.

Dave ;)

---

### Post by 5hadow5un on 2010-10-10
Yes, I suppose could move them to the upper right corner...I think I will keep them where they are though.  I have no problem with "deprogramming" myself.  New OS, new way of doing things...of course I am a little reckless, throwing myself into the "Linuxverse" with little knowledge of it, but by doing so I am forced to learn and learn fast.  Works for me anyway...or it had better, otherwise I will have a somewhat oversized overengineered paperweight/ doorstop.

---

### Post by mikodo on 2010-10-10
> **5hadow5un said:**
> In truth, I am rather surprised at how well Lucid Lynx runs on my laptop:
Dell Latitude D600
Pentium M 1.5 GHz
1 GB DDR
60 GB HD

I keep finding myself moving the pointer to the upper right corners of windows to close/minimize/maximize...old habit,LOL.

Or go to System -> Preferences -> Appearance  -> Customize -> and choose one of the looks that has the buttons on the right, like Clearlooks Classic and click install!

Just read your last post, keep it as it is of course it you want, I like the old way as I outlined.   :P

Mike

---

