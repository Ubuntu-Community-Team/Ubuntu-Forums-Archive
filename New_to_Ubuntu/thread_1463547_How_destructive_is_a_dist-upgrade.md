---
title: "How destructive is a dist-upgrade?"
date: 2010-04-27
forum: New to Ubuntu
---

### Post by Sigma1 on 2010-04-27
Hello,
I suspect this is a naive question. So far I've always installed from Live CD's. This time I'd like to install via dist-upgrade from 8.04 to 10.04. The question is, how much of the tweaking I've done on 8.04 is going to disappear with the upgrade? (By "tweaking", I mean newly installed applications that aren't Synaptics listed for 8.04 (RealPlayer, OpenOffice3 or CodeBlocks for example), as well as one or two hardware tweaks I've made to get suspend to work with my graphics card or to stop unwarranted messages clogging up the log.)
Thanks in advance for any help.

---

### Post by mcduck on 2010-04-27
First, "apt-get dist-upgrade" does not upgrade you to 10.04. ;)

It's just a normal update command, giving you the latest versions of programs available in the your current release version. The difference between "apt-get upgrade" and "apt-get dist-upgrade" is that upgrade can only update existing packages and add new ones (like the Update Manager does) , while dist-upgrade is also able to remove existing packages if required (like updating in Synaptic Package Manager does).

The command to upgrade to next release version is "sudo do-release-upgrade" (CLI) or "gksudo update-manager -d" (GUI).

That being said, upgrading to next release version will not remove any of your existing programs, although there of course can be compatibility issues if one of the programs you have requires a certain version of some package while 10.04 ha a new version of that package. What comes to other tweaks you have made, they will stay intact unless some of the updated packages includes a new version of the configuration file you have tweaked. In those situations you will be offered the option of keeping the old version of that configuration file, but you really should just let it use the new version if you want to make sure things will be working correctly after the upgrade.

(simplified: the upgrade will keep as much of your old programs and configurations intact as possible, but some things might need to be changed to get all the new software working)

---

### Post by wilee-nilee on 2010-04-27
With out a definitive change list and somebody who actually cares, and that knows what to look for, I suspect you wont get answers other then back it up before you do it. You have to remember that nobody is paid here, you can get paid help from Canonical though I believe. Good luck, hope it goes okay for you.

I stand corrected by the above post, but that is common knowledge if you understand the OS basically. Good information though.

---

### Post by mikewhatever on 2010-04-27
Regardless of how destructive or non-destructive dist-upgrade is, you have to backup your files, or better still, clone the system partition and /home. Given these pre-cautions, the level of destructiveness becomes a purely theoretical question, and you are safe to try and experiment.

---

### Post by wilee-nilee on 2010-04-27
It just occurred to me as well that Hardy is grub .97 and ext3 so a net upgrade may be not give you what you would have if you did a fresh install. Grub and the ext4 difference can be dealt with but if it is not part of the upgrade I wouldn't touch it. If the upgrade leaves you with a ext3 and you don't mind, the grub upgrade is easy, if you wanted grub2. There are many people or at least some who can guide you through this if needed.

---

### Post by Sigma1 on 2010-04-27
Thanks to all for these answers. I would have been backing-up my stuff first anyway, though from your replies it looks like many of the changes I've made ought to be preserved.
Re: the last answer. As I understand it, if I go with a distribution upgrade, the system will keep grub and ext3, whereas if I started afresh, the system would install grub .97 and format to ext4...

---

### Post by Sigma1 on 2010-05-02
Here, then, is my answer to my original question:
the upgrade is not too destructive!
I upgraded from 8.04 to 10.04 on an oldish Compaq Presario (with an extra 1Mo of RAM and a second hard disk).
The upgrade went well, if very slowly (servers overloaded or a slow connection). I was given a number of choices along the way, and said yes to all.
All except whether I should replace or keep /boot/grub/menu.lst. I've noticed that replacing this file doesn't work too well on updates, and so normally keep the old one and make the changes manually. This time I kept the old one, and the computer wouldn't reboot. (I should have expected as much, since the old kernels had been removed!) I booted from a LiveCD and editing menu.lst and the computer rebooted.
The only other problem was with flashplugin-nonfree which could neither be reinstalled, nor removed, via synaptic. The answer I found on Google:
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm 
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
I then needed to reinstall a flash plugin for Firefox, of course.
Otherwise the rest of my stuff and other software is completely unaffected. (This includes Crossover Linux and Turboprint software for printers.)
Thanks to all for help.

---

### Post by rannsaicher on 2010-05-02
I upgraded a hardy system and a karmic system  to 10.4 over the weekend.

The karmic upgrade went fine,but removed google-earth.

I have the flashplugin problem to fix tonight on the ex hardy system, and I was also warned about postgres.sql. where the upgrade moved the software to 8.4 from 8.3, but issued a warning about database files not being upgraded.... im going to have to investigate that one.. im not even sure what the dbms is being used for on the machine ( my son perhaps been trying something out?)

Both systems came back after the upgrade and appear stable.

---

### Post by Sigma1 on 2010-05-04
One or two minor problems have cropped up since my last. I'm adding them for the sake of completeness:
1. sbackup doesn't want to back up as before (to an external disk drive); it seems to be advantageously replaced by backintime.
2. The system isn't always shutting down as it should: when I choose shutdown, nothing happens (however many times I try!). Either restarting the xserver with ctrl-alt-bksp (which requires configuring, by the way: it's deactivated by default) or going via the command-line with sudo shutdown 0 -P do the job. I've found nothing significant on the forums to explain this.
Re: the last post by rannsaicher, googleearth is still around after upgrading from Hardy. Did the Karmic > Lucid upgrade actually remove googleearth or render it unuseable?

---

### Post by Sigma1 on 2010-05-22
And one or two extra remarks concerning my last post:
1. I've replaced backintime, which I couldn't get configured as I wanted, by nssbackup, which doesn't appear to be supported, but which does the job sbackup used to do, only better.
2. The shutdown problem is linked to the OOffice quickstarter. Disabling that lets shutdown and reboot options work as they're supposed to do.

---

### Post by gordintoronto on 2010-05-22
Thanks for your comments!

You could mark the thread as "solved" so people know it contains answers, not just questions.

---

### Post by Sigma1 on 2010-05-24
> **gordintoronto said:**
> Thanks for your comments!

You could mark the thread as "solved" so people know it contains answers, not just questions.

Thanks, you're right... I'll do that!

---

