---
title: "Beige Screen of Death...Kind of..."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by greenjellies on 2009-02-08
Hi, my name is Janet and I've spent about 6 hours trying to install Ubuntu and reinstalled it about 4 times but it still hasn't worked.

**Computer: **
is a HP with a celeron processor, about 712mb of ram, and 40gb pata/ide hard drive.

**Background:**
At first I wanted to dual boot XP and Ubuntu but it notified me that the partitioning would take longer so I decided against it. I had a spare 40 gb hard drive because of a computer with a broken power supply so I decided to use it. (I thought of my first HDD as my back-up in case Ubuntu wouldn't work.) However, beforehand, I made sure that the first hard drive booted in XP and everything worked.

Now, with the second hard drive I booted it using the CD I downloaded and burned, checked the CD for errors, and installed Ubuntu using, under the Partition section, a guided 40gb install (meaning, I assume, there would be only one drive).

**Problem:**
When I rebooted it, it passed the Ubuntu loading screen, I typed in my username and password, and then I got stuck on a solid color beige screen with nothing on it except my cursor. After 20 minutes, still, nothing happened. So I kept reinstalling Ubuntu, hoping that something else would happen. It didn't. I got stuck on the same screen even when I chose "Log in automatically" since it was a home computer.

**Remember the backup plan?**
Well, remember that first HDD that I saved with XP on it? Well, I   decided, since Ubuntu wasn't working, that I was going to revert back. However, when I plugged all the wires into the old hard drive, after passing the HP screen, I was met with a blank black screen with an underscore on the top. Restarting the computer didn't help.

Nothing works!!! Not the first hard drive with XP on it nor Ubuntu. Can anyone help me solve any of the problems? I don't care which OS works. I just need one. My parents will kill me when they find out that I totally messed up the computer.

---

### Post by diablo75 on 2009-02-08
Hopefully, during install, you didn't tell it to do a guided install of the entire disc and accidentally told it to use the then primary drive (which contains(ed?) XP).  Otherwise you might have wiped that drive and installed Ubuntu over top, making no use of the secondary drive you added.  If you lost Windows, the lesson learned here the hard way is to BACKUP before you start messing with partitions or formating hard drives.

As for the problem with Ubuntu:

At the login screen, click on the Options button in the lower right corner and then change the session type to Failsafe GNOME and login as usual.  It'll ask you if you want to continue using that type of session for every login after that, or if you just want to do it just this once.  Do it just this once for now.  If it works, log off, do the same thing again, and this time tell it to use Failsafe GNOME from then on.

---

### Post by greenjellies on 2009-02-08
I guess you didn't understand the whole 2 HDD thing.

Both drives were basically identical. Both had XP, both were 40gb, etc.

I decided that I would keep the first drive as backup and it ran quite normally after I quit the Ubuntu install.

With the second, I did a complete guided install since it only gave me the choice between that and manual. I didn't have to back up that drive since I had the first one...and I  really only needed one drive since I had one computer.

The second drive wouldn't work with Ubuntu, so when I plugged the first back in (my computer will only take one HDD at a time since it's old), it wouldn't work.

---

### Post by occams_beard on 2009-02-08
Just a thought... But while you were removing/installing these drives, you did have the computer OFF didn't you? Silly question, I know... But you'd be surprised how often that happens :)

Did you remove remove the IDE cable from the motherboard, or from the drive? If from the motherboard, might want to check you don't have it plugged into the secondary IDE controller. E.g, hook everything up the way it originally was.

Are you sure the drive is getting power? Does it try to spin up? Sometimes people don't push in the power connector all the way in.

---

### Post by greenjellies on 2009-02-08
Yeah. The computer was off. I even unplugged the A/C adapter. I did  unplug it from the motherboard but I plugged it into the right spot. 

Well, the drive with XP works now... I rebooted it from the partition on the hard drive. I really wanted to get Ubuntu to work though. It seemed pretty awesome (though I've never had any problems with XP, I've never gotten the BSOD) and I wanted to be forced to learn some code (I'm taking a computer science class in school over java).

---

### Post by greenjellies on 2009-02-08
At the login screen I chose Failsafe GNOME but I still get the frozen beige screen.

---

