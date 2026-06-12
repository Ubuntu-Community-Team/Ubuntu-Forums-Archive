---
title: "Won't Restart Without Hard Reset"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by PaulWi on 2009-02-01
Just successfully installed 8.04.2.
My (previously XP) machine with a S3 Graphics ProSavageDDR video card which has no linux driver.  So I can only run in 800x600 mode.  Also, when Ubuntu needs to restart (I click restart or it installed updates etc.) and I click OK it blanks the screen but doesn't restart.  I have to press the physical restart button.

Q1 - Is there any way to increase the resolution?
Q2 - Why can't Ubuntu restart the computer automatically?

Thanks.
PS - If you're wondering, yes, I just created a new forum account for myself since I naively used my email address for the last account I set up.

---

### Post by Crafty Kisses on 2009-02-01
Does it restart if you run the following command?```
sudo shutdown -r now
```

---

### Post by DougieFresh4U on 2009-02-01
I can not really answer both your questions, but I can offer you some advice. As you probly know, hard resets are not good for hard drive and also I believe that after updating and a restart is called for, your updates won't be properly installed by doing a 'hard restart, (so I have been told)
I would suggest restarting from terminal or maybe restarting by System>Log out and when login screen appears select options and then select restart. Not sure if you are running Intrepid, but there was an issue at one time where restart wasn't working correctly until they fixed with update.
Sorry I couldn't be of much help

EDIT: terminal
```
sudo restart
```
and machine will reboot

---

### Post by egalvan on 2009-02-02
> **DougieFresh4U said:**
> I can not really answer both your questions, but I can offer you some advice. As you probly know, hard resets are not good for hard drive and also I believe that** after updating and a restart is called for, your updates won't be properly installed by doing a 'hard restart,** (so I have been told)

EDIT: terminal
```
sudo restart
```
and machine will reboot

Absolutley NOT true, a 'restart' is merely a short version of a reset.
More is done, not less.
It does take more time.
It can invoke an 'fsck' check.
It can delete temp caches.
It cannot fail to properly install updates.

ErnestG

---

### Post by PaulWi on 2009-02-02
So I've tried each of the following and here are the results:

"Switch User" - screen goes blank.  Power is on.  I have to hard reset (button).

Using "terminal":
sudo shutdown -r now   
   Screen goes blank.  Power is on.  Have to hard reset (button.
sudo restart
   "Command not found"


Using GUI interface:
**_Log out _**- Screen goes blank. Power is on.  Have to hard reset.
**_Screen lock _**- I can enter password and get back to GUI.
**_Switch User _**- Screen goes blank. Power is on.  Have to hard reset.
**_Hybernate _** - Same as above.
**_Restart_** - Same as above.
**_Shutdown _**- Same as above.

Given the off and on squeeling sounds from my monitor, I believe these problems have to do with the fact that I can't run resolutions above 800x600.  My video card (S3 Graphics ProSavage DDR) doesn't seem to have a linux driver.  This caused me to fail at getting Ubuntu 8.10 running at all.  Now with 8.04 running it is only in 800x600 mode.  S3Graphics.com has some linux drivers but not for this specific card.  I've emailed them asking if a driver is availble.  No response.

Should I buy a new video card?  (Yucky investing in an old machine)
Other tips?

Thanks.  (beginner, newbie, greenhorn, etc.)

---

### Post by sydbat on 2009-02-02
Your monitor shouldn't be making any sound. Are you sure it is not your hard drive? Perhaps it is failing and that is causing the shutdown problems.

---

### Post by PaulWi on 2009-02-02
The squeal is coming from the monitor alright.  It's the familar click-squeel you get when changing resolutions.  But the squeal doesn't go away. 
Now I've made things worse.  After playing with the "Screens and Graphics" (per Mr. Kellemora) I've now created a machine that won't boot at all beyond the "Ubuntu is running in low graphics mode" during bootup and offering me "Configuration", "Reboot" or "Continue".  "Configuration" provides the "Screens and Graphics" screen (with "Screen" and "Driver" tabs).  "Continue" get's a blank screen (I must have selected an incorrect screen/driver previously.)

I can't get past here now because I can't figure out what my graphics card and monitor's settings should be.  And clearly I can't remember what Ubuntu set them to when I first installed which at least allowed the 600x800 resolution.  ("Detect" results in "plug-n-play" which also results in a blank screen.) 

Hmmmmmmmmm. Any more ideas?:(

When I the "Screens and Graphics" configuration.  Once I've selected a something there (Monitor / )

---

### Post by PaulWi on 2009-02-05
Partial Resolution!!
I lied to the Screens and Graphics configuration.  I couldn't find any information on the web regarding my Sceptre CRT monitor Model Q766DU.  I learned that Sceptre also made Komodo CRT monitors.  I selected Komodo as the "Screen" in "Screens and Graphics".  Now I get multiple resolution selections.  Great.

But I still get the blank screen problems described above when Resetting, Shutting down, or Switch Users.  All of the functions result in a blank screen with the power still on.  My only recourse is to press the hard reset button on the CPU.

Thoughts?

---

