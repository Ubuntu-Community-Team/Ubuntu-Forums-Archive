---
title: "Upgrade to 10.10 stuck at &quot;Configuring grub-pc&quot; section (screenshot)"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-11
The screenshot was actually taken from a seperate computer that I used to VNC into the one that is actually running the upgrade.  It appears the window manager is no longer running, or at least that's what it told me when I try to click the Show Desktop button in the lower left.

The problem I am having is... well, I can't see what the heck that window in the background says because the one up front is in the way and I can't get it to move out of the way.  Stranger still is the fact that the window in the background isn't worthy of it's own tab in the bottom panel, so it's not like I can just click on it and bring it up front.  I'm not sure what it says, what's it's asking, or why the one in the fore ground is hanging off the edge of the screen.  How do I fix this?

Edit:  Well, either I've jumped the gun or cut to the chase or whatever you want to call it.  I decided to just shut the machine off (via the shutdown menu).  WHY??? you ask?  Because I couldn't even type a command into the terminal window. The keyboard (I hadn't noticed until now) didn't appear to be functioning at all. Anyway, the system is now totally hosed (I expected this).  The desktop fails to load.  There's no possible way to get it to somehow pickup where it left off during the upgrade is there?  Perhaps something can be typed into a recovery mode accessed terminal?

---

### Post by Quackers on 2010-10-11
What OSes wre on your system to begin with?
It may be an option to boot from the live cd then follow the details in this thread
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
This will purge and re-install grub to your system. It may pick your system up and it may not. I'm pretty sure the install is toast. 
If that doesn't work there is a program called Testdisk in the repos which some people have found very useful for recovering partitions.
Good luck

---

### Post by solar george on 2010-10-11
I don't think that'll have any luck, even if you recover grub the rest of the system will be in an inconsistant state and may not even be able to run apt or dpkg to even attempt to recover.

---

### Post by MooPi on 2010-10-11
If you can get the system to a console prompt try ```
sudo dpkg --configure -a
```

---

### Post by Nilakka on 2010-10-11
Hi,

I have the same problem, the upgrade process is stuck in phase "Configuring grub-pc" and I can't answer the question about the configuration files because the window is not accessible. I have modified grub boot file (dual boot) but the new default would be fine for time being.

One reason could be that I left my computer unattended when the download began. Now I can run any program with Ubuntu start menu or console but I can't close, move or resize any windows and the upgrade process is stuck. Naturally I can kill programs too, this is how I found what's going on.

I will look forward to any pieces of good advice and leave my computer in this problem state until Tuesday evening EET. Hopefully someone has the problem solved then. :)

Cheers,
Ilkka Kudjoi

Edit: MooPi's suggestion to attempt to configure the packages with dpkg fails because dpkg is locked.

---

### Post by MooPi on 2010-10-11
> MooPi's suggestion to attempt to configure the packages with dpkg fails because dpkg is locked.You could kill the hung dpkg process then restart dpkg --configure -a  ? ```
killall -e dpkg
```

---

### Post by diablo75 on 2010-10-11
> **Quackers said:**
> What OSes wre on your system to begin with?
It may be an option to boot from the live cd then follow the details in this thread
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
This will purge and re-install grub to your system. It may pick your system up and it may not. I'm pretty sure the install is toast. 
If that doesn't work there is a program called Testdisk in the repos which some people have found very useful for recovering partitions.
Good luck

The ONLY OS that was on there was Ubuntu 10.04, which was based on a fresh install I did earlier this year.  It was not an upgrade from 9.10.  Windows has never been on this system.

Grub, so far as I could tell, seems to be working the way it's supposed to as the OS does technically "boot", but the ubuntu splash isn't replaced with the desktop, panels, window manager or anything.  Just a couple error messages about GNOME power settings being screwed up and something else.

I am going to attempt to enter a terminal window and enter the dpkg command mentioned elsewhere in this thread to see if it works.  If not, oh well.  I have to say, I'm quite frankly embarrassed about the fact that I'm not the only one who had this problem, especially when you consider that this was a "normal" install of Ubuntu.  I had it functioning as a print server, an SSH server, a bitorrent client for my cell phone to sent files to, a media server (via PS3MediaServer; based on java), a VNC server, and at one time an apache server but shut it down.

This problem is obviously related to the fact that the window manager had been shut off during the upgrade and not turned back on.  Had it been available, I should have been able to move the windows around each other and address the issue.

---

### Post by diablo75 on 2010-10-11
SUCCESS!!

For anybody else reading this looking for the solution to this kind of problem, here's what I did (starting from the state pictured in the screenshot in the first post).

1.  Click the shutdown button and softly shut the computer down, mid-upgrade.

2.  Hold down the SHIFT key during boot to access the Grub menu and select the second item down in the list (should be the latest version of your kernel with the words "Recovery Mode" in the name).

3.  A menu will appear.  Hit the down arrow until you hit the last item, "Enter root prompt".

4.  Type:

```
sudo dpkg --configure -a
```

This will continue the upgrade starting roughly at where it left off.

For me, I happen to see the little "Info message" box that I couldn't read earlier pop up in CLI blue-screen as pictured in this post.  Adding insult to injury, it would appear the only thing I had to do (if I was able/allowed to do it) would have been to click OK and the upgrade would have continued.  Thank goodness for the terminal.  I think I'll probably do all upgrades exclusively through it from now on.

---

### Post by Matruskan on 2010-10-12
Thank you very much for solving this problem just in time!
xD


PS.: I have a dual-boot on my netbook and was upgrading from Ubuntu Netbook 10.04 to 10.10.

---

### Post by ccrs8 on 2010-10-12
> **diablo75 said:**
> SUCCESS!!

For anybody else reading this looking for the solution to this kind of problem, here's what I did (starting from the state pictured in the screenshot in the first post).

1.  Click the shutdown button and softly shut the computer down, mid-upgrade.

2.  Hold down the SHIFT key during boot to access the Grub menu and select the second item down in the list (should be the latest version of your kernel with the words "Recovery Mode" in the name).

3.  A menu will appear.  Hit the down arrow until you hit the last item, "Enter root prompt".

4.  Type:

```
sudo dpkg --configure -a
```

This will continue the upgrade starting roughly at where it left off.

For me, I happen to see the little "Info message" box that I couldn't read earlier pop up in CLI blue-screen as pictured in this post.  Adding insult to injury, it would appear the only thing I had to do (if I was able/allowed to do it) would have been to click OK and the upgrade would have continued.  Thank goodness for the terminal.  I think I'll probably do all upgrades exclusively through it from now on.

This issue popped up during two upgrades last night.  The first one was on my Dell Mini 9 and while the grub info screen was behind the upgrade progress screen, the OK button was visible to the right of the progress screen and I was able to click it (although I could not read the text of the window).  I didn't think anything of it other than I was surprised by the lack of polish in the process.  I went ahead and upgraded my Dell Optiplex 620, but when the issue appeared again, this time the upgrade progress screen completely hid the "OK" button.  I forced a reboot to see if it would pick up the install but just got a purple screen and an error about GNOME power management.  The computer was up and on the network and able to log in remotely, though, so I wasn't terribly concerned.  I needed to go downstairs so I took my mini 9 with me, ssh'd in to the computer, and ran "sudo dpkg --configure -a" from there.  Piece of cake from there.  I agree that I'll be upgrading from the command line from now on.

---

### Post by QLee on 2010-10-12
In the past we never tried to upgrade X while X was running, perhaps the "old" ways still have some value. The command line is a very powerful tool which remains useful today in those instances where a GUI has failed.

Good catch diablo75!

---

### Post by diablo75 on 2010-10-12
For the record, the PC this occurred on WAS NOT running Compiz.  I have a feeling this makes a difference because I ran a second upgrade on another machine of my own and it didn't have this problem at all (I suspect because Compiz was enabled on the second machine).  Considering how young Compiz is compared to the non-3D window managers that have been tried and true for years before hand, it is kind of startling to see this kind of ironic problem even happen.

---

### Post by QLee on 2010-10-12
I agree.
But, I don't even run compiz, I'm one of those old guys who doesn't have much use for all the cool effects that are necessary these days, ...nor do I have the modern hardware to run them on. I'd guess that more development effort went into making sure that a system like most people are using with fairly modern hardware and all the coolness would upgrade well, after all, there is only so much time available in a six month release cycle.

Still, you correctly accessed the problem and dealt with it appropriately, I just wanted to put in a good word for the command line since a lot of inexperienced users here in ABT don't understand how it can get them out of a problem when no GUI is available. Shame on me for using your thread to make that point.

---

### Post by aetius on 2010-10-12
I also had this problem, and also had Compiz disabled.  I'm a gamer, and had the ATI fglrx drivers installed.  I removed them for the upgrade from 10.04 (fresh install) to 10.10, figuring they might cause a problem.  Once removed, I rebooted into the Ubuntu safe graphics mode, and started the upgrade.

Once stuck at the broken grub-pc dialog, I looked around on the system and checked all the tty's.  The upgrade was apparently running on X display :1 (CRTL+ALT+F9? might have been F8), while there was a single dialog window on X :0 (CTRL+ALT+F8, might have been F7) that said something about restarting, and had an OK button.  I clicked that, but that display then went to a blank screen with a cursor in the upper left hand corner.

I tried starting metacity and compiz from tty0.  Metacity failed with a whole series of pixbuf errors and a lot of other stuff - I couldn't see them all in the console on tty0.  Compiz failed because the system was in safe graphics mode.

I was able to work around the problem with diablo75's workaround, and so the upgrade eventually completed and the system was able to restart into 10.10.  I suspect that this problem could be re-created by attempting an upgrade in safe graphics mode.

---

### Post by djspork on 2011-02-05
i just had the same issue happen to me upgrading from 10.04 to 10.10 but mine got stuck on of all things the ms-ttf fonts ...
trying the solution and we'll see how it goes, seems like it might work

---

