---
title: "WUSB54GSC Driver Installed but Doesn't Detect"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by butsam on 2008-01-24
Gutsy Gibbon detected my Linksys WUSB54GSC Driver and installed it, but when I run iwconfig I don't get any of the indicators that it really is installed.

It is definitely in the Hardware section properly.

I am wondering if this may be a power supplied to the USB port issue? I heard this was an issue with previous versions. Any other thoughts on how to make iwconfig know that this device is for Wireless?

I have tried ndiswrapper but it is unsuccessful. It should not be necessary to use ndiswrapper though, since Gutsy Gibbon came with the driver and it appears to work otherwise, it just is not detected in iwconfig.

Sam

---

### Post by butsam on 2008-01-24
Here is some more information (screenshots of the Hardware screen and the lsusb -v results -- only the Wireless device results are displayed, and extend further than 1 screen).

I tried plugging in after boot-up, no luck.

[ATTACH]57444[/ATTACH]

[ATTACH]57445[/ATTACH]

Sam

---

### Post by butsam on 2008-01-24
I got it to work! Out of all the articles on this site, I found this one most useful: 

Linksys WUSB54GSC Wireless in Ubuntu 7.04 Feisty Fawn

I followed the main post, with two modifications:
* I used the files noted in the reply that end with k.sys instead of the original files in the post
* I did NOT have to use the power adjustment (Gutsy Gibbon - v7.10).

Sam

---

