---
title: "Slow Internet"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by ferox on 2005-11-27
Machine: Dell Inspiron 8200 Laptop
Wireless Adapter: Dlink G650+ RevB. (Texas Instruments)
Wireless Router: Dlink DI 724p+ (1.04 firmware, latest)
Config: Using OPEN, static ip configuration.
Other: wifigtk

Yup, I'm getting the slow internet problem and it is system wide. As I type this, synaptic is updating the repository list at some 7000bytes/sec. I have a 1mbit/sec line. I'm totally new to linux and I don't even know how to get a terminal going. I just use Ctrl+Alt+F1. Is this the same thing? What I do notice is that the connection will be move a sec, pause a few sec, then move again. 

**Steps tried:**
Disable IPv6 system wide
Disable acpi in grub, enable apm
Ping: certain sites get through, but most with some degree of packet loss regardless domain or IP. (25-100%@4 requests)
Ifconfig: shows Rx packets with 5 errors. Everything else looks normal.
DNS servers: Added them into the Network Connection properties.

Thx for your help.
ps: for stuff like ifconfig reports, what's the best way to cut n paste? I've no idea

---

### Post by mindwarp on 2005-11-28
Generally slow network performance is related to conditions on your network.

1. Is the machine dual boot? If so reboot and see if same issues to same servers occur, using all steps.
2. What does "traceroute server_address" say?
3. *Not advised but useful*: if the server you are trying to reach responds to "ping" do a "ping -f server_address".  That will help you figure out the packet loss. 
4. Run the ping -f test on your router.  How much packet loss, latency to your router?  


Hopefully these steps will help you figure out if it is a local network problem or an issue with your internet provider, or specific server you are connecting to.  Also many steps of: [http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643) apply to wireless.

---

### Post by nalmeth on 2005-11-28
If you're using gnome open up a terminal in applications-accessories. Or in KDE open Kmenu and you should find one in a couple places, either choose "run command" and type "konsole" or in system menu you should find it aswell. A good terminal application is "yakuake". In any terminal type:
sudo apt-get install yakuake
and enter password when prompted. Then run yakuake, and it will hide it for you behind your desktop. You can press f12 to summon it at anytime, and it can open multiple tabs, etc.
cntr-alt-f1/f2/f3/f4/f5 works too, but must be a burden to use and switch back..
Like previous reply mentioned, it might be poor network conditions, or if I were to guess at another idea, maybe you have the wrong driver for your wireless card that only partially works. Not likely, but thats I can think up for you man. I can't see any other software driven source for this problem.
Also, just noticed, you have static ip config. Not sure if you've tried yet, but DHCP is dependable in my opinion (or usually so... grrrumble)

Good Luck

---

### Post by ferox on 2005-11-28
*1. Is the machine dual boot? If so reboot and see if same issues to same servers occur, using all steps.*
Nope. Single boot. Just switched from XP. :smile: 

*2. What does "traceroute server_address" say?*
Only had traceroute6 installed which didn't respond to the command. Downloaded traceroute through synaptic (painfully slow, timed out once).

bernard@ferox:~$ traceroute server_address
[COLOR="blue"]traceroute to server_address.domain.com (216.34.94.177), 30 hops max, 38 byte packets
 1  Wireless (192.168.0.1)  29.316 ms  3.223 ms  2.910 ms
 2  219.93.218.177 (219.93.218.177)  178.339 ms  157.525 ms  120.943 ms
 3  219.93.216.109 (219.93.216.109)  65.024 ms  21.596 ms  21.850 ms
 4  219.93.155.33 (219.93.155.33)  22.479 ms 219.93.155.41 (219.93.155.41)  20.5 68 ms 219.93.155.33 (219.93.155.33)  25.650 ms
 5  brf-odsy01-srp1-0.tm.net.my (210.187.135.1)  28.858 ms  20.768 ms 203.106.24 0.201 (203.106.240.201)  22.136 ms
 6  219.93.151.98 (219.93.151.98)  31.151 ms 210.187.142.1 (210.187.142.1)  23.0 24 ms  21.849 ms
 7  vlan150-brf-sw04.tm.net.my (219.93.175.115)  76.579 ms 219.93.174.146 (219.9 3.174.146)  141.066 ms 219.93.174.147 (219.93.174.147)  23.543 ms
 8  219.93.151.226 (219.93.151.226)  23.458 ms 219.93.151.210 (219.93.151.210) 21.286 ms 219.93.151.226 (219.93.151.226)  23.359 ms
 9  * * if-3-0.core2.LXE-LosAngeles.teleglobe.net (216.6.125.1)  2922.706 ms
10  if-1-2.mcore4.LAA-LosAngeles.teleglobe.net (216.6.85.9)  3075.326 ms * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * bhr2-pos-0-0.Tukwilase2.savvis.net (208.172.81.222)  3266.710 ms
17  csr11-ve241.Tukwilase2.savvis.net (216.34.64.42)  3201.338 ms * *
18  * * *
19  * * *[/COLOR]

*3. *Not advised but useful*: if the server you are trying to reach responds to "ping" do a "ping -f server_address". That will help you figure out the packet loss.*
**bernard@ferox:~$ ping -c 4 [www.google.com](www.google.com)**
--- [www.l.google.com](www.l.google.com) ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3001ms
rtt min/avg/max/mdev = 239.799/240.332/240.866/0.724 ms
bernard@ferox:~$
[B]
bernard@ferox:~$ ping -f server_address[/B]
PING server_address.domain.com (216.34.94.177) 56(84) bytes of data.
ping: cannot flood; minimal interval, allowed for user, is 200ms

**bernard@ferox:~$ ping -i 200 -f server_address**
PING server_address.domain.com (216.34.94.177) 56(84) bytes of data.
It stops responding after this and I've to press ctrl+c to stop it:
--- server_address.domain.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
[I]
4. Run the ping -f test on your router. How much packet loss, latency to your router? [/I]
**bernard@ferox:~$ ping -i 200 -f 192.168.0.1**
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
Also stops responding. Help. Ctrl+c :
--- 192.168.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.677/2.677/2.677/0.000 ms
**bernard@ferox:~$ ping -c 4 192.168.0.1**
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1644 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=650 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=2.24 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=2.36 ms

--- 192.168.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 2.242/574.866/1644.295/671.764 ms, pipe 2

Also, thanks for the help with the terminal. I did use dhcp/wep128 and it connected fine but still internet was slow. So i'm just using static for the time being to eliminate any possible problems. Will try to change drivers.

---

### Post by ferox on 2005-11-28
Following this link and trying what they say
[http://www.ubuntuforums.org/showthread.php?t=87643](http://www.ubuntuforums.org/showthread.php?t=87643)

bernard@ferox:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:57:6E:7B
          inet addr:192.168.0.115  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4073 errors:88 dropped:0 overruns:0 frame:0
          TX packets:4202 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4152804 (3.9 MiB)  TX bytes:441719 (431.3 KiB)
          Interrupt:11

Tried all the steps. Nothing works. Will try changing the driver.

---

### Post by greenway on 2005-11-28
Looking at the time took traceroute to reach the first hop (2.910 ms) and your servers pong reply times, I would say the problem is at your WLAN/router. This also because the time to get to the other hops seems normal (I run a similar route from my network and your traceroute times are less then mine).

Do you have normal UTP ports on your WAP? If so, connect a PC directly to the router and check if this improves your internet speed.

I am no expert on WLAN issues; maybe someone else can help you on that. Goodluck anyway!

---

### Post by ferox on 2005-11-28
Problem solved! At least I think it is...

It was a driver related issue. Apparently, by default linux loads the acx driver for this adapter i have. So I had to manually remove it.

Go to /lib/modules/kernelversion/kernel/drivers/net/wireless and run:
sudo mv acx /root/ 
sudo depmod -a

Then i downloaded a usrobotics drivers from linuxant and used those instead with ndiswrapper. Now everything works like a charm.
Signal strength even went up from 50+ to 100%. (I'm next to the router)

Thx everyone for your help.

---

