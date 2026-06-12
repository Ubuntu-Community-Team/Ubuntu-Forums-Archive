---
title: "wireless - losing packages"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by Thiago Cesar Vieira on 2007-12-10
Hi friends!

After 1 week using wireless in Ubuntu, suddenly **my connection gets bad**. Sometimes I can use normally, other losing some packages and almost all time with no wireless.

I use wireless normally in **Windows**, so my adapter and the router is working fine. My problem is in Ubuntu configuration. I use dhcp in a D-Link router with WEP 128 bits.

I followed procedure to [troubleshoot my wireless]("http://ubuntuforums.org/showthread.php?t=571188"), and listed above the results. Does anyone have already seen it before or knows the procedure to fix my problem?

**$ lspci**
[I]...
05:06.0 Network controller: Texas Instruments ACX 111 _54Mbps_ Wireless Interface
...[/I]

**$ iwlist wlan0 scanning**
[I]wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:FE:48:6E
                    ESSID:"[MY_ESSID]"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/100  Signal level=21/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s[/I]

**$ cat /etc/network/interfaces**
[I]auto lo
iface lo inet loopback

iface wlan0 inet dhcp
wireless-key s:[MY-KEY]
wireless-essid [MY_ESSID]

auto wlan0[/I]

**$ ifconfig -a**
[I]eth0 ...
lo   ...

wlan0     Link encap:Ethernet  HWaddr 00:13:46:34:D3:85  
          inet addr:192.168.0.151  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe34:d385/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3092 errors:17 dropped:0 overruns:0 frame:0
          TX packets:2802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3025914 (2.8 MB)  TX bytes:561166 (548.0 KB)
          Interrupt:16 Base address:0x8000[/I]

**$ iwconfig wlan0**
[I]wlan0     IEEE 802.11b+/g+  ESSID:"[MY_ESSID]"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:FE:48:6E   
          _Bit Rate:54 Mb/s_   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=39/100  Signal level=14/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/I]


**$ lshw -C network**
[I]  *-network:0
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wlan0
       version: 00
       serial: 00:13:46:34:d3:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.0.151 latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network:1
...[/I]


**$ sudo dhclient wlan0**
[I]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from 192.168.0.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.151 -- renewal in 579250 seconds.[/I]


After some minutes it starts to **lose packages** when I ping in router (192.168.0.1)... rate of successful packages 100% goes to 80%, 60%, 40%...

My **log files** listed bellow start logging problems...
[I]/var/log/kern.log
/var/log/messages
/var/log/syslog[/I]

[I]Dec  9 11:51:52 kernel: [ 1035.974387] acx: got IV_ICV_Failure (crypto) IRQ(s)
Dec  9 11:52:21 kernel: [ 1064.191699] wlan0: tx error 0x10, buf 05! (MSDU lifetime timeout? - try changing 'iwconfig retry lifetime XXX')
Dec  9 12:00:52 kernel: [ 1575.379976] NETDEV WATCHDOG: wlan0: transmit timed out
Dec  9 12:00:52 kernel: [ 1575.379984] wlan0: FAILED to free any of the many full tx buffers. Switching to emergency freeing. Please report!
Dec  9 12:00:52 kernel: [ 1575.380015] wlan0: tx timeout!
Dec  9 12:00:52 kernel: [ 1575.380118] wlan0: recalibrating radio
...
Dec  9 12:05:52 kernel: [ 1875.164877] wlan0: got disassoc frame with reason 4 (due to inactivity)
A cada 2segundos printa essa mensagem:
Dec  9 12:06:29 kernel: [ 1912.366504] acx: BUG: no free txdesc left[/I]


**$ iwconfig wlan0**
[I]wlan0     IEEE 802.11b+/g+  ESSID:"[MY_ESSID]"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          _Bit Rate:1 Mb/s_   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=43/100  Signal level=20/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0[/I]


**$ sudo dhclient wlan0**
[I]There is already a pid file /var/run/dhclient.pid with pid 5944
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
Trying recorded lease 192.168.0.151
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

--- 192.168.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.[/I]


**$ sudo ifconfig wlan0 down**
Stops to log errors.

**$ sudo dhclient -r wlan0**
[I]There is already a pid file /var/run/dhclient.pid with pid 6505
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.[/I]


**$sudo ifconfig wlan0 up**
Starts to log again:
[I]Dec  9 12:18:33 kernel: [ 2635.423531] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  9 12:19:10 kernel: [ 2672.586353] acx: BUG: no free txdesc left[/I]

[B]$ sudo iwconfig wlan0 essid "[MY_ESSID]"
$ sudo iwconfig wlan0 key s:[MY_KEY]
$ sudo iwconfig wlan0 mode Managed
$ sudo dhclient wlan0[/B]

[I]After last command
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:13:46:34:d3:85
Sending on   LPF/wlan0/00:13:46:34:d3:85
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/I]


**My /var/log/syslog prints**
[I]Dec  9 12:33:22 dhclient: No DHCPOFFERS received.
Dec  9 12:33:22 dhclient: No working leases in persistent database - sleeping.
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Successfully called chroot().
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Successfully dropped root privileges.
Dec  9 12:33:22 avahi-autoipd(wlan0)[6945]: Starting with address 169.254.7.33
Dec  9 12:33:23 kernel: [ 3524.796812] acx: BUG: no free txdesc left
Dec  9 12:33:26 kernel: [ 3527.294933] acx: BUG: no free txdesc left
Dec  9 12:33:27 avahi-autoipd(wlan0)[6945]: Callout BIND, address 169.254.7.33 on interface wlan0
Dec  9 12:33:27 avahi-daemon[5278]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:27 avahi-daemon[5278]: New relevant interface wlan0.IPv4 for mDNS.
Dec  9 12:33:27 avahi-daemon[5278]: Registering new address record for 169.254.7.33 on wlan0.IPv4.
Dec  9 12:33:30 kernel: [ 3531.841374] acx: BUG: no free txdesc left
Dec  9 12:33:31 avahi-autoipd(wlan0)[6945]: Successfully claimed IP address 169.254.7.33
Dec  9 12:33:32 kernel: [ 3533.338381] acx: BUG: no free txdesc left
Dec  9 12:33:34 kernel: [ 3535.836501] acx: BUG: no free txdesc left
Dec  9 12:33:37 kernel: [ 3538.334619] acx: BUG: no free txdesc left
Dec  9 12:33:39 kernel: [ 3540.832737] acx: BUG: no free txdesc left
Dec  9 12:33:41 avahi-autoipd(wlan0)[6945]: SIOCSIFFLAGS failed: Permission denied
Dec  9 12:33:41 avahi-autoipd(wlan0)[6945]: Callout STOP, address 169.254.7.33 on interface wlan0
Dec  9 12:33:41 avahi-daemon[5278]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec  9 12:33:41 avahi-daemon[5278]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:41 avahi-daemon[5278]: Withdrawing address record for 169.254.7.33 on wlan0.
Dec  9 12:33:41 avahi-daemon[5278]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:41 dhclient: receive_packet failed on wlan0: Network is down
Dec  9 12:33:41 avahi-daemon[5278]: New relevant interface wlan0.IPv4 for mDNS.
Dec  9 12:33:41 avahi-daemon[5278]: Registering new address record for 169.254.7.33 on wlan0.IPv4.
Dec  9 12:33:41 dhclient: receive_packet failed on wlan0: Network is down
Dec  9 12:33:41 avahi-daemon[5278]: Withdrawing address record for 169.254.7.33 on wlan0.
Dec  9 12:33:41 avahi-daemon[5278]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 169.254.7.33.
Dec  9 12:33:41 avahi-daemon[5278]: Interface wlan0.IPv4 no longer relevant for mDNS.[/I]


After I **restart **my machine...
[I]Dec  9 12:44:55 NetworkManager: <info>  Updating allowed wireless network lists. 
Dec  9 12:44:55 NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Dec  9 12:50:16 kernel: [  420.557064] wlan0: rx: 8 DUPs in 21 packets received in 10 secs
Dec  9 12:50:35 kernel: [  439.245000] wlan0: tx error 0x20, buf 02! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:35 kernel: [  439.245012] wlan0: tx error 0x20, buf 03! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:35 kernel: [  439.245023] wlan0: tx error 0x20, buf 04! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182437] wlan0: several excessive Tx retry errors occurred, attempting to recalibrate radio. Radio drift might be caused by increasing card temperature, please check the card before it's too late!
Dec  9 12:50:39 kernel: [  443.182450] wlan0: tx error 0x20, buf 05! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182458] wlan0: tx error 0x20, buf 06! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182468] wlan0: tx error 0x20, buf 07! (excessive Tx retries due to either distance too high or unable to Tx or Tx frame error - try changing 'iwconfig txpower XXX' or 'sens'itivity or 'retry')
Dec  9 12:50:39 kernel: [  443.182489] wlan0: recalibrating radio
Dec  9 12:50:39 kernel: [  443.229739] wlan0: successfully recalibrated radio[/I]

Finally, I tried to configure my adapter (iwconfig rate, txpower, sens, mode) but no success.


If you you have some advice, I'd like to "hear". Any words for you is much for me to understand Ubuntu better.

---

### Post by Original Brownster on 2007-12-11
Hi,
An excellent post, loads of info. 
I've found a bug filed so it's quite likely the problem rather than a config issue. 
[URL="http://sourceforge.net/tracker/index.php?func=detail&aid=1588707&group_id=75380&atid=543745"]
See this bug report[/URL]

The guy at the end thinks he had  a work around for it, maybe it'll help you.

---

### Post by Thiago Cesar Vieira on 2007-12-15
Hi Original Brownster! Thanks for your help.

The link that you posted reports one case that **IRQ of wlan-card was the same of graphic-card**. The solution was **changing the PCI-Card-Slots**.

$ lspci -vvv|grep -B 5 -i IRQ

My output shows the same IRQ from my wlan-card and ethernet.
[I]05:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to **IRQ 17**
--
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (5750ns min, 7750ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to **IRQ 17**[/I]


I tried to do this: I changed wlan-card and cleaned graphic-card's cooler. My Windows reinstalled again these 2 hardware cards and works fine - video and wirelles.

But, Ubuntu tells in boot:

[I]* Starting Powernowd...
/etc/rc2.d/S20powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: directory non existent
* CPU frequency scaling not supported [ok]
* Running local boot scripts (/etc/rc.local) [ok][/I]  <-- stop here

Actualy I don't have */sys/devices/system/cpu/cpu0/cpufreq/* directory.


I've read */usr/share/doc/powernowd/README.DEBIAN* and a lot of references in Internet. So, I tried:
[I]$ dmesg | grep power
powernow_k8: found 1 AMD Athlon 64...
powernow_k8: BIOS error_ no PSB or **ACPI** _PSS objects[/I]

My BIOS config...
[I]Power
 ACPI Suspend Type [S1&S3]
 ACPI APIC support [Enabled][/I]

[I]# powernowd
Found 1 scalable unit: __1 'cpu' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_frep: no  sch file or directory.
PowerNowd ecountered an error and could not start.[/I]

I [added the line]("http://ubuntuforums.org/showthread.php?t=103488") "p4_clockmod" to my */etc/modules*, but no success.


Booting by **Recovery Mode** has the same result.


Have someone similar problems like this?

---

### Post by Thiago Cesar Vieira on 2007-12-17
Hi all!

I couldn't solve that problem, so I reinstalled Ubuntu Gutsy, but trouble with wireless still persists...

Sometimes:
[I]NETDEV WATCHDOG: wlan0: transmit timed out
wlan0: FAILED to free any of the many full tx buffers. Switching to emergency freeing. Please report!
wlan0: tx timeout![/I]

Sometimes:
*acx: BUG: no free txdesc left*

I can't use my wireless, only wired works. In Windows wireless is working fine. Has someone an advice?


Thanks a lot!

---

