---
title: "Complete reinstall advice"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by orangenick on 2010-10-24
hi all,

wanted to ask for some advice:

I have a WinXP IBM R60 laptop on which I have loaded Ubunto 10.4 as a dual boot setup.  

Unfortunately, the XP installation needs replacing because its got too old and slow.  My problem is that from previous experience I know that the OEM XP installation will format the entire harddisk before loading on XP, irrespective of how it has been partitioned etc... well done IBM!

So, the advice I was looking for was how can I 'backup' the entire linux partition(s), Grub settings etc. so that once I have trashed everything with the windows re-install I can easily rebuild the linux partitions and the grub bootloader as it is now.  I'm not so worried about personal file backups as I have those backed up on my SOHO server.  I'm more interested in the configuration of the machine, partitions, boot loaders and that kind of stuff, or is it easier just to do a fresh linux install?

Please take into account that I know very little about ubuntu, other than it just works.

thanks,

nick

---

### Post by thunk77 on 2010-10-24
Here you go:

[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

Just a friendly reminder that the search function is your friend :)

edit: on second thought, you'd be better off with a clean install from scratch because I realize that the how-to is quite complicated for someone with not as much experience.

What are the important configurations of your machine? Maybe we can take this step-by-step.

---

### Post by swoody on 2010-10-24
The simplest way may be a fresh install of Ubuntu as well. If most everything is default (except for your partitioning scheme), restoring a system from a backup will probably be more hassle than just reinstalling. The Ubuntu installer will setup Grub, allow you to configure your partitions, and take care of setting everything up for you.

Were there any things you have customized that you would like to easily restore? If you have customized certain aspects of the system, backing up those configuration files may be a quick and easy way to get things running again. Otherwise, if you'd like to save all the settings you have setup with your user account, you could either create a backup of your complete /home/<name> directory, or even specific directories which contain the settings you want to keep.

Let us know some more details about anything you'd specifically like to backup and we should be able to get more focused answers for you :)

- Woody

---

### Post by wojox on 2010-10-24
Yo kind of lost me. :confused:

Are you going to reinstall XP or upgrade to Vista, 7? Do you just want Ubuntu Linux souly on the laptop?

---

### Post by psycho5 on 2010-10-24
He's going to use the Dell restoration cd to reinstall XP but that will automate the entire process and restore to factory settings, so he is looking for a way to backup  his ubuntu settings

---

### Post by orangenick on 2010-10-25
Hi, thanks for all the replies...

Psycho5 is right, will re-install XP.  (its an Ibm not a Dell, but yeah...same difference)

thunk : will have to look at your link cos it seems to be related to making a live cd, but I suppose thats not very far from what I want to do.  My partition is 30gb so its not going to fit on a cd, I guess I can use an external harddisk.  

I have done a lot of 'learning' Ubuntu on this laptop and haven't made notes of everything I've had to tweak to get it working.  Much of it has been blindly copying and pasting from forum posts.  While I can't think of anything I can't possibly loose, I wonder if I do a fresh install the wireless, sound, bluetooth etc. will still work.  Perhaps it is possible to backup a directory that would keep any device configuration settings?

The easiest thing for me would be to copy the current installation, let the XP insatll wipe everything and then put the installation back on.  

I'm sure I'm not the first person to be in this position, as almost all laptops come with an OEM version of windows, and they don't seem to care too much about how the disks are when you run the installation... I hoped there was something ready out-of-the-box that might get around it.

So, I'm currently leaning toward the fresh install option, though as a long term solution (I like to reinstall windows at least once a year to keep it 'fresh') I think it might turn out to be a lot of work.

---

