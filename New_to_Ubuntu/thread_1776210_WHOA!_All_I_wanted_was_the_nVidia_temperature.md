---
title: "WHOA! All I wanted was the nVidia temperature"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2011-06-05
I was trying to install the panel applet that shows my nVidia graphics card temperature. I looked at "Additional Drivers" and see that there are two choices. The "green light" is on an NVIDIA card that reads: 

(version current) [Recommended]

BUT, the green light that should be at the bottom (over the help radio button) is NOT green, which could mean:

"This driver is not activated"

Trying to solve this without having to ask others, I came across: 

Nvidia driver activated but not currently in use (11.04)
[http://ubuntuforums.org/showthread.php?t=1743386](http://ubuntuforums.org/showthread.php?t=1743386)

and read down to post #9 by ebbr.bugs. He shows a link to his post at:

[http://ubuntuforums.org/showpost.php?p=10742896&postcount=4](http://ubuntuforums.org/showpost.php?p=10742896&postcount=4)

which is very short and I quote it here -in red color for clarity:

[COLOR="Red"]Your problem is that you have the nvidia driver installed as a deb package but not the driver itself, for which you need the kernel headers. 
Install the package kernel-headers-blabla corresponding to your current kernel (see uname -a). Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel - this will force the creation of the nvidia kernel module. Reboot.

Those commands:
sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae[/COLOR]

I looked in my Synaptic package manager and saw that those above two packages are NOT installed on my computer:

linux-headers-2.6.38-8-generic-pae
linux-image-2.6.38-8-generic-pae

I now have them installed, but cannot understand what Mr. ebbr.bugs means by:

[COLOR="Red"]Then do install --reinstall of the nvidia package or install --reinstall of the linux kernel -[/COLOR]

Can someone please tell me how to do this so I do NOT harm my otherwise working system?

---

### Post by Quackers on 2011-06-05
In Additional Drivers you want the one that's "recommended" to have the green light next to it.
If you have a Nvidia graphics card and the correct driver installed you should be able to view the graphics card's temp in the Nvidia Settings screen.

---

### Post by Mark_in_Hollywood on 2011-06-06
As it stands, I'm grossly confused. Currently my Additional Drivers shows two green lights, one top and one bottom.

Top is in front of

NVIDIA accelerated graphics driver (version current) [Recommended]

and the bottom green light:

This driver is activated but not currently in use.

HOWEVER, I have the lm-sensors installed, ran sudo sensors detect, rebooted and now have the GPU temp in the panel applet. Also the NVIDIA X Server Settings appears in the menu, too!

GO FIGURE!

---

