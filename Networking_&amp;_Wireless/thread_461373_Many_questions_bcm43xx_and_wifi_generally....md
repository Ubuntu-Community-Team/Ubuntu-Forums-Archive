---
title: "Many questions bcm43xx and wifi generally..."
date: 2007-06-01
forum: Networking &amp; Wireless
---

### Post by usernamed on 2007-06-01
Please bear with me for posting this, I appreciate this is going to sound like I'm covering well covered ground, but it's frustrating the hell out of me and I'd like to make ubuntu usable as I've switched completely from Windows, and I'm not finding my exact issue when searching (although there's so many Broadcom issues I could have missed the post that will answer my prayers)

When I start the machine, I don't have wifi.  I can usually get wifi working through a seemingly random combination of the following commands:

```
sudo modprobe bcm43xx
``` (despite seeing the bcm43xx module already loaded using lsmod)
```
sudo ifconfig eth1 down
``` followed by ```
sudo ifconfig eth1 up
``` (despite being able to see the interface in ifconfig)
```
sudo /etc/init.d/networking restart
```

The exact combination that works seems to differ each time I restart the computer.  I'm using the bcm43xx driver and wpa_supplicant to connect to my WPA wireless router.

The message I keep seeing in amongst the dmesg output is:

```
[  592.162592] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

And /var/log/messages (when grepped for eth1) shows:

```
Jun  1 20:48:42 lt1 kernel: [   65.775625] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  1 20:51:12 lt1 kernel: [  232.254739] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  1 20:52:10 lt1 kernel: [  290.574002] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun  1 21:04:54 lt1 kernel: [ 1055.985933] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun  1 21:04:55 lt1 kernel: [ 1056.682619] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
```

As you can see, even while typing this message, I've lost the connection once, despite sitting 8 foot from the router with no obstructions.  I know the hardware is fine because it ran flawlessly in WinXP for over a month.

My first question would be how to get the wireless working reliably and automatically upon startup?

My other questions relate to how to stop the DHCP thingy trying to DHCP scan for eth0, wlan0 and a whole bunch of other interfaces when it does its initial scan?  I unticked the other interfaces in Network Manager, but it hasn't made any difference.  

It's really strange that I can get wireless to work, but only intermittently.  Can anyone help?

---

### Post by MrObvious on 2007-06-01
I use the network manager. Make sure you don't have ndiswrapper or anything else set up, just BCM43xx. 

```
sudo rmmod ndiswrapper
sudo rmmod bcm43xx
sudo modprobe bcm43xx
```

After you get it working, just go to the network manager icon, left click it, and you should be able to choose your network you want without problem. I have a BCM4318 and it works easy. I just have to find a way to have it remember my WPA key now but other than that it works flawlessly.

---

### Post by usernamed on 2007-06-01
Hi,

Thanks for the response.  I'm certain ndiswrapper isn't running by looking through the list of modules loaded when I run lsmod.  It was one of the things I suspected might be happening, but doesn't seem to be.

Oh by the way, re: your WPA problem, there's a sticky post visible in this very forum (I believe by wieman01) regarding getting WPA working.  I followed that to set up wpa_supplicant which seems to have done the job for me with WPA.

It's just getting the connection up to begin with (and keeping it) that seems to be a struggle for me.  I'm running Feisty - AMD64 on an HP NX6125 laptop if that helps anyone.

---

### Post by MrObvious on 2007-06-01
Try forgetting all those extra commands and letting it go with the network manager. It should detect it automatically. Just sudo rmmod bcm43xx and sudo modprobe bcm43xx and let the network manager try to handle it. That's how I do it.

---

### Post by usernamed on 2007-06-02
Thanks again MrObvious, but dropping and reloading the bc43xx module hasn't made any difference.  I've got more log output in case this is helpful, but Network Manager doesn't seem to allow any encryption stronger than WEP, and I can't get it to read anything other than Manual Configuration.

However, I found a log file (daemon.log) that I didn't know existed and may help things (output below)




ifconfig output
===============

```
eth1      Link encap:Ethernet  HWaddr ??:??:??:??:??:?? (<-changed by me)  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:5 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xc000 

```

iwlist scan output
==================

```

Cell 02 - Address: ??:??:??:??:??:??
                    ESSID:"???"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-46 dBm  Noise level=-70 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 184ms ago

```
Dmesg Output
============
```

[   47.951473] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   52.970028] printk: 11 messages suppressed.
[   52.970036] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   53.949511] warning: many lost ticks.
[   53.949515] Your time source seems to be instable or some driver is hogging interupts
[   53.949526] rip _spin_unlock_irqrestore+0x8/0x10
[   58.000194] printk: 11 messages suppressed.
[   58.000201] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   63.042350] printk: 11 messages suppressed.
[   63.042356] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   68.079219] printk: 11 messages suppressed.
[   68.079227] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   68.421132] NET: Registered protocol family 10
[   68.421239] lo: Disabled Privacy Extensions
[   68.421305] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.421307] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   73.104840] printk: 11 messages suppressed.
[   73.104846] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   78.141026] printk: 11 messages suppressed.
[   78.141033] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   83.156023] printk: 11 messages suppressed.
[   83.156030] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   88.183757] printk: 11 messages suppressed.
[   88.183763] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   93.238051] printk: 11 messages suppressed.
[   93.238057] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[   97.863677] printk: 10 messages suppressed.
[   97.863683] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  102.897104] printk: 11 messages suppressed.
[  102.897111] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  119.522115] printk: 10 messages suppressed.
[  119.522122] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  119.938735] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  120.357270] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  122.894671] printk: 5 messages suppressed.
[  122.894677] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  127.924038] printk: 11 messages suppressed.
[  127.924046] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  132.973798] printk: 11 messages suppressed.
[  132.973804] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  138.004012] printk: 11 messages suppressed.
[  138.004018] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  143.078704] printk: 11 messages suppressed.
[  143.078710] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  148.122693] printk: 11 messages suppressed.
[  148.122699] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  153.162491] printk: 11 messages suppressed.
[  153.162498] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  158.194563] printk: 11 messages suppressed.
[  158.194570] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  162.800320] printk: 10 messages suppressed.
[  162.800328] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  167.862221] printk: 11 messages suppressed.
[  167.862227] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  172.896884] printk: 11 messages suppressed.
[  172.896891] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  177.934774] printk: 11 messages suppressed.
[  177.934782] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  183.021811] printk: 11 messages suppressed.
[  183.021817] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  188.061472] printk: 11 messages suppressed.
[  188.061480] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  193.135589] printk: 11 messages suppressed.
[  193.135596] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  198.154970] printk: 11 messages suppressed.
[  198.154976] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  203.176757] printk: 11 messages suppressed.
[  203.176764] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  207.799704] printk: 10 messages suppressed.
[  207.799711] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  212.820187] printk: 11 messages suppressed.
[  212.820193] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  217.861948] printk: 11 messages suppressed.
[  217.861955] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  222.873237] printk: 11 messages suppressed.
[  222.873246] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  227.909562] printk: 11 messages suppressed.
[  227.909570] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  232.943205] printk: 11 messages suppressed.
[  232.943211] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  237.987439] printk: 11 messages suppressed.
[  237.987445] SoftMAC: Open Authentication completed with ??:??:??:??:??:??
[  242.868140] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[  252.137629] bcm43xx driver
[  252.138223] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
[  252.473613] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

/var/log/messages output
=============
```

Jun  2 07:27:49 ??? kernel: [  198.154970] printk: 11 messages suppressed.
Jun  2 07:27:49 ??? kernel: [  198.154976] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:27:53 ??? kernel: [  203.176757] printk: 11 messages suppressed.
Jun  2 07:27:53 ??? kernel: [  203.176764] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:27:57 ??? kernel: [  207.799704] printk: 10 messages suppressed.
Jun  2 07:27:57 ??? kernel: [  207.799711] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:01 ??? kernel: [  212.820187] printk: 11 messages suppressed.
Jun  2 07:28:01 ??? kernel: [  212.820193] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:05 ??? kernel: [  217.861948] printk: 11 messages suppressed.
Jun  2 07:28:05 ??? kernel: [  217.861955] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:09 ??? kernel: [  222.873237] printk: 11 messages suppressed.
Jun  2 07:28:09 ??? kernel: [  222.873246] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:14 ??? kernel: [  227.909562] printk: 11 messages suppressed.
Jun  2 07:28:14 ??? kernel: [  227.909570] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:18 ??? kernel: [  232.943205] printk: 11 messages suppressed.
Jun  2 07:28:18 ??? kernel: [  232.943211] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:22 ??? kernel: [  237.987439] printk: 11 messages suppressed.
Jun  2 07:28:22 ??? kernel: [  237.987445] SoftMAC: Open Authentication completed with 00:0f:cb:b6:83:0c
Jun  2 07:28:26 ??? kernel: [  242.868140] ACPI: PCI interrupt for device 0000:02:02.0 disabled
Jun  2 07:28:36 ??? kernel: [  252.137629] bcm43xx driver
Jun  2 07:28:36 ??? kernel: [  252.138223] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun  2 07:28:36 ??? kernel: [  252.473613] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

Output from Daemon.log
======================
```

Jun  2 07:24:24 ??? dhclient: Listening on LPF/eth1/??:??:??:??:??:??
Jun  2 07:24:24 ??? dhclient: Sending on   LPF/eth1/??:??:??:??:??:??
Jun  2 07:24:24 ??? dhclient: Sending on   Socket/fallback
Jun  2 07:24:24 ??? dhclient: DHCPRELEASE on eth1 to 192.168.202.1 port 67
Jun  2 07:24:24 ??? avahi-daemon[4727]: Withdrawing address record for 192.168.202.2 on eth1.
Jun  2 07:24:24 ??? avahi-daemon[4727]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.202.2.
Jun  2 07:24:24 ??? avahi-daemon[4727]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  2 07:24:24 ??? avahi-autoipd(eth1)[23086]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jun  2 07:24:24 ??? avahi-autoipd(eth1)[23086]: Successfully called chroot().
Jun  2 07:24:24 ??? avahi-autoipd(eth1)[23086]: Successfully dropped root privileges.
Jun  2 07:24:24 ??? avahi-autoipd(eth1)[23086]: fopen() failed: Permission denied
Jun  2 07:24:24 ??? avahi-autoipd(eth1)[23086]: Starting with address 169.254.10.2
Jun  2 07:24:30 ??? avahi-autoipd(eth1)[23086]: Callout BIND, address 169.254.10.2 on interface eth1
Jun  2 07:24:30 ??? avahi-daemon[4727]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.10.2.
Jun  2 07:24:30 ??? avahi-daemon[4727]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 07:24:30 ??? avahi-daemon[4727]: Registering new address record for 169.254.10.2 on eth1.IPv4.
Jun  2 07:24:34 ??? avahi-autoipd(eth1)[23086]: Successfully claimed IP address 169.254.10.2
Jun  2 07:24:34 ??? avahi-autoipd(eth1)[23086]: fopen() failed: Permission denied
Jun  2 07:24:34 ??? avahi-daemon[4727]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  2 07:24:34 ??? avahi-daemon[4727]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.10.2.
Jun  2 07:24:34 ??? avahi-autoipd(eth1)[23086]: SIOCSIFFLAGS failed: Permission denied
Jun  2 07:24:34 ??? avahi-autoipd(eth1)[23086]: Callout STOP, address 169.254.10.2 on interface eth1
Jun  2 07:24:34 ??? avahi-daemon[4727]: Withdrawing address record for ??:??:??:??:??:?? on eth1.
Jun  2 07:24:34 ??? avahi-daemon[4727]: Withdrawing address record for 169.254.10.2 on eth1.
Jun  2 07:24:34 ??? avahi-autoipd(eth1)[23087]: client: RTNETLINK answers: No such process
Jun  2 07:25:27 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Jun  2 07:25:29 ??? NetworkManager: <information>^Istarting... 
Jun  2 07:25:30 ??? avahi-daemon[4710]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Jun  2 07:25:30 ??? avahi-daemon[4710]: Successfully dropped root privileges.
Jun  2 07:25:30 ??? avahi-daemon[4710]: avahi-daemon 0.6.17 starting up.
Jun  2 07:25:30 ??? avahi-daemon[4710]: Successfully called chroot().
Jun  2 07:25:30 ??? avahi-daemon[4710]: Successfully dropped remaining capabilities.
Jun  2 07:25:30 ??? avahi-daemon[4710]: No service found in /etc/avahi/services.
Jun  2 07:25:30 ??? avahi-daemon[4710]: Network interface enumeration completed.
Jun  2 07:25:30 ??? avahi-daemon[4710]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun  2 07:25:30 ??? avahi-daemon[4710]: Server startup complete. Host name is ???.local. Local service cookie is 3643293330.
Jun  2 07:25:34 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Jun  2 07:25:35 ??? hcid[4963]: Bluetooth HCI daemon
Jun  2 07:25:35 ??? NetworkManager: <debug info>^I[1180765535.548312] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Jun  2 07:25:35 ??? hcid[4963]: Starting SDP server
Jun  2 07:25:44 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jun  2 07:25:56 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Jun  2 07:25:58 ??? dhclient: No DHCPOFFERS received.
Jun  2 07:25:58 ??? dhclient: No working leases in persistent database - sleeping.
Jun  2 07:25:58 ??? avahi-autoipd(eth1)[5217]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jun  2 07:25:58 ??? avahi-autoipd(eth1)[5217]: Successfully called chroot().
Jun  2 07:25:58 ??? avahi-autoipd(eth1)[5217]: Successfully dropped root privileges.
Jun  2 07:25:58 ??? avahi-autoipd(eth1)[5217]: fopen() failed: Permission denied
Jun  2 07:25:58 ??? avahi-autoipd(eth1)[5217]: Starting with address 169.254.10.2
Jun  2 07:26:02 ??? NetworkManager: <information>^IUpdating allowed wireless network lists. 
Jun  2 07:26:02 ??? NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun  2 07:26:04 ??? avahi-autoipd(eth1)[5217]: Callout BIND, address 169.254.10.2 on interface eth1
Jun  2 07:26:04 ??? avahi-daemon[4710]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.10.2.
Jun  2 07:26:04 ??? avahi-daemon[4710]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 07:26:04 ??? avahi-daemon[4710]: Registering new address record for 169.254.10.2 on eth1.IPv4.
Jun  2 07:26:08 ??? avahi-autoipd(eth1)[5217]: Successfully claimed IP address 169.254.10.2
Jun  2 07:26:08 ??? avahi-autoipd(eth1)[5217]: fopen() failed: Permission denied
Jun  2 07:26:36 ??? ntpdate[5349]: can't find host ntp.ubuntu.com 
Jun  2 07:26:36 ??? ntpdate[5349]: no servers can be used, exiting
Jun  2 07:28:26 ??? avahi-daemon[4710]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  2 07:28:26 ??? avahi-daemon[4710]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.10.2.
Jun  2 07:28:26 ??? avahi-autoipd(eth1)[5217]: if_indextoname() failed: No such device or address
Jun  2 07:28:26 ??? avahi-autoipd(eth1)[5217]: Callout STOP, address 169.254.10.2 on interface (null)
Jun  2 07:28:26 ??? dhclient: receive_packet failed on eth1: Network is down
Jun  2 07:28:26 ??? avahi-autoipd(eth1)[5218]: if_indextoname() failed: No such device or address
Jun  2 07:28:26 ??? avahi-daemon[4710]: Withdrawing address record for 169.254.10.2 on eth1.
Jun  2 07:28:26 ??? NetworkManager: <debug info>^I[1180765706.889908] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_14_a5_66_e1_c9'). 
Jun  2 07:28:36 ??? NetworkManager: <debug info>^I[1180765716.202816] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_14_a5_66_e1_c9'). 
Jun  2 07:31:32 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jun  2 07:31:38 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Jun  2 07:31:48 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jun  2 07:32:00 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Jun  2 07:32:03 ??? dhclient: No DHCPOFFERS received.
Jun  2 07:32:03 ??? dhclient: No working leases in persistent database - sleeping.
Jun  2 07:32:03 ??? avahi-autoipd(eth1)[5834]: Found user 'avahi-autoipd' (UID 104) and group 'avahi-autoipd' (GID 110).
Jun  2 07:32:03 ??? avahi-autoipd(eth1)[5834]: Successfully called chroot().
Jun  2 07:32:03 ??? avahi-autoipd(eth1)[5834]: Successfully dropped root privileges.
Jun  2 07:32:03 ??? avahi-autoipd(eth1)[5834]: fopen() failed: Permission denied
Jun  2 07:32:03 ??? avahi-autoipd(eth1)[5834]: Starting with address 169.254.10.2
Jun  2 07:32:07 ??? avahi-autoipd(eth1)[5834]: Callout BIND, address 169.254.10.2 on interface eth1
Jun  2 07:32:07 ??? avahi-daemon[4710]: Joining mDNS multicast group on interface eth1.IPv4 with address 169.254.10.2.
Jun  2 07:32:07 ??? avahi-daemon[4710]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 07:32:07 ??? avahi-daemon[4710]: Registering new address record for 169.254.10.2 on eth1.IPv4.
Jun  2 07:32:11 ??? avahi-autoipd(eth1)[5834]: Successfully claimed IP address 169.254.10.2
Jun  2 07:32:11 ??? avahi-autoipd(eth1)[5834]: fopen() failed: Permission denied
Jun  2 07:39:13 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Jun  2 07:39:18 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Jun  2 07:39:32 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun  2 07:39:40 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Jun  2 07:39:44 ??? dhclient: No DHCPOFFERS received.
Jun  2 07:39:44 ??? dhclient: No working leases in persistent database - sleeping.

```




MORE DAEMON.LOG extracts
========================

When sudo '/etc/init.d/networking restart' doesn't work:
```

Jun  2 07:49:47 ??? dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun  2 07:49:47 ??? dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun  2 07:49:47 ??? dhclient: All rights reserved.
Jun  2 07:49:47 ??? dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun  2 07:49:47 ??? dhclient: 
Jun  2 07:49:47 ??? dhclient: Listening on LPF/eth1/??:??:??:??:??:??
Jun  2 07:49:47 ??? dhclient: Sending on   LPF/eth1/??:??:??:??:??:??
Jun  2 07:49:47 ??? dhclient: Sending on   Socket/fallback
Jun  2 07:49:47 ??? dhclient: DHCPRELEASE on eth1 to 192.168.202.1 port 67
Jun  2 07:49:47 ??? avahi-daemon[4710]: Interface eth1.IPv4 no longer relevant for mDNS.
Jun  2 07:49:47 ??? avahi-daemon[4710]: Leaving mDNS multicast group on interface eth1.IPv4 with address 169.254.10.2.
Jun  2 07:49:47 ??? avahi-autoipd(eth1)[6448]: SIOCSIFFLAGS failed: Permission denied
Jun  2 07:49:47 ??? avahi-autoipd(eth1)[6448]: Callout STOP, address 169.254.10.2 on interface eth1
Jun  2 07:49:47 ??? avahi-daemon[4710]: Withdrawing address record for ??:??:??:??:??:?? on eth1.
Jun  2 07:49:47 ??? avahi-daemon[4710]: Withdrawing address record for 169.254.10.2 on eth1.
Jun  2 07:49:47 ??? avahi-autoipd(eth1)[6449]: client: RTNETLINK answers: No such process
Jun  2 07:49:48 ??? dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
```

When 'sudo /etc/init.d/networking restart' DOES work:
```

Jun  2 07:49:48 ??? dhclient: Internet Systems Consortium DHCP Client V3.0.4
Jun  2 07:49:48 ??? dhclient: Copyright 2004-2006 Internet Systems Consortium.
Jun  2 07:49:48 ??? dhclient: All rights reserved.
Jun  2 07:49:48 ??? dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jun  2 07:49:48 ??? dhclient: 
Jun  2 07:49:49 ??? dhclient: Listening on LPF/eth1/??:??:??:??:??:??
Jun  2 07:49:49 ??? dhclient: Sending on   LPF/eth1/??:??:??:??:??:??
Jun  2 07:49:49 ??? dhclient: Sending on   Socket/fallback
Jun  2 07:49:49 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jun  2 07:49:49 ??? avahi-daemon[4710]: Registering new address record for ??:??:??:??:??:?? on eth1.*.
Jun  2 07:49:51 ??? ntpdate[6476]: can't find host ntp.ubuntu.com 
Jun  2 07:49:51 ??? ntpdate[6476]: no servers can be used, exiting
Jun  2 07:49:57 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Jun  2 07:50:09 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jun  2 07:50:18 ??? dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Jun  2 07:50:18 ??? dhclient: DHCPOFFER from (my wireless router)
Jun  2 07:50:18 ??? dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Jun  2 07:50:18 ??? dhclient: DHCPACK from (my wireless router)
Jun  2 07:50:18 ??? dhclient: bound to (my laptop IP address) -- renewal in 37843 seconds.
Jun  2 07:50:18 ??? avahi-daemon[4710]: Joining mDNS multicast group on interface eth1.IPv4 with address (my laptop IP address)
Jun  2 07:50:18 ??? avahi-daemon[4710]: New relevant interface eth1.IPv4 for mDNS.
Jun  2 07:50:18 ??? avahi-daemon[4710]: Registering new address record for (my laptop IP address) on eth1.IPv4.
Jun  2 07:50:52 ??? ntpdate[6644]: step time server 82.211.81.145 offset 31.635053 sec

```






If you're still reading, my main question is what is avahi, and why is it trying to register an IP address that's nothing to do with me:

```
Jun  2 07:32:07 ??? avahi-daemon[4710]: Registering new address record for 169.254.10.2 on eth1.IPv4.
Jun  2 07:32:11 ??? avahi-autoipd(eth1)[5834]: Successfully claimed IP address 169.254.10.2
```

Is it that dhcp daemon, avahi and network manager are all fighting for control of the same interface?  Given that I'm using wpa_supplicant for my WPA wireless router, which should I be using?

---

