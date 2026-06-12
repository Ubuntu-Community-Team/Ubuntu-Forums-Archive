---
title: "USB 3.0 to Ethernet converters not working after reboot."
date: 2024-08-29
forum: Networking &amp; Wireless
---

### Post by Sathyanarayanan on 2024-08-29
Hi All,

I am trying to do some testing with Raspberry PI running Ubuntu 

```
PRETTY_NAME="Ubuntu 24.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.1 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

```

This is the output of lsusb

```
orange@orange-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 2109:3431 VIA Labs, Inc. Hub
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The USB to Ethernet Adapter is visible here "Bus 002 Device 002: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter" but the same is not displayed in ip a

Output of ip a

```
orange@orange-desktop:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether dc:a6:32:54:1f:be brd ff:ff:ff:ff:ff:ff
    inet 192.168.29.5/24 brd 192.168.29.255 scope global dynamic noprefixroute eth0
       valid_lft 3354sec preferred_lft 3354sec
    inet6 2405:201:f003:18c0:dea6:32ff:fe54:1fbe/64 scope global dynamic noprefixroute 
       valid_lft 3601sec preferred_lft 3601sec
    inet6 fe80::dea6:32ff:fe54:1fbe/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether dc:a6:32:54:1f:bf brd ff:ff:ff:ff:ff:ff
    inet 192.168.29.117/24 brd 192.168.29.255 scope global dynamic noprefixroute wlan0
       valid_lft 3356sec preferred_lft 3356sec
    inet6 2405:201:f003:18c0:33:3932:d471:10e6/64 scope global temporary dynamic 
       valid_lft 3601sec preferred_lft 3601sec
    inet6 2405:201:f003:18c0:38e5:e813:75fb:871e/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3601sec preferred_lft 3601sec
    inet6 fe80::d9eb:a3a2:cdb6:d6b6/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

The device will work flawlessly if I unplug it from USB and reconnect it back. 
It will not work after the system is rebooted, unless you disconnect the device from USB and plug it back in.
I have tried it with multiple USB to Ethernet converters but all of them had the same issue.
Any work around or solutions are highly appreciated.

Forgot to add the results of working USB to Ethernet Converter.
As soon as I reconnect the USB device it shows up in ip a

```
orange@orange-desktop:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether dc:a6:32:54:1f:be brd ff:ff:ff:ff:ff:ff
    inet 192.168.29.5/24 brd 192.168.29.255 scope global dynamic noprefixroute eth0
       valid_lft 2965sec preferred_lft 2965sec
    inet6 2405:201:f003:18c0:dea6:32ff:fe54:1fbe/64 scope global dynamic noprefixroute 
       valid_lft 3594sec preferred_lft 3594sec
    inet6 fe80::dea6:32ff:fe54:1fbe/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
4: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether dc:a6:32:54:1f:bf brd ff:ff:ff:ff:ff:ff
    inet 192.168.29.117/24 brd 192.168.29.255 scope global dynamic noprefixroute wlan0
       valid_lft 2967sec preferred_lft 2967sec
    inet6 2405:201:f003:18c0:33:3932:d471:10e6/64 scope global temporary dynamic 
       valid_lft 3594sec preferred_lft 3594sec
    inet6 2405:201:f003:18c0:38e5:e813:75fb:871e/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3594sec preferred_lft 3594sec
    inet6 fe80::d9eb:a3a2:cdb6:d6b6/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
5: enx00e04c234e98: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:e0:4c:23:4e:98 brd ff:ff:ff:ff:ff:ff
    inet 192.168.29.144/24 brd 192.168.29.255 scope global dynamic noprefixroute enx00e04c234e98
       valid_lft 3470sec preferred_lft 3470sec
    inet6 2405:201:f003:18c0:fec7:99eb:e079:ac6f/64 scope global temporary dynamic 
       valid_lft 3594sec preferred_lft 3594sec
    inet6 2405:201:f003:18c0:5c3a:e1d9:bfb5:24c1/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 3594sec preferred_lft 3594sec
    inet6 fe80::66eb:6ee2:e6a3:dcff/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```


Regards,
Sathya

---

### Post by TheFu on 2024-08-29
Did you try unplugging the built-in ethernet and only having the USB-2-ethernet converter connected?

I've never tried to connect a second ethernet to a Pi.  I have used bonded connections but those are using PCIe adapters on x64 systems, not PIs.

Also, the exact version of r-pi hardware could be important.

You posted the output from the **ip** command, but not system boot logs related to the ethernet adapters.  What do those look like? Any errors or warnings?  When I searched my logs, only the cloud-init log had ethernet debug messages.  Since my systems are all static IPs, not DHCP, I suspect things work different than what you are seeing.  I''ve been burned by using DHCP too many times.

---

### Post by Sathyanarayanan on 2024-08-30
Thank you for your reply, I am using Raspberry PI4, 4GB variant.

I tested with the On-board ethernet disconnected, and the results are the same. The USB to Ethernet is not working unless it is replugged.

I also tried adding a USB3 to wifi from TP-Link it works flawlessly even after reboot.

Regards,
Sathya

---

### Post by Sathyanarayanan on 2024-09-01
I was able to find a work around for the USB issue, putting it here so that it would be useful for some other people

I created a file "/etc/systemd/system/rtl8153-reload.service "

and added the below

```

Unit]
Description=Reload Realtek RTL8153 Ethernet Adapter
After=multi-user.target

[Service]
ExecStart=/bin/bash -c 'sleep 10; modprobe -r r8152 && modprobe r8152'

[Install]
WantedBy=multi-user.target



```


and then invoked it with the following command

sudo systemctl enable rtl8153-reload.service


Everything started working even after reboot.

---

### Post by ajgreeny on 2024-09-01
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction.
I realise that this is something of a workaround but it does seem to be a solution to your problem.

It is a great help to users searching the forum.

---

