---
title: "So Close!!!  Wireless connects, but not to internet..."
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by kelly777 on 2007-08-31
Hello all,

I'm new to Ubuntu (Feisty) and Linux, so please excuse my noobness.

I have installed a wireless USB "card", set up ndiswrapper, and set up the drivers for the wireless.  I can see my wireless network and connect.  However, I cannot connect to the internet and pinging times out.

Some questions:
When logging into the WPA wireless, should the key be entered as 1234567890 or 12:34:56:78:90?
When I look at the connection information, everything is listed as 0.0.0.0.  How can this be fixed for DHCP?

Below is some data from the terminal.  Thanks SO MUCH for helping me out!!!  I've spent hours on this!




kelly777@kelly777-desktop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@02:0c.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:e6:72:1b
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: ioport:ec00-ec7f iomemory:feeffc00-feeffc7f irq:11
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:60:b3:11:cd:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=2Wire,04/08/2004, 2.3.1.3 link=yes multicast=yes wireless=IEEE 802.11g



kelly777@kelly777-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0
kelly777@kelly777-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"kelly777-UVERSE"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



kelly777@kelly777-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 03 - Address: 00:1B:5B:68:2B:49
                    ESSID:"kelly777-UVERSE"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=1
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  



kelly777@kelly777-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp



kelly777@kelly777-desktop:~$ cat /etc/modprobe.d/ndiswrapper
install pci:v00001260d00003886sv00000003sd00001630bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v00001260d00003886sv00000004sd00001630bc*sc*i* /sbin/modprobe ndiswrapper
install pci:v00001260d00003886sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
install usb:v1630p0005d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
alias wlan0 ndiswrapper
kelly777@kelly777-desktop:~$ cat /etc/resolv.conf
kelly777@kelly777-desktop:~$

---

### Post by Darkhack on 2007-08-31
Your /etc/network/interfaces file is missing a lot of information.  DHCP will assign you an IP and DNS server, but you need to enter the router information yourself.  You also stated that you use WPA.  Please show the output of /etc/wpa_supplicant.conf.  Here is how your interfaces file should look, but replace the IP address with the proper information for your particular router.

[QUOTE=/etc/network/interfaces]
auto wlan0
iface wlan0 inet dhcp
netmask 255.255.255.255
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
essid YOUR_SSID
wireless-essid YOUR_SSID
wpa-ssid YOUR_SSID
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
wpa-key-mgmt WPA-PSK
[/QUOTE]

---

### Post by kelly777 on 2007-08-31
This could be the problem...I have no /etc/wpa_supplicant.conf file!  Can I create one? 

Thanks for your assistance!

Edit: I tried...sudo apt-get install wpasupplicant and the system indicates the newest version is already installed.

---

### Post by Darkhack on 2007-08-31
Follow this guide for instructions on how to setup WPA.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by kelly777 on 2007-08-31
I added the following info to /etc/network/interfaces but still have the same problem.  Also did the install wpasupplement, but it was already installed.

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid kelly777-UVERSE
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk #kelly777s loooong hex key

thanks!

---

### Post by Darkhack on 2007-09-01
You're still missing some information.  Append the following to your interfaces file and edit the values as needed for your setup.  DHCP will grab an address and DNS server, but you need to specify your router information first.  Once this is done, do "sudo /etc/init.d/networking restart" and then paste the output of iwconfig here.

> 
netmask 255.255.255.255
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1
essid YOUR_SSID
wireless-essid YOUR_SSID
wpa-conf /etc/wpa_supplicant.conf


---

### Post by kelly777 on 2007-09-01
Each time I run iwconfig it's different...

Sometimes the ESSID is correct, sometimes it's off/any.  The Access point alternates between the correct id and 'not-associated' as well.  

The change seems to occur every few seconds.

Any ideas?

I've added the additional detail into the interfaces file as well as trying static vs dhcp.

Thanks!

---

### Post by kelly777 on 2007-09-01
Darkhack,

Thanks for all the help!  I am now 'on the internets'.  

I guess it was a combo of things, and I'm not really sure what it was.  Eventually, I went back to dhcp, and entered my WPA key into the network manager gui.

I'm now scared to restart the pc!

Thanks again.

---

### Post by Darkhack on 2007-09-01
> **kelly777 said:**
> I'm now scared to restart the pc!

You shouldn't have any problems.  All the configuration files are saved.  If for any reason you do restart and it doesn't connect then do

sudo /etc/init.d/networking restart

And Ubuntu will re-read the configuration files and restart the network for you.  Although I presume you should be just fine.

---

