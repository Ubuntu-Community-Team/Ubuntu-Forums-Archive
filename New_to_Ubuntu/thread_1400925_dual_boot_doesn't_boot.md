---
title: "dual boot doesn't boot"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by itamar0409 on 2010-02-07
hi,
i'm new to ubuntu and i suck at computers. i would like to learn though.  
i tried to dual boot ubuntu (using wubi) with microsoft xp home edition (32 bit).
had choice to boot windows xp or ubuntu and chose ubuntu.
computer looked like it was working, i even saw an ubuntu sign go up on screen. then there were more commands and then...nothing...for a while. is this normal? if not what do i do. this is the first time i ran it so does that mean that ubuntu is not fully installed yet?
(i have a gut feeling, i don't know why, that there is an issue with the video card - ati radeon 7000).  fyi - i also tried booting with a disk of an older version of kubuntu debian 1.3-5 and it just took me to a command line. 
i have pentium 4 cpu 1.60 ghz
1.25 gb ram
intel desktop board model : d845hv
if you need additional information regarding my system i will be happy to provide it. can anyone help me find what the issue could be ?
thanks for your help,
itamar

---

### Post by Eredeath on 2010-02-14
I would try re-installing. And if that doesn't work can you get to a command prompt by holding <alt><ctrl> and F2?

---

### Post by itamar0409 on 2010-02-15
hi,
thanks for getting back to me.
i got it running by running the install on safe graphics mode. which worked.
but then i only had two resolutions to pick from.
i tried to correct this by running in recovery mode:
dpkg-reconfigure xserver-xorg 
but 
a)the program only let me reconfigure my keyboard
b) when i rebooted the screen went black and i didn't see anything for a while.  
i reinstalled version 9.04 on a safe graphics mode (i did so not with wubi but the actual cd and made real partition.
2 problems now. 
1. i only have two resolutions to pick from and they are not big enough.
2. i think the computer is running slow. 
maybe they are both related to a problem with the graphics card?
when running: sudo lshw -html > ~/hardware.html
my graphics card is greyed out:
--------------------------------------------
id:	
display
description: 	VGA compatible controller
product: 	Radeon RV100 QY [Radeon 7000/VE]
vendor: 	ATI Technologies Inc
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	agp agp-2.0 pm bus_master cap_list
configuration:	
latency	=	32
mingnt	=	8
-----------------------------------------------

i don't know if it helps but i'll list the other hardware that is greyed out:

----------------------------------------------
id:	
serial
description: 	SMBus
product: 	82801BA/BAM SMBus Controller
vendor: 	Intel Corporation
physical id: 	
1f.3
bus info: 	
pci@0000:00:1f.3
version: 	12
width: 	32 bits
clock: 	33MHz
configuration:	
latency	=	0
-------------------------------------------------
id:	
communication
description: 	Communication controller
product: 	HCF 56k Data/Fax Modem
vendor: 	Conexant Systems, Inc.
physical id: 	
a
bus info: 	
pci@0000:02:0a.0
version: 	08
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
latency	=	32
-------------------------------------------------
also one device is red
--------------------------------------------
id:	
network
description: 	Ethernet interface
physical id: 	
1
logical name: 	
pan0
serial: 	3e:44:fd:05:6d:e0
capabilities: 	ethernet physical
configuration:	
broadcast	=	yes
driver	=	bridge
driverversion	=	2.3
firmware	=	N/A
link	=	yes
multicast	=	yes
----------------------------------------------


thanks,
itamar

---

### Post by Eredeath on 2010-02-15
It seems as though it might be a driver issue. Check out this thread: [http://http://ubuntuforums.org/showthread.php?t=570382]("http://http://ubuntuforums.org/showthread.php?t=570382")

---

