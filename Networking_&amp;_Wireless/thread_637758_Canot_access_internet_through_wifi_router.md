---
title: "Canot access internet through wifi router"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by tsimmi on 2007-12-11
I recently bought a wifi modem router to build up my network.
It's a micra digital fd57630.
When i connect it through ethernet it works just fine but by wireless it only shows the network and when i try to connect to it, nothing happens. It takes a lot of time and in the end do not connect.
I do not have WPA or WPE enabled but I am filtering the MAC addresses and already have putted the address from this machine (Vaio laptop C1ZB).
In windows everything works fine.

Can anyone help me?
Thanks

---

### Post by Original Brownster on 2007-12-11
Hi,
It's a good idea to start with encryption off until you get it working.

First off we need to know what wireless card/chipset you have in the laptop. open a terminal window for the following commands

try
$lshw -C network
or 
$sudo lspci -v
and look for an entry for your wireless card.

let us know what you find.

Next we need to know does ubuntu load a driver for it, you can see this in the output of lshw above I seem to remember but if not by entering:

$iwconfig

if your system reports a wireless card then a driver is loaded, that simple

if your card has a driver loaded then
can your laptop see your wireless AP ?

$sudo iwlist scan

will return a list of AP's in range and hopefully yours will show up.

This should get you  going, post back the output of the above commands and let us know how you get on.

---

### Post by Existentialist on 2007-12-11
Another thing to check is that you put both the wired and wireless mac addresses to be allowed in the routers settings.

---

### Post by tsimmi on 2007-12-12
Hi!
The result of the first command is:

```
 *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:60:e7:55
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:77:80:99
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=172.17.11.166 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
```

In the iwconfig I got:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"eduroam"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0E:84:D9:55:30   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/100  Signal level=-63 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:169  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8439   Missed beacon:0


```

sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:12:BF:19:89:A7
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=98/100  Signal level=-27 dBm  Noise level=-27 dBm
                    Extra: Last beacon: 100ms ago

```

Thank you very much!

---

### Post by Original Brownster on 2007-12-17
Hi,
look at the results of 'lshw -C network' , see that you have an entry for wireless, PRO/Wireless 3945ABG and further down you can see the driver loaded, ipw3945 all good so far, we know the chipset and a driver is loaded.

iwconfig shows eth1 is your wireless device, its currently configured to connect to an AP with the name  ESSID:"eduroam" note the mac address of the access point as well:  Access Point: 00:0E:84:D9:55:30 

and running iwlist scan has showed that your card can see just one wireless network named ESSID:"WLAN" witha mac address of  00:12:BF:19:89:A7 it also tells us that encryption is off.

so with all this info we know that your card at least appears to be working and you can see one wireless network (AP), is this your AP?  
If so you should be able to go into the tool network-manager and see a wireless device in the list (eth1) by clicking on this you should be able to set the properties to your AP, set the name (ESSID or SSID) to WLAN with encryption off and it should connect.

if not open a terminal and do:
iwconfig
has the essid changed to WLAN? if not we can do it manually,
look at the man page for iwconfig 
man iwconfig
will give you more info however you can set the essid
sudo iwconfig eth1 essid WLAN and restart networking with command
sudo /etc/init.d/networking restart

if your still having problems, look through /var/log/syslog
cat /var/log/syslog
for any entries pertaining to this wireless device, 

let us know how you get on. If im online you can always PM me.

---

### Post by lintoon on 2007-12-17
I had a similar issue.  Wireless worked in XP but didnt work in ubuntu (gutsy).   
I turned off mac filtering and it worked.  I then re-enabled mac filtering and it worked.  On my router I can select my wireless mac address from a list which the netgear router detects.  One thing I did notice though is the name was different.  Eg my laptop is called Tosh in windows and Toshub in ubuntu.

So, for me the mac address with the name Tosh didn't work when booted into ubuntu.  Changed it to Toshub and it worked.

---

