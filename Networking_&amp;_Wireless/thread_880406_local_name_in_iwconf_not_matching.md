---
title: "local name in iwconf not matching"
date: 2008-08-05
forum: Networking &amp; Wireless
---

### Post by mjezell on 2008-08-05
Hi all,

This maybe a silly question but I'm having a problem with wireless speed on my local home network and with trying to trouble shoot the problem I ran into a wierd situation.  When I listed the iwconfig on a mythbuntu frontend computer using a MSI PC60G wireless NIC PCI card using a RT61 PCI driver, the results are - 
> 
lo        no wireless extensions.

wmaster0  no wireless extensions.

[COLOR=Red]wlan0[/COLOR]     IEEE 802.11g  ESSID:"renewabletechnology"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:7E:CD:49:5C   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7    RTS thr: off   Fragment thr=2346 B   
          Link Quality=36/100  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
As you see the logical name for my wireless interface is wlan0.  When I list the lshw -C network for the same computer, I get this - 
> 
 *-network               
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 5
       bus info: pci@0000:01:05.0
       [COLOR=Red]logical name: wmaster0[/COLOR]
       version: 00
       serial: 00:1d:92:12:c5:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.85 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
As you can see the logical name is listed as wmaster0.  Should this be the same in iwconf and lshw?  Can anyone tell me if this is correct or if I have a problem to solve?

Any help would be appreciated.

---

### Post by cdtech on 2008-08-05
You may want to have a look within:
```
/etc/udev/rules.d/**70-persistent-net.rules**
```
The bold is my file (yours may differ).

These are the persistent rules generated for persistent network device naming.

I had to rename mine as such:
```
# PCI device 0x14e4:0x4311 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1a:73:b5:7e:d1", ATTRS{type
}=="1", NAME="wlan0"
```

Hope this helps you get started......

---

### Post by mjezell on 2008-08-05
Hi cdtech,

Thanks for the response.  I checked the file you referred to and the logical name is the same as when I look at ifconfig, so I guess everything is fine,  Thanks for the info and help,

---

