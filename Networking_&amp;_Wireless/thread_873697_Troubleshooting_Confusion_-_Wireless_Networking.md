---
title: "Troubleshooting Confusion - Wireless Networking"
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by wdeed on 2008-07-29
I'm brand new to Ubuntu, so please forgive me.

I've plugged in my wifi USB IEEE 802.11b/g and installed ndiswrapper as well as the driver. 

Despite this there are no signs of a wireless connection so I am working my way through the trouble shooting, but to be honest I can't figure out if my answers are yes or no to any of the trouble shoots:

"3.2.1 Check for device recognition"

Now I can't find 'Hardware Information' on any menu but to find my device I saw in another forum to write this into the terminal:
lspci
lsusb

When I type in lspci I get the following:

ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02) 
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] 
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02) 
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] 
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller 
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) 
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) 
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) 
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M 


When I type in lsusb I get:

ubuntu@ubuntu:~$ lsusb 
Bus 003 Device 006: ID 0416:0035 Winbond Electronics Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ 

Is there a device recognised?

3.2.2 Check for driver

After typing in the command sudo lshw -C network I get:

ubuntu@ubuntu:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: DP83815 (MacPhyter) Ethernet Controller 
       vendor: National Semiconductor Corporation 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 00 
       serial: 00:0f:20:22:b0:04 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s 

3.2.3 Check device is on

Now surely this is the same as above for 3.2.2?

3.2.4 Check for a connection to the router:

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

Now is this good or bad? 

3.2.5 Check IP assignment:

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0f:20:22:b0:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4808 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4808 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:242632 (236.9 KB)  TX bytes:242632 (236.9 KB) 


3.2.6 Check DNS:

ubuntu@ubuntu:~$ ping 82.211.81.158 
connect: Network is unreachable 

Any help to understand this all would be fantastic.

Thank you in advance

---

### Post by wdeed on 2008-07-29
It would be great if someone could tell me at what step things are going wrong and what changes I should make.

Cheers

---

### Post by Ayuthia on 2008-07-29
> **wdeed said:**
> 
"3.2.1 Check for device recognition"

Now I can't find 'Hardware Information' on any menu but to find my device I saw in another forum to write this into the terminal:
lspci
lsusb

When I type in lspci I get the following:

ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02) 
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] 
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02) 
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+] 
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller 
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50) 
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51) 
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) 
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) 
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU] 
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M 


When I type in lsusb I get:

ubuntu@ubuntu:~$ lsusb 
Bus 003 Device 006: ID 0416:0035 Winbond Electronics Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$ 

Is there a device recognised?
Since this is a USB device, it should be found under lsusb so I am guessing that it is the Winbond Electronics Corp.

> 3.2.2 Check for driver

After typing in the command sudo lshw -C network I get:

ubuntu@ubuntu:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: DP83815 (MacPhyter) Ethernet Controller 
       vendor: National Semiconductor Corporation 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 00 
       serial: 00:0f:20:22:b0:04 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=10MB/s 
Since it is a USB device, lshw -C network does not provide any information.

> 3.2.3 Check device is on

Now surely this is the same as above for 3.2.2?The only way that I know to check and see if the USB device is on is to check and see if there are any lights on the USB device.  But if it is detected by lsusb, it usually means that it is on also.

> 3.2.4 Check for a connection to the router:

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

Now is this good or bad? 

3.2.5 Check IP assignment:

ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0f:20:22:b0:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4808 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4808 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:242632 (236.9 KB)  TX bytes:242632 (236.9 KB) 

3.2.6 Check DNS:

ubuntu@ubuntu:~$ ping 82.211.81.158 
connect: Network is unreachable 

Any help to understand this all would be fantastic.

Thank you in advance
eth0 is your wired ethernet card.  Your wireless is usually wlan0 or eth1.  Since it did not find anything, it means that something is not configured right yet.

You might start off by checking if you can get the card up by typing in the Terminal:
```
sudo ifconfig wlan0 up
```
If it says no such device, then try:
```
sudo ifconfig eth1 up
```
If it says the same thing, we can see if ndiswrapper can start it up.  You will need to check the verison of ndiswrapper to make sure that it is all valid (no error appear):
```
ndiswrapper -v
```
Then you will need to check and see if the driver is loaded:
```
ndiswrapper -l
```
If it says that the driver is installed and that the device is present, then it is ok.  If there is an alternate driver, please let us know.  It might mean that there is another driver that might work or else we might have to blacklist that driver (remove it from loading).

---

### Post by wdeed on 2008-07-29
Thank you Ayuthia for your reply.

I decided to (maybe foolishly) properly install Ubuntu on the HD and have now reinstalled the Windows Wireless Drivers program and it says

netw35w 
hardware present: Yes

I then checked to tried to get the card up by typing in the Terminal:

sudo ifconfig wlan0 up

But it said no such device, and said the same for:

sudo ifconfig eth1 up

I typed in ndiswrapper -v and got:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:    /lib/modules/2.6.24-16-generic/ubuntu/misc.ndiswrapper/ndiswrapper.ko
version: 1.52
vermagic: 2.6.24-16-generic SMP mod_unload 586


I then checked to see if the driver was loaded and got this:

install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile install driver described by ‘inffile’
-a devid driver use installed ‘driver’ for ‘devid’
-r driver remove ‘driver’
-l list installed drivers
-m write configuration for modprobe
-ma write module alias configuration for all devices
-mi write module install configuration for all devices
-v report version information

where ‘devid’ is either PCIID or USBID of the form XXXX:XXXX,
as reported by ‘lspci -n’ or ‘lsusb’ for the card

I'm really stuck. Any help on what to do next would be greatly appreciated.

Thank you

---

### Post by Ayuthia on 2008-07-29
> **wdeed said:**
> Thank you Ayuthia for your reply.

I decided to (maybe foolishly) properly install Ubuntu on the HD and have now reinstalled the Windows Wireless Drivers program and it says

netw35w 
hardware present: Yes

I then checked to tried to get the card up by typing in the Terminal:

sudo ifconfig wlan0 up

But it said no such device, and said the same for:

sudo ifconfig eth1 up

I typed in ndiswrapper -v and got:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:    /lib/modules/2.6.24-16-generic/ubuntu/misc.ndiswrapper/ndiswrapper.ko
version: 1.52
vermagic: 2.6.24-16-generic SMP mod_unload 586


I then checked to see if the driver was loaded and got this:

install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile install driver described by ‘inffile’
-a devid driver use installed ‘driver’ for ‘devid’
-r driver remove ‘driver’
-l list installed drivers
-m write configuration for modprobe
-ma write module alias configuration for all devices
-mi write module install configuration for all devices
-v report version information

where ‘devid’ is either PCIID or USBID of the form XXXX:XXXX,
as reported by ‘lspci -n’ or ‘lsusb’ for the card

I'm really stuck. Any help on what to do next would be greatly appreciated.

Thank you

Since you used Windows Wireless Drivers and it says Hardware Present, it is the same thing as ndiswrapper -l.  Most likely you typed something wrong when you typed ndiswrapper -l because the reply that it gave was a help screen when ndiswrapper receives a command that it does not understand.  Also, when there are no errors when you do ifconfig eth1 up, I am guessing that your wireless card is eth1.  If you type ifconfig, you should see eth1 in the list of items.

The next step would be to see if you are able to see any wireless sites:
```
sudo iwlist scan
```

---

### Post by eram on 2008-07-29
Hmmm... You said you have installed ndiswrapper. How did you go about that? Have you installed ndisgtk also? That needs to be installed also for the windows wireless drivers to work.

Thanks!

---

### Post by wdeed on 2008-07-29
Ah yes, I just typed in ndiswrapper -l and it said:
netw35w: driver installed
          device (0416:0035) present

I tried sudo iwlist scan:
lo       interface doesn't support scanning

eth0     Interface doesn't support scannign

Any tips?

---

### Post by wdeed on 2008-07-29
eram - I installed it by having the CD in and then System - Administration - Synaptic Package Manager

ndisgtk is installed as that was how I was able to install the inf file.

---

### Post by Ayuthia on 2008-07-29
> **wdeed said:**
> Ah yes, I just typed in ndiswrapper -l and it said:
netw35w: driver installed
          device (0416:0035) present

I tried sudo iwlist scan:
lo       interface doesn't support scanning

eth0     Interface doesn't support scannign

Any tips?

I guess we should see that ndiswrapper is loaded:
```
lsmod|grep ndiswrapper
```
If it shows ndiswrapper, then it is loaded.

```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
This set of commands is going to remove ndiswrapper and then load it again.  
```
dmesg|grep ndiswrapper
```
This command will help us see if there are any error messages when we try to load ndiswrapper.

---

### Post by wdeed on 2008-07-30
Thank you Ayuthia for all your help so far.

I typed in the code to see if the ndiswrapper is loaded:

ndiswrapper          192928   0
usbcore              146028   6  ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_h 
cd

I removed the then loaded the ndiswrapper.

Then I put in the command for error messages and got the following:
[  817.132214] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1433.866476] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1433.866510] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 1433.866526] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[ 1433.866553] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 1433.866570] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1433.866588] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1433.866604] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[ 1433.866621] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1433.866637] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[ 1433.866654] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 1433.866693] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1433.866710] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[ 1433.866727] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[ 1433.866744] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 1433.866761] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1433.866778] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1433.866795] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 1433.866811] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 1433.866827] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 1433.866853] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 1433.866869] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 1433.866894] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 1433.866911] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 1433.866927] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1433.866944] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[ 1433.866960] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1433.866977] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 1433.866994] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[ 1433.867015] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw35w'
[ 1433.908932] ndiswrapper (load_wrap_driver:112): couldn't load driver netw35w; check system log for messages from 'loadndisdriver'
[ 1433.909006] usbcore: registered new interface driver ndiswrapper
[43047.324718] usbcore: deregistering interface driver ndiswrapper
[43047.326063] ndiswrapper (ntoskernel_exit:2708): object d9f0e220(2) was not freed, freeing it now
[43057.605600] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[43057.954455] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[43057.954488] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[43057.954505] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[43057.954532] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[43057.954549] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[43057.954567] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[43057.954584] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[43057.954601] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[43057.954617] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[43057.954634] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[43057.954674] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[43057.954691] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[43057.954708] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[43057.954725] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[43057.954742] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[43057.954760] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[43057.954776] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[43057.954841] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[43057.954859] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[43057.954884] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[43057.954900] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[43057.954924] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[43057.954940] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[43057.954956] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[43057.954972] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[43057.954988] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[43057.955004] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[43057.955020] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[43057.955040] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw35w'
[43057.996799] ndiswrapper (load_wrap_driver:112): couldn't load driver netw35w; check system log for messages from 'loadndisdriver'
[43057.996870] usbcore: registered new interface driver ndiswrapper

---

### Post by Ayuthia on 2008-07-30
> **wdeed said:**
> 
[43057.955040] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netw35w'
[43057.996799] ndiswrapper (load_wrap_driver:112): couldn't load driver netw35w; check system log for messages from 'loadndisdriver'
[43057.996870] usbcore: registered new interface driver ndiswrapper
It does not look like it likes the driver, but that is a guess.  By any chance, are there any messages in /var/log for loadndisdriver?  You might try:
```
sudo grep -r loadndisdriver /var/log
```
This command will search for the word loadndisdriver in all the files.  You might even search for loadndisdriver:
```
sudo updatedb
locate loadndisdriver
```
The first command will update the database for locate.  The second command will search for a file called loadndisdriver.

---

