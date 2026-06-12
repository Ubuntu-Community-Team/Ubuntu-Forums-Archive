---
title: "WPA with bcm4318 AirForce One 54g"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by WieboJJ on 2007-06-20
Cant seem to connect using wpa supplicant, would be nice to get wpa working as now I'm I only seem to be able to connect to my network with no security enabled whatsoever...

Anyone else with this card able to get wpa working?

I'm on a hp dv8305ca notebook, ubuntu 7.04, with a bcm4318, currently using ndiswrapper and the .inf driver from my windows partition...

Thanks in advance

---

### Post by bedfojo on 2007-06-20
Got the same card, works with WPA2.

Try upgrading ndiswrapper to the latest version (not the 1.38) in the repos but the 1.47 from [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) . You'll need to compile it in yourself.

Then also try removing network-manager and install wicd instead from [http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by kevdog on 2007-06-20
bedfojo

Where did you get the drivers for your card???

---

### Post by WieboJJ on 2007-06-21
Awesome, I will give it a shot,

You still using WPA supplicant?

BCMWL5.inf or BCMWL5a.inf?

thanks,

---

