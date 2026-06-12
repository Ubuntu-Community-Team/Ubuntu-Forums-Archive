---
title: "Didnt configure Network on install, how do i do now?"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by ebichuhamster on 2007-03-04
Basiccally thats it.  I was having trouble with the whole installation at the beginning, so when it couldnt detect DHCP settings automatically i told it to skip the step.  After 2 weeks i finally got the window manager to load and all i need is to configure this network settings so that i can connect to the internet with the actual ubuntu (b/c up untill now i've been booting/rebooting for the internet)

I tried right click-configure on the network icon in the task bar but that didn't seem to do it.  I suspect there's some kind of code for the terminal that allows me to do this? 
I have to say that I'm a newbie so i wont be familiar to most specifications, so if anyone can explain it real nice and slow I'll be very grateful. ^_^

---

### Post by solar george on 2007-03-04
In the system menu you have an option called networking - this should let you set it up.

---

### Post by fishymark27 on 2007-03-13
I did a similar thing, and I can't configure via the networking window. 

 I've tried

ifconfig eth0 down
ifconfig eth0 up
dhclient eth0

and this does work. But I have to do it everytime I start up the computer. Is there a way of making this permanant in the startup?

(I'm new to this whole thing)

---

### Post by lloyd_b on 2007-03-13
(Note: There is a way to do this via the GUI, but I'm a command-line junkie:) )

Edit the file "/etc/networking/interfaces".  Note: You'll need superuser permissions to do this, so I recommend opening a terminal window, and typing "sudo nano /etc/networking/interfaces" or "gksudo gedit /etc/networking/interfaces"

Check if there's any reference to "eth0".  If so, make sure they look like this:
```
auto eth0
iface eth0 inet dhcp
```

If there's no references to eth0, then just add these lines to the file.

The next time you reboot, the eth0 interface should start up automatically.

Lloyd B.

---

