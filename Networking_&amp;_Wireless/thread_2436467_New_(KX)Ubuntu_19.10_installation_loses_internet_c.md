---
title: "New (K/X)Ubuntu 19.10 installation loses internet connection on and off after suspend"
date: 2020-02-06
forum: Networking &amp; Wireless
---

### Post by ravalox on 2020-02-06
So I have a brand new install of Xubuntu 19.10 that will occasionally lose internet for about 30 seconds to a minute periodically; as you may imagine it's very annoying. I did a sudo apt install kubuntu-desktop on it to to get KDE as an option as well; I know that doesn't dictate what wireless driver I use but it does tell you what debug tools I have at hand; I was wondering if this was a known issue with the new version and/or what kind of trouble shooting options I have available to me?



It's an older laptop with this lspci description of the card:
Network controller: Intel Corporation Centrino Wireless-N 1000 [Condor Peak]       
Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN       
Kernel driver in use: iwlwifi       
Kernel modules: iwlwifi

I should point out that I run the wifi card with power management turned off because with power management on this problem was rampant and the card was just slow. I should also add that I suspect that it may have something to do with suspending the laptop when I close the lid; meaning that things are fine until I do that and then my wireless connection speed periodically drops off for a minute.

I tried this:
[https://freedompenguin.com/articles/how-to/ubuntu-wireless-internet-drop-off-fix/](https://freedompenguin.com/articles/how-to/ubuntu-wireless-internet-drop-off-fix/)

It seemed to work for the first two suspends then KDE lost both the network manager and my internet connection entirely and I had to reboot.

---

### Post by praseodym on 2020-02-09
Lets try
```

sudo touch /etc/systemd/system/wifi-resume.service
kdesudo kate /etc/systemd/system/wifi-resume.service
```
Add the following
```

[Unit]
Description=Restart networkmanager at resume
After=suspend.target
After=hibernate.target
After=hybrid-sleep.target

[Service]
Type=oneshot
ExecStart=/bin/systemctl restart network-manager.service

[Install]
WantedBy=suspend.target
WantedBy=hibernate.target
WantedBy=hybrid-sleep.target


```

---

### Post by ravalox on 2020-02-10
So I tried this, it's the method in the link to the original post- when I come back from suspend the network manager in KDE is missing entirely and I can't see what network I'm connected to/choose another one.  I had to switch from XFCE because of a keyboard issue... my experience with this release isn't going very well.  I think this approach works in XFCE but the keyboard issue I've referred to is a dealbreaker for using; periodically it won't let me type into a text box until I change focus to a different textbox, doesn't sound that bad until it happens on login where there are no other boxes- then you have to hard reset the machine.  Do you have a similar problem and does this approach work for you in KDE?

---

### Post by ravalox on 2020-02-11
Sadly after trying this approach in XFCE for a day I have concluded the restarting of the network manager doesn't fix the problem; the driver still just goes hay wire and the only solution seems to be a full reboot.

---

### Post by ravalox on 2020-02-11
So I may have fixed my problem; I wrote this script:

```

#!/bin/sh                                                                                                                                     

MYNAME=$0                                                                                     

DRIVER=iwlwifi                                                                              

/usr/bin/logger $MYNAME 'restart_wifi BEGIN'                                              
/sbin/modprobe -v -r $DRIVER # This removes the driver
sleep 2                                    
/sbin/modprobe -v $DRIVER   # This starts the driver                                      
#systemctl restart NetworkManager.service # network manager restart disabled as not needed
/usr/bin/logger $MYNAME 'restart_wifi END'

```

It seems to be working; the 2 second pause turned out to be important.  I'll mark this solved tomorrow if this seems stable over time.

---

### Post by ravalox on 2020-02-12
Ugh, nothing I've tried works, it all starts to sputter after a while and I just have to reboot.  Not being able to suspend is pretty debilitating for a laptop.

---

### Post by him610 on 2020-02-13
I am surprised none of the subject matter experts have yet to suggest you perform all of the actions in this thread,... [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")
When you complete all of the actions, let everyone know, including where the contents of file, wireless-info.txt is posted.

---

### Post by ravalox on 2020-02-17
Alright, I followed the instructions and it's still persisting with my wireless issues; wirelessinfo: [https://pastebin.com/jdTGTSyv](https://pastebin.com/jdTGTSyv)

---

### Post by ravalox on 2020-02-21
So after some trial and error this is what I've come up with:

```

systemctl stop NetworkManager.service
ip link set wlp4s0 down
sleep 2
modprobe -r iwlwifi
sleep 2
modprobe iwlwifi
sleep 2
ip link set wlp4s0 up
sleep 2
systemctl restart NetworkManager.service

```

Seems to work but it's a bit strange I have to do this, these are very well known intel devices.

---

### Post by him610 on 2020-02-21
I am just guessing, but it appears your wireless module sees the multiple ForbiddenPlanet signals, and keeps switching back and forth between the signals without locking on to one of them. Do you control the router(s) for ForbiddenPlanet?
```

ForbiddenPlanet                   <MAC 'ForbiddenPlanet' [AC1]>  Infra  7     2442 MHz  195 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;
....
ForbiddenPlanet                   <MAC 'ForbiddenPlanet' [AC3]>  Infra  1     2412 MHz  195 Mbit/s  77      &#9602;&#9604;&#9606;_
....
ForbiddenPlanet                   <MAC 'ForbiddenPlanet' [AN12]>  Infra  1     2412 MHz  195 Mbit/s  50      &#9602;&#9604;__

```
If so, then you might consider changing the names so they are slightly different, ie ForbiddenPlanet1, ForbiddenPlanet2, ForbiddenPlanet3.
If you don't control the router(s), you might consider setting your system to  completely ignore the two with lesser signals.
Someone else with more expertise than I may chime in, hopefully.

---

### Post by ravalox on 2020-02-23
So this is a mesh router system, those three wifi networks are one mesh.  I have several devices of this era and this is the only one with this issue.  I do have another network(the router's network) I can switch to to see if I have the problem.

---

### Post by him610 on 2020-02-24
>  this is a mesh router system
Good to know. You can probably disregard whatever I suggested in my earlier post. I compared contents of your wireless-info.txt with my own; concluded they are not that much different except my intel wireless device has a different model number; however, I may have missed something.

---

### Post by ravalox on 2020-02-24
On the contrary, your feedback has been invaluable.  It led me down the path of looking at the driver documentation and I discovered something- it doesn't support mesh routers.  If I want to use my mesh network I'll likely need to get a panda wireless USB adapter.  Frustrating but I think this may be the answer.  I might mark this solved after some more testing.

---

