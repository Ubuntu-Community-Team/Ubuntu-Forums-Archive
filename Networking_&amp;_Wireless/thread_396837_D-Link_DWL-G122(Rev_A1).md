---
title: "D-Link DWL-G122(Rev A1)"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Kione on 2007-03-29
Okay, I installed Edgy yesterday, and after about 2 hours of trying to figure out that all I had to do to install ndiswrapper was plop in the CD, I used ndiswrapper and the drivers that came on the d-link CD to install it. In Networking it now realizes the wireless, and when I connect, the lights on the D-Link go on, the Link one anyway, the Act stays blank. And I cannot connect nor ping to anything, including not being able to ping my wireless router(Belkin F5D7230-4 v5000). I'd really like to start using linux, but with no internet, I'm really no having good luck. I configured it how it should be, I'm almost positive. The ESSID(The router calls it the SSID, but I have ESSID enabled), DHCP, and the password. I'm on my Windows Media Center partition right now, although I'd rather be on my Windows XP pro Partition, but ever since I installed Linux, whenever I attempt to get onto the Windows XP partition, it says that hal.dll is missing or corrupt, I even attempted to replace it from this partition(By putting it in the other partition), a fresh copy from dll-files.com

Any help on either issue would be greatly appreciated, thanks in advance.

[Edit - I'm on a Dell Dimension E310]

---

### Post by Floppyjoe on 2007-03-29
Have you properly setup your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```
You need to add something like this to your wireless interface:
> wireless-essid WarGames
wireless-channel 7
wireless-mode managed
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

I have WPA set-up here in mine

---

### Post by Kione on 2007-03-29
So, I type sudo gedit /etc/network/interfaces

Then what do I do?  Will it ask me for info, and I fill it in?

---

### Post by Floppyjoe on 2007-03-29
> **Kione said:**
> So, I type sudo gedit /etc/network/interfaces

Then what do I do?  Will it ask me for info, and I fill it in?

It will list your network interfaces and then you need to add the information about your access point like the wireless-essid, wireless-channel, wireless-mode

---

### Post by Kione on 2007-03-29
Okay, I'll try that.  Thanks, gotta change to my linux partition(and hopefully not back).

---

### Post by Kione on 2007-03-29
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


iface eth2 inet dhcp
wireless-essid ASDF
wireless-key [censored by me]
address 192.168.2.1
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth2
```

Now the lights don't even go on in the wireless card.  What am I doing wrong?

---

### Post by Floppyjoe on 2007-03-29
> **Kione said:**
> ```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


iface eth2 inet dhcp
wireless-essid ASDF
wireless-key [censored by me]
address 192.168.2.1
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth2
```

Now the lights don't even go on in the wireless card.  What am I doing wrong?

You probably have your information under the wrong interface. also if you are using a static IP then you would have to make the interface lines say something like this:
```
auto wlan0
iface wlan0 inet static
wireless-essid ASDF
wireless-key [censored by me]
address 192.168.2.1
netmask 255.255.255.0

```

---

### Post by Kione on 2007-03-30
My router says ```
DHCP Server	Enabled
```

I've got to go to bed, I've got school in the morning, I'll check back after school, thanks for helping.

---

### Post by Kione on 2007-03-30
Anyone know the problem?

---

### Post by Kione on 2007-03-30
I got some more info, I did ifconfig, and iwconfig.  I did it twice, first time with the wireless disabled, and the next with it enabled.

```
kione@kioneowns:~$ sudo ifconfig
Password:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

kione@kioneowns:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:off/any  
          Mode:Auto  Channel=0  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

kione@kioneowns:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:0F:3D:F9:82:C1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

kione@kioneowns:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I also have a screenshot of my desktop and the wireless card:

[http://img524.imageshack.us/img524/1893/screenshotjy4.png](http://img524.imageshack.us/img524/1893/screenshotjy4.png)

---

### Post by Floppyjoe on 2007-03-31
> kione@kioneowns:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I was partially wrong in one of my earlier posts. eth2 is the wireless interface but would be eth1 if your /etc/network/interfaces file was set up properly. Are you trying to get a static IP address from your router? Because that is what it looks like in your /etc/network/interfaces file. Your file shows this:
> auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


iface eth2 inet dhcp
wireless-essid ASDF
wireless-key [censored by me]
address 192.168.2.1
netmask 255.255.255.0

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






auto eth2
It should show this:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ASDF
wireless-channel 6
wireless-mode managed
wireless-key [censored by me]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```
Where you would substitute your routers channel number for 6. This is if you are not using Network-Manager and are trying to get a DHCP connection from your router.

---

### Post by Kione on 2007-03-31
I'll try that right now, and report back with any news!  Thanks!

---

### Post by Kione on 2007-03-31
My interfaces file now looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid ASDF
wireless-channel 6
wireless-mode managed
wireless-key [censored]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth2 inet dhcp
wireless-essid ASDF
wireless-key [censored]

auto eth2

```

When I did what you said, and went to Networking, it showed my wireless as disabled, so I re-enabled it, neither worked.

---

### Post by Floppyjoe on 2007-03-31
What is the output of iwconfig and ifconfig now as well as the output of:
```
sudo iwlist eth1 scan
```

---

### Post by Kione on 2007-03-31
Results:

```
sudo iwlist eth1 scan
kione@kioneowns:~$ sudo iwlist eth1 scan
Password:
eth1      Interface doesn't support scanning.
kione@kioneowns:~$ sudo iwlist eth2 scan
eth2      No scan results

sudo iwconfig
kione@kioneowns:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=0  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

sudo ifconfig
kione@kioneowns:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:30:E2:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2468 (2.4 KiB)  TX bytes:2468 (2.4 KiB)
```

Anything else?

---

### Post by Floppyjoe on 2007-03-31
Post:
```
lsusb
```

---

### Post by Kione on 2007-03-31
```
kione@kioneowns:~$ sudo lsusb
Password:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 2001:3703 D-Link Corp. [hex] DWL-122 802.11b
Bus 001 Device 006: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0471:0815 Philips 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  

```

---

### Post by Floppyjoe on 2007-03-31
Post:
```
ndiswrapper -l
```

---

### Post by Kione on 2007-03-31
```
kione@kioneowns:~$ sudo ndiswrapper -l
Password:
Installed drivers:
prisma02                driver installed, hardware present 

```

---

### Post by Floppyjoe on 2007-03-31
Blacklist conflicting drivers:
```
sudo gedit /etc/modprobe.d/blacklist
```
Add the following three lines to this file then save and exit this file.
```
blacklist islsm_usb
blacklist islsm_device
blacklist islsm

```

---

### Post by Kione on 2007-03-31
Done, but still no net, do I need to restart linux?

---

### Post by Floppyjoe on 2007-03-31
> **Kione said:**
> Done, but still no net, do I need to restart linux?

Restart would be good.
interface is likely eth2 it may depend on which usb port it is hooked into.
try after reboot:
```
sudo iwlist eth2 scan
```

---

### Post by Kione on 2007-03-31
```
kione@kioneowns:~$ sudo iwlist eth2 scan
eth2      No scan results
```

---

