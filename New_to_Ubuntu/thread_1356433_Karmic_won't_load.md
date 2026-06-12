---
title: "Karmic won't load"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by temac on 2009-12-16
I installed karmic from Windoes XP onto a secondary disc drive. for about a month everything was ok (apart from no drivers for Canoscan LIDE 200).
Ubuntu began an update, some of which was unsucccesful When I rebooted the Ubuntu option immediately faulted to



GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB list possible device/file completions.]

sh: grub>


The only command that seems to work is reboot.

I have uninstalled several times, including manually removing references to Ubuntu in the c:\ boot.ini file, checking the registry for references, reformatting the didk on which ubuntu would reside, downloading a new iso file and burning several cds, runscandisk on both disk drives ... I'm running out of ideas. Am I missing somethig obvious? Surely if I remove ubuntu and reinstall from scratch any corrupte files wil be restored?
I read a similar post (**Cannot boot Ubuntu Karmic Koala **[cremebrulee1979]("http://ubuntuforums.org/member.php?u=975652")). THey didn't seem to get anywhere either.

---

### Post by temac on 2009-12-16
Ok I reformatted the hard disk and reinstalled: seems to be ok for now, but I'll have to restore all my settings. I still don't know what happened and I don't want to go through this procedure again. Anyone? Hello?

---

### Post by Ocxic on 2009-12-16
When you updated Ubuntu it prolly update grub at the same time(not uncommon) and it prolly didn't go very well.

---

### Post by marshmallow1304 on 2009-12-16
It didn't help to format the second drive because Grub is stored in the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of the first drive.  In the future, if you want to fix Grub, see [either of the first two posts here]("http://ubuntuforums.org/showthread.php?t=24113").  If you want to scrap Grub and restore the Windows boot loader, see [this]("http://www.neowin.net/forum/lofiversion/index.php/t292614.html").

---

### Post by temac on 2009-12-17
"It didn't help to format the second drive" - So why did it work?

---

### Post by marshmallow1304 on 2009-12-18
> **temac said:**
> "It didn't help to format the second drive" - So why did it work?

I must have missed your second post.  It worked because when you reinstalled, Ubuntu reinstalled Grub.

---

### Post by themusicalduck on 2009-12-18
This happened to me too a few days ago after an update.

For future reference this is the best way to reinstall grub 2 - [https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD]("https://wiki.ubuntu.com/Grub2#Recover Grub 2 via LiveCD")

That fixed it for me.

---

### Post by temac on 2010-01-01
Wellll.... it happened again. this time i started getting fatal panics, which I worked around,  but now it doesn't matter how many times I uninstall Ubuntu, which drive I install it to, using a grub rescue disk,  - I can't get ubuntu to load from my hard drive. It will load from the CD, but I'm very loth to do anything that would compromise my (highly customised) Windoes XP. 

I like Ubuntu, but until I can get this sorted it will never be my main system.

---

### Post by Methuselah on 2010-01-01
Kernel panics really should not be happening randomly like that.
I had a similar issue with a machine and it turned out that one of the memory sticks was bad.
It was strange because while the Karmic kernel hated that other versions would run without too much issue.

If you want to rule this out, boot the live CD and choose the memory test option.
Then let it run until you see that it has completed at least one pass in the 'pass' column.
This might take a while so do it when you can afford not to use your PC for a while.
Hopefully, there will be no errors in the errors list after one pass is complete.

---

### Post by QIII on 2010-01-01
How old is the "secondary disk"?

"It worked for a while, then started going bad, now won't work at all" sounds like how a drive goes bad.

There are tools for checking the health of a drive.  Even a new drive can go bad.  If you handle it just right and smack a head on the platter, you get a bad sector.  If you are lucky, that is the only one.  But it is rarely that nice.  If you are now dragging a head, things get worse and worse.

---

### Post by temac on 2010-01-01
I worked round the fatal panic by choosing the earlier version at boot; .14 instead of .15 as I remember.
I have run chkdsk/f on both hard drives and checked with Drive Health, but no errors found.
Then I marked the newer version for reinstallation, booted, and no Ubuntu. (12 hours ago).
I now know more about grub that I care to, but uninstalling, cleaning out the registry, making sure that wubildr etc had been exorcised from the computer, re-install;
zilch.
Help!

---

### Post by QIII on 2010-01-01
Sorry I can't take the time to explain better.  I'm trying to keep one eye each on a couple of foster kids while my wife is making New Year dinner...  I just don't want you to have the impression you have been left to your own devices.

I'll use some terms that my help you do a search of the forums.  I'm not sure of your level of expertise.

I'm not sure what effect a Wubi install might have on your performance.  Wubi installs in a loop device, which means that from Ubuntu's perspective it is running on its own drive (well, a block device).  So it should be fat dumb and happy.  But I have read posts from frustrated users where they are having problems with Wubi installs.  From Windows' perspective, Ubuntu is just any other thing to be installed/uninstalled.

You could try to simply create a genuine dual-boot system by installing Ubuntu on the secondary drive.  You'd have to be careful not to destroy any important data on that drive.  Back it up and manually create your desired partitions around whatever you want to keep.  I suggest using a separate /home partition because that makes re-installation or installation of a newer version much easier.

If you are unfamiliar with Linux, that will all sound Greek.  If you are familiar, you probably have a good idea what I am saying.

Sorry I can't spend more time!

If you need to, do some forum searching on "dual-boot" "partition" "/home", etc.

If I get a chance, I'll try to check back in tomorrow.  I have a bunch of dinner guests coming over tonight.

---

### Post by temac on 2010-01-01
So that would explain why when I do search -f/vmlinuz/ and /sbin/init in grub they don't come up on hd0 or whatever but on loop0, where the panic seems to be - can't load the drive.

While I'm typing this in Windows I'm listening to my hard drive constantly seeking. When the shop opens on monday I'll take the box in -  I have a very helpful tech who will replace anything that isn't kosher.

Many thanks for your help - I'll let you know how I go on.

---

### Post by abq911 on 2010-01-01
I have also heard lots of reports that Grub 1.97 Beta 4 is conflicting with Wubi. I recommend that next time that you install Ubuntu fully, because Wubi was intended to try out Ubuntu, not as a full install. 
And if you haven't figured out yet, Wubi is the option to install Ubuntu inside Windows.

---

