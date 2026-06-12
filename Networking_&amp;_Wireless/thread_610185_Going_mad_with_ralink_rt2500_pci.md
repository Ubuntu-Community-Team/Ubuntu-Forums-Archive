---
title: "Going mad with ralink rt2500 pci"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by lamadredelsapo on 2007-11-11
I've installed the latest cvs driver from serial monkey and blacklisted the driver that ships with ubuntu, but even though the driver seems to be correctly installed i'm unable to connect to my WEP protected wireless network. I also installed rutilt and I can see several networks, including mine, but I'm unable to connect to any of them.

lshw -C network outputs the following

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:01:0a.0
       logical name: wlan0
       version: 01
       serial: 00:11:09:5a:45:e3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500 latency=64 module=rt2500 multicast=yes wireless=RT2500 Wireless
```

I don't know what else to try. Help would be REALLY appreciated.

---

### Post by Austin_KW on 2007-11-11
I never had much luck with rutilt. Use the command line or the /etc/network/interfaces file to configure the driver

Make sure you have an ra0 section in /etc/network/interfaces as follows, 
edit the interfaces file with the command ***gksudo gedit /etc/network/interfaces***
```

auto ra0
iface ra0 inet dhcp
    pre-up ifconfig ra0 up
    pre-up iwconfig ra0 mode managed
    pre-up iwconfig ra0 essid ***YourNetworkName***
    pre-up iwconfig ra0 key ***YourNetworkHexKey*** *or* ***s:YourNetworkAsciiKey***

```

I think that is correct for WEP (I use WPA), just substitute YourNetworkName and your HEX or ascii Key

Then the command ***sudo ifup --f ra0*** should bring the network up & it should come up automatically on the next boot

---

### Post by lamadredelsapo on 2007-11-12
I already tried that, and it's still not working. Could it be that instead of ra0 i have wlan0? How should I change that?

---

### Post by Austin_KW on 2007-11-12
> **lamadredelsapo said:**
> I already tried that, and it's still not working. Could it be that instead of ra0 i have wlan0? How should I change that?

What is the output of the following commands
```

ifconfig -a
sudo iwconfig
sudo iwlist scan
lsmod 

```

---

### Post by lamadredelsapo on 2007-11-12
ifconfig -a
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1B:FC:AA:70:DB  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:feaa:70db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4564543 (4.3 MB)  TX bytes:428162 (418.1 KB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:88 (88.0 b)  TX bytes:88 (88.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:09:5A:45:E3  
          inet6 addr: fe80::211:9ff:fe5a:45e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1238520 (1.1 MB)
          Interrupt:19 Base address:0x4000 

wlan0:ava Link encap:Ethernet  HWaddr 00:11:09:5A:45:E3  
          inet addr:169.254.6.181  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0x4000 
```

output of sudo iwconfig:
```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2500 Wireless  ESSID:"Livebox-D7B0"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:7748-537C-2F29-685C-625C-4B7D-3B   Security mode:open
          Link Quality=0/100  Signal level:-82 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

sudo iwlist scan output:
```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:26:24:9B:68
                    Mode:Managed
                    ESSID:"Livebox-D7B0"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-70 dBm  Noise level:-192 dBm
          Cell 02 - Address: 00:0D:54:A3:AD:E2
                    Mode:Managed
                    ESSID:""
                    Encryption key:on
                    Channel:5
                    Quality:0/100  Signal level:-74 dBm  Noise level:-192 dBm
          Cell 03 - Address: 00:03:C9:8D:0E:BE
                    Mode:Managed
                    ESSID:"gie"
                    Encryption key:on
                    Channel:4
                    Quality:0/100  Signal level:-61 dBm  Noise level:-192 dBm

```


As you can see, even though I did *sudo iwconfig wlan0 essid "gie"* it still keeps Livebox-D7B0 as essid, which is obviously why I cannot connect. How should I force it to change?

---

### Post by lamadredelsapo on 2007-11-12
I finally went the ndiswrapper way, and it works fine. So i'll keep it that way. Thanks though

---

