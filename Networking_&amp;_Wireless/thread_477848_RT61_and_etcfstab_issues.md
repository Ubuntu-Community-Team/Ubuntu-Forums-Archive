---
title: "RT61 and /etc/fstab issues"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by AndyCooll on 2007-06-18
I have a Belkin PCMCIA card that uses the RT61 driver. I followed these instructions to get it working: [ HOWTO: RT61 on Feisty Fawn with WPA]("http://ubuntuforums.org/showthread.php?t=419709") and the wireless card works fine ...sort of. I simply edited my /etc/network/interfaces as per the recommendations in the howto and it worked. Indeed I'm typing this using my laptop with the said PCMCIA card.

The problem is my nfs shares in /etc/fstab aren't automatically mounted. I have to run "sudo mount -a" each time I bootup the laptop to get them to be mounted. I suspect that what's happening is that my /etc/fstab is being loaded _before_ my wireless card is up and running.

How can I check this, what should I be looking for in my log files? More importantly, what can I do to resolve this issue? As I said I simply edited the /etc/network/interfaces file to get the card working, however should I actually manually install the RT61 driver? Do I need to blacklist the RT61 driver? I really don't know what to try next ...

:cool:

---

### Post by AndyCooll on 2007-06-19
Anybody able to help?

---

### Post by Austin_KW on 2007-06-19
you might adding the "mount -a" to /etc/rc.local which is run at the end of the boot sequence. If this is still too early you could batch the command with "at  now +2 min -f scriptfile"

---

### Post by AndyCooll on 2007-06-21
Just want to say thanks for your help. Still not sure why the nfs shares should mount before the wireless card is brought up. However adding the line to /etc/rc.local seems to be a fine workaround and works!

So thanks.

:cool:

---

