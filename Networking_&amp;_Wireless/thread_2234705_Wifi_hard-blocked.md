---
title: "Wifi hard-blocked"
date: 2014-07-16
forum: Networking &amp; Wireless
---

### Post by NeoX12 on 2014-07-16
Hello everyone. Going to start getting used to linux from today lol

I removed windows 8 and installed ubuntu 12.02 on an HP Envy m6 1201-tx

I can't get the wifi working. 
rfkill says that it's hard-blocked.

Also, I can't update/upgrade for some reason.

Can't implement the first command on this thread:
ubuntuforums.org/showthread.php?t=2104690

Can anyone help me with this?
Thanks so much!

---

### Post by Harsh_Parikh on 2014-07-16
I think the version,you have installed has not been supported by ubuntu...this may be one of the reasons for not updating....
for wifi try "nm-applet" command without quotes....may it be helpful to you.....

---

### Post by coffeecat on 2014-07-16
*Thread moved to **Networking & Wireless**.*

General rule of thumb is one thread per issue, unless they are closely related, so let's deal with the wireless issue first. I've renamed your thread - "tonne of problems" is hardly helpful to get the help you need. Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Run the wireless script and post the output file to your next post.

Have you connected you machine with an ethernet cable? If you haven't been able to establish a wired connection, and your wireless is not working, it would not be surprising that you cannot update your system.

Also - which version of Ubuntu are you running? "12.02" does not exist.

---

### Post by NeoX12 on 2014-07-16
Got this:

```
mashruf@SIS:~$ nm-applet
** Message: applet now removed from the notification area



```

Now I got two wifi icons on my taskbar lmao wth aaahahah

---

### Post by NeoX12 on 2014-07-16
> **coffeecat said:**
> *Thread moved to **Networking & Wireless**.*

General rule of thumb is one thread per issue, unless they are closely related, so let's deal with the wireless issue first. I've renamed your thread - "tonne of problems" is hardly helpful to get the help you need. Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Run the wireless script and post the output file to your next post.

Have you connected you machine with an ethernet cable? If you haven't been able to establish a wired connection, and your wireless is not working, it would not be surprising that you cannot update your system.

Also - which version of Ubuntu are you running? "12.02" does not exist.

Oh lol sorry. It's a 12.04.

I am connected to the router via an RJ45. I'll run that script right now and get back to you

Btw, battery life on ubuntu is terrible... any way to fix this?

---

### Post by NeoX12 on 2014-07-16
> **coffeecat said:**
> *Thread moved to **Networking & Wireless**.*

General rule of thumb is one thread per issue, unless they are closely related, so let's deal with the wireless issue first. I've renamed your thread - "tonne of problems" is hardly helpful to get the help you need. Have a look at this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Run the wireless script and post the output file to your next post.

Have you connected you machine with an ethernet cable? If you haven't been able to establish a wired connection, and your wireless is not working, it would not be surprising that you cannot update your system.

Also - which version of Ubuntu are you running? "12.02" does not exist.

wow I think that script was amazing. Where do I learn to make scripts like that lol

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux SIS 3.11.0-24-generic #42~precise1-Ubuntu SMP Fri Jul 4 21:22:54 UTC 2014 
x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

07:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168
/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:18a5]
    Kernel driver in use: r8169

08:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PC
Ie [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2800pci

##### lsusb #####

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c0e Sunplus Innovation Technology Inc. 

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #####

rt2800pci              18995  0 
rt2x00mmio             13661  1 rt2800pci
rt2800lib              81972  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              13287  1 rt2800pci
rt2x00lib              56180  4 rt2800pci,rt2x00mmio,rt2800lib,rt2x00pci
mac80211              623710  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              499466  2 rt2x00lib,mac80211
eeprom_93cx6           13344  1 rt2800pci

##### iw reg get #####

##### interfaces #####

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #####

nameserver 192.168.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

Aquiring of root rights failed.

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### modinfo #####

filename:       /lib/modules/3.11.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     259E8826760AAB9E718FD85
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.11.0-24-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.11.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     2C5ADAF564EF1DAD569D9C3
depends:        rt2x00lib
intree:         Y
vermagic:       3.11.0-24-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     6FD0985B470AF52D6303639
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.11.0-24-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     8422005AAAD8B7D2F811DC4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.11.0-24-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     13FDB85D06F5BF0E3B115CE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-24-generic SMP mod_unload modversions 

##### modules #####

loop
lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
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

[/etc/modprobe.d/hp.conf]
blacklist hp_wmi

##### udev rules #####

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (rt2800pci)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address  removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*",  NAME="wl
an0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2 (r8169)
SUBSYSTEM=="net",  ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address  removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*",  NAME="eth
0"

##### dmesg #####

[   10.440864] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   10.449167] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   25.564220] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready



```

---

### Post by NeoX12 on 2014-07-16
Failing to update anything else.

```
installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 206819 files and directories currently installed.) 
Preparing to replace libminiupnpc8 1.6-3ubuntu1 (using .../libminiupnpc8_1.6-3ubuntu1.1_amd64.deb) ... 
Unpacking replacement libminiupnpc8 ... 
Setting up fglrx-pxpress (0.6~hybrid0.0.2) ... 
dpkg: error processing fglrx-pxpress (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libminiupnpc8 (1.6-3ubuntu1.1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 fglrx-pxpress 
Setting up fglrx-pxpress (0.6~hybrid0.0.2) ... 
dpkg: error processing fglrx-pxpress (--configure): 
 subprocess installed post-installation script returned error exit status 1 


```

Even failed to install Ubuntu One.
I'll reboot.

---

### Post by NeoX12 on 2014-07-16
Anyone has any idea?

---

### Post by NeoX12 on 2014-07-16
.... Yeah I force installed the RT3290 driver into usr/src.... and now I have this:

```

eth0      Link encap:Ethernet  HWaddr 6c:3b:e5:84:be:4c  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::6e3b:e5ff:fe84:be4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2635784 (2.6 MB)  TX bytes:4870953 (4.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr f4:b7:e2:ac:5e:67  
          inet6 addr: fe80::f6b7:e2ff:feac:5e67/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 


```

---

### Post by kc1di on 2014-07-16
Try this command in a terminal  ```
rfkill unblock all
```
see if that will get you WIFI

---

### Post by NeoX12 on 2014-07-16
> **kc1di said:**
> Try this command in a terminal  ```
rfkill unblock all
```
see if that will get you WIFI

lmao after my venture of searching the internet for solutions, 

rfkill list all

doesn't even return an argument LOL

---

### Post by coffeecat on 2014-07-16
> **NeoX12 said:**
> Anyone has any idea?

Please stop bumping your thread so much and instead read what is posted. kc1di suggested "rfkill unblock all", not "rfkill list all"

---

### Post by NeoX12 on 2014-07-16
> **coffeecat said:**
> Please stop bumping your thread so much and instead read what is posted. kc1di suggested "rfkill unblock all", not "rfkill list all"


I was referring to both our commands.
None return any arguments.

And as for the bumping part, noted.

---

### Post by kc1di on 2014-07-16
after issuing ```
sudo rfkill unblock all
``` it will not return any comments , just run it and then see if you can access your WIFI.

---

### Post by NeoX12 on 2014-07-16
> **kc1di said:**
> after issuing ```
sudo rfkill unblock all
``` it will not return any comments , just run it and then see if you can access your WIFI.

Nope. The light on the WiFi toggle button is still orange. And there are no options to connect to a wireless internet.

After following another command though, I got an interface called ra0 but wlan0 is gone now. 

I have the option to create my own WiFi and even connect to hidden wireless connections...apparently. Tried to connect to mine. Didn't work.

Any commands I can put in, so the output helps you figure out what's wrong?

---

### Post by kc1di on 2014-07-16
in that case your going to have to find the machines switch. that turns on the wireless card on mine is the F2 key.  But it varies machine to machine.
You may also need to enable it in your bios. 

you may also want to download the script found on[ this page.]("http://ubuntuforums.org/showthread.php?p=13024222#post13024222")  and run it and post the output here.

---

### Post by NeoX12 on 2014-07-17
Yeah I tried clicking the toggle button.. but no luck. Oh and here's the output of the script.

```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel #####

Linux SIS 3.13.0-30-generic #55~precise1-Ubuntu SMP Fri Jul 4 21:52:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

07:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:18a5]
    Kernel driver in use: r8169

08:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2860

##### lsusb #####

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 138a:0018 Validity Sensors, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c0e Sunplus Innovation Technology Inc. 

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

rt3290sta            1178463  1 

##### iw reg get #####

##### interfaces #####

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

##### iwconfig #####

ra0       Ralink STA  ESSID:""  Nickname:"RT3290STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #####

nameserver 192.168.0.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: ra0 ------------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2860
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

ra0       No scan results

##### iwlist channel #####

ra0       14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### modinfo #####

filename:       /lib/modules/3.13.0-30-generic/updates/dkms/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     094638B480391A92BB06A40
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
depends:        
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

##### modules #####

loop
lp
rtc

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
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

[/etc/modprobe.d/blacklist-ralink.conf]
blacklist rt2800pci
blacklist rt2x00pci

[/etc/modprobe.d/hp.conf]
blacklist hp_wmi

##### udev rules #####

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.2 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:/sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0 (rt2860)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="ra*", NAME="ra0"

##### dmesg #####

[   10.077407] rt3290sta: module license 'unspecified' taints kernel.
[   10.077717] rt3290sta: module verification failed: signature and/or  required key missing - tainting kernel
[   26.032989] <==== rt28xx_init, Status=0
[   26.072030] <==== rt28xx_init, Status=0
[   26.412293] /var/lib/dkms/rt3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_asic.c:2608 assert KeyIdx < 4failed
[   26.412302] /var/lib/dkms/rt3290sta/2.6.0.0/build/src/os/linux/../../common/cmm_asic.c:2608 assert KeyIdx < 4failed

########## wireless info END ############

```

---

### Post by NeoX12 on 2014-07-17
Update: Reset my BIOS, then linux failed to boot, again went in to BIOS and turned on Legacy Support.
Came back to see that my ra0 connected to the wifi... but my android's Fing application showed no laptop connected to the wifi network.

Weird... the wifi toggle is still orange btw.

---

### Post by NeoX12 on 2014-07-17
ran lspci -vvnn

```

07:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:18a5]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 43
    Region 0: I/O ports at 2000 [size=256]
    Region 2: Memory at 61404000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at 61400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

08:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at 61510000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2860
    Kernel modules: rt3290sta, rt2800pci

08:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at 61500000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

```

Says rt2860 is in use, whereas the kernel drivers are rt3290sta and rt2800pci.

All I need to do now is remove the rt2860 and install the others.

I'm learning a lot lol. What next? Thanks a tonne for all the support.

---

### Post by varunendra on 2014-07-18
if you can, please remove the proprietary driver to get the native one back on job. Then, after a reboot, please post the output of the newer script that kc1di linked to. The one you have posted is from the regular script, which is okay, but the newer script provides much more info which may be helpful in some cases.

Along with the script output, please also post the output of -
```
egrep -i 'switch|rt2|firmware|rt3|ra0|wlan'
```

And if the installation is not UEFI based, have you tried resetting the BIOS yet? Resetting BIOS in a UEFI based installation has the risk to reset the boot manager too, so not recommended there.

---

### Post by NeoX12 on 2014-07-18
> **varunendra said:**
> if you can, please remove the proprietary driver to get the native one back on job. Then, after a reboot, please post the output of the newer script that kc1di linked to. The one you have posted is from the regular script, which is okay, but the newer script provides much more info which may be helpful in some cases.

Along with the script output, please also post the output of -
```
egrep -i 'switch|rt2|firmware|rt3|ra0|wlan'
```

And if the installation is not UEFI based, have you tried resetting the BIOS yet? Resetting BIOS in a UEFI based installation has the risk to reset the boot manager too, so not recommended there.

I am fairly new to Linux systems. So I have no idea how to remove drivers.. Did Google around but there are too many different links and terminal commands. Can anyone help me remove the driver so I can do the rest of the job? Thanks a lot.

---

### Post by tgalati4 on 2014-07-18
Open a terminal, post the output of:

```
cat /etc/modules
```

Also, check your BIOS for multimedia key support--enable it.  That was required on a friend's machine to get the wifi switch to work.  Check operation with:

```
rfkill list
```

---

### Post by varunendra on 2014-07-18
> **NeoX12 said:**
> Can anyone help me remove the driver so I can do the rest of the job?

There are two or three ways to install proprietary drivers downloaded as source package. Some need a "config > make > make install" sequence, some may provide an automated installation script (install.sh or autorun.sh). Depending upon the method used to install, the method to remove it opposite of it (e.g., "make uninstall" from the same directory where you ran "make install").

If you can confirm the exact source that you downloaded, and exact steps you followed to install the package, it would be a lot easier to uninstall it using standard procedure. Otherwise it can be done manually, but that would require some more information about current status.

So, can you give us the link to the guide or post that you followed to install the driver? Can you also give us link to the source package you downloaded to install it?

Of course try what tgalati4 suggested first, since that doesn't need a lot of critical changes in the system. If that succeeds, you don't need to do anything else.

---

### Post by NeoX12 on 2014-07-18
> **tgalati4 said:**
> Open a terminal, post the output of:

```
cat /etc/modules
```

Also, check your BIOS for multimedia key support--enable it.  That was required on a friend's machine to get the wifi switch to work.  Check operation with:

```
rfkill list
```

My BIOS is worthless lmao. Minimum number of options available.

```
# /etc/modules: kernel modules to load at boot time.#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.


loop
lp
rtc

```

and 
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

After attaching a wireless adapter. I want the internal adapter to start working.

---

### Post by NeoX12 on 2014-07-18
> **varunendra said:**
> There are two or three ways to install proprietary drivers downloaded as source package. Some need a "config > make > make install" sequence, some may provide an automated installation script (install.sh or autorun.sh). Depending upon the method used to install, the method to remove it opposite of it (e.g., "make uninstall" from the same directory where you ran "make install").

If you can confirm the exact source that you downloaded, and exact steps you followed to install the package, it would be a lot easier to uninstall it using standard procedure. Otherwise it can be done manually, but that would require some more information about current status.

So, can you give us the link to the guide or post that you followed to install the driver? Can you also give us link to the source package you downloaded to install it?

Of course try what tgalati4 suggested first, since that doesn't need a lot of critical changes in the system. If that succeeds, you don't need to do anything else.

Hey man, first of all, thanks a bunch for taking your own time our and helping me out this.

Here's the link I followed: [http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04](http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04)

---

### Post by tgalati4 on 2014-07-18
So we have determined that you are not manually loading a wireless module (/etc/modules) the rtc is a real-time clock, lp is a parallel printer port, don't know what loop is--perhaps some sort of loopback (virtual) device needed for something.

We have determined that your wireless is not switched off (hard block: yes) nor is it disabled in network-manager (soft block: yes).

But it was switched off previously:

> 
##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

So something changed.  Wireless will never connect if it is physically turned off.

Unfortunately, there does not seem to be an easy solution to get wireless to work with this chip:

[http://askubuntu.com/questions/375543/problems-about-the-drivers-for-ralink-rt3290-wi-fi-adapter](http://askubuntu.com/questions/375543/problems-about-the-drivers-for-ralink-rt3290-wi-fi-adapter)

[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

So, others have been able to get it working.  It requires some patience and some experience with linux, compiling, and handling modules.  Don't expect to get it right the first time.  Keep an ethernet cable handly.  You will need it.

---

### Post by varunendra on 2014-07-18
> **NeoX12 said:**
> Hey man, first of all, thanks a bunch for taking your own time our and helping me out this.

Here's the link I followed: [http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04](http://askubuntu.com/questions/455030/ralink-rt3290-wifi-driver-is-not-working-in-ubuntu-14-04)

Assuming you used the dkms package solution (has been reported to work in most recent posts), then the command to remove it is -
```
sudo dkms remove rt3290sta/2.6.0.0 --all
```
..as per the README guide included in the package that you downloaded.

---

### Post by NeoX12 on 2014-07-19
> **varunendra said:**
> Assuming you used the dkms package solution (has been reported to work in most recent posts), then the command to remove it is -
```
sudo dkms remove rt3290sta/2.6.0.0 --all
```
..as per the README guide included in the package that you downloaded.
Did as you asked me to and got this:
```


Mashruf@SIS:~/Downloads/Torrents$ sudo dkms remove rt3290sta/2.6.0.0 --all


-------- Uninstall Beginning --------
Module:  rt3290sta
Version: 2.6.0.0
Kernel:  3.11.0-26-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


rt3290sta.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.11.0-26-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




Running the post_remove script:
depmod.........


Backing up initrd.img-3.11.0-26-generic to /boot/initrd.img-3.11.0-26-generic.old-dkms
Making new initrd.img-3.11.0-26-generic
(If next boot fails, revert to initrd.img-3.11.0-26-generic.old-dkms image)
update-initramfs..........


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  rt3290sta
Version: 2.6.0.0
Kernel:  3.13.0-30-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


rt3290sta.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-30-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




Running the post_remove script:
rm: cannot remove `/etc/modprobe.d/blacklist-ralink.conf': No such file or directory
depmod........


Backing up initrd.img-3.13.0-30-generic to /boot/initrd.img-3.13.0-30-generic.old-dkms
Making new initrd.img-3.13.0-30-generic
(If next boot fails, revert to initrd.img-3.13.0-30-generic.old-dkms image)
update-initramfs........


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  rt3290sta
Version: 2.6.0.0
Kernel:  3.13.0-32-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


rt3290sta.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-32-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




Running the post_remove script:
rm: cannot remove `/etc/modprobe.d/blacklist-ralink.conf': No such file or directory
depmod........


Backing up initrd.img-3.13.0-32-generic to /boot/initrd.img-3.13.0-32-generic.old-dkms
Making new initrd.img-3.13.0-32-generic
(If next boot fails, revert to initrd.img-3.13.0-32-generic.old-dkms image)
update-initramfs........


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  rt3290sta
Version: 2.6.0.0
Kernel:  3.2.0-67-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


rt3290sta.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-67-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




Running the post_remove script:
rm: cannot remove `/etc/modprobe.d/blacklist-ralink.conf': No such file or directory
depmod....


: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.


DKMS: uninstall completed.


------------------------------
Deleting module version: 2.6.0.0
completely from the DKMS tree.
------------------------------
Done.


```

---

### Post by NeoX12 on 2014-07-19
> **tgalati4 said:**
> So we have determined that you are not manually loading a wireless module (/etc/modules) the rtc is a real-time clock, lp is a parallel printer port, don't know what loop is--perhaps some sort of loopback (virtual) device needed for something.

We have determined that your wireless is not switched off (hard block: yes) nor is it disabled in network-manager (soft block: yes).

But it was switched off previously:



So something changed.  Wireless will never connect if it is physically turned off.

Unfortunately, there does not seem to be an easy solution to get wireless to work with this chip:

[http://askubuntu.com/questions/375543/problems-about-the-drivers-for-ralink-rt3290-wi-fi-adapter](http://askubuntu.com/questions/375543/problems-about-the-drivers-for-ralink-rt3290-wi-fi-adapter)

[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

[http://ubuntuforums.org/showthread.php?t=2104690](http://ubuntuforums.org/showthread.php?t=2104690)

So, others have been able to get it working.  It requires some patience and some experience with linux, compiling, and handling modules.  Don't expect to get it right the first time.  Keep an ethernet cable handly.  You will need it.

Alright man. Really appreciate it. I will definitely take a look at those links once java has finished downloading on my system.
Now that I got that proprietary graphics driver removed, I can install packages properly. I think I'll be able to fix this pretty soon.


I'll keep you updated man. Thanks so much :)

---

### Post by praseodym on 2014-07-19
```
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
```

Did you install the firmware for th rt3290st driver?

Please try:
```

echo hp_wmi | sudo tee -a /etc/modules
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot after that

---

### Post by tgalati4 on 2014-07-19
Why do you have so many kernel versions on your system?  You should remove the old kernels using *synaptic*:  3.2.XX, 3.5.XX, 3.11.XX and just keep 3.13.XX.  These proprietary drivers have to be compiled and linked to the kernel and having so many kernels can cause installation issues.  The installers expect only one kernel.

---

### Post by NeoX12 on 2014-07-19
> **praseodym said:**
> ```
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
```

Did you install the firmware for th rt3290st driver?

Please try:
```

echo hp_wmi | sudo tee -a /etc/modules
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot after that

```

mashruf@SIS:~$ sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware
[sudo] password for mashruf: 
cp: cannot stat `/usr/src/Ralink_3290sta/src/common/rt3290.bin': No such file or directory
mashruf@SIS:~$ echo hp_wmi | sudo tee -a /etc/modules
hp_wmi
mashruf@SIS:~$ echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
options hp_wmi wireless=1

```

Rebooting. . .

Btw, the dialogue box for connecting to my wifi constantly keeps on popping up, so I can choose between my internal adapter and the external adapter.. irritating.

---

### Post by NeoX12 on 2014-07-19
> **praseodym said:**
> ```
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
```

Did you install the firmware for th rt3290st driver?

Please try:
```

echo hp_wmi | sudo tee -a /etc/modules
echo "options hp_wmi wireless=1" | sudo tee /etc/modprobe.d/hp.conf
```
Reboot after that
Good LORD IT WORKED!

Laptop's wifi adapter working the way it's supposed to! You guys are effin' amazing! Your terminal commands did the trick!

---

### Post by NeoX12 on 2014-07-23
Right. My laptop's adapter works fine but when I attach and connect to the wifi using my wireless adapter, even after being connected, it keeps on asking me my password for connecting to the wifi.
This dialogue box comes up, asking me to select my adapter - either the internal or external one.

I've tried:
```


sudo ifconfig wlan0 down


```

Doesn't work.

---

### Post by praseodym on 2014-07-23
Try to unload/load the internal driver when the stick is plugged/unplugged:

```
gksudo gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Put this in:

```
ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"

SUBSYSTEM=="net", KERNEL=="wlan1", RUN+="/sbin/modprobe -rf rt3290sta"

GOTO="rules_end"

LABEL="onboard_load"

SUBSYSTEM=="net", KERNEL=="wlan*", RUN+="/sbin/modprobe rt3290sta"

LABEL="rules_end"


```
Restart UDEV:
```

sudo service udev reload
sudo service udev restart
```
Re-plug the stick

---

### Post by NeoX12 on 2014-07-23
> **praseodym said:**
> Try to unload/load the internal driver when the stick is plugged/unplugged:

```
gksudo gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Put this in:

```
ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"

SUBSYSTEM=="net", KERNEL=="wlan1", RUN+="/sbin/modprobe -rf rt3290sta"

GOTO="rules_end"

LABEL="onboard_load"

SUBSYSTEM=="net", KERNEL=="wlan*", RUN+="/sbin/modprobe rt3290sta"

LABEL="rules_end"


```
Restart UDEV:
```

sudo service udev reload
sudo service udev restart
```
Re-plug the stick

Did what you asked me to :)
Things look fine for now.

Where'd you learn all that man? Pretty amazing stuff right there.

---

### Post by varunendra on 2014-07-23
> **praseodym said:**
> Try to unload/load the internal driver when the stick is plugged/unplugged:

```
gksudo gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Put this in:

```
ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check"

SUBSYSTEM=="net", KERNEL=="wlan1", RUN+="/sbin/modprobe -rf rt3290sta"

GOTO="rules_end"

LABEL="onboard_load"

SUBSYSTEM=="net", KERNEL=="wlan*", RUN+="/sbin/modprobe rt3290sta"

LABEL="rules_end"


```
Restart UDEV:
```

sudo service udev reload
sudo service udev restart
```
Re-plug the stick
Nice hack praseodym! I'd be interested too in knowing how you came up with this one. :)

---

### Post by praseodym on 2014-07-23
From one of my German collegues here:

[http://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322](http://forum.ubuntuusers.de/topic/wlan-usb-8194/#post-3133322)

I've posted it somewhere here, too, but I don't find it right now.

---

### Post by NeoX12 on 2014-07-24
Bleh. No luck. The dialogue box still keeps on coming up even when I'm connected to my wifi.

---

### Post by praseodym on 2014-07-24
Which encryption do you use? Try WPA2-AES (CCMP), check the router manual

---

### Post by NeoX12 on 2014-07-24
That's what I use. AES.

---

### Post by praseodym on 2014-07-24
Strange, lets check out:
```

lsmod
iwconfig
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
iwlist chan
sudo iwlist scan
```

---

### Post by varunendra on 2014-07-24
..or a fresh report of the wireless_script for even more comprehensive report, use the new one this time : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

