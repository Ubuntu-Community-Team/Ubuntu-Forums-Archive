---
title: "Trouble connecting to 2WIRE base station"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by pax131 on 2008-03-27
Hello all,

I recently purchased a Mac Pro and decided to throw Linux on it. I'm an engineer so I really enjoy having free access to up-to-date compliers, debuggers and the Kile frontend forTeX. Apple's reliance on the 6.3.5 version of gdb has started to become a major thorn in my balls of late..

..but I digress.

I've tried Linux on Apple hardware before, but an inability to use my wireless card has prevented me from adopting it. Here's a rundown of the hardware involved:

```
Operating system: Kubuntu 7.10 Gutsy 32-bit

Wireless card: Broadcom Corporation BCM4328 802.11a/b/g/n (rev03)

Base Station: 2WIRE 2700HG-B Gateway
```

After a month of tinkering in my spare time, I finally used ndiswrapper (version 1.52, utils version 1.9) to recognize the wireless card by extracting the bcmwl15.ini file from the R151517.EXE file avaliable on Dell's website. It appears to be working as iwlist produces the following output:

```
iwlist wlan0 scan
wlan0     Scan completed :

               Cell 02 - Address: 00:18:3F:02:45:49
                              ESSID:"2WIRE969"
                              Protocol:IEEE 802.11g
                              Mode: Managed
                              Frequency:2.437 Ghz (channel 6)
                              Quality:23/100 Signal level:-81 dBm Noise level:-96 dBm
                              Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                              48 Mb/s; 54 Mb/s
                              Extra:bcn_int=100
                              Extra:atim=0

```
The results of the scan seem to jive with the way the base station is set up: the ESSID and AP match, the broadcast channel is the wright one, all possible bit rate options are listed. The base station is currently using WEP-open for authentication.

After browsing the forums, here are the steps I have tried to establish a connection:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "2WIRE969"
sudo iwconfig wlan0 key <10-digit key goes here>
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 6604
killed old client process, removed PID file
..blah... blah...

Listening on LPF/wlan0/00:1c:b3:ff:57:e0
Sending on   LPF/wlan0/00:1c:b3:ff:57:e0
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
.
.
.
retries
.
.
.
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.
```

The network is working just fine otherwise- I'm sitting in front of the Mac Pro typing this on my laptop. Signal strength is full. The Mac Pro also gets full signal strength when I reboot into OS X. Any assistance would be greatly appreciated- Linux is a great operating system but it's pretty worthless to me without a working internet connection!

---

### Post by pax131 on 2008-03-28
Hello from Ubuntu!

So I got the wireless working, The two changes I made were:

-Extracted a new bcmwl5.inf file from the broadcomxpinstaller.exe file on the Mac OS X system disc using unrar

-Disabled ipv6

I'm not sure which of those did the trick, but the wireless card is working now!

---

