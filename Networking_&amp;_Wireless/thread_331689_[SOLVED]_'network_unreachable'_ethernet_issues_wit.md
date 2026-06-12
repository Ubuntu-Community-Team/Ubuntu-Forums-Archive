---
title: "[SOLVED] 'network unreachable' ethernet issues with Linux"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by mmtowns on 2007-01-04
Hi again everyone.
I just installed Dapper on my computer (dual booting w/XP).  I am having some issues with getting my network card working.

Here's my setup:
Athlon XP 1700
GeForce2 400 MX
384MB RAM
LNE100TX NIC (I've also tried switching it out with a 3Com 3C905TX, but still same problem)

I boot into Dapper (very slow bootup, but that's a new thread for another day) and I cannot get on the internet.  In addition, when trying to ping my router's ip address,  192.168.0.1, I get "network unreachable."  

ifconfig tells me that my NIC seems to be installed correctly, but is not getting an IP address.  My XP box 'ipconfig' tells me that the DHCP on my router is working fine, IP of 192.168.0.104 currently as I type this message.  

I have gone so far as plugging in directly to my cable modem (instead of going through the router), but I have the same problem.

It's also interesting to note that I have this same problem when booting a PCLinux OS LiveCD, but not a "DreamLinux" LiveCD.  

Any assistance or suggestions you can provide would be appreciated.  I realize you all work for free, but Ubuntu's active and helpful forums are what encourage me to keep giving Ubuntu a try.

Thanks in advance!

---

### Post by kingmonkey on 2007-01-05
Its probably slow at booting up because its waiting for DHCP to give it an IP.

Do you have DHCP set up on your router? If not switch it on.

Try setting up dapper with a static ip to see if that works.

---

### Post by mmtowns on 2007-01-05
Thanks for the quick reply, kingmonkey.
I double checked my router settings.  It is setup for DHCP.  DHCP seems to be working, because it gives my XP box an IP, my MacBook an IP and my XP laptop an IP all in the 192.168.0.x range.  

I also just tried a static IP...assigned myself 192.168.0.161 with a Gateway of 192.168.0.1 and DNS servers of 208.67.222.222 & 208.67.220.220
I am still unable to ping 192.168.0.1, which is my router, ping times out.  

I really appreciate your prompt reply.  Are there any other suggestions?

---

### Post by koenn on 2007-01-05
show us the output of
```
 ping 127.0.0.1
```  (a few lines is enough) and
```
ifconfig 
```

---

### Post by mmtowns on 2007-01-07
I wasn't able to save the output from the console (couldn't mount a USB drive or a hard drive for some reason...Ubuntu doesn't like m!), so I'm attempting to retype everything that I printed from the screenshot

matt@ubuntu: ~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 byes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.050 ms
64 byes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.041 ms
64 byes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.040 ms
64 byes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.043 ms
64 byes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.040 ms
64 byes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.039 ms

--- 127.0.0.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4997 ms
rtt min/avg/max/mdev = 0.039/0.042/0.050/0.005 ms
matt@ubuntu: ~$ ifconfig
eth1      Link encap:Ethernet    HWaddr  00:60:08:31:A8:10
            inet6 addr: fe80:260:8ff:fe31:a810/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:31 errors:0 dropped:0 overruns:0 frame:0
            TX packets:23 errors:1 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen: 1000
            RX bytes:18622 (18.1 KiB)    TX bytes: 6282 (6.1 KiB)
            Interrupt:11   Base addresss: 0xe400

lo         Link encap: Local Loopback
            inet addr:127.0.0.1   Mask:255.0.0.0
            inet6 addr:  ::1/128 Scope:Host
            UP LOOPBACK RUNNING   MTU:16436  Metric:1
           RX packets:17 errors:0 dropped:0 overruns:0 frame:0
           TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
           collissions: 0 txqueuelen:0
           RX bytes:1280 (1.2 KiB)    TX byes:1280 (1.2 KiB)

matt@ubuntu:~$
matt@ubuntu:~$

I hope this can help solve the network/ethernet issues described to start this thread.

Your help is greatly appreciated.

---

### Post by koenn on 2007-01-08
the succesful  ping to 127.0.0.1 tells us you have a working tcp/ip stack on your computer, i.e. it has the software it needs to be capable of connecting to a network. so far, so good;

the output of ifconfig shows you have no IP address, and you're going to need one. 
is this with dhcp or did you (try to) set an ip address manually ? 

I suggest we try a static IP address first. 
-be sure your router's IP address is really 192.168.0.1
-set a matching ip adress + network mask (255.255.255.0 should do), and set the router as your gateway. 
when done, check that /etc/network/interfaces looks something like this
#
```

auto eth0
iface eth0 inet static
        address 192.168.0.250
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

```

re-activate the NIC with
```

ifdown
ifup

```

for good measure, check that your system recognizes the networkcard, 
```
lspci |grep Ethernet
```
in addition, you could check for any reference to the card and its driver being loaded with dmesg


To make sure we're good so far, ping your own IP address 
```
ping 192.168.0.250
```
if this ping is succesfull, your computer is OK and the problem is further along the line.

---

### Post by Bliss on 2007-01-21
Same problem here in Edgy Eft. Network card is a PCI Realtek 8139, correctly detected and modules loaded. Same "network unreachable" problem with either static IP or DHCP. Windows XP works fine, Fedora Core as well. What's wrong with Ubuntu? :(

---

### Post by Hanzerik on 2007-01-21
Hhmm, I have both of those cards installed in one of my [systems](http://hanzerik.no-ip.info/sysinfo/). And both work fine out of the box. 

Do you/have you had any issues with your router. Ports going bad, only working at 10BaseT? I once had a LinkSys router that had two bad ports that would not work at 100BaseT, only 10BaseT, so I had to manually set my cards to run at 10BaseT-FD instead of 100.

---

### Post by rishi000 on 2007-01-25
The same thing just happened to me in Edgy. When I installed the thing and since then, the box was working just fine. Then all of a sudden, it can't communicate with my router. I'm trying to work on it now from my Dapper laptop, which can connect to the router and internet just fine over the wifi network. I feel like this has something to do with a recent update. Does anyone know if there are any known issues with dhclient or something?

---

### Post by mmtowns on 2007-01-27
Network w/Ubuntu still does not work.  I have narrowed it down to something with my Ubuntu install.  The router is not the problem because it works fine in XP and with a few other Linux distros.  I've tried static IP and it still does not work...

I am still experiencing USB mouse issues, too.  [http://www.ubuntuforums.org/showthread.php?t=326288](http://www.ubuntuforums.org/showthread.php?t=326288)

My 'fix' has been to get a USB to PS/2 converter so that I can continue to use my Microsoft Optical mouse with Linux.  

...will still keep plugging away.  So far, DreamLinux 2.2 Multimedia Edition likes my machine the best - working network, (mostly) working sound and no problems with the USB mouse.  Now if only their community could match that of the mighty Ubuntu...!

---

### Post by mmtowns on 2007-10-14
Network, sound and mouse are all working.  

See thread [http://ubuntuforums.org/showthread.php?t=326288](http://ubuntuforums.org/showthread.php?t=326288) for the fix.  

Disabling ACPI at boot did the trick...

---

