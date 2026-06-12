---
title: "Logon issue"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by confuzd on 2011-04-07
Looking for help:
 
I installed latest version OK, when I login it starts then right back to login. I have attempted multiple installs same prob.
 
I installed old version 8.?? login worked OK, upgraded to ver 9.?? login worked OK.
 
Thru several upgrades from 8.?? to 9.?? the login worked fine. It is when I upgrade or install ver 10 that this problem comes out.
 
Why does the login not work properly???????
 
Any help???
 
Thanks 
Scott

---

### Post by kn0w-b1nary on 2011-04-07
Can you try installing 10.10 fresh? remember to reformat first or it will not work.

---

### Post by confuzd on 2011-04-12
I have attempted fresh install of 10.10 with the same result.
 
Anybody have any thoughts about this???
 
About ready to give up...Help:D

---

### Post by Frogs Hair on 2011-04-12
Does it run live from the disc , if not , it may be hardware related .  Did you run a checksum ? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by confuzd on 2011-04-13
I found that it does not run from the disk.
 
I did a clean install of Win XP that works ok
 
I previously installed Ubun ver 8 ok, then upgrade to ver 9 ok
 
Whether I upgrade to ver 10 from web or install ver 10 from disk I have same issue.
 
System is older P4 w 512 ram,  I guess ver 10 doesn't work on this hardware.
 
Oh well

---

### Post by PPPilot on 2011-04-13
confuzd,

I had the same problem with Lucid (10.04). Try this.

1. At the login screen select your login name.
2. Note down in the bottom panel in Sessions select "Gnome Safe Mode"
3. Type in your password and hit enter.

If your system stays logged in, check your panels to see what is missing.
In my case it was the Network Manager Applet. I then went to System>Preferences>Startup Applications and unchecked  :"Network Manager"

Now I logout out and logged back in using the regular, non-safe mode, Gnome session and all was well. I then Entered Alt-F2 and entered "nm-applet". I found that as long as you run it after login startup is complete there is no problem. I then created an application to run the command "nm-applet" on the panel so that I did not have to type it in every time. I turned it in as a bug but this is an easy work around.

I suspect you have the same issue. If your problem turns out to not be the Network Manager Applet substitute your problem program and do the same procedure outlined above.

Hope this helps.....

---

