---
title: "terminal session - left margin problem"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by ProntoAnthony on 2010-10-24
With other forum members' help, yesterday I adjusted the screen resolution of the Control-Alt-Fn terminal sessions to a higher resolution (640x480 to 1280x1024) to better suit my monitor.

One unexpected outcome is that I had to adjust my monitor's  geometry to position the visible screen to the right in order that the first 2 characters of each line of terminal sessions are visible. The left margin, if you will.

The result is the GUI gnome screen is also shifted to the right, effectively cutting off the last 2 characters. The right margin. It seems to me the Ubuntu GUI and non-GUI screen geometry is out of sync.

The TERM variable is set to linux on these virtual terminal sessions.

The Gnome terminal sessions are fine. Their TERM is xterm.

I'm running 64bit Lucid LTS on a Dell system with a Dell E177FPmonitor and nVidia GeForce 6150 LE graphics card.

I'm not sure how to view the driver version number for the card.

Thanks for your help.

---

### Post by ProntoAnthony on 2010-10-24
I reset my monitor to factory defaults and upgraded to GeForce drivers list in the Software Center and nothing has changed.

---

### Post by ProntoAnthony on 2010-10-24
This is puzzling, but it seems to have resolved the GUI/non-GUI screen position conflict.

I went into the nvidia X server settings and changed the gui screen resolution from 1280x1024 to 1152x864. Strange. Is this the only fix?

By the way,the vbeinfo command doesn't even list 1152x864 as an optional resolution. This is very strange.

---

