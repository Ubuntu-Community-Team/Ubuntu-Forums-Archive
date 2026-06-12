---
title: "[SOLVED] gusty: wireless NOT READY"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by sdesrousseaux on 2007-11-02
hi
excuse for my english, i'm a french people
so i've just installed the new version of ubuntu: 7.10 Gutsy

i've a problem with my pci wifi card: SMC2802W, that appears as an ISL3890 or an ISL3886

but eth0 is NOT READY!

here is my configuration:

- iwconfig
```
lo        no wireless extensions.

eth0      NOT READY!  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=31 dBm   Sensitivity=0/200  
          Retry short limit:0   RTS thr=0 B   Fragment thr=0 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
- lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 14)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 06)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 06)
00:04.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 10)
00:0e.0 SCSI storage controller: Adaptec AHA-7850 (rev 03)
00:0f.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
00:10.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:11.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
00:11.1 Input device controller: Creative Labs SB Live! Game Port (rev 06)
01:05.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2 Ultra] (rev 11)
```
- lshw -C network
```
  *-network DISABLED      
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 driverversion=1.2 latency=64 maxlatency=28 mingnt=10 module=prism54 multicast=yes wireless=NOT READY!
```
- dmesg  | grep eth
```
[   53.649257] eth0: resetting device...
[   53.649292] eth0: uploading firmware...
[   53.773158] eth0: firmware version: 1.0.4.3
[   53.773244] eth0: firmware upload complete
[   54.770851] eth0: no 'reset complete' IRQ seen - retrying
[   55.770434] eth0: no 'reset complete' IRQ seen - retrying
[   55.770447] eth0: interface reset failure
```
- fichier interfaces
```
auto lo
iface lo inet loopback
```
- /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 12689
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:b4:00:00:00
Sending on   LPF/eth0/00:30:b4:00:00:00
Sending on   Socket/fallback
SIOCSIFFLAGS: Timer expired
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Timer expired
SIOCSIFFLAGS: Timer expired
Listening on LPF/eth0/00:30:b4:00:00:00
Sending on   LPF/eth0/00:30:b4:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
grep: /etc/resolv.conf: No such file or directory
                                                                         [ OK ]
```

thx
stephane

---

### Post by Lambert on 2007-11-02
I'm not 100% sure as sometimes these drivers/devices get a little confusing. But I believe your device needs the islsm driver and not the prism54 driver. You also need isl3886 firmware. I'm not sure if these are installed with gutsy and like I said, not sure 100% it's the right one.

The firmware does look like a problem and if prism54 is the driver you may need firmware.

---

### Post by sdesrousseaux on 2007-11-03
hi, thx for your response, but i don't know where i can fin these driver and firmware
my pci wifi card is SMC2802W

and it appears as 00:0f.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

so i need ISL3890 driver? and ISL3886 firmware?

thx

---

### Post by Lambert on 2007-11-03
> **sdesrousseaux said:**
> hi, thx for your response, but i don't know where i can fin these driver and firmware
my pci wifi card is SMC2802W

and it appears as 00:0f.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

so i need ISL3890 driver? and ISL3886 firmware?

thx

I'm actually going to suggest trying ndiswrapper first.

You will need to add prism54 to the file /etc/modprobe.d/blacklist so it doesn't load (just add that exact term on a separate line at bottom of file)

Then search the forums or help.ubuntu.com for instrutioncs on using ndiswrapper. You can try the windows drivers that came with the device or there are drivers here. [http://www.ralinktech.com/drivers/Windows/IS_RT2460_WPA_031804_Drv2.01.00.zip](http://www.ralinktech.com/drivers/Windows/IS_RT2460_WPA_031804_Drv2.01.00.zip)

The link for the drivers I gave you is for v2 of your card which I believe is what you have but I haven't verified.

If you want to try the islsm driver you can search for howtos on using the islsm driver or search using your card # for more information. I see the isl3886 firmware in gutsy but not the islsm driver. As I stated before, some of these drivers get confusing and it's possible the islsm driver is becoming deprecated and merging into the prism54 driver but support for your device is not there or not working with that driver it appears.

---

### Post by sdesrousseaux on 2007-11-03
hi, wonderfull it works, thx!!!

i see my wireless network now, but i don't arrive to connect to it...

i put the wep key but it always ask me the key.... i don't know why...

---

### Post by Lambert on 2007-11-03
> **sdesrousseaux said:**
> hi, wonderfull it works, thx!!!

i see my wireless network now, but i don't arrive to connect to it...

i put the wep key but it always ask me the key.... i don't know why...

Search new threads started by kevdog. He has some great posts that might help. Come back with what you tried, what looked like it worked and any output from commands he suggested.

---

### Post by sdesrousseaux on 2007-11-03
hi, it works now...
i've only the set the channel to use and it's ok
thx

---

### Post by kevdog on 2007-11-03
Can you be more specific how you solved this problem -- what you typed -- that would be great.

---

### Post by sdesrousseaux on 2007-11-03
i've installed the driver of my pci card with ndiswrapper:
- cd driver-directory
- sudo ndiswrapper-1.9 -i driver.inf 
- sudo ndiswrapper -m

to solve my problem of chanel, i've changed the channel on my router to 11 and set the chanel to use with this command:
- sudo iwconfig wlan0 channel 11

---

