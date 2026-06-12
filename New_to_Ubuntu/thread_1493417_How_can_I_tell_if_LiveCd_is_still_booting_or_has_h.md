---
title: "How can I tell if LiveCd is still booting or has hung?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by NUboon2Age on 2010-05-25
While booting I got that standard error that I think everyone booting from the CD gets about getpwuid failing. That one doesn't concern me, but I also lost the splash screen that at least has the activity indicator.  The HD and CD activity lights went off and its just got a screen with the error message I described above on a black background. The screen saver is still working giving a blank screen and I can bring it back to the black background w/ error message by hitting a key or touching the touch pad.  I can't tell if its still working on booting up. Is there any way to pull up the splash screen back up or other way to tell if its hung or still trying to boot up?

---

### Post by Ozymandias_117 on 2010-05-25
If you see the getpwuid error, you should already be in verbose mode. So if it does anything, it will tell you. (Note mine stayed on that error for about 2 minutes before moving on)

---

### Post by NUboon2Age on 2010-05-25
> **Ozymandias_117 said:**
> I believe pressing esc will put it in verbose mode, that way you can see if it's moving anywhere.

Thank you, That's the kind of thing I was wondering about...
Hmmm.... I tried hitting esc but it didn't change anything.

---

### Post by Ozymandias_117 on 2010-05-25
Yeah, sorry, That's why I edited it :P The fact that you're seeing the error means you're already in verbose mode.

---

### Post by NUboon2Age on 2010-05-26
I rebooted w/ (ubuntu-derived) PeppermintOS and found that different combos of cntl/alt and esc, F1, F2, and F7 brought up different modes, including bringing the splash screen back up.

So I still don't know the answer to my original question, whether my machine is hanging on bootup with the livecD, but I at least have some more things to try.  If anyone has some more specific info on which modes correspond w/ which key combos in Ubuntu, please chime in.

---

### Post by Peter09 on 2010-05-26
When you first see the splash screen hit any key. That should give you a menu which allows you to set / unset some boot parameters.

---

### Post by NUboon2Age on 2010-05-31
According to another thread:

Cntl+ Alt+ "f1-6 are tty, f7 will bring you to the GUI again."

---

