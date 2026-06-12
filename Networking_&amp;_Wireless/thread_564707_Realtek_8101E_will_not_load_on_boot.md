---
title: "Realtek 8101E will not load on boot"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by dgtldaydrmr on 2007-10-01
Perhaps someone may have some insight on whats not working correctly.
I run ubuntu and slackware.

You don't have to read this it's just some background info.
[I]Ubuntu - because it runs great right out of the box with little to no problems and is good to get a system up and running in a short period of time
Slackware - for something difficult that i have to troubleshoot and install nearly everything manually so I can better learn some basics about linux and the way things work.
[/I]

In ubuntu my realtek R8101E works fine and is automatically setup with a fresh install.
In slackware I installed it and set it up but for whatever reason i can't get it to load when the computer boots. i can manually ifconfig eth0 up but I'm curious as to why it isn't loading automatically.

The only thing I can think of is it's not reading the /etc/sysconfig/network-scripts/ifcfg-eth0 script


I know this is not a pure ubuntu question but this forum is very active with a great community.



Thanks in advance!

---

### Post by noob12 on 2007-10-01
Suggestions:
- On your slackware make sure you have **ONBOOT=yes** in that ifcfg-eth0 .  
- Use Ubuntu.  You can learn about linux on Ubuntu as well.

---

### Post by dgtldaydrmr on 2007-10-01
I used the netconfig script and checked the settings in /etc/rc.d/rc.inet1.conf

```

    # Primary network interface card (eth0)
    IPADDR[0]=""
    NETMASK[0]=""
    USE_DHCP[0]="yes"
    DHCP_HOSTNAME[0]=""

```

note: USE_DHCP[0]="yes"


it seemed it wouldn't read from the /etc/sysconfig/network-scripts/ifcfg-eth0

by the way I had this in the ifcfg-eth0 config file
```

DEVICE=eth0
BOOTPROTO=dhcp
ONBOOT=yes

```

though I'm not sure what the network config script did to enable the adapter on boot.
I tried setting up the card with the ifcfg-eth0 file first then tried in KDE with the GUI tool... for some reason the GUI tool would not save changes and even when it did they didn't reflect in the config file.

the only thing that worked but had to be re-done every time I turned the computer on was:
```

ifconfig eth0 xx.xx.xx.xxx netmask xxx.xxx.xxx.x

```

Even then I couldn't figure out how to setup the gateway and dns servers...
I read the ifconfig man page about 10 times and looked the the ifconfig --help as well.


Thanks for the reply!

-Ubuntu just works and doesn't give me crazy problems to troubleshoot I like it but I need something that requires me to set things up and manually change/install/fix.

I guess all in all Ubuntu just doesn't give me enough problems to solve but I love it for usability.
When I have something that works "out of the box" I am less inclined to break it.
Slackware on the other hand requires alot of custom configuration to get it going.

I think I have fried my slackware kernel at least 3 times and I'm on my 5th or 6th install.
Ubuntu I installed once and it works and I would like to keep it that way :P

---

### Post by dgtldaydrmr on 2007-10-01
But now... that the wired network is up and running...
I have to get my wireless working... thats what fried my Kernel last time...
Tried installed the mac80211 modules and durring the compile there was a warning message i chose to ignore because it didn't look that important... well i was wrong. next boot = kernel panic.

Round: 2! DING!

---

### Post by noob12 on 2007-10-01
You might have better luck on slackware forums for continuing with the slackware stuff.  Good luck.

---

