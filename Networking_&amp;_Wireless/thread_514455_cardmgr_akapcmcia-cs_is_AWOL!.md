---
title: "cardmgr aka:pcmcia-cs is AWOL!"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by sonic256 on 2007-07-31
So, I've just got a fresh install of 7.04 on my Dell laptop (I don't know the model, but its a few years old).  And I'm working on setting up wireless with my Airnet AWN154 card, and I'm following the [Trouble Shooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and I've made it all the way to 3.1.2 and the part where I have to kill my /var/run/cardmgr.pid, well I don't have that process to kill, pcmcia-cs is not installed, and if I do a 'sude apt-get install pcmcia-cs' my system says it can't find that file, my laptop has no ethernet to get the package from the internet.  I know that pcmciautils is the newer version of the pcmcia-cs package (I think) so does the Guide need to be updated with new commands or am I totally missing something basic? 

Thank You very much,
Tim

PS: My bud told me that rebooting would do the same thing as killing that process/package (the one I don't have), and when I reboot and run a 'sudo lshw' I see my ethernet controller but not my pcmcia card, I have ndiswrapper installed with the driver from [here, the AWN154 version](http://www.airnetusa.com/download_center.html).

---

