---
title: "Day 4 of using Linux: How to recover when system hangs?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by OldByter on 2009-01-28
Hi,
Four days ago I turned my back on XP, downloaded the Ubuntu/Linux ISO, burned it to a CD and was pleasantly surprised by the ease of installation, the user-friendly window-based interface and all the software available. Very nice!

However, I have a re-occurring problem. The entire system hangs/freezes frequently while attempting to move layers in a large image file (17MB) in Gimp. It happens less frequently if I use the keyboard arrow keys instead of the mouse.

Questions: Is there a way to recover from a system hang other than rebooting the computer? (By system hang I mean: the mouse pointer will move, but absolutely nothing responds to mouse clicks.) Is there a log file or something which might let me know why the problem occurs?

Thanks in advance.

---

### Post by DGortze380 on 2009-01-28
> **OldByter said:**
> Hi,
Four days ago I turned my back on XP, downloaded the Ubuntu/Linux ISO, burned it to a CD and was pleasantly surprised by the ease of installation, the user-friendly window-based interface and all the software available. Very nice!

However, I have a re-occurring problem. The entire system hangs/freezes frequently while attempting to move layers in a large image file (17MB) in Gimp. It happens less frequently if I use the keyboard arrow keys instead of the mouse.

Questions: Is there a way to recover from a system hang other than rebooting the computer? (By system hang I mean: the mouse pointer will move, but absolutely nothing responds to mouse clicks.) Is there a log file or something which might let me know why the problem occurs?

Thanks in advance.

ctrl+alt+bkspace will restart X and kill all graphical programs currently running.

You may want to look into upgrading your RAM, just a guess, but that sounds like your issue.

---

### Post by bwang on 2009-01-29
Alt+SysRq+R+E+I+S+U+B reboots the computer safely.

---

### Post by DGortze380 on 2009-01-29
> **bwang said:**
> Alt+SysRq+R+E+I+S+U+B reboots the computer safely.

lmao...


or, ctrl+alt+f2
sudo shutdown -h now

---

### Post by Tomatz on 2009-01-29
Open a terminal and run this command:

```
metacity --replace
```

Then try to replicate the bug.

---

### Post by Captain_tux on 2009-01-29
Why's that funny? Alt+SysRq+R+E+I+S+U+B is an excellent method to recover your system...

---

### Post by hyper_ch on 2009-01-29
ctrl-alt-backspace --> that will restart the whole xserver (hence all graphical programs will be closed)

---

### Post by DGortze380 on 2009-01-29
> **Captain_tux said:**
> Why's that funny? Alt+SysRq+R+E+I+S+U+B is an excellent method to recover your system...

It's funny because it's excessively long and rarely necessary, simply restarting X and/or dropping to shell will allow you to recover without a reboot.

I never said it didn't work.

---

### Post by Captain_tux on 2009-01-29
> **DGortze380 said:**
> It's funny because it's excessively long and rarely necessary, simply restarting X and/or dropping to shell will allow you to recover without a reboot.

I never said it didn't work.

Ahhh, yes... ok, I get what you mean now.

Thanks for the answer bro...

---

### Post by DezSP on 2009-01-29
Ctrl+Alt+PrtScr+K is another one for getting rid of a hang (and practising butterfly hand movements). It restarts X and *something else*, I don't really know what. But it's worked in the past where Ctrl+Alt+Backspace has failed. :P

---

### Post by OldByter on 2009-01-31
Thanks for the replies.

I attempted to recover using the keyboard and found it was non-responsive as well.

Solution found:
The suggestion about it possibly being a memory-module problem helped me find a solution! My PC uses and AMD Athlon at 900MHz (100x9) and the memory modules are PC133. I went into the BIOS and forced the memory to run at 100 instead of 133 and haven't had the 'hang' problem since.

---

