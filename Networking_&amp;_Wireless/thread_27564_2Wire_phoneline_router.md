---
title: "2Wire phoneline router"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by ate50eggs on 2005-04-16
I am connected to a HomePNA network with a USB adapter and I can't connect with ubuntu. I see the adapter in the device manager. When I pull up the network configuration box, I see dialup and ethernet (I have an ethernet card which is not plugged into anything) If I activate the ethernet, the box gets checked and remains checked, but I'm not really connected.

I checked out a similar problem here, ([http://www.ubuntuforums.org/showthread.php?t=9229](http://www.ubuntuforums.org/showthread.php?t=9229)) but that solution didn't work for me. Has anyone run into this? anyone know if USB hpna is supported at all?

(btw, I'm not 100% sure that I didn't just make some dumb mistake in the network configuration. I'm new to linux)

---

### Post by geekgod on 2005-04-18
have you tried ndis wrapper on the 2wire drivers [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
2wire uses the same drivers for all their usb devices so maybe taking the driver from support.2wire.com and ndiswrapper it will come to life..

---

### Post by ate50eggs on 2005-04-18
Ok, I've got the drivers and I've been reading about NdisWrapper, but I'm not exactly sure what to do. something like this [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper) mmaybe?

do I have to install ndiswrapper, or is it part of the standard ubuntu install?

---

### Post by ate50eggs on 2005-04-20
Ok, I followed the instructions here: [http://www.ubuntuforums.org/showthread.php?t=19978&highlight=ndiswrapper+usb+howto](http://www.ubuntuforums.org/showthread.php?t=19978&highlight=ndiswrapper+usb+howto)   but with the right drivers. afterwards I get:
*driver detected. hardware detected.*


[I]
#ndiswrapper -l [/I]
gives me something that sounds like my device


that sounds promising. 
[I]
#modprobe ndiswrapper[/I]

gives me an error. I didn't go past there.

---

