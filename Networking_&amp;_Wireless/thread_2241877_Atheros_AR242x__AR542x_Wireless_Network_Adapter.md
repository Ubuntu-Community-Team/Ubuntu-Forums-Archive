---
title: "Atheros AR242x / AR542x Wireless Network Adapter"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by shane28 on 2014-08-28
I just installed Linux on an old laptop that was gathering dust in a closet due to a CPU issue to learn a new OS in my spare time. Of course, now that Linux is installed, the computer is working flawlessly. All this to say I'm very, very, very new to Linux and am a little overwhelmed by the terminal piece of the software. I'm running through the supplied tutorial on the website, which is great, but I am realizing it will take some time to be proficient in the software. Unfortunately, my wireless adapter failed to install during the OS install process forcing me to bounce between computers while playing, which leads to my problem and request from the community.

Through some digging in the forums I have found some prompts that has given me the type of installed wireless adapter, listed in the title (Atheros AR242x / AR542x Wireless Network Adapter). None of the commands I've found so far have done anything for me, could someone give me the command needed to install the proper driver for this adapter so I don't have to use two laptops to learn how to use Linux?

Thanks Guys

Shane

---

### Post by Hadaka on 2014-08-28
Hi, please follow the yellow brick road..
[http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222)
thanks

---

### Post by shane28 on 2014-08-28
Thanks so much for your help, my output is as follows:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Linux 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Turion(tm) X2 Dual-Core Mobile RM-72
Memory : 3699 MB
Uptime : 22:16:56 up 14 min,  2 users,  load average: 1.03, 0.79, 0.48


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30f2]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 5986:0137 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            yes


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k_htc              95963  0 
ath9k_common           13551  1 ath9k_htc
ath9k_hw              453856  2 ath9k_common,ath9k_htc
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath5k                 149924  0 
ath                    28698  4 ath9k_common,ath5k,ath9k_htc,ath9k_hw
mac80211              630653  2 ath5k,ath9k_htc
cfg80211              484040  4 ath,ath5k,mac80211,ath9k_htc
wmi                    19177  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
ath9k_htc     (3): btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
============================o=============o========o=============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169  | connected   | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         73.177.108.198
    Prefix:          24 (255.255.255.0)
    Gateway:         73.177.108.1
    DNS:             75.75.75.75
    DNS:             75.75.76.76

    Address:         2001:558:6006:6:4c94:4f7:109a:51c7
    Prefix:          128
    Gateway:         fe80::225:84ff:fe57:4ee2

    Address:         fe80::21e:68ff:fee0:6706
    Prefix:          64
    Gateway:         fe80::225:84ff:fe57:4ee2

    Address:         2001:558:6006:6:4c94:4f7:109a:51c7
    Prefix:          128
    Gateway:         ::
    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2
----------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | ath5k  | unavailable | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search hsd1.tn.comcast.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         73.177.108.1    0.0.0.0         UG    0      0        0 eth0
73.177.108.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 73.177.108.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 9.619/10.711/11.804/1.097 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.049/0.049/0.049/0.000 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k_htc]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
srcversion:     76D0CC269ACAA11EA825B93
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[hp_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[ath5k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

---

### Post by shane28 on 2014-08-28
Could the hard block be caused by a switch on the laptop? This model has a touch button for the wifi that is currently showing as "on" but is unresponsive, it reminds me that there was an issue with this button before the OS switch and another reason it ended up in a closet.

Thanks again for taking the time to help

Shane

---

### Post by Hadaka on 2014-08-29
Hi, yes ..hard block usually means a physical or keyboard switch
lets see if we can shake it lose.
please do..
```
sudo modprobe -r hp-wmi
sudo rfkill unblock all
```
*If that unblocks it then do.
```
sudo su
echo "blacklist hp-wmi"  >>  /etc/modprobe.d/blacklist.conf
exit 0
```
then do..
```
sudo modprobe -rf ath9k
sudo modprobe -rf ath5k
sudo modprobe -v ath5k
```
thanks.
*if it does NOT spring to life,please run the wireless script again

---

### Post by shane28 on 2014-08-29
Hadaka, I have a few rookie questions for you to make sure I am understanding your instructions correctly.

First, are each of these code boxes to be copied and pasted in full to the terminal or seperate by each line?

Second, how can I check if the hard block has been removed without running the original wireless script?

Last, the second code changes the beginning of my command line from "Shane@Linux:~$" to "root@Linux:". Is this normal?

I appologize for for the rookie questions, reallly looking forward to working through the tutorials after I get this WIFI problem worked out.

---

### Post by Hadaka on 2014-08-29
Hi, shane28
 Thank you for takeing the time to ask when you dont know what
to do. With linux that is a very wise thing to do.  please copy and
paste one line at a time. I broke it down to 3 seaparate command 
entries because the first will hopefully unblock your hard block
the second will write code to keep it unblocked
and the 3rd is to remove an incorrect driver and then unload
and reload the correct driver,,ath5k...thanks again!

to see if the hard block is removed use this command
```
rfkill list all
```
*also please note the added correction of "exit 0" in the second set of commands.
this will get you out of root and back into regular terminal. I apologize for that error.

---

### Post by shane28 on 2014-08-29
Eureka, got the hard block off. Still not showing any wireless networks in the Settings>Network>Wireless section. I went ahead and ran the wireless script again which gave me the output below. I just want to mention again that I did have a problem with this wireless card before switching over to Linux, it could end up being a hardware problem too.

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Linux 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Turion(tm) X2 Dual-Core Mobile RM-72
Memory : 3699 MB
Uptime : 10:25:01 up 6 min,  2 users,  load average: 0.71, 0.47, 0.25


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:30f2]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 5986:0137 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath5k                 149924  0 
ath                    28698  1 ath5k
mac80211              630653  1 ath5k
cfg80211              484040  3 ath,ath5k,mac80211
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

ath5k         (3): fastchanswitch=N | nohwcrypt=N | no_hw_rfkill_switch=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         73.177.108.198
    Prefix:          24 (255.255.255.0)
    Gateway:         73.177.108.1
    DNS:             75.75.75.75
    DNS:             75.75.76.76

    Address:         2001:558:6006:6:4c94:4f7:109a:51c7
    Prefix:          128
    Gateway:         fe80::225:84ff:fe57:4ee2

    Address:         fe80::21e:68ff:fee0:6706
    Prefix:          64
    Gateway:         fe80::225:84ff:fe57:4ee2

    Address:         2001:558:6006:6:4c94:4f7:109a:51c7
    Prefix:          128
    Gateway:         ::
    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | ath5k  | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search hsd1.tn.comcast.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         73.177.108.1    0.0.0.0         UG    0      0        0 eth0
73.177.108.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 73.177.108.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 7.610/7.646/7.683/0.094 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.063/0.098/0.134/0.036 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
```

---

### Post by Hadaka on 2014-08-29
getting rid of the hard block is great news, lets clean
some more stuff up and do some diagnostis. please do
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
sudo iw reg set US
```
then do and post,,,
```
ping -c3 8.8.8.8
ping -c3 75.75.75.75
ping -c3 google.com
```
then do and post..
```
sudo iwlist scan wlan0
```
thanks.

---

### Post by shane28 on 2014-08-29
Unfortunately, I'm getting the following response from your last command line
 ```
iwlist: unknown command `wlan0' (check 'iwlist --help').
```

The rest of the code looks as follows (I've replaced the ip address with some funny numbers)

```
shane@Linux:~$ sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
[sudo] password for shane: 
shane@Linux:~$ sudo iw reg set US
shane@Linux:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=50 time=23.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=50 time=22.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=50 time=19.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 19.585/21.699/23.100/1.525 ms
shane@Linux:~$ ping -c3 75.75.75.75
PING 75.75.75.75 (75.75.75.75) 56(84) bytes of data.
64 bytes from 75.75.75.75: icmp_seq=1 ttl=57 time=21.4 ms
64 bytes from 75.75.75.75: icmp_seq=2 ttl=57 time=20.3 ms
64 bytes from 75.75.75.75: icmp_seq=3 ttl=57 time=22.4 ms

--- 75.75.75.75 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 20.349/21.407/22.419/0.862 ms
shane@Linux:~$ 
shane@Linux:~$ ping -c3 google.com
PING google.com (555.555.55.55) 56(84) bytes of data.
64 bytes from atl14s08-in-f0.1e100.net (555.555.55.55): icmp_seq=1 ttl=57 time=28.8 ms
64 bytes from atl14s08-in-f0.1e100.net (555.555.55.55): icmp_seq=2 ttl=57 time=29.5 ms
64 bytes from atl14s08-in-f0.1e100.net (555.555.55.55): icmp_seq=3 ttl=57 time=28.1 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 28.190/28.851/29.564/0.595 ms

```

---

### Post by Hadaka on 2014-08-29
sorry about the command it is suppose to be,,,
```
sudo iwlist wlan0 scan
```
please run and post the output. 
thanks.

---

### Post by Hadaka on 2014-08-29
Let's configure your network settings, first remove the ethernet cable
and boot. you should have a triangle looking thing next to the envelope..upper right corner
this is the network manager applet. click that, then... edit connections..wireless and configure your settings like the attached
[ATTACH=CONFIG]255944[/ATTACH][ATTACH=CONFIG]255945[/ATTACH][ATTACH=CONFIG]255946[/ATTACH]
........wireless......................IPv4..........................IPv6......
be sure to also check the Available to all others box as well...lower left.

next
access your router settings and set them to wpa2 ccmp  aes
if possible, anything but tkip
boot and test.

---

