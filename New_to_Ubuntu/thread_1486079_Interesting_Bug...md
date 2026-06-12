---
title: "Interesting Bug.."
date: 2010-05-17
forum: New to Ubuntu
---

### Post by 2boats on 2010-05-17
I have a Dell Latitude D520 with 10.04.  It was a clean install of 9.10 with an upgrade.  I lost "wired network" in my system tray and could not connect other than wireless.
I, for reasons known only to myself, I loaded another copy of 10.04 as a dual boot.  When it booted up I noticed in Grub that there were two kernels for each installation.  When I booted the second one  for my original installation I had "wired network" but no "wireless".

After trying some things that proved fruitless I did a clean install of Windows XP,  Updated it then a clean install of Ubuntu 10.04, updated it.  Loaded the drivers for my wireless.  Everything worked great!

Now there are two sets of boot kernels for 10.04 in grubb.  If I boot from one I have wireless if I boot from the other I have wired. Neither gives me both.  This doesn't seem right but, it is workable.:)  Everything else I've tested works properly!

---

### Post by corncob on 2010-05-17
Bump!  Crazy! Maybe the next kernel update will fix it.

---

### Post by -humanaut- on 2010-05-17
A fully updated Lucid had a new kernel in the updates awhile ago thats why it's showing 2 kernels sometimes kernel updates are prone to breaking hardware I keep upto 3 on my system in case update A) breaks my system It's happened before check the proposed updates I believe theres a fix there.

---

### Post by sir_nasty on 2010-05-17
I'm going to throw out the stupid question.... because that's what I do... have you run the Ubuntu updates since the install?

---

### Post by -humanaut- on 2010-05-17
No, but I HIGHLY recommend you atleast grab the security updates.

---

### Post by 2boats on 2010-05-17
I ran updates immediately after install before I did anything else.  I did that prior to installing drivers for the wireless.  I run updates regularly....I just ran it again and I'm up to date - there was nothing new.

When I brought my computer out of hibernation this afternoon It had turned off networking on both boots...turning it back on on one turned it on on both.

---

### Post by -humanaut- on 2010-05-17
If the older Kernel supports your hardware better then you should use it. Like I said I try to keep 3 around (when available) Check the proposed updates and see if theres a newer Kernel in there. I believe that there is but I'm not 100% I last updated my computer with Backports and Proposed updates about 4-5 days ago.

---

