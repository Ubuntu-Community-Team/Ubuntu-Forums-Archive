---
title: "I exploded madwifi."
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by Rovdjur on 2007-07-16
So when I installed my Ubuntu system (last night), the wireless card seemed to be working, but actually did not. The card would pick up wireless AP's, but would not connect to them, even if there was no password set.

So I did some messing around, and due to the fact that I am a newbie, I completely messed it up.

The hardware profiler in Ubuntu recognizes that the wireless chip is there (Atheros AR5212 802.11abg NIC), but iwconfig outputs this:

```
jonas@tux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

```

I tried making an install of madwifi through Terminal, and I get this:

```
jonas@tux:~/Desktop/madwifi-0.9.3.1$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.20-16-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/jonas/Desktop/madwifi-0.9.3.1/ath'
test -d //lib/modules/2.6.20-16-generic/net || mkdir -p //lib/modules/2.6.20-16-generic/net
cp ath_pci.ko //lib/modules/2.6.20-16-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/jonas/Desktop/madwifi-0.9.3.1/ath'
make: *** [install-modules] Fel 1
jonas@tux:~/Desktop/madwifi-0.9.3.1$ 

```

I am sure there is a simple fix, but I do not know what it is. Can anyone help?

---

### Post by ukripper on 2007-07-16
can you post output of the following file:

```
sudo gedit /etc/interface/networks
```

---

### Post by Rovdjur on 2007-07-16
> **ukripper said:**
> can you post output of the following file:

```
sudo gedit /etc/interface/networks
```

It's blank.

---

### Post by ukripper on 2007-07-16
Can you post following command's output:

```
dmesg | grep tail
```

```
sudo lspci
```

---

### Post by Rovdjur on 2007-07-16
> **ukripper said:**
> Can you post following command's output:

```
dmesg | grep tail
```

```
sudo lspci
```

Well ```
dmesg | grep tail
``` did nothing.

And ```
sudo lspci
``` came up with this:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71d4
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

```

I assume you are looking for the Wireless card model (which I already posted in the first post :-/)

---

### Post by ukripper on 2007-07-16
As you have messed it up try this guide [http://ubuntuforums.org/showthread.php?t=38972](http://ubuntuforums.org/showthread.php?t=38972) you would need to install it from scratch but with new feisty installation it works as restricted driver and just works fine with wlassistant put essid and key. I am using same chipset in my Sony vaio without problem.

---

