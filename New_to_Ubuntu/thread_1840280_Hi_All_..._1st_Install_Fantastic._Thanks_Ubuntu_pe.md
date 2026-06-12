---
title: "Hi All ... 1st Install Fantastic. Thanks Ubuntu people !* couple of small issues."
date: 2011-09-07
forum: New to Ubuntu
---

### Post by greg0 on 2011-09-07
Hi Everyone.
I'm a brand new 32bit Ubuntu user in Australia.  I installed 11.4 one week ago, Its great. I cant believe how well it works and whats packed into it, so many programs all for free. All who contributed really deserve a big thanks.

I installed side by side Win7 64bit on a homebuilt PC using GAMA78LMT-S2 motherboard & 955 X4 be  CPU.  Nearly everything worked first go without me changing settings, WOW ! 
I discovered Ubuntu whilst looking for solutions to never ending Win 7 problems (after selling to anyone & taking my money microsoft deemed my OEM copy illegal, they used to allow for hobby builders.) So I gave Ubuntu a try, it fit my leftover budget.  :smile: And was blown away at how well it worked and what great software it included.  Amazing !.
 
I Haven't stopped giving it a rap to my friends and workmates. A couple are of them are going to try an install, one next weekend. 

Only small trouble was HD5670 PCIE Videocard caused very slow boot , black screens and stalls, fixed by removing card & using on board graphics. Hope to get card working again one day. 

And I seem to be having the odd folder and drive icon pop into the desktop at random ? Should I deletE these if duplicates. My boot log show a few missing files. The only recovery console I found in boot menu required programming knowledge, is that right or am I missing more than a couple of files ?
  
Ive lots to re learn, any ideas would be appreciated.  Im really enjoying  this wonderful new thing with the funny name Ubuntu. 

Thanks

---

### Post by Beacon11 on 2011-09-07
Glad you're enjoying it! Regarding the video card, with the HD5670 inserted does Ubuntu ever actually boot? If so, have you tried installing proprietary drivers for it? Search the menu for "Additional Drivers" and see if it gives you the opportunity to install something-- it may help. (If you're not using Unity, i.e. you're using Classic mode, it's in System > Administration > Additional Drivers.)

When you say your boot log is showing a few missing files, what do you mean exactly? Can you paste the relevant log entries in here?

---

### Post by ikt on 2011-09-07
Welcome :)

> **greg0 said:**
> And I seem to be having the odd folder and drive icon pop into the desktop at random ? Should I deletE these if duplicates. My boot log show a few missing files.

Ubuntu will do this when you mount a drive, by any chance are the folders on a networked computer or external hard drives or other internal drives?

If you're really interested here's a run down on mounting a drive: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

But to be short and sweet, ubuntu doesn't mount drives like windows, windows will automatically mount drives and give them a letter (c: d: etc), ubuntu/linux lets you mount the drive anywhere you want, by default ubuntu mounts it in /media, so your external drive will actually appear like a folder.

Some more information here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

There's also a link in my sig to where you can find other Australian Ubuntu users.

Have fun :)

---

