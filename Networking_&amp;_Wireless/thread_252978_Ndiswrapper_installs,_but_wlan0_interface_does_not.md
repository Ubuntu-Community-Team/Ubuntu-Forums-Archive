---
title: "Ndiswrapper installs, but wlan0 interface does not exist."
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by Aninhumer on 2006-09-07
I am running the amd64 version of ubuntu-dapper, and whenever I install a ndiswrapper driver (mrv8335 or mrv8000c). The install is successful, there are no error messages when I modprobe ndiswrapper and lsmod shows ndiswrapper. However when I open the network settings dialog (or run ifconfig -a) no new interfaces are available.

I believe this is probably something to do with my new amd64 system. However I would have thought ndiswrapper would have warned me if the drivers wouldn't work, and they appear to do so.

If I need 64 bit drivers, where am I likely get them?
I have tried the marvell website, but it's very hard to navigate, and their driver search tool is impossible to use.

---

### Post by dbeckler on 2006-09-07
I am pretty sure you need 64 bit drivers.  The problem with this is that they are almost nonexistent.  I had to switch from 64 bit to the K7 kernel to get my wireless running.

---

### Post by Aninhumer on 2006-09-08
Is there no way of using 32bit drivers on a 64bit kernel?
Also is there any way of using 64bit apps on a 32bit kernel? (I'm guessing there isn't)

Hmm maybe I should consider buying a new wireless card?
Which are the most open brands?

---

### Post by amo-ej1 on 2006-09-08
you could also simply use a plain old 32 bit distro ;-), that how I solved it on my old 64 bit laptop. you don't need all that address space anyhow :p

---

### Post by cdgrocott on 2006-09-08
I'm having the same problem with 32-bit drivers on a 32-bit distro. 

I've followed pretty much every tutorial I can find for using ndiswrapper to install drivers for my card (Belkin F5D7000) and it all seems to work fine, except for the fact that wlan0 never shows up!

](*,)

---

### Post by UrbenLegend on 2006-09-08
I have the exact same card. If the ndiswrapper driver is installed correctly, Ubuntu should list the card as eth0. Try a 'iwconfig' and see if its listed. If that's the case, you'll have to edit your '/etc/iftab' file.

---

### Post by SFDD on 2006-09-10
Same here: 32bit distro on a 32bit machine. When ndiswrapper is installed, I see no wireless network connection. When I get rid of it, the connection comes back. Install it again, and it goes away. This leaves me using the bcm43xx driver (for a Dell 1300 wifi card), which works but constantly drops single intermittantly.

So, I'm thinking it's not a 64-bit issue.

---

### Post by cdgrocott on 2006-09-10
I could have sworn I'd replied to this, to let people know that I'd got it sorted, but obviously not...

The trick seems to be in blacklisting the bcm43xx driver. The full process is [described in detail here by jhuff]("http://ubuntuforums.org/showthread.php?t=187004"). Worked first time for me! :-D

Although it's worth noting that the device was installed as eth0 / eth1 /eth# , and not as wlan0 as reported by ndiswrapper.

---

