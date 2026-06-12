---
title: "wireless bcm43xx driver ubuntu 8.04"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Erik. on 2008-04-28
I am already trying 3 days to fix my internet connection.

I installed 8.04 on my computer, i want to use wireless internet.
I found this thread:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Now everything was going good.
i only need to do the Hardy Bug Fix
When i do lshw -C network after the fix i see this:

```

  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wlan0
       version: 03
       serial: 00:0f:66:1d:6e:b4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,03/23/2006, 4.40.1 ip=172.27.183.222 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```

After reboot this is my output:
```

erik@erik-desktop:~$ lshw -C network 
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0f:66:1d:6e:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.27.183.222 multicast=yes wireless=IEEE 802.11g

```

But i still have no internet connection.

Could someone help me whit fixing this problem?

Erik

---

### Post by superprash2003 on 2008-04-28
could you post ifconfig and iwconfig results here

---

### Post by Erik. on 2008-04-28
i did the bug fix and it worked, after i rebooted my computer it does not work at all.

i tried it again but it still does not work.
outputs:

```

erik@erik-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:17:53:43  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe17:5343/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1709 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1459134 (1.3 MB)  TX bytes:351922 (343.6 KB)
          Interrupt:18 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49476 (48.3 KB)  TX bytes:49476 (48.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:1d:6e:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:d8010000-d8012000 

```

```

erik@erik-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by superprash2003 on 2008-04-28
go to system->administration->restricted drivers and make sure they are enabled

---

### Post by Erik. on 2008-04-28
I made a startup script and now it works, only thing i always need to start that script for internet connection...

Only problem i need sudo and also tried sudo -i but that does not work for the startup...
i need sudo at startup only for that script.

---

### Post by superprash2003 on 2008-04-28
hope this is what you are looking for 
echo (password) | sudo -S (command)

---

### Post by Erik. on 2008-04-28
it does not work sorry.
Premission denied

---

### Post by Feenix3k on 2008-04-28
The driver bcm43xx has been blacklisted and replaced with

 configuration: driver=b43-pci-bridge latency=32 module=ssb

bcm43xx has to be un-blacklisted and the abouve coponets b43 and ssb need to be blacklisted. I dont know how to blacklist those componites, but the are blocking the bcmwl5.inf I need too

---

### Post by Feenix3k on 2008-04-28
The driver bcm43xx has been blacklisted and replaced with

 configuration: driver=b43-pci-bridge latency=32 module=ssb

bcm43xx has to be un-blacklisted and the above components b43 and ssb need to be blacklisted. I don't know how to blacklist those components, but the are blocking the bcmwl5.inf I need too.

---

### Post by GabrielDunn on 2008-04-28
I am having a similar problem.  BCM4306 card fresh install of 8.04

rowena@rowena-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:9d:46:d3:49  
          inet addr:10.11.12.182  Bcast:10.11.12.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe46:d349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4748389 (4.5 MB)  TX bytes:689107 (672.9 KB)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107800 (105.2 KB)  TX bytes:107800 (105.2 KB)

rowena@rowena-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"starbucks"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

--

rowena@rowena-laptop:~$ lspci | grep Broadcom\ Corporation
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

-

So it looks like my card is recognized but not working.  I checked the restricted driver manager and I don't see to need any.

Any ideas?

---

### Post by Erik. on 2008-04-28
Did you tried the bug fix?

this is my script:

```

/etc/dbus-1/event.d/25NetworkManager stop

cd /home/erik/bcm43xx

sudo  ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo  depmod -a
sudo  modprobe ndiswrapper
sudo  cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo  ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant


sudo  rmmod b43
sudo  rmmod b44
sudo  rmmod b43legacy
sudo  rmmod ssb
sudo  rmmod ndiswrapper
sudo  modprobe ndiswrapper
sudo  modprobe ssb

echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod b43legacy\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb' | sudo tee -a /etc/init.d/rc.local

cp -v -f /home/erik/bcm43xx/interfaces /etc/network/interfaces
/etc/dbus-1/event.d/25NetworkManager start
sudo  /etc/init.d/networking restart

exit

```

in don't know why i need to do this but this works for me...
as you can see i made a copy of my interfaces file,
I install the driver all the time and then do the other steps.
ater those steps the interface file is empty, so i replace it and reload it...
This works fine for me

---

### Post by DFalconX on 2008-04-28
My wireles card does not appear:
I get this:

```
josue@samandrosii:~$ ifconfig
eth56     Link encap:Ethernet  direcciónHW 00:16:d3:ad:a2:5b  
          inet dirección:192.168.1.110  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::216:d3ff:fead:a25b/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:988 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:776748 (758.5 KB)  TX bytes:160259 (156.5 KB)
          Interrupción:220 Dirección base: 0x4000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:1836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1836 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:93676 (91.4 KB)  TX bytes:93676 (91.4 KB)

josue@samandrosii:~$ sudo  rmmod b43
[sudo] password for josue: 
ERROR: Module b43 does not exist in /proc/modules

```

---

