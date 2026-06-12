---
title: "WIFI connection problem = PLEASE HELP!"
date: 2005-07-20
forum: Networking &amp; Wireless
---

### Post by jordanj1969 on 2005-07-20
I have a HP Pavilion zv5037wm Laptop with built-in Broadcom 802.11b/g WLAN card. Not for the lack of trying, I can not get it to connect to my USR8054 Wireless router. It works fine when I'm logged on under Windows XP. I have Ubuntu with Kubuntu-Desktop installed. Can anyone assist me?

Below is the output of my iwconfig, ifconfig and /etc/network/interfaces


jjordan@ubuntujj:~$ ifconfig
eth0 Link encap:Ethernet HWaddr (My Mac Address)
inet addr:192.168.123.102 Bcast:192.168.123.255 Mask:255.255.255.0
inet6 addr: fe80::202:3fff:fe6c:6a6/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1281 errors:0 dropped:0 overruns:0 frame:0
TX packets:607 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:701789 (685.3 KiB) TX bytes:107787 (105.2 KiB)
Interrupt:19 Base address:0xa000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:25123 errors:0 dropped:0 overruns:0 frame:0
TX packets:25123 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2264384 (2.1 MiB) TX bytes:2264384 (2.1 MiB)

wlan0 Link encap:Ethernet HWaddr (My Mac Address)
inet6 addr: fe80::290:4bff:fe4c:fb38/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:18 Memory:d0204000-d0205fff

jjordan@ubuntujj:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID: off/any
Mode:Managed Frequency:2.412 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management: off
Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.



jjordan@ubuntujj:/etc/network$ cat interfaces | more
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
iface eth0 inet dhcp

iface ppp0 inet ppp
provider ppp0


iface wlan0 inet dhcp
wireless-essid jordan
wireless-key (My Key)

auto wlan0

---

### Post by Lunde on 2005-07-20
Try writing manually writing the ESSID, case sensitive
$ sudo iwconfig wlan0 essid *****

where the stars are your routers ESSID
Then:
$ dhclient wlan0

---

### Post by Lunde on 2005-07-20
Also.. I can see that iwconfig lacks a key.. it's not reading your network interface.
Try:
$ sudo iwconfig wlan0 key ************

Note, this will not be a permanent solution, but just to locate if this is the error

---

### Post by jordanj1969 on 2005-07-20
I've done both of those commands, still not working

---

### Post by Lunde on 2005-07-20
[QUOTE=jordanj1969]I've done both of those commands, still not working[/QUOTE]
 what's your output for wlan0 from iwconfig now? can you post it.. make sure you don't reboot your PC after you entered those commands, they will disapere.

---

### Post by jordanj1969 on 2005-07-20
jjordan@ubuntujj:/etc/network$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by jordanj1969 on 2005-07-20
Does the eth0 interface need to be disabled?  I've tried it both ways with no luck, just curious.


jjordan@ubuntujj:/etc/network$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by varunus on 2005-07-20
What is the output of "sudo iwlist wlan0 scan" in a terminal?

It looks like your card isn't finding the router...The scan will see if it is or not.  Did you follow the broadcom specific howto from the "Tips and Tricks" section of the forum?  There's a glitch in some broadcom cards that stop ndiswrapper from turning on the radio.  (Something about radiostate.)

---

### Post by Lunde on 2005-07-20
There's no changes in iwconfig... still without the Essid. The suggestion from varunus is good you should look into that, Also can you check your /var/log/syslog for errors and post them here if you still have problems.

---

### Post by jordanj1969 on 2005-07-20
jjordan@ubuntujj:/etc/network$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:00:8D:86
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-86 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:C0:49:E0:81:16
                    ESSID:"jordan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-53 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

---

### Post by jordanj1969 on 2005-07-20
I did a cat of a couple of the *.conf files in /etc/ndiswrapper/bcmwl5 folder and did not find (RadioState). Could this be causing the problem?

---

### Post by ProNoblem on 2005-07-20
I've also had this problem, you could check if we have the same card by executing the next command in a terminal:
```
joris@instant-coffee:~ $ lspci |grep Broad
0000:02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```
As you can see, I have the BCM4306 chip on my Asus WL100G (I don't know if this is the same one as you have (simply try [COLOR=Blue]lspci |grep Broad[/COLOR], but it's probable that this will work on your laptop)

The difference between our two configs lies within the used driver, I've attached my driverfiles so that you can try with the exact same files.
With the use of these files, there was an entry called "RadioState|0" in my config files (/etc/ndiswrapper/bcmwl5[COLOR=Red]a[/COLOR]/*.conf, mind the "a", which makes me believe that were using different drivers for the same card)
Changing this into "RadioState|1" worked with my card (do "rmmod ndiswrapper" and then "modprobe ndiswrapper" to try the editted configfiles)

Hope this will solve your problem.

---

### Post by jordanj1969 on 2005-07-20
I used your driver, and yes, we do have the exact same wirless card.  I still cant get it to work.... how do I clean out ndiswrapper and all wireless drivers and start over?  I changed the RadioState to 1 in the .conf files.  There were only 2 files that needed to be changed.  This is what I'm seeing when I perform ifconfig command for my wlan0:

wlan0     Link encap:Ethernet  HWaddr 00:90:4B:4C:FB:38
          inet6 addr: fe80::290:4bff:fe4c:fb38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:d0204000-d0205fff

Is the Link encap suppose to be Ethernet?

---

### Post by ProNoblem on 2005-07-21
To see which drivers are installed by ndiswrapper, do:
```
sudo ndiswrapper -l
```
You should see something like this:
```
joris@instant-coffee:~ $ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5a driver present, hardware present
```

Now do the following for every driver installed:
```
sudo ndiswrapper -e bcmwl5a
```
Change bcmwl5a to the drivers listed with 'ndiswrapper -l'

Check if every driver is really deleted with 'ndiswrapper -l' again.
If all drivers are gone, do:
```
sudo rm /etc/ndiswrapper/*
```
Now all the drivers are gone, and you can begin with a clean slate.

Install the driver you've downloaded from the attachment by doing:
```
sudo ndiswrapper -i  /folder/where/you/extracted/the/drivers/bcmwl5a.inf
```

Now edit the *.conf files in /etc/ndiswrapper and change 'RadioState|0' to 'RadioState|1' (be sure to check every file!)

Now we create an alias for wlan0 into module configuration file so that this module is used whenever the wireless interface is started:
```
sudo ndiswrapper -m
```

You also need to add the ndiswrapper module to the startup modules so Ubuntu can setup the device when your machine starts. You need to add ndiswrapper to the end of the /etc/modules file:
```
sudo gedit /etc/modules
```

Reboot your laptop and cross your thumbs.. (hopefully this'll work)

P.s. Just to be sure, you're absolutely 100% without a doubt sure that there is no button on your laptop to enable/disable the internal wireless card, and if this button is there that it's set to enable?

---

### Post by csnowman00 on 2007-08-29
I had the same problem. 

You need to upgrade the firmware for the router.  The router will work with XP and not Ubuntu or Vista.  It took me a week to figure it out.

Here is my post:
[http://ubuntuforums.org/showthread.php?t=534220&highlight=usr8054](http://ubuntuforums.org/showthread.php?t=534220&highlight=usr8054)

---

### Post by kevdog on 2007-08-29
Few things since a lot of advice is being thrown around here - each going a  different direction.

How did you install the original driver?? Seems like ndiswrapper.
Can you post the following:
lshw -C network
lspci -nn
ndiswrapper -v

Im assuming you have the Windows XP drivers available somewhere?
Do you have a wired ethernet connection on this computer??

This info will provide all of us enough info to make a reasonable decision how to proceed.

---

### Post by DennisMonague on 2007-11-03
I'm having a similar problem with different equipment.  My system is an Acer Aspire 5040 with an Atheros AR5005G Wireless Network Adapter (seems like lots of people are having problems with these).  I'm running 7.10.  My computer has a radio button on the front face of the laptop (will light up if it's on).  I have no problems running my wireless in XP (except with a reformat and clean install that is, then I have to use the recovery cd's because just installing the drivers for some reason won't work)  Here is the information on my system as requested in the previous post: 

dennis@dennis-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:6b:c0:0d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.49+,06/21/2007,5.3.0.56 latency=128 maxlatency=28 mingnt=10 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:43:64:e2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.101 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes

dennis@dennis-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374] (rev 80)
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375] (rev 80)
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373] (rev 80)
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 82)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller [1002:4376] (rev 80)
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377] (rev 80)
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371] (rev 80)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
06:05.0 Ethernet controller [0200]: Atheros Communications, Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
06:06.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)

dennis@dennis-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.49
vermagic:       2.6.22-14-generic SMP mod_unload 

Not sure if you need this too but I did the following just in case: 

dennis@dennis-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D3:43:64:E2  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:fe43:64e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2870525 (2.7 MB)  TX bytes:623846 (609.2 KB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:6B:C0:0D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Memory:d0200000-d0210000 

dennis@dennis-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dennis@dennis-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for dennis:
wlan0     No scan results

I've been at this for about 2 weeks now.  If I can get this wireless thing sorted out I'll probably just do away with windows altogether (running a dual boot system at the moment).  Thanks in advance.

---

### Post by DennisMonague on 2007-11-03
I forgot to note.  Under System>Administration>Network a wireless connection is listed and is noted as roaming mode enabled.  As well, System>Administration>Network Tools I can change to Wireless Interface (wlan0).  Finally, in the little network icon on the desktop, if clicked will say i can do a bunch of stuff like connect and create wireless networks.  

I really need some help on this one.  I'm new to Linux and have been reading so much I think I now need glasses!

---

