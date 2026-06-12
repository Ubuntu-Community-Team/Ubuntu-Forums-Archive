---
title: "Atheros AR2413/2414 / lubuntu 13.04 / Acer Aspire 5040"
date: 2013-10-27
forum: Networking &amp; Wireless
---

### Post by henrik2 on 2013-10-27
Houston, we have a problem.

After a clean install (no dual boot) the wireless switch do not respond in any way. Wireless is greyed out and stated as 'Disabled'. Rfkill list shows everything to be fine, until i disable & enable wifi in Network manager, after it shows hardblock to be on. There are no wireless options in the bios.

Laptop:
Acer Aspire 5040

Version:
```
Description:    Ubuntu 13.04
```

Kernel:
```
3.8.0-32-generic i686
```

Wireless chip:
```
06:05.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
```

iwconfig:
```
wlan0     IEEE 802.11bg  ESSID:off/any            Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

lsmod | grep ath (there are some acer_wmi's as well, but blacklisting acer_wmi did not help):
```
ath5k                 134997  0 ath                    19187  1 ath5k
mac80211              526519  1 ath5k
cfg80211              436243  3 ath,ath5k,mac80211

```

Kernel boot messages:
```
[   12.233304] ath5k 0000:06:05.0: registered as 'phy0'[   13.228138] ath: EEPROM regdomain: 0x63
[   13.228146] ath: EEPROM indicates we should expect a direct regpair map
[   13.228151] ath: Country alpha2 being used: 00
[   13.228153] ath: Regpair used: 0x63
[   13.481160] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)

```

lshw:
```
*-network:0             
       description: Wireless interface
       product: AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg]
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:52:fc:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.8.0-32-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:9 memory:c0200000-c020ffff
  *-network:1
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:45:38:88
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.101 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:a000(size=256) memory:c0210000-c02100ff memory:44000000-4401ffff

```

Scan:
```
wlan0     No scan results
```

Rfkill (before disable & enable):
```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: no
```

After:
```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: yes
```

(Forgot to mention that typing rfkill unlock all or sudo rfkill unblock wifi did not help either)

Thank you for your time!

---

### Post by henrik2 on 2013-10-28
Anyone? Even a slightest clue?

Possible fixes i still haven't tried are installing lubuntu on outern partition without having my hdd attached (would install without the encryptions, but ins't that what nohwcrypt=1 is supposed to do? [btw tried that as well, and didn't work out]) and that wifi would get some life after hibernate & wake up? from which it never does and have to reboot it manually. Most of the threads are 4-5 years old, thus why i'm here.

Henrik

---

### Post by henrik2 on 2013-10-30
Hellooooo again!

Updated lubuntu to 13.10 and ran Varunendra's wireless script located here: [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385).

```


*************** info trace ***************


***** uname -a *****


Linux <name of the computer removed> 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 athlon i686 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


06:05.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k
--
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:1079]
    Kernel driver in use: r8169


***** lsusb *****


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


***** PCMCIA Card Info *****




***** iwconfig *****


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes


***** lsmod *****


ath5k                 134963  0 
ath                    19187  1 ath5k
mac80211              513247  1 ath5k
cfg80211              401436  3 ath,ath5k,mac80211


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254


    DNS:             192.168.0.254




- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****




***** resolv.conf *****


nameserver 127.0.1.1
search home.gateway


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     B7A923930DCF3B82CF57D26
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)


filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 




***** udev rules *****


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:14.4/0000:06:07.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


***** dmesg *****


[   14.447721] ath5k 0000:06:05.0: registered as 'phy0'
[   16.402501] ath: EEPROM regdomain: 0x63
[   16.402506] ath: EEPROM indicates we should expect a direct regpair map
[   16.402511] ath: Country alpha2 being used: 00
[   16.402513] ath: Regpair used: 0x63
[   16.614137] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   25.151707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.152530] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.670566] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


****************** done ******************



```

What caught my eye is that this time wlan0 is not getting any power and the power management is off. 
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
 Also i would somehow remember from some other thread that NetworkManagers ```
[ifupdown] managed=false
``` should be true?

Wifi button on front still doesn't respond (no surprise with no power) and the hardblock is still on (no surprise when i can't press the button responsively).

Any help appreciated ;)

---

### Post by henrik2 on 2013-11-05
Update:

Heeey henrik here bringing another monologue to this pesky problem! Now i have re-installed Windows Xp and Lubuntu 13.10 and tried enabling wireless in windows -> reboot to lubuntu, without progress! yeey! I did notice though that even Win Xp required Atheros Utility Client to be installed before working (yes i got it working in windows), or at least seemed like so. But nonetheless do they have a unix version? No! splendid!

Another "find" is a thread from june 2011 to february 2012: [http://ubuntuforums.org/showthread.php?t=1776004&page=3](http://ubuntuforums.org/showthread.php?t=1776004&page=3)     (Starting from page 3 because relevant problem to user "Djesurun1")

Where chili555 noticed strange behaviour: [http://ubuntuforums.org/showthread.php?t=1776004&page=3&p=11704582#post11704582](http://ubuntuforums.org/showthread.php?t=1776004&page=3&p=11704582#post11704582)


My code:
```
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/ieee80211/phy0/[COLOR=#ff0000]rfkill0 disappeared[/COLOR]
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <info> (wlan0): cleaning up...
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <warn> (3) failed to find interface name for index
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: (nm-system.c:766):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <error> [1383670168.95139] [nm-system.c:768] nm_system_iface_get_flags(): (unknown): failed to get interface link object
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/accept_ra': (2) No such file or directory
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]: <warn> sysctl: failed to open '/proc/sys/net/ipv6/conf/wlan0/use_tempaddr': (2) No such file or directory
Nov  5 18:49:28 Aspire-5040 NetworkManager[680]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/net/wlan0, iface: wlan0)
Nov  5 18:49:44 Aspire-5040 NetworkManager[680]: <info> [COLOR=#ff0000]rfkill1: found[/COLOR] [COLOR=#ff0000]WiFi radio killswitch [/COLOR](at /sys/devices/pci0000:00/0000:00:14.4/0000:06:05.0/ieee80211/phy1/rfkill1) (driver ath5k)


```

Following chili555's guidance:

```
hg@Aspire-5040:~$ sudo cat /var/log/dmesg.0 | grep -i err
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.104093] ACPI: Using IOAPIC for interrupt routing
[    0.133747] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.133810] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.133873] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.133936] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.133998] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.134060] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.134121] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.134184] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   14.101927] yenta_cardbus 0000:06:06.0: Using CSCINT to route CSC interrupts to PCI
[   14.101930] yenta_cardbus 0000:06:06.0: Routing CardBus interrupts to PCI
[   14.269266] SKU: override=0x1
[   14.345245] [drm:radeon_get_legacy_connector_info_from_bios] *ERROR* Unknown connector type: 8
[   14.773898] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro


```

But as in countless other threads, Djesurun1 bought another wireless network card and the problem just vanished for him.

Well, back to investigating again. Cheers

---

### Post by varunendra on 2013-11-06
> **henrik2 said:**
> Houston, we have a problem.
ROFL !! :lolflag:

> **henrik2 said:**
> Updated lubuntu to 13.10 and ran Varunendra's wireless script located here: [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385).
Erm... not 'Varunendra's' script actually <sigh !>, as I mentioned in the very first line in that post
> **varunendra said:**
> .. please download and run [wireless_script]("http://dl.dropbox.com/u/57264241/wireless_script") (developed by Wild Man & Krytarik, helped by anewguy, chili555, llua. I'm only using it :P).
But thanks for the free credits ! :P

Now, choosing to be a bit ignorant for a while, how about testing/confirming some old fixes?

The first one for acer models is to blacklist the "acer-wmi" driver when it becomes a culprit instead of a helper -
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and confirm it is not loaded -
```
lsmod | grep acer
```

If that does not help, there is an interesting parameter available -
```

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
....
**parm:           no_hw_rfkill_switch:[COLOR="#FF0000"]Ignore the GPIO RFKill switch state[/COLOR] (bool)**

```
I'm not sure it does what I *think* it does. Let's find out by using it -
```
echo "options ath5k no_hw_rfkill_switch=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
Reboot and see if we have any pleasant surprise.

Regarding this -
> What caught my eye is that this time wlan0 is not getting any power and the power management is off. 
```
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   **[COLOR="#FF0000"]Tx-Power=off [/COLOR]**  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:**off**

```
While Power Management being off is a good thing (it won't try to *save* power, which is good for us), I believe the Tx-Power=off is a result, not the cause of the hard-block. Nevertheless, you may try -
```
sudo iwconfig wlan0 txpower=**[COLOR="#0000CD"]on[/COLOR]**
```
You may also try some other acceptable values instead of "on", like auto, fixed, 15, 20 etc. See "man iwconfig" (txpower section) for details.

Finally this -
> Also i would somehow remember from some other thread that NetworkManagers ```
[ifupdown] managed=false
``` should be true?

The default value is "false", which only means that Network Manager will ignore any interfaces that are managed by /etc/network/interfaces file. It is perfectly okay and has nothing to do with wifi hardblock state.

So... we have two things to try - 1) blacklist acer-wmi, 2) try the driver parameter as suggested above.
Try these and let me know the result.

**PS:**
Whatever happens to the wifi issue, congratulations for the thread being promoted from monologue to a dialogue :P
By the way, you can always PM those who you think may be able to help. ;)

---

### Post by henrik2 on 2013-11-10
!! A reply! [-o< the forums are alive! (no but really thanks for the reply. appreciated)

Since i found the script from your signature, i thought to forward the credits to you. Anyhow hats off and thanks to the developers of the script.

Now for the codes:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Did unfortunately not work, and confirmed it doesn't load on startup (lsmod returns nothing)

That```
**parm:           no_hw_rfkill_switch:[COLOR=#FF0000]Ignore the GPIO RFKill switch state[/COLOR] (bool)**
``` is indeed interesting parameter, strange i did not notice it. Have to pay more attention next time. However adding the options to the config did not help either. So still have to look for other options.

Thanks for clarifying those two, especially "power=off" to  be a result instead of a cause of hardblock.

---

### Post by varunendra on 2013-11-10
Hmm.. let's take a look at a fresh report of the wireless_script, plus the outputs of (after implementing the previously suggested changes) -
```
lsmod
dmesg | egrep 'ath5k|wlan'
grep -R '[[:alnum:]]' /sys/module/{ath5k,acer_wmi}/parameters
```
If you get any error about "acer_wmi" directory not existing, also try "acer-wmi" (hyphen instead of underscore). You'd get error on both if it is still blacklisted. To unblacklist it (since blacklisting doesn't seem to be helping) -
```
sudo sed -i '/^blacklist acer-wmi/ d' /etc/modprobe.d/blacklist.conf
```

---

### Post by henrik2 on 2013-11-10
Fresh report:
```

*************** info trace ***************

***** uname -a *****

Linux Aspire-5040 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 athlon i686 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

***** lspci *****

06:05.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0418]
    Kernel driver in use: ath5k
--
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:1079]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

ath5k                 134963  0 
ath                    19187  1 ath5k
mac80211              513247  1 ath5k
cfg80211              401436  3 ath,ath5k,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             192.168.0.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     No scan results


***** resolv.conf *****

nameserver 127.0.1.1
search home.gateway

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist acer-wmi

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

***** modinfo *****

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     B7A923930DCF3B82CF57D26
alias:          pci:v0000168Cd0000FF1Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-12-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x001a (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   14.612526] ath5k 0000:06:05.0: registered as 'phy0'
[   16.203008] ath: EEPROM regdomain: 0x63
[   16.203014] ath: EEPROM indicates we should expect a direct regpair map
[   16.203017] ath: Country alpha2 being used: 00
[   16.203019] ath: Regpair used: 0x63
[   16.238634] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   18.348081] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.348590] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

lsmod:
```
Module                  Size  Used by
nls_iso8859_1          12617  0 
zram                   18070  1 
parport_pc             31981  0 
ppdev                  17391  0 
rfcomm                 53664  0 
bnep                   18893  2 
bluetooth             323534  10 bnep,rfcomm
arc4                   12536  2 
joydev                 17097  0 
snd_hda_codec_realtek    45473  1 
pcmcia                 51368  0 
snd_hda_intel          42658  1 
snd_hda_codec         164003  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
radeon               1307301  2 
snd_pcm                89488  2 snd_hda_codec,snd_hda_intel
ath5k                 134963  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19187  1 ath5k
snd_rawmidi            25094  1 snd_seq_midi
yenta_socket           40193  0 
ttm                    71886  1 radeon
mac80211              513247  1 ath5k
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
pcmcia_rsrc            18319  1 yenta_socket
drm_kms_helper         46867  1 radeon
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
k8temp                 12842  0 
snd_timer              24447  2 snd_pcm,snd_seq
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
drm                   242354  4 ttm,drm_kms_helper,radeon
psmouse                90642  0 
serio_raw              13189  0 
cfg80211              401436  3 ath,ath5k,mac80211
snd                    60790  12 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i2c_piix4              17682  0 
i2c_algo_bit           13197  1 radeon
soundcore              12600  1 snd
wmi                    18590  0 
video                  18777  0 
ohci_pci               13305  0 
mac_hid                13037  0 
ati_agp                13177  0 
shpchp                 32129  0 
lp                     13299  0 
parport                40795  3 lp,ppdev,parport_pc
usb_storage            48294  0 
pata_acpi              12886  0 
r8169                  61434  0 
mii                    13654  1 r8169
pata_atiixp            13058  2 

```

dmesg:
```
[   14.612526] ath5k 0000:06:05.0: registered as 'phy0'
[   16.238634] ath5k: phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   18.348081] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.348590] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


```

grep -R '[[:alnum:]]' /sys/module/{ath5k,acer_wmi}/parameters:

straaaange...
```
/sys/module/ath5k/parameters/no_hw_rfkill_switch:Y
/sys/module/ath5k/parameters/fastchanswitch:N
[COLOR=#ff0000]/sys/module/ath5k/parameters/nohwcrypt:N[/COLOR]
grep: /sys/module/acer_wmi/parameters: No such file or directory


```

nohwcrypt won't change its parameter when either ```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf

or

echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf


```

Any idea? gksudo?

---

### Post by varunendra on 2013-11-11
That is indeed strange, although I don't think that parameter has anything to do with hard block state. But since it is abnormal for it to not accept the parameter, please check (assuming you have made the parameter permanent by creating a conf file) -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k
```
Does the second command return any error messages? Post back if there are any.

And let's also check if there are unnecessary conf files for the driver -
```
grep ath5k /etc/modprobe.d/*
```

I don't have many ideas left about the hard block state now. But since blacklisting acer-wmi didn't help, please remove it from blacklist as suggested earlier. Check lsmod on next boot to make sure it is loading again. Then try various boot options temporarily, the **acpi** related ones, as suggested here : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
List of (almost) all available acpi related boot options : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

---

### Post by henrik2 on 2013-11-11
Looked up from Linux wireless wiki that it's working as supposed (i guess?). > **Hardware Encryption:**[COLOR=#000000][FONT=Arial] Hardware encryption is enabled again, by sharing code with ath9k. Before that HW encryption was disabled in AP mode due to bugs in the ath5k key handling.[/FONT][/COLOR]Link: [http://wireless.kernel.org/en/users/Drivers/ath5k#A2010-09-16](http://wireless.kernel.org/en/users/Drivers/ath5k#A2010-09-16)

Neither of the ath5k modprobe commands reports any errors.

Aaand grep finds:
```

/etc/modprobe.d/ath5k.conf:options ath5k nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop

```

Seems like nohwcrypt and no_hw_rfkill_switch are overlapping each other since```
[COLOR=#000000]grep -R '[[:alnum:]]' /sys/module/{ath5k,acer_wmi}/parameters:[/COLOR]
``` shows this time:
```

/sys/module/ath5k/parameters/no_hw_rfkill_switch:N
/sys/module/ath5k/parameters/fastchanswitch:N
/sys/module/ath5k/parameters/nohwcrypt:Y

```

well, retyped hw_kill_switch to be true and nohwcrypt to be false.

Will start trying those acpi options later today.

---

### Post by varunendra on 2013-11-11
> **henrik2 said:**
> Looked up from Linux wireless wiki that it's working as supposed (i guess?).
You certainly aren't using your wireless in AP (access point) mode which that quote from the wiki page refers to. Besides, you just confirmed yourself that it does accept the parameter. So 'Now' it is working as expected, there might have been some error/conflict/override earlier.

> Seems like nohwcrypt and no_hw_rfkill_switch are overlapping each other since```
[COLOR=#000000]grep -R '[[:alnum:]]' /sys/module/{ath5k,acer_wmi}/parameters:[/COLOR]
``` shows this time:
```

/sys/module/ath5k/parameters/no_hw_rfkill_switch:N
/sys/module/ath5k/parameters/fastchanswitch:N
/sys/module/ath5k/parameters/nohwcrypt:Y

```

well, retyped hw_kill_switch to be true and nohwcrypt to be false.
In our attempt to make "no_hw_rfkill_switch" parameter permanent, we overwrote the "ath5k.conf" file, thus removing the imposition of "nohwcrypt=Y" parameter, so I don't think they are overlapping. You can try -
```
echo "options ath5k nohwcrypt=Y no_hw_rfkill_switch=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```

Another parameter (the last one) - "fastchanswitch" also seems to be meant specifically for your card. I overlooked it as it doesn't seem to have anything to do with hardblock. But since the obvious ones aren't seem to be helping, you may also try that (in temporary mode of course) -
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k fastchanswitch=Y
```
..needless to say - that's an attempt in desperation. I was most hopeful with the first two suggestions (blacklisting acer_wmi and the rfkill parameter), and now the next best hope is with some of the acpi boot options.

---

