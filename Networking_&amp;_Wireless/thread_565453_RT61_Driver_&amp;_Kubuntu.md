---
title: "RT61 Driver &amp; Kubuntu"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by flushie86 on 2007-10-02
I recently installed Kubuntu on an old PIII 800 system, Kubuntu is recommended with LinixMCE, I wanna be wireless. I have an Airlink AWLH5025 MIMO XR wireless card, has the 2600 chipset. However the default driver in Kubuntu can see the card, can't configure it or connect to any networks! Whether they be WEP or WPA or OPEN. I decided to use the drivers on the disk for the card with ndiswrapper and it worked!! One problem, the drivers on the disk have the same name as the default driver and when I reboot the system the default drivers take over. I can't add the rt61 to the blacklist because I lose them both!

Is there anyway to remove the default rt61 driver?

---

### Post by unisol on 2007-10-02
use this command to remove the driver (as root):

Code:
ndiswrapper -e driver_name
modprobe -r <drivername>E.G.:
Code:
modprobe -r  name of wireless cardAnd load Ndiswrapper again (As root):

Code:
modprobe ndiswrapper

if it is listed in /etc/modules twice then;

It shouldn't be a problem if you have the same module listed in /etc/modules twice.
But if you have any problems, you can remove ndiswrapper from /etc/modules by using:
sudo cp /etc/modules /etc/modules-old
grep -v ndiswrapper /etc/modules | sudo tee /etc/modules

---

### Post by flushie86 on 2007-10-02
This did not work. The system still thinks it's using the default rt61 driver. Any other suggestions?

---

### Post by kevdog on 2007-10-02
Can you post the following:

lshw -C network
lspci -nn
modinfo rt61

Thanks

---

