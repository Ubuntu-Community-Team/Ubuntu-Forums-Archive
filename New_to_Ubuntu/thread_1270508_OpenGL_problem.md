---
title: "OpenGL problem"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by 44tr on 2009-09-19
Ok, the short of it is, when I start to run the program Stellarium, I get an error that says "This computer does not support OpenGL" and several other programs won't work I suspect for the same reason.  I want to know how to fix this.

Info that may help.  I upgraded from Ubuntu 8.10 to 9.04 and I believe that is when my problem(s) started.  I tried re-installing the software that was having problems and things that said OpenGL which I'm pretty sure this computer SHOULD support :-)

The software used to work if nothing else.  Thanks in advance for any assistance!

Chris

---

### Post by mgranet on 2009-09-19
What video card do you have? You might not be running the proprietary graphics drivers, which support 3D/OpenGL.

---

### Post by 44tr on 2009-09-19
I'm using "NVIDIA accelerated graphics driver (version 173) recommended"

and I have an NVIDIA GeForce FX 5600XT (AGP) card.  Celestia doesn't work either.  Thanks for reply

---

### Post by 44tr on 2009-09-19
Incidentally, I opened the NVIDIA server settings app and it generates a message that says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I take it this is not good.

---

### Post by coldfusion1313 on 2009-09-19
I have a Nvidia 7150m integrated chip and I am running driver version 180. Check and see if you can use the newer version.

---

### Post by shae on 2009-09-19
I think that is the right version.  What does

```
cat /etc/X11/xorg.conf
```

give you?

---

### Post by 44tr on 2009-09-19
Umm, just how do I go about doing that?  I thought 173 was the newest version since I haven't gotten any update notifications.

And why would everything work fine with Hardy and quit when I "upgrade"; did I screw up the upgrade?

---

### Post by 44tr on 2009-09-19
Hang on, I get an error creating the "child process" when I try to open a terminal.

---

### Post by 44tr on 2009-09-19
I guess I have to log out and try to log in to the system without using Gnome?

---

### Post by 44tr on 2009-09-19
Eeeeek!  I logged out and tried logging in to a failsafe terminal session and it wouldn't let me.  It just flashed for a bit and sent me back to the login screen.  I'm starting to get nervous.  I've let this go on for a couple months because I've been moving from Florida to Georgia and changing jobs.  I can't remember a lot of details about the upgrade or other hints.

---

### Post by 44tr on 2009-09-19
I can still log in to my normal Ubuntu user interface, and most things like email and firefox and open office still work fine.  What can I do?

Thank you.

---

### Post by shae on 2009-09-19
Try using alt+f2 and typing in xterm.  Then follow my previous instructions.

---

### Post by 44tr on 2009-09-19
> **shae said:**
> Try using alt+f2 and typing in xterm.  Then follow my previous instructions.

I still get an error that says "There was an error creating the child process for this terminal" if I check the Run in Terminal box in the Run dialog box; if I don't check it, nothing at all happens.

:confused:

---

### Post by Soley on 2009-09-19
[http://ubuntuforums.org/showthread.php?t=550260]("http://ubuntuforums.org/showthread.php?t=550260")

Maybe that thread will be of some help.

---

### Post by 44tr on 2009-09-20
> **shae said:**
> I think that is the right version.  What does

```
cat /etc/X11/xorg.conf
```

give you?

OK, I have learned to boot up into recovery mode and get to a root terminal prompt.  I have to post this on a different computer since I don't know how to post here from a root prompt if it is possible.

I ran the above command and the result was a long comment explaining what the file did and no longer did.  Then it had three sections: DEVICE, MONITOR, and SCREEN that looked pretty generic to me:

```
Section "Device"
        Identifier    "Configured Video Device"
End Section

Section "Monitor"
        Identifier    "Configured Monitor"
End Section

Section "Screen"
        Identifier     "Default Screen"
        Monitor        "Configured Monitor"
        Device         "Configured Video Device"
End Section
```

That's it.  What next?  Anybody?

---

### Post by 44tr on 2009-09-20
> **Soley said:**
> [http://ubuntuforums.org/showthread.php?t=550260]("http://ubuntuforums.org/showthread.php?t=550260")

Maybe that thread will be of some help.

Soley, I appreciate the reply, but I THINK that person had a different problem causing his child process error, though it was hard for me to follow.

I would appreciate help on this front as well; do I have (at least) two separate problems or are they probably related?

thanks!

---

### Post by 44tr on 2009-09-20
Anybody around today that can walk me through this headache?  I don't have lot's of time during the week .  Thanks!

---

### Post by 44tr on 2009-09-20
To sum up (and bump up :-), I have an OpenGL error and opening a terminal in Gnome is impossible because of a child process error.  I'll be around all evening if anybody can start me along the path to figuring this out.  I still don't understand the nuts and bolts of Linux well enough to go it alone.  Thanks in advance.

---

### Post by 44tr on 2009-09-21
New info.  Here are the results of my .xsession-errors file.  I can't interpret it, but it may help.

Also included are the contents of the /ect/X11/xorg.conf file (help01.txt).

I took the day off partly to deal with this so please ...  Thanks.

---

### Post by shae on 2009-09-21
Well your xorg.conf file looks like it should at least work at the moment.

You might want to figure out the child process problem because that could be at the root of it all.

Try

```
ls -l /dev/null
ls -l /dev/random
```

This will check to see if you are experiencing the same problem as the other thread.

---

### Post by 44tr on 2009-09-21
Sorry about the delay; I had to run out.  The results of the above commands:

crw-rw-rw- 1 root root 1, 3 Jun  3 00:09 /dev/null
crw-rw-rw- 1 root root 1, 8 Feb 27 2002 /dev/random

I thought this looked fine, at least from what I could get out of the other thread.  Where next?

Chris

---

### Post by shae on 2009-09-21
Yeah that looks fine.  The only think I can think of is to edit your xorg.conf file to look like mine:

```
Section	"Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Option		"nologo"	"True"
EndSection

Section	"Monitor"
	Identifier	"Monitor0"
EndSection

Section	"Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
EndSection

```

Of course back up your current one.

---

### Post by 44tr on 2009-09-21
Having storm issues will try new suggestions soon.

---

### Post by 44tr on 2009-09-21
OK, this day has been ridiculous.

I backed up the xorg.conf file and now I don't know what i can edit the silly file with; I normally use gedit, but that is a gnome application and I can't run that from the root prompt in recovery mode.  What editor do I have access to here?  I did search and the only thing that came up was vi; I don't know how to use vi.

I guess reboot, edit the file and save it as something else, reboot in recovery mode, rename it and change the permissions (to ?); is there not a better way?

---

### Post by 44tr on 2009-09-22
I'm not totally helpless :-)

I installed a text editor (joe) that I could run from the prompt and learned enough to make the needed modifications.  That's the good news.

The bad news is that using the new xorg.conf file stopped the boot and gave me the option of entering ubuntu in low resolution mode.

I switched back; it doesn't appear that this file is the problem.

I remember when I upgraded that it asked me if I wanted to overwrite my current ?? (desktop, configuration, something) or keep it and I chose to keep it since I thought it was just talking about desktop configuration.

Was that a mistake?  Correctable?  Would upgrading to 9.10 help when it becomes available?

Thanks again.

---

### Post by unutbu on 2009-09-22
44tr, after googling to find out about the "creating child process" error, I found a few suggestions but no solid confirmed solution. How hard would it be to backup your personal data and reinstall Jaunty? 

I think something in the upgrade process did not go so well, and perhaps a clean install would solve all your problems. 

You might be able to manuever a bit more comfortably if you boot from a LiveCD.
Then you should be able to open a terminal, and I believe your hard drive partitions should be available to you under the "Places" menu in the gnome panel. (Or maybe also as an icon on your desktop). If not I can suggest terminal commands to mount the partition with your /home folder some place like /mnt.

In any case, perhaps if you can backup your personal files, reinstallation might be the easiest way to get back up and running...

If there is a problem with this idea, tell us about it and perhaps we can suggest a workaround.

---

### Post by 44tr on 2009-09-22
Thanks for the suggestions unutbu.  I was thinking it might come to that, and it is possible, though perhaps painful since I have customized a number of things for both convenience and functionality (and aesthetics :-)

I can back up my documents without too much pain; but is it a good idea just to back up the home directory (all the users) and restore it whole?  could that bring back problems?

What else should I back up?  Will all my cookies for the browser and passwords for the internet sites, etc. disappear?  Any other common files that aren't in the home directory?  It may have to wait for the weekend so suggestions on both what and how to backup and restore most easily are appreciated greatly.  Thanks.

---

### Post by unutbu on 2009-09-22
> but is it a good idea just to back up the home directory (all the users) and restore it whole? could that bring back problems?

That's a very good point.

Problems with Linux come in 2 flavors: those that are user-level problems, and those that are system-wide. The user-level problems are caused by an error in a configuration file in your home directory. The system-wide problems can be caused by any file outside the home directories. 

All user-level problems have one thing in common: If you create a new user, and log in as the new user, then the problem disappears. Once you know that a problem is a user-level problem, you can try to hunt down the misbehaving configuration file in the original home directory, or you can just port your files over to the new user and (eventually) dump the old user. You change user name (given the last time we talked, kind of ironic, huh)?

So before going ahead with the reinstall idea, a relatively simple thing to try might be creating a new user (System>Admin>"Users and Groups") and seeing if the terminal works there. If that works, then we could try to figure out the OpenGL issue.

---

### Post by 44tr on 2009-09-23
That was a really good idea.  I created a new user and I had exactly the same problem with that user, so I apparently have a system wide problem.

Your right, kind of ironic...

I suppose I need to think harder about reinstall; I did remember, though, that I have Windows installed on a virtual box machine in there, so this will really be a pain.  Any suggestions for making it less painful?

Thanks.

---

### Post by unutbu on 2009-09-24
Yes, reinstalling can be time consuming, and although the following ideas won't help 
this time, perhaps they might help in the future:

[list]
[*] Keep your personal data and system config files in a separate /data partition. The Ubuntu installer allows you to set up a separate /data partition if you select "Manual partitioning" (you type in /data as the mount point manually). That way, if/when you reinstall the operating system, you can do so without it deleting your personal data.

You can also save important system configuration files (like those in the /etc directory) in the separate partition too. I use a separate data partition like this:

```
/data1:
  drwxr-xr-x 65 unutbu unutbu  4096 2009-09-23 21:54 unutbu
  drwxr-xr-x  5 root   root    4096 2009-05-09 23:15 etc
  drwx------  2 root   root   16384 2008-12-01 20:30 lost+found
  drwxr-xr-x  2 root   root    4096 2009-08-13 09:38 root
  drwxr-xr-x  3 root   root    4096 2008-12-02 22:32 var

```
I use symlinks to connect the files in /data to their usual spots in the file system.

By isolating data on a separate partition, backing-up becomes simple too:```


sudo rsync -a --delete /data1/ /data3/
```

This copies everything in /data1 to /data3, a similarly-sized partition on a different hard drive.

[*] Keep notes on all software you install so you can follow the notes on how to do it next time. I tend to install packages using the command line so that I can cut-and-paste the terminal session into my notes.

[*] You can save a lot of internet bandwidth/time by backup up packages you've installed as .deb files. There are instructions on how to do that here: [http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

[*] I never do this, but some find it useful to: install Ubuntu, then install extra packages, and then use remastersys to make a custom LiveCD. That way, when you want to reinstall, all your custom packages are installed as well. See [http://www.remastersys.klikit-linux.com/capink.html](http://www.remastersys.klikit-linux.com/capink.html). 
[/list]

Hope this helps.

---

### Post by 44tr on 2009-09-27
That is most helpful.  I couple details are a little fuzzy, so I may inquire about them when I finish preparing for murdering, uh renewing, my system.

Thank you.

---

### Post by 44tr on 2009-10-31
OK, I have finally been able to devote some time to examining my system and prepare to reinstall.  My system is currently a bit complicated, but I intend to simplify.

I have three (3) hard drives:

(hd0, 300G) /dev/sda
sda1 linux swap 2G
sda2 ext3 /     93G
sda3 ext3 /mnt/share_1  93G (contains a virtual box machine with XP installed)
sda4 extended
    sda5  /home    110G

(hd1, 120G)  /dev/sdb
sdb1 ntfs 25G (Win XP OS for dual boot system)
sdb3 ext3 16MB (Grub partition to control dual boot)
sdb2 extended
     sdb5 ntfs 10G (some files I need to save)
     sdb6 ntfs 15G (some files I need to save)
     sdb7 ntfs 30G (some files I need to save)
     sdb8 ntfs 30G (some files I need to save)

(hd2, 80G)  /dev/sdc
sdc1 ext3 75G (this was an NTFS partition I just wiped and reformated with the Ubuntu Partition Editor, intending to use to back up files, but the permissions are access only (root owner) and I still don't have a terminal so it isn't easy. I will eventually pull this drive to put in another computer.)

Now, I am getting rid of XP entirely on hd1 and just need to back up those files on the secondary partition.  I had help setting up the grub partition (see [http://ubuntuforums.org/showthread.php?t=907559&page=9](http://ubuntuforums.org/showthread.php?t=907559&page=9)) and I thought it was a nice idea, but I don't know how to save it and wipe the drive or even if it is worth saving when I will no longer have a dual boot?? still seems nice in case I want to install another distro on a partition for experimenting.  Opinion?

Anyway, since my /home is on it's own partition, and I guess I can find a way to copy my /etc and other files somewhere, does this simplify doing a fresh install??  Advice at this point?  Thanks very, very much.

Chris

---

### Post by 44tr on 2009-11-01
OK, I went ahead and backed up everything I could, blew away the Windows and Ubuntu installations and installed Ubuntu 9.10 fresh.  It works; I'm in the process of going through testing and customizing, but this problem is done.  Thanks to all trying to lend me a hand.

---

