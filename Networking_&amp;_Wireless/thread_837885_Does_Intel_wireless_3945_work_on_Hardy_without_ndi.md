---
title: "Does Intel wireless 3945 work on Hardy without ndiswrapper?"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by sparetalk on 2008-06-22
I installed Hardy almost as soon as it was released. I haven't been able to get wireless working on it since. I use a Toshiba M115-S3094 with an Intel 3945 ABG card.
Has anyone with a similar config been able to get it to work with a stock install?

Thanks.

---

### Post by anandjm on 2008-06-23
Yes, it uses the iwl3945 module

---

### Post by syko21 on 2008-06-23
I found it to be unreliable when compared to the ipw3945 module that preceded it, I used ndiswrapper with it and had much better results than the iwl3945 driver hardy provides.
That said, the latest drivers available are getting rather good. [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)
You have to compile them yourself however.

---

### Post by chili555 on 2008-06-23
The native iwl3945 works perfectly for me. Please be sure to install linux-backports-modules-hardy-generic as it contains an update to iwl3945.

---

### Post by sparetalk on 2008-06-23
Thanks guys. Obviously you have a grip on things. I'm essentially a windows guy but I'm not easily scared off by characters on a terminal screen.
Can someone hold my hand through getting this working?
Really appreciate it.
For starters, how do I check which driver is currently installed and if it is installed/configured correctly?

---

### Post by chili555 on 2008-06-23
Your command:```
sudo lshw -C network
```Should produce someting like this:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:c2:1b:8d
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=iwl3945** ip=192.168.1.103 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11gNext, check:```
iwconfig
```You should see something like:> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"GBR9"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:19:58:77   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=81/100  Signal level=-53 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.Your interface may be wlan0 instead of eth1. Now try scanning for networks:```
sudo iwlist eth1 scan
```> Cell 01 - Address: 99:9C:41:19:58:79
                    ESSID:"GBR9"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=84/100  Signal level=-50 dBm  Noise level=-84 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000ca240f4b5dLet's try to connect:```
sudo iwconfig eth1 essid GBR9
sudo iwconfig eth1 key <my_26-character_WEP_key>
sudo dhclient eth1
```

---

### Post by sparetalk on 2008-06-23
The lshw -C network gave me the following output
> *-network
description: Wireless interface
product: PRO/Wireless 3945ABG Network Connection
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 02
serial: 00:18:de:53:cd:ff
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

iwconfig gives me
> wlan0     IEEE 802.11g  ESSID:""  Nickname:""
Mode:Managed  Frequency:2.447 GHz  Access Point: 00:14:95:E5:2E:89   
Bit Rate=54 Mb/s   Tx-Power=27 dBm   
Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
Power Management:off
Link Quality=97/100  Signal level=-29 dBm  Noise level=-66 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My essid is "parasx" but when I try to connect I get
>  iwconfig wlan0 essid parasx
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.


---

### Post by chili555 on 2008-06-24
> SET failed on device wlan0 ; Operation not permitted.Ordinary users are not allowed to manipulate such settings, but the Super User is. Please add *sudo* to your commands:```
sudo iwconfig eth1 essid GBR9
sudo iwconfig eth1 key <my_26-character_WEP_key>
sudo dhclient eth1
```

---

### Post by sparetalk on 2008-06-24
I tried that same command with sudo too and no error message but no connection either. In one of the network management programs I see that there are two wifi interfaces defined, wlan0 which is stated as unknown or something similar and wmaster0 which shows as active but doesn't connect to anything.
There's some changes since then. I went back and saw that you recommended installing linux-backports... so I went to the package manager and installed it. It also downloaded and installed a kernel 2.6... something. I'm guessing here coz after that the system just went crazy. My wifi got clobbered and it demanded a restart.
After restart all I got was a shell prompt. I had six kernel options to boot from but all I got was a shell prompt at the end of each option. Being a linux moron, I do not know the command to load the gui in ubuntu.
However tonight is a new night and I'm gonna reinstall Ubuntu from the CD and try again. :)

---

### Post by Turtle.net on 2008-06-24
> **chili555 said:**
> ```
sudo iwconfig eth1 essid GBR9
sudo iwconfig eth1 key <my_26-character_WEP_key>
sudo dhclient eth1
```

I tried these commands, but I'm using WPA and not WEP, therefore the instruction is not working.

Any idea ?

---

### Post by chili555 on 2008-06-24
> **Turtle.net said:**
> I tried these commands, but I'm using WPA and not WEP, therefore the instruction is not working.

Any idea ?Sure, check here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by sparetalk on 2008-06-26
OK. The OS is now back, but so's the problem. I still can't get connected to my wifi. The results of the "lshw" and "iwconfig" commands are the same as before.
What should I do next?

---

### Post by chili555 on 2008-06-26
```
sudo iwconfig wlan0 essid parasx
sudo iwconfig wlan0 key <any_WEP_encryption_here?>
sudo dhclient wlan0
```Let us know.

---

### Post by sparetalk on 2008-06-26
The first two commands did not display anything in the terminal window.
The "sudo dhclient wlan0" displayed the following.
> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:53:cd:ff
Sending on   LPF/wlan0/00:18:de:53:cd:ff
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

### Post by Turtle.net on 2008-06-26
In fact my problem seemed to be related to the kill switch :
  ```
$ dmesg | grep switch
[   11.209430] SMP alternatives: switching to UP code
[   11.577999] SMP alternatives: switching to SMP code
[   11.868581] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   37.395167] iwl3945: Radio disabled by HW RF Kill switch
[  195.123476] iwl3945: Radio disabled by HW RF Kill switch
[  195.124130] iwl3945: Radio disabled by HW RF Kill switch

``` my switch is off ... :(

Once the system boots with the switch off on my Acer Aspire 5600, there is no way that you can turn the switch back on.
After several trial and errors, it seems that the switch can be turn on when grub is loading, not after...

Anyway, now my wireless seems to be woking :)

---

### Post by sparetalk on 2008-07-01
I'm still exactly where I was 4 days ago. Any ideas on the output from my previous post?
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:53:cd:ff
Sending on LPF/wlan0/00:18:de:53:cd:ff
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping. 
```
Thanks.

---

### Post by skankster on 2008-07-02
Hello, I have an issue with iwl3945 too. I'm using WICD though not Network Manager as I switched to WICD before I upgraded due to past wifi issues.

iwl3945 apparently has problems with its scanning and won't pick up hidden SSIDs. From what I can gather, here's the list of possible fixes:

1) Update from backports which have a fix. I have backports enabled, have done an update and there is no change to behaviour.

2) Follow the instructions here:
[http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/](http://linuxexpert.wordpress.com/2008/04/28/fix-intel-wireless-driver-on-hardy/)

When I try this it makes my whole system go a little 'funny', to be technical. The GUI gets unresponsive, there are many sticky key issues when typing, and the disk seems to be in almost constant usage.

3) Uninstall iwl3945 and compile and install ipw3945. I haven't tried this as it looks a little involved.

4) Download, compile and install the latest version of the driver from:
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

Again I haven't tried this.

5) Broadcast your ESSID. I think I'm left with this one. 

Unless anyone knows of any other things to try?

---

### Post by 73ckn797 on 2008-08-28
I had to reload my Toshiba M115-S3094 with the same wireless card. Now I cannot connect wifi on the home network. I ran some of the commands suggested here. I received similar results but did have problems with the following commands:

"sudo iwconfig eth1 essid BadWind"
No respones but just returned me to the command line.

"sudo iwconfig eth1 key <my_26-character_WEP_key>"
The second command kept returning syntax or unknown argument responses. If I enter my WPA code after the "key" entry it would never work. I tried quotes, <> and nothing but the key-phrase

"sudo dhclient eth1"
It returned multiple lines with last 2 lines 
"No DHCPOFFERS received
No working leases in persistent database - sleeping"

Wireless was working before reinstall. I completely wiped, repartitioned and formatted the HD.

---

### Post by eddieishavingago on 2008-08-28
Great Forum!!  I only just bought a laptop with Vista, and it's horrible. Just think, buy a new computer, newer and more powerful, and it isn't faster than my older one with XP!!! Pitty it broke.
Anyhow, I've been messing with ubuntu and I quite like it. It's much faster than vista(maybe except for video encoding, haven't tried that).
I've bumped into a problem. My new laptop is a Samsung R70 A009, and the wifi appears to be an Intel Wireless PRO 3945BG chip. Ubuntu detects when I turn it on and off in the network settings. It greys out when I turn it off, and appears again when I turn it on. But it simply doesn't work. 
Would it be wise to try what is posted on this post to get it working? Should I have a go at installing ndiswrapper or madwifi or another driver?
If so, is there a step by step driver install and uninstall tutorial for DUMMIES like me around anywhere? I'm afraid of typing in something wrong and screwing it all up.

---

### Post by 73ckn797 on 2008-08-28
My wireless woes are fixed. I performed a complete wipe of the HD and installed the XP Media that came with it. The wireless worked after resetting the router and modem (unplug for 10-15 seconds and reconnect).

I just re-installed Ubuntu 8.04 and wireless worked immediately. I will delete the XP installation.

---

