---
title: "wnda3100v2 ubuntu 13.04"
date: 2014-04-10
forum: Networking &amp; Wireless
---

### Post by fattyz on 2014-04-10
Hi all.  I spent today trying to get this wireless adapter working with no luck.  I followed 2 threads and got so I can see the driver and the hardware installed but then I am stuck.  I think this thread contains the solution  [http://av3ngr.wikispaces.com/Netgear+WNDA3100v2+USB](http://av3ngr.wikispaces.com/Netgear+WNDA3100v2+USB) 

but I am having trouble getting the commands to run in terminal.  (total noob) This command in particular 

su -c 'yum -y localinstall --nogpgcheck [http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm](http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm) [http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm](http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm)'
su -c 'yum -y install kmod-ndiswrapper' 

I have the drivers and ndiswrapper installed, windows wireless drivers sees the driver and the hardware but the USB stick won't light up.

This thread [http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173) I get to the last command - iwconfig - to check if it is working and I get the following
```

mark@markii-pc:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME-EC72"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D3:FE:EC:70   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:17  Invalid misc:39   Missed beacon:0

```

Here is a little more code the result of lsub
```

mark@markii-pc:~$ lsusb
Bus 002 Device 005: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 002 Device 002: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I DO have wireless, the laptop has wireless but it is dying and I need the netgear adapter.  I tried this morning doing this in 10.04, now I am upgraded to 13.04.

Thanks

---

### Post by cariboo on 2014-04-10
Moved to Networking & wireless

---

### Post by fattyz on 2014-04-15
So I'm back on this after having spent a week on Compiz/Emerald which was WAY more fun but ... this is important!  I was wrong about the thread above with the terminal commands I couldn't run.  After reading it again I see that I already accomplished all that and I have not got anything working.

Ndiswrapper (windows wireless drivers)  Installs the drivers I downloaded and installs them and sees the hardware.  Nothing else is happening.  I tried to install the drivers from the disk under wine but all the install CD does is put an icon on the desktop to run the install wizard like under windows.  This in windows tells you when to plug in the adapter and the driver sees the hardware and turns it on.  That program, though installed under wine will not start or run.

I can click on configure wireless networks, I see my network but trying to edit it will not work.  I was able to do so on a previous attempt and this did not accomplish anything anyway but it says to do so in the threads I have seen so far.

So I am stuck (though I DO have a nice shiny new installation of 14.04)  The light on the adapter is flashing now and then currently as though it felt it should be doing something,  a very hopeful sign, but I can't see any way to get it to start up or select it to provide wireless for my laptop.  I hope I have not overlooked anything too obvious and I will continue to google for additional threads.  Sometimes all it takes is a slight change in the wording and bingo!

Any suggestions greatly appreciated

---

### Post by fattyz on 2014-04-16
Found this which has terminal commands for loading the driver but no luck. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I'll keep updating this today as I should have time to work on it.  :  )

Yours

---

### Post by fattyz on 2014-04-16
Maybe if I can blacklist the driver for the built in wifi and THEN enable wireless the drivers will load.  I found this idea referenced but not exactly how to do it.  In windows both wifi adapters would (seemingly) work at the same time and I would shut off the built in one which is no longer working correctly.  Hence the wnda3100v2.

Thanks again

---

### Post by chili555 on 2014-04-16
> In windows both wifi adapters would (seemingly) work at the same time and I would shut off the built in one which is no longer working correctly. Great job, Windows. Every time I turn on my computer, I have to fiddle with things to get connected. Every. Time.[/RANT]

Let's start by blacklisting and unloading permanently (until we choose to reload it) the built-in. The first step is to identify it. Please run and post:```
sudo lshw -C network
```

---

### Post by fattyz on 2014-04-16
Thanks for your reply

*-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 70:f1:a1:27:af:68
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A ip=10.0.0.17 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d4600000-d460ffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 70:5a:b6:df:aa:a4
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:d3500000-d353ffff ioport:1000(size=128)
  *-network
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 44:94:fc:17:8c:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.59+,08/26/2009, 5.10.79.30 link=no multicast=yes wireless=IEEE 802.11g

---

### Post by chili555 on 2014-04-16
If you want to blacklist the internal, which seems to be connected right now (!!), please open a terminal and do:```
sudo -i
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r ath9k
exit
```Now is your USB working? Seeing networks? Connecting? If not, try a reboot and check again.

---

### Post by fattyz on 2014-04-16
Close!  When I try to connect the USB lights up and flashes trying to connect but fails.  :  (  I tried several times (and rebooted) and tried to configure network under ndiswrapper (graphical).  It shows another entry for my network never accessed and fails if I try to configure.

I was able to get to configure network under the wife tab in notification center but it still fails to connect.

---

### Post by chili555 on 2014-04-16
> tried to configure network under ndiswrapper (graphical).I don't understand that at all. Where or what is that? Maybe I don't have enough experience with ndiswrapper.

When you click the Network Manager icon, do you see your network? [http://www.techotopia.com/images/d/de/Ubuntu_10.10_networkmanager_menu.jpg](http://www.techotopia.com/images/d/de/Ubuntu_10.10_networkmanager_menu.jpg)  Can you click on it and try to connect? Are you challenged for your WPA2 password? When you supply it, does it try to connect?

The Dr. Gloom in me fears that you have added so many self-configurations that we will have lots to undo before we can connect smoothly.

---

### Post by fattyz on 2014-04-16
I installed ndiswrapper in Ubuntu software center which puts a tab under 'system' that says window wireless drivers (I am at the other computer so cant look at it exactly)  This launches a graphical interface to help you install the windows drivers and shows the drivers and device are present.  

Yes I see the network and yes it tries to connect and accepts the password but fails.

---

### Post by fattyz on 2014-04-16
Ndiswrapper installed from software center puts a graphical interface called windows wireless drivers under system in the main menu (I am at the other computer so can't look at it)  This lets you select and install the driver and tells you if the hardware is present and driver installed.  Yes it sees the network takes the password and tries to connect but fails.

---

### Post by chili555 on 2014-04-16
> Yes it sees the network takes the password and tries to connect but fails.Let's see if there any clues as to what's going wrong. ```
dmesg | grep ndis
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20
```Ideally, run as you are trying to connect and with any ethernet cable detached.

---

### Post by fattyz on 2014-04-16
Can we do it with the old internet connection enabled because that first command spits out a pageload of info and I am unable to cut and paste?  (I don't know how to turn it back on)  :  )

It is saying among other stuff that the driver couldn't load because the kernel is 64bit and the windows driver isn't.

---

### Post by chili555 on 2014-04-16
If you have a reliable ethernet or tethered connection, you can hook up after you run the commands to post them. A perhaps easier way is to pump the results into a text document:```
dmesg | grep ndis  >  wifi.txt
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20  >>  wifi.txt
```Find the file wifi.txt in your user directory and paste it here.

If you have no reliable connection, transfer the file wifi.txt on a USB stick or similar to another computer.

---

### Post by fattyz on 2014-04-16
OK here is the output with the USB plugged in:

[   15.418277] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   15.425725] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   16.063020] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   16.824411] usbcore: registered new interface driver ndiswrapper
[   17.535451] ndiswrapper: interface renamed to 'wlan1'
[  878.567247] usbcore: deregistering interface driver ndiswrapper
[  878.604508] ndiswrapper: device wlan1 removed
[  878.668451] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  878.897653] ndiswrapper (wrap_pnp_start_usb_device:643): reset failed: -19
[  878.900593] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  878.900599] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[  878.901188] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[  878.910436] usbcore: registered new interface driver ndiswrapper
[  879.244091] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  879.244097] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[  879.244741] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[  891.239771] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  891.239780] ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43xx32'
[  891.240605] ndiswrapper (load_wrap_driver:103): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[  910.157984] usbcore: deregistering interface driver ndiswrapper
[  910.178482] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  910.367156] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  910.901750] ndiswrapper: interface renamed to 'wlan1'
[  910.920164] usbcore: registered new interface driver ndiswrapper
[ 1495.224516] ndiswrapper: device wlan1 removed
[ 2842.627178] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[ 2843.522202] ndiswrapper: interface renamed to 'wlan1'
(standard input):Apr 16 09:30:20 markii-pc NetworkManager[732]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 09:30:39 markii-pc NetworkManager[732]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 09:31:47 markii-pc NetworkManager[732]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:07:10 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:08:43 markii-pc NetworkManager[781]:       interface-parser: parsing file /etc/network/interfaces
(standard input):Apr 16 11:08:43 markii-pc NetworkManager[781]:       interface-parser: finished parsing file /etc/network/interfaces
(standard input):Apr 16 11:09:33 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:11:14 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:12:11 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:14:15 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:21:13 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:24:28 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:29:11 markii-pc NetworkManager[732]:       interface-parser: parsing file /etc/network/interfaces
(standard input):Apr 16 11:29:11 markii-pc NetworkManager[732]:       interface-parser: finished parsing file /etc/network/interfaces
(standard input):Apr 16 11:30:08 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:42:04 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:44:38 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HPE710n.803250'.
(standard input):Apr 16 11:45:34 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:48:37 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:50:55 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 09:30:20 markii-pc NetworkManager[732]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 09:30:39 markii-pc NetworkManager[732]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 09:31:47 markii-pc NetworkManager[732]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:07:10 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:08:43 markii-pc NetworkManager[781]:       interface-parser: parsing file /etc/network/interfaces
(standard input):Apr 16 11:08:43 markii-pc NetworkManager[781]:       interface-parser: finished parsing file /etc/network/interfaces
(standard input):Apr 16 11:09:33 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:11:14 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:12:11 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:14:15 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:21:13 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:24:28 markii-pc NetworkManager[781]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:29:11 markii-pc NetworkManager[732]:       interface-parser: parsing file /etc/network/interfaces
(standard input):Apr 16 11:29:11 markii-pc NetworkManager[732]:       interface-parser: finished parsing file /etc/network/interfaces
(standard input):Apr 16 11:30:08 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:42:04 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:44:38 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HPE710n.803250'.
(standard input):Apr 16 11:45:34 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:48:37 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
(standard input):Apr 16 11:50:55 markii-pc NetworkManager[732]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'HOME-EC72'.
Apr 16 12:16:16 markii-pc kernel: [ 2843.522202] ndiswrapper: interface renamed to 'wlan1'
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): driver does not support SSID scans (scan_capa 0x00).
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): using WEXT for WiFi device control
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): new 802.11 WiFi device (driver: 'ndiswrapper' ifindex: 6)
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/4
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): bringing up device.
Apr 16 12:16:16 markii-pc kernel: [ 2843.531222] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): preparing device.
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): deactivating device (reason 'managed') [2]
Apr 16 12:16:16 markii-pc kernel: [ 2843.536028] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Apr 16 12:16:16 markii-pc NetworkManager[732]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/net/wlan1, iface: wlan1)
Apr 16 12:16:16 markii-pc NetworkManager[732]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1) supports 1 scan SSIDs
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): supplicant interface state: starting -> ready
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Apr 16 12:16:16 markii-pc wpa_supplicant[788]: wlan1: Reject scan trigger since one is already pending
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1): supplicant interface state: ready -> disconnected
Apr 16 12:16:16 markii-pc NetworkManager[732]: <info> (wlan1) supports 1 scan SSIDs
Apr 16 12:16:26 markii-pc NetworkManager[732]: <info> (wlan1): supplicant interface state: disconnected -> inactive

---

### Post by chili555 on 2014-04-16
> ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BNot good. Let's see:```
ls /etc/ndiswrapper
```Thanks.

---

### Post by fattyz on 2014-04-16
Thank you,  that comes back bcmn43xx64

Thanks

---

### Post by chili555 on 2014-04-16
So this should now be gone:> ndiswrapper (load_sys_files:200): couldn't prepare driver 'bcmn43x[COLOR="#FF0000"]x32[/COLOR]'Please reboot so we have a clean slate and let's see the log again:```
dmesg | grep ndis  >  wifi2.txt
cat /var/log/syslog | grep -e wlan -e etwork | tail -n20  >>  wifi2.txt
```

---

### Post by fattyz on 2014-04-16
Still tries to connect but fails.  Here is the log.  The entry for the 32bit driver is gone.

[   15.845059] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   15.879199] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   17.591773] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   17.860438] usbcore: registered new interface driver ndiswrapper
[   17.888853] ndiswrapper: interface renamed to 'wlan1'
Apr 16 19:15:18 markii-pc dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15 (xid=0x6caac1a)
Apr 16 19:15:35 markii-pc NetworkManager[755]: <warn> (wlan1): DHCPv4 request timed out.
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2127
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> Activation (wlan1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> Activation (wlan1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> (wlan1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 16 19:15:35 markii-pc NetworkManager[755]: <warn> Activation (wlan1) failed for connection 'HOME-EC72 1'
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> Activation (wlan1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> (wlan1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> (wlan1): deactivating device (reason 'none') [0]
Apr 16 19:15:35 markii-pc avahi-daemon[454]: Withdrawing address record for fe80::4694:fcff:fe17:8c68 on wlan1.
Apr 16 19:15:35 markii-pc avahi-daemon[454]: Leaving mDNS multicast group on interface wlan1.IPv6 with address fe80::4694:fcff:fe17:8c68.
Apr 16 19:15:35 markii-pc avahi-daemon[454]: Interface wlan1.IPv6 no longer relevant for mDNS.
Apr 16 19:15:31 markii-pc wpa_supplicant[835]: message repeated 19 times: [ wlan1: WPA: EAPOL-Key Replay Counter did not increase - dropping packet]
Apr 16 19:15:35 markii-pc wpa_supplicant[835]: wlan1: CTRL-EVENT-DISCONNECTED bssid=00:1d:d3:fe:ec:70 reason=3 locally_generated=1
Apr 16 19:15:35 markii-pc NetworkManager[755]: <info> (wlan1): supplicant interface state: completed -> disconnected
Apr 16 19:15:37 markii-pc avahi-daemon[454]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::4694:fcff:fe17:8c68.
Apr 16 19:15:37 markii-pc avahi-daemon[454]: New relevant interface wlan1.IPv6 for mDNS.
Apr 16 19:15:37 markii-pc avahi-daemon[454]: Registering new address record for fe80::4694:fcff:fe17:8c68 on wlan1.*.
Apr 16 19:15:38 markii-pc wpa_supplicant[835]: wlan1: Reject scan trigger since one is already pending

---

### Post by chili555 on 2014-04-17
> I can click on configure wireless networks, I see my network but trying to edit it will not work. Do you have any settings in Network Manager that you added yourself in an attempt to get the device to connect? Typically, you need none. If you have any, please remove them. Usually, the defaults are perfectly fine. 

Have you added any settings here?```
cat /etc/network/interfaces
```If so, please edit the file down to:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```If you make changes in either or both places, restart NM:```
sudo service network-manager restart
```If all goes as we expect, the pop-up will report that you are now disconnected and then connected. You may have to look for your network and connect again: [http://nfgk.files.wordpress.com/2013/08/network-manager.jpg?w=540](http://nfgk.files.wordpress.com/2013/08/network-manager.jpg?w=540)

Your device shows every sign of wanting to connect as expected.

---

### Post by fattyz on 2014-04-17
Well, it's working.  I can't really believe this but I'll try to explain it.  The only thing I can figure is when I blacklist the old driver and select the new one and hardware a new network gets created?  (Or when it gets installed, I'm not sure.)  If not, I am now logged into my neighbors router, but I doubt it because it took the password for my Xfinity account.  (when I opened the browser I was asked for my Xfinity password something I have never seen before)  While we were doing all this I kept looking at the list of available wireless networks and I thought I was seeing different ones, ones I was not used to. I also noticed that it was creating a duplicate of my original network name.  So I was thinking about it last night and I wondered if it was making up new networks,  so this morning after I read your post I selected one called Xfinity and clicked on it (after I disabled the default driver) and Viola!  Connected right away.  It will NOT however connect to my old network name.  So I put a password on the Xfinity network and I am either all set or I locked one of my neighbors out of their router.

I will look to see if I can check the hardware address for the router just in case...

Update  When I check the connection information the interface is called (wlan) and everytime I connect a new network name appears xfinity , 2 etc, and security gets disabled.  
Update  After fooling around with it, yes that's it.  A new network name appears.  Even the cell phones see it.  I have no idea how or why.  I know it's my router though because to be sure, I walked upstairs and unplugged it, no doubt about it.  When I used the USB under windows, I connected to my regular network.  

Yours

---

### Post by chili555 on 2014-04-17
I am very glad it's working by whatever means. Please check back if we can help you further.

Have fun!

---

### Post by fattyz on 2014-04-17
Thank you so much for the time you spent on that, I had read many of your posts while I was searching for an answer and knew when I saw your reply that now there'd be a good chance of getting to the bottom of it.  As you would expect, the connection is much faster.

Thanks again,

Yours

---

### Post by fattyz on 2014-04-21
I have been on the phone with Xfinity and it seems I am not quite out of the woods (solved) yet.  The Xfinity wifi connection I am using is an unsecured wifi hotspot the router creates.
I need to connect to my home network with the password.  Before I let those guys do a factory reset on my router and rename the network, shoud I try some of the kernel magic I was reading about in some of these other posts?  

[http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839)

Thanks

---

### Post by chili555 on 2014-04-21
> shoud I try some of the kernel magic I was reading about in some of these other posts? Which specific post do you have in mind? What I read was several different devices that are *not* the same as yours.

---

### Post by fattyz on 2014-04-21
Post # 6 which I think makes a change to the kernel.  The thing is we never really connected to my network, only to the wifi hot spot.  It was just a thought I had as I had to reinstall everything the other night and did a little more searching and noticed some of these posts.  They may be unrelated or device specific.

Thanks

---

### Post by chili555 on 2014-04-21
> **fattyz said:**
> Post # 6 which I think makes a change to the kernel.  
ThanksPost #6 is for a Realtek device. I believe, under the silicon, that yours is a Broadcom. > ;;
;; Copyright 1998-2009, Broadcom Corporation.
;; All Rights Reserved.
;;
;; This is UNPUBLISHED PROPRIETARY SOURCE CODE of Broadcom Corporation;
;; the contents of this file may not be disclosed to third parties, copied or
;; duplicated in any form, in whole or in part, without the prior written
;; permission of Broadcom Corporation.
;;
<snip>Believe me, if there was the slightest chance to use a native driver and not ndiswrapper, I'd be all over it. 

What can we (read: you!) do to test and confirm that it will attach to your encrypted network?

---

### Post by fattyz on 2014-04-21
Since it never even got to asking for the password, I don't know.  I will start searching on the Xfinity site and see if I can get anyone over there who has dealt with this.  I'm sure people have!  I did not realize there were no more options.  Reading those other posts (not carefully enough) led me to hope there were other things to try.

Edit: This explains a lot. [http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2](http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2)

Thanks again.

---

### Post by fattyz on 2014-04-25
"What can we (read: you!) do to test and confirm that it will attach to your encrypted network? "

How about buy a new one?  (total out of pocket after selling the netgear wnda3100v2 should be about 8 bucks)

Well, I did.  I got my Panda Wireless 300mps 2.4 GHz wireless adapter today and plugged it in and after I blacklisted the ath9k it started itself up right away.  AND
According to connection information I am only getting about the same speed as the old laptop wireless ath9k?  Also according to connection information, no driver is loaded. Is it possible loading the Panda driver will increase the speed over the native driver?  If so, would you be willing to give me a hand loading it?  

Thanks again

---

### Post by chili555 on 2014-04-25
Let's see what's loading and not loading. Please post:```
lsusb
lsmod
```I'm always willing to lend a hand for you!

---

### Post by fattyz on 2014-04-25
Thanks!

lsusb
Bus 002 Device 003: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 002 Device 006: ID 05ac:12a8 Apple, Inc. 
Bus 002 Device 005: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 002 Device 004: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Module                  Size  Used by
ipheth                 13448  0 
ctr                    13049  1 
ccm                    17773  1 
nls_utf8               12557  1 
isofs                  39835  1 
nvram                  14411  0 
arc4                   12608  2 
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              626489  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
joydev                 17381  0 
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  0 
bnep                   19624  2 
coretemp               13435  0 
rfcomm                 69160  0 
psmouse               102222  0 
serio_raw              13462  0 
bluetooth             395423  10 bnep,rfcomm
snd_hda_codec_realtek    61438  1 
lpc_ich                21080  0 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
i915                  783485  3 
soundcore              12680  1 snd
drm_kms_helper         52758  1 i915
drm                   302817  4 i915,drm_kms_helper
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi
i2c_algo_bit           13413  1 i915
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
binfmt_misc            17468  1 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 52616  0 
ahci                   25819  3 
libahci                32168  1 ahci
hid                   106148  2 hid_generic,usbhid
atl1c                  46086  0

---

### Post by chili555 on 2014-04-26
As we see here, the driver *is* loading:> rt2800usb 27034 0 
rt2x00usb 20742 1 rt2800usb
rt2800lib 89076 1 rt2800usb
rt2x00lib 55307 3 rt2x00usb,rt2800lib,rt2800usb
mac80211 626489 3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211 484040 2 mac80211,rt2x00libI also see no conflicting wireless drivers loading. You did a fine job with your blacklist.

Tell me more about your speeds. What are you getting and what do you expect? What does this say?```
iwconfig
```Is your router capable of N speeds?

---

### Post by fattyz on 2014-04-26
No my router has only 2 settings. 802.11 g/n or b/g/n.  Switching to b/g/n stopped the connection speed from fluctuating.  (The new router like the ath9k would swing from 50 mbs to 0)  I talked to the manufacturer and they said Comcast might give me a router that would allow me to set to 802.11 n (only) to get speeds over 150 mbs.  Right now I have a constant speed of about 39 mbs set on 802.11 b/g/n.  I am pretty sure the laptop router will give me about the same though I have not tested it on the b/g/n setting.  I thought maybe their driver would give me a speed boost but it looks like I probably have all I can get.  Can't  really go wrong for 20 bucks (that includes shipping.)

 iwconfig
wlan2     IEEE 802.11bgn  ESSID:"HOME-EC72"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:D3:FE:EC:70   
          Bit Rate=26 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:836  Invalid misc:320   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.

---

### Post by chili555 on 2014-04-26
You might have a look at the router settings. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, since your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/rc.local
```Right above the line exit 0, add the line:```
iw reg set IS
```Proofread carefully, save and close gedit. 

Any improvement?

---

### Post by fattyz on 2014-04-26
Ok, making the change to AES let the speeds jump as high as 130mbs when I was sitting up by the router.  Now the speed is bouncing a little but lots of that is upwards, happily.  I was on ch 11 already manual and the MHz adjustment I don't see or I don't have.  If I follow correctly the rest of you post you want my country code to be correct?  I think it is, which means I don't have to add that line above exit 0?  Pardon me if I did not understand.  

Right now I would say the adjustments you suggested made quite a lot of improvement.

sudo iw reg get
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

---

### Post by chili555 on 2014-04-26
> sudo iw reg get
country US:You are all set; no changes needed in /etc/rc.local.

I'm glad it's working well.

---

### Post by fattyz on 2014-04-27
Thanks again for all your help I'll mark this solved.

Yours

---

