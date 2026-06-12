---
title: "Intel ipw3945 wlan vanished?"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by JoSch on 2007-11-21
Hi!

After a restart my wlan interface no longer showed up in network manager or the network configuration GUI.
I checked lspci and my intel ipw3945 was still there.
I checked the restricted drivers manager - the module was activated.
I checked iwconfig - nothing.
I did 'sudo modprobe ipw3945' no errors and 'lsmod | grep ipw' correctly shows the module as loaded and ready.
I threw in the gutsy desktop cd and observed exactly the same - so it's probably not my configuration.
Why shows my card up in lspci but nowhere else?

EDIT: can a mod please remove this post? it got solved

---

### Post by kuja on 2007-11-21
> **JoSch said:**
> Hi!

After a restart my wlan interface no longer showed up in network manager or the network configuration GUI.
I checked lspci and my intel ipw3945 was still there.
I checked the restricted drivers manager - the module was activated.
I checked iwconfig - nothing.
I did 'sudo modprobe ipw3945' no errors and 'lsmod | grep ipw' correctly shows the module as loaded and ready.
I threw in the gutsy desktop cd and observed exactly the same - so it's probably not my configuration.
Why shows my card up in lspci but nowhere else?
You didn't accidentally flip the wireless switch did you? I could see that causing this sort of problem ...

---

### Post by Ivan Wagner on 2007-11-29
Happened the same thing to me yesterday... I actually installed new packages such as ubuntustudio-audio, ubuntustudio-video and ubuntustudio-graphics. I suspect that by adding these previously mentioned packages caused something else to be removed... But perhaps it's something else that caused the issue.
Anyways the ipw3945 module seems to be loaded correctly (by writing the lsmod | grep ipw commands).
Another piece of information I can give you is that no yellow LED is blinking while the bluetooth LED is on.
If I right-click on the network-manager applet on the top right corner of my desktop, I actually see the "Enable networking" voice, but previously the "Enable wireless networking" or something similar was displayed as well.

Some one able to help us out?

Thank you in advance for any new reply,

Ivan.

---

### Post by Ivan Wagner on 2007-11-29
Ok I found out what's the problem about... A new kernel version (2.6.22-14-rt) has been installed after that I installed the ubuntustudio-x packages.

If I choose kernel 2.6.22-14-generic everything goes back as normal...

Cheers,


Ivan.

---

### Post by Ivan Wagner on 2007-11-29
Ok... Obviously everything works fine as long as you also install the linux-restricted-modules-2.6.22-14-rt package...

Ivan.

---

