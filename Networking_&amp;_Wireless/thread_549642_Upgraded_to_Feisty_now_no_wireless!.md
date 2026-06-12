---
title: "Upgraded to Feisty now no wireless!"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by CoriolisSTORM on 2007-09-12
Well, I upgraded from Feisty using a fresh install from a CD, and my wireless  card WUSB54Gv4 is no longer recognized.  I have followed the guide at the top of the page to try and get it working like I did under Dapper but it doesn't show up at all after I blacklisted rt5XX (forgot the exact one specified).  I am using Ndiswrapper from synaptic as I can't get the other to install correctly from sourceforge.  (And yes I have build essentials and kernel headers installed)  When I do ndiswrapper -l (or ndisgtk) it tells me that the driver is present but no hardware is present,  I know it is at least plugged in, as when it starts up the light flashes a couple of times then the thing apparently turns off.  What do I need to do?  Before I forget, I also am on a WPA network as well.  
edit1:  Well, I un blacklisted the driver and restarted and I finally get it to where it recognizes the device, only problem is I don't have WPA support.  What now?

---

### Post by jnorthr on 2007-09-13
Pretty much the same story here, but i just left WPA off for the time being until i can find other guides as to how to hook it up successfully. Just don't do any paswords over the airwaves !!!:(

---

### Post by CoriolisSTORM on 2007-09-13
That's a problem for me since I am not the network admin.

---

