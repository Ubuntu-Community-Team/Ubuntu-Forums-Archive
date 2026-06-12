---
title: "Connects to network, not internet"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by WUSB11 MY A**E on 2007-09-20
Right, before I begin, I am an absolute beginner at linux, after first installing it a week ago, yet I am probably intermediate to advanced windows user (beginner at networking though)...

Anyway, the wireless adapter I am using is WUSB11v4. I know I have it definitely working with ndiswrapper for the driver as I can connect to the ad-hoc network in my home. I can look at files on the computers in the network etc. Anyway, one computer in this network also shares its internet connection with the rest of the computers in the network. I can connect to the network itself but I cannot work out how to use the shared internet.

I am using feisty...

Heres ifconfig, iwconfig and route

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Default"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: EE:33:67:EC:2E:B9   
          Bit Rate=11 Mb/s   
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:B0:45:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1830 (1.7 KiB)  TX bytes:1830 (1.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:F0:32:38  
          inet addr:192.168.0.144  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fef0:3238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25523 (24.9 KiB)  TX bytes:49647 (48.4 KiB)



route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
```

---

### Post by helgman on 2007-09-20
Sounds like the problem is your default gateway settings. It should be set to the IP-address of the computer sharing the internet connection.

At the command line (in terminal) try **route** and look for the line with the 'Destination' saying *default* or 0.0.0.0 and then note the 'Gateway' of that line. If the Gateway differs from the one sharing the connection you have to set it (the IP-address of the one sharing the connection) as your default gateway.

Try

```
sudo route add default gw <gateway IP-address>
```

Regards,
Helgman

---

### Post by WUSB11 MY A**E on 2007-09-20
Thanks :D I'll try it now...

---

### Post by WUSB11 MY A**E on 2007-09-20
(Sorry if double posting isn't allowed in these forums, I've seen others doing it so I am guessing it's ok to do it if trying to get attention that the thread has changed, but not just to bump up the thread)

Anyway, I've posted the results from ifconfig, iwconfig and route. I tryed "sudo route add default gw 192.168.0.0" but it doesn't appear to be working. I probably entered the wrong address in though. Anyway, the results from route appeared to not be completely as you described, you can see them in the top post...

Thanks

---

### Post by helgman on 2007-09-20
> **WUSB11 MY A**E said:**
> I tryed "sudo route add default gw 192.168.0.0" but it doesn't appear to be working.

My guess is that 192.168.0.0 is the network address, so the hosts in your network would have addresses in the span of 192.168.0.1-254. You'll need the IP-address of the computer sharing the network connection. The IP-address of that machine (the address it uses on the inside, not the Internet side) should be the gateway address (let me know if you need help finding the IP-address, but don't forget to tell what OS it runs). For example, let's say the IP-address of the computer sharing the internet connection is 192.168.0.1 the command would look like:

```
sudo route add default gw 192.168.0.1
```

Output of command 'route -n' on my machine produces (I add the option -n to get the addresses, not the hostnames):

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

So in my case 192.168.1.1 is the default gateway.

Does this help?

Helgman

---

### Post by WUSB11 MY A**E on 2007-09-20
right I'll just try that (have to reboot yet again :S)

Thanks for the help too!

---

### Post by WUSB11 MY A**E on 2007-09-20
Worked perfectly, thanks very much!!!

Right, now every time I start up my computer I need to run the following in the terminal:

sudo iwconfig wlan0 mode ad-hoc
sudo ifdown wlan0
sudo ifup wlan0
sudo route add default gw 192.168.0.1

I am just wondering if there is a way for this to happen automatically at startup, rather than me type it every time. Thanks.

---

### Post by helgman on 2007-09-20
Glad I could help!

As for the other problem, you are not alone. I don't have a solution for you but there are other threads on the subject:

[http://ubuntuforums.org/showthread.php?t=555731](http://ubuntuforums.org/showthread.php?t=555731) (new)
[http://ubuntuforums.org/showthread.php?t=96318](http://ubuntuforums.org/showthread.php?t=96318) (old)

Unfortunately there are no replays to them. The problem as I see is it that the commands must be run as root (sudo) otherwise you could just make a script and have it run at logon. The big thing is trying to find out WHY this should be done to get things to work ...

Regards,
Helgman

---

### Post by 0darn on 2007-09-20
hi , im running xubuntu 7.04 , and did the "sudo network-admin" with my wireless pcmcia ,
( other distros has been more tweak to get it work with ndiswrapper and configs & more ),this distro it just worked :) ..
The config file where most are : /etc/network/ interfaces
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-essid ARGH
wireless-key abcdefabcdef01234567891234
auto wlan0

and enabled wlan devices: /etc/wlan/ wlan.conf      ( cleaned it some )
> WLAN_DEVICES="wlan0"
ChannelList="01:02:03:04:05:06:07:08:09:0a:0b:00:00:00"
ChannelMinTime=200
ChannelMaxTime=250
WLAN_SCAN=n
TMPDIR=/tmp
SSID_wlan0=""
ENABLE_wlan0=y
#SSID_wlan1=""
#ENABLE_wlan1=n
#SSID_wlan2=""
#ENABLE_wlan2=n

Dns goes: /etc/ resolve.conf
> search Namex
nameserver 192.168.2.1

the 'auto wlan0' in 'interfaces' is read by Udev and its hotscripts? in: /etc/udev/rules.d/85-ifupdown.rules
> # This file causes network devices to be brought up or down as a result
# of hardware being added or removed, including that which isn't ordinarily
# removable.
# See udev(7) for syntax.
SUBSYSTEM=="net", DRIVERS=="?*", GOTO="net_start"
GOTO="net_end"
LABEL="net_start"
# Bring devices up and down only if they're marked auto.
# Use start-stop-daemon so we don't wait on dhcp
ACTION=="add",		RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifup -- --allow auto $env{INTERFACE}"
ACTION=="remove",	RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown -- --allow auto $env{INTERFACE}"
LABEL="net_end"

Gateway/route file i cant find right now

/maybe some help - 0darn

---

