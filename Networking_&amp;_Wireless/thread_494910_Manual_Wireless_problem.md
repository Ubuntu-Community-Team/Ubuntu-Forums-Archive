---
title: "Manual Wireless problem"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by mercurymouth on 2007-07-07
Hey guys, sorry if this is a ridiculous question, but I am new.  So I installed Feisty and my wireless was working great on the home network.  Then I took it to my brother-in-law's house where he had to use the "manual network" settings to work with his wireless system.  Now I am back home and I can't figure out how to connect to my own home wireless network again.  Is there any way to change back from the "manual wireless" mode back to the mode where the system automatically detects the network and I simply choose which I want to connect to w/o going through all the manual settings?

---

### Post by kevdog on 2007-07-07
First you probably altered the /etc/network/interfaces file to set up the manual settings.  I would simply put a # sign in front of the lines you set up so if you ever go back to your brother's place, you can simply remove the # signs to restore the settings (a # sign means that line is a comment and is skipped).  

If you are using network manager, then do the following:
System->Administration->Network
Choose your wireless connection
Hit properties, and then select "Enable roaming mode"

Hit Ok.

It should work then.

---

### Post by mercurymouth on 2007-07-07
Sounds about right.  I'll try it out.  Thanks a lot.   You were right and it is working great again.  Thanks man!

---

