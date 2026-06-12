---
title: "GLX Dock and ATI"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by farkinid on 2010-03-08
Hi guys,

I've been using Ubuntu for the last couple of months now and have become quite comfortable with it. However, I'm encountering an issue which no amount of google-ing seems to solve.

_Problem_
I have installed glx-dock (cairo-dock) and I have a black background behind the dock. This blocks my windows. After research, I've found that this is because I'm using ATI proprietary drivers for my Radeon HD4200.

_Workarounds_
So far I've used the dock's options to hide the problem but its not good enough because now my windows blocks the dock.

_Solutions and problems_
The way I see it, I have 2 options. The 1st is uninstall the proprietary drivers and go with open source drivers. However, I can't find a step-by-step guide on how to go about this. Can somebody please point out a guide or maybe give me directions on how to uninstall the proprietary drivers and install the open source ones?

My 2nd option would be to update the proprietary drivers. To install the proprietary drivers initially, I simply used System -> Hardware Drivers -> selected the card. (This is a simplified explanation)

When I downloaded the latest .run file from AMD and ran dpkg, I somehow disabled all my video drivers. After tinkering around I managed the get my proprietary drivers running again but I'm back at square 1.

_Summary_
Need guide to uninstall proprietary and install open source drivers. Also welcome suggestions on how to handle glx-dock

---

### Post by Mark Phelps on 2010-03-09
See instructions in the link below for removing the proprietary drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

