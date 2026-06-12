---
title: "[SOLVED] Networking - Last Chance Saloon"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2008-09-30
How do you get an Ubuntu unit to co-exist on a Windows network?

From Ubuntu:
I want to be able to browse the Windows network from within File Browser.  I want to be able to view the various workgroups that exist.  I want to be able to access Windows shares (after providing the correct credentials).

From Windows:
I want to be able to browse to the Ubuntu unit from within Explorer.  I want to be able to view the workgroup that the Ubuntu unit is on in Explorer.  I want to be able to access Ubuntu shares (after providing the correct credentials).

What I cannot do:
Make any changes to the Windows network.  Make any changes to the Windows units.
Ubuntu just has to appear, and operate, as if it were another Windows unit on the network.

What I do not want to do:
Have to remember the IP addresses of various boxes.  These are DHCP assigned and likely to change.

After many attempts I am now confused as to what do do, or if it is even possible to have an Ubuntu box work correctly on a Windows network.  To me, at the moment, it seems not.

Samba - this seems to be a server.  Do I need that in the above scenario?  My Ubuntu unit will be a network client, not a domain controller or anything.
smbfs - do I need that?
smbnetfs - do I need that?
system-config-smaba - do I need that?
swat - do I need that?

Please, someone, **ANYONE**!  Point me in the direction of documentation, a "How to", guide, or *anything* which is valid for Hardy.  I mostly seem to find documentation/tips for Feisty or Gutsy and these never seem to be quite right.

I really am at my wit's end trying to make this work.

I just found this: [http://www.itwire.com/content/view/19728/1162/](http://www.itwire.com/content/view/19728/1162/)
Seems that Hardy is broken.  Anyone know when this bug will be fixed (or how I can find out?)

---

### Post by Another Monkey on 2008-09-30
Yes - it looks like hardy is simply broken that I need to wait for the fix.

More here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)
[http://bugzilla.gnome.org/show_bug.cgi?id=522494](http://bugzilla.gnome.org/show_bug.cgi?id=522494)

---

### Post by Kellemora on 2008-09-30
Hi Monk

I can sympathise with you!  I lost over 3 weeks trying to get a machine up and running on the LAN.............

Using a single computer and two separate hard drives as my experimental set-up, what I have learned so far is, the problem has NOTHING to do with SAMBA or the settings in Samba, if they are right to start with of course.

That is WHY I finally decided to use ONE Computer, not two different computers.  That way all the setting could be identical.

With one hard drive, I have FULL Networking between several machines of all flavors.  XP-Home, XP-MCE, 2 Ubuntu machines, CentOS and Debian.  No problems at all.

OK, lets swap out Mirrored hard drives!  All setting Identical!  With the other hard drive in place, I CAN view the windows boxes, CAN view the Debian machine, CAN view the CentOS machine and CAN view the other Ubuntu machine, but it can't see itself.  NOR can you see the machine now from ANY OTHER COMPUTER.

You can PING to your hearts content and all is OK.  And from the Windows Machines, if you type in the IP address, you can then get to it.  But can't open anything.  Shows the Workgroup, shows the folders, but shows all the folders as Empty.

Now, if you open EITHER of the UBUNTU machines and open the Printers, THERE is the machine you cannot see, plain as the nose on your face, and not only that, you can background print to the machine that can't be seen.

I know there is a Bug of some type in Gnome.  But if it does NOT affect a mirrored hard drive, why should it when you swap another mirrored hard drive in it's place??????  I even experimented with some really old 4 gig Hard Drives too.  Loaded up Ubuntu, did the upgrade and it connected to the network just fine, didn't have to do any tweaking either.

OK, so maybe that's the trick?  Wiped the hard drive, reinstalled Ubuntu and the upgrades, made sure I installed ALL of the packages that are installed and running on the working Ubuntu.  No Dice!  I played with that hard drive for more than 3 days and never got it working either.

So, my conclusing of the matter is, some hard drives prevent the network from working.  Impossible I know!  But I have PROOF!  4 hard drives, each identical to each other, used on a single computer so all the hardware is identical.  Yet only ONE of the hard drives are working on the network, and the one that does work, works perfectly.

I have even copied whole files intact over to the non-working hard drives, such as the entire Samba Folder, All the configuration files, etc.

ONE thing that DID get ONE of the Hard Drives finally working was I DELETED the Shared Folders COMPLETELY, Rebooted and made NEW Folders, then moved the documents back into them.  Suddenly, those shared folders could be seen.  BUT, this only worked on the small 4 gig HD, not the 80 or 200 gig hard drives.  The 4 gig I just keep to try things that might mess things up.  A learning tool so to speak.

On the machine I NEED Ubuntu to work properly, I wiped the disk totally clean, reformatted it in DOS, wiped it again and reformatted it to ext3.  Partitioned it and Installed Ubuntu, Then installed the other OS's, wiped the Ubuntu partition CLEAN and reinstalled Ubuntu again (I do this so it becomes the Bootloader without fiddling with it, and it sees the other distro's).  As they say, third times a charm, my Network is up and running totally glitch free on this machine now too.

Compared the files between the two working hard drives and as expected, they are completely identical.

I've learned I don't even have to get up and go look at a Windows machine to see if it will be working.  If you check from one Ubuntu machine to another, or in the same machine itself, through the network, if the file don't MOUNT on your own Desktop, you won't see it on the Doze machine either.  That saves a lot of leg work in and of itself.

But for me, the solution to the problem was just keep reloading Ubuntu, updating it, then adding the necessary programs for sharing and keep repeating this until it finally starts working on it's own.

Crazy I know, but 3 weeks of trying to FIX IT, DIDN'T!  It only takes a cuople of hours to reload Ubuntu and set it up again.  If it don't work, do it again.  Three times a charm!
ONCE it WAS working.  I moved the hard drive to a different machine, made the necessary changes for the drivers and it kept working.
Moving hard drives to different computers has been MASTERED by CentOS (a Red Hat open distro).  But I prefer Ubuntu, it's the best all around for everything!  Including Support!

TTUL
Gary

---

