---
title: "HOWTO: Update MadWifi for Atheros AR242x"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by lkraemer on 2009-04-29
Your subdirectories or results might be different.....

My Compaq CQ50-139NR uses the Atheros AR242x Wifi Card, and I had
previously installed an older version of the MadWifi drivers.
I wanted to update to the latest version, and not mess up my
Wifi setup on Ubuntu 8.04 LTS.

```

wget -O driver.tar.gz http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
tar xf driver.tar.gz

```

There are two conditions where the MadWifi Drivers might need
to be updated.

1. When a new Kernel has been downloaded and your Wifi doesn't
work.......DO:
```

cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416  #(OR Current Version)
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart #(OR reboot)

```

2. If a new version of MadWifi is released, and NO Kernel Update...
DO:  (use iwconfig to locate Wifi...ie. ath0, wlan0, etc.....)
```

sudo ifconfig ath0 down
cd ~/madwifi_ar5007
cd madwifi-hal-0.10.5.6-r4003-20090416
sudo make uninstall
make clean
make
sudo make install
sudo modprobe ath_pci
sudo /etc/init.d/networking restart #(OR reboot)
sudo ifconfig ath0 up

```

If you are having trouble trying to get the module loaded try this:

On my computer, I can see the madwifi-unload script under madwifi-trunk-r4031-20090529/scripts

On your pc, the madwifi-unload script should be in ~/madwifi_ar5007/madwifi-hal-0.10.5.6-r4068-20090705/scripts

After running the madwifi-unload script, you can proceed with your usual commands (make clean, make ....)

Or you could try this alternative madwifi reinstallation script:

[http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)


My upgrade worked fine.  Yours should also.

lkraemer

updated 11-07-2009

---

### Post by julie20099 on 2009-04-29
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 16

_________________________________

[cheap uggs](http://www.inugg.co.uk)
[hair cuts durham nc](http://salon168.com/seethematwork.htm)

---

