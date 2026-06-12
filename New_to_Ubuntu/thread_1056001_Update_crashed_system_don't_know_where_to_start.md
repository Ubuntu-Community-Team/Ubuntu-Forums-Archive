---
title: "Update crashed system don't know where to start"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by JamesMcG on 2009-01-31
I just installled an update on my desktop, all of a sudden it mentioned something about new distribution and everything started throwing errors saying it was deleting 37 packages. I tried to stop it and reboot into recovery mode. That allowed me to get back into ubuntu but I now have no network, lost all the nvidia stuff so I'm running on one monitor....

Basically at this point I'm lost and don't know where to start.

Any help would be greatly appreciated,

thank you,
Jim

Edit, forgot to mention I am running 8.10 32 bit with the latest update

---

### Post by SnakeHips on 2009-01-31
Hi Jim ,sorry to hear about your probs and welcome to Ubuntu.

would you post the output of the following:

In terminal type
```
cat /etc/X11/xorg.conf
```

---

### Post by JamesMcG on 2009-01-31
I lost all networking so I am typing into the laptop what I see on the screen of the desktop that is working. I can't copy and paste and it won't recognize the thumb drive so I have eliminated the part of the output that is commented out.

If you need that I can put it in just will take a while. lol


Section “Device”
Identifier  “Configured Video Device”
EndSection

Section “Monitor”
Identifier   “Configured Monitor”
EndSection

Section “Screen”
Identifier  “Default Screen”
Monitor  “Configured Monitor”
Device  “Configured Video Device”
EndSection

---

### Post by SnakeHips on 2009-01-31
Am I reading it right you broke out of update manager mid-stream so to speak or did they completely finish? and have you done a cold-boot on the desktop machine?

---

### Post by JamesMcG on 2009-01-31
No it gave several messages about update not being able to complete and cancelling the operation, so I closed those out. And when I did I had no networking. I unfortunately didn't think about leaving it as is and using the laptop to ask for help.

So I tried to to a recover mode, everything ran and I booted into normal mode. At that point I had lost one of my monitors, had no networking again and it won't recognize any drive other than the one it is operating on.

I have it dual booted with xp so I still have all the info safe if worst case scenario. All the vital was still on ntfs partitions.

But that's where we are now.

Thank you all for your help
Jim

---

### Post by SnakeHips on 2009-01-31
"So I tried to to a recover mode, everything ran"

Is this still the case? if so lets boot into recover mode and run update manager ,see what it says.

---

### Post by JamesMcG on 2009-01-31
No recovery mode doesn't have networking either.

---

### Post by SnakeHips on 2009-01-31
Hmmmmm my hunch is this borked at the xorg update ,there's a thread going on 'jaunty' about this but sound very similar to whats happend on your 'intrepid' desktop.
[http://ubuntuforums.org/showthread.php?t=1011847](http://ubuntuforums.org/showthread.php?t=1011847)

Personally i'd recover this situation from the LiveCD.

Hope it helps

---

### Post by JamesMcG on 2009-01-31
That's exactly what it sounds like. I'll let you know how it works.

---

### Post by JamesMcG on 2009-01-31
Ok, maybe I'm being (I believe the term across the pond is) daft?

But I've gotten it to boot with the live cd. I have internet connection. But what do I do from there. I've tried updating but it doesn't hold anything because I'm booting from the live cd.

---

