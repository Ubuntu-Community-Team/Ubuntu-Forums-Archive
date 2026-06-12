---
title: "ndiswrapper micronet sp506gk problems"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by olidude7 on 2008-08-08
i've installed ndiswrapper with the GUI and installed the driver

hardware present:yes

i'm stuck now completely, the wireless connection option does not appear in the network manager

all i can gather is this
when i type ifconfig in terminal i get:

oliver@oliver-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:72:16:a8:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xcce0 Memory:f9ee0000-f9f00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79100 (77.2 KB)  TX bytes:79100 (77.2 KB)


but when i type iwconfig i get:


oliver@oliver-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


i am completely confused and i also have no idea what the above information i just posted means :lolflag:

---

### Post by Ayuthia on 2008-08-08
> **olidude7 said:**
> i've installed ndiswrapper with the GUI and installed the driver

hardware present:yes

i'm stuck now completely, the wireless connection option does not appear in the network manager

all i can gather is this
when i type ifconfig in terminal i get:

oliver@oliver-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:72:16:a8:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xcce0 Memory:f9ee0000-f9f00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1582 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79100 (77.2 KB)  TX bytes:79100 (77.2 KB)


but when i type iwconfig i get:


oliver@oliver-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


i am completely confused and i also have no idea what the above information i just posted means :lolflag:
The hardware present means that the windows driver was loaded fine but the ifconfig and iwconfig information shows that the wireless card has not been activated.  

Can you post the results of the following from the Terminal:
```
lshw -C network
lsmod|grep ndiswrapper
ndiswrapper -l
```
The first command will list out information about your network cards and possibly show some driver information that might help explain what your card is doing.  The second command is checking to see if the ndiswrapper module is loaded.  The third command is checking to see what windows driver is installed and if there are any alternate drivers.  If there are alternet drivers, you might have to blacklist them so that they don't cause any confllict with ndiswrapper.

You might also check:
```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
dmesg|grep ndiswrapper
```
Sometimes there is an error message that shows up in the logs when ndiswrapper is loaded.  It might help provide a clue on what is happening.

---

### Post by olidude7 on 2008-08-08
what a numpty i am
i think the problem was i was trying to get it to work in the terminal, before i found out there was a gui and i think it bugered it up
my brother accidently did an unclean shut down and it wouldn't boot into hardy
i reinstalled hardy, reinstalled ndiswrapper and straight thru the gui it works!!!

theres a lesson here, its do not try to do stuff in terminal till you r ready, its a powerful tool that can kill!!!

well thanks for your help, i'm certain i would of used it, but it works now for no reason

---

### Post by olidude7 on 2008-08-08
well that was extremely brief
it worked and connected to my wpa network, then i rebooted and it still claims to have wireless functionality but can't find any networks or manually connect either

i am not going to attempt what is written above before someone makes sure its what to with the position i am now in,
thanks in advance

---

### Post by olidude7 on 2008-08-08
now this is becoming interesting, if the device was last used successfully in windows and i then boot into hardy it finds the network and connects, if i have rebooted from a previous hardy session where it worked or not it is detected but cannot find any wireless networks

---

### Post by olidude7 on 2008-08-09
ok with lshw -C network and the other commands, i get this when its working after a successful windows session

```
oliver@oliver-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:16:a8:9d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.4-1 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan1
       version: 20
       serial: 00:11:3b:10:77:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,04/13/2006,5.1060.0 ip=192.168.0.4 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
oliver@oliver-desktop:~$ lsmod|grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  9 usblp,lirc_mceusb2,ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
oliver@oliver-desktop:~$ ndiswrapper -l
net8185 : driver installed
	device (10EC:8185) present
oliver@oliver-desktop:~$ sudo modprobe -r ndiswrapper
[sudo] password for oliver: 
oliver@oliver-desktop:~$ sudo modprobe ndiswrapper
oliver@oliver-desktop:~$ 
oliver@oliver-desktop:~$ dmesg|grep ndiswrapper
[   39.459491] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.828612] ndiswrapper: driver net8185 (Realtek,04/13/2006,5.1060.0413.2006) loaded
[   40.221514] ndiswrapper: using IRQ 20
[   46.296181] usbcore: registered new interface driver ndiswrapper
[   46.298032] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[  270.422342] ndiswrapper: device wlan1 removed
[  270.422451] usbcore: deregistering interface driver ndiswrapper
[  285.597723] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  285.607792] ndiswrapper: driver net8185 (Realtek,04/13/2006,5.1060.0413.2006) loaded
[  285.861739] ndiswrapper: using IRQ 20
[  291.804204] usbcore: registered new interface driver ndiswrapper
[  291.804301] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
oliver@oliver-desktop:~$ 
oliver@oliver-desktop:~$ 

```

and again, when it appears in network manager but can't find networks (happens after any hardy session, regardless of it working or not in that session)

```
oliver@oliver-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:16:a8:9d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.4-1 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wlan1
       version: 20
       serial: 00:11:3b:10:77:65
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,04/13/2006,5.1060.0 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
oliver@oliver-desktop:~$ 
oliver@oliver-desktop:~$ lsmod|grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  9 usblp,lirc_mceusb2,ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
oliver@oliver-desktop:~$ ndiswrapper -l
net8185 : driver installed
	device (10EC:8185) present
oliver@oliver-desktop:~$ sudo modprobe -r ndiswrapper
[sudo] password for oliver: 
oliver@oliver-desktop:~$ sudo modprobe ndiswrapper
oliver@oliver-desktop:~$ dmesg|grep ndiswrapper
[   27.149664] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   27.621875] ndiswrapper: driver net8185 (Realtek,04/13/2006,5.1060.0413.2006) loaded
[   27.876686] ndiswrapper: using IRQ 20
[   33.819936] usbcore: registered new interface driver ndiswrapper
[   33.823518] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[   39.812873] ndiswrapper (mp_reset:62): wlan1 is being reset
[   51.805884] ndiswrapper (mp_reset:62): wlan1 is being reset
[   83.787290] ndiswrapper (mp_reset:62): wlan1 is being reset
[  115.768579] ndiswrapper (mp_reset:62): wlan1 is being reset
[  147.749926] ndiswrapper (mp_reset:62): wlan1 is being reset
[  170.929831] ndiswrapper: device wlan1 removed
[  170.929939] usbcore: deregistering interface driver ndiswrapper
[  193.715746] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  193.725961] ndiswrapper: driver net8185 (Realtek,04/13/2006,5.1060.0413.2006) loaded
[  193.979827] ndiswrapper: using IRQ 20
[  199.917508] ndiswrapper: changing interface name from 'wlan0' to 'wlan1'
[  199.918450] usbcore: registered new interface driver ndiswrapper
[  205.912009] ndiswrapper (mp_reset:62): wlan1 is being reset
oliver@oliver-desktop:~$

```

the module still seems to be ndiswrapper all the time so i am just clueless
if its an rtl 8185, couldn't i use this driver 
[HTML]http://rtl8180-sa2400.sourceforge.net/[/HTML]

---

### Post by olidude7 on 2008-08-09
Bump

---

### Post by caljohnsmith on 2008-08-09
If you do:
```
sudo iwlist scan
```
Do you see any wireless networks?

---

### Post by olidude7 on 2008-08-10
> **caljohnsmith said:**
> If you do:
```
sudo iwlist scan
```
Do you see any wireless networks?
shall i do this when its not working, working or both

after windows session (can connect at the moment)

```
oliver@oliver-desktop:~$ sudo iwlist scan
[sudo] password for oliver: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:1E:74:79:70:33
                    ESSID:"SKY28722"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:15:E9:11:60:2C
                    ESSID:"D-link Airplus"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

oliver@oliver-desktop:~$ 


```

and again when network manager can't find networks but the wireless icon is there (after any ubuntu session)

```
oliver@oliver-desktop:~$ sudo iwlist scan
[sudo] password for oliver: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

oliver@oliver-desktop:~$ 


```


i've no idea if it would have anything to do with it but ubuntu and the ubuntu recovery mode appear twice in boot loader, possibly from the ubuntu reinstall mentioned earlier, when now onl one copy of ubuntu is installed on this machine

also each time i ran the scan when it scanned wlan1 there was a delay each time even when nothing was found, i am currently posting this part thru an edit on windows, just a bit for people who are willing to help, don't work urself too hard helping me, its not that hard too go out and get hardware that works on ubuntu out of the box, i mean my old one did, but i needed the extra usb slot sicne this current one is pci

---

### Post by olidude7 on 2008-08-10
bump

---

### Post by olidude7 on 2008-08-11
sorry but this needs bumping again

---

