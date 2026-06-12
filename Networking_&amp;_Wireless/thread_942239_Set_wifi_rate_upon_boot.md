---
title: "Set wifi rate upon boot"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by hyper_ch on 2008-10-09
I just notice that regurarly upon reboot the wifi rate is set to 1 M instead of 54M. Where could that be set permanently to 54M? Anyone knows?

---

### Post by iponeverything on 2008-10-09
If your using 8.04 -- there is bug in nm-applet that causes it to miss report. I think that what you will see with iwconfig will be the correct speed.  

you can set the speed like so:

iwconfig wlan0 rate 54M

where wlan0 is your device.

your could add the command to /etc/crontab to have it execute automatically every hour if has habit of dropping back down.

also putting it in:

/etc/init.d/rc.local

will set it at boot time.

---

### Post by hyper_ch on 2008-10-09
I'm on 8.10 but had the same issue on 8.04. Running cron or put it into rc.local are work arounds. There should be a "right" place to set it :)

---

