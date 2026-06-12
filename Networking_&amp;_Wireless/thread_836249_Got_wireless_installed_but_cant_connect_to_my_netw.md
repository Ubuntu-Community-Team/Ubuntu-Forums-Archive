---
title: "Got wireless installed but cant connect to my network!"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by milkybarkid on 2008-06-21
I've got a Toshiba A210-1B1 and had issues using drivers for the Realtek 8187b which were on the web, managed to install via ndiswrapper using the Win XP driver off the Toshiba site as it wouldn't work with any other driver.

It now manages to see the networks:
```
 Cell 01 - Address: 00:1B:2F:6E:1E:0C
                    ESSID:"SKY10073"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```
 
and displays this with iwconfig:
```
wrighty@wrighty-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
It does ask for the network key, I input this but it doesn't seem to do anything.

Not sure what to do next, note that I've tried WPA, WEP and no authentication?

Please help me on my first cup of ubuntu!

---

### Post by nickdbliss on 2008-06-21
Ok give me the output of #lshw -c network and also show what is in this file
#sudo gedit /etc/network/interfaces

---

### Post by milkybarkid on 2008-06-22
thanks for your response heres what you asked for:

#lshw -c network and also show what is in this file
returns:
```
 *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:33:31:b8:de
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:aa:11:7b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. link=no multicast=yes wireless=IEEE 802.11g
```
#sudo gedit /etc/network/interfaces

returns:
```

auto lo
iface lo inet loopback
```

---

### Post by nickdbliss on 2008-06-22
Just require some info. Do u have dhcp on ur router? And further is network manager working fine for you? Try giving me the output of #ifconfig

---

### Post by milkybarkid on 2008-06-22
DHCP is configured on the router to use 192.168.0.2 - 192.168.0.254, however I used to turn dhcp off as I have a nintendo Wii and found assigning specific IP's via the router worked better, I did try manually specifying an IP to the laptop in ubuntu but made no difference. 

Keep having to boot into dreaded Vista to send these messages at the min.

Also I find that I have to re-install the driver each time I boot into ubuntu to fire the wireless up other wise it doesn't pick up any wireless netowrks. 

As you can tell Ubuntu newbee, thanks for your help!

Here's ifconfig:

```
wrighty@wrighty-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:31:b8:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11800 (11.5 KB)  TX bytes:11800 (11.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:aa:11:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

