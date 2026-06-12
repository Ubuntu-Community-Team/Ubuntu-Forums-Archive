---
title: "Belkin Wireless G Desktop Card"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by SilverGoldBronze on 2008-04-01
Please help me...


I recently purchased a Belkin Wireless G Desktop PCI port card, and I installed it on my computer.

I booted XP, checked it out and my WIFI runs perfectly... on XP.

I booted Ubuntu, checked literally everywhere, and couldn't find my PCI card except as an unknown device in Device Manager.

I checked with the Ubuntu help ans support, and found I had to install Ndiswrapper or something. I did as it told me to, but I couldn't find the "ndisgtk" file it told me to install, so I installed only the two supplements to the program. I am wondering how to download this ndisgtk file so that I can emulate the drivers, but so far, I have not found anything.

There are some Ubuntu geniuses out there and I'm hoping one could help me out.



Additionally, I am not sure how to get the card driver off of XP, as I do not know where to look.

---

### Post by ELF_O8 on 2008-04-01
_[http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.52.tar.gz&21884682](http://sourceforge.net/project/downloading.php?group_id=93482&use_mirror=internap&filename=ndiswrapper-1.52.tar.gz&21884682)_

That should be the complete ndiswrapper. Download to desktop and extract it.
Just open up terminal and eneter ```
cd /home/username/Desktop/ndiswrapperfoldername/

make && sudo make install
```

---

