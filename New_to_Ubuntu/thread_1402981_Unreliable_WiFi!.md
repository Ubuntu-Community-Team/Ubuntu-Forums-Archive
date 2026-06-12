---
title: "Unreliable WiFi!"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by gerryex on 2010-02-09
Hi ALL,
 
I'm continuing to explore Ubuntu on my dual booted (Win 7/Ubuntu) Acer laptop and in general its working pretty well. But I am definitely getting poor results from the WiFi. I know its not the laptop as when I boot into Win 7, the signal strength never falls below 90% and the signal never drops out.
 
In Ubuntu, once I enter the keyring password it makes connection quickly. The initial signal strength is around 88% and one time I even saw 100%. But within a minute or two it drops down to about 40% and sometimes as low as 32%. The connection still works but the signal strength usually stays around 35 - 45%. I know the orientation of the laptop can affect the signal but as a comparison I re-booted into Win 7, without changing the orientation and again the Win 7 signal was never below 90%.
 
Continuing on with Ubuntu, the signal strength remains about 35-45 but then all of a sudden it will loose the connection. The icon shows the twirling pinwheel but it almost never re-connects. When I click on the icon it asks me for the encryption phrase (which it obviously had before) which I enter but it still does not re-connect. When I re-boot it instantly connects and the lowering strength cycle begins again.
 
I read about a different network manager called Wicd and I installed it but that was worse! It seemed to get past the authentication phase but then it failed saying it could not get an IP address (even though with the original network manager that was never a problem). I never was able to connect with Wicd so I removed it but I couldn't figure out how to reinstall the original manager so I ended up re-installing Ubuntu itself (this is another story!!!).
 
So what kinds of things can I look at to get better operation with WiFi?
 
Thanks,
Gerry

---

### Post by nuffink666 on 2010-02-09
Well first of all being a fellow acer owner myself I would like to suggest that you check what wifi adaptor you have and that you have the correct modules loaded for it. If like me you have a Broadcom I found mine was a BCM4311 and found this site which tells you all about how to get the right stuff for Broadcom adaptors. If of course it isn't then please give more details on what your hardware is. 

[http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy](http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy)

---

### Post by Geoff918 on 2010-02-09
> **nuffink666 said:**
> Well first of all being a fellow acer owner myself I would like to suggest that you check what wifi adaptor you have and that you have the correct modules loaded for it. If like me you have a Broadcom I found mine was a BCM4311 and found this site which tells you all about how to get the right stuff for Broadcom adaptors. If of course it isn't then please give more details on what your hardware is. 

[http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy](http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy)

In regards to the hardware, the easiest way to tell (and it's pretty, too) is with the following:

sudo lshw -html > hardware.html

Then you can open the resulting HTML file with your browser and it will have all the details.

You could also use:

lsusb
-or failing that-
lspci

I like the first option most, though.

---

### Post by gerryex on 2010-02-10
> **nuffink666 said:**
> Well first of all being a fellow acer owner myself I would like to suggest that you check what wifi adaptor you have and that you have the correct modules loaded for it. If like me you have a Broadcom I found mine was a BCM4311 and found this site which tells you all about how to get the right stuff for Broadcom adaptors. If of course it isn't then please give more details on what your hardware is. 
 
[http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy](http://wireless.kernel.org/en/users/Drivers/b43#b43_and_b43legacy)
 
Hi nuffink666,
 
My Acer does not use a Broadcom WiFi adaptor but rather uses one from Atheros Comm Inc. Interestingly I get two different part numbers reported by Ubuntu and Win 7. In Ubuntu it says its an AR928X Wireless Network Adaptor (PCI-Express) but Win 7 tells me that it an Atheros AR5B93 Wireless Network Adaptor.
 
Either way, its not a Broadcom. Where would I check for the driver that is currently running and where would I go to see if there is a new version of the driver?
 
Thanks,
Gerry

---

### Post by bkratz on 2010-02-10
You might want to check out this posting if it is a 928X

[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

---

### Post by gerryex on 2010-02-10
> **bkratz said:**
> You might want to check out this posting if it is a 928X
 
[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)
 
Hi bkratz,
 
WOW!! That worked!!! The signal strength has been reading 90% or higher since I re-booted after installing the packages indicated in the above post, and that been at least for 20 minutes or so. Before the packages were installed the reading would start out good but within a minute or so the reading would drop to only 35-45!
 
I only wish I knew what it did! I'm a retired software engineer and I've been using Windows ever since Win ver 3 so I'm pretty familiar with the Windows environment. While I used Unix many (many!!) years back, I'm still mostly lost in Ubuntu. What were those packages that were installed. Were they drivers for older hardware, but if so my loptop is brand new and I would assume the WiFi adaptor would be fairly modern. How would a normal human being even know to install those packages?
 
Is there an equivalent to the Windows Device Manager in Ubuntu? If not how do you find out what driver is associated with each piece of hardware. Are there any tutorials about drivers?
 
Thanks,
Gerry

---

### Post by bkratz on 2010-02-10
Well congratulations! It should stay that way. Here is something on backports

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

will look for answers to the other questions.  Please go to the thread tools and mark as solved in case it helps someone else.

---

### Post by bkratz on 2010-02-10
This looks interesting, I haven't read it yet, but will!

[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-display-system-hardware-information.html)

---

