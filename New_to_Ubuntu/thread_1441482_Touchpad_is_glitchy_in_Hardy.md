---
title: "Touchpad is glitchy in Hardy"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by brettadams1989 on 2010-03-28
I'm new to Ubuntu/Linux. Installed about a week ago and have been having touchpad issues ever since.

At seemingly random intervals the cursor jumps around and the touchpad will stop responding to clicks. I can still move the cursor around onscreen, just not click, select, etc.

Errors for when the cursor jumps around look something like this in Log Viewer:

```
Mar 28 16:14:01 badams006-laptop kernel: [  842.162594] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Mar 28 16:14:01 badams006-laptop kernel: [  842.164076] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Mar 28 16:14:01 badams006-laptop kernel: [  842.194173] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Mar 28 16:14:01 badams006-laptop kernel: [  842.197693] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Mar 28 16:14:01 badams006-laptop kernel: [  842.197698] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Mar 28 16:14:01 badams006-laptop kernel: [  842.197701] psmouse.c: issuing reconnect request
```

I can't post results for when the mouse completely fails, for obvious reasons.

I've searched through some fixes, but most of them leave me completely confused or lost.

The few that I have tried to implement haven't worked so far.

If there is a fix, and I'm sure there is, could someone explain how to correct the issue in complete newbie terms?

---

### Post by brettadams1989 on 2010-03-28
Also note that the touchpad worked fine in XP, so it isn't broken.

---

### Post by nemilar on 2010-03-28
What make/model laptop?

---

