---
title: "wireless help - atheros AR242X"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by brownbox123 on 2009-03-03
I installed Intrepid 8.1 dual boot with Vista. I got my wireless Atheros AR242X to work by following the directions from [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

the problem is that when I restart the computer - the wireless doesn't work again. I can do the fix again above and get the wireless to work again, but the same thing happens every time I restart - the wireless does not work anymore. I think the problem started when I tried to get my headphones/microphone to work.

I'm ok with re-installing 8.1 again to get the wireless to work again (if that's possible), but I don't know how and would prefer not to if I don't have to.

---

### Post by Crafty Kisses on 2009-03-03
Performance has dramatically improved after the release of the new Atheros AR242X driver. You can download it right [here.]("http://file-hosting.site-hosts.net/eeepc/madwifi-nr-r3366+ar5007.tar.gz") Once you have it downloaded it,  compile it from source and install it, and your wireless card should work a lot better. So copy this folder to wherever you want when you're done downloading. Remember you need the build-essential package, but run these commands in these steps and you should be fine:
```
sudo apt-get install build-essential
cd /home/username/foldername
tar xzf madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007/
make
sudo make install
```
Once you have done that in order, the new driver should be compiled and you want to reboot by running the following:
```
sudo shutdown -r now
```
Once you have rebooted you should be good to go and your wireless should work a lot better.

---

### Post by brownbox123 on 2009-03-03
I just tried the directions to download, compile, and install the new driver, but unfortunately the wifi still doesn't work when I rebooted.

---

### Post by brownbox123 on 2009-03-03
So, I'm back to square one. I was able to fix wifi temporarily again (wifi doesn't work again after restart) using the fix in my first post. Below is a copy of what I did for the temporary fix.

> ivan@ivan-laptop:~$ cd ~/Desktop
ivan@ivan-laptop:~/Desktop$ cd compat*
ivan@ivan-laptop:~/Desktop/compat-wireless-2009-02-26$ make
make: Nothing to be done for `all'.
ivan@ivan-laptop:~/Desktop/compat-wireless-2009-02-26$ sudo make install
[sudo] password for ivan: 

Your old wireless subsystem modules were left intact:

/lib/modules/2.6.27-11-generic/kernel/net/mac80211/mac80211.ko
/lib/modules/2.6.27-11-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/adm8211.ko
/lib/modules/2.6.27-11-generic/updates/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/ath9k.ko
/lib/modules/2.6.27-11-generic/updates/b43.ko
/lib/modules/2.6.27-11-generic/updates/b43legacy.ko
/lib/modules/2.6.27-11-generic/updates/b44.ko
/lib/modules/2.6.27-11-generic/updates/ssb.ko
/lib/modules/2.6.27-11-generic/updates/iwlcore.ko
/lib/modules/2.6.27-11-generic/updates/iwl3945.ko
/lib/modules/2.6.27-11-generic/updates/iwlagn.ko
/lib/modules/2.6.27-11-generic/updates/ipw2100.ko
/lib/modules/2.6.27-11-generic/updates/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/libipw.ko
/lib/modules/2.6.27-11-generic/updates/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/libertas_cs.ko
/lib/modules/2.6.27-11-generic/updates/p54pci.ko
/lib/modules/2.6.27-11-generic/updates/p54usb.ko
/lib/modules/2.6.27-11-generic/updates/rt2400pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500pci.ko
/lib/modules/2.6.27-11-generic/updates/rt2500usb.ko
/lib/modules/2.6.27-11-generic/updates/rt61pci.ko
/lib/modules/2.6.27-11-generic/updates/rt73usb.ko
/lib/modules/2.6.27-11-generic/updates/usbnet.ko
/lib/modules/2.6.27-11-generic/updates/cdc_ether.ko
/lib/modules/2.6.27-11-generic/updates/rndis_host.ko
/lib/modules/2.6.27-11-generic/updates/rndis_wlan.ko
/lib/modules/2.6.27-11-generic/updates/rtl8180.ko
/lib/modules/2.6.27-11-generic/updates/rtl8187.ko
/lib/modules/2.6.27-11-generic/updates/zd1211rw.ko

make -C /lib/modules/2.6.27-11-generic/build M=/home/ivan/Desktop/compat-wireless-2009-02-26 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/misc/eeprom/eeprom_93cx6.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/b44.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/usb/cdc_ether.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/usb/rndis_host.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/usb/usbnet.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/adm8211.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/at76c50x-usb.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/ath5k/ath5k.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/ath9k/ath9k.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/b43/b43.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/b43legacy/b43legacy.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/ipw2x00/ipw2100.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/ipw2x00/ipw2200.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/ipw2x00/libipw.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/iwlwifi/iwl3945.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/iwlwifi/iwlagn.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/iwlwifi/iwlcore.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/libertas/libertas.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/libertas/libertas_cs.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/libertas/libertas_sdio.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/libertas/usb8xxx.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/mac80211_hwsim.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/p54/p54common.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/p54/p54pci.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/p54/p54usb.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rndis_wlan.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt2400pci.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt2500pci.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt2500usb.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt2x00lib.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt2x00pci.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt2x00usb.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt61pci.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rt2x00/rt73usb.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rtl818x/rtl8180.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/rtl818x/rtl8187.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/net/wireless/zd1211rw/zd1211rw.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/drivers/ssb/ssb.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/net/mac80211/mac80211.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/net/wireless/cfg80211.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/net/wireless/lib80211.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/net/wireless/lib80211_crypt_ccmp.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/net/wireless/lib80211_crypt_tkip.ko
  INSTALL /home/ivan/Desktop/compat-wireless-2009-02-26/net/wireless/lib80211_crypt_wep.ko
  DEPMOD  2.6.27-11-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'

Currently detected wireless subsystem modules:

/lib/modules/2.6.27-11-generic/updates/net/mac80211/mac80211.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/cfg80211.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/adm8211.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/at76c50x-usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/b43/b43.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/b43legacy/b43legacy.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/b44.ko
/lib/modules/2.6.27-11-generic/updates/drivers/ssb/ssb.ko
/lib/modules/2.6.27-11-generic/updates/iwlcore.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ipw2x00/ipw2100.ko
/lib/modules/2.6.27-11-generic/updates/ipw2200.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/ipw2x00/libipw.ko
/lib/modules/2.6.27-11-generic/updates/net/wireless/lib80211.ko
/lib/modules/2.6.27-11-generic/updates/libertas_cs.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/p54/p54pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/p54/p54usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.27-11-generic/updates/rt61pci.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/usb/usbnet.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/usb/cdc_ether.ko
/lib/modules/2.6.27-11-generic/updates/rndis_host.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rndis_wlan.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rtl818x/rtl8180.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/zd1211rw/zd1211rw.ko

Now run:

make unload

And then load the wireless module you need. If unsure reboot.

ivan@ivan-laptop:~/Desktop/compat-wireless-2009-02-26$ sudo make unload
ivan@ivan-laptop:~/Desktop/compat-wireless-2009-02-26$ sudo make load
Loading ipw2100...
WARNING: Error inserting ieee80211 (/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211.ko): Invalid module format
Loading ipw2200...
WARNING: Error inserting ieee80211 (/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211.ko): Invalid module format
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/updates/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.27-11-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwl3945 (/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading iwl4965...
WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting iwlcore (/lib/modules/2.6.27-11-generic/updates/iwlcore.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting iwlagn (/lib/modules/2.6.27-11-generic/updates/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
FATAL: Error inserting rt61pci (/lib/modules/2.6.27-11-generic/updates/rt61pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
b43 loaded successfully
b43legacy loaded successfully
ivan@ivan-laptop:~/Desktop/compat-wireless-2009-02-26$ 

this is what i see (after the temporary fix and before i restart computer) when i run the lshw -C network.

> ivan@ivan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:06:4c:5b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:66:bc:4a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.101 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:b6:80:7c:dc:a4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


---

### Post by bsharp on 2009-03-04
Add it to /etc/modules:
```
echo "ath_pci" | tee -a /etc/modules
```

It will load it on startup.

---

### Post by anewguy on 2009-03-04
Well, I'm not sure of the answer.  I do know that with other wireless chipsets and their drivers that when I have had that problem it is usually due to a module (driver) not being loaded at boot.  You should re-check the instructions you followed and see if there is a statement like "modprobe xxxxx" somewhere.  It may be necessary to add that "xxxxx" (whatever the name) to the modules loaded at boot (edit /etc/modules, add a new line at the end with the name in it, save the file and then reboot).  It's also possible that perhaps the driver is included in the blacklist files so it isn't loaded at boot - check the /etc/modprobe.d/blacklist file to see if one of the drivers created by the process you are following is listed in a "blacklist xxxxx" statement - if so, just comment out that particular blacklist line, save the file and reboot.

Dave :)

---

### Post by brownbox123 on 2009-03-04
> **bsharp said:**
> Add it to /etc/modules:
```
echo "ath_pci" | tee -a /etc/modules
```

It will load it on startup.

Forgive my noobness, but i'm not exactly sure how to add it to /etc/modules. Below is what happens when i put the code above. Please advise.
> 
ivan@ivan-laptop:~$ echo "ath_pci" | tee -a /etc/modules
tee: /etc/modules: Permission denied
ath_pci
ivan@ivan-laptop:~$ sudo echo "ath_pci" | tee -a /etc/modules
tee: /etc/modules: Permission denied
ath_pci

---

### Post by bsharp on 2009-03-04
Oops my bad.

It should be:
```
echo "ath_pci" | sudo tee -a /etc/modules
```

Sorry I can't go into much detail on the "tee" command, but basically what that does is pipes the output of echo "ath_pci" (ath_pci) and appends it onto the end of /etc/modules. On the next reboot, the modules file is read and everything listed in there is loaded on startup.

---

### Post by brownbox123 on 2009-03-04
> **bsharp said:**
> Add it to /etc/modules:
```
echo "ath_pci" | tee -a /etc/modules
```

It will load it on startup.

so i got into /etc/modules by doing this:
```
sudo gedit /etc/modules
```
then i added the line below to the very end of the /etc:
```
echo "ath_pci" | tee -a /etc/modules
```
so now /etc/modules looks like this:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
echo "ath_pci" | tee -a /etc/modules
then i rebooted, no luck, wifi doesn't work again. Am I adding the line correctly to /etc/modules?

this is what lshw -c network looks like when I restart my computer:
```
ivan@ivan-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:06:4c:5b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:3e:a8:95:dc:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by bsharp on 2009-03-04
the echo command is a terminal command. All you need added to /etc/modules is ath_pci.

Your modules file should look like this:

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ath_pci
```

Sorry for not being more clear.

---

### Post by brownbox123 on 2009-03-04
Ok. I was able to edit my /etc/modules file. I rebooted. No wireless yet. my /etc/modules now looks like this:
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ath_pci

---

### Post by bsharp on 2009-03-04
Do you still have the drivers installed from the package you downloaded earlier?

If so, run in a terminal:
```
sudo modprobe ath_pci
sudo depmod -a
```

and reboot, it should work. If not, follow the directions in the earlier post to install and then run the above commands.

---

### Post by brownbox123 on 2009-03-04
I couldn't find "modprobe xxxxx" in the temporary fix that i used in my first post in this thread. I also looked up the the blacklist mentioned by anewguy > It's also possible that perhaps the driver is included in the blacklist files so it isn't loaded at boot - check the /etc/modprobe.d/blacklist file to see if one of the drivers created by the process you are following is listed in a "blacklist xxxxx" statement - if so, just comment out that particular blacklist line, save the file and reboot.

there i found ath_pci blacklisted, so i deleted that line, saved the file, rebooted, and wifi still didn't work.

i wasn't sure if i still had the new Atheros driver from a previous post, so installed it again 

```
ivan@ivan-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ivan@ivan-laptop:~$ cd madwifi-ng-r3366+ar5007/
bash: cd: madwifi-ng-r3366+ar5007/: No such file or directory
ivan@ivan-laptop:~$
ivan@ivan-laptop:~$ cd madwifi-ng-r3366+ar5007/
bash: cd: madwifi-ng-r3366+ar5007/: No such file or directory
ivan@ivan-laptop:~$ cd madwifi-ng-r3366+ar5007
bash: cd: madwifi-ng-r3366+ar5007: No such file or directory
ivan@ivan-laptop:~$ cd ~/Desktop
ivan@ivan-laptop:~/Desktop$ cd madwifi-ng-r3366+ar5007
ivan@ivan-laptop:~/Desktop/madwifi-ng-r3366+ar5007$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/ivan/Desktop/madwifi-ng-r3366+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.o
/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.c:246: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211] Error 2
make[1]: *** [_module_/home/ivan/Desktop/madwifi-ng-r3366+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
ivan@ivan-laptop:~/Desktop/madwifi-ng-r3366+ar5007$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/ivan/Desktop/madwifi-ng-r3366+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.o
/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.c:246: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/ivan/Desktop/madwifi-ng-r3366+ar5007/net80211] Error 2
make[1]: *** [_module_/home/ivan/Desktop/madwifi-ng-r3366+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
ivan@ivan-laptop:~/Desktop/madwifi-ng-r3366+ar5007$ cd
 
```
then i added the following code:
```
ivan@ivan-laptop:~$ sudo modprobe ath_pci
FATAL: Module ath_pci not found.
ivan@ivan-laptop:~$ sudo depmod -a
ivan@ivan-laptop:~$
```
i rebooted, and still the wireless did not work.

---

### Post by orethrius on 2009-03-04
The Atheros driver is not modprobing, because the Atheros driver was never installed - because the compile (make) errored out.  I don't suppose anyone more versed in this driver's implementation can see the problem?

---

### Post by anewguy on 2009-03-04
Part of the problem here is that you are not getting a driver to compile so you have nothing to install.  There was an earlier suggestion of using mad wifi drivers instead, and I would suggest you investigate that.  There are also numerous returns in a yahoo! search with ubuntu atheros AR242X driver.  I've linked a few of those below:

[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/")

[http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/]("http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/")

[http://playingwithsid.blogspot.com/2009/01/atheros-ar242x-wireless-on-ubuntu.html]("http://playingwithsid.blogspot.com/2009/01/atheros-ar242x-wireless-on-ubuntu.html")

[http://ubuntuguy.com/how-to/using-an-atheros-ar242x-with-ubuntu-810/]("http://ubuntuguy.com/how-to/using-an-atheros-ar242x-with-ubuntu-810/")

[http://ubuntuguy.com/how-to/using-an-atheros-ar242x-with-ubuntu-810/]("http://ubuntuguy.com/how-to/using-an-atheros-ar242x-with-ubuntu-810/")  This one looks like what you were trying to do, but follow method 2, not method 1, and you'll avoid the compilation problems.

Remember - google and yahoo, using ubuntu followed by keywords about your problem can give you a lot of help.  Normally you'll even find posts from this forum linked there.

Dave :)

---

### Post by brownbox123 on 2009-03-04
Yay - big props - Thanks to everyone who gave help. 

I finally got my AR242x wireless to work after rebooting. This is the solution that worked for me: I followed the instructions to use madwifi snapshot from [http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/](http://blog.hyperandy.com/2008/11/01/atheros-ar242x-ubuntu-810-ibex/)

Thanks again Codename, anewguy, bsharp, and orethrius!

---

### Post by cptrohn on 2009-03-04
I have this exact same wireless card and the easiest way to do it is with the Linux backports...


and it works very,very well too.

---

### Post by anewguy on 2009-03-04
> **cptrohn said:**
> I have this exact same wireless card and the easiest way to do it is with the Linux backports...


and it works very,very well too.

That was in one of the links I provided, and seeing that I don't have that wireless card, it's nice to know it does work - thanks!

Glad to have put in my 2-cents worth.

dave :)

---

