---
title: "ATI Dual Monitor/Big Desktop problem"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by durrell on 2008-12-05
I'm an experienced Linux user, but this is absolutely frustrating me to no end. In 8.04, I could not get dual monitors to work. I'd get the "white screen of death" every time. Looking back, I imagine it was a Compiz conflict. I have now updated to 8.10 and after removing all Compiz related packages have managed to get dual monitors set up correctly. However, I'd really like to use the "big desktop" feature. I can not get it working.

Basically, my setup is this:

2 Dell 1908FP 1280x1024 monitors
ATI Radeon 2400XT

Interestingly enough, with the ATI Catalyst Control Center the big desktop feature works fine. But there are two problems: one, it doesn't write to my xorg.conf so it just resets itself to clone upon reboot, and two, for some reason it randomly reboots my computer.

Any help would be greatly appreciated.

Thanks!

---

### Post by Victor Liu on 2008-12-29
For me, it would stay in big desktop mode at the login screen, and then once I logged in, it would go to clone mode. If this is the problem, make sure after you set Big Desktop mode in Catalyst control center, you then go to System > Preferences > Screen resolution, and set the resolution to the new "combined" resolution of the two monitors. For me, it was already selected, so just confirm it to save the settings. Next time you log in, it should stay in big desktop mode.

Not sure about the randomly rebooting problem though.

---

### Post by vlad_oz on 2009-06-04
I had the same problem as Victor Liu, and doing what he's recommended solved it. Just a couple of comments though (I'm using Ubuntu 8.04 and have ATI Radeon X600 video card):
1) Install the latest ATI driver applicable for your card first. You can get it from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) they also offer a "how to" PDF, follow that rather than various instructions found on the forums, you might have to proceed with the "manual installation" if "automatic" doesn't work. Restart after the driver has been installed.
2) After restart you should see ATI Catalyst Control Center and ATI Catalyst Control Center (super-user) in your Applications menu. I've used the "super-user" one. For me, once I've selected dual screen display from the Catalyst Control Center, the new resolution wasn't automatically selected, so I had to pick from System > Preferences > Screen resolution. If its not immediately obvious what to pick, go for the highest one, in my case its: 2560 x 1024, which is double width of the optimum resolution for each of my LCDs (I'm using two Dell 1907FPt 19" screens), i.e. 1280x1024 & 1280x1024.
3) Once the new resolution has been selected the screens may appear all jumbled up, so you can't see the "confirm new resolutions" dialog box. If you don't confirm, the resolution will revert back to what was previously selected. Even if you can't see the confirmation dialog, you can still hit the right arrow button and hit enter to confirm. The screen will still appear jumbled up, so restart X by pressing Ctrl+Alt+Backspace

---

