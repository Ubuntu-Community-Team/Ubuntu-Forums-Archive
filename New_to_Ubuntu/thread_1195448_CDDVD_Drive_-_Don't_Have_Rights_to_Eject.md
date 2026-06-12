---
title: "CD/DVD Drive - Don't Have Rights to Eject"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Ceiling Fan Man on 2009-06-23
I made the complete switch from Windows to Ubuntu about 4 months or so ago, and have had no complaints thus far of any importance (Just minor things that aren't any kind of big deal)... Until this happened today.

  I had a PlayStation game in my disc drive that I was playing with PCSX. I pressed the eject button physically on the drive to remove my game, and instead of opening, I got this message:
[IMG]http://linux.skyfallgames.com/cd.png[/IMG]
(In case there's an error loading the image: "**Can not eject volume**; You are not privileged to eject this volume.")

  Now I'm not having problems ejecting, that's not what I'm crying out for here, I just ran "sudo nautilus" and clicked the eject button there and got it out. My problem is that I think this is a bit ridiculous that I don't have permission to eject my own disc drive.

  Is there any way to prevent this from happening?

---

### Post by ibutho on 2009-06-23
Does that happen to all discs? Are you a member of the cdrom and plugdev groups (check by entering **id** in a terminal)?

---

### Post by Revolutionary101 on 2009-06-23
All you need to do is in Terminal type

```
sudo nautilus
```

When the file browser window opens just go find your CD drive then eject the CD.

---

### Post by wpshooter on 2009-06-23
> **Revolutionary101 said:**
> All you need to do is in Terminal type

```
sudo nautilus
```

When the file browser window opens just go find your CD drive then eject the CD.

Hmmmmmmm, I thought that they said they had already done that !!!

---

### Post by Ceiling Fan Man on 2009-06-23
> **ibutho said:**
> Does that happen to all discs? Are you a member of the cdrom and plugdev groups (check by entering **id** in a terminal)?

No, the PS1 disc is the first disc to cause the problem... The system was booted with it in the drive, that may be related. And yes, I am in those groups.


> Quote:
[QUOTE]Originally Posted by Revolutionary101
All you need to do is in Terminal type

```
sudo nautilus
```

When the file browser window opens just go find your CD drive then eject the CD.
Hmmmmmmm, I thought that they said they had already done that !!![/QUOTE]

Yes, that was the first thing I did (After taking the screenshot). My question was how can I prevent it from happening in the future?

---

### Post by Revolutionary101 on 2009-06-24
ooops sorry I didn't see that part that said they had already tried that.

---

### Post by ibutho on 2009-06-24
Just to clarify something,if you put in a disc into the cd/dvd tray whilst logged in to the system, you can eject it without any problems but if a disc is already in the tray during boot up, you cannot eject it when you login?

---

### Post by Ceiling Fan Man on 2009-06-25
> **ibutho said:**
> Just to clarify something,if you put in a disc into the cd/dvd tray whilst logged in to the system, you can eject it without any problems but if a disc is already in the tray during boot up, you cannot eject it when you login?

Sorry for the late reply... Been a busy couple of days and I had forgotten about my thread until I was closing my extra websites I had open that had accumulated.

I just tested that theory by putting in the same PS1 game disc, and rebooting. I could eject after I logged in, no problem. So then I shut it down completely with the disc in, switched off the power supply and held the power button in a few seconds to drain all the caps, then started it back up, logged in, waited a few minutes... It ejected fine.

I guess my error was a one-time deal? Surely there was something to trigger it, but I can't imagine what. I suppose since it's such a rare thing apparently, it's not too important. I admit, I started this thread mostly out of frustration. I thought it was pretty crappy that I didn't have permission to eject my disc drive by physically pushing the button, you know?

---

### Post by nandemonai on 2009-06-25
> **Ceiling Fan Man said:**
> Sorry for the late reply... Been a busy couple of days and I had forgotten about my thread until I was closing my extra websites I had open that had accumulated.

I just tested that theory by putting in the same PS1 game disc, and rebooting. I could eject after I logged in, no problem. So then I shut it down completely with the disc in, switched off the power supply and held the power button in a few seconds to drain all the caps, then started it back up, logged in, waited a few minutes... It ejected fine.

I guess my error was a one-time deal? Surely there was something to trigger it, but I can't imagine what. I suppose since it's such a rare thing apparently, it's not too important. I admit, I started this thread mostly out of frustration. I thought it was pretty crappy that I didn't have permission to eject my disc drive by physically pushing the button, you know?

Just a side note but you generally can't eject a CD while it is in use or mounted in Linux. You need to unmount it first then it will usually spit the disc out for you.

---

### Post by zwdev on 2009-06-26
Generally your system says that if there is a process accessing or using your dvd drive, a simple 
"sudo eject" will do the trick.

---

### Post by dyingsun on 2009-06-26
> **ibutho said:**
> Just to clarify something,if you put in a disc into the cd/dvd tray whilst logged in to the system, you can eject it without any problems but if a disc is already in the tray during boot up, you cannot eject it when you login?


Hi, sorry to interrupt, but what you said is exactly my problem - i have to sudo eject /dev/cdrom   to eject the cd if I reboot or logout. 

id returns these values in relation to cdrom and plugdev:


24(cdrom)   46(plugdev)


Anyway as I said, sorry to interrupt, but it seemed relevant enough to this thread.

Cheers!
Damien

---

### Post by ricardisimo on 2009-08-16
Same here. At first I thought it was an issue with someone else being logged in first, but I just logged my wife out, then logged myself in and was told I could not unmount floppy0 (the USB disc drive) because my wife still owned it, even after she was logged out.

Obviously, yeah - you open a terminal, log in as root and eject. Simple as that may be, it is clearly missing the point, at least as I see it: open access to removable drives is not a security concern in the least. Barring an ongoing process which you don't want interrupted (ripping a CD/DVD, etc.) there should be no issue with letting whoever is logged in eject CDs and DVDs.

And yes, I am in the admin group as well as cdrom, plugdev, etc., etc. That's not the issue; security paranoia is the issue.

---

### Post by scaramanzia on 2009-08-16
Hi guys. Don't forget when a user inserts a CD in tray, doesn't want another user to eject it if the first user isn't willing to do that. The meaning of being a multi-task and multi-user, as linux does, is that things like that can happen all the time, if not prevented.
Surely, it isn't a well described security policy, but the main difference between Linux and Windooze is that the last one supposes that if you are in front of this machine, you're surely its owner, or, at least, its only user by now. This policy isn't valid in Linux: you shouldn't touch anything if you can harass someone: when you insert a CD while not logged, this CD gets "locked" to the user who was logged in when mounted. But when no one is logged, the all proccesses belong to root, and other internal users.

---

### Post by lexis_t on 2009-08-18
Hi there!
I have similar problem with a dvd ejecting..
But I cannot eject my dvd tray if there is a disk inside :-( by any command, nautilus, applet, etc... Only with "sudo eject" it ejects successfully.
If there is no disk the tray is ejected without sudo...

Does somebody know what is the problem?

PS: I'm a member of cdrom and plugdev groups!

---

### Post by kuja on 2009-08-18
> **lexis_t said:**
> Hi there!
I have similar problem with a dvd ejecting..
But I cannot eject my dvd tray if there is a disk inside :-( by any command, nautilus, applet, etc... Only with "sudo eject" it ejects successfully.
If there is no disk the tray is ejected without sudo...

Does somebody know what is the problem?

PS: I'm a member of cdrom and plugdev groups!

Well, if it's open or in use by any programs at all, then it  won't eject for you. Close everything that might  be using the disks files or folders first. To get a list of the processes that are accessing those, run "sudo fuser -c /media/cdrom"

---

