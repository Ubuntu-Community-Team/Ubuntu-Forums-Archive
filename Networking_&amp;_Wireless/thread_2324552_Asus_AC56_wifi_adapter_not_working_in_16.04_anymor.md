---
title: "Asus AC56 wifi adapter not working in 16.04 anymore"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by psychedelicwonders2 on 2016-05-14
Since 16.04 is now LTS, I figured I could post this here instead of the development forum.

So I haven't been on Ubuntu for the last couple of weeks and now my wifi adapter isn't working in 16.04 again.  It was workin good for a while, but hasn't started back up.

I unplugged it multiple times, put it in different USB 3.0 slots, did a  full update and dist-upgrade just now and even re-ran all of this code:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

And the adapter isn't lighting up (there's a blue light on it that shows  when it's alive) or working at all and even Ubuntu isn't seeing any  wifi networks at all.

Any suggestions on how to get this to work again?

---

### Post by jeremy31 on 2016-05-14
Could you post results from the wireless script, a link is in my signature

---

### Post by psychedelicwonders2 on 2016-05-14
Here you go:

```

########## wireless info START ##########

Report from: 14 May 2016 18:29 EDT -0400

Booted last: 14 May 2016 00:00 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1] (rev 05)
    Subsystem: ASRock Incorporation Ethernet Connection (2) I218-V [1849:15a1]
    Kernel driver in use: e1000e

05:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: ASRock Incorporation QCA8171 Gigabit Ethernet [1849:10a1]
    Kernel driver in use: alx

##### lsusb #############################

Bus 002 Device 002: ID 8087:8002 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0b05:17d2 ASUSTek Computer, Inc. 
Bus 003 Device 003: ID 045e:07a5 Microsoft Corp. Wireless Receiver 1461C
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF]>  
          inet addr:192.168.1.191  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:8004:1ba0::27/128 Scope:Global
          inet6 addr: 2602:306:8004:1ba0:caf9:ddd4:d43:d824/64 Scope:Global
          inet6 addr: 2602:306:8004:1ba0:50e7:c29a:84b0:39da/64 Scope:Global
          inet6 addr: fe80::d70b:aca:c823:955/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20099078 (20.0 MB)  TX bytes:2248126 (2.2 MB)
          Interrupt:20 Memory:fb200000-fb220000 

enp5s0    Link encap:Ethernet  HWaddr <MAC 'enp5s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

##### iwconfig ##########################

enp0s25   no wireless extensions.

enp5s0    no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    100    0        0 enp0s25
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s25
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s25

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       770     1  0 17:36 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       21b93eb9-b2da-4a41-9d57-f114c9ea16b0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   21b93eb9-b2da-4a41-9d57-f114c9ea16b0 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.191/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        ip_address = 192.168.1.191
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = -18000
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.254
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = attlocal.net
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1463348223
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 0.0.0.0
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         2602:306:8004:1ba0::27/128
IP6.ADDRESS[2]:                         2602:306:8004:1ba0:50e7:c29a:84b0:39da/64
IP6.ADDRESS[3]:                         2602:306:8004:1ba0:caf9:ddd4:d43:d824/64
IP6.ADDRESS[4]:                         fe80::d70b:aca:c823:955/64
IP6.GATEWAY:                            fe80::6655:b1ff:fe58:8be0
IP6.ROUTE[1]:                           dst = 2602:306:8004:1ba0::/64, nh = fe80::6655:b1ff:fe58:8be0, mt = 100
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:fe:75:ed:9d:28:bd:64:be:68:fa:68:5c:3f:21:f4:c6
DHCP6.OPTION[2]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[3]:                        rebind = 483840
DHCP6.OPTION[4]:                        max_life = 2592000
DHCP6.OPTION[5]:                        preferred_life = 604800
DHCP6.OPTION[6]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[7]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[8]:                        life_starts = 1463261824
DHCP6.OPTION[9]:                        ip6_address = 2602:306:8004:1ba0::27
DHCP6.OPTION[10]:                       ip6_prefixlen = 64
DHCP6.OPTION[11]:                       renew = 302400
DHCP6.OPTION[12]:                       starts = 1463261824
DHCP6.OPTION[13]:                       iaid = 99:5c:2b:69
DHCP6.OPTION[14]:                       dhcp6_server_id = 0:1:0:1:c7:92:bc:bc:64:55:b1:58:8b:e0

GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA8171 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp5s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/net/enp5s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

Sorry, try again.
[[/etc/NetworkManager/system-connections/ATTh2Y6MbA 1]] (600 root)
[connection] id=ATTh2Y6MbA 1 | type=wifi | permissions=user:eagleeye:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ATTh2Y6MbA
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATTh2Y6MbA 2]] (600 root)
[connection] id=ATTh2Y6MbA 2 | type=wifi | permissions=user:eagleeye:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ATTh2Y6MbA
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATTh2Y6MbA]] (600 root)
[connection] id=ATTh2Y6MbA | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ATTh2Y6MbA
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp0s25   no frequency information.

enp5s0    no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp0s25   Interface doesn't support scanning.

enp5s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################


```

Thank you.

You can probably read that better, but to me I don't see the Asus AC56 adapter listed in that wireless.txt file any where, do you?

---

### Post by jeremy31 on 2016-05-14
Since your ethernet looks to be working ```
sudo apt-get install rtl8812au-dkms
```

Or it can be found [http://packages.ubuntu.com/xenial/all/rtl8812au-dkms/download](http://packages.ubuntu.com/xenial/all/rtl8812au-dkms/download)

---

### Post by psychedelicwonders2 on 2016-05-14
Thank you.  Going to reboot now, here are the results, does everything look good to you?

Any idea what would have disabled it and made it completely inactive?

```
$ sudo apt-get install rtl8812au-dkms
[sudo] password for jo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  dkms
The following NEW packages will be installed:
  dkms rtl8812au-dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,091 kB of archives.
After this operation, 8,049 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 dkms all 2.2.0.3-2ubuntu11 [67.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 rtl8812au-dkms all 4.3.8.12175.20140902+dfsg-0ubuntu2 [1,024 kB]
Fetched 1,091 kB in 0s (1,107 kB/s)       
Preconfiguring packages ...
Selecting previously unselected package dkms.
(Reading database ... 212206 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11) ...
Selecting previously unselected package rtl8812au-dkms.
Preparing to unpack .../rtl8812au-dkms_4.3.8.12175.20140902+dfsg-0ubuntu2_all.deb ...
Unpacking rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11) ...
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu2) ...
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
First Installation: checking all kernels...
Building only for 4.4.0-22-generic
Building initial module for 4.4.0-22-generic
Done.

8812au:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-22-generic/updates/dkms/

depmod....

DKMS: install completed.


```

---

### Post by psychedelicwonders2 on 2016-05-14
Back up and running on wifi again, THANK YOU!

Any idea what the issue was?  Do you think this will be a continued problem for me with this adapter?  I tried to get the most compatible one that I could.

---

### Post by jeremy31 on 2016-05-14
You may have been getting updated kernels which would require the driver to be reinstalled or there was another dkms module installed that caused issues.  You can look at ```
dkms status
``` and it might show something

---

### Post by psychedelicwonders2 on 2016-05-14
Ok so if I'm having problems again later, just re-run this code?:

```
sudo apt-get install rtl8812au-dkms
```

Here's the output of dkms status, does it look right/ok to you?

```
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.4.0-22-generic, x86_64: installed
```

---

### Post by jeremy31 on 2016-05-14
See if ```
modprobe -v rtl8812au
``` does anything

---

### Post by psychedelicwonders2 on 2016-05-14
```
$ modprobe -v rtl8812au
modprobe: FATAL: Module rtl8812au not found in directory /lib/modules/4.4.0-22-generic
jPsychw@Station:~
```

Thoughts?

---

### Post by jeremy31 on 2016-05-14
Ok, how about ```
sudo modprobe -v 8812au
```
As that is the module in the alias file of the source code

---

### Post by psychedelicwonders2 on 2016-05-14
I'm so rusty on ubuntu, I'm not even sure what that means lol

That code didn't seem to do anything, prompted me for my PW and then back to the prompt:

```
~$ sudo modprobe -v 8812au
[sudo] password for PsychW: 
PsychW@Station:~$ 


```

---

### Post by jeremy31 on 2016-05-14
So what does ```
lshw -c net; modprobe -c | grep -i 17d2
``` show

---

### Post by psychedelicwonders2 on 2016-05-14
```
:~$ lshw -c net; modprobe -c | grep -i 17d2
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Ethernet Connection (2) I218-V
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: enp0s25
       version: 05
       serial: d0:50:99:5c:2b:69
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.1-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:32 memory:fb200000-fb21ffff memory:fb239000-fb239fff ioport:f020(size=32)
  *-network
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: enp5s0
       version: 10
       serial: d0:50:99:5c:2b:67
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:37 memory:fb100000-fb13ffff ioport:d000(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@3:3
       logical name: enx9c5c8eb15a66
       serial: 9c:5c:8e:b1:5a:66
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8812au ip=192.168.1.194 multicast=yes wireless=IEEE 802.11bgn
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
alias usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in* 8812au


```

---

### Post by jeremy31 on 2016-05-14
Please run the script again and post the new results.  The wireless has a driver loaded along with an IP address although the logical name doesn't seem correct.

Actually try ```
systemctl restart NetworkManager.service
```

And see if wifi functions as there is a bug in Network Manager

---

### Post by psychedelicwonders2 on 2016-05-14
> **jeremy31 said:**
> Please run the script again and post the new results.  The wireless has a driver loaded along with an IP address although the logical name doesn't seem correct.

Actually try ```
systemctl restart NetworkManager.service
```

And see if wifi functions as there is a bug in Network Manager

When I ran that code the wifi disabled itself and then re-enabled.

What can we do to get this bug gone?

What other code do you want me to re-run?

Thanks again.

---

### Post by jeremy31 on 2016-05-14
If it works after the Network manager restart, you just have to wait for the updates to make it into the repos.  Bug reports have been filed and reported as fixed even in other Linux distros

---

### Post by psychedelicwonders2 on 2016-05-14
Ok, is it something I should check daily or weekly?

---

### Post by jeremy31 on 2016-05-14
I would just update when it says updates are available, there is no telling how long it may take for Ubuntu to approve the fix to go into the main repos

---

### Post by psychedelicwonders2 on 2016-05-14
Cool, well a big THANK YOU for all the help tonight.  I'll keep rocking till the wheels fall off and come back to this thread if I have issues again.

---

### Post by jeremy31 on 2016-05-14
You are welcome.  I know running the code after every reboot is not the best solution but for now it works.  I have no idea why everyone isn't affected by the bug as I have two laptops running Ubuntu 16.04 and neither one has any issues with wifi

---

### Post by psychedelicwonders2 on 2016-06-15
> **psychedelicwonders2 said:**
> ```
$ modprobe -v rtl8812au
modprobe: FATAL: Module rtl8812au not found in directory /lib/modules/4.4.0-22-generic
jPsychw@Station:~
```

Thoughts?

So after updating again today this adapter no longer works - this is beyond frustrating.

I ran through the following code again 

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/gnab/rtl8812au.git
cd ~/rtl8812au
make
sudo make install
sudo modprobe 8812au
```

and got this same FATAL module error code listed above

What is the problem and how do I fix it?

Is there any way to secure this wifi adapter code during updates so that it's not affected and therefore disabled?

---

### Post by jeremy31 on 2016-06-16
```
sudo apt-get install dkms
sudo dkms add ./rtl8812au
sudo dkms build -m 8812au -v 4.2.2
sudo dkms install -m 8812au -v 4.2.2
```

Reboot

That will install it as dkms and it should work after a kernel update unless it is an issue with secure boot or network manager

---

### Post by psychedelicwonders2 on 2016-06-16
Ok thank you, I will try that shortly and report back.

When does secure boot come into play?  I would like to set up my system with a TPM module - would this come into play with the secure boot & this wifi adapter issue?

---

### Post by psychedelicwonders2 on 2016-06-18
> **jeremy31 said:**
> ```
sudo apt-get install dkms
sudo dkms add ./rtl8812au
sudo dkms build -m 8812au -v 4.2.2
sudo dkms install -m 8812au -v 4.2.2
```

Reboot

That will install it as dkms and it should work after a kernel update unless it is an issue with secure boot or network manager

Hmm, so everything seemed to install properly, I rebooted, but wifi adapter still isnt working.

What code can I run for you to help check the status?

Thank you.

---

### Post by jeremy31 on 2016-06-18
Run the wireless script again and post the results

---

### Post by psychedelicwonders2 on 2016-06-18
[http://paste.ubuntu.com/17492540/](http://paste.ubuntu.com/17492540/)

---

### Post by jeremy31 on 2016-06-18
See what this does ```
sudo modprobe -v 8812au; modprobe -c | grep -i 17d2
```

---

### Post by psychedelicwonders2 on 2016-06-18
after running that code and restarting, still no dice on the wifi working.

Do you want me to post the results of running that code?  Seems to be a very long & lengthy output of code.

---

### Post by jeremy31 on 2016-06-18
Run the code, now that I edited a typo and post results

---

### Post by psychedelicwonders2 on 2016-06-18
```
Station:~$ sudo modprobe -v 8812au; modprobe -c | grep -i 17d2
[sudo] password for psychwond: 
insmod /lib/modules/4.4.0-24-generic/updates/dkms/8812au.ko 
modprobe: ERROR: could not insert '8812au': Exec format error
alias usb:v0B05p17D2d*dc*dsc*dp*ic*isc*ip*in* 8812au


```

I'll try to reboot, but that format error doesn't sound right so I want to wait for your reply before I do

---

### Post by jeremy31 on 2016-06-18
What does ```
dkms status
``` show

---

### Post by psychedelicwonders2 on 2016-06-18
```
Station:~$ dkms status
8812au, 4.2.2, 4.4.0-24-generic, x86_64: installed (WARNING! Diff between built and installed module!)
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.4.0-22-generic, x86_64: installed
rtl8812au, 4.3.8.12175.20140902+dfsg, 4.4.0-24-generic, x86_64: installed
station:~$ 


```

So I guess it looks good?  I will try to reboot now

---

### Post by jeremy31 on 2016-06-18
We have to remove one of the dkms files.  Should remove the easiest one ```
sudo apt-get remove rtl8812au-dkms
```
reboot

After that might have to remake it with ```
sudo dkms install -m 8812au -v 4.2.2 -k 4.4.0-24-generic
```

Reboot again

---

### Post by psychedelicwonders2 on 2016-06-18
> **jeremy31 said:**
> We have to remove one of the dkms files.  Should remove the easiest one ```
sudo apt-get remove rtl8812au-dkms
```
reboot


Ok after running that piece of code & rebooting my wifi adapter is now back to working again.

So do I/should i still remake it with the following code?:

```
sudo dkms install -m 8812au -v 4.2.2 -k 4.4.0-24-generic
```

---

### Post by jeremy31 on 2016-06-18
This should work for now and that code is only good for this kernel but an alternative might work
```
sudo dkms install -m 8812au -v 4.2.2 -k $(uname -r)
```

If nothing else replace $(uname -r) with the terminal result for ```
uname -r
```  It should work with the first command but I haven't tried it with dkms

---

### Post by psychedelicwonders2 on 2016-06-18
Ok so I ran uname -r

Station:~$ uname -r
4.4.0-24-generic
Station:~$ 

'So I want to run the following code then?

```
sudo dkms install -m 8812au -v 4.2.2 -k $(4.4.0-24-generic)
```

---

### Post by jeremy31 on 2016-06-18
You should be good until the next kernel update.  Lets say ```
uname -r
```
returns ```
4.4.0-27-generic
``` after the next update and the dkms doesn't work as it is designed to, then
```
sudo dkms install -m 8812au -v 4.2.2 -k 4.4.0-27-generic
```

---

### Post by psychedelicwonders2 on 2016-06-18
Ahh ok, got it thank you. 

Is there a time frame for when the next kernal update is set to be released?

---

### Post by jeremy31 on 2016-06-19
I do not know of a timeline for a kernel release in Ubuntu

---

### Post by psychedelicwonders2 on 2016-06-29
Hmm, so having issues with the wifi adatper again, I ran the following code:

```
psychwon:~$ uname -r
4.4.0-28-generic
psychwon:~$ sudo dkms install -m 8812au -v 4.2.2 -k 4.4.0-28-generic
[sudo] password for psychwon: 
Module 8812au/4.2.2 already installed on kernel 4.4.0-28-generic/x86_64
psychwon:~$ 


```

But even though it says it's installed it's still not working?

Any ideas?

Thanks.

---

### Post by jeremy31 on 2016-06-30
Let me guess ```
sudo modprobe -v 8812au
```
Gives you an error like in post 31, exec format error

---

### Post by psychedelicwonders2 on 2016-07-01
```
psychwon:~$ sudo modprobe -v 8812au
[sudo] password for psychwon: 
insmod /lib/modules/4.4.0-28-generic/updates/dkms/8812au.ko 
modprobe: ERROR: could not insert '8812au': Exec format error


```

Yes it seems so, what should I do?

Thanks.

---

### Post by jeremy31 on 2016-07-01
Hopefully this works ```
sudo dkms remove -m 8812au -v 4.2.2 -k 4.4.0-28-generic
sudo dkms install -m 8812au -v 4.2.2 -k 4.4.0-28-generic
```

Reboot

---

### Post by psychedelicwonders2 on 2016-07-01
Yes that seems to have worked, thank you.

Any idea what the issue was?

So when the kernal updates again in the future and the adapter no longer works, should I do the sudo dkms remove/install code again before running:

```
psychwon:~$ uname -r
4.4.0-28-generic
psychwon:~$ sudo dkms install -m 8812au -v 4.2.2 -k 4.4.0-28-generic
```

There isn't a permanent fix for this issue is there?  I'm going to have to keep fighting this adapter?  Hopefully in the future at one point I will go hardline, but for now can only get wifi without having a cord running through the middle of the house.

Thanks for all the continued help & support.

---

### Post by jeremy31 on 2016-07-01
It might be something with dkms or the dkms.conf or Makefile of the module.  I can't be sure at this time what is the cause but it seems that the module is building on the old kernel instead of the new one

---

### Post by maxbar on 2016-08-28
Just for those who have trouble with getting the AC56 to reliable stay online:

I had trouble with the gnab version, abperiasamy's version worked for me:

github.com/abperiasamy/rtl8812AU_8821AU_linux

I just downloaded, unzipped and then I followed the README.md instructions near the end (AKA "make clean, make, make install" - the DKMS version of instructions didn't work for me to keep the adapter reliably online).

AND IF YOU HAVE THIS ADAPTER AND KNOW HOW TO RUN IT IN UBUNTU 16.04 AS AN AP, PLEASE POST DETAILED INSTRUCTIONS IN HERE OR CREATE NEW POST AND LINK TO IT - THANKS!

---

### Post by jeremy31 on 2016-08-28
The 8812au-dkms in the repositories might work in 16.04

---

### Post by maxbar on 2016-08-28
> **jeremy31 said:**
> The 8812au-dkms in the repositories might work in 16.04

They were the first I tried and they didn't work at all. In any case, the adapter works just fine with abperiasamy's but I just can't get it to run as an AP, which I think has nothing to do with that driver but rather the surrounding software and configs.

---

