---
title: "Dreaded:  xmessage: problems reading the message file"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by toggle on 2007-10-01
I just downloaded and ran the installer for broadcom wireless 43xx cards on a cleanly installed 7.04 Ubuntu installed pc (that currently has zero network access).

I've seen a lot of posts about the message:  xmessage: problems reading the message file

And a lot of replies saying "Dude you didn't extract the files right".

Well in my case, the files are all extracted correctly (directories and all) but I continue to get this message if I try to install the firmware, or ndiswrapper, or I try to remove the firmware.

Any help greatly appreciated.

---

### Post by toggle on 2007-10-02
bump.

Anyone?

---

### Post by Cyber-J on 2007-10-04
Are you using the offline version of the installer? If so there was a file that the Ndiswrapper installer script was looking for but couldn't find because it had the wrong name. It has since been corrected and the offline package reuploaded with the fix. If you can, try and download the updated package and see if it works for you. If you cannot, try renaming a file named LICENSE which is located in the package root directory to LICENSE-BROADCOM and then running the installer.py script again to see if it works.

---

### Post by toggle on 2007-10-04
Thanks very much Cyber-J, I was beginning to think nobody could help me.

I am using the offline version, but I do have other windows pcs that are Internet connected. I will download the file again and see what happens.

The install script does report that I have the right chipset for the firmware upgrade - which is what I would prefer to use over ndiswrapper. I only mentioned ndiswrapper because I was getting the same result, and I wanted to head off any suggestions to try that.

Anyway, thanks again I will report back later with results.

Cheers.

---

### Post by toggle on 2007-10-04
Yep, that solved the problem... thanks again!

---

