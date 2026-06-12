---
title: "thinkpad x60 - atheros driver - wireless now working"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by deniro0311 on 2007-05-01
I have a thinkpad x60 with the thinkpad abgn nic (atheros).  The nic seems to be causing people a lot of problems with 7.04.  After a little work I got it working.  For those of you in the same boat here is how I did it.  

First, use synaptic to get ndiswrapper.  Get the ndiswrapper gui driver installer while you are at it.  Now go to the Lenovo site and get the windows driver for the thinkpad abgn nic.  Next, go to the following link and follow the directions...  [http://thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter]("http://thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter")
The only part I deviated from was the part about installing the driver .inf file.  I used the ndiswrapper gui for that, just to see if it worked.

My nic is now working very well.  I also didn't have to do any tinkering to get WPA working, it just works.  I personally don't see why everyone is complaining so much about the networking tools that come with this version of Ubuntu.  They work great, now that my nic is up.  I hope this helps.

---

