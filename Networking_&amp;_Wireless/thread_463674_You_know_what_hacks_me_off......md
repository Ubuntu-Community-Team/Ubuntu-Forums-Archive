---
title: "You know what hacks me off....."
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-06-03
Ok first of all -- there is no mention that installing the bcm43xx drivers for broadcom rev03 cards results in only transmission rates of 11Mb/s.  Im not sure why this was never discussed but that stinks.

Anyway -- in order to rectify the problem I spent all day uninstalling the bcm43xx drivers (remanants were all over the system even after using aptitude to uninstall the package), uninstalling ndiswrapper packages (again remnants all over the system), downloading ndiswrapper from svn, compiling from source, installing both ndiswrapper and wpa_supplicant, and then learning how to configure for WPA.

Seriously I know many users of the forums probably have done this, but in order to get a working configuration it was a 6-7 hour b**ch!!

Seriously Im trying to talk to my friends about how good ubuntu is, but in my opinion any novice trying to make the switch from windows would have said SCREW IT about 10 minutes into the process.

The tutorials on this forum helped, however the best source for configuring ndiswrapper came directly from their website, particularly consulting the section troubleshooting.  Why there were so many different version of ndiswrapper still in the system after removal is beyond me, but this really screwed things up.

Im hoping Gusty will attempt to filx most of the problems with this wireless fiasco.  As you can see from this networking and wireless section there are many posts stating "Can get wireless working!"  Its no wonder after dealing with ndiswrapper myself!

Why does getting wireless ethernet connections have to be so difficult??? (Yes I know the manufactures dont as a whole release linux drivers, but come on, the current work-around is ridiculous!)

---

### Post by cornsnap on 2007-06-04
You are absolutely right, the time it takes to install drivers can sometimes take a lot of time however we are all working together to try and achieve the same goal.  Things will become easier once Linux begins to catch hold but it's up to you and I (Technical Folks) to work out the bugs and feed this information back to the engineers at Ubuntu.  You'll see manufacturers  begin making drivers that will work like a charm soon. :)

Peace.

Stay focused.

---

