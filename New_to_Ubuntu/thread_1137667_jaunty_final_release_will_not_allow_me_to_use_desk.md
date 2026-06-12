---
title: "jaunty final release will not allow me to use desktop effects"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-04-25
from what i gather i have no driver for my video card but none is listed in the restricted drivers utility. some info on my computer is an HP Pavillion dv4-1275mx with ATI Radeon graphics. i will post more details if needed. i really need assistance with this though

---

### Post by Temposs on 2009-04-25
That's odd...I've never worked with an ATI chip before, but I think you should open System->Administration->Synaptic Package Manager and then search for fglrx. Install the module called xorg-driver-fglrx. See if that works for you.

---

### Post by infinitejones on 2009-04-25
Same here - HP Pavilion with nVidia 8400M - all restricted drivers installed and up to date. Desktop effects worked fine before (ie. with 8.10) but following a clean upgrade to Jaunty, I can't enable desktop effects at all.

Any more ideas, anyone?

---

### Post by T2manner on 2009-04-25
I have the same exact problem. 
Except I have an Intel driver.

---

### Post by Temposs on 2009-04-25
Guys you both have different graphics cards than the OP. You should start a new thread specifying your specific graphics card.

---

### Post by PatrickMoore on 2009-04-25
> **Temposs said:**
> That's odd...I've never worked with an ATI chip before, but I think you should open System->Administration->Synaptic Package Manager and then search for fglrx. Install the module called xorg-driver-fglrx. See if that works for you.

the only i have that is remotely similar to what you advised was a package titled xserver-xorg-video-radeon which is indeed installed. is there any configuration i need to do?

---

### Post by PatrickMoore on 2009-04-25
synaptec is only showing me installed packages when i search. i tried adjusting my repositories but nothing is changing

---

### Post by Temposs on 2009-04-25
Go to System->Administration->Software Sources

Click on the Ubuntu Software tab. Under "Downloadable From the Internet", all the check boxes should be checked except maybe "Source Code". Check any of the others if they're not checked. If that's the case, after you close Software Sources(it should reload your repositories when you close), open Synaptic Package Manager again, and do the search I indicated.

---

### Post by PatrickMoore on 2009-04-25
this is probably more appropriate in another thread. but i found the package by browsing. its my search functions that are out of whack. i tested it by searching for the conky package which did not come up

---

### Post by Temposs on 2009-04-25
I found it!

In Synaptic on the bottom left, you've probably clicked on "Status", and "Installed" within that. Well maybe that's not your problem, but it produces the results you're describing. Try clicking "Sections", and click "All" there.

---

### Post by MrWES on 2009-04-25
> **PatrickMoore said:**
> from what i gather i have no driver for my video card but none is listed in the restricted drivers utility. some info on my computer is an HP Pavillion dv4-1275mx with ATI Radeon graphics. i will post more details if needed. i really need assistance with this though

Had the same problem with my ATI card; guess some ATI cards do not like the new default EXA acceleration in Jaunty. You might try adding this line to your /etc/X11/xorg.conf file

```
	Option          "AccelMethod"   "XAA"

```

Reboot and/or restart the X server.

Bill

---

### Post by PatrickMoore on 2009-04-26
a fresh install resolved my issues im downloading the driver via restricted drivers menu now. thank you temposs.

---

### Post by chouse626 on 2009-07-13
I have 4 pc's running Ubuntu Jaunty Jackalope and it seems like whenever I update the computer I lose desktop effects and my video card no longer allows me to do it.  3 out of 4 pc's I updated with the "recommended updates" and no longer could I used desktop effects.  However the 4th pc is fine.  All of these computers are exactly the same two HP's and two Toshiba laptops.  I think it has something to do with the system hardware drivers and the updates remove those.  I dunno I just wish I could find out wtf the issue is b/c the two toshiba's I'd love to have the desktop effects back.

---

