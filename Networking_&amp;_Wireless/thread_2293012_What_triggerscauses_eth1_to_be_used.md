---
title: "What triggers/causes eth1 to be used?"
date: 2015-09-01
forum: Networking &amp; Wireless
---

### Post by johnny36 on 2015-09-01
TLDR:
Laptop has eth1 as wired connection
[COLOR=#000000]if i was to ifconfig, it would be eth1, lo, and wlan0[/COLOR]
 eth1 says last used 4 hours ago, what does it mean last used 4 hours ago? what is the trigger? what causes it to be used? _**why does restarting or a hard boot the laptop not refresh it?**_
[COLOR=#000000]---------------

Hello,

Total newbie to Ubuntu, I found out today that I have this wired connection 1  apparently it is  eth1 (dont have eth0 for some reason) and im on the  laptop connected to wifi

Ever since my install on Ubuntu, I never used a cable for anything except an HDMI cable

To connect to my wifi I'm using a usb wifi.

Before I found out that my wired connection 1 was last used/trigged 4 hours ago

[/COLOR]I surfed the web, restarted my computer, downloaded unity tweak tool, unplugged/plugged my usb wifi because internet stopped workign for some reason

My problem here is I don't know what trigged it to say "last used 4 hours ago"

[COLOR=#000000]I attempt to replicate the trigger....[/COLOR]

[COLOR=#000000]I restart my computer, nothing changes.[/COLOR]

[COLOR=#000000]I turn off wifi, nothing changes.[/COLOR]

[COLOR=#000000]I try unplugging my wifi usb nothing changes.[/COLOR]

[COLOR=#000000]I am so lost... 

[/COLOR]I'm super paranoid if someone hjacked my internet or someone stole my info cause I know literally nothing about computers.

---

### Post by tgalati4 on 2015-09-02
Welcome to the forums.

Your network connections are maintained by [NetworkManager]("https://help.ubuntu.com/community/NetworkManager").  To see the status of these connections you can use the Command Line version.  Open a terminal:

```
nmcli con
```

You will notice that there are timestamps for these connections the last time they were made.  So, unless you have a cable connected, I don't see how your system could be compromised, unless somebody plugged into it.

---

### Post by johnny36 on 2015-09-02
sadly i deleted 'eth1' already and remade a new one so i can't see the previous timestamps.

the problem here is i never plugged any cable on my laptop

like how could it be 'last used' when i never plugged anything in besides hdmi, wifi usb and power cord?

--------------- 

Edit:

I just booted Ubuntu off my USB and wired connection says it was last used "4 minutes" ago which is the same time i booted my pc. 

no cable , just wifi.

How did eth1 even get used?


Edit 2:
Reinstall fixed everything. Thanks.

---

