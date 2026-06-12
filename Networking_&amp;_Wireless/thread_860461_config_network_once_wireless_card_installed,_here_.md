---
title: "config network once wireless card installed, here is the output"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by alspal on 2008-07-15
I have installed dling g510 wireless card on ubuntu 8.04 i386, now have difficulty connecting to network throug router.

here is the output:

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:1B:11:8D:72:C4
                    ESSID:"DLINK"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:1D:6A:20:42:F8
                    ESSID:"Goosen-WLAN"
                    Mode:Managed
                    Channel:11
                    Encryption key:on

sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 rev B 802.11g
       vendor: RaLink
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: ra0
       version: 00
       serial: 00:19:5b:d2:dd:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61 ip=192.168.0.92 latency=64 link=yes module=rt61 multicast=yes wireless=RT61 Wireless
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:62:58:61
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s


sudo cat /etc/network/interfaces
auto ra0
iface ra0 inet static
address 192.168.0.92
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency:2.412 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by alspal on 2008-07-15
please help, I have been at it for weeks. I would like to use Linux, however I need help!!!

---

### Post by chili555 on 2008-07-15
Your scan results include this:> Encryption key: onYou need to amend your *interfaces* file as follows:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.0.92
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
wireless-essid DLINK
wireless-key <your 10 or 26-character_key>
```Afterwards, please do:```
sudo ifdown ra0 && sudo ifup ra0
```Are you now connected?

---

### Post by alspal on 2008-07-15
thank you for the reply, where and how do i edit my interface settings?

---

### Post by jimfromsa on 2008-07-15
cd to /etc/networks```
sudo gedit interfaces
```

This should get you to the interface screen.

---

### Post by alspal on 2008-07-15
sudo gedit interfaces 

does not work, no do anything

---

### Post by chili555 on 2008-07-15
sudo gedit /etc/network/interfaces

After you type in the changes, proofread, save and close.

---

### Post by alspal on 2008-07-15
when trying to save the edited file it says i do not have the necessary permition. I did use sudo ...

---

### Post by alspal on 2008-07-15
finally edited the interface settings. and then run command sudo ifdown ra0 && sudo ifup ra0

got this reply
error for wireless request "set encode" (8B2A)
set failed on device ra0 ; network is down
error for wireless request "set encode" (8B1A)
set failed on device ra0 ; network is down

---

### Post by chili555 on 2008-07-15
Let's try everthing we can think of to try.

Try:```
gksudo gedit /etc/network/interfaces
```Place all in one command and press enter. Enter your password when prompted.

If that doesn't work, for you, then do:```
sudo su
```Enter your password. Now, do:```
gedit /etc/network/interfaces
```Whichever one works, make your changes, proofread, save and close. Then do:```
sudo ifdown ra0 && sudo ifup ra0
```Are you connected?

---

### Post by alspal on 2008-07-16
> **alspal said:**
> finally edited the interface settings. and then run command sudo ifdown ra0 && sudo ifup ra0

got this reply
error for wireless request "set encode" (8B2A)
set failed on device ra0 ; network is down
error for wireless request "set encode" (8B1A)
set failed on device ra0 ; network is down

I have run the commands you requested and got these output results. THe wireless network i am trying to connect to is Goosen-WLAN should, the essid therefore not be set to Gooosen-WLAN instead of DLINK?

---

### Post by chili555 on 2008-07-16
> THe wireless network i am trying to connect to is Goosen-WLAN should, the essid therefore not be set to Gooosen-WLAN instead of DLINK?Your scan results, see post #1, showed two scan results. I'm sorry, I assumed the first one listed was yours. Please change to Gooosen-WLAN in your *interfaces* file.

It doesn't like your WEP key. You do have a 10 or 26-character key, right? The lines in interfaces should look something like this, assuming you have a 10-character key:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.0.92
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
wireless-essid Goosen-WLAN
wireless-key 0123abc789d
```Is that what your file looks like with your details substituted, of course?

---

### Post by alspal on 2008-07-16
Yes that is what the interfaces file looks like now. And when I run sudo ifup ra0...

i get the following
error for wireless request "set encode" (8B2A)
set failed on device ra0 ; network is down
error for wireless request "set encode" (8B1A)
set failed on device ra0 ; network is down

what to do?

---

### Post by alspal on 2008-07-16
those errors dissapear when I use iface ra0 inet ipv4ll instead of static address. However I am still not connected?!

---

### Post by chili555 on 2008-07-16
Let's try a different approach. Please amend *intefaces* to:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet static
address 192.168.0.92
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
up iwconfig ra0 essid Goosen-WLAN
up iwconfig ra0 key 0123abc789d
```Then do:```
sudo ifdown ra0 && sudo ifup ra0
```Did you connect?

---

### Post by alspal on 2008-07-16
no connection, and no messages

---

### Post by alspal on 2008-07-16
output says, 

ifdown: interface ra0 not configured

---

### Post by alspal on 2008-07-16
Hopeless?

---

### Post by alspal on 2008-07-17
output says, 

ifdown: interface ra0 not configured

---

### Post by alspal on 2008-07-17
Need help, please help.

---

### Post by chili555 on 2008-07-17
I wonder if your static IP numbers are all correct. Please try this:```
auto lo
iface lo inet loopback

auto ra0
iface ra0 inet dhcp
up iwconfig ra0 essid Goosen-WLAN
up iwconfig ra0 key 0123abc789d
```Then restart networking:```
sudo /etc/init.d/networking restart
```If the DHCP request times out ("...sleeping..."), then please post:```
dmesg | grep ra0
```Let's see if we can see where we are failing.

> ifdown: interface ra0 not configured That's normal. In human language, that means, roughly, 'OK, you asked me to take ra0 down; it's down and no longer configured.'

---

### Post by alspal on 2008-07-17
no dhcpoffers recieved

alspal@alspal-desktop:/etc/network$ dmesg | grep ra0
[   68.839978] ra0: no IPv6 routers present
[  534.071327] ra0: no IPv6 routers present
[  596.615489] ra0: no IPv6 routers present
[ 1174.684983] ra0: no IPv6 routers present
[ 1288.185736] ra0: no IPv6 routers present
[ 2284.698213] ra0: no IPv6 routers present
[ 2321.455720] ra0: no IPv6 routers present
[ 2378.056412] ra0: no IPv6 routers present
[ 2461.704090] ra0: no IPv6 routers present
[18681.578411] ra0: no IPv6 routers present
[20755.554698] ra0: no IPv6 routers present
[20781.396227] ra0: no IPv6 routers present
[20939.143716] ra0: no IPv6 routers present
[27983.096849] ra0: no IPv6 routers present
[28007.699987] ra0: no IPv6 routers present
[28043.532455] ra0: no IPv6 routers present
[28330.433193] ra0: no IPv6 routers present
[31081.931849] ra0: no IPv6 routers present
[31240.892778] ra0: no IPv6 routers present
[106556.064815] ra0: no IPv6 routers present

---

### Post by alspal on 2008-07-17
hello?

---

### Post by alspal on 2008-07-17
hi! wasup?

---

### Post by alspal on 2008-07-17
no help here?

---

### Post by chili555 on 2008-07-17
I was reading this: [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980)  and especially this part:> (c) "No DHCPOFFERS Received"

A lot of people have posted in this thread complaining about the error "No DHCPOFFERS Received" error when they try "sudo dhclient ra0". I myself have encountered this error when trying to connect to one of the APs in the building where I work. However, I couldn't find a solution and thus could not reply to their posts. Until I read reharpernc's post which suggested using "iwpriv" instead of "iwconfig". [For more information on "iwpriv", type "man iwpriv" in your terminal.]

So for people who have encountered this problem, try:

Code:

sudo iwpriv ra0 set NetworkType=Infra
sudo iwpriv ra0 set AuthMode=SHARED
sudo iwpriv ra0 set EncrypType=WEP
sudo iwpriv ra0 set DefaultKeyID=1
sudo iwpriv ra0 set Key1=<my wep key>
sudo iwpriv ra0 set SSID=<my essid>

then try to connect to your AP with

Code:

sudo dhclient ra0I believe, in your case, AuthMode is more likely to be OPEN.

I realize this is a bit old, but let's try it.

---

### Post by alspal on 2008-07-19
still no dhcp offers recieved. Any other suggestions?

---

### Post by alspal on 2008-07-21
should i perhaps provide some sort of output again to see if anything has changed?

---

### Post by alspal on 2008-07-24
please help, any ideas?

---

### Post by alspal on 2008-07-25
damn, this forum sucks? is there a number that i can phone to get help?

---

