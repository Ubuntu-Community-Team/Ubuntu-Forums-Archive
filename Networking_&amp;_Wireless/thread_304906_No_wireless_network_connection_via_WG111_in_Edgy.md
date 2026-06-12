---
title: "No wireless network connection via WG111 in Edgy"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by phazon. on 2006-11-22
Hi

I've installed 6.10 on my PC with any no problem, but am having serious problems getting a network connection working. I understand 6.10 should support the Netgear WG111 out of the box - Device Manager does show that it is connected and if I do a 'iwconfig' it shows me that wlan0 has an 802.11b/g device with the correct ESSID for my network (as I defined in the GUI). However next to Access Point it says 'Not-Associated'. If I continue to do iwconfigs I can see it is just cycling through the wireless channels one by one.

Can anyone point out where I am going wrong in trying to get connected to my access point?

Thanks

---

### Post by FrodoB on 2006-11-22
Well if it is a WG111v2 then it should work out of the box and your WEP key is like an issue. Completely remove it while debugging. When it is connecting go generate some known correct keys:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

If you device is not version 2 then I don't know if it will work or not.  You should probably publish the output of:

lsusb

so we can see what chipset you actually have.

---

### Post by phazon. on 2006-11-22
Hi

Thanks for the quick response. I have already disabled the encryption on the router, and it is a v2 WG111 I've got - this is the output from lsusb

nick@home-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 003 Device 001: ID 0000:0000

Thanks

---

### Post by FrodoB on 2006-11-22
I have one here in front of me, here is my lsusb:

Bus 001 Device 003: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

You should see something like this from iwconfig:

wlan0     802.11b/g  Mode:Managed  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If you do then go to the System->Administration->Networking menu and configure the system as your access point is setup.

Check the contents of /etc/networking/interfaces, it should be something like this:

iface wlan0 inet dhcp
wireless-essid My_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

You can make some good WEP keys at:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

A good connection looks like this:
wlan0     802.11b/g linked  ESSID:"My_ESSID"  
          Mode:Managed  Channel=1  Access Point: 00:70:22:B3:53:17   
          Bit Rate=54 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

You should be able to control it with

$ sudo ifdown wlan0

$ sudo ifup wlan0

---

### Post by phazon. on 2006-11-22
OK so my interfaces file looks like yours except auto wlan0 is before the other lines, and I don't have a key entry because I have no security enabled.

I did a ifdown and ifup command, and the ifup started a DHCPdiscover process - this tried discovering to 255.255.255.255 6 times and then said no DHCPOFFERS revceived.

Don't understand.... Please help!

Thanks

---

### Post by phazon. on 2006-11-22
If I go into Network Tools and select the wlan0, it says 'not available' for all the Interface Information - any clues from this?

I don't know where else to look for info or to change settings....

---

### Post by FrodoB on 2006-11-22
Your interfaces entry should look like this if you have no security:

auto wlan0
iface wlan0 inet dhcp
wireless-essid My_ESSID

It does not matter if auto wlan0 is before or after. I always make it after, because that is the way I like it.

What does your iwconfig output look like?

---

### Post by phazon. on 2006-11-22
Hi

Here's the output:

nick@home-desktop:/etc/network$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"NWIB_WIFI"  
          Mode:Managed  Channel=7  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Sensitivity=4/6  
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


gedit interfaces:
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid NWIB_WIFI


Very much appreciate your time on this. It's driving me mad ](*,)

---

### Post by FrodoB on 2006-11-22
Using gedit you need to manually edit the /etc/network/interfaces file and make the record look just like this:

iface wlan0 inet dhcp
wireless-essid NWIB_WIFI
auto wlan0

$ sudo gedit /etc/network/interfaces 

Save it.

Simply unplug the WG111v2, and wait about 5 seconds and then plug it back in and wait about 10 seconds.  

Then run iwconfig and see if it associates.

Show the new iwconfig.


If you run dmesg after putting it back in you should see:

[17179862.732000] Linux kernel driver for RTL8187 based WLAN cards
[17179862.732000] Copyright (c) 2004-2005, Andrea Merello
[17179862.732000] rtl8187: Initializing module
[17179862.732000] rtl8187: Wireless extensions version 20
[17179862.732000] rtl8187: Initializing proc filesystem
[17179862.732000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17179862.848000] rtl8187: Card MAC address is 00:14:6c:66:49:47
[17179863.020000] rtl8187: Card reports RF frontend Realtek 8225
[17179863.020000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17179863.020000] rtl8187: WW:use it with care and at your own risk and
[17179863.020000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179863.052000] rtl8187: This seems a legacy 1st version radio
[17179863.052000] rtl8187: PAPE from CONFIG2: 0
[17179863.052000] rtl8187: Driver probe completed
[17179863.052000] 
[17179863.052000] usbcore: registered new driver rtl8187
[17179863.060000] rtl8187: Setting SW wep key
[17179863.712000] rtl8187: Card successfully reset
[17179871.212000] Linking with H.M.S. Hood
[17179871.268000] Associated successfully
[17179871.268000] Using G rates
reprice@xw4200:~$

---

### Post by phazon. on 2006-11-22
OK done that - interfaces now looks like yours. dmesg does not, link not ready - see the end....
(excuse long post, left it all in from near to first wifi reference)



[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
.
.
.
[17179590.948000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179590.992000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179591.104000] irda_init()
[17179591.104000] NET: Registered protocol family 23
[17179591.204000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179591.204000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179591.204000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179591.204000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179591.216000] 
[17179591.216000] Linux kernel driver for RTL8187 based WLAN cards
[17179591.216000] Copyright (c) 2004-2005, Andrea Merello
[17179591.216000] rtl8187: Initializing module
[17179591.216000] rtl8187: Wireless extensions version 20
[17179591.216000] rtl8187: Initializing proc filesystem
[17179591.216000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17179591.568000] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[17179591.768000] ts: Compaq touchscreen protocol output
[17179592.028000] rtl8187: Card MAC address is 00:18:4d:02:ea:bd
[17179592.244000] rtl8187: Card reports RF frontend Realtek 8225
[17179592.244000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17179592.244000] rtl8187: WW:use it with care and at your own risk and
[17179592.244000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179592.292000] rtl8187: This seems a legacy 1st version radio
[17179592.292000] rtl8187: PAPE from CONFIG2: 0
[17179592.292000] rtl8187: Driver probe completed
[17179592.292000] 
[17179592.292000] usbcore: registered new driver rtl8187
[17179593.084000] rtl8187: Card successfully reset
[17179593.084000] lp0: using parport0 (interrupt-driven).
[17179593.320000] SCSI subsystem initialized
[17179593.324000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179593.324000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.472000] Adding 3068372k swap on /dev/disk/by-uuid/b39d7745-3284-480f-9163-9919fa92b923.  Priority:-1 extents:1 across:3068372k
[17179595.548000] EXT3 FS on hda2, internal journal
[17179595.828000] kjournald starting.  Commit interval 5 seconds
[17179595.840000] EXT3 FS on hda3, internal journal
[17179595.840000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.180000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179596.404000] NTFS volume version 3.0.
[17179601.668000] NET: Registered protocol family 17
[17179605.312000] ACPI: Power Button (FF) [PWRF]
[17179605.312000] ACPI: Power Button (CM) [PWRB]
[17179605.496000] ibm_acpi: ec object not found
[17179605.536000] pcc_acpi: loading...
[17179608.908000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179608.908000] apm: overridden by ACPI.
[17179615.308000] Bluetooth: Core ver 2.8
[17179615.308000] NET: Registered protocol family 31
[17179615.308000] Bluetooth: HCI device and connection manager initialized
[17179615.308000] Bluetooth: HCI socket layer initialized
[17179615.344000] Bluetooth: L2CAP ver 2.8
[17179615.344000] Bluetooth: L2CAP socket layer initialized
[17179615.348000] Bluetooth: RFCOMM socket layer initialized
[17179615.348000] Bluetooth: RFCOMM TTY layer initialized
[17179615.348000] Bluetooth: RFCOMM ver 1.7
[17179736.300000] NET: Registered protocol family 10
[17179736.300000] lo: Disabled Privacy Extensions
[17179736.300000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179736.300000] IPv6 over IPv4 tunneling driver
[17182918.680000] usb 2-2: new high speed USB device using ehci_hcd and address 2
[17182918.816000] usb 2-2: configuration #1 chosen from 1 choice
[17182920.192000] usbcore: registered new driver libusual
[17182920.900000] Initializing USB Mass Storage driver...
[17182920.904000] scsi0 : SCSI emulation for USB Mass Storage devices
[17182920.904000] usb-storage: device found at 2
[17182920.904000] usb-storage: waiting for device to settle before scanning
[17182920.904000] usbcore: registered new driver usb-storage
[17182920.904000] USB Mass Storage support registered.
[17182925.904000] usb-storage: device scan complete
[17182925.904000]   Vendor: Flash/SM  Model: Super Talent 2.0  Rev: 2040
[17182925.904000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182926.600000] SCSI device sda: 252928 512-byte hdwr sectors (129 MB)
[17182926.600000] sda: Write Protect is off
[17182926.600000] sda: Mode Sense: 43 00 00 00
[17182926.600000] sda: assuming drive cache: write through
[17182926.604000] SCSI device sda: 252928 512-byte hdwr sectors (129 MB)
[17182926.604000] sda: Write Protect is off
[17182926.604000] sda: Mode Sense: 43 00 00 00
[17182926.604000] sda: assuming drive cache: write through
[17182926.604000]  sda: sda1
[17182926.660000] sd 0:0:0:0: Attached scsi removable disk sda
[17182926.676000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17182928.916000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17182947.420000] usb 2-2: USB disconnect, address 2
[17190943.632000] rtl8187: RX process aborted due to explicit shutdown
[17190943.632000] rtl8187: RX process aborted due to explicit shutdown
[17190943.632000] rtl8187: RX process aborted due to explicit shutdown
[17190971.416000] rtl8187: Card successfully reset
[17190978.584000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17191466.204000] rtl8187: RX process aborted due to explicit shutdown
[17191466.204000] rtl8187: RX process aborted due to explicit shutdown
[17191466.204000] rtl8187: RX process aborted due to explicit shutdown
[17191466.952000] rtl8187: Card successfully reset
[17191474.120000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17191666.720000] rtl8187: RX process aborted due to explicit shutdown
[17191666.720000] rtl8187: RX process aborted due to explicit shutdown
[17191666.720000] rtl8187: RX process aborted due to explicit shutdown
[17191679.952000] rtl8187: Card successfully reset
[17191687.212000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17191847.120000] rtl8187: RX process aborted due to explicit shutdown
[17191847.120000] rtl8187: RX process aborted due to explicit shutdown
[17191847.120000] rtl8187: RX process aborted due to explicit shutdown
[17191847.920000] rtl8187: Card successfully reset
[17191855.464000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17192297.012000] usb 2-2: new high speed USB device using ehci_hcd and address 3
[17192297.148000] usb 2-2: configuration #1 chosen from 1 choice
[17192297.148000] scsi1 : SCSI emulation for USB Mass Storage devices
[17192297.148000] usb-storage: device found at 3
[17192297.148000] usb-storage: waiting for device to settle before scanning
[17192302.148000] usb-storage: device scan complete
[17192302.148000]   Vendor: Flash/SM  Model: Super Talent 2.0  Rev: 2040
[17192302.148000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17192302.152000] SCSI device sda: 252928 512-byte hdwr sectors (129 MB)
[17192302.156000] sda: Write Protect is off
[17192302.156000] sda: Mode Sense: 43 00 00 00
[17192302.156000] sda: assuming drive cache: write through
[17192302.156000] SCSI device sda: 252928 512-byte hdwr sectors (129 MB)
[17192302.156000] sda: Write Protect is off
[17192302.156000] sda: Mode Sense: 43 00 00 00
[17192302.156000] sda: assuming drive cache: write through
[17192302.156000]  sda: sda1
[17192302.212000] sd 1:0:0:0: Attached scsi removable disk sda
[17192302.212000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17192305.648000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17192425.364000] usb 2-2: USB disconnect, address 3
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000] sda : READ CAPACITY failed.
[17192425.368000] sda : status=0, message=00, host=1, driver=00 
[17192425.368000] sda : sense not available. 
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000] sda: Write Protect is off
[17192425.368000] sda: Mode Sense: 00 00 00 00
[17192425.368000] sda: assuming drive cache: write through
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.368000]  1:0:0:0: rejecting I/O to dead device
[17192425.372000] sda : READ CAPACITY failed.
[17192425.372000] sda : status=0, message=00, host=1, driver=00 
[17192425.372000] sda : sense not available. 
[17192425.372000]  1:0:0:0: rejecting I/O to dead device
[17192425.372000] sda: Write Protect is off
[17192425.372000] sda: Mode Sense: 00 00 00 00
[17192425.372000] sda: assuming drive cache: write through
[17192425.372000]  sda:<3> 1:0:0:0: rejecting I/O to dead device
[17192425.372000] Buffer I/O error on device sda, logical block 0
[17192425.372000]  1:0:0:0: rejecting I/O to dead device
[17192425.372000] Buffer I/O error on device sda, logical block 0
[17192425.372000]  unable to read partition table
[17193050.432000] usb 3-5: USB disconnect, address 2
[17193050.432000] rtl8187: EE:cannot submit RX command. URB_STATUS ffffff94
[17193050.432000] rtl8187: EE:cannot submit RX command. URB_STATUS ffffff94
[17193050.432000] rtl8187: EE:cannot submit RX command. URB_STATUS ffffff94
[17193051.108000] rtl8187: WW:Card reset timeout!
[17193051.316000] rtl8187: wlan driver removed
[17193051.316000] 
[17193095.528000] usb 3-5: new high speed USB device using ehci_hcd and address 3
[17193095.664000] usb 3-5: configuration #1 chosen from 1 choice
[17193095.668000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17193095.872000] rtl8187: Card MAC address is 00:18:4d:02:ea:bd
[17193096.156000] rtl8187: Card reports RF frontend Realtek 8225
[17193096.156000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17193096.156000] rtl8187: WW:use it with care and at your own risk and
[17193096.156000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17193096.196000] rtl8187: This seems a legacy 1st version radio
[17193096.196000] rtl8187: PAPE from CONFIG2: 0
[17193096.196000] rtl8187: Driver probe completed
[17193096.196000] 
[17193099.128000] rtl8187: Card successfully reset
[17193106.252000] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by FrodoB on 2006-11-22
Alternate CD or normal CD install?

---

### Post by phazon. on 2006-11-22
Normal CD - I'm pretty sure anyway, I'll check it

---

### Post by FrodoB on 2006-11-22
What does iwconfig say after you get this dmesg response? Maybe remove and replace or maybe just reboot and see what iwconfig looks like after a reboot.

---

### Post by phazon. on 2006-11-22
iwconfig looks the same as before, rebooting it now, will do a iwconfig as soon as it's up

---

### Post by phazon. on 2006-11-22
OK it's still the same as before - the only difference now is that when I do iwconfig repeatedly it is not shifting off Channel 11 - before it was cycling throught the channels.

Ch11 is the one my router is on. Coincidence?

---

### Post by FrodoB on 2006-11-22
I think it has found it, but why it does not associate is beyond me, I will think on this.

---

### Post by FrodoB on 2006-11-22
You are either close or your device is dead.  Can you try to use the same device on a Windows machine and see if that will clear out the device so it works.  Also, we are out of ideas, so turn off the access point for 5 minutes, restart it and see if that helps. Restart the machines as well.

---

### Post by phazon. on 2006-11-22
Rebooting the access point is a good idea. I'll do that now. The WG111 is new and worked previously in the same machine which was Windows till my HDD died the other day. I can try it in my laptop. But I'll do the router first anyway.

Thanks again.

---

### Post by phazon. on 2006-11-22
One other thing, if I do dmesg now it's got 'Linking with NWIB_WIFI' over and over again. But it also has the 'wlan0: link is not ready' line....

---

### Post by FrodoB on 2006-11-22
Well, maybe you just need to put WEP into both the access point and the interfaces file.  Go to this site and make some keys:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Put the same key into the router and into the record in the interfaces file:

iface wlan0 inet dhcp
wireless-essid Your_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

128bit wep keys are 26 hex characters or 13 ASCII. If you want to use ASCII the record should be:

wireless-key s:XXXXXXXXXXXXX

---

### Post by phazon. on 2006-11-22
OK it's working, although the not how I wanted. Did the above but no change - then found an old Linksys WUSB11 wireless USB card that I forgot about - plugged it in and it worked immediately.

So must be something up with the Netgear, what a pain in the ***.

Any, FrodoB, huge thanks for your help on this this evening (well it's evening for me anyway) and apologies it appears to have been a hopless cause. Really appreciate it.

---

### Post by FrodoB on 2006-11-22
OK, too bad, can you return it? I have seen two or three other folks on this forum and it just worked for them. Really strange.

---

### Post by phazon. on 2006-11-22
Yeah, I'll have to look at returning it. It came in a bundle with the router. Weird that it worked on Windows OK.

Thanks again.

---

### Post by FrodoB on 2006-11-22
One last thing. If the other device uses the same identifier then you will know that you wep key is good etc.  Reboot without the device in the machine, then after it is up insert it and check dmesg and iwconfig once more.

If that does not work, then there is something different about this device.

---

### Post by phazon. on 2006-11-22
By identifier I guess you mean wlan0 - in which case yes. When I plugged in the Linksys, it worked straight away - I didn't change *anything* from the previous setup that had failed with the Netgear.

Cheers.

---

### Post by FrodoB on 2006-11-22
Right, I was hoping that a reboot and inserting the device after the fact might bring it to life.  Mine plugs and plays quite well. I must admit that I normally put it in after a boot has already occurred and it just finds and attached to the access point upon plugin.

---

### Post by FrodoB on 2006-11-22
Also try adding wireless-mode managed to the interfaces entry:

wireless-mode managed


Then try once more.

---

### Post by flapane on 2006-11-23
I too have NOT ASSOCIATED, but the wep key is correct, and a 5$ chinese pcmcia wifi works!!

gipi@gipinet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b/g  ESSID:"3Com"
          Mode:Managed  Channel=2  Access Point: Not-Associated
          Bit Rate=11 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gipi@gipinet:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid 3Com
wireless-key E2F4FFCD21BCF3C1A3F5321B3E

#auto wlan0
#iface wlan0 inet dhcp
#wireless-essid 3Com
#wireless-key E2F4FFCD21BCF3C1A3F5321B3E

iface wlan0 inet dhcp
wireless-essid 3Com
wireless-key E2F4FFCD21BCF3C1A3F5321B3E
auto wlan0
gipi@gipinet:~$ dmesg | grep rtl
[   35.745195] rtl_ieee80211_crypt: registered algorithm 'NULL'
[   35.745200] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[   35.745203] rtl_ieee80211_crypt: registered algorithm 'WEP'
[   35.745205] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[   35.775161] rtl8187: Initializing module
[   35.775163] rtl8187: Wireless extensions version 20
[   35.775166] rtl8187: Initializing proc filesystem
[   35.777020] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[   35.933109] rtl8187: Card MAC address is 00:14:6c:f0:51:3d
[   36.205200] rtl8187: Card reports RF frontend Realtek 8225
[   36.205204] rtl8187: WW:This driver has EXPERIMENTAL support for this 
chipset.
[   36.205207] rtl8187: WW:use it with care and at your own risk and
[   36.205209] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO 
[email]andreamrl@tiscali.it[/email]
[   36.275363] Modules linked in: pata_pcmcia libata scsi_mod joydev r8187 
ieee80211_rtl tsdev snd_seq_dummy snd_seq_oss snd_seq_midi 
snd_seq_midi_event snd_seq usbhid pcmcia nvidia psmouse serio_raw 
snd_via82xx parport_pc parport i2c_viapro pcspkr gameport snd_mpu401_uart 
evdev via_ircc irda snd_via82xx_modem snd_ac97_codec snd_ac97_bus 
snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_page_alloc crc_ccitt 
yenta_socket rsrc_nonstatic i2c_core snd_rawmidi snd_seq_device snd 
soundcore r1000 r8169 pcmcia_core shpchp pci_hotplug ext3 jbd ehci_hcd 
uhci_hcd usbcore ohci1394 ieee1394 ide_generic ide_cd cdrom ide_disk 
via82cxxx generic thermal processor fan vesafb capability commoncap vga16fb 
cfbcopyarea vgastate cfbimgblt cfbfillrect fbcon tileblit font bitblit 
softcursor
[   36.275702]  <6>rtl8187: This seems a new V2 radio
[   36.296484] rtl8187: PAPE from CONFIG2: 0
[   36.296643] rtl8187: Driver probe completed
[   36.296665] usbcore: registered new driver rtl8187
[   36.727434]        <ffffffff8020c2c8>{__delay+8} 
<ffffffff8887acae>{:r8187:rtl8180_reset+142}
[   36.727456]        <ffffffff8887ae0a>{:r8187:rtl8180_adapter_start+26}
[   36.727467]        <ffffffff8887afcb>{:r8187:_rtl8180_up+27} 
<ffffffff8887b8c1>{:r8187:rtl8180_open+49}
[   37.091123] rtl8187: Card successfully reset
[  212.364533] rtl8187: RX process aborted due to explicit shutdown
[  212.364754] rtl8187: RX process aborted due to explicit shutdown
[  212.364976] rtl8187: RX process aborted due to explicit shutdown
[  212.399127] rtl8187: Setting SW wep key
[  213.825844] rtl8187: Card successfully reset
[  213.919226] rtl8187: wlan driver removed
[  214.833882] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[  214.883995] rtl8187: Card MAC address is 00:14:6c:f0:51:3d
[  214.958916] rtl8187: Card reports RF frontend Realtek 8225
[  214.958920] rtl8187: WW:This driver has EXPERIMENTAL support for this 
chipset.
[  214.958922] rtl8187: WW:use it with care and at your own risk and
[  214.958925] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO 
[email]andreamrl@tiscali.it[/email]
[  214.972736] rtl8187: This seems a legacy 1st version radio
[  214.972792] rtl8187: PAPE from CONFIG2: 0
[  214.972854] rtl8187: Driver probe completed
[  215.070688] rtl8187: Setting SW wep key
[  215.377209] rtl8187: Card successfully reset
gipi@gipinet:~$ cat /etc/issue.net
Ubuntu 6.10
gipi@gipinet:~$

---

### Post by FrodoB on 2006-11-23
Well, this is the second one that I have seen on this list that does not want to associate.  If you have a Windows machine that you could try it on and it worked, it could conceivably  reset something and it might start working in Ubuntu as well.  If  it will not work in Windows then it is bad for sure.

I see a lot of these on the refurbished market, maybe there is a reason? I bought mine used and it has just always worked in Ubuntu.

---

### Post by phazon. on 2006-11-23
> **FrodoB said:**
> Also try adding wireless-mode managed to the interfaces entry:

wireless-mode managed


Then try once more.

Hi FrodoB, the above made no difference.

flapane, no help to you but at least it's not just me now ](*,)
:)

---

### Post by FrodoB on 2006-11-23
Well, maybe someone will come along and tell us what the real root cause is here. Very strange indeed.

---

### Post by flapane on 2006-11-23
> **FrodoB said:**
> Well, this is the second one that I have seen on this list that does not want to associate.  If you have a Windows machine that you could try it on and it worked, it could conceivably  reset something and it might start working in Ubuntu as well.  If  it will not work in Windows then it is bad for sure.

I see a lot of these on the refurbished market, maybe there is a reason? I bought mine used and it has just always worked in Ubuntu.

in winxp is ok and it's brand new.
I've just wrote to the developer

---

### Post by FrodoB on 2006-11-23
I will be really interested to hear what the developer might have to say about this situation.

---

### Post by encho on 2006-11-24
Some time ago I had same problem with my wireless card. Not associating with access point and driving me mad. I remember that I had to remove network-manager and installed wifi-radar or other way around and it worked. Check for those.

---

### Post by flapane on 2006-11-25
up

---

### Post by FrodoB on 2006-11-25
flapane;

Is up a bump or you got it up?

---

### Post by flapane on 2006-11-25
ehm yes sorry, "up" is the italian method for "bump"

---

### Post by FrodoB on 2006-11-25
What do you see when you run:

sudo iwlist wlan0 scanning

---

### Post by FrodoB on 2006-11-25
Here is my dmesg output:

```

[17311920.472000] usb 3-4.4: new high speed USB device using ehci_hcd and address 6
[17311920.568000] usb 3-4.4: configuration #1 chosen from 1 choice
[17311920.704000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17311920.704000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17311920.704000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17311920.704000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17311920.724000] 
[17311920.724000] Linux kernel driver for RTL8187 based WLAN cards
[17311920.724000] Copyright (c) 2004-2005, Andrea Merello
[17311920.724000] rtl8187: Initializing module
[17311920.724000] rtl8187: Wireless extensions version 20
[17311920.724000] rtl8187: Initializing proc filesystem
[17311920.724000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17311920.840000] rtl8187: Card MAC address is 00:14:6c:66:49:47
[17311921.008000] rtl8187: Card reports RF frontend Realtek 8225
[17311921.008000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17311921.008000] rtl8187: WW:use it with care and at your own risk and
[17311921.008000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO andreamrl@tiscali.it
[17311921.040000] rtl8187: This seems a legacy 1st version radio
[17311921.040000] rtl8187: PAPE from CONFIG2: 0
[17311921.044000] rtl8187: Driver probe completed
[17311921.044000] 
[17311921.044000] usbcore: registered new driver rtl8187
[17312101.504000] rtl8187: Setting SW wep key
[17312102.192000] rtl8187: Card successfully reset
[17312108.072000] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[17312129.616000] Linking with My_ESSID
[17312129.672000] Associated successfully
[17312129.672000] Using G rates
[17312129.728000] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[17312139.916000] wlan1: no IPv6 routers present

```

---

### Post by blulam on 2006-11-29
ok so just to let you guy know im number 3 im joining the team to solve this issue aswell becasue i have the same problem TA DA i have a wg111v2 and i HAVE to get it to work because it will be the only one that will work for my purpose(if you pop open the little ba$tard you can connect an external antenna if your good with souder)

things ive tried are using ndiswrapper with xp drivers and with 2000 drivers none worked,
tried fresh install
set channel and mac ids manualy
ect ect

i like the idea of uninstalling the wifi radar and the network manager too im going to try this tomorrow because my eyes are actually blood shot over this issue and i got to be up at 5 (im a network admin ha ha and i cant figure this out ha ha) 

LETS KEEP THIS TREAD ALIVE 
it is the only thread ive found in days of looking thats of any help!!

---

### Post by blulam on 2006-11-29
forgive my short methods of asking before searching ANYWHERE but how do you uninstall network manager and wifi radar is there a remove programs... oh crap i found it never mind but i have to keep this post cause i need the subscription

---

### Post by FrodoB on 2006-11-29
blulam;

Do a fresh install of Edgy or Dapper and then after booting in insert the device and provide the outputs of the tail of dmesg the outputs of lsusb and  iwconfig.  

It will either work or not, at least that is what we have seen so far. We are about 50% successful with these devices so far.

---

### Post by blulam on 2006-11-29
yeah but if ive done that once id rather not do it again, i am however expecting an 8gb cf and botable cf to ide adapter in the mail soon so when that gets here i will have to fresh install will keep informed and ill post those outputs as soon as i get off work

---

### Post by flapane on 2006-11-29
> **FrodoB said:**
> What do you see when you run:

sudo iwlist wlan0 scanning

gipi@gipinet:~$ sudo iwlist wlan0 scanning
wlan0     No scan results
gipi@gipinet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0_ifrename  no wireless extensions.

ath0      IEEE 802.11g  ESSID:"3Com"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0D:54:9B:19:34
          Bit Rate:11 Mb/s   Tx-Power:19 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=20/94  Signal level=-75 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

wlan0     802.11b/g  ESSID:"3Com"
          Mode:Managed  Channel=1  Access Point: Not-Associated
          Bit Rate=11 Mb/s   Sensitivity=4/6
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

gipi@gipinet:~$      

I'am with ath0 now (pcmcia), no way with usb wifi

---

### Post by cajsaj on 2006-12-05
It's not much help, but I've spent days trying to get my new WG111 v2 device to work with no luck. I've reinstalled Edgy a couple of times, used the native driver and tried ndiswrapper. Nothing has worked!

The most success I got was when the light came on:D 

I'm taking back to the shop today, and I've ordered a wireless bridge instead. I'd really like to find out the root cause though.

---

### Post by FrodoB on 2006-12-05
I would really like to know the root cause as well. There seem to be somewhere between %25 to %50 of these devices that just cannot be made to work and the reason is not obvious.

---

### Post by flapane on 2006-12-05
> **FrodoB said:**
> I would really like to know the root cause as well. There seem to be somewhere between %25 to %50 of these devices that just cannot be made to work and the reason is not obvious.

damn it, in this way I can't "convert" my father to ubuntu, because it ABSOLUTELY NEEDS wireless, and this netgear is brand new. He reverted to windows waiting for something...

---

### Post by FrodoB on 2006-12-05
At least one person on this forum has had luck with using ndiswrapper on a WG111v2 that would not associate with the native driver.

---

### Post by drwx on 2006-12-05
> **FrodoB said:**
> At least one person on this forum has had luck with using ndiswrapper on a WG111v2 that would not associate with the native driver.

Yes..see page 3 of my post: [http://ubuntuforums.org/showthread.php?t=311646&highlight=edgy+%26amp%3B+wg111v2]("http://ubuntuforums.org/showthread.php?t=311646&highlight=edgy+%26amp%3B+wg111v2")

---

### Post by flapane on 2006-12-10
I decided downloading the realtek xp64bit driver, which xp x64 users install for wg111 v2.0 x64-8187(1234).zip and installed wih ndiswrapper. The situation seems to be better, because now it find my AP with scanning, while it didn't find it with the kernel driver:
gipi@gipinet:~/Desktop/x64-8187(1234)/XP64$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:0D:54:9B:19:34
                    ESSID:"3Com"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11
                    Quality:13  Signal level:0  Noise level:20
                    Extra: Last beacon: 3ms ago

gipi@gipinet:~/Desktop/x64-8187(1234)/XP64$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"3Com"
          Mode:Managed  Channel=1  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

gipi@gipinet:~/Desktop/x64-8187(1234)/XP64$

anyway it's still NOT ASSOCIATED!!

---

### Post by simyn on 2006-12-18
Here is how I got the WG111v2 to work (on Breezy):

I am not sure if all of this is necessary (or if it will work for anyone else) because I am a noob, however this is the process I went through:


I used the driver from this site (after trying all of the extracted drivers from the CD and having no success with those):

[http://www.megaupload.com/it/?d=MK4LZDM0](http://www.megaupload.com/it/?d=MK4LZDM0)


In Synaptic Package Manager, install Linux Headers (if not already installed)

Install libusb++-dev(2:0.1.10a-17ubuntu1)

[http://packages.ubuntu.com/breezy/libdevel/libusb++-dev](http://packages.ubuntu.com/breezy/libdevel/libusb++-dev)


Install gcc3.4 following this guide

[http://www.ubuntuforums.org/showthread.php?t=79896](http://www.ubuntuforums.org/showthread.php?t=79896)


Uninstall ndiswrapper and install ndiswrapper 1.6

Blacklist the following by creating a file called 'blackist' in the /etc/modprobe.d directory:

r2400
r2500
r8187
madwifi
ath_pci
ath_rate_sample
wlan
wlan.acl
wlan.ccmp
wlan.tkip
wlan.wep
wlan.xauth
ath_hal
ath_hal.mod
hal.o
ah.osdep.o
bcm
islsm_pci
islsm
islsm_usb
prism2_usb
acx
bcm43xx
p80211



Install wifi-radar (this did not seem to do anything so I am not sure if it is needed).

Install driver.

load driver BEFORE inserting the adapter by typing: sudo modprobe ndiswrapper



Insert adapter.  The light should come on.


type iwconfig and you should see something for wlan0


Type: > sudo iwconfig wlan0 channel <YOUR_CHANNEL>



Type: > iwlist scan


Type: > sudo iwconfig wlan0 ap <YOUR_AP>


Type: > sudo iwconfig wlan0 essid <'YOUR_ESSID'>  (use single quotes around it)



Type: > sudo dhclient wlan0



Check a website in your browser to see if you are online.

---

### Post by aMUSEd on 2007-01-02
Plz tell me how i can set upp my rtl 8187 wlan in ubuntu 6.10

Thx in advance....

---

### Post by aMUSEd on 2007-01-02
my board is an asus p5b deluxe wifi...with this onboard usb rtl 8187...

in opensuse 10.2 it worked with the realtek driver....in ubuntu i tried the built in one...

Thx

---

### Post by devoncatt on 2007-01-10
I have an ASUS P5W board with built in WIFI. It works fine in XP, Windows VISTA  RTM but not at all in Edgy or Suse 10.2 with drivers installed. Using Network Manager 

This is not a PCI it is built in - it seems to register as a USB wireless device. It sees the wireless aceess point but times out while attempting to get an address. In Mempis or Mint Linux ( both Ubuntu based) the most I can get is a 169. (ARP?)  address and 30% signal strength- and definitely not connected.

Any suggestions? Tried with or without network manager, with or without wifi-radar. With RTL 8187 Linux driver from realtek.

Really scratching my head over this one
Devoncatt
Output of various commands below




chelle@tazx2:~$ dmesg | grep rtl
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'NULL'
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'TKIP'
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'WEP'
[17179595.188000] rtl_ieee80211_crypt: registered algorithm 'CCMP'
[17179595.460000] rtl8187: Initializing module
[17179595.460000] rtl8187: Wireless extensions version 20
[17179595.460000] rtl8187: Initializing proc filesystem
[17179595.460000] rtl8187: Reported EEPROM chip is a 93c46 (1Kbit)
[17179595.572000] rtl8187: Card MAC address is 00:15:af:07:9c:11
[17179595.748000] rtl8187: Card reports RF frontend Realtek 8225
[17179595.748000] rtl8187: WW:This driver has EXPERIMENTAL support for this chipset.
[17179595.748000] rtl8187: WW:use it with care and at your own risk and
[17179595.748000] rtl8187: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO [email]andreamrl@tiscali.it[/email]
[17179595.792000] rtl8187: This seems a new V2 radio
[17179595.792000] rtl8187: PAPE from CONFIG2: 0
[17179595.792000] rtl8187: Driver probe completed
[17179595.792000] usbcore: registered new driver rtl8187
[17179595.896000] rtl8187: Setting SW wep key
[17179596.576000] rtl8187: Card successfully reset
chelle@tazx2:~$ sudo iwlist wlan0 scanning

wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:12:1F:E1
                    ESSID:"dcatt"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:15  Signal level:0  Noise level:113
                    Extra: Last beacon: 12ms ago

chelle@tazx2:~$ lsusb
Bus 007 Device 005: ID 046d:0a04 Logitech, Inc.
Bus 007 Device 006: ID 0bda:8187 Realtek Semiconductor Corp.
Bus 007 Device 004: ID 05e3:0606 Genesys Logic, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 008 Device 002: ID 2040:9950 Hauppauge
Bus 008 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c30a Logitech, Inc.
Bus 002 Device 004: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000

lle@tazx2:~$ lspci
00:00.0 Host bridge: Intel Corporation 975X Express Memory Controller Hub (rev c0)
00:01.0 PCI bridge: Intel Corporation 975X Express PCI Express Root Port (rev c0)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c6
05:00.1 Display controller: ATI Technologies Inc Unknown device 71e6
chelle@tazx2:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g link..  ESSID:"dcatt"
          Mode:Managed  Channel=7  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by flapane on 2007-01-10
naw I also wrote to andreamrl a lot of times but he never answered, I reverted my father's box to xp, where his r8187 works WONDERFULLY

---

### Post by aMUSEd on 2007-01-10
i tried with the native realtek linux driver and it didn't work out....in the scan i found the ap but it never associated with.

The i installed ndiswrapper and got it working with old (not the most recent) realtek win98 drivers.

kind reagrds

---

### Post by phossal on 2007-01-10
I came to this thread many times while trying to figure out my wg111v2. In the end, a few of us ended up with [this tutorial]("http://ubuntuforums.org/showthread.php?t=329299") that seems to get most people up and running. Note in the tutorial that some of the devices which are labeled as wg111v2 are actually wg111v1 chips.

---

### Post by boudders on 2007-02-04
Great guide, but I am stuck in a pickle.

I can scan using:
iwlist wlan0 scan

And I can see the access point and but I cannot manage my wireless connection in Netowork Manager. 

When I run:
sudo gedit etc/network/interfaces 

I see that my wlan0 is associated with AP but they can't talk to eachother! 

Any ideas?

EDIT:

I also get this when I type in:
ndiswrapper -m

module configuration contains directive install pci:v000014E4d00004301sv00001737sd00004301bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004301sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv000014E4sd00000417bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv00001737sd00004320bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v000014E4d00004320sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4220d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install usb:v0846p4240d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
;you should delete thatmodprobe config already contains alias directive

---

### Post by phossal on 2007-02-04
Are you connected via cat-5? Can you post the output from commands like:
```
iwconfig
```

[EDIT] Did you install ndiswrapper?

---

### Post by boudders on 2007-02-04
Results from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2346 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by phossal on 2007-02-04
Did you install ndiswrapper?

---

### Post by boudders on 2007-02-06
Yea I have the latest ndiswrapper installed -1.8

---

### Post by phossal on 2007-02-06
What's the output to *ndiswrapper -l*?

---

### Post by boudders on 2007-02-13
ndiswrapper -l outputs:

netwg111 driver installed, hardware present

---

### Post by phossal on 2007-02-13
If your hardware is properly detected by ndiswrapper, perhaps the default drivers have not been blacklisted, or are still being loaded anyway. My signature contains a tutorial on setting up this device, and I recommend you review it. Using ndiswrapper and removing the rl*818* drivers from the machine seems to work in the majority of cases.

---

