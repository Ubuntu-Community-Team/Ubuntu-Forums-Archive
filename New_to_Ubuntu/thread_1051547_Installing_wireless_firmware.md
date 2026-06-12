---
title: "Installing wireless firmware"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Diminished on 2009-01-26
Hello,

I was wondering if anyone would be able to help me. Esentially I cannot connect to the internet. I have recently installed 8.10 and The networkwork manager was unable to find any wireless networks (one of which this laptop is connected to) so I installed wcid just to see whether anything different occured; it didn't. I'm lead to believe that this may be the case that the adapter was turned off in windows, which I no longer have, or that I don't have the correct driver/firmware.

The machine is a Dell Inspiron 510m and the following is information my network controller:

Broadcom Corporation BCM4306 802.11b/g Wireless LAN controller (rev 03)
Subsystem: Dell Device 0003
Flags: bus master, fast devsel, latency 32 IRQ 5
Memory at fcffc000 (32-bit, non-prefetchable) [size=8k]
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb

So, I was wondering where to go from here as I'm, as the sub-forum suggests, an 'absolute beginner'.

Thanks in advance for any help offered,

Diminished

---

### Post by XanTrax on 2009-01-26
First please check restricted drivers manager located in System -> Administration -> Hardware drivers and make sure if you have the ability to enable them, you can.

If it is not available in there or you dont see something pertaining to "Broadcom B43 wireless driver" then follow these steps:

Open a terminal (gnome-terminal or xterm) and run these commands:

1. ```
sudo lshw -C network
```
2. ```
iwconfig
```
3. ```
ifconfig -a
```

and post the output of each command please.

---

### Post by Diminished on 2009-01-26
Firstly, thanks for the quick reply.

Under harware driver all I see is: "No proprietary drivers are in use on this system."

As for the others, here are the responses:


  *-network:0             
       description: Network controller 
       product: BCM4306 802.11b/g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: 3 
       bus info: pci@0000:01:03.0 
       version: 03 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=32 module=ssb 
  *-network:1 
       description: Ethernet interface 
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:01:08.0 
       logical name: eth0 
       version: 81 
       serial: 00:0f:1f:d1:44:2e 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s 
  *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:0b:7d:0f:34:3d 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 3 
       logical name: pan0 
       serial: f6:8a:f3:9a:2b:b9 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 


lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 



eth0      Link encap:Ethernet  HWaddr 00:0f:1f:d1:44:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:362 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:24636 (24.6 KB)  TX bytes:24636 (24.6 KB) 

pan0      Link encap:Ethernet  HWaddr f6:8a:f3:9a:2b:b9  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:0f:34:3d  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-7D-0F-34-3D-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by XanTrax on 2009-01-26
Thats interesting...Your devices are each listed twice (wired and wireless) and at first it doesnt say disabled but then it does.  That is really weird.  If it said UNCLAIMED next to *-network: then we could know that the hardware has not been assigned/claimed by a driver. Then afterwards iwconfig reports that its up but just not associated with an access point.  Please run these commands next:

```

iwconfig wlan0 essid <name of your access point or router>
dhclient wlan0

```

If you have a WEP key on your router or access point, run this command:

```

iwconfig wlan0 enc <key>

```

Please post the output of those commands and please put them inside the [code] tags.  Thank you.

---

### Post by Diminished on 2009-01-26
Sorry, I forgot the tags the first time.

Anyway, here is what I get:

```
iwconfig: unknown command dhclient
```

And for the second one I don't get any response, it simple gives another line for command input.

Thanks.

---

### Post by utnubuuser on 2009-01-26
Hi -- here's a page about ubuntu on an 510m> [http://www.incunabulum.de/projects/it/ubuntulaptop/wireless](http://www.incunabulum.de/projects/it/ubuntulaptop/wireless)

...and here's an older thread,  (looked kinda interesting)> [http://ubuntuforums.org/showthread.php?t=204361](http://ubuntuforums.org/showthread.php?t=204361)

...and > [http://www.linuxquestions.org/questions/mandriva-30/need-wireless-internet-help-mandrake-10-dell-inspiron-510m-intel-wireless-2100-3a-252783/](http://www.linuxquestions.org/questions/mandriva-30/need-wireless-internet-help-mandrake-10-dell-inspiron-510m-intel-wireless-2100-3a-252783/)

---

### Post by XanTrax on 2009-01-26
> **Diminished said:**
> Sorry, I forgot the tags the first time.

Anyway, here is what I get:

```
iwconfig: unknown command dhclient
```

And for the second one I don't get any response, it simple gives another line for command input.

Thanks.

This command:
```

sudo iwconfig wlan0 essid <name of your access point or router>

```

Where <name of your access point or router> is where the name of your router should go.  For example, my router is called chuck-home.  I would do this:
```
sudo iwconfig wlan0 essid chuck-home
```

then after that command executes, I type this:
```
sudo dhclient wlan0
```

Then, if you have WEP enabled...For example, my WEP key is 1234abcd I would do:
```
sudo iwconfig wlan0 enc 1234abcd
```

Please try those commands again.





> **utnubuuser said:**
> Hi -- here's a page about ubuntu on an 510m

...and here's an older thread,  (looked kinda interesting)

Why have him try to install ndiswrapper if his card has been detected and a driver claims it?  Just wondering, for future reference...

---

### Post by utnubuuser on 2009-01-26
I'm not.

They were just threads about the 510m, and one of the threads mentioned the driver having problems with competing against itself.

---

### Post by Diminished on 2009-01-26
Oh sorry, I see. Here's what I have now:

```
dave@dave-laptop:~$ sudo iwconfig wlan0 essid <MyRouter>
[sudo] password for dave: 
dave@dave-laptop:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

wmaster0: unknown hardware address type 801 
SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:0b:7d:0f:34:3d 
Sending on   LPF/wlan0/00:0b:7d:0f:34:3d 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
sudo iwNo DHCPOFFERS received. 
No working leases in persistent database - sleeping.  
dave@dave-laptop:~$ sudo iwconfig wlan0 enc <WEP>

```

And then nothing after that.

---

### Post by XanTrax on 2009-01-27
> **Diminished said:**
> Oh sorry, I see. Here's what I have now:

```
dave@dave-laptop:~$ sudo iwconfig wlan0 essid <MyRouter>
[sudo] password for dave: 
dave@dave-laptop:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

wmaster0: unknown hardware address type 801 
SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:0b:7d:0f:34:3d 
Sending on   LPF/wlan0/00:0b:7d:0f:34:3d 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
sudo iwNo DHCPOFFERS received. 
No working leases in persistent database - sleeping.  
dave@dave-laptop:~$ sudo iwconfig wlan0 enc <WEP>

```

And then nothing after that.

First:  run this command

```
sudo ifconfig wlan0 up
```

Now, read below:


Above I see that you have <my router> where it should be your router name and <WEP> where it should be the WEP key of the wireless router.  Did you replace <my router> with your router name and <WEP> with your WEP key for your wireless router and just substituted them here as to not show us what they are?  If you did NOT replace <my router> and <WEP> with your router name and WEP key when you were executing the commands then read below:


In this case you put <my router> where you have to put the name of your wireless router that you want to connect to and <WEP> is supposed to be the WEP key for the wireless router.  Read this example carefully:


1. Want to ensure my wireless network interface is up
2. My wireless router name I want to connect to is "chuck-home".
3. My wireless router has WEP encryption key of 1234abcd 
4. I want to get a DHCP assigned IP address from my wireless router.  

Here is how I would do it.  Each number corresponds to the instruction above:

1.```
sudo ifconfig wlan0 up
```
2.```
sudo iwconfig wlan0 essid chuck-home
```
3.```
sudo iwconfig wlan0 enc 1234abcd
```
4.```
sudo dhclient wlan0
```



Now heres another case:

1. Ensure your wireless network interface is up and active
```
sudo ifconfig wlan0 up
```
2. Your wireless router is named "dave-home"
```
sudo iwconfig wlan0 essid dave-home
```
3. Your wireless router has a WEP encryption of "testwep"
```
sudo iwconfig wlan0 enc testwep
```
4. Your wireless router has DHCP (which it should) and you want to get an IP from it now that you have authenticated and associated your wireless network card with it
```
sudo dhclient wlan0
```


Remember, those are just test cases...you have to supply YOUR information for YOUR wireless router

Where you had <my router> in your commands above, it should have been the name of YOUR router

Where you had <wep> in your commands above it should have been YOUR WEP key.

So, recap:

Each line below represents a new command

```

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <router_name>
sudo iwconfig wlan0 enc <router_wep_key>
sudo dhclient wlan0

```

WHERE:
<router_name> = the name of the wireless router you want to connect to
<router_wep_key> = the WEP key of the wireless router you want to connect to **_IF it has it enabled_**

Please post the output of those four commands in order, please.

---

### Post by Diminished on 2009-01-27
Yeah, sorry I was unclear. I had put in the router name/wep and chose to alter it before posting on here. I don't know why though, doesn't really matter.

Anyway, I have re-entered the commands and here is exactly what I see (with the wep key blanked out):

```
dave@dave-laptop:~$ sudo ifconfig wlan0 up 
[sudo] password for dave: 
SIOCSIFFLAGS: No such file or directory 
dave@dave-laptop:~$ sudo iwconfig wlan0 essid 47Kitchener 
dave@dave-laptop:~$ sudo iwconfig wlan0 enc <WEP> 
dave@dave-laptop:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.1 
Copyright 2004-2008 Internet Systems Consortium. 
All rights reserved. 
For info, please visit http://www.isc.org/sw/dhcp/ 

wmaster0: unknown hardware address type 801 
SIOCSIFFLAGS: No such file or directory 
SIOCSIFFLAGS: No such file or directory 
wmaster0: unknown hardware address type 801 
Listening on LPF/wlan0/00:0b:7d:0f:34:3d 
Sending on   LPF/wlan0/00:0b:7d:0f:34:3d 
Sending on   Socket/fallback 
receive_packet failed on wlan0: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 
send_packet: Network is down 
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12 
send_packet: Network is down 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
```

---

### Post by Ayuthia on 2009-01-27
Can you post the results of:
```
dmesg|grep b43
ps -ef|grep Network
```
The first command will list out system messages related to the b43 module.

The second command is to verify that Network Manager is up and running.  It might be Network Manager that is causing a conflict.

---

### Post by Diminished on 2009-01-27
Ok, here are the responses. I did have to uninstall network manager to install winc though, but the problem was obviously before that. Should I reinstall it?

```
dave@dave-laptop:~$ dmesg|grep b43 
[    7.169597] b43-pci-bridge 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5 
[   19.740014] b43-phy0: Broadcom 4306 WLAN found 
[   27.792012] input: b43-phy0 as /devices/virtual/input/input10 
[   27.864141] firmware: requesting b43/ucode5.fw 
[   27.920012] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   27.920012] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[   35.388011] input: b43-phy0 as /devices/virtual/input/input11 
[   35.436127] firmware: requesting b43/ucode5.fw 
[   35.440011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   35.440011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[   39.344020] input: b43-phy0 as /devices/virtual/input/input12 
[   39.384124] firmware: requesting b43/ucode5.fw 
[   39.388010] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   39.388010] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[   43.360018] input: b43-phy0 as /devices/virtual/input/input13 
[   43.396154] firmware: requesting b43/ucode5.fw 
[   43.400012] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   43.400012] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[  347.348017] input: b43-phy0 as /devices/virtual/input/input14 
[  347.388147] firmware: requesting b43/ucode5.fw 
[  347.392011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  347.392011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[  651.348014] input: b43-phy0 as /devices/virtual/input/input15 
[  651.392123] firmware: requesting b43/ucode5.fw 
[  651.396011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  651.396011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[  955.340015] input: b43-phy0 as /devices/virtual/input/input16 
[  955.376147] firmware: requesting b43/ucode5.fw 
[  955.380012] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  955.380012] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1259.344015] input: b43-phy0 as /devices/virtual/input/input17 
[ 1259.380145] firmware: requesting b43/ucode5.fw 
[ 1259.384010] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1259.384010] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1563.344015] input: b43-phy0 as /devices/virtual/input/input18 
[ 1563.380148] firmware: requesting b43/ucode5.fw 
[ 1563.384011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1563.384011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1615.844015] input: b43-phy0 as /devices/virtual/input/input19 
[ 1615.884225] firmware: requesting b43/ucode5.fw 
[ 1615.892019] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1615.892019] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1713.000016] input: b43-phy0 as /devices/virtual/input/input20 
[ 1713.040221] firmware: requesting b43/ucode5.fw 
[ 1713.045412] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1713.045458] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1713.096015] input: b43-phy0 as /devices/virtual/input/input21 
[ 1713.132135] firmware: requesting b43/ucode5.fw 
[ 1713.136011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1713.136011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1778.172018] input: b43-phy0 as /devices/virtual/input/input22 
[ 1778.208232] firmware: requesting b43/ucode5.fw 
[ 1778.216018] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1778.216018] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 1867.348016] input: b43-phy0 as /devices/virtual/input/input23 
[ 1867.388206] firmware: requesting b43/ucode5.fw 
[ 1867.396020] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 1867.396020] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 2106.143471] input: b43-phy0 as /devices/virtual/input/input24 
[ 2106.184148] firmware: requesting b43/ucode5.fw 
[ 2106.188011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 2106.188011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 2171.344016] input: b43-phy0 as /devices/virtual/input/input25 
[ 2171.380149] firmware: requesting b43/ucode5.fw 
[ 2171.384010] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 2171.384010] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 2475.354392] input: b43-phy0 as /devices/virtual/input/input26 
[ 2475.396207] firmware: requesting b43/ucode5.fw 
[ 2475.404019] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 2475.404019] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 2556.147339] input: b43-phy0 as /devices/virtual/input/input27 
[ 2556.188132] firmware: requesting b43/ucode5.fw 
[ 2556.192012] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 2556.192012] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 2779.344014] input: b43-phy0 as /devices/virtual/input/input28 
[ 2779.388228] firmware: requesting b43/ucode5.fw 
[ 2779.396020] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 2779.396020] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 2947.170678] input: b43-phy0 as /devices/virtual/input/input29 
[ 2947.212179] firmware: requesting b43/ucode5.fw 
[ 2947.216012] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 2947.216012] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 3079.348015] input: b43-phy0 as /devices/virtual/input/input30 
[ 3079.388148] firmware: requesting b43/ucode5.fw 
[ 3079.392011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 3079.392011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 3293.128014] input: b43-phy0 as /devices/virtual/input/input31 
[ 3293.172126] firmware: requesting b43/ucode5.fw 
[ 3293.176010] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 3293.176010] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
[ 3383.348016] input: b43-phy0 as /devices/virtual/input/input32 
[ 3383.388147] firmware: requesting b43/ucode5.fw 
[ 3383.392011] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[ 3383.392011] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4). 
dave@dave-laptop:~$ ps -ef|grep Network 
dave     11533 11410  0 15:02 pts/1    00:00:00 grep Network 
```

---

### Post by XanTrax on 2009-01-27
> **Ayuthia said:**
> Can you post the results of:
```
dmesg|grep b43
ps -ef|grep Network
```
The first command will list out system messages related to the b43 module.

The second command is to verify that Network Manager is up and running.  It might be Network Manager that is causing a conflict.

Was just gonna get to that :p.


@ Diminished:

EDIT: I think you may have some further problems.  Network-manager isnt running at all....  Please try these commands and then execute again, the commands I told you earlier.

```

sudo /etc/init.d/networking start
sudo NetworkManager

```

then execute the previous commands and post the output.


I want to see what the output says from that then you can do as the error from dmesg says and go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and follow the instructions there.  I do not know exactly why it wouldnt have worked on a fresh install because in my desktop PC I have the exact same card as you installed in a PCI-e slot and the card worked with a fresh install of Ubuntu.  Try out that link and maybe try the links that one of the previous posters had posted in regards to your laptop

---

### Post by Ayuthia on 2009-01-27
Before you try to start up Network Manager, you need to download the firmware to make the b43 module work.  It is missing the files in /lib/firmware/b43.  Since you are having problems with Hardware Drivers, please try and install b43-fwcutter through Synaptic or from the Terminal:
```
sudo apt-get install b43-fwcutter
```I am assuming that you have a working internet connection because you are posting results.  If that is the case, you should say yes when it asks to fetch the firmware for you.  If the question does not come up, please try the following:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```The information that I supplied here is just about the same thing as what dmesg is suggesting.  It is Ubuntu's automated installer (the somewhat hidden portion of Hardware Drivers).

That should get the firmware installed.  From there:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will reload the wireless module so that it can find the firmware and then we try to bring it up and look for wireless sites.  Let us know if it is able to scan for wireless sites.

---

### Post by XanTrax on 2009-01-27
> **Ayuthia said:**
> Before you try to start up Network Manager, you need to download the firmware to make the b43 module work.  It is missing the files in /lib/firmware/b43.  Since you are having problems with Hardware Drivers, please try and install b43-fwcutter through Synaptic or from the Terminal:
```
sudo apt-get install b43-fwcutter
```I am assuming that you have a working internet connection because you are posting results.  If that is the case, you should say yes when it asks to fetch the firmware for you.  If the question does not come up, please try the following:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```The information that I supplied here is just about the same thing as what dmesg is suggesting.  It is Ubuntu's automated installer (the somewhat hidden portion of Hardware Drivers).

That should get the firmware installed.  From there:
```
sudo modprobe -r b43 ssb
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```
This will reload the wireless module so that it can find the firmware and then we try to bring it up and look for wireless sites.  Let us know if it is able to scan for wireless sites.

Thanks for this.  Silly me thinking to start network manager while dmesg is already reporting the error and saying what to do. Brainfart #-o

---

### Post by Ayuthia on 2009-01-27
> **XanTrax said:**
> Thanks for this.  Silly me thinking to start network manager while dmesg is already reporting the error and saying what to do. Brainfart #-o

Don't worry about it.  I just saw that Network Manager was not running so I figured that we can take advantage of the situation.  Network Manager can sometimes cause conflicts when setting up your wireless card.

---

### Post by Diminished on 2009-02-04
Sorry that it has taken me so long to get back to you; I've been very busy lately. I'd just like to thank you for all of your help, I've sorted it. :-)

I ended up reinstalling network manager and then finding the b43 firmware. Thanks again guys.

---

