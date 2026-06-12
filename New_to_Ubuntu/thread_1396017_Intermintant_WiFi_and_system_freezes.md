---
title: "Intermintant WiFi and system freezes"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by gerryex on 2010-02-01
Hi ALL,
 
Well, I'm still getting the hang of Ubuntu and while it is mostly working OK, I am seeing some probems with WiFi and system freezing. I have an Acer laptop with dual boot into Win 7 and Ubuntu.
 
In Ubuntu the WiFi connects right after boot up and shows a high signal strength, over 90%. Then after a while it shows about 45% and stays that way. Closer to the router does not change the readings. Then after a ramdom while it cuts out all together. Sometimes I can get it back but other times I have to reboot, and then it comes back as soon as the boot is done.
 
When I'm in Win 7 the Wi Fi signal never goes below 90% and so far I have never lost the signal.
 
What also sometimes happens when I lose the signal in Ubuntu, is that the system seem to get hung up and doesn't respond properly. When this happens any kind of clicking on the WiFi icon does nothing. Then at one point I wanted to bring up a terminal window and while the lower panel stated something like "Terminal starting up" but the window never came up. Then I went to restart it but it seemed to get hung up on a text only full screen and some error messages came up:
 
INIT: AVAHI-DEAMON main process (743) terminated with status 255
INIT: HAL main process (705) terminated with status 1
INIT: RSYSLOG-KMSG main process (436) killed by terminal signal
 
 
It never went to reboot and I had to manually power off and back on to reboot. Does any of this make sense? Is there another WiFi network manager I can install and if so how do I get rid of the current one.
 
I'm kind of surprised as from all I read Ubuntu is supposed to be pretty stable but at least for me Win 7's WiFi seems much more stable the Ubuntu's!!
 
Thanks,
Gerry

---

### Post by LinuxGuy1234 on 2010-02-01
I'll try to clean up the tech stuff, but a program running while the computer is started called "NetworkManager" runs and talks between your network card and Ubuntu. This is aided by "drivers", which are loaded on-demand. They sometimes glitch.

Try running this in the terminal:
```

lspci -vv > pci.txt
uname -a > version.txt
iwconfig > wireless.txt
```

These commands should give some info. Post "pci.txt", "version.txt" and "wireless.txt" from your "Home Folder" here. We may be able to find the problem.

---

### Post by gerryex on 2010-02-01
> **LinuxGuy1234 said:**
> I'll try to clean up the tech stuff, but a program running while the computer is started called "NetworkManager" runs and talks between your network card and Ubuntu. This is aided by "drivers", which are loaded on-demand. They sometimes glitch.

Try running this in the terminal:
```

lspci -vv > pci.txt
uname -a > version.txt
iwconfig > wireless.txt
```These commands should give some info. Post "pci.txt", "version.txt" and "wireless.txt" from your "Home Folder" here. We may be able to find the problem.


HI,

I've attached the files you asked for.

Thanks a bunch!!
Gerry

P. S.  I'm sending this reply on the laptop and the signal strength stated out at 83% and is now 38%!

---

### Post by gerryex on 2010-02-05
Bump!
 
Anyone?
 
Thanks,
Gerry

---

