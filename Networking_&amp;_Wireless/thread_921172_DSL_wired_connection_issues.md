---
title: "DSL wired connection issues"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by rusman86 on 2008-09-16
I'm new to the Linux community. I have an old dell desktop that I installed Ubuntu 8.04 server edition on, but it failed the network setup (DHCP). Not only did it fail, but it also shuts down my whole wireless internet when that computer is running now. I figured I would try the desktop edition of Ubuntu and see if I had the same issue. I do. I use yahoo DSL with a 2WIRE router. I tried changing settings from roaming and also tried direct connection and bypassing the router, but both failed with no internet connection. It seems very odd that the router will not broadcast wirelessly, and I lose my whole internet connection throughout the house, when linux is running. I have to power down the linux computer and reset the router in order to get it back. Do you think it is a security issue? I have no idea. Thanks for any help in advance.

---

### Post by Crafty Kisses on 2008-09-16
I'd like to see the results of this command:
```
ifconfig
```

---

### Post by rusman86 on 2008-09-16
I apologize. I should have posted that earlier since that is the first question I saw in most of the forums I checked. Could you please tell me what we are specifically looking for when typing this command? Thanks. Here it is: 

> russell@russell-desktop:~$ ifconfig

eth0 Link encap:Ethernet  HWaddr 00:0b:db:0e:3c:df  
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:20 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:0e:3c:df  
inet addr:169.254.7.55  Bcast:169.254.255.255  Mask:255.255.0.0
UP BROADCAST MULTICAST  MTU:1500  Metric:1
Interrupt:20 

lo Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:1110 errors:0 dropped:0 overruns:0 frame:0
TX packets:1110 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:57100 (55.7 KB)  TX bytes:57100 (55.7 KB)



---

### Post by caljohnsmith on 2008-09-16
Please also post the output of:
```
sudo lshw -C network
```
And just a small tip, when you paste the results into the message box here at the forums, if you highlight it, press the pound sign # at the top of the message box to put "code" tags around it; that will make it easiest to read. :)

---

### Post by rusman86 on 2008-09-16
```
russell@russell-desktop:~$ sudo lshw -C network
[sudo] password for russell: 
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0b:db:0e:3c:df
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s


```

---

### Post by caljohnsmith on 2008-09-16
OK, please also post:
```
cat /etc/modprobe.d/blacklist
route -n
dmesg | grep -ie eth0 -ie b44
cat /etc/network/interfaces
```

---

### Post by rusman86 on 2008-09-16
Thanks for the quick responses. 

```
russell@russell-desktop:~$ sudo cat /etc/modprobe.d/blacklist
[sudo] password for russell: 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

russell@russell-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
russell@russell-desktop:~$ dmesg | grep -ie eth0 -ie b44
[   24.595308] b44.c:v2.0
[   24.615583] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0b:db:0e:3c:df
[   88.249245] ADDRCONF(NETDEV_UP): eth0: link is not ready
russell@russell-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback



iface eth0 inet dhcp

auto eth0


```

---

### Post by caljohnsmith on 2008-09-16
How about pulling up the Network Manager (System > Admin > Network), unlock it, click your eth0 interface, hit properties, and click to enable the roaming mode. Does that allow you to connect?

---

### Post by rusman86 on 2008-09-16
No, enabling roaming mode does not make the internet work. Router still fails as well when Linux is running and Linux computer has to be shut down in order for wireless internet to work throughout my house on windows.

---

### Post by caljohnsmith on 2008-09-16
My mistake, I missed in your first post where you mentioned you had all ready tried roaming mode. Have you run any other OSes on that computer (e.g. Windows), and have they been able to use your ethernet card OK? Also, can you connect any of your other computers to your router via ethernet (not wireless) and confirm that they can connect OK to your router? Also, have you tried connecting to the router via a static IP?

---

### Post by rusman86 on 2008-09-16
I have been running windows XP on that computer through the router and everything has been fine, so I know the router works directly connected. The computer is actually plugged into the router via usb (not sure if that makes a difference). I did not change the setup at all when I switched OS to linux. As far as static IP, I tried that with linux server and it did not work... I looked up my IP using whatismyip.com and put that in. Can you walk me through doing it on ubuntu desktop, or should I try ? Thanks

---

### Post by caljohnsmith on 2008-09-17
> **rusman86 said:**
> I have been running windows XP on that computer through the router and everything has been fine, so I know the router works directly connected. The computer is actually plugged into the router via usb (not sure if that makes a difference). I did not change the setup at all when I switched OS to linux. As far as static IP, I tried that with linux server and it did not work... I looked up my IP using whatismyip.com and put that in. Can you walk me through doing it on ubuntu desktop, or should I try ? Thanks
First, if you can find the "gateway" IP address that your other working computers are using, you'll need that info. If they are Windows, if you right-click the system tray icon for your internet connection, and click "properties", there should be a tab in that dialog box that will tell you. Also from that dialog box, find what that computer's IP address is. Note that the IP address listed will be the computer's LAN IP (the IP your router assigns to that computer), and not your external IP as seen on the internet by sites like whatismyip.com. The IP may be something like 192.168.1.xxx, 192.168.0.xxx, etc. The gateway should be similar too. 

Once you know the gateway and IP, then just open the Network Manager (System > Admin > Network), click unlock and enter your password, click your ethernet interface eth0, click properties, disable roaming mode, under connection settings select "static IP", fill in a static IP that is the same as the IP of the other computer except for the last 3 digits. Fill in gateway as the same as the other computer, and subnet mask is 255.255.255.0. 

If you have trouble, let me know what gateway and IP address your other working computer is using, and we can go from there.

---

### Post by rusman86 on 2008-09-17
I got that info off a different computer that is running vista only. Here is the info:

IPv4 IP address : 172.16.1.36
IPv4 subnet mask : 255.255.0.0
IPv4 default gateway : 172.16.0.1

I remember seeing something about IPv6 in linux.. Do I need to change a setting to work specifically with IPv4? Also, you said subnet mask fill in 255.255.255.0, but my vista computer was using 255.255.0.0. Which one should I use.

---

### Post by caljohnsmith on 2008-09-17
> **rusman86 said:**
> I got that info off a different computer that is running vista only. Here is the info:

IPv4 IP address : 172.16.1.36
IPv4 subnet mask : 255.255.0.0
IPv4 default gateway : 172.16.0.1

I remember seeing something about IPv6 in linux.. Do I need to change a setting to work specifically with IPv4? Also, you said subnet mask fill in 255.255.255.0, but my vista computer was using 255.255.0.0. Which one should I use.
Yes, use the same 255.255.0.0 netmask as Vista is using, because that Vista computer's IP address is varied in the last two octets, not just the last octet compared to the gateway address. I'm wondering though why it is set up that way, because that isn't the the norm for most home routers that I'm aware of. But first on your Vista computer, press the Windows key + r simultaneously to get a "run command" dialog, type "cmd", enter, and in that command screen try:
```
ping 172.16.1.150 
```
If that doesn't return a response, use that IP as the static IP for Ubuntu, along with the 172.16.0.1 gateway. Let me know how it goes.

---

### Post by rusman86 on 2008-09-17
Okay, so basically the subnet mask is going to have 255 for numbers that don't change and 0 for numbers that do change in the IP ?

So I will try to use that IP and let you know.

Result : Failed... Wireless internet still cut out in the house when the computer booted up, and after shutting down the computer, the router automatically reset and internet worked again. I will try a few more times with the static IP before I go to school in a few. Any other suggestions ?

---

### Post by caljohnsmith on 2008-09-17
> **rusman86 said:**
> Okay, so basically the subnet mask is going to have 255 for numbers that don't change and 0 for numbers that do change in the IP ?

Yes.
[quote=rusman86]
So I will try to use that IP and let you know.

Result : Failed... Wireless internet still cut out in the house when the computer booted up, and after shutting down the computer, the router automatically reset and internet worked again. I will try a few more times with the static IP before I go to school in a few. Any other suggestions ?[/QUOTE]
I'll have to give it some more thought. Yours is the first case I've come across of a router "crashing" or becoming unusable just by trying to connect to it. Really strange.

---

### Post by rusman86 on 2008-09-17
Yea, I tried a few more times, still same result. What is the IPv6 and IPv4 difference ? In the network settings, there is a 'host' tab and all the info in there is IPv6, not IPv4, which was what Vista had stated. 

I will check to see if there is a firmware update on my router as well.

---

### Post by rusman86 on 2008-09-18
I have found other threads listing same problem with 2wire router. It is a router problem.. If anyone has found a solution or working firmware update, please advise. I will look into getting a new router

---

### Post by caljohnsmith on 2008-09-18
One more thought, rusman86: can you go into your router settings and change it so your computers on the LAN use the same subnet as your router IP (the gateway address)? I mean making the computers use addresses 172.16.0.xxx instead of 172.16.1.xxx. I think that could only help. Let me know if you try it and if it makes any difference.

---

