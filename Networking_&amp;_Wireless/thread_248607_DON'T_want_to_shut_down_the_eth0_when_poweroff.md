---
title: "*DON'T* want to shut down the eth0 when poweroff"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by Rumcajs_tr on 2006-09-01
As I understand, by default, Ubuntu shuts down the eth0 interface while shuting down the computer.
I DON'T WANT to shutdown my eth0 card when powering off the PC.

I thought that it is done by:
```
halt -d -f -i $poweroff $hddown
```
in the **/etc/init.d/halt** file.

So I decided to remove the "-i" parameter, as this is described in the documentation for shutdown of the network.
The line now looks like this:
```
halt -d -f $poweroff $hddown
```

BUT IT DIDN'T HELP!

Did I miss something?! Please Help!

---

### Post by meng on 2006-09-01
What am _I_ missing here? How can the ethernet card still be active when your computer is off?

---

### Post by sebastfr on 2006-09-01
> **meng said:**
> What am _I_ missing here? How can the ethernet card still be active when your computer is off?

for using eg. wake-on-lan

what about removing some of the 'network' symlinks under /etc/rc0.d (the run-level for halt)?

Seb

---

### Post by galileon on 2006-09-01
its not a linux as far as i know, its ur mobo that needs to have the feature, and as long as theres power into the box, the network card is up...it might even have a led that lights up to tell you its connected

---

### Post by Rumcajs_tr on 2006-09-01
The LAN card stays on normally when power-off from WinXP, so it *IS* a linux issue.
I will try to test sebastfr's suggestions, this might help....
will report later...

---

### Post by Chris Tucker on 2006-09-01
Ubuntu doesnt so much shut down the eth0 device when it shuts down the system, if your light on your network hardware (switch,router,hub,modem) that leads to the system in question is still on when your computer is off, it's network card is still on.
Theres a flag in ethtool that has to be set every boot for Wake On LAN to work, its a weird thing, i know, bios should handle WOL all by itself, under any circumstances, but its not always the case.

Theres a howto ive written here that also has an automated script for setting up the script to set the flags on boot, without any hassle:
[http://www.ubuntuforums.org/showthread.php?t=234588]("http://www.ubuntuforums.org/showthread.php?t=234588")

---

### Post by doobit on 2006-09-01
[http://www.ubuntuforums.org/showthread.php?t=234588](http://www.ubuntuforums.org/showthread.php?t=234588)
Thanks for posting the howto, Chris.

---

### Post by Rumcajs_tr on 2006-09-01
SOLVED!

Tanks for sebastfr !!!!
I removed:
networking file form /etc/init.d
S35networking file from /etc/rc0.d
S35networking file from /etc/rc6.d
S40networking file from /etc/rcS.d

Not sure what each directory is for, but the LAN card remains on.
Maybe, one of the files should stay there, please send comments...

Just to describe the reason, why I wanted my eth0 interface to stay on:
I have the ASUS wl-500gx router and it seems, that there is a bug in the DHCP server.
I have set (in the configuration of the router) manual assignment of IP according to the MAC adress of my PC. So if I go to DHCP leases log table, I can see the MAC dresss of my PC, next to it the IP I assigned and next to it the word "manual"
In other cases (IP not assigned to MAC adress) there is always a timeout in seconds, when the DHCP lease expire, instead of word "manual".
Up to here, everything is OK. HOWEVER:
If I shutdown the linux, the eth0 card goes off and when it goes on againg, the router doesnt display "manual" next to IP adress in DHCP leases log. there is a timeout as if the IP adress hasn't been assigned to the specific MAC. After rebooting the router from the web interface, the "manual" assignment is back!

So it is definitelly a bug in the asus FW, however this workaroud works OKAY!

---

### Post by sebastfr on 2006-09-02
nice one!... but I was thinking... did you have to remove the 'networking' script from the /etc/init.d/ ? Wouldn't it be better to just remove the symlinks from the /etc/rc[n] directories? (I say that 'cause it's handy to have the script in init.d for restarting the network interfaces)

probably no biggies anyway...

seb

---

