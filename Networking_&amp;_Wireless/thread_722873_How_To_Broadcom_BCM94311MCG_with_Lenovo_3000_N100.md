---
title: "How To Broadcom BCM94311MCG with Lenovo 3000 N100"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by Integration on 2008-03-12
This for Ubuntu Gutsy:

Run this command if you get BCM94311MCG as your card this should work. This is being re-written specifically for the Lenovo 3000 N100 from another place I found on the web for a different laptop. So if you have a different brand of laptop you will be taking your chances. This is what worked for me:

```
lspci | grep Broadcom\ Corporation
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

This is howto install driver “BCM94311MCG wlan mini-PCI” in my notebook, Lenovo 3000 N100

   1. First step, you must uninstall ndiswrapper & bcm43xx-fwcutter

```
          sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
          sudo apt-get remove bcm43xx-fwcutter
```

   2. Add bcm43xx to the /etc/modprobe.d/blacklist file

```
          sudo vim /etc/modprobe.d/blacklist
          add this line “blacklist bcm43xx” (without “”)
```

   3. Reboot
   4. Download driver for BCM94311MCG wlan mini-PCI here: [http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html") ( if this link expire or not found, you can contact me :) )

```
          tar -xzvf WLANBroadcom.tar.gz
          move the folder WLANBroadcom to your home directory
          mv WLANBroadcom/ /home/yourname/
```

   5. Install ndiswrapper from source :

```
          sudo apt-get update
          sudo apt-get install build-essential
          sudo apt-get install linux-headers-`uname -r`
          sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
          mkdir -p ~/bcm43xx/ndiswrapper
          cd ~/bcm43xx/ndiswrapper
          sudo wget sudo wget http://internap.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.49.tar.gz

```
```
          tar xvzf ndiswrapper-1.49.tar.gz
          cd ndiswrapper*
          make distclean
          make
          sudo make install
```

   6. Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper

```
          sudo ndiswrapper -r bcmwl5
          cd /home/yourname/WLANBroadcom/
          sudo ndiswrapper -i bcmwl5.inf
          ndiswrapper -l

          sudo vim /etc/modules
          add this line “ndiswrapper” (without “”)

          sudo modprobe ndiswrapper
          sudo ndiswrapper -m
```

Once I again I just modified this I don't take credit for the whole thing but my wifi is working now :D

---

### Post by tfarinella on 2008-07-20
i did this now i get

```

thomas@tomslaptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

thomas@tomslaptop:~$ sudo iwconfig wlan0
wlan0     No such device

```

---

