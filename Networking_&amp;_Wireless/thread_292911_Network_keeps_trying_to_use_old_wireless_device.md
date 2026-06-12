---
title: "Network keeps trying to use old wireless device"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by boz on 2006-11-04
Greetings,

I was using the rt2500 driver for my WUSB54G v4 device, but I was getting tired of it freezing my system all the time so I changed to the Windows driver.  After I did that, Ubuntu automatically created a new device called wlan0 and claims that it can't find the old device rausb0.  However, it keeps trying to use the old device and I can't make any connections with the new device.  When I click on the network icon on the top right, I get
```
SIOCGIFFLAGS error: No such device
```
I have wlan0 set as my default device and I'm sure it's configured correctly.  I go though all the necessary steps by configuring and activating the device through the GUI.  I've deleted all of the lines pertaining to the old device and added lines for the new device in /etc/network/interfaces and I've even executed
```
sudo iwconfig wlan0 essid ******** mode Managed
```
from the command line.  I'm fresh out of ideas, but I'm still a bit new to linux and wireless-tools.  If anyone can help, I would appreciate it.

Kelly

---

### Post by Dr. Nick on 2006-11-04
By windows srivers you mean ndiswrapper?

You may need to unload and blacklist the rt2500 driver, run **lsmod** and see if its loaded, If so then do 

sudo modprobe -r **module_name**

---

### Post by TiredBird on 2006-11-05
You might also look at '/etc/iftab'. udev, a program that reviews all device names assigned by the kernel, (and changes some of them), uses this file to assign the names to your interfaces. Look at that file and make sure that the names are properly matched to the mac addresses of the cards.

---

### Post by boz on 2006-11-05
Dr Nick,
The rt2570 driver is blacklisted.  I double-checked with the commands you supplied.  Thank you.

TiredBird,
I checked iftab and wlan0 isn't listed.  Neither is rausb0 (the old device).  Does this mean the driver is installed correctly?  Can I just add my device to this file, or is it more involved than that?

Thanks.

---

### Post by TiredBird on 2006-11-05
I have to admit, I really don't know. But I think it's safe to assume that in the '/etc/iftab' file you need one line for each hardware network interface you have. See 'man iftab'.

I have deduced that that file provides symbolic names for the network hardware interfaces. Assuming you have one hardwire and one wireless interface, you should have two lines in there.

The symbolic names in that file tie to the symbolic names used in the '/etc/network/interfaces' file. Of course there's going to be an 'lo' reference in the 'interfaces' file that doesn't have an equivalent in 'iftab' because that's the loopback interface. Otherwise there should be a one-to-one correspondance. 

I put together a 'howto' for another interface, [(which is located here)]("http://www.ubuntuforums.org/showpost.php?p=1707809&postcount=1"), but the last part of it relating to 'iftab' and 'interfaces' should apply to your situation as well. You might want to look at the last part of that post.

---

### Post by boz on 2006-11-05
Thanks again.  I tried what you said, but nothin' doing.  I uninstalled the driver and installed one of a different date and - blammo! - it worked.  My conclusion:  ndiswrapper is hit-and-miss, but it's definitely better than nothing.

---

