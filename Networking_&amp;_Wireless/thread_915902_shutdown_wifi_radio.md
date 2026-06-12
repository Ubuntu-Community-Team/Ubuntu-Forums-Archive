---
title: "shutdown wifi radio"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by whauser on 2008-09-10
Hi all,
I'm running the latest LTS release of Ubuntu on a Toshiba A135-S2386.  It's not the most linux compatible machine but I've been using Ubuntu succesfully for over a year now. 

Anyhow, the battery life is not so great - maybe an hour and a half.  Running powertop indicates that the computer is virtually always active because the darn wifi radio is constantly causing it to wake up.  I've shutdown the polling of the dvd drive per powertop's recomendation - though I must warn you that allowing *powertop* to shutdown the polling for you screws something up and makes the drive unusable/unmountable.  If I tried to re-enable polling in the terminal then I'd get the message that polling was already enabled on that drive. I finally fixed the problem by disabling polling using the disable command and then re-enabling it (got it back to normal) and then I disabled it using the disable command in terminal - no longer polls or automounts but the drive can now be manually mounted.  Looks like a bug in the powertop program but that's a separate issue.

The big problem still is that I can't kill the wifi radio.  I've got a kill switch on the front of the laptop but ubuntu doesn't recognize this switch.  On or off the wifi stays on.  I can uncheck the "enable wireless" option in network manager and that disconnects me from the internet but the wifi radio stays on (the number of wifi interrups displayed in powertop does not decrease).

So, how the heck to I turn off the wifi radio?  It's killing my battery.

---

