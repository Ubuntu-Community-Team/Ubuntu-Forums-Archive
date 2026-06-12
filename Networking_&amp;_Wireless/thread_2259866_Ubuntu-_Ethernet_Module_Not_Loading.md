---
title: "Ubuntu- Ethernet Module Not Loading"
date: 2015-01-07
forum: Networking &amp; Wireless
---

### Post by 1139560 on 2015-01-07
Hello Everyone, I was wondering if somone can help me diagnose, and fix a problem with the ethernet Module that is not loading/being regnized/claimed

---

### Post by praseodym on 2015-01-07
Please run the wireless script from the sticky thread and show the output. Does WLAN work?

---

### Post by 1139560 on 2015-01-09
I am running a Wired Connection on this Desktop, i have compiled, and tryed to load the module for the onboard Ethernet but no success, I am currently using a usb to ethernet adapter, which has restored internet Temperarly

Here is some information about the card


```
root@user-desktop:/home/user# lshw -c network
  *-network UNCLAIMED                                       -this is the one that the module isnt liking it
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:fe400000-fe41ffff memory:fe427000-fe427fff ioport:f060(size=32)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth2
       serial: 00:50:b6:09:dc:13
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=08-Nov-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=10.1.10.29 link=yes multicast=yes port=MII speed=100Mbit/s
```



Intel e1000e should be the driver

```
root@user-desktop:/home/user# modinfo e1000e
filename:       /lib/modules/3.2.0-74-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
version:        3.1.0.2-NAPI
license:        GPL
description:    Intel(R) PRO/1000 Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     BC98E0BD9BE9F1638D89AE9
alias:          pci:v00008086d000015A3sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A2sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A1sv*sd*bc*sc*i*
alias:          pci:v00008086d000015A0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001559sv*sd*bc*sc*i*
alias:          pci:v00008086d0000155Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000153Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001503sv*sd*bc*sc*i*
alias:          pci:v00008086d00001502sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F0sv*sd*bc*sc*i*
alias:          pci:v00008086d000010EFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010EAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001525sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CEsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010CBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BFsv*sd*bc*sc*i*
alias:          pci:v00008086d000010E5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000294Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BDsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C3sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C2sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C0sv*sd*bc*sc*i*
alias:          pci:v00008086d00001501sv*sd*bc*sc*i*
alias:          pci:v00008086d00001049sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010C4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C5sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010BBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001098sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BAsv*sd*bc*sc*i*
alias:          pci:v00008086d00001096sv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Csv*sd*bc*sc*i*
alias:          pci:v00008086d000010F6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D3sv*sd*bc*sc*i*
alias:          pci:v00008086d0000109Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000108Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000107Dsv*sd*bc*sc*i*
alias:          pci:v00008086d000010B9sv*sd*bc*sc*i*
alias:          pci:v00008086d000010D5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DAsv*sd*bc*sc*i*
alias:          pci:v00008086d000010D9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001060sv*sd*bc*sc*i*
alias:          pci:v00008086d000010A5sv*sd*bc*sc*i*
alias:          pci:v00008086d000010BCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010A4sv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000105Esv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-74-generic SMP mod_unload modversions 
parm:           copybreak:Maximum size of packet that is copied to a new buffer on receive (uint)
parm:           TxIntDelay:Transmit Interrupt Delay (array of int)
parm:           TxAbsIntDelay:Transmit Absolute Interrupt Delay (array of int)
parm:           RxIntDelay:Receive Interrupt Delay (array of int)
parm:           RxAbsIntDelay:Receive Absolute Interrupt Delay (array of int)
parm:           InterruptThrottleRate:Interrupt Throttling Rate (array of int)
parm:           IntMode:Interrupt Mode (array of int)
parm:           SmartPowerDownEnable:Enable PHY smart power down (array of int)
parm:           KumeranLockLoss:Enable Kumeran lock loss workaround (array of int)
parm:           CrcStripping:Enable CRC Stripping, disable if your BMC needs the CRC (array of int)
parm:           EEE:Enable/disable on parts that support the feature (array of int)
parm:           Node:[ROUTING] Node to allocate memory on, default -1 (array of int)
parm:           debug:Debug level (0=none,...,16=all) (int)
```





root@user-desktop:/home/user# modprobe e1000e
root@user-desktop:/home/user# ^C



lsmod
```
root@user-desktop:/home/user# lsmod
Module                  Size  Used by
snd_hda_codec_realtek   224261  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180113  10 bnep,rfcomm
binfmt_misc            17540  1 
asix                   27020  0 
usbnet                 26212  1 asix
ppdev                  17113  0 
snd_hda_intel          33719  5 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32866  1 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79081  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                98097  0 
joydev                 17693  0 
mac_hid                13253  0 
serio_raw              13211  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47238  0 
hid                    99883  1 usbhid
i915                  482876  3 
drm_kms_helper         46978  1 i915
e1000e                156873  0 
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
```

---

### Post by 1139560 on 2015-01-09
root@user-desktop:/home/user# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)

---

### Post by praseodym on 2015-01-09
Please show
```

cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
```

---

### Post by 1139560 on 2015-01-09
root@user-desktop:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth2
iface eth2 inet dhcproot@user-desktop:~# 



root@user-desktop:~# cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.1.10.1




root@user-desktop:~# cat /etc/udev/rules.d/70-persistent-net.rules

# PCI device 0x10b7:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/0000:03:00.0 (3c59x)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:50:da:23:80:21", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:40:f2:e2:45:5f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0b95:0x7720 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:50:b6:09:dc:13", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


root@user-desktop:~# ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:50:b6:09:dc:13  
          inet addr:10.1.10.29  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: 2601:7:7981:4000:250:b6ff:fe09:dc13/64 Scope:Global
          inet6 addr: fe80::250:b6ff:fe09:dc13/64 Scope:Link
          inet6 addr: 2601:7:7981:4000:396d:4c18:65b5:f68f/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28521 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16902659 (16.9 MB)  TX bytes:2170773 (2.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1464 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1464 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:116968 (116.9 KB)  TX bytes:116968 (116.9 KB)


eth2 is my usb ethernet connection that i am using to type this

---

### Post by praseodym on 2015-01-09
Why is eth2 set in the "interfaces"? Did you do it manually?

Try to reset the file:
```

echo "iface lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot.

---

### Post by 1139560 on 2015-01-09
After Rebooting i found i was unable to reconnect to the internet using my usb dongle, upon Closer inspection using  "lshw -c network" it says my dongle  is "DISABLED[FONT=Ubuntu Mono][COLOR=#000000]"

[/COLOR][/FONT]user@user-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:fe400000-fe41ffff memory:fe427000-fe427fff ioport:f060(size=32)
  



*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: eth2
       serial: 00:50:b6:09:dc:13
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=08-Nov-2011 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet multicast=yes port=MII speed=100Mbit/s
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


I used  thumbdrive to copy the printout  and posted it on my other computer

---

### Post by SeijiSensei on 2015-01-09
Is the Ethernet adapter connected to the same router as the dongle was using?

If so, try this. 

1) Enter "sudo nano /etc/network/interfaces" from the command prompt.
2) You'll be in a file editor.  Replace the contents of the file with
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```
3) Restart the computer.  Run "ifconfig" at a command prompt.  Is there an "eth0" with an assigned IP address?

4) If not, restore your original configuration with the dongle by changing "eth0" to "eth2" in /etc/network/interfaces and rebooting.

lsmod shows the e1000e kernel module loaded, and some of the other information above shows that Linux detects the adapter.  However I was worried when I read this:
> **1139560 said:**
> I am running a Wired Connection on this Desktop, i have compiled, and tryed to load the module for the onboard Ethernet but no success, 
Supoort for Intel adapters is included with the standard kernels; you shouldn't ever need to compile a module for one of their adapters.  However, if you're running a modified kernel, we may not be able to help you.

---

### Post by 1139560 on 2015-01-12
After Reinstalling The OS, I had internet during install from cd, however upon reboot, there  no internet, after the next reboot there was internet access!
 After Several  Reboots the Internet Constintly Works, However The Internet Rarely if ever works from a cold boot.
Any advice; restarting immediatly after booting up each time is quite annoying

---

### Post by 1139560 on 2015-01-12
After further diagnostics, and restarts it seems as if the internet always works, 
If i boot from cold boot the internet doesnt seem to run,  lshw -c network says driver is unclaimed, but if i do a restart command ethernet works o reboot

---

### Post by 1139560 on 2015-01-13
Problem Fixed after BIOS update

---

