---
title: "Help! Blinking/multicolour screen at boot up"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by FarmerDaughter on 2009-07-18
Please help me. This is really bad... and I have no clue what is wrong. I logged out of my laptop running ubuntu 9.04 and I got a blank screen, so I shut down and restarted. Since then I only get the boot grub screen, the ubuntu loader and then a blinking screen with multi colours on it (where my user login screen used to show). Whats wrong? What did I do? Can I fix this? If so how?The laptop is brand new (1 week old, worked fine up to now) and was w/ vista (removed). I have a recovery and a drivers cd. In case it is important I uploaded themes before logging out, however I did not make any changes to the human theme. Thank you!

---

### Post by soumo on 2009-07-18
Sounds similar to a problem I had; my probs were hardware related though requiring sending it in.

1st I suggest you try using any external device, eg. s-video or vga cables to your tv and reboot to see if those work ok.

If you don't have those, you can try booting with your ubuntu cd to see how far you get.

If any of those are okay then at least it doesn't sound like a hardware issue.

Do you see any flickering, scan lines or dots?

Also if you can see the boot grub loader, that does not necessarily mean it's NOT a hardware problem.

I'm not sure what other help I could suggest so I won't check back on this thread.  But do PM if any of this seems to get you anywhere and I'll look further.

Other generic advice: 
-if you can pull your drive and start in another computer okay then it's not your OS
-if you can put another harddrive in your computer and it boots okay, then it prolly is your OS

But hopefully someone else will help you with some easier troubleshooting tips.
it might be helpful for you to post system specs, ie. RAM, video card etc.

Best of luck!

---

### Post by ajgreeny on 2009-07-18
It sounds like a graphics driver problem to me.  Did you do an update before the reboot, as it may be that you can simply re-install your drivers.

Alternatively try booting the live CD to see if that still works, and if so reboot in recovery mode (second choice in grub) and then choose xfix when you get to the menu.  When that had done its good deeds, hopefully you may be able to boot again to the GUI.

---

