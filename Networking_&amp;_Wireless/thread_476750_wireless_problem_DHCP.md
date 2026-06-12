---
title: "wireless problem DHCP?"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by alzaf on 2007-06-17
I bought a Belkin 54g wireless router. On windows XP the wireless router works. 

On Feisty, I identified the wireless network card as a rt2500. The output is as follows:

 > 
Output: sudo lspci -vvvv

00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 6833
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at febf8000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-


I followed the instructions in [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29) to install the rt2500 module. I did all of the instructions on page apart from using  RaConfig2500. I had to use the latest CVS version as the module-assistant driver and latest beta did not compile (RaConfig2500 came up with error saying that device could not be found and I found a launchpad bug report saying RaConfig needed to be setup with same driver but the latest CVS did not have RaConfig2500 source)

I managed to get the rt2500 module installed. The output is as follows

> 
Output: modinfo rt2500.ko

filename:       rt2500.ko
license:        GPL
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS 2007061015
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     D9EE9F3BF3D7E90108415D9
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           debug:Debug mask: n selects filter, 0 for none (int)
parm:           ifname:Network device name (default ra%d) (charp)


I compiled the rt2500 module as debug and get the following output when bringing ra0 up

> 
output /var/debug :: rt2500 module set as compilied

Jun 17 20:07:54 theman-laptop kernel: [ 1134.896000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1134.896000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1134.896000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1134.996000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1134.996000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1134.996000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.100000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.100000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.100000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.200000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.200000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.200000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.256000] rt2500: RT2500_get_ether_stats --->
Jun 17 20:07:54 theman-laptop kernel: [ 1135.304000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.304000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.304000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.408000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.408000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.408000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.508000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.508000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.508000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.612000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.612000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.612000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.712000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.712000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:54 theman-laptop kernel: [ 1135.712000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1135.816000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1135.816000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1135.816000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1135.920000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1135.920000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1135.920000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1136.020000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1136.020000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1136.020000] rt2500: <==== RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1136.124000] rt2500: ====> RTMPHandleInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1136.124000] rt2500: ====> RTMPHandleTbcnInterrupt
Jun 17 20:07:55 theman-laptop kernel: [ 1136.124000] rt2500: <==== RTMPHandleInterrupt


I added an entry to /etc/modules for rt2500

From the above tutorial and posts in ubuntu forms., I used various settings for ra0 in /etc/network/interfaces all with the same results. The current settings  I have is as follows:

> 

iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "belkin54g"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="wireless1"
        pre-up ifconfig ra0 up
auto ra0


The results are always as follows when bringing up ra0 using sudo ifup ra0:

> 
Listening on LPF/ra0/00:11:09:af:0c:c0
Sending on   LPF/ra0/00:11:09:af:0c:c0
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


From the wireless routers manual, I managed to find its static address as 192.168.2.1. When entering this into web browser I am able to amend the routers settings. I tried settings

> 
iface ra0 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 0.0.0.0
wireless-essid belkin54g
wireless-key s:wireless1


It came up with the following error when brining ra0 up:

> 
SIOCADDRT: Invalid argument
Failed to bring up ra0.


From other posts, I got commands which output the following details

> 
sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0D:26:0F:06  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe26:f06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1044 errors:0 dropped:0 overruns:0 frame:0
          TX packets:966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:835979 (816.3 KiB)  TX bytes:125027 (122.0 KiB)
          Interrupt:21 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3192 (3.1 KiB)  TX bytes:3192 (3.1 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:AF:0C:C0  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:feaf:cc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1544823 (1.4 MiB)
          Interrupt:21 Base address:0x4000 


sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"belkin54g"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:7769-7265-6C65-7373-3100-0000-00
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-212 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:11:50:A7:B6:D0
                    Mode:Managed
                    ESSID:"belkin54g"
                    Encryption key:off
                    Channel:11
                    Quality:0/100  Signal level:-54 dBm  Noise level:-203 dBm
          Cell 02 - Address: 00:50:18:4B:EB:F2
                    Mode:Managed
                    ESSID:"default"
                    Encryption key:on
                    Channel:11
                    Quality:0/100  Signal level:-78 dBm  Noise level:-212 dBm


From the router setup page it is set to dynamic and my laptop is showing up in DHCP client list.

I'm not sure if this problem can be fixed but would be grateful for all help given.

---

### Post by dolphin_oracle on 2007-06-17
I don't know how to fix it, but the first sentence on that page is that if you use those directions under feisty, it will break WIFI.


from top of the linked page:

WifiDocs/Driver/RalinkRT2500
1. WARNING!

The /etc/network/interface changes described on this page will break wifi in Feisty. See [WWW] this post for more details.

**edit**

Hey I just noticed that you are assigning the same IP address as your router as to your ra0.  Try disabling eth0 then enabling ra0 with dhcp.

---

### Post by alzaf on 2007-06-17
thanks for prompt reply, dolphin_oracle. 

There seems to be a lot of bugs concerning wifi in Feisty.  I've amended settings using network-admin which amends settings in /etc/network/interfaces and it comes out with same results.

I can only assume everything else on the rt2500 setup page will work on Feisty?

# edit

I just read your edit. I have connected an ethernet cable from router into my laptop so I am able to connect to the internet. I  set firestarter as a shared connection. I have tried without the ethernet cable connected and still get same problem.

---

