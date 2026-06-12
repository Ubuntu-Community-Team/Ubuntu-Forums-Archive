---
title: "Wired Network won't start"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by Doctor J on 2007-11-03
Background: i have a PowerBook G4 that dual boots into OS X and Ubuntu.  I had Feisty on for a while, was able to use both wired and wireless networking.  Both wired and wireless get their connections from an Airport Extreme router in front of a Westell DSL modem.  

Yesterday i did a clean install of Gutsy, and now i can't convince it to go online to get the restricted driver for the Broadcom wireless interface.  The network icon on the toolbar shows "No network connection".  Starting the "Network Settings" window seems unreasonably slow: ~1 minute just to populate the window and another minute to bring up the "eth0 Properties" window.  After enabling the wired connection for DHCP [eth0 was initially disabled], the icon shows a cable unplugged.  I have verified the cable is seated on both ends and the system is able to use wired networking when booted into OS X.

I'm at the end of what i know to do.  What else should i accomplish to troubleshoot this?

---

### Post by joeabiraad on 2007-11-03
i have the same problem ...

Anyone help ?

---

### Post by Doctor J on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/155572) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				@joeabiraad:  It looks like there's not much help to be had from this forum.  There is definitely something wrong with the network-manager package on the CD.  When i run 'top' in the Terminal, it shows that the network-manager process is consuming 96% of CPU.  Killing the process then allows for reasonable responsiveness for the rest of your programs.  However, it still doesn't allow me online to download the needed updates.  :mad:  It's a shame this kind of thing couldn't be found out before the disk image was put out.  I guess i'll have to go back to Feisty until a patched disk can be made available...

---

