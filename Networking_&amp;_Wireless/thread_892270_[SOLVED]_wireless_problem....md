---
title: "[SOLVED] wireless problem..."
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Thomazian on 2008-08-17
Hi all, Ubuntu detected my WG111v2 adapter however the signal is very poor and constantly drops out (as opposed to Windows).

I decided to use the Windows drivers and installed them using ndisgtk.  I now have no wireless at all.

From what I can tell, the driver did install correctly.  I am hoping that someone can look at the below code and point out anything obvious that may not be correct with my setup, or give me some other suggestions.

Thanks for your help.


lsusb
```
ITC-Ubuntu:~$ lsusb
Bus 004 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:001e Microsoft Corp. IntelliMouse Explorer
Bus 001 Device 001: ID 0000:0000  

```


lshw -C network
```
ITC-Ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:26:e9:87
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:af:83:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net111v2 driverversion=1.52+NETGEAR Inc.,03/27/2006,5.1 multicast=yes wireless=IEEE 802.11g

```


iwconfig
```
ITC-Ubuntu:~$ iwconfig
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


ifconfig
```
ITC-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:0d:26:e9:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:9 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76700 (74.9 KB)  TX bytes:76700 (74.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:6c:af:83:3a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


ndiswrapper -l
```
ITC-Ubuntu:~$ ndiswrapper -l
net111v2 : driver installed
	device (0846:6A00) present (alternate driver: rtl8187)

```

---

### Post by Thomazian on 2008-08-17
I am guessing my inital problem of slow connection was not the driver, but a configuration issue so I have reverted my wireless back to the orignal driver using:

```

sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe rtl8178

```

I still have two issues:

1. I now have to manually load the rtl8178 driver via the terminal after boot. Does anyone know how I can automate this?

2. My wireless connection still has a low connection rate that is prone to drop out.  Are there any configuration changes I can try to improve the connection speed above 1 & 2Mb/s?

```
ITC-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1C:DF:CF:3B:CE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/64  Signal level=30/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Ayuthia on 2008-08-17
> **Thomazian said:**
> I am guessing my inital problem of slow connection was not the driver, but a configuration issue so I have reverted my wireless back to the orignal driver using:

```

sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe rtl8178

```

I still have two issues:

1. I now have to manually load the rtl8178 driver via the terminal after boot. Does anyone know how I can automate this?

2. My wireless connection still has a low connection rate that is prone to drop out.  Are there any configuration changes I can try to improve the connection speed above 1 & 2Mb/s?

```
ITC-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:1C:DF:CF:3B:CE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=51/64  Signal level=30/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

You can try the following and see if it will load the module for you:
```
echo rtl8178|sudo tee -a /etc/modules
```
If it does not work, you will have to edit the /etc/modules file and remove the rtl8178 line.  To edit it:
```
gksu gedit /etc/modules
```

Unfortunately, I don't know how to fix the speed issue, sorry.

---

### Post by jualin on 2008-08-17
If the problem is speed issue then you can try disabling IPV6 in Firefox by writing > about:config on the address bar and then searching for IPv6 and changing the status from "False" to "True", however this will not fix the signal issue, just the speed. 
How did you install the Windows driver using Ndiswrapper(ndisgk)?

---

### Post by Thomazian on 2008-08-18
Hi Guys,

Thanks for your advice, I think I have it worked out. I haven't changed anything regarding IPv6, I may not have been clear in my post however when I am close to the router everything is fine.  

The unreliable wireless issue occurs when I move the laptop back to the computer desk (in another room), not DNS resolution or Internet speed once connected.

Also to clarify I am using the standard Ubuntu drivers rtl8187, I removed the Windows wg111 driver and ndiswrapper.

Ill give a run down of what I found.  First I wanted to make sure I actually had good signal in the computer room, so I used Netstumbler in Windows to check signal strength. (attached) Very good signal with 0 noise, no other conflicting channels... definately has to be a driver or config issue.

Lets try configuring....

Playing with the iwconfig command I recieved varying results depending upon my parameters. 

I tried common combinations of speed settings from 54M to 11M with and without 'auto'.  According to the manual ('man iwconfig') 'auto' negotiates the connection speed at or below the parameter you enter.

After setting a speed, I reset the wireless conection by right clicking the network icon in the panel disabling wireless, then enabling wireless and running iwconfig to see the result.  I also opened a few web pages to test usability.

Using iwconfig to set speeds with and without 'auto' parameter:
```
sudo iwconfig wlan0 rate 54M auto
...reset wireless and test conection...

sudo iwconfig wlan0 rate 54M
...reset wireless and test conection...

etc..

sudo iwconfig wlan0 rate 11M auto
...reset wireless and test conection...

sudo iwconfig wlan0 rate 11M
...reset wireless and test conection...

```

Some of the speeds did not work at all or would load one page then stop.  For me the sweet spot was at 11M auto.  Still slower than Windows but is now reliable. (If I was back near the router I am sure a higher speed would have been stable)

I would suggest others with a similar issue to try the above and find that speed that works for you.

I did notice a discrepency between the speed from iwconfig (11Mb)```
ITC-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:CF:3B:CE   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=39/64  Signal level=28/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and what is reported in 'Connection Information' (right click on the network icon in panel). (attatched)

Mine says 5Mb, I think this is the best speed it could negotiate when connecting as I specified the 'auto' parameter.  But why is iwconfig reporting 11Mb?  Has the network re-negotiated speed back up to 11Mb and it is just that the Connection Information does not refresh its speed?  Maybe someone can shed some light on this.

For me I am satisfied that this has resolved the issue of poor wireless connection using default drivers, it is not as good as the Windows connection but is as good as these drivers are going to get.

I am now going to take it a step further and install the ndiswrapper with Windows wg111 driver to see if there is any improvement over the Ubuntu drivers.  

Once I have this resolved I will be ready to clean install with Ubuntu and remove my dual boot with Windows :)

..I will keep you posted with my ndis findings.

---

### Post by Thomazian on 2008-08-19
I have installed the Windows driver using 'ndisgtk' and my wireless connection has improved drastically.

I did not have to do any configuration to get the driver working, I simply followed the How To [https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html) and it worked.

It starts automatically upon bootup and I did not have to blacklist any drivers.

My connection now connects at 54M with good signal and is stable.  My conclusion is the Ubuntu drivers rtl8187 for the WG111v2 are not as good as the Windows driver with ndiswrapper.

```
ITC-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"belkin54g"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:DF:CF:3B:CE   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
ITC-Ubuntu:~$ ndiswrapper -l
net111v2 : driver installed
	device (0846:6A00) present (alternate driver: rtl8187)

```

---

### Post by jualin on 2008-08-22
We are glad to hear that you got everything working fine now. For some cards Windows Wireless drivers are better and improve your connection.

---

### Post by tomjennings on 2008-09-15
> **Thomazian said:**
> I have installed the Windows driver using 'ndisgtk' and my wireless connection has improved drastically.

Totally great!!! I too did 'rate 11M auto' and solved the dead-interface problem, so I'm at least operable!

But which windows driver did you use? There seems to be a number of them, and the latest from the netgear site is a 'setup.exe' binary, not an install disk type package with a .inf file. 

I found one, old apparently, 1.28 "beta"; ndiswrapper loads it OK but says "hardware not installed" so maybe it's for the prism card?

Damn Netgear for usin the same revision  number for two totally different products!

Thanks again for yhour work and your insight.

---

### Post by Thomazian on 2008-09-15
Hi tomjennings,

Glad to hear it worked for you too.

To get the driver files, I downloaded the latest setup.exe from Netgear and started of the setup in Windows.  I specified the install location to 'c:\temp'.

Setup.exe will extract the necessary files to this directory.  If you use the same location as I did, you should find the three driver files under 'c:\temp\Driver\Win2KXP'.  Keep a back up of these three files to avoid going through the setup again later :)

---

