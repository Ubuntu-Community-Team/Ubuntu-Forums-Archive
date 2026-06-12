---
title: "Dual Monitor Question"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by JavaKid on 2011-07-04
I'm new to Ubuntu.  

I've just installed Desktop 11.04 on a machine with two ATI Radeon 5870 video cards and each have a monitor plugged into them.  They are identical monitors purchased at the same time.  I would like to get the second one working. 

I searched to see if anyone else had this issue and could not find an answer.

In my System Settings - Control Panel - Monitor Preferences it has one listing of:
[HTML]<p> Samsung Electric Company 7" </p>[/HTML]

I've clicked the 'Detect Monitors' button but only the one listing persist.

Any help would be appreciated.

Steve

---

### Post by alphacrucis2 on 2011-07-04
> **JavaKid said:**
> I'm new to Ubuntu.  

I've just installed Desktop 11.04 on a machine with two ATI Radeon 5870 video cards and each have a monitor plugged into them.  They are identical monitors purchased at the same time.  I would like to get the second one working. 

I searched to see if anyone else had this issue and could not find an answer.

In my System Settings - Control Panel - Monitor Preferences it has one listing of:
[HTML]<p> Samsung Electric Company 7" </p>[/HTML]

I've clicked the 'Detect Monitors' button but only the one listing persist.

Any help would be appreciated.

Steve

Install the Catalyst driver.

---

### Post by seawolf167 on 2011-07-06
You'll want to install drivers for your system then adjust their settings. You have two choices
1. You can use the drivers available from the Additional Drivers (System -> Administration -> Hardware Drivers, or on 11.04, click the power button in the upper right, select System Settings, then Additional Drivers)
2. You can install the [proprietary drivers suite ]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")from ATI. I recommend this option since you are running two in crossfire [assumingly], as you should have a little more customization options.

---

