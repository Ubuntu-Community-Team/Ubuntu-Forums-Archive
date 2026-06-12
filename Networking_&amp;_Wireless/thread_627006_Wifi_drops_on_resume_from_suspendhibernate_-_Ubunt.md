---
title: "Wifi drops on resume from suspend/hibernate - Ubuntu 7.10 on Dell Inspiron 1420n"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by ben_choad on 2007-11-29
Hi all,

I have a Dell Inspiron 1420n laptop that came with Ubuntu 7.04. I upgraded via the Update Manager to 7.10 (so this is not a clean install). It's an all-Intel chipset (graphics, sound, wireless etc.) which uses the ipw3945 wireless card. I applied this fix as suggested by the Dell Linux wiki:

ttp://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues

This basically loads the iwl3945 module driver. 

I have two problems so far: 

1. When I suspend or hibernate the machine and resume, the wifi connection drops. The network manager applet in the menu bar doesn't even give me the option of connecting to a wireless network leading me to believe that the driver shuts down completely. Only a reboot fixes the problem. 

Is there any way I can restart the driver or nm-applet after resuming? I haven't actually done a diff of the processes running before suspend or hibernate and after to figure what exactly died, but I figure I would ask here first to see if any one has any ideas. 

I tried adding the line STOP_SERVICES="networking" to /etc/defaults/acpi-support and that had no effect either. 

2. The second, more minor problem, is that the wifi only comes up about 75% of the time after boot even though I have the network password in my keyrind. However, I can just go into nm-applet and manually connect to the network. It's workable and quick but still a bit annoying. 

The worse problem is not being able to go into suspend/hibernate at all - I have to leave the machine running or shut it down. 

Thanks for any help and thoughts. 

-Ben

---

### Post by tpischke on 2007-11-30
Me too.  Unfortunately can't add too much info.  Exact same behavior using iwl3945, no wifi options after suspend/resume.

Tried killing nm-applet and restarting, no difference.  Logout and login also doesn't help, so appears to be some problem with the driver itself.

---

### Post by xardy on 2007-11-30
seems to be the same as in this thread: [http://ubuntuforums.org/showthread.php?p=3867222#post3867222](http://ubuntuforums.org/showthread.php?p=3867222#post3867222)

a workaround has been posted there. This even happens to me when I'm just working on my laptop...

---

