---
title: "D-link DWL-122 usb ver. b1 help needed"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by Zzzach on 2008-02-23
I need help getting a dwl-122 ver. b1 connected to a wireless network. I shows the network and tries to connect but it doesn't assign an ip address or connect to the internet. I tried installing the windows driver for it but it says the driver is invalid after I install it. I don't know what else to do, it seems super complicated getting this thing working. Any suggestions?? Thanks

---

### Post by jan quark on 2008-02-24
please post the output of these terminal commands to sehd some light ony our current network stutus
thank you

```
iwconfig
```

```
sudo iwlist scan
```

```
sudo lshw -C network
```
```

cat /etc/network/interfaces
```

---

### Post by acad1 on 2008-02-24
> **Zzzach said:**
> I need help getting a dwl-122 ver. b1 connected to a wireless network. I shows the network and tries to connect but it doesn't assign an ip address or connect to the internet. I tried installing the windows driver for it but it says the driver is invalid after I install it. I don't know what else to do, it seems super complicated getting this thing working. Any suggestions?? Thanks


I will be interested in following up your thread. I have the dwl-122 ver. b1 working with Ubuntu 7.04, but it will not work when I use Ubuntu 7.10. As I am not too conversant with Linux yet, I cannot guide you through the process, but I will follow with great interest the answers provided by jan quark.

---

### Post by acad1 on 2008-02-26
Just wondering if some-one can help any further with this problem.
My wireless adapter works with Feisty which is installed in my hard disk. When running a live CD of 7.10 the wireless adapter is not working.

With 7.04 the device is recognised as "rausb1" but with 7.10 on live CD the wireless device is recognised as "wlan0"
The data below is taken from 7.04, which is installed on my hard drive

andy@andy-desktop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"****T-WIRELESS"  Nickname:""
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:1B:2F:72:75:A8   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Link Quality=86/100  Signal level:-54 dBm  Noise level:-201 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@5
       logical name: rausb1
       serial: 00:13:46:63:1e:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RT2500USBSTA driverversion=1.0.0 - BETA2 ip=192.168.0.3 multicast=yes wireless=RT2500USB WLAN
andy@andy-desktop:~$ 


The data shown below here is taken from Ubuntu 7.10 running the live CD on the same hard drive


ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: ATM network controller
       product: AccessRunner PCI ADSL Interface Device
       vendor: Conexant
       physical id: 2.1
       bus info: pci@0000:01:02.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:46:63:1e:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
ubuntu@ubuntu:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:46:63:1e:ae
Sending on   LPF/wlan0/00:13:46:63:1e:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
ubuntu@ubuntu:~$ 

Can someone please help and advise me how to get Ubuntu 7.10 wireless working.
I would like to upgrade, but not if 7.10 is not going to work on my hard disk.

What will happen if I use the upgrade facility on the installed version of 7.04? Will I lose the exising connection when the install is completed?

---

