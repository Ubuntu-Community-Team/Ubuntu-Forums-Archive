---
title: "Trouble connecting to internet"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by ror on 2006-08-16
I have installed Ubuntu 6.06 (alternate amd64 version) recently (and new to linux). I installed ndiswrapper, installed relevent windows network drivers with it and it confirms they've been installed and hardware is present.

Next I fill the information out for the wireless network. Clicked activate, after waiting for it to load it says something about interface eth0 being active. I press ok, and try to use firefox and it doesn't work. I go back to the network menu and it says eth0 is not active again. 

I've had a look for other ways of getting it sorted out but came up short. 

Can anyone help please?

---

### Post by ComplexNumber on 2006-08-16
install wifi-radar from somewhere. i found out that i didn't need to fill any infornmation in because either wifi-radar and/or network manager seemed to configure everything for me. all i needed to do was install the ndiswrapper and the windows drivers using ndiswrapper....and that was that.

i think you're nearly there, though :)

---

