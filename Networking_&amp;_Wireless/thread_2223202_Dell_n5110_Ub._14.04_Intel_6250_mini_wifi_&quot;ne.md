---
title: "Dell n5110 Ub. 14.04 Intel 6250 mini wifi &quot;network-disabled&quot; and greyed out on nm"
date: 2014-05-09
forum: Networking &amp; Wireless
---

### Post by chrisco23 on 2014-05-09
I bought an Intel Centrino 6250 card on ebay to replace the Intel Centrino 6235 that came with my Dell n5110 Inspiron laptop, solely because the 6235 cannot connect to 5Ghz networks.

I installed it today but I can't get wireless at all with it.  Greyed out in NetworkManager, and shows as "*-network DISABLED" in 'lshw -C network'.

The Fn+F2 stuff appears to work (toggles Yes/No) but doesn't help me.

Is there any hope for it/me?

I spent 3 hours scouring forums so here are the results of most of the things I remember from other threads that I will probably be asked about:

```

[FONT=arial]sudo lshw -C network[/FONT]
[FONT=arial]  *-network               [/FONT]
[FONT=arial]       description: Ethernet interface[/FONT]
[FONT=arial]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT]
[FONT=arial]       vendor: Realtek Semiconductor Co., Ltd.[/FONT]
[FONT=arial]       physical id: 0[/FONT]
[FONT=arial]       bus info: pci@0000:05:00.0[/FONT]
[FONT=arial]       logical name: eth0[/FONT]
[FONT=arial]       version: 05[/FONT]
[FONT=arial]       serial: 18:03:73:86:85:ec[/FONT]
[FONT=arial]       size: 10Mbit/s[/FONT]
[FONT=arial]       capacity: 100Mbit/s[/FONT]
[FONT=arial]       width: 64 bits[/FONT]
[FONT=arial]       clock: 33MHz[/FONT]
[FONT=arial]       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT]
[FONT=arial]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT]
[FONT=arial]       resources: irq:50 ioport:e000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff[/FONT]
[FONT=arial]  *-network DISABLED[/FONT]
[FONT=arial]       description: Wireless interface[/FONT]
[FONT=arial]       product: Centrino Advanced-N + WiMAX 6250 [Kilmer Peak][/FONT]
[FONT=arial]       vendor: Intel Corporation[/FONT]
[FONT=arial]       physical id: 0[/FONT]
[FONT=arial]       bus info: pci@0000:09:00.0[/FONT]
[FONT=arial]       logical name: wlan1[/FONT]
[FONT=arial]       version: 09[/FONT]
[FONT=arial]       serial: 00:15:00:55:a5:a4[/FONT]
[FONT=arial]       width: 64 bits[/FONT]
[FONT=arial]       clock: 33MHz[/FONT]
[FONT=arial]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT]
[FONT=arial]       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-17-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn[/FONT]
[FONT=arial]       resources: irq:53 memory:f7e00000-f7e01fff[/FONT]
[FONT=arial]  *-network[/FONT]
[FONT=arial]       description: Ethernet interface[/FONT]
[FONT=arial]       physical id: 2[/FONT]
[FONT=arial]       logical name: wmx0[/FONT]
[FONT=arial]       serial: 00:1d:e1:0d:aa:71[/FONT]
[FONT=arial]       capabilities: ethernet physical[/FONT]
[FONT=arial]       configuration: driver=i2400m_usb firmware=i6050-fw-usb-1.5.sbcf link=no[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial] iwconfig
wmx0      no wireless extensions.


wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


lo        no wireless extensions.
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: i2400m-usb:1-1.4:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial] lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2880 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 8086:0188 Intel Corp. WiMAX Connection 2400m
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]

```

---

### Post by mikewhatever on 2014-05-10
You should probably add the output of **rfkill list all** to the OP. Also, make sure the wireless is on - sometimes, there is a switch, waiting to be flipped.

---

### Post by chrisco23 on 2014-05-11
Thanks.

The rfkill list all is the same output for me as rfkill list.

About the switch, do you mean the Fn+F2 thing?  By toggling that key combination, it toggles the results of phy0, to be "Hard blocked: yes" instead of "Hardblocked: no".  Neither setting gives me any working wifi.

---

### Post by mikewhatever on 2014-05-15
Rfkill says the WIMAX thing is softblocked, so you may want to try unbloking it with <rfkill unblock  i2400m-usb>.
Also, **dmesg** usually gives the clues on hardware issues - try something like <dmesg | grep wlan>.

---

