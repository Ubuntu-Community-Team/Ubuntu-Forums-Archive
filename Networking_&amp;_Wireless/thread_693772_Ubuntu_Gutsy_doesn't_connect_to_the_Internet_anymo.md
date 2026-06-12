---
title: "Ubuntu Gutsy doesn't connect to the Internet anymore"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by DoDoENT on 2008-02-11
Hello everyone!

Since I've moved my linux partition to another hard disk, internet connection on my edubuntu 7.10 doesn't work anymore. It simply can't get IP from the router. I'm quite sure that the there is a problem with file permissions (which were disrupted during the file transfer - because I couldn't move the partition directly with the partition magic nor with the gparted, I created a new partition on the new hard disk and copied all the files from the previous root directory and corrected the /boot/grub/menu.lst so the boot process can work), because after the first boot from the new drive, sudo command didn't work (but I solved that by changing the permissions of /usr/bin/sudo with the chmod command). That's why I now think that there is still a file that has wrong permissions set because dhclient can't get IP. I'm curious which file would that be? (I've set the permissions of files in /bin /usr/bin /sbin and /usr/sbin as they are set on ubuntu 7.10 installed on my laptop). Or is there a problem with something else?

This is the extract from my daemon.log:

```
Feb 10 16:42:40 Locutus NetworkManager: <info> Device eth1 activation scheduled...
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1) started...
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 10 16:42:40 Locutus NetworkManager: <info> Activation (eth1/wireless): access point 'MaxADSL' is unencrypted, no key needed.
Feb 10 16:42:41 Locutus NetworkManager: <info> supplicant_interface_init() - connect to global ctrl socket (0/10).
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: sending command 'INTERFACE_ADD eth1^I^Iwext^I/var/run/wpa_supplicant5^I'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: response was 'OK'
Feb 10 16:42:41 Locutus NetworkManager: <info> supplicant_init() - connect to device ctrl socket (1/10).
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: sending command 'AP_SCAN 1'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: response was 'OK'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: sending command 'ADD_NETWORK'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: response was '0'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 ssid 4d61784144534c'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: response was 'OK'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: response was 'OK'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: sending command 'ENABLE_NETWORK 0'
Feb 10 16:42:41 Locutus NetworkManager: <info> SUP: response was 'OK'
Feb 10 16:42:41 Locutus NetworkManager: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 10 16:42:41 Locutus NetworkManager: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful. Connected to access point 'MaxADSL'.
Feb 10 16:42:41 Locutus NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 10 16:42:41 Locutus NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Feb 10 16:42:42 Locutus NetworkManager: <info> Activation (eth1) Beginning DHCP transaction.
Feb 10 16:42:42 Locutus dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Feb 10 16:42:42 Locutus NetworkManager: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Feb 10 16:42:42 Locutus NetworkManager: <info> DHCP daemon state is now 12 (successfully started) for interface eth1
Feb 10 16:42:43 Locutus avahi-daemon[5006]: Registering new address record for fe80::218:f3ff:fe58:152 on eth1.*.
Feb 10 16:42:45 Locutus dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Feb 10 16:42:45 Locutus dhclient: DHCPOFFER from 192.168.1.1
Feb 10 16:42:45 Locutus dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Feb 10 16:42:45 Locutus dhclient: DHCPACK from 192.168.1.1
Feb 10 16:42:46 Locutus NetworkManager: <info> Old device 'eth1' activating, won't change.
Feb 10 16:44:21 Locutus NetworkManager: <info> Device 'eth1' DHCP transaction took too long (>99s), stopping it.
Feb 10 16:44:21 Locutus dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 7118
Feb 10 16:44:21 Locutus dhclient: killed old client process, removed PID file
Feb 10 16:44:21 Locutus dhclient: DHCPRELEASE on eth1 to 192.168.1.1 port 67
Feb 10 16:44:21 Locutus dhclient: send_packet: Network is unreachable
Feb 10 16:44:21 Locutus dhclient: send_packet: please consult README file regarding broadcast address.
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) Stage 4 of 5 (IP Configure Timeout) scheduled...
Feb 10 16:44:22 Locutus NetworkManager: <info> DHCP daemon state is now 14 (normal exit) for interface eth1
Feb 10 16:44:22 Locutus NetworkManager: <info> DHCP daemon state is now 14 (normal exit) for interface eth1
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) Stage 4 of 5 (IP Configure Timeout) started...
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) failure scheduled...
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) Stage 4 of 5 (IP Configure Timeout) complete.
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) failed for access point (MaxADSL)
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) failed.
Feb 10 16:44:22 Locutus NetworkManager: <info> Deactivating device eth1.
Feb 10 16:44:23 Locutus avahi-daemon[5006]: Withdrawing address record for fe80::218:f3ff:fe58:152 on eth1.
Feb 10 16:44:50 Locutus NetworkManager: <WARN> nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device

```

If I run dhclient from a console, the following happens:

```
dodo@Locutus:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth1/00:18:f3:58:01:52
Sending on LPF/eth1/00:18:f3:58:01:52
Listening on LPF/eth0/00:13:d3:9a:21:1d
Sending on LPF/eth0/00:13:d3:9a:21:1d
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted

```

A then it freezes. I have to kill it with ctrl+c
The very same command on my laptop gives much different output (on my laptop internet works):

```
dodo@2nd-of-12:/etc/dhcp3$ sudo dhclient
[sudo] password for dodo:
There is already a pid file /var/run/dhclient.pid with pid 20612
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1b:77:31:26:34
Sending on LPF/eth1/00:1b:77:31:26:34
Listening on LPF/eth0/00:1b:38:2d:d8:06
Sending on LPF/eth0/00:1b:38:2d:d8:06
Sending on Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.35 -- renewal in 122684 seconds.
```

Any ideas what could be the problem? I'm out of ideas :(:(

---

### Post by PureSamuel on 2008-02-11
Are you using wireless?

---

### Post by DoDoENT on 2008-02-11
Yes. Why?

---

### Post by PureSamuel on 2008-02-11
When you installed Gutsy, did you have an internet connection?
My wireless wouldn't work the first time I installed but I reinstalled with a wired connection and my wireless started to work.

---

### Post by DoDoENT on 2008-02-11
After I installed gutsy, internet didn't work because I had to install bcm43xx-fwcutter and cut the firmware for my WLAN card from windows driver. After that, it worked well.

After I moved my partition, internet stopped working.

I tried to re-extract the firmware from windows driver. Operation completed successfully, but it didn't solve my problem. WLAN scanning works fine, therefore I guess, drivers are OK. The problem is when dhclient tries to obtain IP address. See the extract from logs from my first post.

---

### Post by PureSamuel on 2008-02-11
What happens when you type "sudo iwconfig wlan0"?

---

### Post by DoDoENT on 2008-02-11
```
dodo@Locutus:~$ sudo iwconfig wlan0
wlan0     No such device

dodo@Locutus:~$ sudo iwconfig eth1
[sudo] password for dodo:
eth1      IEEE 802.11b/g  ESSID:"MaxADSL"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: 00:13:49:E1:DA:AB   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=51/100  Signal level=-63 dBm  Noise level=-54 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by PureSamuel on 2008-02-11
Are you using a desktop or a laptop?
Also, does the wireless icon appear at the top?

---

### Post by DoDoENT on 2008-02-11
The problem is on my desktop computer. On my laptop, internet works. There is a wireless icon on the top, and network manager finds WLAN networks, but when I click the desired WLAN network, IP can't be obtained. WLAN drivers work OK. Read the log I've posted in my first post! After the DHCPACK has been received, received IP settings can't be applied.

---

### Post by DoDoENT on 2008-02-11
I've found a solution!!!!!

The problem was in dhclient - it doesn't work. I've managed to download the dhcpcd with my laptop and install it on my desktop computer.

Now I've made the manual configuration of WLAN with ifconfig, iwconfig, ifup and dhcpcd (without network manager).

I'll try to investigate now what happened to dhclient...

---

### Post by PureSamuel on 2008-02-11
Excellent.
I can't say I would have solved that..

---

### Post by DoDoENT on 2008-02-11
As I regained internet connection, I opened the synaptic package manager and reinstalled all files that have dhcp or avahi in their names. And after reboot internet works even with network manager. :guitar::popcorn:

---

### Post by rustybronco on 2008-02-11
**Way out of my league here, but...**
> **DoDoENT said:**
> Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) failed for access point (MaxADSL)
Feb 10 16:44:22 Locutus NetworkManager: <info> Activation (eth1) failed.
Feb 10 16:44:22 Locutus NetworkManager: <info> Deactivating device eth1.
Feb 10 16:44:23 Locutus avahi-daemon[5006]: Withdrawing address record for** fe80::218:f3ff:fe58:152** on eth1.
**Feb 10 16:44:50 Locutus NetworkManager: <WARN> nm_device_802_11_wireless_scan(): could not trigger wireless scan on device eth1: No such device**
[/CODE]

If I run dhclient from a console, the following happens:

```
dodo@Locutus:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth1/**00:18:f3:58:01:52**
Sending on LPF/eth1/00:18:f3:58:01:52
Listening on LPF/eth0/00:13:d3:9a:21:1d
Sending on LPF/eth0/00:13:d3:9a:21:1d
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFNETMASK: Permission denied
SIOCSIFBRDADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCADDRT: Operation not permitted

```

A then it freezes. I have to kill it with ctrl+c

Any ideas what could be the problem? I'm out of ideas :(:(

[https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/19740](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/19740)
> How I fixed it....

have a look in /etc/iftab, my file had eth0 linked to the wrong mac address, hence the nic was being given the next available (eth1) as shown by ifconfig -a.

When I changed the mac address in /etc/iftab to have eth0 mac 00:xx:xx:xx:xx:xx (for the actual card), everything started just fine !

In laymans terms, eth1 was the only interface the machine could assign, but the /etc/network/interfaces file was still trying to play with eth0.

Another way to fix it is to change eth0 to eth1 in all places in /etc/network/interfaces.

---

