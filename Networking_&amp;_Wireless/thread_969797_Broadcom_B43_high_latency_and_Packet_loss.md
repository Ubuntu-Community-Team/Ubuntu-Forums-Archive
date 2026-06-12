---
title: "Broadcom B43 high latency and Packet loss"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by johnehowe on 2008-11-03
I am still having issues with my Broadcom B43 (4311) wireless card despite doing all of the obvious upgrades to the b43-fwcutter driver and firmware. It is working but I am still getting high latency times (Avg 14ms) and 2+% packet loss. If I use an PCMCIA NetGear wg511 card then all is well. Anyone have any ideas for improving this?

---

### Post by Ayuthia on 2008-11-03
> **johnehowe said:**
> I am still having issues with my Broadcom B43 (4311) wireless card despite doing all of the obvious upgrades to the b43-fwcutter driver and firmware. It is working but I am still getting high latency times (Avg 14ms) and 2+% packet loss. If I use an PCMCIA NetGear wg511 card then all is well. Anyone have any ideas for improving this?

Which revision of the 4311 card do you have (lspci -nn)?  Also which kernel are you using (uname -r)?

You might even try the wl driver (Broadcom STA) if you have no issues with using a prorietary driver.

---

### Post by johnehowe on 2008-11-03
Sorry, I did not include 

[B]Rev 2

2.6.24-21-generic[/B]


01:02.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

---

### Post by Ayuthia on 2008-11-03
> **johnehowe said:**
> Sorry, I did not include 

[B]Rev 2

2.6.24-21-generic[/B]


01:02.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

You might try Intrepid.  The 2.6.27 kernel uses newer firmware and has some improvements in signal and transmission.

14e4:4319?  That is a new one for me!  If it is really a 14e4:4319, it might not work with the wl driver.  I don't recall seeing that number anywhere.

---

### Post by johnehowe on 2008-11-03
I would prefer not to use a proprietary driver but if it fixes the problem then we have to do what it takes, right! :) Can you point me in the right direction for the wl driver (Broadcom STA) that you reference.

---

### Post by Ayuthia on 2008-11-03
It should be in System->Administration->Hardware Drivers.  Just select the Broadcom STA option.  If it is not there, you might check and see if the module is already there:
```
sudo updatedb
locate wl.ko
```
It should be in /lib/modules/2.6.24-21-generic/volatile if I recall correctly.

---

### Post by johnehowe on 2008-11-03
> **Ayuthia said:**
> It should be in System->Administration->Hardware Drivers.  Just select the Broadcom STA option.  If it is not there, you might check and see if the module is already there:
```
sudo updatedb
locate wl.ko
```
It should be in /lib/modules/2.6.24-21-generic/volatile if I recall correctly.


When I ran the above commands the db is updated but the wl.ko appeared to do nothing. Looking in Hardware Drivers the only driver listed is the B43 that I am currently using that is having issues. Any further assistance would be appreciated. I am so close to getting the Broadcom to work correctly.

---

### Post by Ayuthia on 2008-11-03
> **johnehowe said:**
> When I ran the above commands the db is updated but the wl.ko appeared to do nothing. Looking in Hardware Drivers the only driver listed is the B43 that I am currently using that is having issues. Any further assistance would be appreciated. I am so close to getting the Broadcom to work correctly.

Unfortunately, my child has overtaken my laptop that has Intrepid and an updated Hardy so I cannot see what the next steps should be exactly.  I think that there is a file in /etc/init.d called linux-restricted-modules.  You might try to see if you can start it:
```
sudo /etc/init.d/linux-restricted-modules restart
```That might bring it up for you.  If not, there is a way where you can compile the drivers yourself:
[http://ubuntuforums.org/showthread.php?t=896713](http://ubuntuforums.org/showthread.php?t=896713)

---

### Post by johnehowe on 2008-11-03
I am on the right path with your help. I was able to get the Broadcom working great once prior to a reboot. I was able to get it to use the BCM43xx instead of the newer B43 in Synaptics. However, I can not get it to work again. It keeps wanting to use the B43 in Hardware Drivers. How can I clear the B43 out of Hardware Drivers and get it to enable the older 43xx. Each time that I enable in Hardware drivers it is installing the B43 instead of using the BCM43xx that I installed in Synaptics.

---

### Post by Ayuthia on 2008-11-03
> **johnehowe said:**
> I am on the right path with your help. I was able to get the Broadcom working great once prior to a reboot. I was able to get it to use the BCM43xx instead of the newer B43 in Synaptics. However, I can not get it to work again. It keeps wanting to use the B43 in Hardware Drivers. How can I clear the B43 out of Hardware Drivers and get it to enable the older 43xx. Each time that I enable in Hardware drivers it is installing the B43 instead of using the BCM43xx that I installed in Synaptics.

You will need to blacklist the b43 driver:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -u
```
You will also need to check and see if you have the b44 module.  It is the Broadcom 44xx series of the wired ethernet card.  If you do, you might need a workaround to avoid having the ssb module interfere with your bcm43xx driver.

I did not blacklist the ssb module in hopes that the b43 module being blacklisted will prevent the need of the ssb module loading.  My understanding is that only the b43 and b44 modules load the ssb module.

---

### Post by johnehowe on 2008-11-04
I had blacklisted the B43 but it keeps showing up in the Hardware Drivers and what appears that it continues to be used despite my attempts to uninstall in Synaptic and only install the BCM43xx in Synaptic. Funny thing is that it may be using the BCM43xx that is installed as well because the issues has much improved (see Below)

5776 packets transmitted, 5599 received, **3% packet loss**, time 28274710ms
rtt min/avg/max/mdev = 0.277/**2.677**/884.216/33.777 ms

---

### Post by Ayuthia on 2008-11-04
> **johnehowe said:**
> I had blacklisted the B43 but it keeps showing up in the Hardware Drivers and what appears that it continues to be used despite my attempts to uninstall in Synaptic and only install the BCM43xx in Synaptic. Funny thing is that it may be using the BCM43xx that is installed as well because the issues has much improved (see Below)

5776 packets transmitted, 5599 received, **3% packet loss**, time 28274710ms
rtt min/avg/max/mdev = 0.277/**2.677**/884.216/33.777 ms

If that is the case, you will need to blacklist the ssb module also:
```
echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist
sudo update-initramfs -u
```

You will also need to go into /etc/modprobe.d/blacklist and comment out the bcm43xx line:
```
gksu gedit /etc/modprobe.d/blacklist
```
Look for:
```
blacklist bcm43xx
```
and make it look like:
```
#blacklist bcm43xx
```

You might also want to have /etc/modules load the bcm43xx driver too:
```
echo bcm43xx | sudo tee -a /etc/modules
```

---

### Post by johnehowe on 2008-11-04
Well the results and performance was worse with the BCM43xx. The best performance that I can get out of the card was by upgrading as follows:

- sudo apt-get install b43-fwcutter
- wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
- tar -xjf broadcom-wl-4.80.53.0.tar.bz2
- cd broadcom-wl-4.80.53.0/kmod
- sudo b43-fwcutter -w /lib/firmware wl_apsta.o
- sudo rmmod b43
- sudo modprobe b43

- Close the terminal and reboot

Note: This driver will only work on Linux kernel 2.6.24 or older. To find out what kernel version you have, type uname -r into a terminal. As of this time Hardy Heron (8.04) uses 2.6.24, so unless you have manually installed a newer kernel, the above steps will work for you.

**Updating the Firmware on the Wireless Card:**

Ensure the following before Proceeding:
Kernel : Linux-2.6.24, including 2.6.24-rcX and 2.6.24.Y or older

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

---

