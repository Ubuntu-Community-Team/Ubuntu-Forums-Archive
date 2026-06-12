---
title: "Internet connectivity issue,"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by kdarkentity on 2007-10-26
I am running gutsy off of my gateway laptop and recently i have been experiencing some issues with connecting to the internet. When i first boot up my machine into Ubuntu if there is a wired network that im plugged into or if there are wireless networks around it connects automatically, however if i wish to change my connection to another network during the same session my network driver crashes. Also when i try to open manual configuration it crashes as well. I am not sure where to begin diagnostics on this and up until recently i was having no problems with internet connectivity soo any help at all will be most appreciated. 

thanks

---

### Post by Lambert on 2007-10-27
Start by looking in your logs. If you go into the administrations menu you will see syslog. Look through the files for errors or other events around the time you're having network issues. You will see a copy choices of logs to look at. syslog should show most of what you need.

network manager is also very buggy. Not sure what device/driver you're using but wicd for some is a better option to managing network.

---

