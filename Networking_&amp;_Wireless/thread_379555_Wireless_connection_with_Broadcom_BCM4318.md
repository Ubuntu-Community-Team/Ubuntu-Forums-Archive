---
title: "Wireless connection with Broadcom BCM4318?"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by wildzer0 on 2007-03-08
I just installed Edgy on my laptop and I'm not able to make the wireless work. I see that the network controller is not on the supported list, does that mean I'm just flat out of luck? I don't know a ton about linux but was interested in trying it out - this is definitely a deal breaker though if I can't get wireless to work. I'm using an HP Pavilion DV1000. Any help would be greatly appreciated!

If it helps, lspci gets me this:

06:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless Lan Controller (rev 02)
Subsystem: Hewlett-Packard Company Unknown Device 1355
Flags: bus master, fast devsel, latency 32, IRQ 4
Memory at b0104000 (32-big, non-prefetchable) [size=8K]

---

### Post by srt4play on 2007-03-08
Try this howto:  [http://www.ubuntuforums.org/showthread.php?t=285809]("http://www.ubuntuforums.org/showthread.php?t=285809")

---

### Post by Floppyjoe on 2007-03-08
I have a tutorial on the Broadcom 4318 in my signature.

---

### Post by wildzer0 on 2007-03-08
Thank you for those links! That got me much closer. I can get as far as actually trying to connect using the wireless assistant, but I get a message that says "Connection failed. Please consult README about broadcast address" 

I'm booted into XP right now so I don't have the exact logs, if you need it, I can work with a wired connection to post them.

---

### Post by Floppyjoe on 2007-03-08
> **wildzer0 said:**
> Thank you for those links! That got me much closer. I can get as far as actually trying to connect using the wireless assistant, but I get a message that says "Connection failed. Please consult README about broadcast address" 

I'm booted into XP right now so I don't have the exact logs, if you need it, I can work with a wired connection to post them.

When I first got my wireless working on my laptop I had all kinds of problems getting the different wireless connection programs working. Most of the time they wouldn't connect. I eventually settled on Network Manager to do the job for me. The different programs will conflict with each other if you have more than one installed. To get network manager to work properly I found that I needed to disable all the network interfaces in System/Administration/Networking. On top of that i commented out all the network interfaces except for the lo interface in /etc/network/interfaces.

---

### Post by jml on 2007-03-08
That's what worked for me as well.  network-manager and network-manager-gnome was what finally worked for me.

Joe

---

### Post by srt4play on 2007-03-15
> **wildzer0 said:**
> Thank you for those links! That got me much closer. I can get as far as actually trying to connect using the wireless assistant, but I get a message that says "Connection failed. Please consult README about broadcast address" 

I'm booted into XP right now so I don't have the exact logs, if you need it, I can work with a wired connection to post them.

Have you had any luck with this?

---

