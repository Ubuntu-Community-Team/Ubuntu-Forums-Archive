---
title: "wireless setup for 10.04.3 LTS  64 bit"
date: 2013-12-07
forum: Networking &amp; Wireless
---

### Post by stevekramer99 on 2013-12-07
Hello,

I have recently installed 10.04.3 LTS 64 bit on a USB drive, and would like to set up wireless.  

I found under Network Interface (?) window that there were no wireless networks shown, only an option to add one.  I haven't connected to a wireless network before using Ubuntu, but I have a "dual boot" system with windows 7 and I do normally connect to wireless when Win7 is loaded.

This is the first time I have run Ubuntu, but I found some instructions elsewhere on the web.  I downloaded a driver from Broadcom I thought was the right one (tg3-3.129d?) and followed some instructions to install it but the result was nothing changed as far as the Network Interface connection options.  

The instructions were to unzip the driver tar file and copy into the src directory and then run a make command.  This apparently ran without error, but the result was no change in the wireless networks available as indicated on the Network Interface window.

I ran a nm-tool command which reported 802.11 WiFi, Driver wl, State: Disconnected.
I ran a lshw -C network command that reported:  Product:  BCM4311 802.11b/g WLAN.

I would really appreciate if someone possibly guide me through setting up wireless with Ubuntu or provide supporting information?

thanks!
steve

---

### Post by mikewhatever on 2013-12-07
Check out the [Broadcom wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"). You might also want to know that 10.04 is no longer supported.

---

### Post by varunendra on 2013-12-07
Welcome to the forums stevekramer99 ! :)

The tg3 driver is for Ethernet, not wireless, and the "wl" driver you have currently installed is not correct for BCM4311 cards. The correct driver b43 is already present in the kernel but needs a proprietary firmware to work.

To remove the "wl" driver and install the firmware to make your wireless work, please do the following -

Open a terminal (Ctrl-Alt-T) and purge the "wl" driver with this command -
```
sudo apt-get purge bcmwl-kernel-source
```

Then download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/saucy/all/linux-firmware-nonfree/download)

Copy the downloaded .deb file to your Ubuntu desktop and double-click it to install. Reboot to get a working wireless.

**PS:**
Like Mike said, 10.04 desktop is no longer supported. So it is strongly recommended to install the latest LTS (12.04.3) unless you have a good reason to stick with an outdated version.

---

