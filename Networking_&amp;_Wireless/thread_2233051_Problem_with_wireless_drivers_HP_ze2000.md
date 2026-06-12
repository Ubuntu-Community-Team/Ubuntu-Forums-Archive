---
title: "Problem with wireless drivers HP ze2000"
date: 2014-07-06
forum: Networking &amp; Wireless
---

### Post by frodoswaggins on 2014-07-06
Hi,

I read in this thread ([http://ubuntuforums.org/showthread.php?t=2198189](http://ubuntuforums.org/showthread.php?t=2198189))  and I have the same problem. I dont know which wireless card I have, the model is the same but maybe its another card, no? How can I view which is my card?

Bucky ball said in the other thread, first post from him to do these things:

sudo lshw -C network

ze2000@ze2000-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:9f:21:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.15 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:a000(size=256) memory:d0208000-d02080ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0204000-d0205fff
ze2000@ze2000-laptop:~$ 


I dont find anything 'b43' under additonal drivers.

I tried to do this command:
sudo apt-get install b43-fwcutter firmware-b43-installer

And it didnt work. I installed it and it didnt work with that.

Maybe someone have some other tips :).

---

### Post by squakie on 2014-07-06
Take a look at the last 3 posts in [this]("http://ubuntuforums.org/showthread.php?t=2231879&page=3") thread - it may help you.  Particulary, follow the instructions for loading the firmware then removing and loading the driver module afterwards.

---

### Post by varunendra on 2014-07-06
Welcome to the forums frodoswaggins!

It seems you have a working Ethernet connection and you can connect to internet via that. If yes, the easiest way to install the firmware is the command -
```
sudo apt-get install linux-firmware-nonfree
```
..followed by a reboot. The commands are obviously to be entered in a terminal (Ctrl-Alt-T).

Although the "sudo apt-get install b43-fwcutter firmware-b43-installer" commands should also have worked. Did you reboot after running them?

If installing the firmware (and rebooting) doesn't work, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by frodoswaggins on 2014-07-06
> **varunendra said:**
> Welcome to the forums frodoswaggins!

It seems you have a working Ethernet connection and you can connect to internet via that. If yes, the easiest way to install the firmware is the command -
```
sudo apt-get install linux-firmware-nonfree
```
..followed by a reboot. The commands are obviously to be entered in a terminal (Ctrl-Alt-T).

Although the "sudo apt-get install b43-fwcutter firmware-b43-installer" commands should also have worked. Did you reboot after running them?

If installing the firmware (and rebooting) doesn't work, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

Thanks man, I tried what you said first, and it didnt work.

 Yes I rebooted and I took help from a friend that has more experience than I, but we didnt get it to work.

I tried what you said in thread. Here is all that was in the terminal (im not sure if I should had selected only a part, but here's all :) ):

```
ze2000@ze2000-laptop:~$ wget -N -t 5 -T 10 https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-07-06 11:51:55--  https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropbox.com... 54.225.245.82
Connecting to dl.dropbox.com|54.225.245.82|:443... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script [following]
--2014-07-06 11:51:55--  https://dl.dropboxusercontent.com/s/qjc87hzk1z5x6z0/wireless_script
Resolving dl.dropboxusercontent.com... 54.225.82.235, 54.225.207.39, 54.243.60.55, ...
Connecting to dl.dropboxusercontent.com|54.225.82.235|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15531 (15K) [text/plain]
Saving to: `wireless_script'

100%[======================================>] 15,531      --.-K/s   in 0s      

Last-modified header missing -- time-stamps turned off.
2014-07-06 11:51:56 (232 MB/s) - `wireless_script' saved [15531/15531]



        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')

[sudo] password for ze2000: 


    ########################################################################

    DONE! All results saved in -

         File Name:     "wireless-info.txt" 
         Directory:     "/home/ze2000"

    Please upload the above file or its contents where you are seeking help.

    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------

    ########################################################################



ze2000@ze2000-laptop:~$ 


```

I havent tried if it works yet, I will reboot and try right now.

---

### Post by frodoswaggins on 2014-07-06
And nope, it didnt work. 

I will try with the second answer in this thread.

---

### Post by varunendra on 2014-07-06
> **frodoswaggins said:**
> ```
....
    ########################################################################

    **DONE! All results saved in -**

         File Name:     "**wireless-info.txt**" 
         Directory:     "/home/ze2000"

    **Please upload the above file or its contents where you are seeking help.**
....
....
    ########################################################################
```

I need to see the contents of the '**wireless-info.txt**' file created in your home directory. That is the file that the script generated and contains a detailed information about your wireless setup (with all sensitive information, if any, filtered out).

---

### Post by frodoswaggins on 2014-07-06
> **varunendra said:**
> I need to see the contents of the '**wireless-info.txt**' file created in your home directory. That is the file that the script generated and contains a detailed information about your wireless setup (with all sensitive information, if any, filtered out).

Here it is :). Thanks for your help!

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ze2000-laptop 2.6.32-62-generic i686,  Ubuntu 10.04.4 LTS, lucid

CPU    : Mobile AMD Sempron(tm) Processor 3000+
Memory : 464 MB
Uptime : 11:51:56 up  1:54,  2 users,  load average: 0.47, 0.29, 0.15


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Kernel modules: ssb
05:09.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




module parameters ~~~~~~~~~~~~~~~~~~


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected
ooooooo
 Interface & ID    | Type  | Driver  | State        | Default | Speed     | Support      | HW Addr   
ooooooo
 eth0  [Auto eth0] | Wired | 8139too | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             190.157.8.33
    DNS:             181.48.0.229
+++++++


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

nm-system-settings.conf (used up to 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false



NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

Wireless connection 1 : ssid=72;65;84;79;71;82;65;78;68;69; | autoconnect=false | ipv4=auto | ipv6=ignore | mtu=0 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 190.157.8.33
nameserver 181.48.0.229


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.utf8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist ssb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4318 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x0bda:0x8189 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
broadcom-sta-common.conf: blacklist b44
                    blacklist b43legacy
                    blacklist b43
                    blacklist ssb
                    install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
sl-modem.conf     : install slamr /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slamr; test -e /dev/slamr0 && (chmod 660 /dev/slamr0 && chgrp dialout /dev/slamr0) || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0)
                    remove slamr /sbin/modprobe --remove --ignore-remove slamr; test -e /dev/slamr0 && /bin/rm -f /dev/slamr0 2>/dev/null
                    install slusb /sbin/modprobe -qb ungrab-winmodem; /sbin/modprobe --ignore-install slusb; test -e /dev/slusb0 && (chmod 660 /dev/slusb0 && chgrp dialout /dev/slusb0) || (/bin/mknod -m 660 /dev/slusb0 c 243 0 2>/dev/null && chgrp dialout /dev/slusb0)
                    remove slusb /sbin/modprobe --remove --ignore-remove slusb; test -e /dev/slusb0 && /bin/rm -f /dev/slusb0 2>/dev/null

[/etc/pm/config.d/00sleep_module]
# The sleep/wake system to use.  Valid values are:
#   kernel    The built-in kernel suspend/resume support.
#             Use this if nothing else is supported on your system.
#   uswsusp   If your system has support for the userspace
#             suspend programs (s2ram/s2disk/s2both), then use this.
#   tuxonice  If your system has support for tuxonice, use this.
#
# The system defaults to "kernel" if this is commented out.
# SLEEP_MODULE="kernel"

[/etc/pm/sleep.d/action_wpa] [executable]
#!/bin/sh

# Action script to enable/disable wpa-roam interfaces in reaction to
# pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2008-2009, Kel Modderman <kel@otaku42.de>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

if [ ! -x /sbin/wpa_action ]; then
    exit 0
fi

SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, disconnect any wpa-roam managed interfaces,
# reconnect it on resume.

case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac

if [ -z "$COMMAND" ]; then
    # ifplugd(8) - <iface> <action>
    #
    # If an ifplugd managed interface is brought up, disconnect any
    # wpa-roam managed interfaces so that only one "roaming" interface
    # remains active on the system.

    IFPLUGD_IFACE="${1}"

    case "${2}" in
        up)
            COMMAND=disconnect
            ;;
        down)
            COMMAND=reconnect
            ;;
        *)
            echo "${SELF}: unknown $0 arguments: ${@}" >&2
            exit 1
            ;;
        esac
fi

if [ -z "$COMMAND" ]; then
    echo "${SELF}: unknown arguments: ${@}" >&2
    exit 1
fi

for CTRL in /var/run/wpa_supplicant/*; do
    [ -S "${CTRL}" ] || continue

    IFACE="${CTRL#/var/run/wpa_supplicant/}"

    wpa_action "${IFACE}" check || continue

    if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
        # if ifplugd is managing this interface (not likely but..)
        # do nothing
        continue
    fi

    wpa_cli -i "${IFACE}" "${COMMAND}"
done


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-2.6.32-62-generic root=UUID=1b260d2d-2ac9-4639-82a4-af463d4bff4d ro quiet splash


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.004263] Initializing cgroup subsys net_cls
[    0.823595] audit: initializing netlink socket (disabled)
[    1.812104] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.195908] 8139too Fast Ethernet driver 0.9.28
[   21.561562] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin

    ======== Done ========
```

---

### Post by Hadaka on 2014-07-06
Hi, with the cable connected to the internet
and the usb wifi NOT in..unplugged please do,,
*Ignore any errors, but copy and paste each line anyway
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do.
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
remove the cable and BOOT
test wireless

---

### Post by frodoswaggins on 2014-07-06
> **Hadaka said:**
> Hi, with the cable connected to the internet
and the usb wifi NOT in..unplugged please do,,
*Ignore any errors, but copy and paste each line anyway
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do.
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
remove the cable and BOOT
test wireless

The usb wifi was connected before. But not when I ran that command...

Anyway thanks a lot! It's working now!

---

### Post by Hadaka on 2014-07-06
Glad it's working !!
Please mark this thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Takashi_Kosaka on 2014-12-22
I have a HP ze2000 bcm4318. Several month ago, it worked. But, I have  tried re-install Ubuntu12.04 from CD, all methods dose not work.
Also, when I tried to update, OS can not shut down and wifi does not work.
When I tried the followings:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

ze2000 becomes crashed GUI screen and shows a terminal mode 
and OS hangs up.

When I tried 
just update by GUI, OS can not shut down.

Also, when I tried to upgrade OS14.04, Installing fail. In this time, OS had sent error messages to Ubuntu.

---

### Post by Masood_Ejaz on 2015-06-27
I just installed Lubuntu 15.04 and it did not find the driver for the wireless adaptor although it did recognize the adaptor (Broadcom). I used the same that I used when I installed older version of Ubuntu and it worked. Here is what I did:

-----------------------------------------------------------------------
HP ze2000 - Wireless Network adaptor
--------------------------------------
Broadcom Corporation BCM4318 (Airforce 1 54G) 802.11g. Wirless LAN controller [14e4:4318]

Drivers available in Ubuntu
----------------------------
b43 - Open source driver

For Chip ID BCM4306 (rev 03), BCM4309, BCM4311, BCM4312, BCM4318, BCM4322, BCM4331, BCM43224 and BCM43225.

If you do not have any other means of Internet access from Ubuntu, then you will have to download the firmware from another computer with Internet access, from an existing OS on another partition, or before you install Ubuntu. You will also need the b43-fwcutter package which is usually included on the install media or can be downloaded from the official online repositories.


Install the b43-fwcutter package ([https://launchpad.net/ubuntu/+source/b43-fwcutter](https://launchpad.net/ubuntu/+source/b43-fwcutter)). This is usually located on the Ubuntu install media under /cdrom/pool/main/b/b43-fwcutter/ or you can download the binary '.deb' package by following the links on launchpad (Note: For Lubuntu, install from Ubuntu as the folder is not available in Lubuntu)

Double click on the package to install or in a Terminal issue the following commands:

        cd /cdrom/pool/main/b/b43-fwcutter/
        sudo dpkg -i b43-fwcutter*

If you already have broadcom-wl-4.150.10.5 folder, copy it in home directory and perform the following in terminal

sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

If you do not have the folder then copy broadcom-wl-4.150.10.5.tar ([http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)) in home directory and perform the following in terminal:

    tar xfvj broadcom-wl-4.150.10.5.tar.bz2
    sudo b43-fwcutter -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

Restart system.

-----------------------------------------------------------

---

