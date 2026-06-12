---
title: "No wireless after Intrepid Ibex upgrade"
date: 2008-12-02
forum: Networking &amp; Wireless
---

### Post by gilesroberts on 2008-12-02
Dear All,

Wireless has worked flawlessly on my laptop (Sony Vaio VGN-TX3XP) since I installed Ubuntu on it many moons ago.  I've only ever had to go into the graphical network manager and add my wireless keys.  However after upgrading to Intrepid Ibex I'm not getting any joy despite spending hours trawling the Ubuntu forums.  I'm no longer seeing any network interfaces in the graphical network manager.  Initially even my wired connection didn't work but I managed to resolve that by adding the following lines to my /etc/network/interfaces file:

auto eth0
iface eth0 inet dhcp

However doing the same for what I believe is my wireless adaptor didn't get me connected:

auto eth1
iface eth1 inet dhcp



The following is an output from my network restart:

/etc/init.d/networking restart
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 6420
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:a9:3e:d6:94
Sending on   LPF/eth0/00:13:a9:3e:d6:94
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wmaster0.pid with pid 6553
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:a9:3e:d6:94
Sending on   LPF/eth0/00:13:a9:3e:d6:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.65 from 192.168.1.1
DHCPREQUEST of 192.168.1.65 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.65 from 192.168.1.1
bound to 192.168.1.65 -- renewal in 42324 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface wmaster0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
SIOCSIFFLAGS: Operation not supported
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: Operation not supported
SIOCSIFFLAGS: Operation not supported
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
receive_packet failed on wmaster0: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 16
send_packet: Network is down
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[wmaster0]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[wmaster0]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[wmaster0]: waiting for interface wlan0 before doing NFS mounts
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
   ...done.
gilesroberts@gilesvaioubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 6995
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:a9:3e:d6:94
Sending on   LPF/eth0/00:13:a9:3e:d6:94
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
Ignoring unknown interface wmaster0=wmaster0.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:13:a9:3e:d6:94
Sending on   LPF/eth0/00:13:a9:3e:d6:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.65 from 192.168.1.1
DHCPREQUEST of 192.168.1.65 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.65 from 192.168.1.1
bound to 192.168.1.65 -- renewal in 35811 seconds.
 * if-up.d/mountnfs[eth0]: waiting for interface eth2 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface ath0 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface wlan0 before doing NFS mounts
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
wlan0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up wlan0.
   ...done.



Output from lspci

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)



Output from iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



lsmod | grep "iwl3945"
iwl3945                98804  0 
rfkill                 17176  2 iwl3945
mac80211              216820  1 iwl3945
led_class              12164  1 iwl3945
cfg80211               32392  2 iwl3945,mac80211



lshw -C network
[sudo] password for gilesroberts: 
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:be:2e:0c
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: PRO/100 VM Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:3e:d6:94
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.65 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:2d:14:74:34:8c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



So I'm guessing the big problem from lshw is that my wireless card is showing as disabled.  I can't for the life of me figure out how to enable it.  I'm hoping somebody can help me.

Regards Giles.

---

### Post by cdtech on 2008-12-02
Check out this same issue regarding the iwl3945 driver:
[http://ubuntuforums.org/showthread.php?p=4611920](http://ubuntuforums.org/showthread.php?p=4611920)

---

### Post by gilesroberts on 2008-12-02
Thanks.  I did look at that post earlier.

Following issuing the modprobe commands, doing the ifconfig simply produced another error message:

ifconfig eth1 up
SIOCSIFFLAGS: No such file or directory

Having had a search on other linux forums, they're alternatively suggesting faulty firmware or firmware in an incorrect location.  How do I check the above issues?

Regards Giles.

---

### Post by gilesroberts on 2008-12-03
Here's what I believe are the relevant lines from my dmesg:



dmesg
[sudo] password for gilesroberts: 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-10-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Fri Nov 21 12:00:22 UTC 2008 (Ubuntu 2.6.27-10.20-generic)
[    0.000000] BIOS-provided physical RAM map:
....
....
[ 9923.816609] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 9923.818377] firmware: requesting iwlwifi-3945-1.ucode
[ 9923.d823217] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[ 9923.823233] iwl3945: Could not read microcode: -2
[10252.971979] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[10252.973763] firmware: requesting iwlwifi-3945-1.ucode
[10252.978578] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[10252.978594] iwl3945: Could not read microcode: -2



Now searching for iwlwifi-3945

Matches for iwlwifi-3945:

    /lib/firmware/2.6.20-16-386/iwlwifi-3945.ucode
    /lib/firmware/2.6.22-14-386/iwlwifi-3945-1.ucode
    /lib/firmware/2.6.22-14-386/iwlwifi-3945.ucode
    /lib/firmware/2.6.24-21-386/iwlwifi-3945-1.ucode
    /lib/firmware/2.6.24-21-386/iwlwifi-3945.ucode



I don't appear to have any in the folder /lib/firmware/2.6.27-10-generic/ which is the version that dmesg says it's loading.  Is this correct?

---

### Post by gilesroberts on 2009-02-01
Some more information:

As you can see from the lshw listing above, the wireless card appears to have the id of wmaster0.  Looking at the output from iwconfig, as near as I can make out, the wireless card has an id of eth1.  Is this normal?  Is this what my problem is?  Also none of my network connections show up in any of the GUI networking tools.  Although my wired connection (eth0) works fine.

Another bit of info, I can issue the command iwconfig eth1 essid <mynetworkid> and then iwconfig returns with the essid named as <mynetworkid>.  Does this mean that my wireless card has actually connected to my router?  Or is this just configuration info?  Unfortunately, it doesn't return with an ip address.  :(

Please help me.  I've been struggling along without wireless on my laptop for a few months now.  I know the hardware is fine as it connects ok under Windows.

---

### Post by thenewcrowd on 2009-02-01
When i upgraded to Intrepid i had a number of issues related to this, the first thing i did is reinstall my network manager.  With my live cd install the wireless never worked off the bat.  the other ussue is (with my ibm) that the wireless on/off button is miss-handled and does not work currently.  Its possible for you to have one of those 2 issues or a bad driver.  You could get your hands dirty and try and code it to work.. or its possible if you know where to find the wireless driver you can use ndiswrapper to use your windows driver for it... sorry for the non-specific answer.  but alteast ya got an idea where to go...

---

