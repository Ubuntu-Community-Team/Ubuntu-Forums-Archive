---
title: "HOWTO: Configure gnome-ppp to work with a Verizon xv6700"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by fefniir on 2006-12-28
I'm not to good at intros, so I'll get right to the point.

1. From the starting screen fill the Username and Password with whatever you feel like putting there. I just typed in "none" for both, though you might want to check the remember password button.

2. In the Phone number box enter DT#777

3. Click on the setup button and start off on the Modem tab

4. Device: type in the path to your xv6700 when it's in tethered mode, mine is /dev/ttyUSB0. Yours might be different. Don't hit the Detect button, it suffers the same problem as wvdialconfig and will segfault if you try to use it.

5. Type: Make sure you have ISDN Modem selected from the drop-down menu. This sets the dial command to AT. When gnome-ppp combines that with the phone number you entered previously you get the correct command of ATDT#777.

6. Goto the Options tab and make sure the Ignore terminal strings (Stupid Mode) is checked.

7. Click on close and you should be all ready to go.

Hope this helps someone.
If there's any problem, questions, or if there's something important that I forgot, let me know.

---

