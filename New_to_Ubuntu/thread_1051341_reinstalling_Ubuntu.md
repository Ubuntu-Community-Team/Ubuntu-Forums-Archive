---
title: "reinstalling Ubuntu"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-26
I've tried everything I can think of to reinstall Ubuntu.
I've formatted the drive.
I've loaded the CD of Ubuntu.
I've changed the BIOS.
I've pulled cables.
I've tried to load the Vista cd.

All I get is GRUB error 22 on the drive that previouslt had Ubuntu on it.

---

### Post by kansasnoob on 2009-01-26
> **Jack Shankle said:**
> I've tried everything I can think of to reinstall Ubuntu.
I've formatted the drive.
I've loaded the CD of Ubuntu.
I've changed the BIOS.
I've pulled cables.
I've tried to load the Vista cd.

All I get is GRUB error 22 on the drive that previouslt had Ubuntu on it.

You get that error after reinstalling Ubuntu?

What are you able to boot now?

Are you able to boot either Vista or Ubuntu?

Or are you just running the live CD?

---

### Post by kansasnoob on 2009-01-26
Oh, and how did this mess begin?

---

### Post by Jack Shankle on 2009-01-26
I can boot into Vista and XP PRO
Can't reinstall Ubuntu.

I first installed Vista  HD 1(sata) partition 1
Then XP PRO on HD 1 (sata) partition 2
Then Ubuntu on HD2 (whole drive)
It won't Boot so I formatted the drive and now am trying to
reinstall Ubuntu.

---

### Post by bennachie on 2009-01-26
You should be able to access the BIOS during the boot-up sequence (usually by pressing the ESC key or a designated function key), and thereby force the system to boot from the CD drive. That will allow you to reformat the drive containing Ubuntu, but may not resolve your bootloader problems.

If you have one drive containing Windows and a second containing Ubuntu, you may need to preface the reinstallation by using Super Grub Disk (see [www.supergrubdisk.org](www.supergrubdisk.org)) to reset the master boot record so that the system defaults to Windows when booting. The reinstallation will restore the capacity for you to choose which OS you want to boot into.

If you are still experimenting with Ubuntu, and not using it as your production OS, you might want to consider using a Wubi-based installation within Windows rather than using a second disk. This is very handy if everything turns pear-shaped, and the performance hit is really quite modest.

---

### Post by cjv8888 on 2009-01-26
Have a look at this

```
http://users.bigpond.net.au/hermanzone/p15.htm#22
```

I think re-installing Ubuntu will probably fix the problem. If not , post back to see what the error is.

---

### Post by kansasnoob on 2009-01-26
Can you boot the Ubuntu Live CD?

If so I'd love to see screen shots of both drives!

Or at least the output of:

```
sudo fdisk -l
```

---

### Post by Jack Shankle on 2009-01-26
There is no Ubuntu on my Puter at the present time.
I have formatted the hd. It is a separate hd from the
vista and XP PRO hd.
If I change bios to only see the Ubuntu HD and change the cables 
to the first HD, This is what I see on a black screen:
  
Grub loading stage1.5
Grub loading, please wait 
error 22

Nothing can be keyed in at this point.
only thing that works is a reboot.
The Ubuntu cd does nothing.

---

### Post by Muffinabus on 2009-01-26
> **Jack Shankle said:**
> There is no Ubuntu on my Puter at the present time.
I have formatted the hd. It is a separate hd from the
vista and XP PRO hd.
If I change bios to only see the Ubuntu HD and change the cables 
to the first HD, This is what I see on a black screen:
  
Grub loading stage1.5
Grub loading, please wait 
error 22

Nothing can be keyed in at this point.
only thing that works is a reboot.
The Ubuntu cd does nothing.
Tell the bios to boot from the CD, not the hard drive.

---

### Post by Sjeti on 2009-01-26
Do you have any externals or jump drives plugged in?

If I leave my USB drive plugged in I always get a grub error 22, but removing it fixes that.

---

### Post by kansasnoob on 2009-01-26
> **Jack Shankle said:**
> There is no Ubuntu on my Puter at the present time.
I have formatted the hd. It is a separate hd from the
vista and XP PRO hd.
If I change bios to only see the Ubuntu HD and change the cables 
to the first HD, This is what I see on a black screen:
  
Grub loading stage1.5
Grub loading, please wait 
error 22

Nothing can be keyed in at this point.
only thing that works is a reboot.
The Ubuntu cd does nothing.

Well, it sounds to me like your BIOS is not set to load the Live CD first.

---

### Post by Jack Shankle on 2009-01-26
Your so right. In the shuffle The dvd drive got turned off.
My only excuse is the definition of that drive is hard to read. 
Still dumb thought. It's not my first dumb mistake.
Sorry to waste your time.

---

### Post by kansasnoob on 2009-01-26
That's not dumb! I spent nearly 24 hours trying to straighten out what I was sure was a symlink problem when I only needed to install Abiword to read the files I'd created with Abiword!

That was dumb!

---

### Post by Jack Shankle on 2009-01-27
Allmost there, now that I have the DVD BIOS turned on LOL.
This was an attempt at a triple boot scenario.

Here is what's happening now:
I can boot into Vista.
I can boot into XP Pro.
I can boot into Ubuntu.
This is where the fun starts.
It throws up the main window of Ubuntu and the Orange bar goes
about an 1/8 of the way and hangs. Then a black screen comes up with a ton white letters and hangs. If the enter key is hit a Green window comes up with this Message:
  Server Authorization Directory (Daemon/SerAauthDir) is set to /var/lib/gdm but is not owned by user 105 and group 113. Please correct the ownership or GDM configuration and restart GDM.
An OK button doesn't work and Control/Alt/Delete is the only way out.
Thank for any help.
Nothing is ever easy........

---

