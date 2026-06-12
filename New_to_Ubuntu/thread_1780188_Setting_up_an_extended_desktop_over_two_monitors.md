---
title: "Setting up an extended desktop over two monitors"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Statesman83 on 2011-06-11
I am having trouble setting up an extended desktop over two monitors (one is a laptop screen, the other is a CRT) in Ubuntu 11.04.

The Monitor Preferences screen identifies them both but, despite de-selecting  "Same image in all all monitors," both screens show the same screen. I have tried using an application, such as "Multiple Monitors," both the "Clone and Extended" screen selections are grayed out.

Any suggestions?

---

### Post by VOT Productions on 2011-06-11
What is your video card?

---

### Post by corncob on 2011-06-11
Is there anything applicable under System > Hardware > Additional Drivers you could install or activate?

---

### Post by Statesman83 on 2011-06-12
VOT Productions:  I have an ATI Radeon (TM)  HD 3200 Graphics card. It is capable of using an extended desktop with two monitors, since this works in Windows Vista.

Corncob: No, I'm afraid there is nothing under "Additional Drivers" in addition to what has already been installed.

---

### Post by bg4m3r on 2011-06-18
I'm having similar issues. Do you have the Catalyst drivers installed? They should show up under the additional drivers control. This will let you at least do the extended desktop, however, I haven't been able to get anything to cooperate. It wants to make my 2nd monitor my primary monitor, and I can't find a way to swap them. Maybe I'll try the apps you listed here and see if those help.

The monitor I WANT to be the primary is connected via DVI, the other is connected via HDMI, which I think may be part of the problem.

---

### Post by Statesman83 on 2011-06-18
Acutally, I do have the Catalyst control drivers installed and I was able to get the extended desktop to work.

To do so, open "ATI Catalyst Control Center", with the second monitor attached, and click on Display Manager. It should be able to detect both monitors and ask to reset for optimal performance. Although the screens will not yet be extended, after you restart your computer, they should be.

Sorry to hear that you are having problems, bg4m3r. Afraid I am anything but a programmer, so I can only offer sympathy, but hopefully you can get your problem resolved soon!

---

