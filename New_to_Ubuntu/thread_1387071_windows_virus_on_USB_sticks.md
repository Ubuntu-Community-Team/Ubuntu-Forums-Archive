---
title: "windows virus on USB sticks"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by benfindlay on 2010-01-21
Hi all,

I'm fairly happy I have the right answer on this, but would like to get confirmation from the community for my own peace of mind. Here's the situation:

I have 3 USB memory stick that are all showing up on Windows machines as a folder, not a USB drive. As a result it is inaccessible. On suspicion of a virus, I have examined it using Mac OS X and found the presence of an autorun.inf file, which is 'locked', and a suspicious looking executable called cafgm.exe in the RECYCLER folder on the stick. The autorun.inf is displayed as a unix executable file in Mac OS X. I can delete the files fine, even though the autofun.inf is showing up as 'locked'

My understanding is that Linux/unix machines are immune to Windows viruses so I can just delete the files from the stick (since it is FAT32) and all will be well again. What I would like to do however is examine the autorun.inf to confirm that it is indeed causing the abnormal mounting behaviour observed in Windows.

So what I would like confirmation of is that using ***cat*** to display the contents of the autorun.inf file in Terminal is perfectly safe to do. Ordinarily I wouldn't worry one bit about this, it's just that Mac OS X displays the file as a unix executable in Finder, which had me somewhat puzzled.

Can someone please confirm using cat to view the file is ok to do?

Thanks

Ben

---

### Post by stim on 2010-01-21
You are correct. Linux/Unix is immune to Windows viruses.   Removing and/or inspecting the autorun.inf is safe.  You can also use the program "file-roller" to inspect the contents of the .exe, it will treat the .exe as an archive (zip,tar,etc)

---

### Post by Nightstrike2009 on 2010-01-21
I can confirm windows viruses cannot affect Ubuntu (or linux) but could infect windows machines (if you care about that sort of thing LOL)

Try installing "ClamTK" (GUI version with & for Clamav) or "ClamAV" (Terminal version) if you wish to remove them in Ubuntu.:-)

For some reason you have to type "sudo freshclam" in a teminal window (or Hold Alt + F2 keys down to update signatures but aside from an update button its fine. Only use on pen drives or home folder though, don't use it on Linux filesystem (Full system scan) as it suffers from "False positives" and could break ubuntu, don't set it to auto delete mode either you need to check whether its a "False Positive" before deleting. :-(

It was originally ment as an email virus scanner but great for Usb drives or odd folders you suspect to be virused (Non system) :-)

---

### Post by steveneddy on 2010-01-21
You also may consider simply formatting the drive to erase all of the data and reset the file system on the drive.

---

### Post by pricetech on 2010-01-21
A normal "autorun.inf" file is just a text file.  You can look at it in a text editor if you prefer.

I'd use gparted to remove the partition if you're really concerned about a virus.  Then format it on a winders box if you plan to use it with winders.

---

### Post by lisati on 2010-01-21
> **pricetech said:**
> A normal "autorun.inf" file is just a text file.  You can look at it in a text editor if you prefer.


+1
I'd be more worried about whatever programs/data the autorun.inf points to than its actual presence.

More info on autorun can be found here: 
[http://en.wikipedia.org/wiki/AutoRun](http://en.wikipedia.org/wiki/AutoRun)
[http://en.wikipedia.org/wiki/AutoPlay](http://en.wikipedia.org/wiki/AutoPlay)

---

### Post by benfindlay on 2010-01-22
Hi all, thanks for your replies, that's pretty much what I thought.

Just to clarify the reasons for my paranoia regarding the autorun; I'm aware that they commonly exist and are normally nothing to worry about; however, this memory stick should definitely NOT have an autorun.inf present, as the stick was formatted immediately after purchase to remove all the bundled junk that came with it. That's what was making me paranoid.

Thanks again

Ben

---

### Post by 3rdalbum on 2010-01-22
Just use 'cat'. Cat won't execute the file, it will merely read it.

Actually I'd suggest using 'less' instead:

```
less autorun.inf
```

---

### Post by QuimNuss on 2010-01-22
I'm not 100% sure on this, but I think it's windows that creates the autorun.inf when you plug your USB in. Same for Recycled and other hidden folders. (I usually erase them from Linux and, indeed, they re-appear after plugging it to a Windows machine)

As windows is in charge of the file, that explains why so many trojans can access the file and make it point to their own virus executables.

---

### Post by KeLa on 2010-01-22
> **QuimNuss said:**
> I'm not 100% sure on this, but I think it's windows that creates the autorun.inf when you plug your USB in.
I have never seen windows do that. (i mean virus free windows)
Have been using usb sticks in windows and linux since usb sticks came to market.

---

### Post by hooldus on 2011-04-10
[edited]

---

