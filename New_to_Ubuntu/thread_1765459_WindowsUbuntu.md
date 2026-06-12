---
title: "Windows/Ubuntu"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Tsujimoto on 2011-05-23
Hey, I'm pretty new to Ubuntu and it on a dual boot kind of setup. So that I can still have Windows and Ubuntu at the same time. Anyhow, just yesterday, I went on Windows and did a Windows Update. I reinstalled the computer and went back on Windows. When I tried to restart and go on Ubuntu, I couldn't. Usually a purple screen with 6 or so different booters shows up, but what showed up was a black screen for just 2 boots. Ubuntu and Microsoft. I did the Ubuntu boot and it gave me the demo version of Ubuntu. The way I resolved it was to put the disk back in and Update from 11.04 back to 11.04 (if that makes sense.) I'm wondering, is there anyway I could avoid this????? :confused:

---

### Post by _0R10N on 2011-05-23
Hi!! Windows is not intentioned to live with other OSs. So, if you've reinstalled windows after installing Ubuntu, you must reinstall grub to your MBR, so your PC  will be able to dual-boot again.

Regards!

---

### Post by coffeecat on 2011-05-23
> **Tsujimoto said:**
> I'm wondering, is there anyway I could avoid this????? :confused:

That's an interesting question. For a Windows update to have done what you've described, it would have had to re-install Windows code to the mbr. Which is extraordinary. It's not happened to me - yet - but I have seen similar reports in other threads, so I believe you. I'm simply flabbergasted that a Windows update does that.

There was a slightly simpler way to re-install grub to the mbr (which is what you need for the purple menu screen you describe). Here's a link for future use in case this happens again:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

By the way, which version of Windows did this dastardly deed? Iirc correctly, the version of Windows that did this in the other threads was XP, which may explain why I haven't seen this.

**EDIT**: Just noticed this in your post:

> **Tsujimoto said:**
> Anyhow, just yesterday, I went on Windows and did a Windows  Update. I reinstalled the computer and went back on Windows.

What do you mean by, "I reinstalled the computer"? Did you do only a Windows update or did you reinstall Windows? If you installed Windows then, yes, the mbr gets written with Windows code - every time. You can't prevent it.

---

### Post by Tsujimoto on 2011-05-23
Actually that was a big typo, I believe I meant "restarted."
It's Windows Vista btw.


> **coffeecat said:**
> That's an interesting question. For a Windows update to have done what you've described, it would have had to re-install Windows code to the mbr. Which is extraordinary. It's not happened to me - yet - but I have seen similar reports in other threads, so I believe you. I'm simply flabbergasted that a Windows update does that.

There was a slightly simpler way to re-install grub to the mbr (which is what you need for the purple menu screen you describe). Here's a link for future use in case this happens again:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

By the way, which version of Windows did this dastardly deed? Iirc correctly, the version of Windows that did this in the other threads was XP, which may explain why I haven't seen this.

**EDIT**: Just noticed this in your post:



What do you mean by, "I reinstalled the computer"? Did you do only a Windows update or did you reinstall Windows? If you installed Windows then, yes, the mbr gets written with Windows code - every time. You can't prevent it.

---

### Post by Mark Phelps on 2011-05-24
> **Tsujimoto said:**
> I went on Windows and did a Windows Update. I reinstalled the computer and went back on Windows. When I tried to restart and go on Ubuntu, I couldn't. Usually a purple screen with 6 or so different booters shows up,
This would be a GRUB menu created by Ubuntu.
> ... but what showed up was a black screen for just 2 boots. - Ubuntu and Microsoft.
This would be a Windows OS selection screen -- created using a Wubi install. 
> I did the Ubuntu boot and it gave me the demo version of Ubuntu. 
Makes no sense -- the only way you get the "demo" versiuon is to boot from the CD and select the Try option.
> The way I resolved it was to put the disk back in and Update from 11.04 back to 11.04 (if that makes sense.) 
So,basically, you reinstalled Ubuntu.
> I'm wondering, is there anyway I could avoid this????? :confused:
Have been doing Windows Updates longer than I care to mention -- and have NEVER had it rewrite the MBR in the process.  So, don't know HOW you ended up losing Ubuntu startup capability simply through Windows Updates.

Have you confirmed that Windows still works OK after the updates?

---

### Post by _0R10N on 2011-05-24
If you haven't solved your problem yet, here's a good step-by-step to follow. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

regards!

---

### Post by _0R10N on 2011-05-24
If you haven't solved your problem yet, here's a good step-by-step to follow. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

regards!

---

