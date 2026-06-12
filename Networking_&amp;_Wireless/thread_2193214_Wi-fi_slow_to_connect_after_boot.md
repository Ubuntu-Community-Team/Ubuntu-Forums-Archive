---
title: "Wi-fi slow to connect after boot"
date: 2013-12-11
forum: Networking &amp; Wireless
---

### Post by bigboiburgers7 on 2013-12-11
Like the title says it takes me 30 minutes to and hour to connect to my wifi when i start up my computer. :(
I could use some of your advice.

```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25
Dec 11 14:59:52 dc7700 dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67 (xid=0x972a9a7)
Dec 11 14:59:55 dc7700 dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67 (xid=0x972a9a7)
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info>   address 192.168.2.3
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info>   prefix 24 (255.255.255.0)
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info>   gateway 192.168.2.1
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info>   nameserver '192.168.2.1'
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info>   domain name 'Belkin'
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 11 14:59:55 dc7700 NetworkManager[922]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Dec 11 14:59:55 dc7700 avahi-daemon[703]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Dec 11 14:59:55 dc7700 avahi-daemon[703]: New relevant interface wlan0.IPv4 for mDNS.
Dec 11 14:59:55 dc7700 avahi-daemon[703]: Registering new address record for 192.168.2.3 on wlan0.IPv4.
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> Policy set 'Wi-Fi connection 1' (wlan0) as default for IPv4 routing and DNS.
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> DNS: starting dnsmasq...
Dec 11 14:59:56 dc7700 NetworkManager[922]: <warn> dnsmasq not available on the bus, can't update servers.
Dec 11 14:59:56 dc7700 NetworkManager[922]: <error> [1386791996.551368] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Dec 11 14:59:56 dc7700 NetworkManager[922]: <warn> DNS: plugin dnsmasq update failed
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> Writing DNS information to /sbin/resolvconf
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> Activation (wlan0) successful, device activated.
Dec 11 14:59:56 dc7700 NetworkManager[922]: <warn> dnsmasq appeared on DBus: :1.92
Dec 11 14:59:56 dc7700 NetworkManager[922]: <info> Writing DNS information to /sbin/resolvconf

```

I tried lspci -nn | grep 0280 Chilli but didn't work for me.

---

### Post by chili555 on 2013-12-11
Then let's see:```
lspci -nn
```Also this is interesting:> <error> [1386791996.551368] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus:I saw this: [http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict](http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict)

Let's see which you have installed:```
sudo dpkg -s dnsmasq | head -n5
sudo dpkg -s dnsmasq-base | head -n5
```

The whole process you posted in the log took 4 seconds, not 30 minutes, so we may need to dig deeper.

---

### Post by bigboiburgers7 on 2013-12-11
> **chili555 said:**
> Then let's see:```
lspci -nn
```Also this is interesting:I saw this: [http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict](http://askubuntu.com/questions/262301/is-dnsmasq-not-loading-because-of-a-network-manager-conflict)

Let's see which you have installed:```
sudo dpkg -s dnsmasq | head -n5
sudo dpkg -s dnsmasq-base | head -n5
```

The whole process you posted in the log took 4 seconds, not 30 minutes, so we may need to dig deeper.

Sholda said it's a USB so ```
lspci -nn
``` won't work. I tried ```
lsusb -nn
``` but that's not right apparently.

sudo dpkg -s dnsmasq | head -n5
```
Package: dnsmasq
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 111

```

sudo dpkg -s dnsmasq-base | head -n5
```
Package: dnsmasq-base
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 616

```

 I was already connected when i ran ```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25
``` should i reboot and run it while trying to connect?

---

### Post by chili555 on 2013-12-11
I assume you have an ordinary computer setup using Network Manager and connecting to a home router and nothing else going on that's unusual. If so, please do:```
sudo apt-get remove dnsmasq
```Reboot and then let me see the log again:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25
lsusb
```

---

### Post by bigboiburgers7 on 2013-12-11
Removing dnsmasq possibly solved it. :P 

I tried rebooting three and was able to auto connect every time. I'll post back in a few days if it worked for sure and mark question solved in a couple days.

Thanks for taking the time to help a Ubuntu noob Chili555.

---

### Post by chili555 on 2013-12-11
My pleasure! I hope it goes well.

---

### Post by bigboiburgers7 on 2013-12-13
It didn't continue to work. :cry:

```
josh@dc7700:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 148f:3370 Ralink Technology, Corp. RT3370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04f3:01a4 Elan Microelectronics Corp. Wireless Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
josh@dc7700:~$ cat /var/log/syslog | grep -e wlan -e etwork | tail -n25
Dec 13 16:53:57 dc7700 kernel: [  177.649212] wlan0: authenticate with ec:1a:59:d1:b1:c0
Dec 13 16:53:57 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 13 16:53:57 dc7700 kernel: [  177.713438] wlan0: direct probe to ec:1a:59:d1:b1:c0 (try 1/3)
Dec 13 16:53:57 dc7700 kernel: [  177.916033] wlan0: direct probe to ec:1a:59:d1:b1:c0 (try 2/3)
Dec 13 16:53:57 dc7700 kernel: [  178.120020] wlan0: direct probe to ec:1a:59:d1:b1:c0 (try 3/3)
Dec 13 16:53:57 dc7700 kernel: [  178.324018] wlan0: authentication with ec:1a:59:d1:b1:c0 timed out
Dec 13 16:53:58 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Dec 13 16:53:58 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 13 16:53:59 dc7700 wpa_supplicant[807]: wlan0: SME: Trying to authenticate with ec:1a:59:d1:b1:c0 (SSID='belkin.1c0' freq=2412 MHz)
Dec 13 16:53:59 dc7700 kernel: [  179.873355] wlan0: authenticate with ec:1a:59:d1:b1:c0
Dec 13 16:53:59 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 13 16:53:59 dc7700 kernel: [  179.937437] wlan0: direct probe to ec:1a:59:d1:b1:c0 (try 1/3)
Dec 13 16:53:59 dc7700 kernel: [  180.140020] wlan0: direct probe to ec:1a:59:d1:b1:c0 (try 2/3)
Dec 13 16:54:00 dc7700 kernel: [  180.344022] wlan0: direct probe to ec:1a:59:d1:b1:c0 (try 3/3)
Dec 13 16:54:00 dc7700 kernel: [  180.548022] wlan0: authentication with ec:1a:59:d1:b1:c0 timed out
Dec 13 16:54:00 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Dec 13 16:54:00 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Dec 13 16:54:05 dc7700 NetworkManager[745]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Dec 13 16:54:05 dc7700 NetworkManager[745]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Dec 13 16:54:05 dc7700 NetworkManager[745]: <info> Marking connection 'Wi-Fi connection 1' invalid.
Dec 13 16:54:05 dc7700 NetworkManager[745]: <warn> Activation (wlan0) failed for connection 'Wi-Fi connection 1'
Dec 13 16:54:05 dc7700 NetworkManager[745]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec 13 16:54:05 dc7700 NetworkManager[745]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec 13 16:54:05 dc7700 NetworkManager[745]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Dec 13 16:54:05 dc7700 NetworkManager[745]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.

```

---

### Post by chili555 on 2013-12-13
> wlan0: SME: Trying to authenticate with ec:1a:59:d1:b1:c0 (SSID='[COLOR="#FF0000"]belkin.1c0[/COLOR]' freq=2412 MHz)And then:> (wlan0): device state change: config -> failed (reason '[COLOR="#FF0000"]SSID not found[/COLOR]') [50 120 53]Are you in a different location? Is the router turned on?? Does scanning see it?```
sudo iwlist wlan0 scan
```

---

### Post by bigboiburgers7 on 2013-12-13
Same location. If i keep trying to connect it will eventually.

```
josh@dc7700:~$ sudo iwlist wlan0 scan
[sudo] password for josh: 
wlan0     Scan completed :
          Cell 01 - Address: EC:1A:59:D1:B1:C0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"xxxxxxx"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f314fddd7
                    Extra: Last beacon: 3248ms ago
                    IE: Unknown: 000A62656C6B696E2E316330
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050000000000000000000000000000000000000000

```

---

### Post by bigboiburgers7 on 2013-12-27
Just a update in case anyones seaches for this. I finally got my wifi working correctly on Ubuntu 13.10 64bit, kernel 3.11. :p

My lsusb that shows my wifi dongle.
```
josh@dc7700:~$ lsusb Device 003: ID 148f:3370 Ralink Technology, Corp. RT3370 Wireless Adapter 
```

I gave up on getting the rt2800usb drivers to work with my adapter and compiled the v2.6.1.3 from the [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501) site. This fixed my wifi issues completly but caused a few crashes for my computer every day. 

The solution i eventually found that worked was to follow this guide [http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/](http://www.ctheroux.com/2012/09/ralink-rt5572-based-wifi-usb-dongle-setup-on-ubuntu-12-04/) and download the "Edited" drivers in step 4. Been using it for a couple of days and quick to connect to wifi and no drops.

---

