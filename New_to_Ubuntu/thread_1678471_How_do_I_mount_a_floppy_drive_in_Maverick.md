---
title: "How do I mount a floppy drive in Maverick?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by bwallum on 2011-01-30
Apologies for raising this old issue again but some of us still have occasion to read floppy discs.

I am trying to to get the 'Floppy Drive' in 'Places' to work. This is a tidying exercise in that I can read and write floppy discs using the 'udisks --mount /dev/fd0' command. (Howto attached for details)

I don't understand the code behind the links in 'Places' and would like to learn.

How do I get the 'Floppy Drive' link to work?

---

### Post by Rocket2DMn on 2011-01-30
Floppy drives usually have a line in the fstab file to tell it what options to use when mounting.  Was your floppy drive installed in the machine when you installed Ubuntu?  If you have a floppy disk available, stick it in the drive, then please post the output of the following commands.  If you don't have a disk, post the output anyway:
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```

---

### Post by quadproc on 2011-01-30
> **bwallum said:**
> Apologies for raising this old issue again but some of us still have occasion to read floppy discs.
Me too.
> 
I am trying to to get the 'Floppy Drive' in 'Places' to work. this is a tidying exercise in that I can read and write floppy discs using the 'udisks --mount /dev/fd0' command. (Howto attached for details)
I will start by saying that I have a single floppy drive which is USB connected to this system which is running Ubuntu 10.10.  Because of the nature of the connection, I find that the floppy will be /dev/sdh or /dev/sdi most of time, depending on what else I have plugged into which USB connectors.

I do not see anything in Places regarding a floppy.  When I want to use the floppy I just mount it onto a directory which I created, and then I have to remember to unmount it when done.  Once mounted, the floppy can be accessed through its directory, and that directory can be accessed through Places.  But the floppy drive itself does not show in Places.

Linux can be rather obscure in dealing with floppies.  Part of the problem is that many or most mother boards have some hardware that is recognized as a floppy interface, but that hardware is usually not connected to a physical floppy drive.  Thus, software things which are looking for a floppy will either fail outright or will partially succeed and will often confuse the user.

quadproc

---

### Post by bwallum on 2011-01-30
....info

EDIT
Floppy drive was installed before Ubuntu - system upgraded from Lucid - AMD64 - Problem similar on three other machines running Maverick Desktop i386.

---

### Post by Rocket2DMn on 2011-01-30
Ok, it looks like there is a line in there for the floppy.  What happens if you try to mount from the command line:
```
sudo mount /dev/fd0
```
Does it show at /media/floppy0 ? If you get feedback, please post it here (you can post inline using [noparse]```

```[/noparse] tags rather than using an attachment).

---

### Post by philinux on 2011-01-30
What about fdutils in synaptic?

---

### Post by bwallum on 2011-01-30
sudo mount /dev/fd0 does nothing, tried fdutils. sudo fdmount /dev/fd0 (and tried /media/floppy0) does nothing...or nothing visible on screen and no floppy drive clunking sounds.

Shown under Computer is a device that the system calls Floppy Drive. I can left click and get a menu but when choosing 'Mount' I get the error message as per the attachment. The drive contains a floppy disc and I can access using the code ```
udisks --mount /dev/fd0
``` the 0 is the numeric zero.

---

### Post by bwallum on 2011-01-30
EDIT: Now behaviour of site back to normal for me

---

### Post by Rocket2DMn on 2011-01-30
If you don't get feedback from the mount command, then it should have actually mounted - did you check /media/floppy0 to see if anything was there?  Otherwise it should say that it couldn't find any media.

It looks like you may be suffering from bug [lpbug]441835[/lpbug].

Also, we are aware of ongoing forum issues, they are being worked on.  See this [announcement]("http://ubuntuforums.org/announcement.php?f=326").

---

### Post by coffeecat on 2011-01-30
I can confirm the OP's experience. My self-built desktop has a floppy in it, installed before I installed Maverick. This line was written by the Maverick installer to /etc/fstab:

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```... and a Floppy icon appears in computer:/// . But when I put a floppy in the drive and double-click on the floppy icon I get the error window as in the attached image. Of course there's medium in the drive - the window only pops up after the unmistakable sound of a floppy being read.

There have been a lot of threads about this and I found many words on Launchpad as well, but as far as I can see precious little effective action. I'm reduced to using the code the OP has posted which works for me. Viz:

```
udisks --mount /dev/fd0
```@bwallum, sorry I can't explain the code behind what is meant to happen in the Places menu but clearly doesn't. There is a bug in whichever part of the system is meant to deal with this but it seems no one has fixed it yet.

---

### Post by bwallum on 2011-01-30
Thanks for the forum server status, I have subscribed to the bug but there doesn't appear to be a solution, at least, nobody has found one yet.

What I wanted to try was to put 'udisks --mount /dev/fd0' or something similar behind the 'Floppy Drive' menu item. If that worked then perhaps we would have a solution. It would at least tidy things up and remove the frustration of a non functioning default menu item in 'Places'. I don't know how to put the code behind the menu item, hence this post.

---

### Post by coffeecat on 2011-01-30
> **bwallum said:**
> What I wanted to try was to put 'udisks --mount /dev/fd0' or something similar behind the 'Floppy Drive' menu item. If that worked then perhaps we would have a solution. 

I do have a sort-of solution. It's not as elegant as what you would like, but if you need to access floppies frequently it might help. It involves putting a launcher in the panel.

Right-click on the panel and choose 'Add to Panel. In the new window choose 'Custom Application Launcher' and click on 'Add'. Put whatever you like in the Name and Comment fields and 'udisks --mount /dev/fd0' in the Command field. The icon is somewhat non-specific, so click on that if you want to change it. OK that and you have a launcher which you can click on after you put a floppy in the drive, after which a black floppy icon will appear on the desktop.

If you want to change the icon after adding the launcher simply right-click on the launcher and choose properties.

---

### Post by bwallum on 2011-01-30
You've been reading my HowTo ...although I have to acknowledge I didn't discover it.

EDIT:
Thanks coffecat, you prompted me to revisit the HowTo in #1. I have omitted to mention that the default 'Disk Mounter' should be added to the top panel as well so that it appears when the floppy drive is mounted and gives a convenient method for unmounting (when changing over floppy discs for example)

---

### Post by coffeecat on 2011-01-30
> **bwallum said:**
> You've been reading my HowTo 

I didn't actually - not until you just mentioned it. But there you are - great minds and all that. :P

---

