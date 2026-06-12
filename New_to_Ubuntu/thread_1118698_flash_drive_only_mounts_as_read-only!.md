---
title: "flash drive only mounts as read-only!"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by miesnerd on 2009-04-07
So I've never really had a period where this was actually a problem until now. I've tried "sudo nautilus" and changing permissions with no avail. I've backed up the data on the flash drive to my home directory. I'm looking for the next steps taken (remember: I've backed up all my data already so no biggie if I have to reformat the FAT filesystem) just so i can use my freaking flash drive. And btw, it seems like this isnt a problem with the OS as it seems to be with this computer-- same computer I cant ever mount my Sansa e250 on, even now that I have rockbox on it!

---

### Post by miesnerd on 2009-04-07
because this potentially could be questions asked by others 1) Yes, other flash drives seem to work just fine on this computer, plugged into the same USB port, and 2)my ipod is recognized just fine, as well.

---

### Post by Temposs on 2009-04-07
Did you happen to use your flash drive in Windows? You may have removed the flash drive without ejecting it in Windows, which can cause problems in Ubuntu.

---

### Post by llamabr on 2009-04-07
I recently had a similar issue.  Googling suggested that the partition may be corrupt.  Rather than trouble shooting futher, I formatted it as vfat, and now it works and mounts fine.

---

### Post by miesnerd on 2009-04-07
> **Temposs said:**
> Did you happen to use your flash drive in Windows? You may have removed the flash drive without ejecting it in Windows, which can cause problems in Ubuntu.

definately. I go back and forth all the time for work. Please explain, a) so I learn and b) so I can fix it.

If only our university would let me put linux on my GA computer, this wouldnt be a problem!

---

### Post by LowSky on 2009-04-07
You cannot just pull out the flash drive when you think it is done loading files, sometimes that is not true. you should always use the 'unmount' option in Ubuntu, and the 'Remove drive safely' option in Windows (can be found in the notification area -- little green icon).

---

### Post by miesnerd on 2009-04-07
> **LowSky said:**
> You cannot just pull out the flash drive when you think it is done loading files, sometimes that is not true. you should always use the 'unmount' option in Ubuntu, and the 'Remove drive safely' option in Windows (can be found in the notification area -- little green icon).
I guess I should have have explained myself. I'm well aware of that, but I was more curious in the form of "what problems can it cause". Sorry.

So if I go into work today, mount the drive, and unmount it correctly, could that solve my problem? Or is the problem, as ubuntu sees it, that I unmounted the drive once incorrectly?

---

### Post by MrWES on 2009-04-07
> **miesnerd said:**
> I guess I should have have explained myself. I'm well aware of that, but I was more curious in the form of "what problems can it cause". Sorry.

So if I go into work today, mount the drive, and unmount it correctly, could that solve my problem? Or is the problem, as ubuntu sees it, that I unmounted the drive once incorrectly?

By not properly doing a "Safety Remove Hardware" in windows; a flag is left on the drive and Ubuntu will think the drive is in use. Properly mounting and removing the drive in Windows should solve your problem in Ubuntu.

Bill

---

### Post by miesnerd on 2009-04-07
> **MrWES said:**
> By not properly doing a "Safety Remove Hardware" in windows; a flag is left on the drive and Ubuntu will think the drive is in use. Properly mounting and removing the drive in Windows should solve your problem in Ubuntu.

Bill

Thanks man.
I'll try that today, and if not, I guess my only option then is to reformat?

Is there a way to use the terminal to get rid of the flag though? Seems like since I know there's no reason for the flag (clearly, its NOT in use right now on a windows computer) that I could just override that.

---

### Post by bruceschaller on 2009-04-14
I had the same problem.  Jaunty seems to handle this pretty darn well though.

Right click the mounted drive.
-> Unmount.
Unplug Drive
Plug Drive back in
Works like a charm.

Cheers!
Bruce Schaller

---

