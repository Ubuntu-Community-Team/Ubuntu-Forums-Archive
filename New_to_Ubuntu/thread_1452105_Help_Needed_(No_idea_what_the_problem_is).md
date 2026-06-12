---
title: "Help Needed (No idea what the problem is)"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by lanetherif on 2010-04-11
Hi,

Today I re-installed the my video driver (Ati 4800 series), since I was having problems with compiz (It just stopped working). While restarting the PC, growing impatient and thinking that Ubuntu might have frozen, I hit the restart button. After salutation (I don`t know the exact term) screen which is also problematic (It is a kubuntu -which is not installed at the moment- splash screen with a 640*480 resolution, I was thinking about it much since I was able to reach gnome interface without a problem), I am face to face with a blue screen. There is starting sound of Ubuntu, but nothing else.

This thread might as well be suitable for 10.04, I am using it. However, at the moment I am really lost for ways to even identify the problem. 

Any help will be appreciated.

---

### Post by Silent Warrior on 2010-04-11
I'm just guessing here, but it really sounds like you rebooted while the kernel-modules were compiling. I don't think that's a good idea, but I also don't see why compilation wouldn't resume or retry on the next boot-up... Do you know the name of the driver-package you installed? (fglrx-something-or-other, I bet.) If so, I suggest you boot into recovery-mode (hold R-shift during start-up to get the menu) and choose 'root-prompt with networking' or something like it. Then just enter ...
```
sudo dpkg-reconfigure <name-of-driver-package-here> <type in the others on the same line>
```
... and reboot, unless you get some error-message. Then WAIT. :) I think that, if you press escape during the post-Grub graphical bit (it's moved to Plymouth now, right? No U-/Xsplash anymore?), you'll get text-output. If so, this will tell you what's going on, and whether there's a problem.
The kernel-module-compilation will only need to be done once, by the way.

---

### Post by lanetherif on 2010-04-11
> **Silent Warrior said:**
> I'm just guessing here, but it really sounds like you rebooted while the kernel-modules were compiling. I don't think that's a good idea, but I also don't see why compilation wouldn't resume or retry on the next boot-up... Do you know the name of the driver-package you installed? (fglrx-something-or-other, I bet.) If so, I suggest you boot into recovery-mode (hold R-shift during start-up to get the menu) and choose 'root-prompt with networking' or something like it. Then just enter ...
```
sudo dpkg-reconfigure <name-of-driver-package-here> <type in the others on the same line>
```... and reboot, unless you get some error-message. Then WAIT. :) I think that, if you press escape during the post-Grub graphical bit (it's moved to Plymouth now, right? No U-/Xsplash anymore?), you'll get text-output. If so, this will tell you what's going on, and whether there's a problem.
The kernel-module-compilation will only need to be done once, by the way.

I found the driver from hardware drivers. I don`t how the name goes. Here in live CD, under hardware drivers window, it goes like ATI/AMD proprietary FGLRX graphics driver. 
How should write it in recovery mode?

---

### Post by lanetherif on 2010-04-11
> **Silent Warrior said:**
> I'm just guessing here, but it really sounds like you rebooted while the kernel-modules were compiling. I don't think that's a good idea, but I also don't see why compilation wouldn't resume or retry on the next boot-up... Do you know the name of the driver-package you installed? (fglrx-something-or-other, I bet.) If so, I suggest you boot into recovery-mode (hold R-shift during start-up to get the menu) and choose 'root-prompt with networking' or something like it. Then just enter ...
```
sudo dpkg-reconfigure <name-of-driver-package-here> <type in the others on the same line>
```... and reboot, unless you get some error-message. Then WAIT. :) I think that, if you press escape during the post-Grub graphical bit (it's moved to Plymouth now, right? No U-/Xsplash anymore?), you'll get text-output. If so, this will tell you what's going on, and whether there's a problem.
The kernel-module-compilation will only need to be done once, by the way.

Thank you. Shift+R worked. Under the menu, I have chosen dkpg/dpkg/dkgp and let it repair what once is broken. :)
Despite the splash screen of Kubuntu, non-existence of a sound icon on top right, a compiz that can not be enabled and a Firefox that becomes unresponsive whenever a video is opened, I am happy to be login again. :P

---

