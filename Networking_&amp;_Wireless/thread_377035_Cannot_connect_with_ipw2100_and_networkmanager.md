---
title: "Cannot connect with ipw2100 and networkmanager"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by marciano#1 on 2007-03-05
My laptop has an Intel ipw2100 card. I verified that it may work in NetworkManager.
Kubuntu Edgy 6.10  I have installed NetworkManager and KNetworkManager.
eth0 and eth1 are enabled in System Settings - Network Settings.
I got three icons: a picture with and unplugged RJ and a red cross (disconnected), and two pairs of monitors (working wired eth0 and not working eth1).

**$iwlist eth1 scan**   //detected remote Ad-Hoc

eth1      Scan completed :
          Cell 01 - Address: 02:05:20:A8:D4:03
                    ESSID:"STONE WIFI"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality:98  Signal level:0  Noise level:0
                    Extra: Last beacon: 6156ms ago

**$ ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:02:3F:BB:5D:C6
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:febb:5dc6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1890803 (1.8 MiB)  TX bytes:301301 (294.2 KiB)
          Interrupt:10 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 00:04:23:6B:E7:46
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000 Memory:e0000000-e0000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6768 (6.6 KiB)  TX bytes:6768 (6.6 KiB)

**$ iwconfig**

lo        no wireless extensions.

eth1      unassociated  ESSID:"Ubuntu_WiFi"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

Ad-Hoc unit is an old D-Link dwl-120 I've been using about 2 o 3 years. It is working fine, I use it for wireless connection for my PDA.
I remember I had some problems getting d-link work fine (win XP): I had to manually set channel 11 in both laptop and desktop. (just a thought).

Thanks in advance

---

### Post by RomeReactor on 2007-03-05
Hi. According to your iwlist scan:

> eth1 Scan completed :
Cell 01 - Address: 02:05:20:A84:03
ESSID:"STONE WIFI"
Protocol:IEEE 802.11b
Mode:Ad-Hoc
**Channel:11**

however, your iwconfig shows:

> Mode:Managed **Channel=0** Access Point: Not-Associated

It seems you have to set your channel using iwconfig: If you haven't done so already, open a terminal (Applications-->Accessories-->Terminal) and type

```
sudo iwconfig eth1 channel 11
```

Or manually enter the channel in your **interfaces** file:

```
gksudo gedit /etc/network/interfaces
```

look for your **eth1** entry and add below it

```
wireless-channel 11
```

save, close and reboot. See if that helps.

---

### Post by marciano#1 on 2007-03-06
> $ sudo iwconfig eth1 channel 11
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.

I edited /etc/network/interfaces manually added:

iface eth1 inet static
address 192.168.0.2
netmask 255.255.255.0
wireless-essid Ubuntu_WiFi
**wireless-channel 11**

but 
> $iwconfig
still

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Ubuntu_WiFi"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:16 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I previously had disabled eth1 and rebooted

---

### Post by marciano#1 on 2007-03-06
> sudo iwconfig eth1 mode ad-hoc


fixed this issue......  aparentely.
Network monitor turned on after performing that command but kNetworkManager is still "disconnected"

---

### Post by marciano#1 on 2007-03-06
pinging to access point IP produces duplicated packages, I don't know why

From Apple Manual Page for ping
[I]DUPLICATE AND DAMAGED PACKETS
     The ping utility will report duplicate and damaged packets.  Duplicate
     packets should never occur when pinging a unicast address, and seem to be
     caused by inappropriate link-level retransmissions.  Duplicates may occur
     in many situations and are rarely (if ever) a good sign, although the
     presence of low levels of duplicates may not always be cause for alarm.
     Duplicates are expected when pinging a broadcast or multicast address,
     since they are not really duplicates but replies from different hosts to
     the same request.

     Damaged packets are obviously serious cause for alarm and often indicate
     broken hardware somewhere in the ping packet's path (in the network or in
     the hosts).[/I]

Browsing for remote places Konqueror does detect a Windows Workgroup (where the wireless remote adapter is plugged in).  It is supposed to display Windows (192.168.0.1) storage media, files and directories (Win folders).
This is the way that my laptop worked in the past when XP (192.168.0.2) was installed.
I cannot connect to Internet (192.168.0.1 has a gateway to 192.168.1.1) wich shares its internet connection from a wired router (192.168.1.254).

As I said before in this thread I am able to connect to Internet from my PDA (accessing  192.168.0.1)

KNetworkManager is "disconnected" yet (No network device found).
Thank you.

---

