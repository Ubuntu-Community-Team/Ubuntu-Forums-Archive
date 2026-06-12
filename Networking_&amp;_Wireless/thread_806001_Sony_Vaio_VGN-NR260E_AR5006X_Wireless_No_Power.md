---
title: "Sony Vaio VGN-NR260E AR5006X Wireless No Power"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by DVANDERM on 2008-05-24
I have an issue with my wireless network card on my Sony Vaio VGN-NR260E. The wireless card will not turn on. The code on the case is AR5BXB63 which when Googling resuls that my wireless card is a AR5006x. Here is what I know and what I have tried:

1. The restricted drivers that are installed do not work. 
2. The light on the wireless card does not light up.
3. The card is recognized but just won't turn on. 
4. I have tried many different "suggestions" and followed numerous tutorials to a T.
5. I have installed ndiswrapper and tried using both the XP driver and the Vista Driver. Neither worked. 
6. I have tried different suggestions and posts for other cards with the same issue. None have worked. 
7. Here is the information for various commands:

iwconfig provides

> 
danny@danny-LT:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


sudo lshw -C network provides

> 
danny@danny-LT:~$ sudo lshw -C network  
*-network                      
description: Ethernet interface       p
roduct: 88E8039 PCI-E Fast Ethernet Controller       
vendor: Marvell Technology Group Ltd.       
physical id: 0       
bus info: pci@0000:02:00.0       
logical name: eth0       
version: 15       
serial: 00:1a:80:24:de:0d       
capacity: 100MB/s       
width: 64 bits       
clock: 33MHz       
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation       
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair  

*-network UNCLAIMED       
description: Ethernet controller       
product: AR242x 802.11abg Wireless PCI Express Adapter       vendor: Atheros Communications Inc.       
physical id: 0       
bus info: pci@0000:06:00.0       
version: 01       
width: 64 bits       
clock: 33MHz       
capabilities: pm msi pciexpress msix cap_list       configuration: latency=0


sudo iwlist scan provides

> 
danny@danny-LT:~$ sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.



sudo cat /etc/network/interfaces provides

> 
danny@danny-LT:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback


lspci -vv provides (only snipped the ethernet portion)

> 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)	
Subsystem: Sony Corporation Unknown device 902d	
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-	
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-	
Latency: 0, 
Cache Line Size: 64 bytes	
Interrupt: pin A routed to IRQ 219	
Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=16K]	
Region 2: I/O ports at 2000 [size=256]	
Capabilities: <access denied>

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)	
Subsystem: Foxconn International, Inc. Unknown device e000	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-	
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-	
Interrupt: pin A routed to IRQ 18	
Region 0: Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]	
Capabilities: <access denied>

---

### Post by DVANDERM on 2008-05-24
Woops. I apologize. I forgot to run lspci -vv as sudo. Here it is:
> 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)

	Subsystem: Sony Corporation Unknown device 902d

	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-

	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

	Latency: 0, Cache Line Size: 64 bytes

	Interrupt: pin A routed to IRQ 219

	Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=16K]

	Region 2: I/O ports at 2000 [size=256]

	Capabilities: [48] Power Management version 2

		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)

		Status: D0 PME-Enable- DSel=0 DScale=1 PME-

	Capabilities: [50] Vital Product Data

	Capabilities: [5c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+

		Address: 00000000fee0300c  Data: 413a

	Capabilities: [e0] Express Legacy Endpoint IRQ 0

		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-

		Device: Latency L0s unlimited, L1 unlimited

		Device: AtnBtn- AtnInd- PwrInd-

		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-

		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-

		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes

		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0

		Link: Latency L0s <256ns, L1 unlimited

		Link: ASPM L0s Enabled RCB 128 bytes CommClk+ ExtSynch-

		Link: Speed 2.5Gb/s, Width x1



06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

	Subsystem: Foxconn International, Inc. Unknown device e000

	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-

	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

	Interrupt: pin A routed to IRQ 18

	Region 0: Memory at fa000000 (64-bit, non-prefetchable) [disabled] [size=64K]

	Capabilities: [40] Power Management version 2

		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)

		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

		Address: 00000000  Data: 0000

	Capabilities: [60] Express Legacy Endpoint IRQ 0

		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-

		Device: Latency L0s <512ns, L1 <64us

		Device: AtnBtn- AtnInd- PwrInd-

		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-

		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-

		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes

		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0

		Link: Latency L0s <512ns, L1 <64us

		Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-

		Link: Speed 2.5Gb/s, Width x1

	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1

		Vector table: BAR=0 offset=00000000

		PBA: BAR=0 offset=00000000




I just discovered the edit button... 

sudo cat /etc/resolv.conf results in the following:

> 

cat: /etc/resolv.conf: No such file or directory


---

### Post by DVANDERM on 2008-05-24
I have discovered with further research that it appears MadWifi does not support this card yet.

---

### Post by Syspeg on 2008-05-29
I have the same networkcard on my LG E510. I found a solution here [http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html]("http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html") I't was real easy to follow. If you wan't to have the solution in swedish it's here. [http://syspeg.googlepages.com/programmering2]("http://syspeg.googlepages.com/programmering2") I hope this works for you.

---

### Post by DVANDERM on 2008-05-29
> **Syspeg said:**
> I have the same networkcard on my LG E510. I found a solution here [http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html]("http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html") I't was real easy to follow. If you wan't to have the solution in swedish it's here. [http://syspeg.googlepages.com/programmering2]("http://syspeg.googlepages.com/programmering2") I hope this works for you.

THANK YOU THANK YOU THANK YOU!!!!! YOU"RE AWESOME!!! :o)

---

### Post by DVANDERM on 2008-06-03
This works great but I keep having to redo the following when I log in:

cd madwifi-ng-r2756+ar5007
sudo modprobe ath_pci

I tried doing the following however I get an error message about Permission denied:

sudo echo ath_pci >> /etc/modules

Anyone have any thoughts on what I can do to have it to where I don't have to keep re entering the above commands every time I log in?

---

### Post by mikebdoss on 2008-08-26
For those of you still struggling with this, Chili555's method at [http://ubuntuforums.org/showpost.php?p=5557124&postcount=4](http://ubuntuforums.org/showpost.php?p=5557124&postcount=4) worked perfectly for me on the Vaio NR260E (using the Atheros AR242x wireless card).

---

### Post by DVANDERM on 2009-05-30
Updated to 9.04 and now I can't get this to work. Tried everything here. Madwifi.org is having issues. Anyone have any suggestions as the restricted drivers that come with 9.04 do not work.

Oh and here is "sudo lshw -C network"

```

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1d:d9:76:ea:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:36:ff:24:91:9b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by t0mppa on 2009-05-31
They migrated to madwifi-project.org.

9.04 got ath5k as default driver, since its development has taken it past the older one (ath_pci). Did you try that before enabling the ath_pci driver from the proprietary drivers?

---

### Post by DVANDERM on 2009-05-31
> **t0mppa said:**
> They migrated to madwifi-project.org.

9.04 got ath5k as default driver, since its development has taken it past the older one (ath_pci). Did you try that before enabling the ath_pci driver from the proprietary drivers?

Yes. I tried enabling the restricted drivers. That didn't work at all. 

Funny thing is now the wireless is working again. First it worked, then it didn't work, now it does again? 

But all is well now as I followed what this guy provided here: [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html?showComment=1243783666846#c6633531152309505753](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html?showComment=1243783666846#c6633531152309505753) and it seems to be ok for now. I'll just have to wait to figure out if it is truly fixed or just faking me out. 

Thanks for the response.

---

### Post by DVANDERM on 2009-05-31
I rebooted and it's not working again.

---

### Post by DVANDERM on 2009-05-31
I reinstalled 9.04. It is working again. The following is what I have while it's working:

sudo lshw -C network
```

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1d:d9:76:ea:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.103 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:c0:11:b3:56:e2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
sudo lspci
```

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"********************"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:23:69:5B:62:9A   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=106/100  Signal level:-34 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:1a:80:24:de:0d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:76:ea:03  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:d9ff:fe76:ea03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:785 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1414026 (1.4 MB)  TX bytes:117166 (117.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-D9-76-EA-03-61-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

This time when I loaded the updates after the install I deselected all the bluetooth updates on a hunch. I'm not sure if there is something with the bluetooth updates that are causing an issue but I'm not having problems now after the update like before. 

I also reported the bug that I plan on updating with new notes:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382188](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382188)

---

### Post by DVANDERM on 2009-05-31
LOL

It stopped working YET AGAIN! ](*,)

I now show this:

sudo lshw -C network

```
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1a:80:24:de:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.1.106 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1d:d9:76:ea:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:23:72:53:50:87
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

sudo lspci

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

iwconfig

```

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

``` 

sudo ifconfig

```

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

```

so I guess it's not the blue-tooth after all.

---

### Post by t0mppa on 2009-06-01
Since lshw says your interface is disabled, are you sure you didn't accidentally press the on/off button on your laptop? If not, you could try to bring it up with 'sudo ifconfig wlan0 up'.

---

### Post by DVANDERM on 2009-06-01
> **t0mppa said:**
> Since lshw says your interface is disabled, are you sure you didn't accidentally press the on/off button on your laptop? If not, you could try to bring it up with 'sudo ifconfig wlan0 up'.

It's a slider switch. I tried both ways just in case. I tried the ifconfig wlan0 up before but it gave me an error message because the wireless card wasn't even recognized. Wait a minute, I didn't do it with sudo though. Hmmmmmm... if turns out to be that I am going to slap myself!

I'll try it tonight when I get home.

Thanks!

---

### Post by DVANDERM on 2009-06-01
I haven't tried the suggested 'sudo ifconfig wlan0 up' yet. I turned my laptop on when I came home and it is working... again. This is so strange.

---

### Post by t0mppa on 2009-06-01
Well, like the saying goes: don't fix it, if it isn't broken. :)

---

### Post by DVANDERM on 2009-06-01
I'm not I'm not! I'm just waiting for it to die again. LOL I really want to know what is up with it. LOL.

---

