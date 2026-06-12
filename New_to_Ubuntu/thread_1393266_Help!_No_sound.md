---
title: "Help! No sound"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by kombipom on 2010-01-29
Hi

My man (kombipom) is away for the weekend and our system (mythtv) has no sound. It was working last night and I shut down as normal last night but tonight no sound :(

I have tried other applications other than myth and still nothing.  have rebooted - nothing, shut down and left it for 10 minutes - nothing. The amp is on and correct channel selected. The speaker icon at the top says output 100%. When I check the applications tab of the sound prefernces box with a program running on myth it says that no applications are running?

Any hints or tips for a non-ubuntu person? I am supposed to be having a girls night tomorrow with DVD's :(

Help me Obi Wan Kenobe, you're my only hope!

Kelly

---

### Post by audiomick on 2010-01-29
Check the simple stuff first; all the cables are plugged in, amp is really turned up and so on.

---

### Post by kombipom on 2010-01-29
Thanks Michael, all checked, all good - no sound :(

---

### Post by lijcam on 2010-01-29
One of the other basics to test is that they output is not muted. Has happened to me more then once.

Open the terminal (accessories >> terminal) and type ' alsamixer '.

To get you out of trouble unmute all outputs by pressing 'm' on each one. Mute is indicated by the MM while unmuted is indicated by 00.

If this fixes the problem these changes will be undone when you reboot again. It can only be saved with the root password using 'sudo alsactl <sound dev no>' eg sudo alsactl 0.

---

### Post by kombipom on 2010-01-29
Genius! Thanks Lijcam/Obiwan :KS

I have sound! And I know how to fix it next time

Thank you so, so much:D

---

