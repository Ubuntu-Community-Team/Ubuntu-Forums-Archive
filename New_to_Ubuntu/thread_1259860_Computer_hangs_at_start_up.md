---
title: "Computer hangs at start up"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-09-06
I came in complaining about this once before, and everyone told me it must be a hardware problem. WELL IT IS NOT. IT IS NOT, and I don't want people to tell me that this time. There is something wrong with Ubuntu. 

When I start my computer up, every once in a while it will stop loading as soon as it hits the little ubuntu loading bar. It will then turn off the monitor, or stop sending signals to the monitor (the screen goes blank and the light goes from green to amber). It will make noises like it's doing something for awhile. It will often do it a number of times in a row. This time it happened about ten times in a row. It will turn off the monitor at different points, sometimes loading more, sometimes loading less. A couple of times this time I noticed some white writing come up underneath the loading bar but it was turned off too fast for me to read it. It managed to get to the white writing point twice, but it looked like different instructions. The first time I thought it said something about "routine something checks" or "rootline something checks" roots or boots may have been mentioned. The last time I saw it say something about hitting esc. I can't turn the power off from the tower and have to flick off the powerbar. This is really bad for my computer and I don't want to have to keep doing it! Ten times in a row I just did it! The fact that it worked this time seems totally random. I don't understand.

I am running a pentium 4 2.93 Ghz with 370 mbs of RAM. I know my RAM is a little low. No I can't afford more, and besides that is not the problem. I have recently cleaned out my fans, it is not an overheating problem. I have tried booting from memory and I have tried booting from disc and the same thing happened.

---

### Post by ecmatter on 2009-09-06
The following isn't a fix, but it will let you see what's going on as your computer boots and show you exactly where it hangs:

Open /boot/grub/menu.lst

```

sudo nano /boot/grub/menu.lst

```PgDown until you find a similar entry to the following:

```

title           ubuntu 9.04, kernel 2.6.28-15-generic
uuid          325ddc57-be0f-4861-898d-ba798e012a42
kernel       /boot/vmlinuz-2.6.28-15-generic root=UUID=325ddc57-be0f-4861-898d-ba798e012a42 ro  single quiet splash
initrd         /boot/initrd.img-2.6.28-15-generic

```delete 'quiet' and 'splash' and save the file <CNTRL>+O.

Reboot.

Now you should be able to see what's going on as the computer boots (no splash screen, no loading bar).  From what you're saying, you should get to a point in the boot process where it runs a routine check of drives.  If it fails there, chances are it's a problem with your hard disk (and it may give you an option to attempt to repair the disk).

---

### Post by rahrahmah on 2009-09-06
It won't let me save. It says that I don't have permission. I'm on the only account. It didn't give me the option of typing my password. How do I give myself permission?

---

### Post by eyeyoubin on 2009-09-06
that's curious. sudo command gives you root permission...

---

### Post by pi.boy.travis on 2009-09-06
If you put 'sudo' in front, like ecmatter said, it should prompt for your password before it opens the file, unless you have put in your password within the last 5 minutes.

---

### Post by ecmatter on 2009-09-07
Can you change permissions for the file?

```

sudo chmod 664 /boot/grub/menu.lst

```

...or does sudo fail in that instance as well?  If it does, then I'm not sure what you could do to diagnose the problem.

---

### Post by pi.boy.travis on 2009-09-07
> **ecmatter said:**
> Can you change permissions for the file?

```

sudo chmod 664 /boot/grub/menu.lst

```

...or does sudo fail in that instance as well?  If it does, then I'm not sure what you could do to diagnose the problem.

Please DO NOT change the permissions for any file outside your home directory!  It could really mess things up, or even make your system totally unbootable.  Trust me,  I learned this one the hard way. . .

---

### Post by ecmatter on 2009-09-07
> **pi.boy.travis said:**
> Please DO NOT change the permissions for any file outside your home directory!  It could really mess things up, or even make your system totally unbootable.  Trust me,  I learned this one the hard way. . .

The [GRUB HOW TO]("https://help.ubuntu.com/community/GrubHowto") in the Ubuntu Documentation suggests changing permissions for the menu.lst file.  I can't see how changing permissions in this instance is any different.

You should change them back, though, as soon as you're finished editing the file:

```

sudo chmod 644 /boot/grub/menu.lst

```

---

### Post by rahrahmah on 2009-09-07
I didn't type anything. All I did was get rid of "quiet splash". I didn't go through the command line because it scares me. I went through menus. Should that make a difference? I don't know how to "change permissions".

---

### Post by wojox on 2009-09-07
just open the terminal:


```
gksudo gedit /boot/grub/menu.lst
```

That will let you remove those options and save the file.

---

### Post by mbzn on 2009-09-07
I believe the message you got was the filesystem check. Ubuntu runs this every now and again.

---

### Post by wojox on 2009-09-07
Good point mbzn.

I think it's like every 33 boots or so many months.

---

### Post by mbzn on 2009-09-07
I noticed that after 9.04 it doesn't warn you what it's doing anymore. the changes above will show you. It's usually after an x amount of mounts to the / partition. It is somewhere close to 30.

---

### Post by smithpeter018 on 2009-09-07
I think you should re-install your operating system maybe its corrupted if its not then check your hard disk on other computer maybe your hard disk media is slow

---

### Post by rahrahmah on 2009-09-07
Going through the terminal did work, as opposed to going through menus. Why that makes a difference, I don't know. The Terminal still freaks me out, though. I applied the changes to make it tell me what it's doing.

This time around, it said partition has been mounted 27 times without check, forcing check. It scanned through and then started up. I really can't say if this is what was going wrong however. I waited, before. Like, for a long time, and it never came back from whatever it was doing. It would think and think then go quiet but the monitor continued to receive no signal. Perhaps the way it scanned with a "quiet splash" confused the video signal. Who knows? Regardless, it worked this time, and if it wants to turn itself off again at least I'll be able to see the point at which it freaks out.

THANKS SO MUCH! 

By the way, if any of you are the people who develop Ubuntu, or know where I could make suggestions, I think that having a scan that turns your computer off at start up with no warning at seemingly random times is pretty dumb. Someone on here mentioned that silencing the start up info is new to this distro, and I think that it's a failed idea. I could have damaged my computer by turning the power off in the middle of these scans because I didn't know what was happening.

---

