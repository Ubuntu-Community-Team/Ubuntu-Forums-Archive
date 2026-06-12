---
title: "DHCLIENT problem"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by thatrandomguy on 2008-05-03
Hey,

I just tried that tutorial and everything was going well until it tried to get an ip address (the sudo dhclient wlan0 on step 14.)

Here is the Message i got:

Listening on LPF/wlan0/00:17:3f:ad:79:c8
Sending on LPF/wlan0/00:17:3f:ad:79:c8
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received
No working leases in persistent database - sleeping.


I'm running 8.04.

Can anyone help?

Thanks
Chris

---

### Post by chrisdudeperson on 2008-05-03
please help!

---

### Post by lswest on 2008-05-03
what tutorial were you following?  how are you trying to connect to the network (wired, wireless?) what card, to a router or direct connection?  is the card set on roaming mode?  More info would be good, if you could post the output of ```
lshw -C network
``` too it would be useful.

---

### Post by chrisdudeperson on 2008-05-03
Sorry about that, i forgot to link to the tutorial!

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)


And i'm running wireless.



Here is the output of that command:

lshchris@chris-desktop-linux:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:ad:79:c8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN


Thanks
Chris

---

### Post by lswest on 2008-05-03
i just gave that how-to a cursory glance and the output here doesn't list a driver being used, not sure if it will, but i do believe it should.  Are you sure you followed the tutorial correctly? (not that i'm insulting your intelligence, it just looks like a long how-to where you could easily miss a step).  Maybe have a look through it again and see if you missed any step regarding the starting of the actual driver.

---

### Post by chrisdudeperson on 2008-05-03
well, there is a driver in hardware drivers and i dont think i missed any steps because i didn't get any errors or anything.

o yeah i got my other account working, i forgot the password:P

same guy and that random guy

---

### Post by thatrandomguy on 2008-05-03
i'll use this account to save confusion

---

### Post by thatrandomguy on 2008-05-03
I Need Some Help Please!

---

