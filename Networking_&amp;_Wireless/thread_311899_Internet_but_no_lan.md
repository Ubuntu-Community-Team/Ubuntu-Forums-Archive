---
title: "Internet but no lan"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by mrcrud12 on 2006-12-03
Hi!

I've just installed Ubuntu 6.06 on a Toshiba satellite laptop and everything worked fine until i tried to use my wireless network. 

It's WPA protected and up to now I've tried network-manager-gnome and wifi-radar.

Both allow me to connect to the internet without any problem, however, i cant reach the other machines on my local network ( one windows laptop and one wired Ubuntu web/file server ). 

When i put the ip of my server in Firefox, it times out. Ping doesn't work either way.

Where could the problem be?

Thanks!

---

### Post by Mitush on 2006-12-27
I have exactly the same problem. Did you find a solution yet?

---

### Post by mrcrud12 on 2006-12-27
didn't find a solution. Just reinstalled Ubuntu. Lan and internet works fine now, as long as it's wired.

My wifi is WPA2 Personal, and i just cant get Ubuntu to cooperate. I've tried network-manager-gnome, wifi-radar, kwlan to no avail...

---

### Post by Mitush on 2006-12-27
It must be some router settings. I have Linksys WRT54GL. Wireless (laptop) and wired (desktop) internet are fine but I still cannot ping hosts on the LAN. I am using 128-bit WEP key for wireless. Thinking about changing the firmware on the router...

Saw something similar [here]("http://www.wrtforums.com/viewtopic.php?t=1382&sid=93dc5b33f43e4503f7ab78261817328e")

---

### Post by Mitush on 2006-12-28
It might be that the wireless hosts are not actual nodes in the "switch part" of the WRT54GL. In this case, I guess, it would be in principle impossible to ping/access wired/wireless hosts from a wireless node.

---

