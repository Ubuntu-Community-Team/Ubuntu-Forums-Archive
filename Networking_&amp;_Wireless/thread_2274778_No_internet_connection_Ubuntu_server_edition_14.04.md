---
title: "No internet connection Ubuntu server edition 14.04 LTS"
date: 2015-04-22
forum: Networking &amp; Wireless
---

### Post by tech291083 on 2015-04-22
Hi Friends,

I have just installed Ubuntu 14.04 LTS Server distro (32 bit) off a DVD. I did not connect my LAN cable to the router at the time of the installation ie my pc was offline at the time of installation as I thought it might engage in downloading some packages during the installation itself thereby extending the overall time for installation. After successful installation, I am not able to access the internet via LAN using my router. I have my router assign different ips to pcs connected to it via wireless or LAN as it is a small home network. Can you please help me? I did restart the pc a few times. I want to install GUI and other packages once the internet becomes available. Thanks.

---

### Post by tech291083 on 2015-04-22
So far I have tried the following as root. 

sudo vi /etc/network/interfaces

It had the following 2 lines:

auto lo
iface lo inet loopback

and I added these 2 lines.

auto eth0
iface eth0 inet dhcp


Then I applied the following commands,

dhclient -r

/etc/init.d/networking restart

Rebooted the pc, but no internet yet. Thanks.

---

### Post by bbl232 on 2015-04-22
can you post the result of running

```
ifconfig
```

please?

---

### Post by tech291083 on 2015-04-24
> **bbl232 said:**
> can you post the result of running

```
ifconfig
```

please?

Here it is, thanks.
```

lo: Link encap:Local Loopback
    inet 127.0.0.1  netmask 255.0.0.0
    inet6 ::1/128  Scope:Host
    UP LOOPBACK RUNNING MTU:65536 Metric:1
    RX packets:48 errors:0 dropped:0 overruns:0 frame:0
    TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:3584 (3.5 KB)  TX bytes:3584 (3.5 KB)
```

---

### Post by michi1983 on 2015-04-24
Hey there,

please read this and provide the script in your next comment so we can see what hardware is built-in in your computer.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

You will have to download the script and copy it over to your Ubuntu machine when you don't have internet access right now.

Meanwhile you could try a ```
sudo ifup eth0
``` and an additional ```
sudo ifconfig
``` to see if the interface gets up.

Greetz

---

### Post by tech291083 on 2015-04-24
> **michi1983 said:**
> 
You will have to download the script and copy it over to your Ubuntu machine when you don't have internet access right now.

Meanwhile you could try a ```
sudo ifup eth0
``` and an additional ```
sudo ifconfig
``` to see if the interface gets up.

Greetz

I have just installed Ubuntu Server 14.04 LTS, which has no GUI at all, so please let me know how I can execute the script. Even if I copy it to pen drive after downloading on another pc of mine, how am I supposed to run this script? I am sorry, but this issue is killing me. I am a huge Ubuntu fan. This is putting me off. Please help. Thanks.

---

### Post by michi1983 on 2015-04-24
Devices like pen drives get mounted into /media folder. So download the script on a computer with internet access. 
Copy it to the pen drive and then copy it over to the Ubuntu machine.
From there just follow the steps from the link I posted earlier. 
Make it executable and let it run. Copy the created .txt file back to the pen drive and post the content of the .txt file here.

---

### Post by tech291083 on 2015-04-24
> **michi1983 said:**
> Devices like pen drives get mounted into /media folder. So download the script on a computer with internet access. 
Copy it to the pen drive and then copy it over to the Ubuntu machine.
From there just follow the steps from the link I posted earlier. 
Make it executable and let it run. Copy the created .txt file back to the pen drive and post the content of the .txt file here.

Meantime here is what I get when I do.

```
sudo ifup eth0
``` 

```

[I]cannot find device "eth0"
error getting hardware address for eth0: No such device
Failed to bring up eth0
[/I]
```

Thanks

---

### Post by tech291083 on 2015-04-24
Meantime here is what I get when I do.

```
sudo ifup eth0
``` 


```

sudo lshw -C network
  *-network   DISABLED            
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: p4p1
       version: 06
       serial: aa:aa:11:11:11:11 (I am deliberately giving you the wrong one, privacy concern, thanks)
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:24 ioport:e000(size=256) memory:f7c00000-f7c00fff memory:f0000000-f0003fff


```

---

### Post by tech291083 on 2015-04-24
Here is the outcome of ifconfig command from my another drive, which has only Fedora 20 installed and running on it, connected to the same pc. Ubuntu is installed on another drive altogether.

```
[root@localhost john]# ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 90  bytes 7724 (7.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 90  bytes 7724 (7.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

p4p1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.100  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::aaaa:1111:1111:1111  prefixlen 64  scopeid 0x20<link>
        ether aa:aa:11:11:11:11  txqueuelen 1000  (Ethernet)
        RX packets 5655  bytes 3875081 (3.6 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5330  bytes 680493 (664.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:7f:16:36  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

[root@localhost john]# 

```

Thanks.

---

### Post by tech291083 on 2015-04-24
> **michi1983 said:**
>  post the content of the .txt file here.

Here it is....the file is called ...wireless-info.txt

```

########## wireless info START ##########

Report from: 25 Apr 2015 08:00 IST +0530

Booted last: 25 Apr 2015 07:26 IST +0530

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/john/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 039: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 003: ID 0457:0150 Silicon Integrated Systems Corp. Super Talent 1GB Flash Drive
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless_script: line 176: rfkill: command not found

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

auto eth0 
iface eth0 inet dhcp

##### ifconfig ##########################

p4p1      Link encap:Ethernet  HWaddr <MAC 'p4p1' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

p4p1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### NetworkManager info ###############

./wireless_script: line 201: nmcli: command not found

./wireless_script: line 203: nmcli: command not found

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

Acquisition of admin privileges failed.

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

p4p1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

p4p1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

########## wireless info END ############


```

Thanks.

---

### Post by tech291083 on 2015-04-24
I am sure that someone will be help me now since the contents of the script are here for everyone to look into, thanks.

---

### Post by bbl232 on 2015-04-26
in /etc/network/interfaces
change
```

auto eth0
iface eth0 inet dhcp

```

to

```

auto p4p1
iface p4p1 inet dhcp

```

then run

```

sudo ifup p4p1

```

---

### Post by bbl232 on 2015-05-21
Did the interfaces change fix it?

---

### Post by tech291083 on 2015-06-25
Sorry, I had to install Windows on this drive and thus could not check the settings that you mentioned. But I will soon install Ubuntu Server again and do the settings as suggeted by you, thanks.

---

