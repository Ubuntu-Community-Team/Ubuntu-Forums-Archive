---
title: "Wireless won't connect"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by munguanaweza on 2008-10-02
Hi,
just trying out Xubuntu 8.04 for the first time.  I have a Dell Inspiron with PIII 600 and 512mb ram.  I installed the OS and was able to connect immediately with the pcmcia nic, but when I install the wireless card I can't get it to connect to the internet. 

 It is a DWL-G650 with an AR5212 chipset. The driver is loaded, and I can see by the blinking lights that the card is powered.  When I run in terminal iwconfig I get:
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Tuxnet1"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:43:F0:D4:72   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-35 dBm  Noise level=-92 dBm
          Rx invalid nwid:5  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If I run sudo lshw -C network I get this result:
 *-network               
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:13:46:9f:d0:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
lxmark@lxmark-laptop:~$ 

I tried to follow the troubleshooting suggestions here:

[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-device](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html#troubleshooting-device)

but when I try to open the systems > preferences > hardware, the preferences and beyond are not there.  I don't see any other means of checking hardware installation in the applications menu.

Can anyone give me some help as to how to get the wireless working?  It seems like its about halfway there, almost ready to work but presently won't let me connect to the internet.

Thanks!

---

### Post by iponeverything on 2008-10-02
does "sudo dhclient ath0" do anything for you?

What are the addresses that wireless router is giving out?

try to address your interface by hand:

sodo ifconfig ath0 192.168.0.5 
route add default gw 192.168.0.1

if 192.168.0.5 is your dhcp range and 192.168.0.1 is the address of
your router.

---

### Post by superprash2003 on 2008-10-02
also post ifconfig output and try pinging your modem

---

### Post by munguanaweza on 2008-10-02
Hi,
here are some answers:

sudo dhclient ath0
There is already a pid file /var/run/dhclient.pid with pid 5969
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:12:42:7f:d0:2d
Sending on   LPF/ath0/00:12:42:7f:d0:2d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

ping 192.168.0.1
connect: Network is unreachable

(When I pinged the router address with the ethernet card in the pcmcia slot the router responded.)

 ifconfig
ath0      Link encap:Ethernet  HWaddr 00:12:42:7f:d0:2d  
          inet6 addr: fe80::213:42ff:fe7f:d02d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:17 dropped:17 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4859 (4.7 KB)  TX bytes:9457 (9.2 KB)

ath0:avahi Link encap:Ethernet  HWaddr 00:12:42:7f:d0:2d  
          inet addr:169.252.3.238  Bcast:169.252.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3310 (3.2 KB)  TX bytes:3310 (3.2 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-12-42-7F-D0-2D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:753 errors:0 dropped:0 overruns:0 frame:37
          TX packets:117 errors:1 dropped:17 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:84731 (82.7 KB)  TX bytes:11187 (10.9 KB)
          Interrupt:11 


I tried to manually configure the address manually but it didn't work.  I don't think that I understand how to find the correct addresses, even though I can log into my router via the browser and the ethernet connection.

Keep trying!

---

### Post by munguanaweza on 2008-10-03
Bump

---

### Post by Slowspeed on 2008-10-03
I have the DWL-G650M PCMCIA wifi card installed on an old Dell X200.

I had to use the windows driver shipped with the card using NDISWRAPPER in order to enable the wifi card properly.
The gui application windows wireless drivers located under system/administration will help you configure the driver. 

I am able to use the card with Ubuntu Hardy Heron with no problems finding hot spots or at home.

---

### Post by munguanaweza on 2008-10-03
Hi,
thanks for the response.  It seems like the Atheros driver may be working, but the wireless card isn't recognized by the computer so I can't get on the internet with it. I've used other linux systems, and I think my next step would usually be to make sure the card is recognized by the OS.  

 I've looked for the windows wireless you suggested, but it isn't there in systems.  Also, there is no tab for preferences > hardware, so I can't make sure that the card is being recognized by the computer.  Seems like an OS problem to me, but truly I am not a computer expert and I could have it all wrong.

---

### Post by Slowspeed on 2008-10-03
If you go into the Synaptic package manager and search for ndiswrapper you should find the package as it is a standard Ubuntu supported package.

I hope that I am not steering you down the wrong path.

If you are able to ping your wireless access point then there is no problem with the way your card is currently configured. 

If you are sure that your card is not recognized I would definitely try the windows driver / Ndiswrapper solution.

[http://packages.ubuntu.com/source/feisty/ndiswrapper](http://packages.ubuntu.com/source/feisty/ndiswrapper)

UBUNTU documentation:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by munguanaweza on 2008-10-05
Hi,
I thought that I would give your suggestion a try just on the off chance it was a driver problem, so I installed ndiswrapper with the windows wireless tools.  Then I installed the windows driver for the wireless card.  The driver is installed properly, but I am having the same problem.  I can't get hooked up to the internet.  

It seems like the card isn't configured into the operating system or something, even though the drivers are installed, and the card is powered.  

Anyone have any thoughts?  Why is there no way to check if the card is installed in the operating system from the system dropdown menu?

Thanks

---

### Post by munguanaweza on 2008-10-06
Bump

---

### Post by Slowspeed on 2008-10-06
> **munguanaweza said:**
> Hi,
I thought that I would give your suggestion a try just on the off chance it was a driver problem, so I installed ndiswrapper with the windows wireless tools.  Then I installed the windows driver for the wireless card.  The driver is installed properly, but I am having the same problem.  I can't get hooked up to the internet.  

It seems like the card isn't configured into the operating system or something, even though the drivers are installed, and the card is powered.  

Anyone have any thoughts?  Why is there no way to check if the card is installed in the operating system from the system dropdown menu?

Thanks

Actually, you can go to the system drop down menu and select administration then select Network. This will list your physical network connections that are available. 
You can select the connection for wireless and click on properties to review and update the settings of the connection/device.
The screen will be grayed out and you will have to supply the root password in order to use this function.

You can also use terminal and type iwconfig to view your wireless network device and see what it is connected to.

regards,

---

### Post by munguanaweza on 2008-10-06
Hi,
thanks for the reply.  I have performed both of the actions you mentioned, and one may read my iwconfig readout in my first post in the thread.  

Is there a specific dropdown list for hardware as mentioned in the documentation that I referenced in my first post in this thread?

Is there an upper limit on the number of characters that one may input to the WPA supplicant encryption code box in Xubuntu?  I can't tell if all the characters are actually going in once I reach the physical dimensions of the box as I type across and add characters in the box.  When I reach the limit of the box the characters don't jump to let me know that more are going in.

---

### Post by munguanaweza on 2008-10-07
Bump

---

### Post by Slowspeed on 2008-10-09
> **munguanaweza said:**
> Hi,
thanks for the reply.  I have performed both of the actions you mentioned, and one may read my iwconfig readout in my first post in the thread.  

Is there a specific dropdown list for hardware as mentioned in the documentation that I referenced in my first post in this thread?

Is there an upper limit on the number of characters that one may input to the WPA supplicant encryption code box in Xubuntu?  I can't tell if all the characters are actually going in once I reach the physical dimensions of the box as I type across and add characters in the box.  When I reach the limit of the box the characters don't jump to let me know that more are going in.

I do not have the level of knowledge to assist with these questions. 
Sorry, 
slowspeed

---

### Post by munguanaweza on 2008-10-10
[I]I do not have the level of knowledge to assist with these questions.
Sorry,
slowspeed[/I]

That makes two of us, thanks for trying, Slowspeed.

---

