---
title: "wired network not working"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-07-07
I recently upgraded from 9.10 to 10.04. During this time I was temporarily using a wireless adapter on my desktop (and no ethernet). For whatever reason, Ubuntu is dropping the connection constantly. I used to see a lot of wpa_supplicant errors in the logs back in 9.10. Those errors went away in 10.04, but I was still having the same problems.

Anyway, I switched back to ethernet. Now I cannot get the system to detect ethernet. I am writing this post by live cd, so I know that its not a hardware issue. If I don't have the wireless adapter plugged in, the network icon in the panel disappears. The wired connection either says "disabled" or "not managed" depending on what things I have messed with.

My usual 
```
    sudo vi /etc/network/interfaces

    auto eth0
    iface eth0 inet dhcp

    sudo /etc/init.d/networking restart
```
is not working. Any suggestions?

---

### Post by mikewhatever on 2010-07-07
Post the output of **sudo lshw -C network**. That should at least show if the driver is loaded.

---

### Post by dineshs on 2010-07-07
If you want NM to manage your network devices
/etc/network/interfaces should contain only this(Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
```
auto lo
iface lo inet loopback

```
You can also try this
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
[COLOR="Blue"]Should restart the machine after doing this[/COLOR]

---

### Post by mikewhatever on 2010-07-07
In my case, /etc/NetworkManager/nm-system-settings.conf has 'managed=false', and no issues with the NM managing all connections.

---

### Post by dineshs on 2010-07-07
I understand that either /etc/network/interfaces should contain [I]auto lo
iface lo inet loopback[/I]
or */etc/NetworkManager/nm-system-settings.conf*  must be set to *managed=true*
I mean you will be having only those to lines in /etc/network/interfaces.Am I right?

---

### Post by bnhrobotics on 2010-07-07
> **dineshs said:**
> If you want NM to manage your network devices
/etc/network/interfaces should contain only this(Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager))
```
auto lo
iface lo inet loopback

```
You can also try this
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
[COLOR="Blue"]Should restart the machine after doing this[/COLOR][/QUOTE]


I had tried this last night. It didn't work for me. Ill try the other suggestions and post the output when I get home from work. Thanks

---

### Post by dineshs on 2010-07-07
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)

---

### Post by bnhrobotics on 2010-07-07
Removing network manager state didnt work. =(


Output of lshw:

```
bryan@bryan-desktop:~$ sudo lshw -C network
[sudo] password for bryan: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:1d:e2:dd
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.0.100 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:fdf00000-fdf1ffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:0f:b0:d5:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.198 multicast=yes wireless=IEEE 802.11bg
bryan@bryan-desktop:~$ 


```

---

### Post by dineshs on 2010-07-08
Have you tried the following ?
1)right click NM icon and ensure it is enabled?
2)check BIOS
3)then see if these links can help
> [http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)
and
[http://ubuntuforums.org/showpost.php?p=7041625&postcount=4](http://ubuntuforums.org/showpost.php?p=7041625&postcount=4)

---

### Post by mikewhatever on 2010-07-08
According to **sudo lshw -C network** you get IPs on both wired and wireless interfaces, in other words, something is working.
Can you also post the outputs of the following:

ifconfig

nm-tool

---

### Post by bnhrobotics on 2010-07-09
I did some experimentation. Turns out that ethernet works 9.10 and below, but not for 10.04. I did a fresh install for 10.04. 

Here are the results. Excuse the SSID name... my roommates did that.

Network management stuff didn't work. Hope this stuff helps.


```
bryan@bryan-desktop:~$ sudo lshw -C network
[sudo] password for bryan: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:24:1d:1d:e2:dd
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:fdf00000-fdf1ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:0f:b0:d5:42
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.198 multicast=yes wireless=IEEE 802.11bg
bryan@bryan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:1d:e2:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x6000 

eth0:avahi Link encap:Ethernet  HWaddr 00:24:1d:1d:e2:dd  
          inet addr:169.254.9.143  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:0f:b0:d5:42  
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:fff:feb0:d542/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40298652 (40.2 MB)  TX bytes:2029276 (2.0 MB)

bryan@bryan-desktop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:24:1D:1D:E2:DD

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto PEN15] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt73usb
  State:             connected
  Default:           yes
  HW Address:        00:1D:0F:B0:D5:42

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    thecube1:        Infra, 00:23:69:E9:C0:15, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA
    Error404:        Infra, 00:22:6B:98:40:CE, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    gators:          Infra, 00:14:BF:6D:33:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    *PEN15:          Infra, 00:1B:11:6A:B0:CB, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Cyrus the Great: Infra, 00:1E:E5:F3:1C:E5, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.198
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


bryan@bryan-desktop:~$
```

---

### Post by bnhrobotics on 2010-07-15
I can't figure out what is going on. I am on the internet via live CD of 9.10 right now. Any other suggestions before I install 9.10 in place of 10.04? 

It worries me quite a bit that the ethernet stops working from version to version.

---

### Post by dineshs on 2010-07-15
I am not an expert but from post#11 I understand that you have got an IP in wireless interface .Are you trying wireless or wired?Can you post the output of
```
ping 192.168.0.1 -c3
```
```
ping 4.2.2.1 -c3
```

---

### Post by bnhrobotics on 2010-07-15
Wireless works (only using wireless temporarily)
Wired does not (this is my permanent solution)

I'll repost as soon as I can reboot and check those for you.

Thanks

Bryan

---

### Post by dineshs on 2010-07-15
I will be offline for 3 hrs.You can also try this
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
and set```
NetworkingEnabled=true
```

---

### Post by bnhrobotics on 2010-07-15
Networking is already set to true.

bryan@bryan-desktop:~$ ping 192.168.0.1 -c3
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=4.11 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=6.43 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=5.20 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 4.114/5.252/6.437/0.950 ms
bryan@bryan-desktop:~$ ping 4.2.2.1 -c3
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=56 time=45.7 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=56 time=41.6 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=56 time=55.5 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 41.604/47.610/55.508/5.834 ms

---

### Post by dineshs on 2010-07-16
You got these results using wired?Then you can set DNS to 4.2.2.1 in NM under ipv4 and I hope your problem will be solved.
If not
Can you post the results of 
sudo lshw -C network
[COLOR="DarkRed"]while using the live CD[/COLOR].
Because from the result of sudo lshw -C network ( 10.04 ) the driver loaded seem to be r8169 for  RTL8111/8168B PCI Express Gigabit Ethernet controller.I dont know whether this is the problem.Pl see if these links can help
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by bnhrobotics on 2010-07-16
Fixed! 

[http://ubuntuforums.org/showthread.php?p=9597610#post9597610](http://ubuntuforums.org/showthread.php?p=9597610#post9597610)

I guess I had two threads going. Mods can delete this one.

---

