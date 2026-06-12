---
title: "Directory /lib/firmware deleted"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by greenleaves on 2006-11-18
Hi,

I'm a new bee here. While I was struggling with bcm43xx-fwcutter in Edgy, I deleted the entire /lib/firmware directory, and got the following error message:

bcm43xx-fwcutter can cut the firmware out of wl_apsta.o

  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
/lib/firmware/bcm43xx_microcode2.fw: No such file or directory

Wonder how I can restore the entire directory from a repository source without reinstalling Edgy all over again?

Thank you.

---

### Post by coffeecat on 2006-11-18
I don't know whether this will work, but this is what I would try:

Boot up the live CD, mount the partition on which you have the hard drive installation, and then copy the whole of /lib/firmware from the live system to the HD partition. In theory, that will give you an identical /lib/firmware to a freshly installed one - but I might be wrong. :wink:

If you need any help mounting the partition, just post back.

---

### Post by greenleaves on 2006-11-18
Thanks for the hint. Will give it try just in case.

I did google and found a solution to get back the bcm43xx firmware. Here is the code:

sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

However my bcm43xx is still not working.

1. iwconfig
2. iwlist eth1 scan

Both show eth1 was configured. When "dhclient eth1", I got

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dmesg shows:

ADDRCONF(NETDEV_UP): eth1: link is not ready (broadcom 4306)

Any ideas?

**UPDATE:** Problem solved. It's to do on the router side that I need to enable 802.3 b/g compatible in order to get it to work. Strange though, the same bcm43xx card on my laptop works on both Fedora 6 and Windows without the b/g setting.

---

### Post by sirtang on 2007-12-11
> **greenleaves said:**
> Thanks for the hint. Will give it try just in case.

I did google and found a solution to get back the bcm43xx firmware. Here is the code:

sudo /usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

However my bcm43xx is still not working.

1. iwconfig
2. iwlist eth1 scan

Both show eth1 was configured. When "dhclient eth1", I got

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

dmesg shows:

ADDRCONF(NETDEV_UP): eth1: link is not ready (broadcom 4306)

Any ideas?

**UPDATE:** Problem solved. It's to do on the router side that I need to enable 802.3 b/g compatible in order to get it to work. Strange though, the same bcm43xx card on my laptop works on both Fedora 6 and Windows without the b/g setting.


How to enable  802.3 b/g compatible ?
I don't know how to configure the wireless card's IP address. 


1. If I execute command "iwconfig" :

eth1      IEEE 802.11b/g  ESSID:"default"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:13:46:36:95:45   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=80/100  Signal level=-50 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:5636  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

2. If I execute command " iwlist eth1 scanning" :

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:36:95:45
                    ESSID:"default"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-43 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 44ms ago

          Cell 02 - Address: 00:13:46:0C:CC:D5
                    ESSID:"kemao"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-77 dBm  Noise level=-71 dBm
                    Extra: Last beacon: 60ms ago

---

