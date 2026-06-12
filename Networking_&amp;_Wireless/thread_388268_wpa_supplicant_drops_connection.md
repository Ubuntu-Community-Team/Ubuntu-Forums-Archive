---
title: "wpa_supplicant drops connection"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by MrDetermination on 2007-03-19
[This guide](http://www.ubuntuforums.org/showthread.php?t=263136&page=10) gets me up and running for a short time in Edgy, then nothing after a random amount of time.  It seems to disconnect with inactivity and maybe with "too much" activity (last night it dropped with IRC, web traffic and streaming radio).  My network manager applet shows a "wired network RaLink RT2561/RT61 802.11g pc", or did before I implemented the things in the first post of this thread.  The card is actually a Linksys PCI card, WMP54g.  I drop after a few minutes of inactivity and can't figure out why or how to restore connection without restarting the machine.  wpa_gui shows nothing, absolutely nothing.  This is being posted from a fresh reboot.

interfaces:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid thisismyhouse
gateway 192.168.0.1
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

wpa_supplicant:
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="thisismyhouse"
       scan_ssid=1
       proto=WPA RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
psk=404b8fb415XXXXXXXX90504acd10dbfcf
}

```

```
chip@Metallo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"thisismyhouse"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:46:A3:D1:E4   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.

chip@Metallo:~$ sudo lshw
Password:
metallo                   
    description: Desktop Computer
    product: VT8367-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: VT8367-8235
       physical id: 0
       slot: PS/2 Mouse
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (09/10/2003)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.4
          slot: Socket A
          size: 1333MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 
        *-network:1
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@00:12.0
             logical name: eth0
             version: 74
             serial: 00:0d:87:aa:42:96
             size: 10MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
             configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
             resources: ioport:e000-e0ff iomemory:ee10a000-ee10a0ff irq:11
chip@Metallo:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:A3:D1:E4
                    ESSID:"thisismyhouse"
                    Mode:Master
                    Frequency:2.412 GHz
                    Encryption key:on
                    Extra:wpa_ie=dd160050f201010000XXX
                    Extra:tsf=000000c6053221ca

chip@Metallo:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:f8:2d:fa:01
Sending on   LPF/wlan0/00:18:f8:2d:fa:01
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.101 -- renewal in 301942 seconds.

```

Any ideas?

---

### Post by spd106 on 2007-03-19
Try adding this line to the wpa_supplicant.conf

```
ctrl_interface=/var/run/wpa_supplicant
[COLOR="Red"]fast_reauth=1[/COLOR]
#ap_scan=2

network={
...

```

There are a few lines that you won't need anymore. I suggest that you backup the old interfaces file and replace the wlan0 stanza with this one. 
```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

```This works for me on Edgy, though it won't work on Dapper or earlier. Obviously I have omitted lo and other interfaces for brevity.

---

