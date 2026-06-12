---
title: "help with hangups"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by need2no on 2009-07-14
I'm new to Ubuntu and just installed Ubuntu-9.04-desktop onto my old Dell as the only OS. All went well, checked out what was there - no problems - tried to shutdown from the username in the upper right corner and it seemed to be shutting down but stopped on a black screen with a line saying:   [3185.549436] system halted
on the next line is what looks like a DOS prompt.

I tried the control-alt-backspace and  alt-printscreen R E I S U B  that I found in the help sections but get no response (nothing types at the prompt).  My computer is hanging there. Any advice?

---

### Post by doas777 on 2009-07-14
well it sounds like it's already shut down from a soft perspective,so  just hit the power button to power it off. none of the x-commands work because x is no longer running. a system halt is basically shutdown (the halt command shuts you down). nothing is running even though the power is still engaged.

are there any lines above the "[3185.549436] system halted"? they may be the clue as to why the hardware did not realize that the OS had unbooted.

---

### Post by need2no on 2009-07-14
There are no other lines above.  Thanks for the info - it does look like the old DOS shutdown now that you mention it.

---

