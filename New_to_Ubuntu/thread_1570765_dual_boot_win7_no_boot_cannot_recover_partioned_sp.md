---
title: "dual boot win7 no boot cannot recover partioned space for ubuntu"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by jefalahac on 2010-09-08
I attempted to dual boot a dell laptop - partitioned space for ubuntu 10.04 gnome. Had a successful install. Computer booted several times in both OS's then the Dell disk utility did its thing and I could not get into either. I successfully recovered the win7 after formatting/dumping ubuntu and rewriting the mbr. I have not been able to recover the space set aside for ubuntu. I have attempted with the ubuntuLive and GPartedLive cd's. I apologize if this issue has already been addressed but I have had no luck in locating any mention of this issue or my stupidity in the forum.

Thank you, whomever, for any guidance that can be provided.

---

### Post by jtarin on 2010-09-08
> **jefalahac said:**
>  I have had no luck in locating any mention of this issue or _my stupidity in the forum._
It's only your first post...give us time to mention it.:p We all make big mistake!

Just joking....but are you saying you cannot boot the Live CD? Do you have any operating system at all on the disc? Did you format the disc? How did you restore the MBR?

---

### Post by Jesus_Valdez on 2010-09-08
Have you tried using the windoes 7 format software? It's on the control panel under system, if I recall correctly.

If you are'nt planning using the spaces dedicate to Ubuntu, just format it, so Windows can "see it".

---

### Post by 0N3 on 2010-09-08
Go to Start> on the menu right click Computer and select manage the space blacked out should be Free space or so i forget right click and format it should recover your dedicated Ubuntu space

---

### Post by Mark Phelps on 2010-09-09
Click the Windows "button" and enter Disk Management.  This will launch the Disk Management console and allow you to see and manage your partitions.

---

### Post by jefalahac on 2010-09-09
Sorry for any confusion in my post.

Tried to dual boot a win7 dell. Worked for a while then the dell disk utility did its thing to the mbr and I couldn't boot the computer in either os. Ended up removing ubuntu then used the win disk utility to remedy the mbr. win7, someone should make a puke emoticon, something would be nice for any reference to windows, I digress... win7 runs fine but does not see the partitioned space created for the ubuntu installation. Have tried ubuntuLive cd and GPartedLive but have not been able to blow away the partition and re-integrate to the win7 partition.

---

### Post by jtarin on 2010-09-09
If you still have a viable install of Ubuntu you can restore by placing Grub in the /root of the Ubuntu partition not the MBR of the disk and using the Win Loader to do the booting that way Dell doesn't complain.My signature has part of the solution...a Grub reinstall is the other part.

---

### Post by srs5694 on 2010-09-09
Boot the Ubuntu installer into live CD mode, open a terminal (text-mode shell) window, and type "sudo fdisk -l". Post the results here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. That will tell us how your disk is laid out; without that information, all we can do is post guesses, some of which could be dangerous.

---

