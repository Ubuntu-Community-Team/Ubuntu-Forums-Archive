---
title: "Problem changing screen resolution on Dell Dimension B110"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by StevenBrown on 2011-03-01
I installed Ubuntu on my Dell Dimension B110 desktop computer, and it is running fine with 1280 x 1024 screen resolution. However, I want to use 1024 x 768 screen resolution. When I switch to that resolution, the top three inches of the screen appear twice, pushing the bottom of the screen down out of sight. I am afraid to make it the default resolution, because if it boots with this same problem, I may not be able to change it back to the resolution that was working.
 
The monitor hardware ID is "DELA014". It is a 17-inch flat panel display. The graphics controller is "Intel 82865G." In Windows, it uses the Microsoft plug-and-play driver; no Dell driver is installed, and the monitor works ok. 
 
Any help will be appreciated.

---

### Post by vivek.pandey on 2011-03-01
on terminal  type xrandr and see whether the resoltuion you wanna change to is there in the list or not
xrandr tells the allowed resolutions

---

### Post by StevenBrown on 2011-03-01
xrandr reports that 1024 x 768 is a supported screen resolution. The problem is that the top three inches of the screen appear twice, first as a band across the top of the screen, and under that is the normal screen. The bottom of the screen is pushed down out of view. No one else has experience this problem? I find it hard to believe it is unique to my computer.
 
What if I ignore the problem and select "make as default" instead of "apply"? If the problem is still there when I reboot, and I can't access the dialog box or menu to switch the resolution back to 1280 x 1024, is there any other way I can switch the resolution?

---

