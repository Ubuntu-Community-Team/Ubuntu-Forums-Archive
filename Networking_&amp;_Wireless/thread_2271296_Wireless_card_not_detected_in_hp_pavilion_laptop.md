---
title: "Wireless card not detected in hp pavilion laptop"
date: 2015-03-29
forum: Networking &amp; Wireless
---

### Post by justin45 on 2015-03-29
I have an hp laptop pavilion dv2500. I have ubuntu linux 14.04 64 bit version installed on the laptop. Even though the laptop has a wireless card installed, ubuntu does detect the wireless card, but the card doesn't show up in the networking icon in the upper right hand corner. If I boot into linux, I get a black screen so I boot off of the install cd, choose the nomodeset option and then I can do whatever I need to do. I have a 
broadcom corporaton: bcm4311 802.11b/g wireless lan controller
and a
nvidia corporation:c6 [geforce 7150m/nforce 630m] video card

I'm probably missing things. I'd like to work on the wireless issue first before working on the video card issue.

---

### Post by maclenin on 2015-03-29
**justin45!**

These should help:

1. Black screen - have you tried pressing "Shift" at start-up to access the grub menu / activate nomodeset without the "install cd"?
 
2. Video driver - I would look at [option 1]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and [option 2]("http://askubuntu.com/questions/377205/how-to-find-out-what-graphics-driver-is-installed") to find a video driver that suits.

3. Wireless driver - As described in "option 1", above - navigate to the "Additional Drivers" dialog where you should be able to activate the "Broadcom STA wireless driver".

After completing steps 2. and 3. you should be good to re-boot - with video and wirelessly (and without the "install cd")!

Good luck!

---

### Post by justin45 on 2015-03-29
If I hold down the shift key at startup, I get the grub menu, but there is no nomodeset option listed.

---

### Post by Vladlenin5000 on 2015-03-29
> **justin45 said:**
> If I hold down the shift key at startup, I get the grub menu, but there is no nomodeset option listed.

You need to add that option, ie, you need to edit the whatever Ubuntu entry you boot from and add *nomodeset* instead of or along with the other options like *quiet splash*, etc.

---

### Post by justin45 on 2015-03-29
I googled in and found instructions on this website about how to set nomodeset and other kernel boot options in grub2 so I'll go through the steps and see what happens and I'll report back here and let anyone know if I need any additional help.

---

### Post by justin45 on 2015-03-29
After spending some time with my issue, I'm not any closer to solving the issue.

For black screen issue, If I type in a terminal,
Gksudo gedit /etc/default/grub
the command says that the program gksudo isn't installed, but if I type in 
Sudo apt - get install gksu, the command can't find the gksu package.

Further information on google says that gksu isn't included in version 14.04 of ubuntu linux

For video driver issue, what am I looking for in the list of video drivers?

If I put the ubuntu linux install disc in my laptop, use the nomodeset option and go to the additional drivers section, there is one driver for the wireless card which isn't the right one and about three for the video card, non of which seem to work.

I appreciate the help so far.

---

### Post by maclenin on 2015-03-30
**justin45!**

Take a peek [here]("http://ubuntuforums.org/showthread.php?t=2259849") - and go to step 12. (through 16.) - it may help re: nomodeset. After you "Shift" into the grub menu, you'll be highlighting "*Ubuntu" (probably the top and already highlighted option) rather than "*Try Xubuntu without installing".... NB: Take note of the settings you modify, before you modify them - so you can restore them, if something does not work properly.

Assuming success with nomodeset, you should then be able to continue with steps 2. (video) and 3. (wireless) from my original reply.

Again, good luck!

---

### Post by justin45 on 2015-03-30
After doing a lot of reading and some trial and error, I don't think that it's possible to solve my issue using only another wireless connection.

I do have the correct files to be installed for both my video card and my wireless card.

Using a wired connection, what would I do to install the correct drivers for both my video card and my wireless card?

---

### Post by maclenin on 2015-03-31
**justin45!**

EDIT: It looks like you have modified your reply re: the .run experiment. To answer your latest question re: wired connection - keep your laptop wired to the internet until you have completed all phases (driver activation / software updates / etc) of the ubuntu install - and the system has been rebooted and is up and running properly. Install the video and wireless drivers exactly as I've suggested.

I HIGHLY recommend using the ubuntu-supported / tested steps I refer to in my original reply to address the video card driver issue:
 
> **maclenin said:**
> 2. Video driver - I would look at [option 1]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and [option 2]("http://askubuntu.com/questions/377205/how-to-find-out-what-graphics-driver-is-installed") to find a video driver that suits.

You should still have access to the "Additional Drivers" dialog - via recovery mode. Use it (as described in "option 1" and "option 2") to install BOTH the video and wireless drivers.

I would also give a go to completely removing the nvidia .run files from your system - see [uninstall 1]("http://askubuntu.com/questions/219942/how-to-uninstall-manually-installed-nvidia-drivers") and [uninstall 2]("http://unix.stackexchange.com/questions/112077/uninstalling-run-file") - though the quickest (and surest) way to do this might be to re-install ubuntu (and give the grub / nomodeset route another try).

In my experience, the range of [software options]("https://help.ubuntu.com/community/InstallingSoftware") provided within the ubuntu "package" is generally more than ample to address any issues I have ever had with my system. Only as a last resort do I venture (or .run) beyond to fix or modify - and then - very carefully....

---

### Post by justin45 on 2015-04-02
It turned out that I was doing things the hard way. Using a wired internet connection, I installed both the wireless card driver and the recommened video card driver so I'l good to go and my issue is solved.

I learned a lot from how to solve this issue. I want to thank everyone that helped me out. Now I know the informaton for myself.

---

### Post by maclenin on 2015-04-03
**justin45!**

Doing things the hard way leads to extra learning - time well spent - and glad to hear you've solved the riddle! 

Assuming all is resolved - make sure you mark your thread as [SOLVED]  - via "Thread Tools" - so that others can easily locate and learn from your experience.

---

