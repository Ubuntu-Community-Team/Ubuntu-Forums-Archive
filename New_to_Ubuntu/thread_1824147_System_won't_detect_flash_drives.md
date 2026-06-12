---
title: "System won't detect flash drives"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Bearly Able on 2011-08-13
I have been trying to use a flash drive to back up data from a friend's computer, but the system refuses to see it.  I've tried three different drives (two different makes), all of which work on my Ubuntu PC and laptop.  I've tried every USB port in her machine, but without success.  I set up this machine for her some months ago, and used one of these same flash drives to transfer the data from her previous computer without any problems at all.

Anybody got any ideas how to solve this?  Your help will be much appreciated.

---

### Post by amjjawad on 2011-08-13
> **Lesley Lutomski said:**
> I have been trying to use a flash drive to back up data from a friend's computer, but the system refuses to see it.  I've tried three different drives (two different makes), all of which work on my Ubuntu PC and laptop.  I've tried every USB port in her machine, but without success.  I set up this machine for her some months ago, and used one of these same flash drives to transfer the data from her previous computer without any problems at all.

Anybody got any ideas how to solve this?  Your help will be much appreciated.

Have you checked your File Manager?
When you plug your USB to your machine, Open your File Manager and check it there.

---

### Post by Bearly Able on 2011-08-13
It doesn't appear there.

---

### Post by amjjawad on 2011-08-13
> **Lesley Lutomski said:**
> It doesn't appear there.

From Terminal:

```
sudo fdisk -l

```

---

### Post by Bearly Able on 2011-08-13
Thank you.  I'm at home at the moment but I'll try that on Monday and post back.

---

### Post by AgentZ86 on 2011-08-13
Are you trying to backup the data from from another ubuntu machine or a windows machine ?

---

### Post by Bearly Able on 2011-08-13
I want to back up the data on my friend's Xubuntu machine to a Flash drive for safety before I make changes to her system.  i.e. in case I screw up and need to be able to restore things!  I have done it before and don't understand why it doesn't work now.

---

### Post by idoitprone on 2011-08-13
Can I ask? what is the os of her system?

and?

Post the output of
```
sudo fdisk -l
```

I want to see the filesystem type of the usb

---

### Post by Bearly Able on 2011-08-14
> **idoitprone said:**
> Can I ask? what is the os of her system?
 Xubuntu 10.04 (LTS)
and?
> **idoitprone said:**
> 
Post the output of
```
sudo fdisk -l
```

I want to see the filesystem type of the usb

I'm at home at the moment and can't check her machine before tomorrow.

On my Ubuntu system, all the USB drives I've tried on her machine work fine, with the filesystem type showing as msdos.  I used one of the three a few months ago to back-up her files from her previous machine (also Xubuntu 10.04) and transfer them to the new one.  It worked in both machines then and I haven't reformatted it since.

---

### Post by spiky001 on 2011-08-14
Just an option IF you dont get flash drive to work maybe move files by network to your pc.

---

### Post by Bearly Able on 2011-08-14
Thank you.  I'll bear that in mind if I become *really* desperate, because I haven't a clue how to go about it!

---

### Post by Bearly Able on 2011-08-26
This is the first chance I've had to get back to the system, and suddenly it's working again.  Well, sort of - I can only get one user account to "see" the USB drives, but the other account doesn't matter anyway.  I don't know why the problem started, or why it's apparently fixed, so I'm not sure I can mark this "solved".  I suspect I'll be back...!  Thanks to all who replied anyway.

---

### Post by amjjawad on 2011-08-27
> **Lesley Lutomski said:**
> This is the first chance I've had to get back to the system, and suddenly it's working again.  Well, sort of - I can only get one user account to "see" the USB drives, but the other account doesn't matter anyway.  I don't know why the problem started, or why it's apparently fixed, so I'm not sure I can mark this "solved".  I suspect I'll be back...!  Thanks to all who replied anyway.

Just keep us updated and if the problem got fixed all by itself or you managed to fix it, you then can mark this thread as SOLVED. 
Marking this thread as solved doesn't mean you can't edit it later on, it's just a mark for others who is having similar issues to know what are the steps to fix their issue.

Glad it's working now :)

---

### Post by Bearly Able on 2012-03-27
Back again.

The same machine has suddenly given up on my USB drives again, for no apparent reason.  Same scenario - the drives work on my machine, the light on the drive comes on to indicate it's connected and receiving power, but the system doesn't show it.  Doesn't matter which USB port I use.

I've tried ```
sudo fdisk -l
```and all that shows is the hard drive.

---

### Post by idoitprone on 2012-03-27
> **Lesley Lutomski said:**
> Back again.

The same machine has suddenly given up on my USB drives again, for no apparent reason.  Same scenario - the drives work on my machine, the light on the drive comes on to indicate it's connected and receiving power, but the system doesn't show it.  Doesn't matter which USB port I use.

I've tried ```
sudo fdisk -l
```and all that shows is the hard drive.

time to get a little more dirty
plug in the usb 
and post
```
dmesg | tail 
```this will display the kernel logs 


while your at it post
```
lsusb -v
```if the kernel does not see the usb, then I dont know what to do.

one question?
does fdisk -l
show a drive name sdb1?

---

