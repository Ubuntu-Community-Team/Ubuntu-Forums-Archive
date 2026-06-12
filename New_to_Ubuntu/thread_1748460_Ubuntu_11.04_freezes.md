---
title: "Ubuntu 11.04 freezes"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Veerdavid on 2011-05-03
Hello everyone!

I recently started using ubuntu and I installed 11.04 on a relatively old computer.
My problem is that, in about 5 minutes after booting in the system freezes. I can only push the power button and wait for the pc to shut down.
Also, in the 5 mins I'm able to do anything, the display is... strange. For example, when I push the right button anywhere the menu apperas but it disappears instantly. It's strange because it's still there, only I can't see it. 
Could this be related to the pc freezing?

Thanks,
Dávid

---

### Post by Rubi1200 on 2011-05-03
Hi and welcome to the forums :-)

Please post the full specifications for the computer, especially RAM and graphics card.

---

### Post by Veerdavid on 2011-05-04
Here it is:

Motherboard: asus P5P800-MX
Power supply: chieftec si-a300p3
Ram: two kingston 256 MB PC3200
HDD: barracuda 7200.7 80Gb
Graphics card: none, I connect my monitor via the VGA integrated on the motherboard
Monitor: sony SDM-S73

If I forgot anything, please tell ((:
[SIZE=1][FONT=Verdana]
[/FONT][/SIZE]

---

### Post by polardude1983 on 2011-05-04
11.04 freezes for me too and 10.10 never did. Usually anytime I leave the pc alone and go somewhere it just freezes. So I don't think its because your pc is old.

---

### Post by Rubi1200 on 2011-05-04
> **Veerdavid said:**
> Here it is:

Motherboard: asus P5P800-MX
Power supply: chieftec si-a300p3
Ram: two kingston 256 MB PC3200
HDD: barracuda 7200.7 80Gb
Graphics card: none, I connect my monitor via the VGA integrated on the motherboard
Monitor: sony SDM-S73

If I forgot anything, please tell ((:
[SIZE=1][FONT=Verdana]
[/FONT][/SIZE]
You need to check whether your system meets the requirements to run Unity:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

I suggest you try using the Classic desktop option at the login screen and see if you still have the same problem.

---

### Post by Veerdavid on 2011-05-04
I have tried using classic and the results are the same :(
Then I switched to classic without effect, that still didn't solve anything.
When I run Ubuntu in safe mode the display is right, but the system still freezes.

---

### Post by matthewtomlinson on 2011-05-30
Yep I am getting this as well and I only use the Classic Desktop.
Seems to be more of a problem running on batteries, and / or wireless ?

No problem with 10.10

:(

---

### Post by KoRnKloWn on 2011-06-05
I also have this problem, I have a Sony Vaio VGN NW125J, 4 GB of RAM, Intel Core 2 Duo at 2.1 GHz, and 128 MB of dedicated video memory, so I KNOW it's not the computer, I can even run KDE without any problems.

What usually happens for me, is it's usually when I have firefox open, and leave my computer for a while, doesn't even have to be that long, just 1 minute can do it. Some times it does it when firefox isn't even open. The only way I know how get out of it is to use Ctrl+Alt+F1, log in, then do sudo reboot

---

### Post by Smooth Operator on 2011-06-05
My 2 Cents
Ubuntu 11.04 is very unstable and you mentioned your Comp is old are you using 32bit version of the OS?..

---

### Post by kervin on 2011-06-08
Same thing and with 10.10 always worked smoothly..

---

### Post by Veerdavid on 2011-06-08
I decided to install 10.10 on the compter and everything works just fine.
I won't mark the thread as solved i case someone have the same problem or someone knows a solution.

---

### Post by Ederico on 2011-06-09
Same problem here, no problems with 10.10.

I don't even know how to find my computer specifications to post them here. I'm considering returning to 10.10, since 11.04 hasn't really improved my experience a big deal (actually, with the freezing problem, quite the contrary). I'd rather wait, maybe some updates will do the trick.

---

### Post by VanR on 2011-06-09
Do as I finally did and install 10.04. I had all kinds of trouble with 11.04 and my computer I bought new in Jan. is well up to specs. I tried 2 different versions of 11.04 over the past 2 days and Software Center was broken on both of them. Not to mention the graphic driver problems. I left all that behind till they get it fixed in the future.
Oh yeah 10.10 is good too. I may upgrade to that eventually.

---

### Post by KoRnKloWn on 2011-06-15
11.04 works well enough for me to stick with it, only minor glitches for me. Plus I really like Unity. And it actually freezes MUCH less after the last update, at least on my computer, it only freezes every couple days now, and it restarts fast, so I don't care right now, however I'm still anxious for when it's completely fixed.

---

### Post by Wray on 2011-06-16
> **KoRnKloWn said:**
> 11.04 works well enough for me to stick with it, only minor glitches for me. Plus I really like Unity. And it actually freezes MUCH less after the last update, at least on my computer, it only freezes every couple days now, and it restarts fast, so I don't care right now, however I'm still anxious for when it's completely fixed.


screen savers cause my machine to freeze.I'm running   11.04

---

### Post by dFlyer on 2011-06-16
> **Wray said:**
> screen savers cause my machine to freeze.I'm running   11.04

I had this problem with both beta 1 and 2 but have not experience it since the final release. Do you have all the update installed?

---

### Post by Wray on 2011-06-17
> **dFlyer said:**
> I had this problem with both beta 1 and 2 but have not experience it since the final release. Do you have all the update installed?


Ummm,  don't know.  How do i find out?

---

### Post by Wray on 2011-06-17
I installed all the upgrades.  Screensaver doesn't hang my system now,
but the screensaver itself just freezes a minute or so after it becomes active...

---

### Post by alexis44 on 2011-06-17
> **Wray said:**
> Ummm,  don't know.  How do i find out?
Go to System at the top of your screen, then Administration, then to Update Manager.  It will generally be in there if there are updates available. :)

---

### Post by jjww on 2011-08-04
I have the same issues. I think this might be Java related as it seems to happen more often for me when I'm running multiple apps that are heavt on Java usage - elipse, netbeans, etc...

---

### Post by shammydog on 2011-08-05
Same issue.  11.04 freezes, mouse moves around but nothing clickable, no keyboard control whatsoever.  Requires hard power off to recover.  Seems to be related to inactivity.  I am going to try disabling power management see if that helps at all.  Love the OS otherwise.  running classic gnome descktop btw.  Unity blows.

---

### Post by bivinsj407 on 2011-08-05
I had the same problem, went back to 10.04 and am very happy with that version....  jim

---

### Post by wildmanne39 on 2011-08-05
Hi, here is a link on freezing it might help.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by ursaminor on 2011-08-06
Just a thought:  [http://lubuntu.net/]("http://lubuntu.net/")

This version is a lightweight version of Ubuntu and Xfce. The latest version is 11.04 and comes in 32 or 64 bit. Good for older computers.

---

### Post by KoRnKloWn on 2011-08-06
I looked through that wiki, and my problem doesn't seem to match any of the examples. Well, sometimes it does, but most of the time it's the type of freeze where I can still move the mouse around but can't click on anything, and it doesn't require a power cycle, all I need to do is  ctrl+alt+F1 and sudo service gdm restart.

And by the way, I don't think Unity sucks, I love Unity, it doesn't require so much customization like Gnome Classic does (I like the customization, but it just eats too much of my time playing with it). Unity is like the Mac OS philosophy, just start it up and use it, no screwing around getting it to look pretty, because it already looks pretty. The only thing I had to do was a few small tweaks with compiz and Ubuntu Tweak, and adding some things to the white list. Personally I'm always exited to see what the next update with Unity is, and I can't wait till they get a logo set for it (from what I understand they're working on coming up with a logo for Unity, separate from the Ubuntu logo).

---

### Post by scandibilly on 2011-08-10
**I'm having the same problem with 11.04 amd64**, and the only thing I can do once it happens is a **hard shutdown**.

I have a **Lenovo y550**, and while I can't post the complete stats it should be more than sufficient for running just about any form of Linux out there, especially such a highly developed one like Ubuntu.  Something of note is that I have an **nVidia GeForce 240m** graphics card.  I'll get to that in a second...

Within the first few minutes after boot (or sooner if I try to open anything), the display stalls -- the cursor can sometimes barely move at first, but what ALWAYS happens is that the display completely freezes.  I've run a memtest, my hard drive health is excellent, and my BIOS doesn't seem to have any problems. Everything appears work fine until I try to use it a little bit.  Less frequently, the screen will stall before the login screen (this doesn't happen often).  Waiting does nothing, and only a hard stop gets things working again ... though only very temporarily after reboot.

I tried installing **Fedora 15** due to the troubles I've had with this problem and found out that **this exact problem exists for some people using Fedora 15**, too.  I can't point to a specific forum for this discussion, but any saavy Google user will be able to find several about it.  Evidently, the nouveau drivers used by Fedora don't work properly with some nVidia cards, and **the proprietary nVidia ones *may* be the cause of/don't help this problem**.  However, it has been proposed that there is **a problem with the most recent linux kernel** -- a kernel shared by the latest releases of both Fedora and Ubuntu.  I had no problems on this laptop with amd64 versions of Ubuntu 9.10 - 10.10.  **Though Fedora is using GNOME 3 and Ubuntu Unity, both are based on GNOME** -- I'm not sure if a recent GNOME package is to blame.  A few people on the Fedora forums (and for the same problem in Fedora) had luck with this problem using their **experimental drivers** while others saw no change.

Installing the proprietary third-party upgrades doesn't help, and I can't get the GUI going long enough to "roll back" the new nVidia drivers to the old one just to see if they will work. If and only if the newest drivers are the known to be the problem and installing a previous version the known solution, I would like to know how to do this from the command line before Unity starts.  I'd also like to vape Unity and use GNOME 2.32 instead -- if I wanted a playskool netbook GUI on Ubuntu I'd get a netbook

I'd appreciate any info on this, and am willing to answer any questions relevant to solving this problem.  Also, I'll post an update to this thread if I solve it on my end or through someone's advice.
____________

**EDIT1:** Under the link posted earlier in this thread ([https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Reporting_GPU_lockup_Bugs]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Reporting_GPU_lockup_Bugs")) I found the following:
> **Problem: Log shows "[mi] EQ overflowing" and X freezes**

This message indicates that the server has noticed that the GPU is locked up.

This is a particularly common failure-mode for the nouveau driver. The nouveau kernel module has minimal GPU hang checking, and a hang will often result in the X driver spinning until the server dies with the EQ overflow. . . . . . Reporter-supplied details of when the freeze occurs are necessary for a useful bug report. 

I think this *may* be what's happening, but I can't (or don't know how to) generate any backtraces or dmesg with the display stalling the way it is.
____________

**EDIT2:** So, after reinstallation the splash screen doesn't even load on boot, and the following was in the list of services started:
> Starting GNOME Display Manager  [OK]
Starting Userspace bootsplash  [OK]
Starting CUPS printing spooler/server  [OK]
**Stopping** Userspace bootsplash  [OK]


  I had to hard stop, reboot, and then hold down the shift key following my Lenovo BIOS splash to open the GRUB kernel options.  Booting with recovery mode, I chose to update packages (though I had chosen the update option at installation and had a installation-confirmed ethernet connection -- evidently it did nothing). Then I attempted to resume with a normal boot.

The "normal boot" turned out to be a shell prompt requiring my login and password. After entering these was the message that 0 packages can be updated and 0 updates are security related, followed by the instructions  *** System restart required *** and some legal boilerplate.  I entered "sudo reboot now" and got the same stall at boot.  The list on the screen shows that "Starting automatic crash report generation" failed, and then further down:
> Starting GNOME Display Manager  [OK]
Starting Userspace bootsplash  [OK]
Starting CUPS printing spooler/server  [OK]
**Stopping** Userspace bootsplash  [OK]

Just as before, in this screen the cursor hangs and commands don't work.
W  T  F?
Hard stop, REBOOTED again into recovery mode, chose the failsafe low graphics mode and got the message: >  ! It seems that you do not have the hardware required to run Unity.  Please choose Ubuntu Classic at the login screen and you will be using the traditional enviroment.  I clicked "close".

(Note: Thanks again, Canonical, for ruining Ubuntu with Unity...)

So, now with Gnome running and while still in failsafe, I can finally use the desktop -- and without a jungle of pretty graphics and fade effects and hidden trees and application name typing obfuscating everything I'm trying to do.  I (now) easily access and click on System > Administration > Login screen and select Ubuntu Classic as my default session.  Close, and then restart.

On restart, GRUB automatically loads the kernel list, and now I'm scratching my head.  I select the Linux 2.6.38-10-generic kernel (NOT the recovery mode) and hit enter.  Nothing.  Just a blinking cursor.  Hard stop. Reboot.

On boot, GRUB loads a purple background followed by the black blinking cursor screen.  Hard stop.  Reboot.

On boot, hold shift and then into GRUB -- I chose "Previous kernels" option, and select 2.6.38-8-generic.  CURSOR SCREEN...but then the cursor disappears.  By now I'm thinking that maybe I lack the Ubuntu Classic gnome dependencies, and it's starting to feel like Linux did 10 years ago.  Hard stop. Reboot.

Shift key. GRUB.  2.6.38-10-generic recovery mode again.  failsafeX.  Reconfigure graphics.  Create new configuration for this hardware.  Done.  Restart X.  Blinking screen.  Back to Recovery Menu.  Resume normal boot. System puts me back into a shell prompt.  I enter <startx> -- screen says, > NVIDIA: could not open the device file /dev/nvidia0 (Input/output error).
(EE) NVIDIA(0):Failed to initialize the NVIDIA GPU at PCI:1:0:0  <...etc.>
(EE) Screen(s) found, but none have a usable configuration.
< and,>
"Fatal server error:  no screens found."
< then, further down >
xinit: giving up
xinit:unable to connect to X server: Connection refused
xinit:server error


&#3232;_&#3232;

Back to shell prompt, <sudo reboot now>, hold shift key, choose recovery kernel, failsafeX.

From here I went into the Synaptic Package Manager and marked all the xserver stuff for reinstallation (yeah, I know that any problems are stuck in the configuration files, but I did it for peace of mind) and checked to make sure I had the latest nVidia drivers (yes), the experimental nouveau driver (yes) and the mark the nv package (since an earlier error flashed by saying it was missing) and install. I check "proposed updates" in the software sources.  I then install/upgrade the linux kernel to 2.6.38.11.26 as well as the xserver Intel driver (which I'll remove next if this doesn't work).  Apply changes.

I then perform an update.  All sorts of stuff thanks to selecting proposed updates in the software sources.  Yes, I know that can lead to some instability because they haven't been tested thoroughly, but I'm desperate and know there may be some solutions in there somewhere and apparently with 11.04 Canonical doesn't believe in testing things thoroughly either.

So yet another restart.  This time, at least the regular kernel gets me to the "Ubuntu 11.04" splash screen before failing.  I see this under the list of starting/stopping:
> 
/dev/sda5: clean, 236/18980864 files, 1240802/75908608 blocks
init: ureadahead-other main process (796) terminated with status 4
init: ureadahead-other main process (806) terminated with status 4
*Starting load fallback graphics devices  [fail]


Hard stop.  Reboot into failsafeX.  Open NVIDIA X Server Settings.  I get a message to run nvidia-xconfig (or something like that) as root because I'm not using the NVIDIA X driver..  When I do that, xorg says there's no driver listed in the file.  So, back in NVIDIA X Server Settings I check the box next to "Include X Display Names in the Config File" whatever that means.  I'm starting not to care anymore.  Back to Synaptic.

I uninstall the nouveau drivers and the xorg intel graphics driver.  I then go to [http://pkgs.org/]("http://pkgs.org/") and download the Ubuntu 11.04 deb's for nvidia-current 280.13 and nvidia-settings 280.13.  Restart.

GRUB loads, Userspace bootsplash stops again. Hard stop. Restart. Shift key. Recovery mode. FailsafeX.  NVIDIA X Server Settings.  See: "!  You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nividia-xconfig' as root), and restart the X server."

BUT THIS TIME INSTEAD OF A HUGE F-U I SEE:

> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
**New X configuration file was written to '/etc/X11/xorg.conf'**

I open the file in gedit and see some nvidia stuff in there.

m9(^_^)b

Schweet.

Restart.

Black screen.  Blinking cursor.

Followed this:  [http://ubuntuforums.org/showthread.php?t=1741754&page=2]("http://ubuntuforums.org/showthread.php?t=1741754&page=2")
Reboot.  Didn't seem to do anything.
Then this: [http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html]("http://www.techdrivein.com/2011/06/howto-fix-ubuntu-1104-wont-boot-after.html")

And FINALLY GOT A GNOME LOGIN SCREEN.  No stalls.  No freezes.  NVIDIA X Server Settings show my card is up and running.  Everything worked!

Restarted computer just to check.  Fail screen.  Screw you Ubuntu.

---

### Post by scandibilly on 2011-08-11
**UPDATE ON SOLUTION:**

Just install Ubuntu 10.04. And start re-learning Windows so you're good-to-go when support ends for 10.04.

---

### Post by james_fried on 2011-09-03
Hi scandibilly,

Have you made any progress on this bug?

My machine seems to be doing similar to yours... I also got the

> ! It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.

I'm going to smash around with my XOrg conf and see if there's a blend that will keep my machine stable. My guess is that something in firefox is causing the crash - it's completely random at the moment.

J

edit: and I'm looking at this massive page too for clues... [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/276518](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/276518)

---

### Post by swapnilps on 2011-09-19
Even I am having the same issue..:(
Especially when I am accessing Internet.. Initially I thought, Its a problem with firefox (as I was facing same issue with previous version of Ubuntu Studio 10.04) That time updating firefox helped me.. Now when I check with Chromium or Firefox n my Ubuntu Studio 11.04, No clues.. why this is happening!:confused:
just for the info: I was using Studio 10.04 as mentioned earlier, then I updated it to 10.10 using update manager; then again I updated it to Studio 11.04.
Here I am attaching three screenshots which might be to the help.

Please please please Advice!!!

---

### Post by hofik on 2011-09-20
I have the same issue. Ubuntu 11.04 freezes on login prompt. ... It doesn't, if I'm connected to the LAN via a cable... so I think the issue is in the Wireless adapter Atheros AR5B95. ... tested further, started on cable, switched to WIFI - it got frozen.... it all works fine on Windows 7. ... Should I try to reinstall 10.10? Any other solurion to similar problem?

---

### Post by centaurusa on 2011-09-20
> **hofik said:**
> I have the same issue. Ubuntu 11.04 freezes on login prompt. ... It doesn't, if I'm connected to the LAN via a cable... so I think the issue is in the Wireless adapter Atheros AR5B95. ... tested further, started on cable, switched to WIFI - it got frozen.... it all works fine on Windows 7. ... Should I try to reinstall 10.10? Any other solurion to similar problem?

[SIZE=2]Your issue appears to be similar to one reported on an [/SIZE][SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]Acer Aspire One 522[/FONT][/COLOR][/SIZE][SIZE=2].  Two solutions were provided, only the second being a true Linux-based solution.  Anyway, it might be worth trying both.  The second is easily reversible by removing the blacklist command and re-running the update command.  Note that the blacklist command, while it might solve the problem using wireless, will disable any wired Internet connection. 

[/SIZE][SIZE=2]Ubuntu 11.04 (including Beta 1) freezes when wireless is connected requiring forced power down.  Web forums ([http://ubuntuforums.org/showthread.php?t=1680348](http://ubuntuforums.org/showthread.php?t=1680348)) provide two solutions:[/SIZE]
[SIZE=2]
[/SIZE]
  [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]Re: Acer Aspire One 522 - Smiles and Frowns[/FONT][/COLOR][/SIZE]
  [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]
[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif](1) You can either boot Win7 before and do a reboot to Linux or do following:[/FONT][/COLOR][/SIZE]
  [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]
[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif](2) Add in sudo gedit /etc/modprobe.d/blacklist.conf this line[/FONT][/COLOR][/SIZE]
  [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]blacklist atl1c[/FONT][/COLOR][/SIZE]
  [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]and, in Terminal, issue the command:[/FONT][/COLOR][/SIZE]
  [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]sudo update-initramfs -u[/FONT][/COLOR][/SIZE]
 [SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif]
[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Liberation Serif, Times New Roman, serif][Note: The forum text suggests that this driver supports the Atheros L1C gigabit ethernet adapter, and blacklisting the driver disables Ethernet and any wired connections &#8211; this is the case and the wired connection is unavailable until the blacklisted driver is restored and the machine is rebooted - but, in normal usage, the wireless connection is the method of choice so that the wired connection isn't needed.]  Both &#8220;solutions&#8221; seem to work.[/FONT][/COLOR][/SIZE]

---

### Post by james_fried on 2011-09-21
For my part - I've given up on this for my work computer. I just couldn't justify the time to hack together something stable on 11.* with unity / the updated drivers / etc. I've rolled back to 10 and everything's stable again.

---

### Post by khurtsiya on 2011-09-28
same problem

on brand new lenovo e520 with 4 gb RAM

freeze after copying about 200 rows column in libreoffice

---

