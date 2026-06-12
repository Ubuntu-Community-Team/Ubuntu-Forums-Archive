---
title: "Wlan0 on CLI only troubleshooting"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by ultima-thule on 2007-12-18
Having trouble either with wireless card or my command line syntax has an error. Hope my report is so complete that it will be help to others as reference. 

Referred to this forum's excellent sticky reference with the info that my card needs ndiswrapper.
My wlan0 is Trendnet TEW-423PI

So compiled ndiswrapper and did:
ls driver/
net8185.cat
net8185.inf
net8185.sys
sudo ndiswrapper -i driver/net8185.inf

Next I have a bash script with these lines :
BEGIN SCRIPT
sudo modprobe ndiswrapper
sudo /bin/ndiswrapper/utils/ndiswrapper -m
sudo killall -q dhclient
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 power all
iwlist wlan0 power
sudo iwconfig wlan0 ap 00:11:23:3e:d0:2f
iwlist wlan0 scan
sudo iwconfig wlan0 key open s:aaapassword [1]
sudo iwconfig wlan0 key open [1]
iwlist wlan0 key
sudo iwconfig wlan0 essid my_accesspoint_apple_airport_router
sudo iwconfig wlan0 commit
sleep 5
sudo dhclient wlan0
ifconfig wlan0 | grep "inet addr"
ping -c 3 [www.google.com](www.google.com)
sudo iwconfig wlan0

END OF SCRIPT

Here are outputs from lines in above script:

1)
iwlist wlan0 power
wlan0 Current mode: All packets received 
                             timeout: 0us

2)
iwlist wlan0 scan
wlan0   No scan results

3) 
iwlist wlan0 key
wlan0 0 keys available :

4)
iwconfig wlan0 commit
Error for wireless request "Commit changes" (8B00) :
        SET failed on device wlan0; Operation not supported.

5)
dhclient wlan0
Listening on LPF/wlan0/00:14:d1:34:cb:55
Sending on LPF/wlan0/00:14:d1:34:cb:55
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
.....
No DHCPOFFERS received.
No working leases in persistent database -sleeping.

6)
iwconfig wlan0
wlan0 802.11b/g ESSID:"my_accesspoint_apple_airport_router" 
           Mode: Managed Frequency=2.457 Ghz Access Point: 00:11:23:3e:d0:2f
           Bit rate: 11Mb/s
           Retry : on Fragment:off
           Encryption key: 676F-6163-7456-3744-0000-0000-00 Security mode:open
           Power management timeout:0us mode: All packets received
           Link quality: 0 Signal Level: 0 Noise level: 0
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid fraq: 0
           Tx excessive retries:0 Invalid misc:0 Missed beacon: 0

---

### Post by kevdog on 2007-12-18
Check out my guide to connecting from the command line -- its in my signature

---

### Post by ultima-thule on 2007-12-19
kevdog, Your wireless troubleshooting and ndiswrapper howto are good references. Following your 
steps in the ndiswrapper page I found that my r8185 driver was not functioning, with 
```

ndiswrapper -l

```
Reloaded drivers following your ndiswrapper steps, using drivers Trendnet CD, now the output is:
```

net8185 : driver installed
    device (10EC:8185) present (alternative driver: r8180)

```

Also attempted this:
```

sudo modprobe r8185
FATAL: Module r8185 not found.

```

Here is my new wireless script based on your scripting:
```

sudo ifconfig wlan0 down
sudo dhcleint -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 essid "my_airport"
sudo iwconfig wlan0 key s:my_password
sudo iwconfig wlan0 ap 00:12:24:5e:d0:2f
sudo iwlist scan
sudo dhclient wlan0
sudo iwconfig wlan0

```
After it runs, do not get a ping to my router or [www.google.com](www.google.com) :(
```

No DHCPOFFERS received.

```
The wireless access was attempted with, and without, my extra line:
```

sudo iwconfig wlan0 ap 00:12:24:5e:d0:2f

```
( ap is the mac address on my apple airport )
```

iwconfig wlan0

```
Reports the same output as my first post. The essid, mode, access point, encryption key, and others look positive to me ( positive meaning: parameters are populated with correct looking stuff).

The most negative output is from 
```

iwlist scan
wlan0 No scan results

```
( Should be some scan results, I live amongst a dozen access points )

That looks like something is dead. Any suggestions anyone?

---

### Post by ultima-thule on 2007-12-19
Original poster here, adding to last my post. I just  attempted with the more wide open:
```

iwconfig wlan0 ap any
iwconfig wlan0 essid any

```
Still 
```
iwlist scan
```
gets nothing.

and I feel silly for saying this last.....the data link light never comes on. 

Driver issue, still?

---

### Post by kevdog on 2007-12-19
You are having a driver issue.  Please post

lshw -C network

What driver do you want to use?

---

### Post by ultima-thule on 2007-12-19
Oh, this is a surprise, I swear I looked at this before last ndiswrapper update of driver and it wasn't
disabled....i think.
```

*-network: 0 Disabled
description: Wireless interface
product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
vendor: Realtek Semiconductor 
capabilities : bus_master cap_list ethernet physical address wireless
configuration: broadcast=yes driver=rt8180 latency=32 maxlatency=64 mingnt=32 module=r8180 
multicast=yes wireless=802.11b/g

```

TrendNet TEW-423PI Wireless card is the device.

---

### Post by kevdog on 2007-12-19
What driver do you want to use?? ndiswrapper.  If you do, you need to blacklist the rt8180 driver:

echo blacklist rt8180 | sudo tee -a /etc/modprobe.d/blacklist

Then modprobe ndiswrapper

---

### Post by ultima-thule on 2007-12-19
```

echo blacklist rt8180 | sudo tee -a /etc/modprobe.d/blacklist
modprobe ndiswrapper

```
made the lshw output look different:
```

*-network:0
description: Wireless interface
logical name: wlan0

```
still iwlist scan gets no results, and no DHCPOFFERS received.

---

### Post by ultima-thule on 2007-12-20
I copied the script this guy did:
[http://www.quietearth.us/articles/2007/01/19/TrendNet-TEW423PI-working-in-linux](http://www.quietearth.us/articles/2007/01/19/TrendNet-TEW423PI-working-in-linux)
```

#!/bin/sh
modprobe -r ndiswrapper 
apt-get --purge remove ndiswrapper-utils 
rm -r /etc/ndiswrapper/ 
rm -r /etc/modprobe.d/ndiswrapper
rm /lib/modules/$(uname-r)/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
apt-get install linux-headers-$(uname -r)
apt-get install dh-make fakeroot gcc-3.4 build-essential
tar -zxvf ndiswrapper-1.28.tar.gz
cd ndiswrapper-1.28
make uninstall
CC=gcc-3.4 make
fakeroot sudo make install
cd ..
rm -Rf ndiswrapper-1.28
ndiswrapper -i (your driver/bla.inf here)
modprobe ndiswrapper
ndiswrapper -m

```

The above is kind of confusing. At one step it removes ndiswrapper
```

rm -Rf ndiswrapper

```
which made all ndiswrapper commands fail. So reinstalled ndiswrapper executable in /bin/
( question, I've seen ndiswrapper in /etc/, but that makes command not reachable without full path name, where should it live?)

Most important failure is 
```

sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.22-14-server/ubuntu/misc/ndiswrapper/ndiswrapper.ko': no such file found

```
which makes me think unkind thoughts about this guy's tutorial/scripting. And I have to do: 

```

sudo apt-get -f remove linux-ubuntu-modules-2.6.22-14-server
sudo apt-get -f install linux-ubuntu-modules-2.6.22-14-server

```
to make
```

modprobe ndiswrapper

```
exit without failure.

My current state of wireless:

1)
```

lshw outputs:
*-network:0
description: Wireless interface
logical name: wlan0
( the main news is "disabled" does not appear )

```

2)
```

ndiswrapper -l
net8185 : driver installed
device (10EC:8185) present (alternative driver: r8180)

```

3)
```

iwlist scan
wlan0 No scan results

```
4)
```

No DHCPOFFERS received

```

---

### Post by marknjen on 2008-05-24
ultima-thule, did you ever get this to work correctly? If so, can you share your secret? I have the same wireless NIC as you (TrendNet TEW-423PI), and experience the exact problems you are experiencing. I am running Hardy Heron.

---

