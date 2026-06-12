---
title: "Auto fix Wifi [Headless Server]"
date: 2015-12-19
forum: Networking &amp; Wireless
---

### Post by pqwoerituytrueiwoq on 2015-12-19
I am using a Raspberry pi A+ as a wifi thermostat, anyone have any thoughts on imporoving my current repair script
I think my ping test is getting false negatives (or my action is overkill), but just checking if the wlan has a ip address does not mean it is connected as i have been unable to connect from time to time
Wifi scan:
```
pi@thermostat ~ $ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 10:6F:3F:D9:17:F4
                    ESSID:"My WiFi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=100/100  
          Cell 02 - Address: 12:6F:3F:D9:17:F4
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=100/100  Signal level=100/100 
``` 
config:
```
pi@thermostat ~ $ sudo iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Chad's WiFi"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 10:6F:3F:D9:17:F4   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Wireless chip:
```
pi@thermostat ~ $ sudo lsusb -vvs 001:003

Bus 001 Device 003: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x7392 Edimax Technology Co., Ltd
  idProduct          0x7811 EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
  bcdDevice            2.00
  iManufacturer           1 Realtek
  iProduct                2 802.11n WLAN Adapter
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```
Ping results:
```
pi@thermostat ~ $ ping 10.0.0.1 -c 20
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
64 bytes from 10.0.0.1: icmp_req=1 ttl=64 time=3.32 ms
64 bytes from 10.0.0.1: icmp_req=2 ttl=64 time=5.79 ms
64 bytes from 10.0.0.1: icmp_req=3 ttl=64 time=5.78 ms
64 bytes from 10.0.0.1: icmp_req=4 ttl=64 time=5.70 ms
64 bytes from 10.0.0.1: icmp_req=5 ttl=64 time=5.77 ms
64 bytes from 10.0.0.1: icmp_req=6 ttl=64 time=2.50 ms
64 bytes from 10.0.0.1: icmp_req=7 ttl=64 time=8.07 ms
64 bytes from 10.0.0.1: icmp_req=8 ttl=64 time=3.96 ms
64 bytes from 10.0.0.1: icmp_req=9 ttl=64 time=5.79 ms
64 bytes from 10.0.0.1: icmp_req=10 ttl=64 time=5.70 ms
64 bytes from 10.0.0.1: icmp_req=11 ttl=64 time=5.77 ms
64 bytes from 10.0.0.1: icmp_req=12 ttl=64 time=5.72 ms
64 bytes from 10.0.0.1: icmp_req=13 ttl=64 time=5.75 ms
64 bytes from 10.0.0.1: icmp_req=14 ttl=64 time=5.74 ms
64 bytes from 10.0.0.1: icmp_req=15 ttl=64 time=6.10 ms
64 bytes from 10.0.0.1: icmp_req=16 ttl=64 time=7.41 ms
64 bytes from 10.0.0.1: icmp_req=17 ttl=64 time=3.24 ms
64 bytes from 10.0.0.1: icmp_req=18 ttl=64 time=5.70 ms
64 bytes from 10.0.0.1: icmp_req=19 ttl=64 time=5.76 ms
64 bytes from 10.0.0.1: icmp_req=20 ttl=64 time=5.73 ms

--- 10.0.0.1 ping statistics ---
20 packets transmitted, 20 received, 0% packet loss, time 19025ms
rtt min/avg/max/mdev = 2.505/5.469/8.078/1.279 ms
```
Current Fix script:
```

#!/bin/bash
##################################################################
# This had been modifyed by OP!
# A Project of TNET Services, Inc
#
# Title:     WiFi_Check
# Author:    Kevin Reed (Dweeber)
#            dweeber.dweebs@gmail.com
# Project:   Raspberry Pi Stuff
#
# Copyright: Copyright (c) 2012 Kevin Reed <kreed@tnet.com>
#            https://github.com/dweeber/WiFi_Check
#
# Purpose:
#
# Script checks to see if WiFi has a network IP and if not
# restart WiFi
#
# Uses a lock file which prevents the script from running more
# than one at a time.  If lockfile is old, it removes it
#
# Instructions:
#
# o Install where you want to run it from like /usr/local/bin
# o chmod 0755 /usr/local/bin/WiFi_Check
# o Add to crontab
#
# Run Every 5 mins - Seems like ever min is over kill unless
# this is a very common problem.  If once a min change */5 to *
# once every 2 mins */5 to */2 ...
#
# */5 * * * * /usr/local/bin/WiFi_Check
#
##################################################################
# Settings
PATH="/usr/sbin:/sbin:$PATH"
echo "Current Path(s)"
echo $PATH
# Where and what you want to call the Lockfile
lockfile='/tmp/ram/WiFi_Check.pid'
# Which Interface do you want to check/fix
wlan='wlan0'
##################################################################
echo "Starting WiFi check for $wlan"
date
echo

# Check to see if there is a lock file
if [ -e $lockfile ]; then
    # A lockfile exists... Lets check to see if it is still valid
    pid=$(cat $lockfile)
    if kill -0 &>1 > /dev/null $pid; then
        # Still Valid... lets let it be...
        echo "Process still running, Lockfile valid"
        exit 1
    else
        # Old Lockfile, Remove it
        echo "Old lockfile, Removing Lockfile"
        rm $lockfile
    fi
fi
# If we get here, set a lock file using our current PID#
echo "Setting Lockfile"
echo $$ > $lockfile

# We can perform check
echo "Performing Network check for $wlan"
broken=0
if ifconfig $wlan | grep -q "inet addr:" ; then
    echo "Network is seemingly Okay"
    echo
    echo "Ping Test:"
    ping 10.0.0.1 -c 1
    if [ $? -eq 0 ];then
        echo "    Wifi Working"
    else
        echo "    Wifi Down"
        broken=1
    fi
    echo
else
    broken=1
fi
if [ $broken -eq 1 ];then
    echo "Network connection down! Attempting reconnection."
    ifdown $wlan
    sleep 5
    ifup --force $wlan
    ifconfig $wlan | grep "inet addr"
    sleep 7
fi

echo
echo "Current Setting:"
ifconfig $wlan | grep "inet addr:"
echo

# Check is complete, Remove Lock file and exit
echo "Process is complete, removing lockfile"
rm $lockfile

# Backup Log
logFile="/tmp/ram/wifiCheck"
if [ -f $logFile ];then
    if [ -f $logFile.log ];then
        if [ -f $logFile.log.old ];then
            if [ -f $logFile.log.older ];then
                cp $logFile.log.older $logFile.log.oldest
            fi
            cp $logFile.log.old $logFile.log.older
        fi
        cp $logFile.log $logFile.log.old
    fi
    cp $logFile $logFile.log
fi
exit 0

##################################################################
# End of Script
##################################################################
```
cron task:
```
*/10 * * * * /usr/local/sbin/wifiCheck > /tmp/ram/wifiCheck
```

---

