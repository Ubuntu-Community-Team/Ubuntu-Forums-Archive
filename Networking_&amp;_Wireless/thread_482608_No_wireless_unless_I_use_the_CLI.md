---
title: "No wireless unless I use the CLI"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2007-06-23
When I power on my computer, my wireless is not active ( no light, no wireless detected ). I have to type "sudo modprobe bcm43xx" and it turns on and works flawlessly. I can reboot and it still works, until I power down. Power up and go to terminal and type the command.
I read up on modprobe [from this site]("http://www.die.net/doc/linux/man/man8/modprobe.8.html"), but I am a little lost on what it actually accomplishes.
What can I do to fix this?
Thanx in advance!

---

### Post by kevdog on 2007-06-23
What does your /etc/modprobe.d/blacklist file say??

---

### Post by lsutiger on 2007-06-23
Thanx! It was blacklisted, from a different install I tried for the driver. Removed, rebooted and it worked....what a community :D

---

