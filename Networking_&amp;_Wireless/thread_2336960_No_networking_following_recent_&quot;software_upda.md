---
title: "No networking following recent &quot;software update&quot; on 14.04"
date: 2016-09-13
forum: Networking &amp; Wireless
---

### Post by richardgmorris on 2016-09-13
Hello all,

As the title suggests, following a recent "software update", I am unable to connect to the internet with wired or wireless connections.  [The only error that showed up during the update was concerning a conflict when upgrading llvm, which I assume is unrelated.]   I am using a Dell Precision 5510, running 14.04.5, with kernel 3.19.0-68.

Since I am using another computer to write this post and cant copy/paste, I will not type out all the output of commands unless asked, but here is a summary...

From the "wireless-info" script (which I already had saved from [previous problems arising from Secure Boot]("https://ubuntuforums.org/showthread.php?t=2331090"))... 

lspci... returns the Intel 8260 wireless card and an unassigned device from Realtek Semiconductor.

rfkill, lsmod and ifconfig... blank!

Running lshw -C network returns the wireless card as unclaimed and ethernet doesn't show up at all?  (eth1 doesn't show up anywhere in the wireless-info script either).

Can anyone help, I'm really a bit out of my depth here.

Cheers,
Richard

---

### Post by ajgreeny on 2016-09-13
For a start that kernel and hardware enablement stack is now no longer supported so I suggest you update to the xenial HWE or do a full upgrade/install of Xenial 16.04.1.
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for the info on that.

However, I do not see why that would suddenly cause a problem of network connection by both ethernet and wifi so let's dig a bit deeper.
See all the info in the sticky post at [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and show us the output of the script linked to there. It will help those who know more about networking and wifi to find a solution for you.

---

### Post by richardgmorris on 2016-09-13
Thanks ajgreeny,You're right, I am indeed going to upgrate to Xenial; up until recently I was waiting for the point update, and since then I seem to have been busy.  Thanks for the link.The script you link-to is precisely the "wireless-info" script mentioned in my post.  Which was hard to post as I did not have the ability to connect to the internet.Anyway, looking at "/var/log/dpkg.log", I realized that the offending update included a kernel change, from 3.19.0-65 to 3.19.0-68.  Sorry I hadn't noticed this when I made my original post.   Assuming this was the likely cause of my problems, I ran the "wireless script", and then booted into the previous kernel 3.19.0-65 from the grub menu.  This restored my connectivity as expected, allowing me to post the results (see attached).Thanks for your help... any / all comments or thoughts welcome.

---

### Post by richardgmorris on 2016-09-13
I have since fixed the LLVM conflict mentioned in the original post (by forcing an overwrite) and performed the software update again (whilst booted into 3.19.0-65) and everything appears to be working as expected.  I don't understand what caused the original problem, so any ideas would still be useful.  For now though, I will mark the post as solved.  Thanks to anyone who looked at this or spent any time trying to help.

---

