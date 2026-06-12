---
title: "Will this work?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by RazzyDaz on 2009-12-16
Hello....
   I am trying to accomplish a few things, one of them is to update my bios.  Long story short, spyware took over my computer and killed Vista.  I am no longer able to boot from CD or load into Vista.  I can only load via safe mode.  Lately, I have been using Ubuntu on an older computer and would like to use it on my screwed up Vista machine.  I was able to load 9.04 Wubi, via safe mode.  
    What I would like to do is to update my bios, so I'm able to boot a LiveCD.  Is there a way through the terminal to do this.  I have the zip file, but I'm unsure where to place it.  Also, is there a way to fully install 9.10 over Wubi?  I would love to kill Vista and only use Ubuntu.  

Thanks for helping a newbie :)

---

### Post by laidback on 2009-12-16
Unless your PC is particularly old I would suggest that you will be able to boot from the Live CD, but you might need to alter the boot sequence within the bios. Enter the bios at boot up (normally by pressing Esc, or Del or similar, it'll tell you on the boot screen if you're quick enough to read it) then find the section that describes the boot sequence. You may currently have HD (hard-disc) as your first option and CD/DVD as your second. Switch it so that CD/DVD becomes first and the HD becomes second. Save and exit the bios.

Now put the Live CD in the drive and reboot, Ubuntu will load in preference to the OS on your HD (Vista). When there's nothing in the CD drive it'll boot from the HD.

---

