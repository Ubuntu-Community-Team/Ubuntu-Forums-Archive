---
title: "No wireless connection/recognition"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by Jacob_field on 2014-05-21
Hi, I am having a problem with connecting to a wireless network in lubuntu. I have a Toshiba Portege running lubuntu 14.04. I can connect via ethernet cable.

Here are the details:

It shows the wireless device  as eth1 in System tools/System profiler and benchmark/Interfaces 

I got the internet connection icon on the panel, but when I click it and enter eth1, the status is disconnected.

In the connection properties for eth1, it says: Type: ethernet Address: 00:0E:35:14:37:F9

I have run the wireless_script mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=2082305&highlight=wireless](http://ubuntuforums.org/showthread.php?t=2082305&highlight=wireless)
and here are the results:

 
```
======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

jacobs-toshiba 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) M processor 1500MHz
Memory : 2015 MB
Uptime : 10:34:02 up  1:07,  2 users,  load average: 0.45, 0.48, 0.34


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:05.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Device [8086:2741]
    Kernel driver in use: ipw2200
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 3938:1047  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ipw2200               136401  0 
libipw                 33144  1 ipw2200
lib80211               14040  2 libipw,ipw2200
cfg80211              409394  2 libipw,ipw2200
wmi                    18673  1 toshiba_acpi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
ipw2200      (18): antenna=0 | associate=0 | auto_create=1 | bt_coexist=0 | burst_duration_CCK=0 | burst_duration_OFDM=0 | channel=0 | cmdlog=0 | debug=0 | disable=0 | hwcrypto=0 | led=1 | mode=0 | qos_burst_enable=0 | qos_enable=0 | qos_no_ack_mask=0 | roaming=1 | rtap_iface=0
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | e100    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.107
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth1                       | 802.11 WiFi | ipw2200 | disconnected | no      |           | WEP/WPA/WPA2 | <MAC eth1>

    wireless:        Infra, <MAC C-02 wireless>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    Belkin_N_Wireless_B840A7: Infra, <MAC C-01 Belkin_N_Wireless_B840A7>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WEP
    CenturyLink2642: Infra, <MAC C-NA CenturyLink2642 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    belkin.2b1:      Infra, <MAC C-03 belkin.2b1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Wi-Fi                : ssid=wireless | mac-address=<MAC eth1> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.260/0.276/0.293/0.023 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.044/0.053/0.063/0.012 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

eth1      11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Current Channel=0 - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

eth1      Scan completed :
          Cell 01 - Address: <MAC C-01 Belkin_N_Wireless_B840A7>
                    ESSID:"Belkin_N_Wireless_B840A7"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=41/100  Signal level=-76 dBm  
                    Extra: Last beacon: 244ms ago
          Cell 02 - Address: <MAC C-02 wireless>
                    ESSID:"wireless"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-41 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 96ms ago
          Cell 03 - Address: <MAC C-03 belkin.2b1>
                    ESSID:"belkin.2b1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7176ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ipw2200]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
version:        1.2.2kmprq
srcversion:     6432FDB1497A8B2EC025CB2
depends:        cfg80211,libipw,lib80211
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)

[libipw]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ipw2x00/libipw.ko
version:        git-1.1.13
srcversion:     73DCC060143DEA6F7EDA255
depends:        cfg80211,lib80211

[lib80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=1a5d83e8-d2c2-4556-8f53-e6471cc361ee ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.795389] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.795959] audit: initializing netlink socket (disabled)
[   13.271848] wmi: Mapper loaded
[   14.416258] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   14.416267] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.416516] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.090034] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   16.837270] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 3162.927929] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3163.924063] ipw2200: Failed to send CARD_DISABLE: Command timed out.


======== Done ============
```


Do any of you know what might be wrong? 

Thanks, Jacob

---

### Post by wildmanne39 on 2014-05-21
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2014-05-21
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by varunendra on 2014-05-22
Which one of the listed Routers/Access-Points is yours? Recommended encryption setting is pure WPA2-AES (CCMP). No WPA/WPA2 mixed mode, and certainly not TKIP. Try changing it to pure WPA2 with AES (CCMP) if it is currently set to any other encryption type.

Also, if there is an option to change it, make sure the 'Regulatory Domain' setting is set to your country in the router (are you in US?). Recommended channels are 1 and 11, unless they are already too congested due to neighbouring APs.

In Ubuntu, try (assuming you are in US, if not, change "US" to your country code which you can find here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table) )-
```
sudo iw reg set US
```
Then check -
```
iw reg get
```
It should show the RegDomain settings of "US" now.

---

### Post by Jacob_field on 2014-05-22
I tried the both commands, and the first said something like command not found, and the second said something like theprogram iw is not currently installed, and tells me how to install it. I am asuming I should install it? As for the routers, I think the one under wireless: ```
 wireless: Infra, <MAC C-02 wireless>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    Belkin_N_Wireless_B840A7: Infra, <MAC C-01 Belkin_N_Wireless_B840A7>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WEP
    CenturyLink2642: Infra, <MAC C-NA CenturyLink2642 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    belkin.2b1:      Infra, <MAC C-03 belkin.2b1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 
``` How do I change router settings like that? Also, would it affect the other computers in my house running windows?

Thanks, Jacob

---

### Post by Jacob_field on 2014-05-22
Also, I did go ahead and install iw.

Jacob

---

### Post by varunendra on 2014-05-23
> **Jacob_field said:**
> How do I change router settings like that? Also, would it affect the other computers in my house running windows?
To change router settings (if needed after setting regdomain code), please refer to your router's user manual. The options and layout in various routers' admin control panels can be so different, it is not possible to refer to a guide that suits all. And no, it won't affect other computers in the house. At most they may ask you the security key once more after changing the settings, nothing more.

> **Jacob_field said:**
> Also, I did go ahead and install iw.

So did you try the 'iw reg set' command? Did it make any difference? If not, please check/change the router settings as mentioned earlier.

---

### Post by Jacob_field on 2014-05-23
Ok. I did try the 'iw reg set' command, and it didn't seem to do anything. I will see what I can do with the router.

---

### Post by Jacob_field on 2014-05-23
One thing that might help, I don't think it is a connection/router problem, it seems more like the OS mostly ignores the fact that there is a wireless card installed. It seems to me that it may need a driver, but I have tried additional drivers under software and updates when plugged into ethernet several times, to no avail. Also, under users and groups, I was looking at advanced settings, and I noticed that under user privileges, the "Connect to wireless and ethernet networks" was unchecked, so I just checked all the boxes, and saved it. I have checked back several times, and it has stayed the same.

---

### Post by Jacob_field on 2014-05-23
Also, when I clicked on configure after clicking on the network icon at the icon tray, it gave me an error: "The interface does not exist Check that it is correctly typed and that it is correctly supported by your system."

---

### Post by varunendra on 2014-05-24
> **Jacob_field said:**
> One thing that might help, I don't think it is a connection/router problem, it seems more like the OS mostly ignores the fact that there is a wireless card installed.

Does it get disappeared from "lspci" output? If so, that would be a hardware problem. The card may be loose or totally broken.

When it seems it disappeared, please check -
```
lspci -nnk | grep -iA2 net
```
In the output, do you see these lines -
```
02:05.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Device [8086:2741]
    Kernel driver in use: ipw2200
```
?? If not, either the card is loose, or is gone.

---

### Post by Brian_McCabe on 2014-05-25
I have a Broadcom NIC which I could not get to work and finally discovered that to get the system to recognize this I was supposed to enter the following in the Terminal, 
'sudo apt-get install firmware-b43-installer' (No quotes) but it still did not work. 
Being a REAL Linux EGGSPERT I then decided to try the following.
I entered 'nm-applet' in a Terminal and after hitting enter, with the Terminal still active, I clicked on the new applet in the taskbar, the one with 2 arrows, one pointed up and the other pointed down, and then selected my Wi-Fi Network from those shown and entered the data to activate this, and everything now works.
I hope this makes sense and that it helps.

---

### Post by Jacob_field on 2014-05-27
Brain, I tried the nm-applet thing and it worked. Thank you both of you for your help!

---

