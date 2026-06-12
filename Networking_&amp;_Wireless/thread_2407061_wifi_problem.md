---
title: "wifi problem"
date: 2018-11-29
forum: Networking &amp; Wireless
---

### Post by anth1111 on 2018-11-29
Hi guys I'm new on ubuntu, now i have a problem with my wifi connection, In settings I get: "no wifi adapter found"
I followed many instruction I read here but still it's not working.
I installed ubuntu 18.04 on my hp notebook, with rltk drivers. 

when I type this command: ifconfig wlan0 up
I get:
wlan0: ERROR while getting interface flags: No such device

and when I type this:  iwconfig
I only get this:

enp2s0    no wireless extensions.
lo        no wireless extensions.

what can i do?

---

### Post by mitesh.agrwl on 2018-11-29
Please post the output of the command

```
$ sudo lshw -class network 
```

Use 'code' tags while posting the output.

---

### Post by anth1111 on 2018-11-30
Hello again I got this output:
```
$ sudo lshw -class network
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 07
       serial: 30:e1:71:95:3c:bf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=10.6.13.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:124 ioport:4000(size=256) memory:b2200000-b2200fff memory:b2000000-b2003fff
  *-network UNCLAIMED
       description: Network controller
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:b2100000-b2103fff

```

---

### Post by mitesh.agrwl on 2018-11-30
The wireless drivers are missing for some reasons. [Check this thread]("https://ubuntuforums.org/showthread.php?t=2392986"). Run the script from the signature of Forum Moderator [**[COLOR=#C61919][B]jeremy31**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1924242") and post the results. *Use pastebin to post results from the script.*

---

### Post by jeremy31 on 2018-11-30
Post results from terminal for
```
modfinfo rtl8723be; mokutil --sb-state
```

---

### Post by anth1111 on 2018-11-30
it's not working..```
anthony@anthony-HP-Notebook:~$ modfinfo rtl8723be; mokutil --sb-state

Command 'modfinfo' not found, did you mean:

  command 'modinfo' from deb kmod

Try: sudo apt install <deb name>

SecureBoot enabled
anthony@anthony-HP-Notebook:~$ sudo apt install kmod
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kmod is already the newest version (24-1ubuntu3.1).
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
anthony@anthony-HP-Notebook:~$ modfinfo rtl8723be; mokutil --sb-state

Command 'modfinfo' not found, did you mean:

  command 'modinfo' from deb kmod

Try: sudo apt install <deb name>

SecureBoot enabled
anthony@anthony-HP-Notebook:~$ 


```

---

### Post by mitesh.agrwl on 2018-11-30
command is 

```
 $ modinfo rtl8723be; mokutil --sb-state 
```

---

### Post by anth1111 on 2018-12-01
```
~$ modinfo rtl8723be; mokutil --sb-state
filename:       /lib/modules/4.15.0-39-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     41E3D27D506CBEDC478A504
alias:          pci:v000010ECd0000B723sv*sd*bc*sc*i*
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8723be
vermagic:       4.15.0-39-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)
SecureBoot enabled


```

---

### Post by jeremy31 on 2018-12-01
See the wireless script link in my signature and post results

---

### Post by anth1111 on 2018-12-01
results obtained are in an attached file

---

### Post by jeremy31 on 2018-12-01
Reboot and go into BIOS settings and disable Secure Boot.  Leave the secure boot keys alone

---

### Post by anth1111 on 2018-12-01
It worked Thank you! but wifi signal is weak..

---

### Post by jeremy31 on 2018-12-01
Did you install from Larry Finger's github?  [https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new)

---

### Post by anth1111 on 2018-12-01
Downloaded and I did "make from terminal"

---

### Post by jeremy31 on 2018-12-01
Do ```
sudo rm /etc/modprobe.d/50-rtl8723be.conf
```
Then test to see if the ant_sel parameter makes a difference
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'SSID|level'
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'SSID|level'
```

I know some kernel commit likely broke the ant_sel in some of the Ubuntu 4.15 kernels but the github should work

---

### Post by anth1111 on 2018-12-01
```
anthony@anthony-HP-Notebook:~$ sudo rm /etc/modprobe.d/50-rtl8723be.conf
[sudo] password for anthony: 
anthony@anthony-HP-Notebook:~$ sudo modprobe -r rtl8723be
anthony@anthony-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=1
anthony@anthony-HP-Notebook:~$ iwlist scan | egrep -i 'SSID|level'
lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

                    Quality=38/70  Signal level=-72 dBm  
                    ESSID:"TP-Link_93EE"
                    Quality=34/70  Signal level=-76 dBm  
                    ESSID:"ASUS_28_2G"
                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"HP\xE2\x80\x99s iPhone"
anthony@anthony-HP-Notebook:~$ sudo modprobe -r rtl8723be
anthony@anthony-HP-Notebook:~$ sudo modprobe rtl8723be ant_sel=2
anthony@anthony-HP-Notebook:~$ iwlist scan | egrep -i 'SSID|level'
lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

                    Quality=24/70  Signal level=-86 dBm  
                    ESSID:"HP\xE2\x80\x99s iPhone"
                    Quality=38/70  Signal level=-72 dBm  
                    ESSID:"TP-Link_93EE"
                    Quality=32/70  Signal level=-78 dBm  
                    ESSID:"ASUS_28_2G"


```

Still the same signal,no improvements, but thanks for solving the main problem!

---

