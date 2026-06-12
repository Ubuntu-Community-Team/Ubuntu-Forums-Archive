---
title: "Ubuntu crashes on network select!"
date: 2006-09-09
forum: Networking &amp; Wireless
---

### Post by sas01 on 2006-09-09
Well after using ndiswrapper to get Ubuntu to recognize my Asus 138g wireless adaptor and getting it to find the network (WLAN), I happily go into network admin to configure wlan0.

To my dismay after filling out all of the settings (no WEP, IP and subnet assigned by DCHP) I select the network name from the drop down box (It's WLAN). And it comes up as selected. I click ok and suddenly my computer freezes!

At first I assumed it was an espescially long load time so that it could recognize all the drivers etc etc. Twenty minutes later it had not loaded. My computer was still completely frozen!

I did a dry reboot (where you physically turn your computer off and then back on) and then I noticed that when I booted ubuntu up it took about 10 minutes on the step: "Configuring network interfaces). 

When it did finally load it then suddenly all the modules and other things  being loaded suddenly went into white text on a black background.

It took me to my login screen as usual and I logged in without problem.

What's wrong with my wireless then? I made sure that I used the correct drivers and ndiswrapper. I updated modprobe and hotplug from ndiswrapper. I ran it all as root.

What am I doing wrong?

All help is appreciated.

Regards sas01.

P.S please reply soon as this is some rare time off from the army!

---

