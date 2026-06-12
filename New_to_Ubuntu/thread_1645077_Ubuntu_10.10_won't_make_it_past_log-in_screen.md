---
title: "Ubuntu 10.10 won't make it past log-in screen"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by eatsleepfolk on 2010-12-14
Hello all,

I'm new to linux/ubuntu in general and just began dual-booting 10.04 on my Windows 7 machine. Everything was working fine until I tried to update Ubuntu to 10.10 via the update-manager -d method. Now, when I boot Ubuntu and log-in the screen simply freezes on the default purple wallpaper. No keyboard shortcuts produce anything. Any idea what is causing this and what I can do to fix it?

---

### Post by jkhh07 on 2011-01-03
Yea I got the same problem. Just installed Ubuntu 10.10 from CD on my desktop. This was about a week ago and I believe the initial logon froze after clicking on username and expecting to be logged in. No response from keyboard. Mouse moves around but doesn't do anything when clicking. Cannot switch to VT1. I power cycled the box and logged in with no issues at all right after that. I immediately went to the update manager and updated the default selections and then left for the day. I come back after the new year and monitor is sleeping, computer is on, keyboard has all 'lock' keys on but regardless of keyboard or mouse movement it did not wake up and the monitor kept sleeping. I Kept clicking and pushing buttons for about 5 or 6 minutes, then powered it off once I realized I wasn't getting anywhere. Powered it back on - same exact issue. Freezes after clicking on username to login. Sometimes it gets within 3 - 4 seconds before or after allowing.

Only thing I can get out of it is where after it looks to be frozen, I reseat the mouse cable, and the mouse gets power but no longer moves on the screen.

Driver issue causing the system to lock up?

---

### Post by jkhh07 on 2011-01-04
Alright o right now I have booted in recovery mode kernel 2.6.35-24 from the grub menu. Then chose to run in failsafe mode. An error popped up saying that the system had to be run in low graphics mode. It then gave me a multiple choice box to continue running in low graphics mode or troubleshoot the error. I chose just to continue. Running the system in this mode seemed to immediatley alleviate the problem so far and I am assuming the drivers the system was using for the display is probably part of the problem. I'm going to focus on the graphics issue for now.

---

