---
title: "Realtek R8156 Driver( R8152.c) manual build and surviving patch"
date: 2022-04-17
forum: Networking &amp; Wireless
---

### Post by Andrew_Welham on 2022-04-17
I've had some issues with a r8156b usb to 2.5Gb ethernet  chip.

The default drivers don't allow full duplex. ( so i have requested to Ubuntu Launchpad to update)

In the mean time i have built  the drivers (with a few manual changes) and forced to install. All works well (so far).

If any one is interested i can explain how to build them, as the builds fail for Ubuntu Jammy.

My question is on Jammy when ever the kernel is patched i will need to reinstall the drivers. Is there a way to either block the upgrade for the driver or reinstall  my drivers automatically automatically.

Kind Regards
Andrew

---

### Post by mIk3_08 on 2022-04-17
> **Andrew_Welham said:**
> 
If any one is interested i can explain how to build them, as the builds fail for Ubuntu Jammy.

Can you elaborate more further because I am very interested on how did you do it. Thanks and Cheers.

---

### Post by jeremy31 on 2022-04-17
Moved to Networking
Can you upload your source code to github/gitlab so I could look into making it survive a kernel update

---

### Post by Andrew_Welham on 2022-04-17
So, I&#8217;m using the following usb3 to 2.5gb ethernet adapters. On both Ubuntu Jammy and Windows 11.
[https://www.amazon.co.uk/gp/product/B0856V9FDH/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B0856V9FDH/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1)
The key point is they have R8156B chips , which are supported by the Realtek R8152 driver which Realtek say are part of all kernel 5.6+.
Well in my experience they are, but they don&#8217;t work properly. The adapter is found but only runs at 2500 / half, and trying the commands in the driver Readme.txt file
ethtool -s eth0 autoneg on advertise 0x80000000002f
just gives an error.
I downloaded the drivers from
[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software)
The drivers build fine on Ubuntu focal, but fail on Jammy, not down to the GCC version ( I tried older versions). Looks to be due to some other kernel files.
This is where I am weak as I can&#8217;t code in C, C++.
When you build on Jammy you get
 
/home/andrew/r8152-2.15.0/r8152.c:18530:25: note: (near initialization for &#8216;ops.get_coalesce&#8217;)
/home/andrew/r8152-2.15.0/r8152.c:18531:25: error: initialization of &#8216;int (*)(struct net_device *, struct ethtool_coalesce *, struct kernel_ethtool_coalesce *, struct netlink_ext_ack *)&#8217; from incompatible pointer type &#8216;int (*)(struct net_device *, struct ethtool_coalesce *)&#8217; [-Werror=incompatible-pointer-types]
18531 | .set_coalesce = rtl8152_set_coalesce,
Following some googling I found this site
[https://sbexr.rabexc.org/latest/sources/26/53bfa290b96570.html#0000e00100031001](https://sbexr.rabexc.org/latest/sources/26/53bfa290b96570.html#0000e00100031001)
and it had some additional parameters for the call call
wil_ethtoolops_get_coalesce([struct net_device]("https://sbexr.rabexc.org/latest/sources/00/6c1112d024fa75.html#007ae001008f9001") *ndev,
                           [struct ethtool_coalesce]("https://sbexr.rabexc.org/latest/sources/fb/ba3154a4c199e0.html#001db001001f3001") *cp,
                           [struct kernel_ethtool_coalesce]("https://sbexr.rabexc.org/latest/sources/62/ae4293416fd0ba.html#000c7001000ca001") *kernel_coal,
                           [struct netlink_ext_ack]("https://sbexr.rabexc.org/latest/sources/0c/b0ee748ae17eee.html#0004d00100053001") *extack)
{
So, I just copied them, and took some guesses.
Happy to be corrected by a pro dev if I made the changes badly.
 
A diff between the original by my mode are
# diff ./r8152.c ../r8152-2.15.0/r8152.c
18339,18341c18339
< struct ethtool_coalesce *coalesce,
< struct kernel_ethtool_coalesce *,
< struct netlink_ext_ack *)
---
> struct ethtool_coalesce *coalesce)
18360,18363c18358
< struct ethtool_coalesce *coalesce,
< struct kernel_ethtool_coalesce *,
< struct netlink_ext_ack *)
<
---
> struct ethtool_coalesce *coalesce)
 
The code at least compiles now, throws and error at what looks like signing the code, but the .ko file was produced.
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
sign-file: certs/signing_key.pem: No such file or directory
I then ran 
make install 
sudo depmod -a
sudo update-initramfs -u
Rebooted
 
ethtool -s eth0 autoneg on advertise 0x802f
worked this time
Interface came up 2500/full.
 
Realised the rules file had not been copied, so I copied the rules file from the driver to the /etc/udev/rules.d directory
Rebooted again
 
I did have a driver crash on the first night (ubuntu working but no network), and read on google that the drivers can crash when instructed to go into sleep mode.
As a test I added
GRUB_CMDLINE_LINUX_DEFAULT="usbcore.autosuspend=-1"
To the /etc/default/grub file and updated grub.
Been 2 days and no crashes.
 
If you testing from windows with the rea tek drivers you get 2.3+ Gb for
Ipref3 -c server -R
And about 1.4-1.6Gb for
Ipref3 -c server
 
This is the same for windows to windows and the fix is to enable &#8220;Miscellaneous Transfer setting&#8221; in the windows adapter driver advanced configuration. I now get
 
c:\iperf-3.1.3-win64>iperf3 -c testsvr
Connecting to host testsvr, port 5201
[ 4] local 192.168.1.6 port 51115 connected to x.x.x.x port 5201
[ ID] Interval      Transfer   Bandwidth
[ 4]  0.00-1.00  sec  278 MBytes 2.33 Gbits/sec
[ 4]  1.00-2.00  sec  279 MBytes 2.34 Gbits/sec
[ 4]  2.00-3.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  3.00-4.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  4.00-5.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  5.00-6.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  6.00-7.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  7.00-8.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  8.00-9.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  9.00-10.00 sec  280 MBytes 2.35 Gbits/sec
&#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211;
[ ID] Interval      Transfer   Bandwidth
[ 4]  0.00-10.00 sec 2.73 GBytes 2.35 Gbits/sec         sender
[ 4]  0.00-10.00 sec 2.73 GBytes 2.35 Gbits/sec         receiver
 
iperf Done.
 
c:\iperf-3.1.3-win64>iperf3 -c testsvr -R
Connecting to host testsvr, port 5201
Reverse mode, remote host testsvr is sending
[ 4] local 192.168.1.6 port 51119 connected to x.x.x.x port 5201
[ ID] Interval      Transfer   Bandwidth
[ 4]  0.00-1.00  sec  283 MBytes 2.38 Gbits/sec
[ 4]  1.00-2.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  2.00-3.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  3.00-4.00  sec  282 MBytes 2.36 Gbits/sec
[ 4]  4.00-5.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  5.00-6.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  6.00-7.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  7.00-8.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  8.00-9.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  9.00-10.00 sec  283 MBytes 2.37 Gbits/sec
&#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211; &#8211;
[ ID] Interval      Transfer   Bandwidth    Retr
[ 4]  0.00-10.00 sec 2.76 GBytes 2.37 Gbits/sec  0       sender
[ 4]  0.00-10.00 sec 2.76 GBytes 2.37 Gbits/sec         receiver
 
iperf Done.
 
 
I&#8217;ve logged a request for a new driver for ubuntu  here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1969211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1969211)
 
Found someone else was having issues so posted here
[https://www.cnx-software.com/2022/02/20/fixing-performance-issues-with-realtek-rtl8156b-2-5gbe-usb-dongle-in-ubuntu/](https://www.cnx-software.com/2022/02/20/fixing-performance-issues-with-realtek-rtl8156b-2-5gbe-usb-dongle-in-ubuntu/)
 
@ [**jeremy31**]("https://ubuntuforums.org/member.php?u=1924242")  I don&#8217;t own the code, so not sure if I can, I have linked to the code above. The changes I made probably need to be reviewed by a pro dev

---

### Post by jeremy31 on 2022-04-17
Does it work if you ```
sudo rmmod cdc_mbim
sudo rmmod cdc_ncm
```

I would think the original kernel module has been updated since the download from Realtek and the version numbers can be ignored

---

### Post by Andrew_Welham on 2022-04-18
[FONT=arial]I will test after the next firmware upgrade when my driver gets over written( not sure how to replace other wise). The newer file is around twice the size as a source code[/FONT]

---

### Post by Andrew_Welham on 2022-04-19
Dropped back to kernel 5.15.0-23-generic


# ethtool enx5c857e38e9b7
Settings for enx5c857e38e9b7:
        Supported ports: [  ]
        Supported link modes:   Not reported
        Supported pause frame use: No
        Supports auto-negotiation: No
        Supported FEC modes: Not reported
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Advertised FEC modes: Not reported
        Speed: 2500Mb/s
        Duplex: Half
        Auto-negotiation: off
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        MDI-X: Unknown
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes




# ethtool -s enx5c857e38e9b7 autoneg on advertise 0x80000000002f
netlink error: Operation not supported






# rmmod cdc_mbim
# rmmod cdc_ncm
#  ethtool -s enx5c857e38e9b7 autoneg on advertise 0x80000000002f
netlink error: no device matches name (offset 24)
netlink error: No such device




i cant upgrade the kernel above 5.15.0-23 any more, no options are showing

---

### Post by Andrew_Welham on 2022-04-19
checking the drivers

```
# lshw -c network

  *-network
       description: Ethernet interface
       physical id: 4
       bus info: usb@10:1
       logical name: enx5c857e38e9b7
       serial: 5c:85:7e:38:e9:b7
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=cdc_ncm driverversion=5.15.0-23-generic duplex=half firmware=CDC NCM link=yes multicast=yes port=twisted pair
```

which is why the device disappeared

modprobe r8156 started the driver but did nothing, even after a  reboot

copying the rules file

# more 50-usb-realtek-net.rules
# This is used to change the default configuration of Realtek USB ethernet adapters


```
ACTION!="add", GOTO="usb_realtek_net_end"
SUBSYSTEM!="usb", GOTO="usb_realtek_net_end"
ENV{DEVTYPE}!="usb_device", GOTO="usb_realtek_net_end"


# Modify this to change the default value
ENV{REALTEK_MODE1}="1"
ENV{REALTEK_MODE2}="3"


# Realtek
ATTR{idVendor}=="0bda", ATTR{idProduct}=="815[2,3,5,6]", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="0bda", ATTR{idProduct}=="8053", ATTR{bcdDevice}=="e???", ATTR{bConfigurationValue}!="$env{REALTEK_MODE2}", ATTR{bConfigurationValue}="$env{REALTEK_MODE2}"


# Samsung
ATTR{idVendor}=="04e8", ATTR{idProduct}=="a101", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"


# Lenovo
ATTR{idVendor}=="17ef", ATTR{idProduct}=="304f", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3052", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3054", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3057", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3062", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3069", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3082", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="3098", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="7205", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="720a", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="720b", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="720c", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="7214", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="721e", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="8153", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="a359", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"
ATTR{idVendor}=="17ef", ATTR{idProduct}=="a387", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"


# TP-LINK
ATTR{idVendor}=="2357", ATTR{idProduct}=="0601", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"


# Nvidia
ATTR{idVendor}=="0955", ATTR{idProduct}=="09ff", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"


# LINKSYS
ATTR{idVendor}=="13b1", ATTR{idProduct}=="0041", ATTR{bConfigurationValue}!="$env{REALTEK_MODE1}", ATTR{bConfigurationValue}="$env{REALTEK_MODE1}"


LABEL="usb_realtek_net_end"
```

and rebooting a couple of times bought the interface back

now with the right driver

```
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       bus info: usb@10:1
       logical name: enx5c857e38e9b7
       serial: 5c:85:7e:38:e9:b7
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8152 driverversion=v1.12.12 duplex=full firmware=rtl8156b-2 v1 04/15/21 link=no multicast=yes port=MII
#

```manually configuring the ip (just for now)

```
# ip addr add 192.168.1.200/24 dev enx5c857e38e9b7
# ip link set enx5c857e38e9b7 up
```

iperf3 rates as expected around 2.36Gbs - 2.37Gbs in both directions.

The error -71 talked about on [https://www.cnx-software.com/2022/02...gle-in-ubuntu/]("https://www.cnx-software.com/2022/02/20/fixing-performance-issues-with-realtek-rtl8156b-2-5gbe-usb-dongle-in-ubuntu/")

which i did see once, looks to have been fixed in the rc3 of the latest kernel, so should be making its way down the distributions..

Just stuck with an old kernel

```

# uname -r
5.15.0-23-generic
# apt update
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease [270 kB]
Hit:2 [https://ppa.launchpadcontent.net/nextcloud-devs/client/ubuntu](https://ppa.launchpadcontent.net/nextcloud-devs/client/ubuntu) jammy InRelease
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease
Fetched 270 kB in 0s (670 kB/s)


Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
# apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
# apt dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
although i do remember seeing some weird message about 5.15.0-25-generic from the installer.

---

### Post by mIk3_08 on 2022-04-19
> **Andrew_Welham said:**
> So, I’m using the following usb3 to 2.5gb ethernet adapters. On both Ubuntu Jammy and Windows 11.
[https://www.amazon.co.uk/gp/product/B0856V9FDH/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1](https://www.amazon.co.uk/gp/product/B0856V9FDH/ref=ppx_od_dt_b_asin_title_s00?ie=UTF8&psc=1)
The key point is they have R8156B chips , which are supported by the Realtek R8152 driver which Realtek say are part of all kernel 5.6+.
Well in my experience they are, but they don’t work properly. The adapter is found but only runs at 2500 / half, and trying the commands in the driver Readme.txt file
ethtool -s eth0 autoneg on advertise 0x80000000002f
just gives an error.
I downloaded the drivers from
[https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software](https://www.realtek.com/en/component/zoo/category/network-interface-controllers-10-100-1000m-gigabit-ethernet-usb-3-0-software)
The drivers build fine on Ubuntu focal, but fail on Jammy, not down to the GCC version ( I tried older versions). Looks to be due to some other kernel files.
This is where I am weak as I can’t code in C, C++.
When you build on Jammy you get
 
/home/andrew/r8152-2.15.0/r8152.c:18530:25: note: (near initialization for ‘ops.get_coalesce’)
/home/andrew/r8152-2.15.0/r8152.c:18531:25: error: initialization of ‘int (*)(struct net_device *, struct ethtool_coalesce *, struct kernel_ethtool_coalesce *, struct netlink_ext_ack *)’ from incompatible pointer type ‘int (*)(struct net_device *, struct ethtool_coalesce *)’ [-Werror=incompatible-pointer-types]
18531 | .set_coalesce = rtl8152_set_coalesce,
Following some googling I found this site
[https://sbexr.rabexc.org/latest/sources/26/53bfa290b96570.html#0000e00100031001](https://sbexr.rabexc.org/latest/sources/26/53bfa290b96570.html#0000e00100031001)
and it had some additional parameters for the call call
wil_ethtoolops_get_coalesce([struct net_device]("https://sbexr.rabexc.org/latest/sources/00/6c1112d024fa75.html#007ae001008f9001") *ndev,
                           [struct ethtool_coalesce]("https://sbexr.rabexc.org/latest/sources/fb/ba3154a4c199e0.html#001db001001f3001") *cp,
                           [struct kernel_ethtool_coalesce]("https://sbexr.rabexc.org/latest/sources/62/ae4293416fd0ba.html#000c7001000ca001") *kernel_coal,
                           [struct netlink_ext_ack]("https://sbexr.rabexc.org/latest/sources/0c/b0ee748ae17eee.html#0004d00100053001") *extack)
{
So, I just copied them, and took some guesses.
Happy to be corrected by a pro dev if I made the changes badly.
 
A diff between the original by my mode are
# diff ./r8152.c ../r8152-2.15.0/r8152.c
18339,18341c18339
< struct ethtool_coalesce *coalesce,
< struct kernel_ethtool_coalesce *,
< struct netlink_ext_ack *)
---
> struct ethtool_coalesce *coalesce)
18360,18363c18358
< struct ethtool_coalesce *coalesce,
< struct kernel_ethtool_coalesce *,
< struct netlink_ext_ack *)
<
---
> struct ethtool_coalesce *coalesce)
 
The code at least compiles now, throws and error at what looks like signing the code, but the .ko file was produced.
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:69
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:76
sign-file: certs/signing_key.pem: No such file or directory
I then ran 
make install 
sudo depmod -a
sudo update-initramfs -u
Rebooted
 
ethtool -s eth0 autoneg on advertise 0x802f
worked this time
Interface came up 2500/full.
 
Realised the rules file had not been copied, so I copied the rules file from the driver to the /etc/udev/rules.d directory
Rebooted again
 
I did have a driver crash on the first night (ubuntu working but no network), and read on google that the drivers can crash when instructed to go into sleep mode.
As a test I added
GRUB_CMDLINE_LINUX_DEFAULT="usbcore.autosuspend=-1"
To the /etc/default/grub file and updated grub.
Been 2 days and no crashes.
 
If you testing from windows with the rea tek drivers you get 2.3+ Gb for
Ipref3 -c server -R
And about 1.4-1.6Gb for
Ipref3 -c server
 
This is the same for windows to windows and the fix is to enable “Miscellaneous Transfer setting” in the windows adapter driver advanced configuration. I now get
 
c:\iperf-3.1.3-win64>iperf3 -c testsvr
Connecting to host testsvr, port 5201
[ 4] local 192.168.1.6 port 51115 connected to x.x.x.x port 5201
[ ID] Interval      Transfer   Bandwidth
[ 4]  0.00-1.00  sec  278 MBytes 2.33 Gbits/sec
[ 4]  1.00-2.00  sec  279 MBytes 2.34 Gbits/sec
[ 4]  2.00-3.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  3.00-4.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  4.00-5.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  5.00-6.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  6.00-7.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  7.00-8.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  8.00-9.00  sec  280 MBytes 2.35 Gbits/sec
[ 4]  9.00-10.00 sec  280 MBytes 2.35 Gbits/sec
– – – – – – – – – – – – – – – – – – – – – – – – –
[ ID] Interval      Transfer   Bandwidth
[ 4]  0.00-10.00 sec 2.73 GBytes 2.35 Gbits/sec         sender
[ 4]  0.00-10.00 sec 2.73 GBytes 2.35 Gbits/sec         receiver
 
iperf Done.
 
c:\iperf-3.1.3-win64>iperf3 -c testsvr -R
Connecting to host testsvr, port 5201
Reverse mode, remote host testsvr is sending
[ 4] local 192.168.1.6 port 51119 connected to x.x.x.x port 5201
[ ID] Interval      Transfer   Bandwidth
[ 4]  0.00-1.00  sec  283 MBytes 2.38 Gbits/sec
[ 4]  1.00-2.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  2.00-3.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  3.00-4.00  sec  282 MBytes 2.36 Gbits/sec
[ 4]  4.00-5.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  5.00-6.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  6.00-7.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  7.00-8.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  8.00-9.00  sec  283 MBytes 2.37 Gbits/sec
[ 4]  9.00-10.00 sec  283 MBytes 2.37 Gbits/sec
– – – – – – – – – – – – – – – – – – – – – – – – –
[ ID] Interval      Transfer   Bandwidth    Retr
[ 4]  0.00-10.00 sec 2.76 GBytes 2.37 Gbits/sec  0       sender
[ 4]  0.00-10.00 sec 2.76 GBytes 2.37 Gbits/sec         receiver
 
iperf Done.
 
 
I’ve logged a request for a new driver for ubuntu  here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1969211](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1969211)
 
Found someone else was having issues so posted here
[https://www.cnx-software.com/2022/02/20/fixing-performance-issues-with-realtek-rtl8156b-2-5gbe-usb-dongle-in-ubuntu/](https://www.cnx-software.com/2022/02/20/fixing-performance-issues-with-realtek-rtl8156b-2-5gbe-usb-dongle-in-ubuntu/)
 
@ [**jeremy31**]("https://ubuntuforums.org/member.php?u=1924242")  I don’t own the code, so not sure if I can, I have linked to the code above. The changes I made probably need to be reviewed by a pro dev

I'm gonna study whats inside of this ".c" of the driver maybe I can get some  Idea for this. Thanks for sharing. This is a big help. Regards and  cheers.

---

### Post by Andrew_Welham on 2022-04-19
@[[COLOR=#000000]mIk3_08[/COLOR]]("https://ubuntuforums.org/member.php?u=2079368")[COLOR=#000000]  The firmware is inside the downloaded driver. I  put the drivers from the latest kernel rc3 and the original driver into winmerge , lots of the code is the same. You can see some bug fixes, but there is firmware in the one downloaded from Realtek, where as the linux version references external drivers.


Did you see the post i got it working with the default drivers. The instruction are above


Just got to work out how to get back the the latest kernel as i appear stuck

[/COLOR]

---

