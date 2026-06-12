---
title: "Install issues"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by nhguy78 on 2010-04-25
I am REALLY new to Ubuntu.  I am so new that I don't even know what Ubuntu can do.  I am still stuck trying to install.

I am attempting it on an AMD K6.  I was having problems wiping the drive (it wouldn't allow me to boot from CD - would always load Windows).  That was successfully finished but now trying to install.  So when the install initiates, it starts, Ubuntu logo comes up and soon the computer completely powers off as if power plug pulled.  I've tried Ubuntu.  I've tried Kubuntu.  Just today I tried Xubuntu.

I wonder if the computer is powerful enough but I've read elsewhere that it shouldn't be an issue.  Previously I've had XP Professional on it.  Windows loads perfectly fine.  So I don't know what to try next or what to rule out.

---

### Post by QIII on 2010-04-25
If you are using a LiveCD you downloaded, try two checks first:

Check to see that the md5sum is correct for the .iso file that you downloaded.  That will tell you whether the .iso file is corrupt or not.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the hash is not correct, download the .iso again.

If it is and you are using a LiveCD, boot to the LiveCD.  Select "Check disk for errors" (or similar).

If that gives you errors, re-burn the disk at the slowest possible rate your burner allows.

If all of that works, try running Ubuntu in a Live session by clicking "Try Ubuntu without making changes to your hard drive" (or similar).

Let us know how all of that goes.

We may also want to take a look at your graphics card and go with the "Alternate install" disk to get around any initial problems you may have with video.

---

### Post by nhguy78 on 2010-05-10
Ok, I think I've got it... not Ubuntu but Xubuntu - the most recent with all updates.  Everything works...finally.  Well, except one thing (might be a weird power setting).  If the lid is closed for any length of time, the screen goes off and does not come back on.  Like I said before it's a really old laptop so...  it could be hardware related.

---

### Post by Don1500 on 2010-05-11
> **nhguy78 said:**
> Ok, I think I've got it... not Ubuntu but Xubuntu - the most recent with all updates.  Everything works...finally.  Well, except one thing (might be a weird power setting).  If the lid is closed for any length of time, the screen goes off and does not come back on.  Like I said before it's a really old laptop so...  it could be hardware related.

When you start up again after closing the lid, do all the programs and files come back without you asking? Closing the lid on a laptop can be set to do just that, turn off completly and remember your settings. It can also be set to go to Stand-by, not completely off, comes back when you open the lid.

---

### Post by nhguy78 on 2010-05-11
> **Don1500 said:**
> When you start up again after closing the lid, do all the programs and files come back without you asking? Closing the lid on a laptop can be set to do just that, turn off completly and remember your settings. It can also be set to go to Stand-by, not completely off, comes back when you open the lid.

Thank you for your help.  The laptop is running on AC power only
and I have all the power management options turned off.

No, if I reboot because I closed the lid(don't do that on purpose any more ;-) ) the system just reboot normally and I log in with everything starting fresh, nothing is saved as a left it(no open programs Etc.).  

I will triple check the monitor/power settings again.  I just want the monitor when closed to do nothing other then not be powered on(displaying anything).  

The standard option is when you close your laptop screen is for the laptop monitor to turn off(no need for it to be on if no one can see it(like the light in your refrigerator), well I close the lid it shuts off...normal but when I open it even a second later the screen is blank and nothing has gone into suspend or hibernate modes. The system is still running doing what it was before the screen was closed just with no image on the screen and nothing I do will turn it back on other then restarting the system.  If I start the system them close the monitor the same thing happens once Gnome loads.  

HOWEVER, something that I think is interesting....
AFTER a normal shutdown at the text screen I can open and close the monitor and it will go off and on as it should.  

Such an odd problem.... but I hate to A. turn off the system or B. leave the monitor open for no reason other then knowing it will not come on again if I don't or unless I re-boot.

Thanks for all your help :-)

---

### Post by n2bnt2 on 2010-05-18
Dunno the answer, but here are some thoughts...

Does suspend and or hibernate work on this system? Might be good to know if they work.

What is the video hardware on this laptop?

---

