---
title: "[SOLVED] rt2870"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by dse.37 on 2008-06-22
I was wondering if somebody here kind enough with experience on this driver could hold my hand on this one.

I'm by no means senseless, but I don't quite understand the readme to the Ralink Tech 2870 driver found [_here_]("http://www.ralinktech.com/ralink/Home/Support/Linux.html").

The parts I'm having trouble with are:

> define the linux kernel source include file path LINUX_SRC
modify to meet your need.

and

> In os/linux/config.mk 
define the GCC and LD of the target machine
define the compiler flags CFLAGS
modify to meet your need.
** Build for being controlled by NetworkManager
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
** Build for being controlled by WpaSupplicant with Ralink Custom Event
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

What does it mean by define the kernel source and where can I find it if I do need to define it? And I don't even know where to begin with the second lot of quoted text, but starting off with explaining what the GCC and LD of the target machine as well as what the CFLAGS are would be a good start.

I'm currently using Gusty with the kernel version 2.6.22-15. The only protection I have on my router is mac address filtering and the fact that the ssid is hidden which is more than enough too keep the monkeys out around here.

Again, thanks in advance to any help provided.

---

### Post by chili555 on 2008-06-22
> define the linux kernel source include file path LINUX_SRC
modify to meet your need. I think, if you have *linux-headers-generic* and *build-essential* installed, it will find the path without any help; it did on my system.> In os/linux/config.mk
define the GCC and LD of the target machine
define the compiler flags CFLAGS
modify to meet your need.
** Build for being controlled by NetworkManager
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
** Build for being controlled by WpaSupplicant with Ralink Custom Event
Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d Since you don't have WPA and may not want it, we can safely skip the latter part. If you intend to allow Network Manager handle your wireless, you should *cd 2870/2008_0528_RT2870_Linux_STA_v1.3.0.0/os/linux* and *sudo gedit config.mk* and go down to line 11 and change:```
HAS_WPA_SUPPLICANT=n
```to:```
HAS_WPA_SUPPLICANT=y
```Then go to line 14 and change:```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```to:```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```Then proofread, save and close gedit. Next, *cd /2870/2008_0528_RT2870_Linux_STA_v1.3.0.0* and run:```
sudo make

```Then follow the remaining steps in the README_STA.

Post back if you get stuck.

---

### Post by dse.37 on 2008-06-23
Thank you kindly, sir. My Belkin Wireless N USB dongle now works with a significantly better connection than my old rtl8187 dongle chipset. The only problem I have now is when I iwconfig to see if everything is working correctly it shows that my mac address is still that of my old rtl8187 card even though it's unplugged.

That's a minor detail though. It doesn't seem to be causing any problems at the moment.

Again thank you for your time and support.
It's greatly appreciated.

---

### Post by lukemack on 2008-06-28
I'm also using this driver. The documentation is terrible from an Ubuntu point of view when it comes to loading the module at boot.

Can you share where you copied the ko file to and how you got it loading at boot (if you have)?

thanks

---

### Post by chili555 on 2008-06-28
Although it's not mentioned, that I can see, in the README, if you run:```
sudo make install
```it puts the module in the right place. It should load after reboot, but if not, post back and I'll show it my crowbar.

---

### Post by lukemack on 2008-06-29
thanks - that sorted it.

---

### Post by lukemack on 2008-07-04
Although the module loads at boot, I still have to do 'sudo ifconfig ra0 down' then 'sudo ifconfig ra0 up', then disable and enable networking in network manager to get the connection to come up.

any ideas how I can automate this?

thanks,

lukemack.

---

### Post by chili555 on 2008-07-04
Try this, instead:```
sudo /etc/init.d/networking restart
```If that works, we can automate it.

---

### Post by lukemack on 2008-07-04
that doesn't work - the only way I can get it to work is the way i described above.

---

### Post by nickolasemp on 2008-07-08
Should I post my [problem]("http://ubuntuforums.org/showpost.php?p=5346272&postcount=15") here? That would be spamming, no? Still, I have a problem with my Ubuntu 8.04.

I still don't understand how it is SOLVED..? Could you help over [there]("http://ubuntuforums.org/showthread.php?p=5346272")?

Thank you a lot in advance...

---

### Post by nightalon on 2008-08-16
I'm copying the custom MacBook Pro Madwifi installation instructions in case we can learn from them:

sudo apt-get install build-essential subversion automake autoconf
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
cd madwifi
make
sudo make install
**sudo sed -i~ 's/^exit 0/modprobe ath_pci\nexit 0/' /etc/rc.local**
**sudo sed -i~ 's/^exit 0/modprobe wlan_scan_sta\nexit 0/' /etc/rc.local**
**sudo sed -i~ 's/^exit 0/iwpriv ath0 bgscan 0\nexit 0/' /etc/rc.local**

Then there's a break (as at this point the driver is allegedly functioning, since it's been "dropped" into the running kernel)

[B]sudo modprobe ath_pci
sudo modprobe wlan_scan_sta
sudo iwpriv ath0 bgscan 0[/B]

I understand that this is a bit different since Atheros employs a Hardware Abstraction Layer or HAL...still-what do these configuration steps mean exactly?

---

### Post by lukemack on 2008-08-17
If you are trying to get the rt2870 working, DO NOT FOLLOW THE STEPS IN THE PREVIOUS POST. This will install madwifi drivers for completely the wrong wireless card.

---

