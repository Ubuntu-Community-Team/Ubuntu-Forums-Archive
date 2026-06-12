---
title: "Programs Crashing"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Tumpster on 2009-04-09
So, recently I had some problems with my hard drive that entailed going through and fixing some sectors in ubuntu. Since then any program I'm running and click open on, as soon as I do, it crashes. My folders in the drop down "Places" menu show up as crazyily renamed one is "ta" and the other is some long "border 1px solid http://www.livenation...." etc and the same goes as well when I open up my home folder. On the left they show the usual "Pictures, Music, Documents" renamed something else but on the right when I actually look at my home folder they are named correctly. Whats going on? Is there any way to fix this so my programs run correctly when I want to open something through them?


By the way, in Firefox there is no troubles with opening....weird....

---

### Post by HereInOz on 2009-04-09
I think you still have issues with your hard drive, or the problems you had have left you with some corrupt files.

Unfortunately, as much as it would be wonderful to be able to rescue the system, you may be looking at a rebuild.  If your /home directory is in another partition, then you should be able to rebuild the system while leaving the /home partition intact (don't format it).  If the /home directory is in the root partition, then you will lose that data in a rebuild, so back it up first.

I don't know what sort of issues you had with the hard drive, but if it caused a problem before, it is probably worth replacing it and rebuilding the system on the new one.

---

### Post by miegiel on 2009-04-09
As **HereInOz** said it's probably corrupted/damaged files that where stored on the bad sectors.

If it's an old disk it's time to get a new one. If the sectors got damaged because you dropped the disk you might be OK after repairing them. But backup stuff you don't want to loose and check your disk a few times the next days to make sure your not getting any new bad sectors.

---

### Post by Tumpster on 2009-04-11
Well the thing is, the hard drive is just fine, there are no bad or corrupt sectors. What had happened was some how while being moved, the hard drive power cable came unplugged so it would start up and run ubuntu for a bit and then things would start locking up as the hard drive lost power. I wondered if my hard drive was dieing and opened the case to inspect and saw the power cable unplugged, after plugging it all back in I've had no problems, just this problem here. Can it be fixed without a whipe or reinstall? If so how?

---

### Post by miegiel on 2009-04-11
Sorry, I thought that "fixing some sectors" implied that you had bad sectors on your disk.

It can be fixed without reinstalling, but you'll need to figure out which files are damaged. That won't be easy and won't be fast.

The quick and dirty way is to reinstall, it only takes 30min (on my PC). And if you have your /home on a separate partition you won't even loose your settings and personal files. You'll only need to reinstall the programs you use and aren't installed by default.

If you don't have a separate home partition, you can start by making one before you reinstall and copy your Tumpster(*) directory there.

(*) guessing your linux user name here ;)

---

