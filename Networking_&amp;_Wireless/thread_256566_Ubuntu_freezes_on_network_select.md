---
title: "Ubuntu freezes on network select?"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by sas01 on 2006-09-13
Using ndiswrapper I have gotten Ubuntu to recognize my wireless card. I go into wireless configuration, select wlan0 and look at the settings. I set everything as it should be:

ESSID: WLAN
No WEP
No WPA
I.P and subnet mask assigned by DCHP.

I click ok and then Ubuntu freezes! Each and every time, it freezes!

Why might this be happening and how can I resolve it?

Regards, sas01

---

### Post by DarkN00b on 2006-09-13
Ubuntu takes a while switch connections, it doesn't happen right away.  I'd say i the system seems to hand for more than 3 minutes then start worrying.

---

### Post by sas01 on 2006-09-13
I had already thought of that, I left the machine for 15 minutes and still nothing. The mouse was frozen and I couldn't turn numlock or capslock on or off.

To me that indicates that the pc isn't going to respond.

Is there a way to stop this? I really need my internet access back up!

---

### Post by JPSkips on 2008-03-04
Hello,

I have the same problem. My Wlan card was already recognised, but when I go into settings, and click OK, it freezes.

Anyone got any suggestions?

---

### Post by unutbu on 2008-03-04
Look at /etc/network/interfaces.
It should contain something like this:

> 
iface wlan0 inet dhcp
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key <key>
wireless-essid <essid>

auto wlan0


Now try

```

sudo /etc/init.d/networking restart

```

If this does not work, post the output from the command above.

Also, I highly recommend reading
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by JPSkips on 2008-03-04
hello.

Thanks for the quick reply.

I just get 

iface wlan0 inet dhcp

no other data. when i try

sudo /etc/init.d/networking restart

it freezes.

I have the realtek 8185 chipset. When I follow the instructions for this on the link you sent, when i get to the command

sudo ifconfig wlan0 down

system freezes as above.

Any other hints?

Thanks again

JP

---

### Post by unutbu on 2008-03-04
Please post the results:
```

ndiswrapper -l
ifconfig
iwconfig
iwlist wlan0 scanning

```

---

### Post by JPSkips on 2008-03-04
ndiswrapper -1
bash: ndiswrapper: command not found
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:EC:2E:C7:AA
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:169 Base address:0xa800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2640 (2.5 KiB)  TX bytes:2640 (2.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:12:0E:47:40:81
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:55 dropped:41 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:608 (608.0 b)  TX bytes:8820 (8.6 KiB)
          Interrupt:185 Memory:f8a40000-f8a40100

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.427 GHz
          Access Point: Not-Associated   Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

 iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:14:7F:5B:E2:88
                    ESSID:"BTHomeHub-FC46"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:7
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 3ms ago
          Cell 02 - Address: 00:0F:B5:36:62:99
                    ESSID:"DunX"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:0  Signal level:0  Noise level:158
                    Extra: Last beacon: 1425ms ago

Hope this helps!

JP

---

### Post by unutbu on 2008-03-04
JPSkips, did you read the part of [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
entitled " Users of RTL 8180, RTL8185, RTL 8187 using the built in native r8187 / r818x drivers"?

---

### Post by JPSkips on 2008-03-05
After 
sudo modprobe r818x 
sudo modprobe r8187 
and
sudo ifconfig wlan0 down
system freezes

---

### Post by unutbu on 2008-03-05
Could you post the output to the following:
```

sudo lshw -C network
cat /etc/network/interfaces
route

```

---

### Post by JPSkips on 2008-03-06
jonathan@jonathan-desktop:~$  sudo lshw -c network
Hardware Lister (lshw) - B.02.06
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.06)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )

jonathan@jonathan-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

jonathan@jonathan-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
jonathan@jonathan-desktop:~$

---

### Post by unutbu on 2008-03-06
Please run lshw command again, except make sure the '-C' is a capital C.
```

sudo lshw -C network

```

---

### Post by unutbu on 2008-03-06
Also, your /etc/network/interfaces has too many references to devices that don't exist.
Your ifconfig output showed you have eth0 and wlan0 (and lo) only. 

So, as root, edit your /etc/network/interfaces to look like this:

```

auto lo
iface lo inet loopback

iface wlan0 inet dhcp
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid <PUT YOUR ESSID HERE>
auto wlan0

iface eth0 inet static

```

---

### Post by unutbu on 2008-03-06
Perhaps one of these links will help you.

Realtek win98 driver - [http://www.majorgeeks.com/Realtek_RT...0XP_d5165.html](http://www.majorgeeks.com/Realtek_RT...0XP_d5165.html) - For use with ndiswrapper if native r818x, r8187 driver is buggy
Realtek win98 driver installation - [http://ubuntuforums.org/showthread.p...highlight=8187](http://ubuntuforums.org/showthread.p...highlight=8187) - Author Panurge
Realtek - Installation with Native Driver - [http://ubuntuforums.org/showthread.php?t=567505](http://ubuntuforums.org/showthread.php?t=567505)

The above links were referenced here:
Useful resources for beginners setting up your wireless connection:
[http://ubuntuforums.org/showthread.php?t=596797](http://ubuntuforums.org/showthread.php?t=596797)

---

