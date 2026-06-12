---
title: "Acer Aspire 5602WLMi ipw3945"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by nibbles on 2007-08-04
Hi,

I've got a little problem with my acer aspire 5602, everything works, except for the wireless. The card is detected, but it doesn't work.

These are my data:

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [ATI Mobility Radeon X1300]
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:09.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

dmesg | grep_ip:
```
[   19.396958] Booting processor 1/1 eip 3000
[    1.045876] io scheduler anticipatory registered
[    1.427907] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.088000] 8139cp 0000:0a:00.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.196000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   16.716000] agpgart: Detected an Intel 945GM Chipset.
[   17.488000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.488000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.488000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.372000] ipw3945: Radio Frequency Kill Switch is On:
[  271.564000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[  897.900000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[ 1141.864000] ipw3945: Radio Frequency Kill Switch is On:
[ 1145.132000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[ 1147.448000] ipw3945: Radio Frequency Kill Switch is On:
[ 1152.864000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

```

I tried with aceracpi, but i get this output:

dmesg | grep acer_acpi:
```
[ 1198.600000] acer_acpi: Acer Laptop ACPI Extras version 0.7
[ 1198.600000] acer_acpi: Detected Acer WMID interface
[ 1198.600000] acer_acpi: Driver registered

```

As you can see it says the kill switch is on.

When i use the physical kill switch, it makes eth1 appear/disappear.

I would really appreciate any help on this one.

Thanks

---

### Post by noob12 on 2007-08-04
Check the BIOS settings too.  Make sure wireless is enabled by default at start.


Can you also post the output of these
```

lshw -C network

ifconfig -a

iwlist scan

cat /etc/network/interfaces

cat /sys/class/net/*/driver/rf_kill

```

---

### Post by nibbles on 2007-08-04
Here's the output of the rest of the commands:

lshw -C network
```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:6e:97:26
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 link=no multicast=yes wireless=unassociated
       resources: iomemory:54000000-54000fff irq:16
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0a:00.0
       logical name: eth0
       version: 10
       serial: 00:16:36:43:1f:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:3000-30ff iomemory:c8300000-c83000ff irq:17

```

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:43:1F:31  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe43:1f31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2820600 (2.6 MiB)  TX bytes:854939 (834.9 KiB)
          Interrupt:17 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:6E:97:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x2000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3418 (3.3 KiB)  TX bytes:3418 (3.3 KiB)


```

iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:C1:0B:4C:52
                    ESSID:"USR5461"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=83/100  Signal level=-51 dBm  Noise level=-51 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 64ms ago


```

cat /etc/network/interfaces
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp








iface eth1 inet dhcp
wireless-essid USR5461
wireless-key s:kakemansstraat













auto eth0



```

cat /sys/class/net/*/driver/rf_kill
```
cat: /sys/class/net/*/driver/rf_kill: No such file or directory

```

The last one seems a little weird, i typed it in right, there's no folder driver for eth1.

I tried to look in the bios for a wireless setting, but the only one i found is one for networking, which is enabled. The bios is quite limited though, not a lot of settings.

Hope this 'll help.

---

### Post by noob12 on 2007-08-04
Looks like your wireless is working.  We need to set you up to use WPA to talk to your access point.

For starters,

```

aptitude install wpasupplicant

```


Also let me know whether you are running Ubuntu or Kubuntu?

And
```

aptitude show network-manager network-manager-gnome knetworkmanager  | grep State

```

---

### Post by nibbles on 2007-08-04
Ok that explains a lot :) thanks

so i downloaded wpasupplicant and the other command shows i've got network-manager and network-manager-gnome, which I downloaded (i don't know if it comes standard). I'm running ubuntu.

---

### Post by noob12 on 2007-08-04
Great!

Is the nm-applet running?  

```

ps -ef | grep nm-applet | grep -v grep

```

If this shows "nm-applet --sm-disable" you're already fine; you should see a little dual-computer icon in the top right corner. 

Otherwise (if you don't see it shown in the previous listing) please run it by typing ALT+F2 and
in the dialog that comes up type
```

nm-applet --sm-disable

```
and hit the Run button.

---

### Post by nibbles on 2007-08-04
Yeah its up already

---

### Post by noob12 on 2007-08-04
OK.  Please do the following

Left click the Network Manager (NM) icon (that little dual computer icon in the panel).  Select Manual Configuration.  Type your password to allow managing this.  Find eth1.  Select it.  Click Properties.  Click enable roaming mode. OK. Close.

After you have done this **cat /etc/network/interfaces**.  Post it.

Now right-click on the the NM icon, and Enable Wireless.  The check box should come on.
Now when you left click on the NM again, you should see a list of wireless networks.  Select yours.
You should get a prompt for entering WPA information.  Enter your WPA key.  It should connect.

If you see something about a keyring, the keyring password is not your WPA key.  That is a password used to protect your various network keys.  If you are setting it for the first time, I recommend you use your login password.

---

### Post by nibbles on 2007-08-04
Ok here is the output:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp








auto eth0

```

I did as you told me, but it won't connect: i can type in my password, but the it stays at 0, although every 10 or 20 seconds the bars of the icon become blue and it says 81 percent.

---

### Post by noob12 on 2007-08-04
OK.  We should try to separate the WPA issues from basic wireless functionality.

Tthen we can come back and finish the WPA setup.

If you control the router, can you temporarily disable WPA and leave it unsecured for this test?

---

### Post by nibbles on 2007-08-04
Hey,

I've turned off the WPA and I can log on without a problem :) Thanks

So what do you suggest for the WPA

---

### Post by noob12 on 2007-08-04
OK.  Before we reenable the WPA.

Can you just do some basic internet browsing and check that things appear to be working.

Also, please show me the output of **iwconfig** and **ifconfig -a**

When you're convinced it is working without WPA, you can reenable WPA and we'll walk through that more carefully.

---

### Post by nibbles on 2007-08-04
It's definitely working, I'm sending this message through my wireless connection.

Here's the iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"USR5461"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:C1:0B:4C:52   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-44 dBm  Noise level=-45 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:646   Missed beacon:0
```

and the ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:43:1F:31  
          inet6 addr: fe80::216:36ff:fe43:1f31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22440157 (21.4 MiB)  TX bytes:2946778 (2.8 MiB)
          Interrupt:17 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:13:02:6E:97:26  
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe6e:9726/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20575 errors:57 dropped:708 overruns:0 frame:0
          TX packets:12514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26490715 (25.2 MiB)  TX bytes:1315223 (1.2 MiB)
          Interrupt:16 Base address:0x2000 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11503 (11.2 KiB)  TX bytes:11503 (11.2 KiB)

```

thx

---

### Post by nibbles on 2007-08-04
Hey, it's ok, I got the WPA working this time, it was a problem with case-sensitivity.

Anyway thanks a lot, you really helped me tremendously, I' very happy with my wireless :)

---

### Post by noob12 on 2007-08-05
Great!  See ya

---

