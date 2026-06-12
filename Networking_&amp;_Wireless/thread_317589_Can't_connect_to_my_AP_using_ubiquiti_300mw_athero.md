---
title: "Can't connect to my AP using ubiquiti 300mw atheros card"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by tee2 on 2006-12-12
After I put in the Ubiquiti 300mW card two new devices appeared, ath0 and wifi0. I've tried connecting with both but neither works. Here is my ifconfig output 
```
tee@tee-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:15:6D:53:6F:20  
          inet6 addr: fe80::215:6dff:fe53:6f20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:14:22:E5:C2:F6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fee5:c2f6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:570296 (556.9 KiB)  TX bytes:123127 (120.2 KiB)
          Interrupt:209 

eth1      Link encap:Ethernet  HWaddr 00:13:CE:E7:9E:A5  
          inet6 addr: fe80::213:ceff:fee7:9ea5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2443 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:201 Base address:0xc000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-15-6D-53-6F-20-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3438 errors:0 dropped:0 overruns:0 frame:326
          TX packets:810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:408481 (398.9 KiB)  TX bytes:36064 (35.2 KiB)
          Interrupt:177 Memory:e0ba0000-e0bb0000 

```

eth0 is a wired connection and eth1 is my laptop's built in wirelss.

I did dmesg | tail and got this:
```
tee@tee-laptop:~$ dmesg | tail
[17179610.272000] lo: Disabled Privacy Extensions
[17179610.272000] IPv6 over IPv4 tunneling driver
[17179620.792000] ath0: no IPv6 routers present
[17179620.836000] eth0: no IPv6 routers present
[17179621.132000] eth1: no IPv6 routers present
[17179624.732000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179857.500000] ath0: no IPv6 routers present
[17180337.968000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[17180348.540000] ath0: no IPv6 routers present
[17180495.128000] ADDRCONF(NETDEV_UP): ath0: link is not ready

```
Does this mean that my card is only looking for a ipv6 connection?

---

### Post by FrodoB on 2006-12-12
If this is a PC CARD (PCMCIA) then reboot with the card out and then after logging in insert the card and run dmesg and give use the whole ath0 initialization.

---

### Post by tee2 on 2006-12-12
```
tee@tee-laptop:~$ dmesg | tail
[17180470.656000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17180470.656000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17180470.656000] wifi0: mac 5.9 phy 4.3 radio 3.6
[17180470.656000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17180470.656000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17180470.656000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17180470.656000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17180470.656000] wifi0: Use hw queue 8 for CAB traffic
[17180470.656000] wifi0: Use hw queue 9 for beacons
[17180470.660000] wifi0: Atheros 5212: mem=0x32000000, irq=177

```
edit: that might not be the whole ting, how would i show that?

---

### Post by FrodoB on 2006-12-12
We need the part that shows ath0 starting up.

Also show the output of iwconfig

---

### Post by tturrisi on 2006-12-12
First off, how have you tried to connect?
Administration > Networking ?  No encryption or WEP? WPA?
Show the results of:
~# iwlist ath0 scan

FYI, the wifi0 is a virtual device created by madwifi driver.

---

### Post by tee2 on 2006-12-12
I'm trying to connect using wpa, using the Network Monitor gnome deskbar widget.

```
tee@tee-laptop:~$ iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:16:B6:A8:83:F2
                    ESSID:"linksys_SES_38666"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/94  Signal level=-93 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  


```

Here's the full dmesg

```
[17180470.032000] pccard: CardBus card inserted into slot 0
[17180470.140000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17180470.188000] wlan: 0.8.4.2 (0.9.2)
[17180470.192000] ath_rate_sample: 1.2 (0.9.2)
[17180470.196000] ath_pci: 0.9.4.5 (0.9.2)
[17180470.196000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[17180470.196000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 19 (level, low) -> IRQ 177
[17180470.656000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17180470.656000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17180470.656000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17180470.656000] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17180470.656000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17180470.656000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17180470.656000] wifi0: mac 5.9 phy 4.3 radio 3.6
[17180470.656000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17180470.656000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17180470.656000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17180470.656000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17180470.656000] wifi0: Use hw queue 8 for CAB traffic
[17180470.656000] wifi0: Use hw queue 9 for beacons
[17180470.660000] wifi0: Atheros 5212: mem=0x32000000, irq=177
[17180480.836000] ath0: no IPv6 routers present

```

---

### Post by FrodoB on 2006-12-12
You probably want to debug with encryption off.

The setup menu is at:

System -> Administration ->Networking

This is fine for WEP and no WEP. Just don't enter a key for non-wep

Everything ends up in a file: /etc/network/interfaces

to edit this file use:

sudo gedit /etc/network/interfaces

Here is how to add WPA-PSK after you get it going:

Using WPA-PSK on Ubuntu 6.10 Edgy Eft:

1) Install wpasupplicant:

$ sudo apt-get update

$ sudo apt-get install wpasupplicant


2) Create a /etc/wpa_supplicant.conf file that contains the following: (make sure that your psk is the same as is in your access point router.)

===================== cut ==========================================================
ctrl_interface=/var/run/wpa_supplicant

ap_scan=2  # 1 = broadcast SSID and 2 = hidden SSID

network={
       ssid="Your_Essid_Name"
       key_mgmt=WPA-PSK
       proto=WPA
       pairwise=TKIP
       group=TKIP       
       psk="vjGRNMaOrREWXAVd1lnI2K2JN203K93TIwF55z99FF5OwkSM5c7i0BnVu7mqiDL"
}

===================== cut ==========================================================

You can make the WPA-PSK passphrases at Gibson Research's Perfect Passwords - GRC's Ultra High Security Password Generator:

[https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)

You must use the same passphrase in your Access Point Router for this to work. Replace my example with your own.

3) Edit the /etc/network/interfaces file and add a record for your wireless device:

$ sudo gedit /etc/network/interfaces

Add a record similar to this one, replacing ath0 with the actual name of your interface.

===================== cut ==========================================================
auto ath0
iface ath0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iath0 -c/etc/wpa_supplicant.conf
wpa-ssid Your_SSID_Name
post-down killall -q wpa_supplicant

===================== cut ==========================================================

Note that -Dwext is the driver that your device is using, please refer to the wpasupplicant 
documentation for additional device driver information. The wext driver is good for
ndiswrapper and the Atheros devices at least.

Note that you need to change the interface, -i, to your wireless device name such as ath0 or wlan0, etc.

4) Reboot your system or use the following command:

sudo /etc/init.d/dbus restart

A complete system reboot can be helpful, so I recommend that.

---

### Post by tturrisi on 2006-12-13
there you go, follow the advice above!

Pls do me a favor.  Once connected, take a walk down the street & see what kind of range that Ubiquiti card gets.  I have several cards & was thinking of getting that 300mw card, but I need to know how it performs distance-wise.
tia

---

### Post by FrodoB on 2006-12-13
Yes, give a report, a lot of folks are interested in this device!

---

### Post by tee2 on 2006-12-13
Sure I'll gladly give a report when I get it working. It still isn't working though, but found out that an external antenna is required! I didn't know that because it can detect my AP. Can anyone recommend a good antenna? Preferably a magnetic mount with >=7 dBi gain.

---

### Post by FrodoB on 2006-12-13
I am sure you know this already, but make sure that it has the right connectors on it, there are a lot of different ones out there.  If the card supplier is no help, I can recommend Netgate:

[http://www.netgate.com/](http://www.netgate.com/)

And if you know what connector you need you can probably get a good deal by doing a search on Google or going to Ebay.

---

### Post by tturrisi on 2006-12-13
Get it from this guy, I bought stuff there & prices was right, shipping fast and he even responds to email:
[http://www.data-alliance.net/servlet/the-50/Ubiquiti-SRC-300mW-802.11G-fdsh-B-fdsh-A/Detail](http://www.data-alliance.net/servlet/the-50/Ubiquiti-SRC-300mW-802.11G-fdsh-B-fdsh-A/Detail)
or here:
[http://www.wlanparts.com/c=48bOUoVOENUX8NltLjQGZFNUw/category/antennas/](http://www.wlanparts.com/c=48bOUoVOENUX8NltLjQGZFNUw/category/antennas/)

---

