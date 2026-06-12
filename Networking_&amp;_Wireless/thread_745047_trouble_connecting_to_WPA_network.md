---
title: "trouble connecting to WPA network"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by equity on 2008-04-04
I often got trouble trying to connect to wireless networks using nm-applet, so I decided to use the CLI in the future to connect to networks using this guide:

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Unfortunately I do not know exactly how the wpasupplicant wants my driver to be named, I tried "ipw" and "ipw3945", but nothing worked for me.

Here is my CLI in- and output:

[B]marcello@G1-AP021C:~$ sudo ifconfig eth1 down
marcello@G1-AP021C:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

eth1: unknown hardware address type 801
eth1: unknown hardware address type 801
Listening on LPF/eth1/
Sending on   LPF/eth1/
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
marcello@G1-AP021C:~$ sudo wpa_supplicant -w -D ipw -i eth1 -c /etc/wpa_supplica
nt.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_
interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=11):
     49 74 61 6c 69 61 6e 57 4c 41 4e                  ItalianWLAN     
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
pairwise: 0x8
group: 0x8
Line 11: network block was not terminated properly.
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout
marcello@G1-AP021C:~$ sudo ifconfig eth1 up
marcello@G1-AP021C:~$ sudo ifconfig eth1 mode managed
mode: Unknown host
ifconfig: `--help' gives usage information.
marcello@G1-AP021C:~$ sudo iwconfig eth1 mode managed
marcello@G1-AP021C:~$ dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
marcello@G1-AP021C:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
marcello@G1-AP021C:~$ [/B]

Does anyone know what is the trouble? I tried ipw and ipw3945 as driver name. The command "lshw -C network" said "ipw3945" were the driver name. But none worked...

Thanks in advance for any help.

---

### Post by kevdog on 2008-04-04
Try wext as the driver and if you could acutally post what you are typing with the wpa_supplicant command and the wpa_supplicant.conf file it would be appreciated.

---

### Post by equity on 2008-04-04
This is what I have in my text file /etc/wpa_supplicant.conf

[B]ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="my_essid_in_quotes"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="my_wpa_psk_key_in_quotes"
        pairwise=TKIP
        group=TKIP[/B]

Sorry the question... but how do I change my driver to wext? At the command line I cannot purge my driver with apt-get or aptitude and in the Restricted Drivers Manager I can only disable my ipw driver, that is all.

---

### Post by kevdog on 2008-04-04
Arent you typing something like

wpa_supplicant -Dwext -c...... (etc)
at the command line?

---

### Post by equity on 2008-04-04
No, I did not see you mention something like that in your tutorial. And why shall I write something including "wext" when I use "ipw"? The point is I am new to Ubuntu and it installed the ipw driver automatically so this is the one I am using at the moment...

---

### Post by equity on 2008-04-05
I think my exact problem is: How does wpa_supplicant want to hear my WLAN driver's name??
In the manual is cited that ipw is for example for the Intel Pro/Wireless 2200, an older version of my wlan adapter. The command "lshw -C network" calls my driver "ipw3945" but wpa_supplicant says this driver is unsupported...

What to do?

---

### Post by kevdog on 2008-04-05
Try wext -- its a catchall for all other drivers

---

### Post by equity on 2008-04-06
Okay, I tried it again telling the wpa_supplicant my driver were "wext", it still does not work...

Here is what stands in my text file:

[B]ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="my_essid_in_quotes"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="my_wpa-psk_key_in_quotes"
        pairwise=TKIP
        group=TKIP[/B]

and here is all my CLI in- and output:

[B]user@G1-AP021C:~$ sudo ifconfig eth0 down
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:ef:d8:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.
1.67 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:d2:69:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1
 firmware=14.2 1:0 () latency=0 module=ipw3945 multicast=yes wireless=unassociat
ed
user@G1-AP021C:~$ 
user@G1-AP021C:~$ 
user@G1-AP021C:~$ gksu gedit /etc/wpa_supplicant.conf
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo ifconfig eth1 down
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant
.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl
_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=10):
     47 65 72 6d 61 6e 57 4c 41 4e                     my_essid      
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
pairwise: 0x8
group: 0x8
Line 11: network block was not terminated properly.
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo ifconfig eth1 up
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo iwconfig eth1 mode managed
user@G1-AP021C:~$ 
user@G1-AP021C:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:19:d2:d2:69:00
Sending on   LPF/eth1/00:19:d2:d2:69:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@G1-AP021C:~$ [/B]

---

### Post by equity on 2008-04-06
what is on? I am sure that the essid and the key is written correctly (actually case matching).

Who knows this phenomenon???

---

### Post by kevdog on 2008-04-06
Please look at your output and think about it:

 *-network DISABLED
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth1
version: 02
serial: 00:19:d2:d2:69:00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1

DISABLED is not a good sign.

---

### Post by equity on 2008-04-06
Yes, but this was before. I later enabled it after setting all this stuff with dhclient etc. up. This should not be the problem.

---

### Post by kevdog on 2008-04-06
Could you show me a lshw statement that proves the network is up?

---

### Post by kevdog on 2008-04-07
Ok, with the device up can you show

iwlist scan

---

### Post by equity on 2008-04-07
This is strange. My WLAN route is 2 meters away from my notebook, the SSID is definitely broadcast. airodump-ng shows me that from all APs near by is my connectivity to my route the best one.
Why does iwlist scan not find my AP??

marcello@G1-AP021C:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:5B:BF:91:B7
                    ESSID:"berkan"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-90 dBm  Noise level=-90 dBm
                    Extra: Last beacon: 1056ms ago

marcello@G1-AP021C:~$

---

### Post by kevdog on 2008-04-07
Either reboot the router or your computer -- something is strange -- I cant answer why its not showing up.  ESSID needs to be broadcast, b/g network.  Band 1-12

---

### Post by equity on 2008-04-07
Do you mean channel 1-12 with band 1-12?? If "yes" that is the problem. I set my AP to channel 13.

---

### Post by kevdog on 2008-04-07
Try a different channel like 1.

---

### Post by equity on 2008-04-07
Okay, I cannot get that this was the prolem. I switched the channel to 11 and now "iwlist scan" finds my AP. But I still cannot connect and the wpa_supplicant says that he cannot read my conf file...


[B]marcello@G1-AP021C:~$ 
marcello@G1-AP021C:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:19:5B:BF:91:B7
                    ESSID:"berkan"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=42/100  Signal level=-84 dBm  Noise level=-84 dBm
                    Extra: Last beacon: 2012ms ago
          Cell 02 - Address: 00:13:49:EE:DA:FA
                    ESSID:"GermanWLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=71/100  Signal level=-63 dBm  Noise level=-63 dBm
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1728ms ago

marcello@G1-AP021C:~$ 
marcello@G1-AP021C:~$ 
marcello@G1-AP021C:~$ sudo ifconfig eth0 down[/B]





[B]marcello@G1-AP021C:~$ sudo wpa_supplicant -w -Dwext -ieth1 -c/etc/wpa_supplicant
.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl
_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='/var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=10):
     47 65 72 6d 61 6e 57 4c 41 4e                     GermanWLAN      
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=15): [REMOVED]
pairwise: 0x8
group: 0x8
Line 11: network block was not terminated properly.
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 11: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
Failed to add interface eth1
Cancelling scan request
Cancelling authentication timeout
[/B]

---

### Post by kevdog on 2008-04-07
Can you post your wpa_supplicant.conf file again?

Make sure there are no spaces at the bottom of the file.

---

### Post by kevdog on 2008-04-07
If its the same as the two you posted previously you forgot a 
} 
on the last line to close the network block.

---

### Post by equity on 2008-04-07
this is the whole conf file (it starts and ends with a " each):

"[B]ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="GermanWLAN"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="004901742003816"
        pairwise=TKIP
        group=TKIP[/B]"

I will try it later. Gotta go to school now. I hope this was the mistake.

---

### Post by equity on 2008-04-07
btw you did not close the network block in your tutorial either.

---

### Post by kevdog on 2008-04-07
I just checked -- what tutorial are you talking about -- the copy I see they are all closed (an no I didn't just edit it either!)

---

### Post by equity on 2008-04-07
Ah... okay...
 
I have overseen the little "}" in the corner of your code.
 
Finally... it works... thanks a lot kevdog :)

Looks like the connection to a WPA network is only stable whilst the shell running the wpa_supplicant is opened, right?
If yes, is there some way to hide it or something to abate the likelyhood of closing the shell accidently?

---

### Post by Jazmo on 2008-04-07
Hmm, it's interesting. My home wlan has WPA security enabled and I have had lots of problems with it (no chance to connect to it). Luckily my neighbour's a wlan also.. without security...

I started to use Wicd, because i heard that it is better network solution than Gutsy's basic one. It finds my wlan, understands that it has WPA turned on but connecting does not work. I checked up the properties of the wireless connection in Windows, it says that there is something (i don't quite undestand) that is crypted with AES. Could this be a problem?

My WPA supplicant driver is wext. Any ideas what i should do?

I've Centrino chipset, wlan device is: PRO/Wireless 3945ABG Network Connection

---

### Post by Jazmo on 2008-04-07
Does it matter that my passphrase has special characters (öäå) in it?

I tried to connect manually by following the How-To ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)) but with ipw it says that operation not permitted and suggests to use wext. When i do, it just doesn't do anything, somewhat hangs, until i stop it by pressing ctrl-c.

Is this a hardware problem? My laptop not compatible with current wpa-software or something?

---

### Post by equity on 2008-04-07
This thread is about how to connect to a WPA encrypted network using the command line.
If you like to connect to some WPA using network using a network manager and got trouble, please open your own thread.

Btw as far as I know there is no acceptable network manager out there for Linux that works like it should at the moment. I struggled a lot with network managers like nm-applet, Wicd and WiFi Radar, none of these worked correctly, so I decided to learn how to connect to a wireless network manually using the command line.

I advice you to just use kevdog's turorial and this topic and remove all this nm rubbish from your system. At the beginning it is a bit work to bear all these commands in mind, but later on you will notice that it has been worthwhile.

If you get some trouble, just post your problems and kevdog, me or someone else will help you.

---

### Post by kevdog on 2008-04-07
> I advice you to just use kevdog's turorial and this topic and remove all this nm rubbish from your system. At the beginning it is a bit work to bear all these commands in mind, but later on you will notice that it has been worthwhile.

Spoken like a true convert.  Again manual connection is kind of a pain, but its the ultimate fallback failsafe mechanism.  If you can do a manual connection, you can connect!! (Hence the purpose of the guide actually!)

---

