---
title: "Karmic DVD Drive Eject Issues"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Corpr8 on 2009-11-25
My first post - (please be gentle with me).

I upgraded to Karmic and generally love it - however, when I rip a DVD/CD (purely for backup purposes you understand) - I then find that I cannot eject the disk afterwards!

How weird.

Currently I am doing the following in a terminal (or by hitting F4 when navigated to Root/media):

eject discname

which returns an error: unount of '/media/discname' failed

However - when I hit the eject button on the front of the drive afterwards, it pops out!

Also - I don't have to remount the disc afterwards - I can just throw another disc in and continue.

Anybody know of a fix for this weird behaviour?

P.

---

### Post by overdrank on 2009-11-25
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by Mr. Devil on 2009-11-25
What if you unmount it before the [COLOR=RoyalBlue]eject [/COLOR]command ?

```
umount discname && eject discname

```

---

### Post by Corpr8 on 2009-11-25
Yup - that does work - however that's approximately 10* the amout of typing and of course I have to remount the DVD afterwards.

So ultimately not a good fix.

Also - In Jaunty, I could just hit eject! So this really is a step backwards.

---

### Post by ukripper on 2009-11-25
if you running a burning program using sudo to burn cd/dvd it may not unmount using just umount command, you may need sudo infront. It all comes down to how you running your program and what permissions you have to umount the dvd. what program are you using?

---

### Post by Corpr8 on 2009-11-25
HI - Thanks for the response...

I am using K9 - but not as SU!

I think this may be a bug (as I have seen this on 2 installs now) - I think it may be something to do with autoplay in the O/S. (I noticed on a previous install that before I set a default action for inserting a DVD, it had a select action box - if you used the eject on that box, it ejected fine even after a rip via K9!)

---

### Post by Hero of Time on 2009-11-25
Do you have an icon on your desktop with the CD drive? If so, right click it and select unmount or eject. That should eject the drive too, using HAL. Mounting should also be done by HAL.

---

### Post by soni1770 on 2009-11-25
if you just type 

eject

that works to


don't forget,

if you hit the up arrow when in the ternimal it will show the last command typed,

so you only have to type eject 1 time, 
then it's just   (up arrow) enter

lots less typing

---

### Post by Corpr8 on 2009-11-25
Ok - So ref the last 2 posts...

1) Ejecting via the GUI - doesn't work (it's greyed out! - in use by something)

2) Just typing eject doesn't work unless I use the DISC name! (Hence I have to type lots each time)

P.S. Thanks for your responses...

---

### Post by stinger30au on 2009-11-25
this seems to be a common bug in 9.10

its got some really wierd faults 9.10 with dvd drives and ripping

also some wierd stuff with scanning as well

i have down graded all my pc's except one to 9.04 just to see if 9.10 gets fixxed or not

so far im still having best results with 9.04

---

### Post by Corpr8 on 2009-11-25
Thanks for the feedback.

I managed to get my scanner working in 9.10 no problems (except for the user in the scanner group and running sane-find-scanner then entering the address in the end of: /etc/sane.d/epson2.conf)

So my only real bugbear is the extra typing to eject a CD Rom lol...

---

### Post by Hero of Time on 2009-11-25
I use Xfce4, so not really sure about the rest, but what if you install xfce4-volstatus-icon and run that? It should create a tray icon when a removable drive is mounted (USB, CD) and allows you to remove them. Maybe Gnome has the same thing?

---

### Post by Corpr8 on 2009-11-25
Hi Hero - Thanks for  the response - I am using KDE which does have the same kind of thing - it just doesn't work :-)

---

### Post by Grenage on 2009-11-25
As a temporary work-around, perhaps a script with a desktop symlink?

---

### Post by Corpr8 on 2009-11-25
Aha - good idea. But obviously this would entail being able to pickup the DVD name dynamically...

Any idea's how I could achieve this?

---

### Post by Hero of Time on 2009-11-25
Why not simply **eject /dev/sr0**? Or use it with sudo, and modify the sudoers file (with visudo) to not ask for a password when using eject?

---

### Post by Corpr8 on 2009-11-25
Hmm not sure about the sudoers file - doesn't this kind of bust Ubuntu's security model wide open? (Or certainly leave the operating system open to abuse from idiots like me)

---

### Post by Grenage on 2009-11-26
You can specify what a user is allowed to do in the sudoers file, giving the user full root access is only one option.

---

### Post by Corpr8 on 2009-11-26
:P:P:P !!!Solution!!!! :P:P:P

Firstly - Hi All and thanks for your help

Ok - So it turns out that if I run:

eject /dev/sr0 (throws an error telling me it can't unmount a disc: yeah right!)
 
then 

eject /dev/sr0

the cd rom ejects...


so now, it's a simple case of writing a .sh file as follows:

#!/bin/sh
eject /dev/sr0
eject /dev/sr0

Then building an application launcher on the desktop (I use KDE so I need to change the display mode on the desktop to folder view then create an application launcher)

App launcher application - explore to sh script then add sh to the front of the path - e.g. sh /home/paul/myscript.sh 
path= /home/paul

And hey presto it all works!!!

1 click eject of a DVD :-)

---

### Post by wjamoore on 2009-12-28
err... congrats on your solution, but that's not really a software solution for the OS

I have discovered that since I have a 2nd user (my wife) that when i try to eject DVD ROM it tells me that only she has permission to unmount the device!!

So I switch user and eject.. no problem, then back to my logon and continue

So for me it's a fundamental bug.  i checked user permissions and we both have the same..

So what can I do for that?

cheers

AM

---

### Post by mörgæs on 2009-12-28
Yes, Ubuntu 9.10 has some confirmed bugs regarding the CD/DVD-drive:

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441338](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441338)
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397734](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397734)

---

### Post by wjamoore on 2009-12-28
and a follow up to this:

It's related to the user who first logs on to the system

I also discovered that if my wife logs on first I cannot see network connections any more in the notification area.

I just tested by restarting and logging in first as me...  DVD ROM now works normally... as does network icon.

Of course now my wife can't unmount a DVD without switching user to me!  nor can she see the network icon

This is a bit of a mess..

I expect if you are the only user on the computer that some things are defaulting to root.  Only a hunch

---

### Post by mc4man on 2009-12-28
As far as the dvd deal

Whichever user first mounts the dvd must at least unmount it before logging out or switching users, then the other user is free to mount and or eject the dvd.
(root can always unmount/eject

That  seems logical when the first user to mount the volume is still logged in (in switch user scenario

Now when the first user to mount the dvd logs out without unmounting the dvd that does seem to be a bit 'off', the mount is no longer 'active' for that user (no longer logged in

There was/is an authorization setting to allow unmounting of filesystems mounted by others, it doesn't seem to apply in this case though

Best bet is to have the user that first mounts the dvd umount it before logging out or switching users

---

