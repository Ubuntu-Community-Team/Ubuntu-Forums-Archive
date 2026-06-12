---
title: "Problem connecting to internet"
date: 2018-02-27
forum: Networking &amp; Wireless
---

### Post by atman2 on 2018-02-27
I am new to Ubuntu and Linux. I have an HP Mini 210 that I installed Ubuntu 16.04 LTS on. It connected to wifi with no problem for a little bit, but now it won't connect. When I click on the icon for wireless it says No network devices available. Any help would be appreciated.

---

### Post by wildmanne39 on 2018-02-27
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by atman2 on 2018-02-27
I am unable to connect even with a wired connection so I used the link and did the wireless-info script. The results are

```



	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


michael-HP-Mini-210-1000 4.13.0-31-generic x86_64,  Ubuntu 16.04.3 LTS, xenial


CPU    : Intel(R) Atom(TM) CPU N450   @ 1.66GHz
Memory : 974 MB
Uptime : 13:46:52 up 3 min,  1 user,  load average: 3.02, 1.98, 0.83




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:365e]
	Kernel modules: ssb




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 005: ID 03f0:241d Hewlett-Packard Gobi 2000 Wireless Modem (QDL mode)
Bus 001 Device 003: ID 0408:0ff1 Quanta Computer, Inc. 
Bus 001 Device 007: ID 05dc:c75c Lexar Media, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:2a1d Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
1: hp-wifi: Wireless LAN        no            no
2: hp-bluetooth: Bluetooth      no            no
3: hp-wwan: Wireless WAN        no            no
4: hci0: Bluetooth              no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 wmi_bmof,hp_wmi




module parameters ~~~~~~~~~~~~~~~~~~


wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


No way to aquire root rights found.




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[hp_wmi]
filename:       /lib/modules/4.13.0-31-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     6FD302672D14FBD954917B7
depends:        wmi,sparse-keymap


[wmi_bmof]
filename:       /lib/modules/4.13.0-31-generic/kernel/drivers/platform/x86/wmi-bmof.ko
srcversion:     94E6C9581AF4C4DFBD3470E
depends:        wmi


[wmi]
filename:       /lib/modules/4.13.0-31-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     810396EFFD5842CDE37306C
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-4.13.0-31-generic root=UUID=2fc4e4da-ae8c-4209-9ab5-76fb2df91b0b ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    2.316800] audit: initializing netlink subsys (disabled)
[    2.777469] wmi_bus wmi_bus-PNP0C14:00: WQBC data block query control method not found
[    7.619332] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   24.177212] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


	======== Done ========

```

---

### Post by wildmanne39 on 2018-02-27
The driver you need is blacklisted for some reason, copy and paste for accuracy, please do:
```
sudo sed -i '/blacklist bcma ssb b43/ d' /etc/modprobe.d/blacklist.conf
```
I believe that will unblacklist the needed drivers if not we will do it the manual way.

Let's reinstall the driver to be sure it is installed, do:
```
sudo apt install --reinstall firmware-b43-installer
``` 
Reboot, if it does not come on please run the wireless script again so we can see if the blacklist ha been removed.

Thanks

---

### Post by atman2 on 2018-02-27
I ran the script to remove the blacklist. It did not show that it did anything. It just came back to the cursor. I tried to run the one to reinstall the driver, but I'm not connected to the internet so it did not work. I rebooted the computer and it did not work. I reran the wireless script and here is the result.

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


michael-HP-Mini-210-1000 4.13.0-31-generic x86_64,  Ubuntu 16.04.3 LTS, xenial


CPU    : Intel(R) Atom(TM) CPU N450   @ 1.66GHz
Memory : 974 MB
Uptime : 20:42:58 up 2 min,  1 user,  load average: 2.49, 1.62, 0.66




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:365e]
	Kernel modules: ssb




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 005: ID 03f0:241d Hewlett-Packard Gobi 2000 Wireless Modem (QDL mode)
Bus 001 Device 003: ID 0408:0ff1 Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 03f0:2a1d Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
1: hp-wifi: Wireless LAN        no            no
2: hp-bluetooth: Bluetooth      no            no
3: hp-wwan: Wireless WAN        no            no
4: hci0: Bluetooth              no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    24576  2 wmi_bmof,hp_wmi




module parameters ~~~~~~~~~~~~~~~~~~


wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


No way to aquire root rights found.




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[hp_wmi]
filename:       /lib/modules/4.13.0-31-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     6FD302672D14FBD954917B7
depends:        wmi,sparse-keymap


[wmi_bmof]
filename:       /lib/modules/4.13.0-31-generic/kernel/drivers/platform/x86/wmi-bmof.ko
srcversion:     94E6C9581AF4C4DFBD3470E
depends:        wmi


[wmi]
filename:       /lib/modules/4.13.0-31-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     810396EFFD5842CDE37306C
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-4.13.0-31-generic root=UUID=2fc4e4da-ae8c-4209-9ab5-76fb2df91b0b ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    2.313267] audit: initializing netlink subsys (disabled)
[    2.760841] wmi_bus wmi_bus-PNP0C14:00: WQBC data block query control method not found
[    7.559753] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   25.304834] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


	======== Done ========



```

---

### Post by wildmanne39 on 2018-02-27
If the command is successful you will not see any output but the blacklist still remains. I have to ask where are you getting this wireless script from it is not the one that we use from my signature. Please do:
```
sudo -H gedit /etc/modprobe.d/blacklist-bcm43.conf
```
Then put a # in front of blacklist ssb, blacklist b43, blacklist bcma for example #blacklist ssb then save the file and reboot does the wifi come on? if not you will need to get an internet connection if possible even if you have to tether your cell phone so you can run the command to reinstall the driver. There is another way to get the driver but you still have to have access the the internet and a flash drive.

Thanks

---

### Post by atman2 on 2018-03-02
I'm sorry I didn't get back sooner. I left yesterday to go out of town. Didn't get a chance to do anything with my laptop. Anyway, I ended up reloading the whole program of Ubuntu. Good news is it works now. If I have any more problems I will get back with you.  Thanks.

---

### Post by wildmanne39 on 2018-03-09
I am glad it is working!

---

