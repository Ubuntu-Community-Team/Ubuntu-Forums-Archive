---
title: "installation boot failure"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by mainegate on 2011-04-23
I have an old Sony Vaio with Windows XP on it. I downloaded the Ubuntu 10.10 desktop i386.iso and started to install. I told the installer that I wanted to delete everything and only have Ubuntu be the only thing on the drive. 

Towards the end of the installation it said there was a failure. I cannot think of the exact language but it was that It could not save something "bootable"...I think the thing that tells it what to do when you start the computer. There were options to save it to different locations (it even said Windows XP as an option...weird because I told it to delete Windows). I tried all the options but it said it couldn't save it. After nothing worked I told it to cancel the installation.

Now when I turn the computer on it doesn't go back to the installation (even though the disk is in) and when it is not in there is just a black screen with a white solid cursor. That is it. 

How do I remove everything from the drive and install just Ubuntu?

---

### Post by oldfred on 2011-04-23
Welcome to the forums.

Does you BIOS have a locked down MBR?
Some users have posted these as the issues on some computers, not sure about your Sony.
BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 

Did you try running the LiveCD in liveCD mode to make sure it worked ok on your computer? Many computers now seem to have video issues. Which just need a parameter to boot. 

But you still should be able to choose the CD as first to boot in BIOS or from one time boot key. Is that how you are selecting which device to boot?

---

